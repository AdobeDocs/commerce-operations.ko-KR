---
title: 캐시 유형
description: 캐시 프런트 엔드를 캐시 유형과 연결합니다.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 캐시 유형

다음 단계는 캐시 프론트엔드를 캐시 유형과 연결하는 단계를 설명합니다.

## 1단계: 캐시 프론트엔드 정의

상거래 애플리케이션에 `default` 다음에 사용할 수 있는 캐시 프론트엔드 [캐시 유형](../cli/manage-cache.md#clean-and-flush-cache-types). 이 섹션에서는 선택적으로 다른 이름으로 캐시 프론트엔드를 정의하는 방법에 대해 설명합니다. 이는 프론트엔드를 사용자 정의하려는 경우에 유용합니다.

>[!INFO]
>
>을(를) 사용하려면 `default` 캐시 유형, 수정할 필요가 없습니다. `env.php` 즉, Commerce의 글로벌 을 수정합니다 `di.xml`. 다음을 참조하십시오 [낮은 수준의 캐시 옵션](cache-options.md).

사용자 지정 캐시 프런트 엔드를 지정해야 합니다. `app/etc/env.php` 또는 Commerce의 글로벌 `app/etc/di.xml`.

다음 예에서는 `env.php` 파일, 재정의 `di.xml` 파일:

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

위치 `<unique frontend id>` 는 프론트엔드를 식별하는 고유한 이름입니다. `<cache options>` 각 캐싱 유형(데이터베이스, Redis 등)에 대한 항목에서 설명하는 옵션입니다.

## 2단계: 캐시 구성

에서 프론트엔드 및 백엔드 캐시 구성 옵션을 지정할 수 있습니다. `env.php` 또는 `di.xml`. 이 작업은 선택 사항입니다.

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

- `<frontend_type>` 는 낮은 수준의 프론트엔드 캐시 유형입니다. 호환되는 클래스의 이름을 지정하십시오. `Zend\Cache\Core`.
을 생략하는 경우 `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 를 사용합니다.

- `<frontend_option>`, `<frontend_option_value>` 는 Commerce 프레임워크가 생성 시 프론트엔드 캐시에 연관 배열로 전달하는 옵션의 이름과 값입니다.
- `<backend_type>` 는 낮은 수준의 백엔드 캐시 유형입니다. 호환되는 클래스의 이름을 지정하십시오. `Zend_Cache_Backend` 그리고 그것은 `Zend_Cache_Backend_Interface`.
- `<backend_option>` 및 `<backend_option_value>` 는 Commerce 프레임워크가 작성 시 연관 배열로 백엔드 캐시에 전달하는 옵션의 이름과 값입니다.

다음을 참조하십시오. [Laminas 설명서](https://docs.laminas.dev/) 최신 Zend 정보를 제공합니다.
