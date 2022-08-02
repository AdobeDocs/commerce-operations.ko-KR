---
title: 정적 보기 파일에 대한 배포 전략
description: Commerce 응용 프로그램의 배포 전략에 대해 읽어 보십시오.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 정적 보기 파일에 대한 배포 전략

정적 보기 파일을 배포할 때 사용 가능한 세 가지 전략 중 하나를 선택할 수 있습니다. 각 사용자는 다양한 사용 사례에 대해 최적의 배포 결과를 제공합니다.

- [표준](#standard-strategy): 일반 배포 프로세스.
- [빠른](#quick-strategy) (_기본_): 둘 이상의 로케일에 대한 파일을 배포할 때 배포에 필요한 시간을 최소화합니다.
- [컴팩트](#compact-strategy): 게시된 보기 파일에서 차지하는 공간을 최소화합니다.

다음 섹션에서는 각 전략의 구현 세부 사항과 기능에 대해 설명합니다.

## 표준 전략

표준 전략을 사용하면 모든 패키지에 대한 모든 정적 보기 파일이 배포되어, 즉 [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

자세한 내용은 [정적 보기 파일 배포](../cli/static-view-file-deployment.md).

## 빠른 전략

빠른 전략은 다음 작업을 수행합니다.

1. 각 테마에 대해 하나의 임의 로케일이 선택되고 표준 전략과 같이 이 로케일에 대한 모든 파일이 배포됩니다.
1. 테마의 다른 모든 로케일:

   1. 배포된 로케일을 재정의하는 파일이 정의 및 배포됩니다.
   1. 다른 모든 파일은 모든 로케일에 대해 유사한 것으로 간주되며 배포된 로케일에서 복사됩니다.

>[!INFO]
>
>기준 _유사_&#x200B;즉, 로케일, 테마 또는 영역과 독립적인 파일을 의미합니다. 이러한 파일에는 CSS, 이미지 및 글꼴이 포함될 수 있습니다.

이 방법은 많은 파일이 복제되지만 여러 로케일에 필요한 배포 시간을 최소화합니다.

## 컴팩트한 전략

이러한 압축 전략은 유사한 파일을 `base` 하위 디렉토리.

가장 최적화된 결과의 경우 가능한 유사성에 대한 세 개의 범위가 할당됩니다. 영역, 테마 및 로케일. 다음 `base` 하위 디렉터리는 이러한 범위의 모든 조합에 대해 만들어집니다.

파일은 다음 패턴에 따라 이러한 하위 디렉토리에 배포됩니다.

| 패턴 | 설명 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 특정 영역, 테마 및 로케일에 대한 파일 |
| `<area>/<theme>/default` | 특정 영역의 특정 테마의 모든 로케일에 대해 유사한 파일입니다. |
| `<area>/Magento/base/<locale>` | 특정 영역 및 로케일에 대한 파일이지만 모든 테마에 대해 비슷합니다. |
| `<area>/Magento/base/default` | 특정 영역에만 해당하는 파일이지만 모든 테마 및 로케일에 대해 비슷합니다. |
| `base/Magento/base/<locale>` | 파일은 모든 영역 및 테마에 대해 유사하지만 특정 로케일에 따라 다릅니다. |
| `base/Magento/base/default` | 모든 영역, 테마 및 로케일에 대해 유사합니다. |

### 배포된 파일 매핑

컴팩트한 전략에 사용되는 배포 방법은 파일이 기본 테마 및 로케일에서 상속됨을 의미합니다. 이러한 상속 관계는 영역, 테마 및 로케일의 각 조합에 대한 맵 파일에 저장됩니다. PHP 및 JS에 대한 별도의 맵 파일이 있습니다.

- `map.php`
- `requirejs-map.js`

다음 `map.php` 파일이 다음 사용자에 의해 사용됩니다. [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 올바른 URL을 빌드하려면 다음을 수행하십시오.

다음 `requirejs-map.js` 이 `baseUrlResolver` requireJS에 대한 플러그인입니다.

예 `map.php`:

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

예 `requirejs-map.js`:

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

정적 보기 파일에 대한 URL을 빌드하려면 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

페이지 렌더링 중에 정적 파일을 찾을 수 없거나 표시되지 않는 문제를 방지하기 위해 URL 연결을 사용하지 마십시오.
