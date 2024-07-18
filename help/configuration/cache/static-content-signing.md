---
title: 정적 콘텐츠 캐시
description: 정적 콘텐츠 서명 및 기능을 활성화하거나 비활성화하는 방법에 대해 알아봅니다.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 정적 콘텐츠 캐시

성능을 향상시키기 위해 Commerce에서는 이미지, JavaScript 및 CSS 파일과 같은 정적 리소스에 대해 `Expires` 헤더를 설정합니다.
정적 리소스에 `Expires` 헤더를 설정하면 브라우저가 해당 URL에서 리소스를 캐시하고 만료될 때까지 캐시된 버전을 제공하도록 합니다.
정적 리소스를 캐시하는 일반적인 [모범 사례](https://developer.yahoo.com/performance/rules.html#expires=)입니다.

브라우저가 정적 리소스를 캐시하고 서버에서 해당 리소스가 변경되면 새 버전을 다운로드할 수 있도록 브라우저 캐시를 지워야 합니다.
웹 사이트 관리자에게는 브라우저 캐시를 수동으로 지우는 작업이 가능하지만, 사용자가 새 버전의 정적 리소스를 다운로드하도록 할 때에는 이 작업이 적절하지 않습니다.

## 정적 콘텐츠 서명

정적 콘텐츠 서명은 정적 리소스에 대한 브라우저 캐시를 무효화할 수 있는 Commerce 기능입니다.
Commerce은 정적 파일의 URL에 배포 버전을 추가하여 이 작업을 수행합니다.

다음은 버전으로 서명된 URL의 예입니다.

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

[`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 명령을 실행하여 정적 콘텐츠를 배포하면 Commerce에서 배포 버전을 자동으로 변경합니다.
이렇게 하면 정적 파일의 URL이 변경되고 브라우저가 파일의 새 버전을 로드하게 됩니다.

Commerce은 기본적으로 이 기능을 활성화하며, Adobe은 이전 정적 리소스를 제공하는 브라우저와 관련된 문제를 방지하기 위해 이 기능을 활성화 상태로 유지하는 것을 권장합니다.

정적 콘텐츠 서명에 대한 구성은 [**[!UICONTROL Stores]**> 설정 > 구성 >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html)에 있습니다.

- **온-프레미스 전용**: 사이트가 [프로덕션 모드](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode)에서 **not**&#x200B;인 경우 이 구성을 사용할 수 있습니다.
- **Cloud**: 이 구성은 프로덕션 모드가 엄격히 적용되기 때문에 숨겨져 있습니다. 따라서 아래 표시된 대로 명령줄을 사용해야 합니다.

![정적 파일 설정](../../assets/configuration/static-files-settings.png)

상태 확인:

```bash
bin/magento config:show dev/static/sign
```

정적 콘텐츠 서명 활성화 또는 비활성화:

```bash
bin/magento config:set dev/static/sign <value>
```

여기서 `<value>`은(는) 1(활성화됨) 또는 0(비활성화됨)입니다.

## 버전 서명

Commerce은 정적 보기 파일의 기본 URL 바로 뒤에 버전 서명을 경로 구성 요소로 추가하여 정적 리소스에 있는 상대 URL의 무결성을 유지합니다.
또한 브라우저는 서명 값의 유무에 관계없이 콘텐츠를 유지하면서 올바른 서명 소스에 대한 상대 URL을 확인하게 됩니다.

브라우저가 서버에서 서명된 소스를 요청하면 서버는 URL 재작성을 사용하여 URL에서 서명 구성 요소를 제거합니다.

## 배포 중 사용

정적 리소스를 업그레이드하거나 수정한 후에는 `setup:static-content:deploy` 명령을 실행하여 버전을 배포하고 정적 콘텐츠를 업데이트해야 합니다. 이렇게 하면 브라우저에서 업데이트된 리소스를 로드하게 됩니다.

다운타임을 줄이기 위해 별도의 서버에 코드를 배포하고 코드 저장소를 사용하여 프로덕션으로 이동하는 경우 `pub/static/deployed_version.txt` 파일도 저장소에 추가해야 합니다.
이 파일에는 배포된 정적 콘텐츠의 새 버전이 포함되어 있습니다.
