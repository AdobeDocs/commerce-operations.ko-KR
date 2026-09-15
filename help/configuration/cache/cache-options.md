---
title: 캐시 백엔드 옵션 및 저장소 참조
description: 파일 시스템, Redis, Valkey 및 데이터베이스 저장소를 포함하여 Adobe Commerce의 캐시 백엔드 옵션에 대해 알아봅니다. Zend 기반(RemoteSynchronizedCache) 및 Symfony 캐시 옵션을 검색합니다.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# 캐시 백엔드 옵션 및 저장소 참조

>[!NOTE]
>
>이 페이지는 온-프레미스 `app/etc/env.php` 구성을 문서화합니다.
>
>[!DNL Adobe Commerce on Cloud] 프로젝트의 경우 `ece-tools` 패키지는 `.magento.env.yaml`의 배포 변수 구성에 따라 배포 중에 결과 `app/etc/env.php` 구성을 생성합니다. `env.php` 파일을 편집하지 않습니다.  [Valkey 및 Redis 서비스 구성에 대한 모범 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) 및 [변수 배포](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)를 참조하세요.

Commerce 애플리케이션은 낮은 수준의 캐시 프론트엔드 및 백엔드를 사용하여 캐시 스토리지에 대한 액세스를 제공합니다. Commerce은 다양한 사용 사례에 맞는 여러 캐싱 백엔드 및 전략을 지원합니다. 이 페이지에서는 사용 가능한 백엔드 및 차이점에 대해 설명합니다.

>[!NOTE]
>
>[Vannish](config-varnish-install.md)은(는) 온-프레미스 배포에 대한 HTTP 수준에서 전체 페이지 캐싱을 처리합니다. [Fastly 서비스](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly)에서 클라우드 배포에 대해 처리합니다. 두 솔루션 모두 낮은 수준의 캐시 백엔드를 사용하지 않습니다.

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

다음 표에는 `<Commerce-install-dir>/app/etc/env.php`에 대한 캐시 백 엔드 구성 값이 요약되어 있습니다. L2 캐싱은 활성화하지 않습니다.

| Commerce 버전 | 백엔드 | 구성 값 |
| ---------------- | ------- | -------------------- |
| 2.4.8 이하(지원되는 경우) | 파일 | 기본값. 구성이 필요하지 않습니다. |
| 2.4.8 이하(지원되는 경우) | 레디스 | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 이하(지원되는 경우) | 밸키 | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 이상 및 지원되는 백포트 | 파일 | `file` |
| 2.4.9 이상 및 지원되는 백포트 | 밸키 | `valkey` |

정확한 패치 수준 지원은 [시스템 요구 사항](../../installation/system-requirements.md)을 참조하십시오.

>[!TAB Zend 기반 캐시(2.4.8 및 이전 버전)]

#### 백엔드 예

온-프레미스 배포의 경우 다음 예제에서는 `<Commerce-install-dir>/app/etc/env.php`에서 직접 캐시 백엔드를 구성합니다. L2 캐싱은 활성화하지 않습니다. 배포 중에 `ece-tools` 패키지를 사용하여 결과 `app/etc/env.php` 구성을 생성하는 [!DNL Adobe Commerce on Cloud] 배포에는 이러한 예제를 사용하지 마십시오.

>[!BEGINTABS]

>[!TAB 레디스]

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

>[!TAB Valkey]

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

>[!ENDTABS]

## L2 캐싱

L2(2-level) 캐싱은 공유 원격 캐시 스토리지 앞의 각 웹 노드에 로컬 캐시 계층을 추가하여 Commerce과 원격 캐시 간의 네트워크 트래픽을 줄입니다. 구현 옵션, 버전 지원 및 구성 단계는 [L2 캐시 구성](level-two-cache.md)을 참조하십시오.

클라우드 프로젝트의 경우 [변수 배포](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}에 설명된 배포 변수를 통해 L2 캐싱을 구성합니다.

- [기본 캐시에 Redis 사용](redis-pg-cache.md)
- [기본 캐시에 Valkey 사용](valkey-pg-cache.md)
- [L2 캐시 구성](level-two-cache.md)
