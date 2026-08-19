---
title: 캐시 백엔드 옵션 및 저장소 참조
description: 파일 시스템, Redis, Valkey 및 데이터베이스 저장소를 포함하여 Adobe Commerce의 캐시 백엔드 옵션에 대해 알아봅니다. 기존 및 최신 접근 방식을 살펴보십시오.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 761
ht-degree: 0%

---

# 캐시 백엔드 옵션 및 저장소 참조

>[!NOTE]
>
>이 페이지는 온-프레미스 `app/etc/env.php` 구성을 문서화합니다.
>
>[!DNL Adobe Commerce on Cloud] 프로젝트의 경우 `ece-tools` 패키지는 `.magento.env.yaml`의 배포 변수 구성에 따라 배포 중에 결과 `app/etc/env.php` 구성을 생성합니다. `env.php` 파일을 편집하지 않습니다.  [Valkey 및 Redis 서비스 구성에 대한 모범 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) 및 [변수 배포](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)를 참조하세요.

Commerce 애플리케이션은 낮은 수준의 캐시 프론트엔드 및 백엔드를 사용하여 캐시 스토리지에 대한 액세스를 제공합니다. Commerce은 다양한 사용 사례에 맞는 여러 캐싱 백엔드 및 전략을 지원합니다. 이 페이지에서는 사용 가능한 백엔드 및 차이점에 대해 설명합니다.

>[!NOTE]
>
>[Vannish](config-varnish-install.md)은(는) 온-프레미스 배포에 대한 HTTP 수준에서 전체 페이지 캐싱을 처리합니다. [Fastly 서비스](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/cdn/fastly)에서 클라우드 배포에 대해 처리합니다. 두 솔루션 모두 낮은 수준의 캐시 백엔드를 사용하지 않습니다.

## 백엔드 캐시 옵션

다음 표에서는 사용 가능한 백엔드 캐시를 요약합니다.

| 백엔드 | 설명 | 구성 안내서 |
| ------- | ----------- | ------------------- |
| 파일 시스템 | 기본값. 캐시 데이터를 `var/cache/` 아래 파일에 저장합니다. 구성이 필요하지 않습니다. | 해당 사항 없음 |
| 레디스 | 고성능 캐싱을 위한 메모리 내 데이터 저장소입니다. | [기본 캐시에 Redis 사용](redis-pg-cache.md) |
| 밸키 | 오픈 소스, Redis 호환 대안. | [기본 캐시에 대한 Valkey 사용](valkey-pg-cache.md) |
| 데이터베이스 | 데이터베이스에서 지원하는 사용자 지정 캐시 엔진 | [사용자 지정 캐시 엔진 만들기](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"}(Adobe Developer 설명서) |

>[!IMPORTANT]
>
>Redis 캐시는 Adobe Commerce 2.4.9 또는 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 및 2.4.8-p4 이상의 패치 릴리스에서는 지원되지 않습니다. 이러한 버전 중 하나로 업그레이드하는 경우 Valkey를 구성하고 이를 사용하도록 캐시 구성을 업데이트합니다. [!DNL Adobe Commerce on-premises]에 대해서는 [Valkey 설정](config-valkey.md)을 참조하십시오.

## 캐시 백엔드 및 L2 구현 {#implementation-approaches}

Commerce은 직접 캐시 백엔드 및 L2 캐싱을 지원합니다. 직접 백엔드가 캐시 스토리지를 선택합니다. L2 캐싱은 원격 스토리지 앞에 로컬 캐시 레이어를 추가합니다.

### 직접 캐시 백엔드

다음 PHP 예제는 `<Commerce-install-dir>/app/etc/env.php`에서 캐시 백엔드를 구성합니다. L2 캐싱은 활성화하지 않습니다.

| Commerce 버전 | 구현 | 백엔드 | 구성 값 |
| ---------------- | -------------- | ------- | ------------------- |
| 2.4.8 이하(지원되는 경우) | 레거시 | 파일 시스템(기본값) | 구성이 필요하지 않습니다. |
| 2.4.8 이하(지원되는 경우) | 레거시 | 레디스 | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 이하(지원되는 경우) | 레거시 | 밸키 | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 이상 및 지원되는 백포트 | 최신 Symfony 캐시 | 파일 시스템(기본값) | `file` |
| 2.4.9 이상 및 지원되는 백포트 | 최신 Symfony 캐시 | 밸키 | `valkey` |

정확한 패치 수준 지원은 [시스템 요구 사항](../../installation/system-requirements.md)을 참조하십시오.

>[!NOTE]
>
>최신 구현에서는 `redis` 형식 이름을 사용할 수 있지만 Redis는 Valkey가 필요한 공식적으로 지원되는 캐시 서비스가 아닙니다. 대신 `valkey`을(를) 사용합니다.

#### 기존 Zend 기반 백엔드 예

온-프레미스 배포의 경우 다음 예제에서는 `<Commerce-install-dir>/app/etc/env.php`에서 직접 캐시 백엔드를 구성합니다. L2 캐싱은 활성화하지 않습니다. 배포 중에 `ece-tools` 패키지를 사용하여 결과 `app/etc/env.php` 구성을 생성하는 [!DNL Adobe Commerce on Cloud] 배포에는 이러한 예제를 사용하지 마십시오.

>[!BEGINTABS]

>[!TAB 기존 백 엔드 Redis]

Redis가 지원되는 릴리스에서만 전체 Redis 클래스 이름을 사용하십시오.

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB 기존 백 엔드 값]

