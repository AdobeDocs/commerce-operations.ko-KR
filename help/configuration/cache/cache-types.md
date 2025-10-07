---
title: 캐시 유형
description: Adobe Commerce에서 캐시 프론트엔드를 캐시 유형과 연결하는 방법에 대해 알아봅니다. 캐시 구성 및 관리 기술을 살펴봅니다.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 캐시 유형

다음 단계는 캐시 프론트엔드를 캐시 유형과 연결하는 단계를 설명합니다.

## 1단계: 캐시 프론트엔드 정의

Commerce 응용 프로그램에는 `default`캐시 형식[에 사용할 수 있는 ](../cli/manage-cache.md#clean-and-flush-cache-types) 캐시 프론트엔드가 있습니다. 이 섹션에서는 선택적으로 다른 이름으로 캐시 프론트엔드를 정의하는 방법에 대해 설명합니다. 이는 프론트엔드를 사용자 정의하려는 경우에 유용합니다.

>[!INFO]
>
>`default` 캐시 유형을 사용하려면 `env.php`을(를) 전혀 수정할 필요가 없습니다. Commerce의 전역 `di.xml`을(를) 수정합니다. [낮은 수준의 캐시 옵션](cache-options.md)을 참조하세요.

사용자 지정 캐시 프론트엔드를 `app/etc/env.php` 또는 Commerce의 전역 `app/etc/di.xml`에 지정해야 합니다.

다음 예제에서는 `env.php` 파일을 재정의하는 `di.xml` 파일에서 정의하는 방법을 보여 줍니다.

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

여기서 `<unique frontend id>`은(는) 프론트엔드를 식별하는 고유한 이름이며 `<cache options>`은(는) 각 캐싱 유형(데이터베이스, Redis 등)과 관련된 항목에서 논의되는 옵션입니다.

## 2단계: 캐시 구성

`env.php` 또는 `di.xml`에서 프론트엔드 및 백 엔드 캐시 구성 옵션을 지정할 수 있습니다. 이 작업은 선택 사항입니다.

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

위치

- `<frontend_type>`은(는) 낮은 수준의 프런트 엔드 캐시 유형입니다. `Zend\Cache\Core`과(와) 호환되는 클래스의 이름을 지정하십시오.
`<frontend_type>`을(를) 생략하면 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)이(가) 사용됩니다.

- `<frontend_option>`, `<frontend_option_value>`은(는) 생성 시 Commerce 프레임워크가 연관 배열로 프론트엔드 캐시에 전달하는 옵션의 이름과 값입니다.
- `<backend_type>`은(는) 낮은 수준의 백엔드 캐시 유형입니다. `Zend_Cache_Backend`과(와) 호환되고 `Zend_Cache_Backend_Interface`을(를) 구현하는 클래스의 이름을 지정하십시오.
- `<backend_option>` 및 `<backend_option_value>`은(는) Commerce 프레임워크가 생성 시 연관 배열로 백엔드 캐시에 전달하는 옵션의 이름과 값입니다.

최신 Zend 정보는 [Laminas 설명서](https://docs.laminas.dev/)를 참조하십시오.
