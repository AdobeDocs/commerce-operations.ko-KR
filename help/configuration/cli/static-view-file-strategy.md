---
title: 정적 보기 파일을 위한 배포 전략
description: Adobe Commerce 애플리케이션에서 정적 보기 파일의 배포 전략에 대해 알아봅니다. 다양한 사용 사례에 적합한 최적의 배포 방법을 살펴보십시오.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 정적 보기 파일을 위한 배포 전략

정적 보기 파일을 배포할 때 사용 가능한 세 가지 전략 중 하나를 선택할 수 있습니다. 각 CSR은 다양한 사용 사례에 대해 최적의 배포 결과를 제공합니다.

- [표준](#standard-strategy): 일반 배포 프로세스입니다.
- [빠른](#quick-strategy)(_기본_): 두 개 이상의 로케일에 대한 파일을 배포할 때 배포에 필요한 시간을 최소화합니다.
- [작게](#compact-strategy): 게시된 보기 파일에서 사용하는 공간을 최소화합니다.

다음 섹션에서는 각 전략의 구현 세부 사항 및 기능에 대해 설명합니다.

## 표준 전략

표준 전략을 사용하면 모든 패키지에 대한 모든 정적 보기 파일이 배포됩니다. 즉, [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php)에서 처리합니다.

자세한 내용은 [정적 보기 파일 배포](../cli/static-view-file-deployment.md)를 참조하십시오.

## 빠른 전략

빠른 전략은 다음 작업을 수행합니다.

1. 표준 전략과 같이 각 테마에 대해 임의의 로케일이 하나씩 선택되고 이 로케일에 대한 모든 파일이 배포됩니다.
1. 테마의 다른 모든 로케일의 경우:

   1. 배포된 로케일을 재정의하는 파일이 정의되고 배포됩니다.
   1. 다른 모든 파일은 모든 로케일에 대해 유사한 것으로 간주되며 배포된 로케일에서 복사됩니다.

>[!INFO]
>
>_유사_&#x200B;이면 로케일, 테마 또는 영역에 독립적인 파일을 의미합니다. 이러한 파일에는 CSS, 이미지 및 글꼴이 포함될 수 있습니다.

이 방법을 사용하면 많은 파일이 복제되더라도 여러 로케일에 필요한 배포 시간을 최소화할 수 있습니다.

## 콤팩트 전략

압축 전략은 유사한 파일을 `base` 하위 디렉터리에 저장하여 파일 중복을 방지합니다.

가장 최적화된 결과를 위해 가능한 유사성에 대한 세 가지 범위(영역, 테마 및 로케일)가 할당됩니다. 이러한 범위의 모든 조합에 대해 `base` 하위 디렉터리가 만들어집니다.

파일은 다음 패턴에 따라 이러한 하위 디렉토리에 배포됩니다.

| 패턴 | 설명 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 특정 영역, 테마 및 로케일에 해당하는 파일 |
| `<area>/<theme>/default` | 특정 영역의 특정 테마의 모든 로케일에 대해 유사한 파일입니다. |
| `<area>/Magento/base/<locale>` | 특정 영역 및 로케일에 해당하는 파일이지만 모든 테마에 대해서는 비슷합니다. |
| `<area>/Magento/base/default` | 특정 영역에만 적용되지만 모든 테마 및 로케일에 대해 비슷합니다. |
| `base/Magento/base/<locale>` | 모든 영역 및 테마에 대해 유사하지만 특정 로케일에 해당하는 파일입니다. |
| `base/Magento/base/default` | 모든 영역, 테마 및 로케일에 대해 유사합니다. |

### 배포된 파일 매핑

컴팩트 전략에 사용된 배포 접근 방식은 기본 테마 및 로케일에서 파일이 상속됨을 의미합니다. 이러한 상속 관계는 영역, 테마 및 로케일의 각 조합에 대해 맵 파일에 저장됩니다. PHP 및 JS에 대한 별도의 맵 파일이 있습니다.

- `map.php`
- `requirejs-map.js`

`map.php`[`Magento\Framework\View\Asset\Repository`이(가) 올바른 URL을 빌드하는 데 ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 파일을 사용합니다.

`requirejs-map.js`은(는) RequireJS에 대한 `baseUrlResolver` 플러그인에서 사용됩니다.

`map.php`의 예:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

`requirejs-map.js`의 예:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 확장 개발자를 위한 팁

정적 보기 파일에 대한 URL을 작성하려면 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244)을(를) 사용합니다.

페이지 렌더링 중에 정적 파일을 찾을 수 없고 표시되지 않는 문제를 방지하기 위해 URL 연결을 사용하지 마십시오.
