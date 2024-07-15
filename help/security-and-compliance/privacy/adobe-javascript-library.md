---
title: Adobe 개인 정보 보호 JavaScript 라이브러리
description: Adobe Commerce에서 수집한 고객 개인 정보에 액세스하고 삭제하는 데 사용자 지정 도구를 사용하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe 개인 정보 보호 JavaScript 라이브러리

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

[Adobe 개인 정보 JavaScript 라이브러리](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)는 개인 데이터에 액세스하고 삭제하는 프로세스를 만드는 데 도움이 되는 도구 집합입니다.

Adobe Commerce 데이터 추적 서비스는 [GDPR(일반 데이터 보호 규정)](gdpr.md) 및 [CCPA(캘리포니아 소비자 개인 정보 보호법)](ccpa.md)과 같은 개인 정보 보호 규정에 적용할 수 있는 개인 정보를 저장할 수 있습니다.

이 라이브러리는 개인 정보 보호 데이터 요청을 만들고, 각 제품의 구현에 보내고, 응답을 수집하기 위한 통합 함수 집합을 제공합니다. 이 라이브러리를 사용하여 이러한 데이터 추적 서비스로 브라우저에 저장된 데이터를 검색하고 제거합니다.

## 설치

다음 방법 중 하나를 사용하여 라이브러리 파일을 다운로드합니다.

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

파일이 있으면 Adobe Commerce 인스턴스에 설치된 사용자 지정 모듈 또는 테마에 추가해야 합니다. 이 작업을 수행하려면 [사용자 지정 JavaScript 사용](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 항목에 설명된 지침을 따르십시오.

## 사용

AdobePrivacy JS 라이브러리는 브라우저에 저장된 ID 데이터를 관리하기 위한 다양한 기능을 제공합니다.

`retrieveIdentities()`
: 서비스에서 찾을 수 없는 ID 배열과 함께 서비스의 ID 배열을 반환합니다.

`removeIdentities()`
: 브라우저에서 ID를 제거하고 `isDeleteClientSide` 부울 속성이 있는 ID 개체 배열을 반환하여 데이터가 삭제되었는지 여부를 나타냅니다.

`retrieveThenRemoveIdentities()`
: 이 함수는 ID 배열을 검색하고 브라우저에서 제거한다는 점에서 `removeIdentities()`과(와) 유사합니다.

이러한 함수 사용에 대한 자세한 내용과 예를 보려면 [공식 라이브러리 설명서](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)를 참조하십시오.

### 초기화

구현 코드에서 AdobePrivacy JS 라이브러리를 사용하려면 새 `AdobePrivacy` 개체를 인스턴스화합니다.

```js
var adobePrivacy = new AdobePrivacy({});
```

생성자는 인스턴스화하는 동안 매개 변수가 있는 구성 개체를 수락합니다.
이러한 구성 매개 변수 목록은 [공식 라이브러리 설명서](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html)를 참조하세요.
