---
title: 배포용 구성 파일
description: Commerce 애플리케이션 설치를 위한 구성 파일의 작동 방식을 이해합니다.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# 배포용 구성 파일

Adobe Commerce은 구성 요소를 쉽게 사용자 정의하고 구성 유형을 만들어 기본 기능을 확장할 수 있는 구성 파일을 제공합니다. 배포 구성 프로세스는 설치에 대한 공유 및 시스템별 구성으로 구성됩니다. Commerce의 배포 구성이 [`app/etc/config.php`](../reference/config-reference-configphp.md)과(와) [`app/etc/env.php`](../reference/config-reference-envphp.md) 사이에 나누어집니다.

- `app/etc/config.php`은(는) _공유_ 구성 파일입니다.
이 파일에는 설치된 모듈, 테마 및 언어 패키지 목록과 공유 구성 설정이 포함되어 있습니다.

  소스 제어에 체크 인하고 개발, 스테이징 및 프로덕션 시스템에서 사용합니다.

- `app/etc/env.php`에 설치 환경과 관련된 설정이 있습니다.

파일은 설치 중에 만들어지며 Commerce 응용 프로그램을 시작하는 데 필요하므로 `config.php` 및 `env.php`을(를) 모두 Commerce _배포 구성_&#x200B;이라고 합니다.

>[!INFO]
>
>[!DNL Commerce 2] 배포 구성은 [!DNL Magento 1.x]의 `local.xml`을(를) 대체합니다.

다른 [모듈 구성 파일](../reference/module-files.md)과 달리 Commerce 배포 구성은 초기화 중에 메모리에 로드되며 다른 파일과 병합되지 않으며 확장할 수 없습니다. (`config.php`과(와) `env.php`은(는) 서로 병합됩니다.)

## 배포 구성에 대한 세부 정보

`config.php` 및 `env.php`은(는) 기본적으로 구성 매개 변수와 값의 계층적 배열인 [다차원 연관 배열](https://www.w3schools.com:443/php/php_arrays.asp)을 반환하는 PHP 파일입니다.

이 배열의 최상위 수준에는 _구성 세그먼트_&#x200B;가 있습니다. 세그먼트에는 임의 키로 식별되는 임의 콘텐츠(스칼라 값 또는 중첩된 배열)가 있습니다. 여기서 키와 값 쌍은 모두 Commerce 프레임워크에 의해 정의됩니다.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php)은(는) 이러한 섹션에 대한 액세스 권한만 제공하지만 이를 확장할 수 없습니다.

다음 계층 수준에서 각 세그먼트의 항목은 비활성화된 모듈을 제외하고 모든 모듈의 구성 파일을 병합한 모듈 시퀀스 정의에 따라 순서가 지정됩니다.

다음 섹션에서는 배포 구성의 구조 및 내용에 대해 설명합니다.

- 설치된 모듈 관리
- 시스템별 구성

## 설치된 모듈 관리

`config.php` 파일에 설치된 모듈 목록이 있습니다. Adobe Commerce은 모듈 관리(설치, 제거, 활성화, 비활성화 또는 업그레이드)를 위한 명령줄 및 웹 기반 유틸리티를 모두 제공합니다.

예:

- 구성 요소 제거: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 구성 요소 상태 확인: [`bin/magento module:status`](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- 구성 요소 [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md)을(를) 활성화하거나 비활성화합니다.

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

값 `1` 또는 `0`은(는) 모듈의 사용 여부를 나타냅니다.

비활성화된 모듈은 Commerce 애플리케이션에서 인식되지 않습니다. 즉, 구성 병합, 종속성 삽입, 이벤트, 플러그인 등에 참여하지 않습니다. 비활성화된 모듈은 Storefront 또는 Admin을 수정하지 않으며 라우팅에 영향을 주지 않습니다.

비활성화된 모듈과 코드 베이스에 없는 모듈의 유일한 차이점은 비활성화된 모듈이 자동 로더에 의해 발견되고, 해당 클래스와 상수를 다른 코드에서 재사용할 수 있다는 것입니다.
