---
title: 캐시 프론트엔드 및 유형 구성
description: Adobe Commerce에서 캐시 프론트엔드를 정의하고 캐시 유형과 연결하는 방법에 대해 알아봅니다. env.php 및 di.xml의 구성 구문을 살펴보십시오.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2: id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: d3c3e48c7627b932d1e46a7d2a99fa77b8b75b4c
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 0%

---

# 캐시 프론트엔드 및 유형 구성

캐시 프론트엔드는 Commerce 캐시 유형과 캐시 저장소 백엔드 간의 인터페이스입니다. 각각 다른 백엔드 설정을 사용하는 여러 프론트엔드를 정의한 다음 각 프론트엔드에 특정 [캐시 유형](../cli/manage-cache.md#clean-and-flush-cache-types)을(를) 할당할 수 있습니다.

이 관계를 사용하여 각 캐시 유형이 데이터를 저장하는 위치를 결정합니다.

`cache type` -> `cache frontend` -> `cache backend`

이 기능은 캐시된 데이터의 여러 유형에 대해 서로 다른 캐시 백엔드 또는 구성을 사용하려는 경우에 유용합니다. 예를 들어 전용 Valkey 데이터베이스를 사용하는 `page_cache` 프런트 엔드에 `full_page` 캐시 형식을 할당하고 다른 캐시 형식에서는 `default` 프런트 엔드를 사용할 수 있습니다.

{{cloud-cache-config}}

## 기본 프론트엔드 사용

Commerce은 모든 캐시 유형에 대해 작동하는 `default` 캐시 프런트 엔드를 제공합니다. [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 프런트 엔드 캐시를 구현하여 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)을(를) 확장합니다.

대부분의 경우 프론트엔드를 사용자 지정할 필요가 없습니다. 백엔드를 구성하기만 하면 됩니다. [캐시 백 엔드 옵션](cache-options.md)을 참조하십시오.

## 사용자 지정 캐시 프론트엔드 정의

다음 단계는 캐시 프론트엔드를 캐시 유형과 연결하는 단계입니다.

### 1단계: 캐시 프론트엔드 정의 및 캐시 유형 할당

사용자 지정 캐시 프론트엔드를 정의하려면 `di.xml`을(를) 재정의하는 `app/etc/env.php`에 구성을 추가하십시오.

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

위치:

- `<unique frontend id>` — 프론트엔드를 식별하는 고유한 이름(예: `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>` — 이 프론트엔드에 대한 백엔드 유형 및 옵션([캐시 옵션](cache-options.md) 참조)
- `<cache type>` — 이 프런트 엔드에 할당할 Commerce 캐시 유형(예: `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>Adobe Commerce 2.4.9 이상에서는 Symfony 캐시 구현에서 `valkey` 또는 `file`과(와) 같은 간소화된 백엔드 유형 이름을 사용합니다. 백 엔드 예제 및 버전별 지침은 [캐시 백 엔드 옵션](cache-options.md)을 참조하십시오.


### 2단계: 프론트엔드 및 백엔드 옵션 구성

`env.php` 또는 `di.xml`에서 프론트엔드 및 백 엔드 캐시 구성 옵션을 지정할 수 있습니다. 이 작업은 선택 사항입니다. 옵션을 지정하지 않으면 Commerce에서는 기본 프론트엔드 및 백엔드 설정을 사용합니다.

`env.php` 예:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

위치:

- `<frontend_type>` — 낮은 수준의 프런트 엔드 캐시 유형입니다. `Zend\Cache\Core`과(와) 호환되는 클래스 이름을 지정하십시오.
생략하면 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)이(가) 사용됩니다.

- `<frontend_option>`, `<frontend_option_value>` — Commerce 프레임워크가 생성 시 프론트엔드 캐시에 연관 배열로 전달하는 옵션의 이름과 값입니다.

- `<backend_type>` — 낮은 수준의 백엔드 캐시 유형입니다. 다음을 지정할 수 있습니다.
  - **최신 Symfony 캐시(2.4.9+, 권장)**: `valkey` 또는 `file`과(와) 같이 간단한 이름
  - **레거시(Zend 기반)**: `Zend_Cache_Backend_Interface`을(를) 구현하는 `Zend_Cache_Backend`과(와) 호환되는 전체 클래스 이름

- `<backend_option>`, `<backend_option_value>` — Commerce 프레임워크가 생성 시 연관 배열로 백엔드 캐시에 전달하는 옵션의 이름 및 값입니다.

>[!NOTE]
>
>**기존 구현과 최신 구현:**
>
>- **레거시(Zend 기반)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **최신(Symfony 캐시)**: Commerce 버전 2.4.9+의 경우 `'backend' => 'valkey'`, 2.4.5 - 2.4.8 릴리스 라인의 경우 현재 패치 릴리스. 여기서 Valkey는 지원되는 캐시 백엔드입니다.
>
>최신 Symfony 캐시 구현은 PSR-6 준수, Igbinary serialization, gzip 압축, Lua 스크립트 및 영구 연결을 통해 더 나은 성능을 제공합니다.

Zend 기반 옵션에 대해서는 [Laminas 설명서](https://docs.laminas.dev/)를 참조하십시오. Symfony 캐시 구성에 대해서는 이 설명서의 [Redis](redis-pg-cache.md) 및 [Valkey](valkey-pg-cache.md) 문서를 참조하십시오.