기존 Valkey 백엔드를 지원하는 릴리스에서 전체 Valkey 클래스 이름을 사용합니다.

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

#### 최신 Sympony 캐시 백엔드

기본 직접 백엔드는 파일 시스템입니다. 최신 구현과 함께 Valkey를 사용하려면 간소화된 `valkey` 백 엔드 유형을 사용하십시오.

다음 구성 예는 최신 Symfony 캐시 구현으로 직접 기본 캐싱을 구성할 때 Adobe Commerce 2.4.9 이상에 올바르고 Valkey가 지원되는 백포트에 적합합니다.

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TIP]
>
>Symfony 캐시 구현은 igbinary serialization, compression, Lua scripts 및 persistent connections와 같은 선택적 성능 기능을 지원합니다. 자세한 내용은 [기본 및 페이지 캐시에 대한 Valkey 구성](valkey-pg-cache.md)을 참조하십시오.

### L2 캐시 구현

L2(2-level) 캐싱은 공유 원격 캐시 스토리지 앞의 각 웹 노드에 로컬 캐시 계층을 추가하여 Commerce과 원격 캐시 간의 네트워크 트래픽을 줄입니다.

| Commerce 버전 | L2 구현 | 원격 백엔드 |
| ---------------- | ------------------ | --------------- |
| 지원되는 경우 2.4.9 이전 | RemoteSynchronizedCache | Commerce 릴리스 및 패치 수준 지원 매트릭스에 따라 Redis 또는 Valkey |
| 2.4.9 이상 | symfony_l2 | 밸키 |

온-프레미스 구성에 대해서는 [L2 캐시 구성](level-two-cache.md)을 참조하세요.

클라우드 프로젝트의 경우 [변수 배포](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}에 설명된 배포 변수를 통해 L2 캐싱을 구성합니다.

#### L2 캐시 구성

- **[!DNL Adobe Commerce on-premises]** 구성 세부 정보는 [L2 캐시 구성](level-two-cache.md)을 참조하십시오.

- **[!DNL Adobe Commerce on Cloud]**&#x200B;의 경우 `app/etc/env.php`을(를) 직접 편집하지 않고 적절한 배포 변수를 통해 L2 캐싱을 구성하십시오. _Cloud의 Adobe Commerce_ 설명서에서 [변수 배포](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}를 참조하십시오.
