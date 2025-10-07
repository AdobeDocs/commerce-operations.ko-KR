---
title: config.php 참조
description: Adobe Commerce 구성에 대한 config.php 파일 값 및 섹션에 대해 알아봅니다. 모듈, 범위, 시스템 설정 및 배포 모범 사례를 살펴봅니다.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 1%

---

# config.php 참조

`config.php` 파일에는 다음 섹션이 포함되어 있습니다.

| 이름 | 설명 |
| --------- | -------------------|
| `i18n` | 모든 인라인 번역 데이터. 이 섹션에서는 읽을 수 없습니다. |
| `modules` | 활성화 및 비활성화 모듈 목록입니다. |
| `scopes` | 관련 정보가 있는 스토어, 스토어 그룹 및 웹 사이트 목록. |
| `system` | 정적 콘텐츠 배포에 필요한 시스템 구성입니다. |
| `themes` | 설치된 테마의 구성입니다. |

## 모듈

모듈 배열과 해당 상태를 포함합니다. 모듈이 활성화된 경우 값은 1입니다. 그렇지 않으면 값이 0입니다.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

[모듈]에 대해 자세히 알아보세요.

## 범위

범위 구성 값의 배열을 포함합니다. 여기에는 다음과 같은 하위 노드가 있습니다.

| 이름 | 설명 |
| ---------- | -----------------------------------|
| `websites` | 웹 사이트 구성 |
| `groups` | 구성 저장 |
| `stores` | 보기 구성 저장 |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

[Commerce 범위][scopes]에 대해 자세히 알아보세요.

## 시스템

시스템 필드 구성 값의 배열을 포함합니다.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

[시스템별 구성](config-reference-sens.md)에 대해 자세히 알아보세요.

## 테마

테마 구성에 대한 값 배열을 포함합니다.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

[테마]에 대해 자세히 알아보세요.

<!-- link definitions -->

[모듈]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[테마]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
