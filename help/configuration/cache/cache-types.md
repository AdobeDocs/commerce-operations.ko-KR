---
title: 캐시 유형
description: 캐시 프론트론을 캐시 유형과 연결합니다.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 캐시 유형

다음 단계는 캐시 프론트렌드와 캐시 유형을 연결하는 단계를 안내합니다.

## 1단계: 캐시 프론트엔드 정의

상거래 응용 프로그램에는 `default` 모든 용도로 사용할 수 있는 프런트 엔드 캐시 [캐시 유형](../cli/manage-cache.md#clean-and-flush-cache-types). 이 섹션에서는 프론트런트를 사용자 지정할 경우 더 선호하는 다른 이름을 사용하는 캐시 프론트론을 선택적으로 정의하는 방법을 설명합니다.

>[!INFO]
>
>를 사용하려면 `default` 캐시 유형, 수정할 필요가 없습니다. `env.php` 전혀; 상거래 전역 수정 `di.xml`. 자세한 내용은 [낮은 수준의 캐시 옵션](cache-options.md).

사용자 지정 캐시 프론트론을 지정해야 합니다 `app/etc/env.php` 또는 상거래 글로벌 `app/etc/di.xml`.

다음 예제는 `env.php` 파일을 재정의하는 경우 `di.xml` 파일:

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

위치 `<unique frontend id>` 는 프론트엔드 및 를 식별하는 고유한 이름입니다. `<cache options>` 옵션은 각 캐싱 유형(데이터베이스, Redis 등)에 해당하는 주제에 설명되어 있습니다.

## 2단계: 캐시 구성

에서 프런트 엔드 및 백엔드 캐시 구성 옵션을 지정할 수 있습니다 `env.php` 또는 `di.xml`. 이 작업은 선택 사항입니다.

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

여기서

- `<frontend_type>` 낮은 수준의 프런트 엔드 캐시 유형입니다. 와 호환되는 클래스의 이름을 지정합니다 `Zend\Cache\Core`.
생략하면 `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 이 사용됩니다.

- `<frontend_option>`, `<frontend_option_value>` 커머스 프레임워크가 생성 시 프런트 엔드 캐시에 연관 배열로 전달하는 옵션의 이름 및 값입니다.
- `<backend_type>` 는 낮은 수준의 백엔드 캐시 유형입니다. 와 호환되는 클래스의 이름을 지정합니다 `Zend_Cache_Backend` 그리고 `Zend_Cache_Backend_Interface`.
- `<backend_option>` 및 `<backend_option_value>` 은 상거래 프레임워크가 생성 시 백엔드 캐시에 연관 배열로 전달하는 옵션의 이름 및 값입니다.

자세한 내용은 [Laminas 설명서](https://docs.laminas.dev/) 최신 Zend 정보를 확인하십시오.
