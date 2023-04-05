---
title: 정적 콘텐츠 캐시
description: 정적 콘텐츠 서명 및 기능을 활성화하거나 비활성화하는 방법을 이해합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 정적 콘텐츠 캐시

성능을 향상시키기 위해 Commerce는 `Expires` 이미지, JavaScript 및 CSS 파일과 같은 정적 리소스에 대한 헤더입니다.
설정 `Expires` 정적 리소스의 헤더는 브라우저에 해당 URL에서 리소스를 캐시하고 만료될 때까지 캐시된 버전을 제공하도록 알려줍니다.
이것은 흔한 일이다 [모범 사례](https://developer.yahoo.com/performance/rules.html#expires=) 정적 리소스를 캐시하는 데 사용됩니다.

브라우저가 정적 리소스를 캐시하고 서버에서 해당 리소스가 변경되면 새 버전을 다운로드할 수 있도록 브라우저 캐시를 지워야 합니다.
웹 사이트 관리자라면 브라우저 캐시를 수동으로 지우는 것이 작동하지만, 새 버전의 정적 리소스를 다운로드하려는 경우 사용자에게 적합한 요청이 아닙니다.

## 정적 콘텐츠 서명

정적 콘텐츠 서명은 정적 리소스에 대한 브라우저 캐시를 무효화할 수 있는 상거래 기능입니다.
Commerce에서는 정적 파일의 URL에 배포 버전을 추가하여 이 작업을 수행합니다.

다음은 버전으로 서명된 URL의 예입니다.

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

명령을 실행할 때 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 정적 콘텐츠를 배포하기 위해 Commerce가 배포 버전을 자동으로 변경합니다.
이렇게 하면 정적 파일의 URL이 변경되고 브라우저가 새 버전의 파일을 로드하게 됩니다.

Commerce에서는 기본적으로 이 기능을 사용할 수 있으며, Adobe은 이전 정적 리소스를 제공하는 브라우저와 관련된 문제를 방지하기 위해 이 기능을 사용하도록 설정하는 것이 좋습니다.

에서 이 기능에 대한 구성을 찾을 수 있습니다. [**[!UICONTROL Stores]**> 설정 > 구성 >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![정적 파일 설정](../../assets/configuration/static-files-settings.png)

상태를 확인합니다.

```bash
bin/magento config:show dev/static/sign
```

정적 콘텐츠 서명 활성화 또는 비활성화:

```bash
bin/magento config:set dev/static/sign <value>
```

위치 `<value>` 는 1(활성화됨) 또는 0(비활성화됨)입니다.

## 버전 서명

Commerce는 정적 리소스 전체에서 상대 URL의 무결성을 유지하기 위해 정적 보기 파일의 기본 URL 바로 뒤에 버전 서명을 경로 구성 요소로 추가합니다.
이렇게 하면 서명 값의 유무/존재 여부에 관계없이 브라우저가 해당 컨텐츠를 유지하면서 올바른 서명된 소스에 대한 상대 URL을 확인하도록 합니다.

브라우저가 서버에서 서명된 소스를 요청하면 서버는 URL rewrites를 사용하여 URL에서 서명 구성 요소를 제거합니다.

## 배포 중 사용

정적 리소스를 업그레이드하거나 수정한 후 `setup:static-content:deploy` 버전을 배포하고 정적 콘텐츠를 업데이트하기 위한 명령으로, 이렇게 하면 브라우저에서 업데이트된 리소스를 로드합니다.

별도의 서버에 코드를 배포하고 코드 리포지토리를 사용하여 프로덕션으로 이동하는 경우 다운타임을 줄이는 경우에도 파일을 추가해야 합니다 `pub/static/deployed_version.txt` 저장소에
이 파일에는 배포된 정적 컨텐츠에 대한 새 버전이 포함되어 있습니다.
