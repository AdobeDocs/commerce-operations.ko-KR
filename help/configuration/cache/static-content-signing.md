---
title: 정적 콘텐츠 캐시
description: 정적 콘텐츠 서명 및 기능을 활성화하거나 비활성화하는 방법에 대해 알아봅니다.
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 정적 콘텐츠 캐시

성능을 향상시키기 위해 Commerce에서는 `Expires` 이미지, JavaScript 및 CSS 파일과 같은 정적 리소스에 대한 헤더입니다.
설정 `Expires` 정적 리소스의 헤더는 브라우저가 해당 URL에서 리소스를 캐시하고 만료될 때까지 캐시된 버전을 제공하도록 지시합니다.
일반적입니다. [모범 사례](https://developer.yahoo.com/performance/rules.html#expires=) 정적 리소스를 캐시합니다.

브라우저가 정적 리소스를 캐시하고 서버에서 해당 리소스가 변경되면 새 버전을 다운로드할 수 있도록 브라우저 캐시를 지워야 합니다.
웹 사이트 관리자에게는 브라우저 캐시를 수동으로 지우는 작업이 가능하지만, 사용자가 새 버전의 정적 리소스를 다운로드하도록 할 때에는 이 작업이 적절하지 않습니다.

## 정적 콘텐츠 서명

정적 콘텐츠 서명은 정적 리소스에 대한 브라우저 캐시를 무효화할 수 있는 상거래 기능입니다.
Commerce는 정적 파일의 URL에 배포 버전을 추가하여 이 작업을 수행합니다.

다음은 버전으로 서명된 URL의 예입니다.

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

명령을 실행할 때 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 정적 콘텐츠를 배포하기 위해 Commerce는 배포 버전을 자동으로 변경합니다.
이렇게 하면 정적 파일의 URL이 변경되고 브라우저가 파일의 새 버전을 로드하게 됩니다.

Commerce에서는 기본적으로 이 기능을 사용할 수 있으며, Adobe은 브라우저가 이전 정적 리소스를 제공하는 것과 관련된 문제를 방지하기 위해 이 기능을 활성화 상태로 유지하는 것을 권장합니다.

이 기능에 대한 구성은에서 찾을 수 있습니다. [**[!UICONTROL Stores]**> 설정 > 구성 >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![정적 파일 설정](../../assets/configuration/static-files-settings.png)

상태 확인:

```bash
bin/magento config:show dev/static/sign
```

정적 콘텐츠 서명 활성화 또는 비활성화:

```bash
bin/magento config:set dev/static/sign <value>
```

위치 `<value>` 는 1(활성화됨) 또는 0(비활성화됨)입니다.

## 버전 서명

Commerce는 정적 보기 파일의 기본 URL 바로 뒤에 버전 서명을 경로 구성 요소로 추가하여 정적 리소스에 있는 상대 URL의 무결성을 유지합니다.
또한 브라우저는 서명 값의 유무에 관계없이 콘텐츠를 유지하면서 올바른 서명 소스에 대한 상대 URL을 확인하게 됩니다.

브라우저가 서버에서 서명된 소스를 요청하면 서버는 URL 재작성을 사용하여 URL에서 서명 구성 요소를 제거합니다.

## 배포 중 사용

정적 리소스를 업그레이드하거나 수정한 후에는 `setup:static-content:deploy` 버전을 배포하고 정적 콘텐츠를 업데이트하는 명령입니다. 이렇게 하면 브라우저가 업데이트된 리소스를 로드합니다.

다운타임을 줄이기 위해 별도의 서버에 코드를 배포하고 코드 저장소를 사용하여 프로덕션으로 이동하는 경우 파일도 추가해야 합니다 `pub/static/deployed_version.txt` 리포지토리에.
이 파일에는 배포된 정적 콘텐츠의 새 버전이 포함되어 있습니다.
