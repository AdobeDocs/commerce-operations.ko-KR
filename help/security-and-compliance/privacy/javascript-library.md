---
title: 개인 정보 JavaScript 라이브러리
description: Adobe Commerce에서 수집한 고객 개인 정보에 액세스하고 삭제하는 데 사용자 지정 도구를 사용하는 방법을 알아봅니다.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 개인 정보 JavaScript 라이브러리

개인 정보 JavaScript 라이브러리는 Adobe Commerce에서 수집한 개인 데이터에 액세스하고 삭제하는 프로세스를 만드는 데 도움이 되는 도구 세트입니다.

Commerce 데이터 추적 서비스는 [GDPR(일반 데이터 보호 규정)](gdpr.md) 및 [CCPA(캘리포니아 소비자 개인 정보 보호법)](ccpa.md)과 같은 개인 정보 보호 규정에 적용할 수 있는 개인 정보를 저장할 수 있습니다.

이 라이브러리는 개인 정보 보호 데이터 요청을 만들고 해당 응답을 수집하기 위한 함수 집합을 제공합니다. 이 라이브러리를 사용하여 Adobe Commerce 데이터 추적 서비스에서 브라우저에 저장된 데이터를 검색하고 제거합니다.

>[!NOTE]
>
>[쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html)가 활성화된 경우, Commerce은 구매자가 동의할 때까지 행동 데이터를 수집하지 않습니다. [!UICONTROL **쿠키 제한 모드**]&#x200B;를 사용하지 않도록 설정하면 Commerce에서 기본적으로 동작 데이터를 수집합니다.

## 설치

CDN 위치 `commerce.adobe.net/magentoprivacy.js`에서 개인 정보 JavaScript 라이브러리를 사용할 수 있습니다.

파일이 있으면 Adobe Commerce 인스턴스에 설치된 사용자 지정 모듈 또는 테마에 추가해야 합니다. 이 작업을 수행하려면 [사용자 지정 JavaScript 사용](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 항목에 설명된 지침을 따르십시오.

### 초기화

새 `MagentoPrivacy` 개체를 가져와서 인스턴스화하거나 `window` 개체를 사용하여 개인 정보 보호 JavaScript 함수에 액세스합니다.

`import` 사용 예:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

`window` 사용 예:

```js
const magePriv = new window.MagentoPrivacy()
```

## 사용

개인 정보 JS 라이브러리는 브라우저에 저장된 ID 데이터를 관리하는 다양한 기능을 제공합니다.

`retrieveIdentity()`
: 브라우저의 서비스에서 ID 개체에 대한 JavaScript 약속을 반환합니다.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: 브라우저의 서비스에서 ID 데이터를 제거합니다.
이 함수는 데이터가 삭제되었는지 여부를 나타내는 `isDeleted` 부울 속성이 있는 ID 개체에 대한 JavaScript 약속을 반환합니다.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
