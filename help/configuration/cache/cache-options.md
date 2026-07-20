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
source-git-commit: a7e44e5b4ddeda89b9fee08aa29b1a31f521e90a
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 0%

---

# 캐시 백엔드 옵션 및 저장소 참조

{{cloud-cache-config}}

Commerce 애플리케이션은 낮은 수준의 캐시 프론트엔드 및 백엔드를 사용하여 캐시 스토리지에 대한 액세스를 제공합니다. Commerce은 다양한 사용 사례에 맞는 여러 캐싱 백엔드 및 전략을 지원합니다. 이 페이지에서는 사용 가능한 백엔드 및 차이점에 대해 설명합니다.

>[!NOTE]
>
>[Vannish](config-varnish.md)은(는) HTTP 수준에서 전체 페이지 캐싱을 처리하고 낮은 수준의 캐시 백엔드를 사용하지 않습니다.

## 백엔드 캐시 옵션

다음 표에서는 사용 가능한 백엔드 캐시를 요약합니다.

| 백엔드 | 설명 | 구성 안내서 |
| ------- | ----------- | ------------------- |
| 파일 시스템 | 기본값. 캐시 데이터를 `var/cache/` 아래 파일에 저장합니다. 구성이 필요하지 않습니다. | 해당 사항 없음 |
| [레디스](config-redis.md) | 고성능 캐싱을 위한 메모리 내 데이터 저장소입니다. | [기본 캐시에 Redis 사용](redis-pg-cache.md)<br>**참고: Adobe Commerce 2.4.9 또는 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 및 2.4.8-p5 이상의 패치 릴리스에는 Redis 캐시가 지원되지 않습니다. Redis가 지원되지 않는 캐시 구성에 Valkey를 사용합니다. 릴리스별로 지원되는 캐시 서비스에 대해서는 [시스템 요구 사항](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/system-requirements)을 참조하십시오. |
| [Valkey](config-valkey.md) | 오픈 소스, Redis 호환 대안. | [기본 캐시에 대한 Valkey 사용](valkey-pg-cache.md) |
| [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | 데이터베이스 지원 캐싱. | [사용자 지정 캐시 엔진 만들기](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"}(Adobe 개발자 설명서) |

{{redis-cache-support}}

## 구현 접근 방식

Commerce은 두 가지 백엔드 구현 접근 방식을 지원합니다. 선택하는 접근 방식은 Commerce 버전에 따라 다릅니다.

>[!BEGINTABS]

>[!TAB 기존 Zend 기반 캐시(2.4.8 및 이전 버전)]

백엔드 구성에 전체 클래스 이름을 사용합니다.

| 백엔드 | 클래스 이름 |
| ------- | ---------- |
| 레디스 | `Magento\Framework\Cache\Backend\Redis` |
| 밸키 | `Magento\Framework\Cache\Backend\Valkey` |

`Zend_Cache_Backend` 인터페이스와 호환됩니다.

**예제 구성:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB 최신 Symfony 캐시(2.4.9 이상, 권장)]

>[!TIP]
>
>최신 Symfony 캐시 구현은 PSR-6 준수, Igbinary serialization, gzip 압축, Lua 스크립트 및 영구 연결을 통해 더 나은 성능을 제공합니다.

간소화된 백엔드 유형 이름을 사용합니다.

| 백엔드 | 이름 입력 |
| ------- | --------- |
| 레디스 | `redis` |
| 밸키 | `valkey` |
| 파일 시스템 | `file` |

**예제 구성:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

전체 구성 옵션에 대해서는 다음을 참조하십시오.

- [기본 캐시에 Redis 사용](redis-pg-cache.md)
- [기본 캐시에 Valkey 사용](valkey-pg-cache.md)
- [L2 캐시 구성](level-two-cache.md)

기존 Zend 기반 옵션에 대해서는 [Laminas 설명서](https://docs.laminas.dev/)를 참조하십시오.
