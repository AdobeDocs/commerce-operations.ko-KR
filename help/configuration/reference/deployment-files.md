---
title: 배포용 구성 파일
description: Commerce 응용 프로그램 설치에 구성 파일이 작동하는 방식을 이해합니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# 배포용 구성 파일

Adobe Commerce에서는 구성 요소를 쉽게 사용자 지정하고 구성 유형을 만들어 기본 기능을 확장할 수 있는 구성 파일을 제공합니다. 배포 구성 프로세스는 설치에 대한 공유 및 시스템별 구성으로 구성됩니다. 상거래 배포 구성이 [`app/etc/config.php`](../reference/config-reference-configphp.md) 및 [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` 은 _공유_ 구성 파일.
이 파일에는 설치된 모듈, 테마 및 언어 패키지 목록이 들어 있습니다. 및 공유 구성 설정을 구성합니다.

   이 파일을 체크 인하여 소스 제어 및 개발, 스테이징 및 프로덕션 시스템에서 사용합니다.

   2.2 릴리스부터 `app/etc/config.php` 파일이 더 이상 `.gitignore` 파일.
이것은 용이하게 하기 위해 행해졌다 [파이프라인 배포](../deployment/technical-details.md).

- `app/etc/env.php` 설치 환경에 해당하는 설정이 포함되어 있습니다.

함께 `config.php` 및 `env.php` 상거래라고 합니다 _배포 구성_ 설치하는 동안 파일을 만들고 Commerce 응용 프로그램을 시작해야 하기 때문입니다.

>[!INFO]
>
>다음 [!DNL Commerce 2] 배포 구성 대체 `local.xml` in [!DNL Magento 1.x].

다른 것과는 달리 [모듈 구성 파일](../reference/module-files.md), 초기화 중에 상거래 배포 구성이 메모리에 로드되고, 다른 파일과 병합되지 않으며, 확장할 수 없습니다. (`config.php` 및 `env.php` 그러나 는 서로 병합됩니다.

## 배포 구성에 대한 세부 사항

`config.php` 및 `env.php` 는 [다차원 연관 배열](https://www.w3schools.com:443/php/php_arrays.asp)기본적으로 구성 매개 변수와 값의 계층적 배열입니다.

이 스토리지의 최상위 레벨은 다음과 같습니다 _구성 세그먼트_. 세그먼트에는 임의의 키로 구분되는 임의의 콘텐츠(스칼라 값 또는 중첩 배열)가 있으며, 이 경우 키와 값 쌍이 모두 상거래 프레임워크로 정의됩니다.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) 는 이러한 섹션에 대한 액세스 권한만 제공하며 확장을 허용하지 않습니다.

다음 계층 수준에서 각 세그먼트의 항목은 [모듈](https://glossary.magento.com/module) 비활성화된 모듈을 제외하고 모든 모듈의 구성 파일을 병합하여 얻은 시퀀스 정의입니다.

다음 섹션에서는 배포 구성의 구조 및 내용에 대해 설명합니다.

- 설치된 모듈 관리
- 시스템별 구성

## 설치된 모듈 관리

다음 `config.php` 파일에 설치된 모듈 목록이 들어 있습니다. Adobe Commerce은 모듈 관리(설치, 제거, 활성화, 비활성화 또는 업그레이드)를 위한 명령줄 및 웹 기반 유틸리티를 모두 제공합니다.

예:

- 구성 요소 제거: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 구성 요소의 상태 확인: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- 구성 요소 활성화 또는 비활성화: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

값 `1` 또는 `0` 모듈의 활성화 여부를 나타냅니다.

비활성화된 모듈이 상거래 응용 프로그램에서 인식되지 않습니다. 즉, 종속성 주입, 이벤트, 플러그인 등에서 병합 구성에 참여하지 않습니다. 비활성화된 모듈은 [상점](https://glossary.magento.com/storefront) 또는 [관리](https://glossary.magento.com/admin) 라우팅에는 영향을 주지 않습니다.

상기 코드 베이스에 있는 비활성화된 모듈과 결석모듈의 유일한 실용적 차이는 자동로드기에 의해 비활성화된 모듈을 찾고, 상수를 다른 코드에서 재사용할 수 있다는 것이다.
