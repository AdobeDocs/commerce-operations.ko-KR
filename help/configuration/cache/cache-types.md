---
title: 캐시 프론트엔드 및 유형 구성
description: Adobe Commerce에서 캐시 프론트엔드를 정의하고 캐시 유형과 연결하는 방법에 대해 알아봅니다. env.php의 구성 구문을 살펴보십시오.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2: id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 3652976a8db3d0bb19ff9cd06adb3a7736c89539
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# 캐시 프론트엔드 및 유형 구성

캐시 프론트엔드는 Commerce 캐시 유형을 캐시 스토리지에 연결합니다. 여러 프론트엔드를 정의하고 각 프론트엔드에 특정 캐시 유형을 할당할 수 있습니다.

>[!BEGINSHADEBOX]

캐시 유형이 데이터를 저장하는 위치를 확인하려면 다음 관계를 사용하십시오.

캐시 유형 → 캐시 프론트엔드 → 캐시 백엔드

>[!ENDSHADEBOX]

Commerce 캐싱 아키텍처에 대한 개요는 [캐싱 개요 및 구성 옵션](caching-overview.md)을 참조하십시오.

>[!NOTE]
>
>클라우드 인프라의 Adobe Commerce의 경우 Cloud Guide에 설명된 [클라우드 배포 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml)을 사용하십시오. `app/etc/env.php`을(를) 직접 편집하지 마십시오. 배포 도구는 이 파일을 생성하며 수동 변경 사항을 덮어쓸 수 있습니다.

## 기본 프론트엔드 사용

Commerce은 모든 캐시 유형에서 사용할 수 있는 기본 프론트엔드를 제공합니다.

대부분의 경우 사용자 지정 프론트엔드를 정의할 필요가 없습니다. 모든 캐시 유형이 동일한 백엔드 및 백엔드 옵션을 사용할 수 있는 경우 기본 프론트엔드를 사용하고 해당 백엔드를 구성합니다. 백엔드별 구성에 대해서는 [캐시 백 엔드 옵션](cache-options.md)을 참조하십시오.

2.4.9 이전 버전의 Adobe Commerce의 경우, 기본 프론트엔드는 이전 Zend 기반 캐시 구현을 사용합니다. `Magento\Framework\Cache\Core` 프런트 엔드가 `Zend_Cache_Core`을(를) 확장합니다. Adobe Commerce 2.4.9 이상 버전에서는 최신 Symfony 구현을 사용합니다. 버전별 지침은 [캐시 백엔드 옵션](cache-options.md)을 참조하십시오.

## 사용자 지정 프론트엔드 정의

하나 이상의 캐시 유형에 기본 프론트엔드와 다른 백엔드 설정이 필요한 경우 사용자 지정 캐시 프론트엔드를 사용합니다.

온-프레미스 배포의 경우 `app/etc/env.php`에서 프론트엔드를 정의합니다. 그런 다음 하나 이상의 캐시 유형을 할당합니다.

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

위치:

- `<frontend-id>`은(는) `default` 또는 `page_cache`과(와) 같은 프런트 엔드의 고유 식별자입니다.
- `<backend-type>`은(는) 프론트엔드에서 사용하는 백엔드를 식별합니다. 지원되는 값은 Adobe Commerce 릴리스 및 선택한 백엔드에 따라 다릅니다.
- `backend_options`에 선택한 백엔드에 대한 옵션이 포함되어 있습니다.
- `<cache-type-id>`은(는) `config`, `layout`, `block_html` 또는 `full_page`과(와) 같은 Commerce 캐시 유형입니다.


백엔드 유형, 지원되는 옵션 및 릴리스별 구성 예제에 대해서는 [캐시 백엔드 옵션](cache-options.md)을 참조하십시오.

## 캐시 유형을 프론트엔드에 할당

`type` 구성은 캐시 형식을 프런트 엔드에 매핑합니다.

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

이 예제에서 Commerce은 `full_page` 캐시 형식을 `page_cache` 프런트 엔드에 할당합니다. 프론트엔드는 해당 캐시 유형을 저장하는 백엔드 구성을 결정합니다.

>[!NOTE]
>
>`full_page` 키는 Commerce 응용 프로그램 캐시 형식을 나타냅니다. Varnish 또는 Fastly를 통한 HTTP 전체 페이지 캐싱은 별도의 캐싱 레이어입니다. [캐싱 개요 및 구성 옵션](caching-overview.md)을 참조하세요.

>[!MORELIKETHIS]
>
>- 성능 최적화를 위한 [L2 캐시 구성](level-two-cache.md)
>- [캐시 관리](../cli/manage-cache.md)
