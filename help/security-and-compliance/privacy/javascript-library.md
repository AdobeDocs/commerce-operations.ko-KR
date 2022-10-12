---
title: 개인 정보 JavaScript 라이브러리
description: Adobe Commerce 및 Magento Open Source에서 수집한 고객 개인 정보에 액세스하고 삭제하는 데 사용자 지정 도구를 사용하는 방법을 알아봅니다.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# 개인 정보 JavaScript 라이브러리

개인 정보 JavaScript 라이브러리는 Adobe Commerce 및 Magento Open Source에서 수집한 개인 데이터에 액세스하고 삭제하는 프로세스를 만드는 데 도움이 되는 도구 세트입니다.

상거래 데이터 추적 서비스는 다음과 같은 개인 정보 보호 규정에 적용되는 개인 정보를 저장할 수 있습니다 [일반 데이터 보호 규정(GDPR)](gdpr.md) 및 [캘리포니아 소비자 개인 정보 보호법(CCPA)](ccpa.md).

이 라이브러리는 개인 정보 데이터 요청을 만들고 해당 응답을 수집하는 함수 집합을 제공합니다. 이 라이브러리를 사용하여 Adobe Commerce 및 Magento Open Source 데이터 추적 서비스에 의해 브라우저에 저장된 데이터를 검색하고 제거합니다.

>[!NOTE]
>
>If [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 이 활성화되어 있으면 Commerce는 쇼핑객이 동의하기 전까지 행동 데이터를 수집하지 않습니다. If [!UICONTROL **쿠키 제한 모드**] 이 비활성화되면 Commerce는 기본적으로 행동 데이터를 수집합니다.

## 설치

개인 정보 JavaScript 라이브러리는 다음 CDN 위치에서 사용할 수 있습니다. `commerce.adobe.net/magentoprivacy.js`

파일이 있으면 Adobe Commerce 또는 Magento Open Source 인스턴스에 설치된 사용자 지정 모듈이나 테마에 파일을 추가해야 합니다. 다음 설명서에 설명된 지침을 따르십시오. [사용자 지정 JavaScript 사용](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 이 작업을 수행할 주제입니다.

### 초기화

새 항목 가져오기 및 인스턴스화 `MagentoPrivacy` 개체 또는 사용 `window` 개인 정보 보호 JavaScript 함수에 액세스하기 위한 개체.

사용 예 `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

사용 예 `window`:

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
이 함수는 `isDeleted` 데이터를 삭제했는지 여부를 나타내는 부울 속성입니다.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
