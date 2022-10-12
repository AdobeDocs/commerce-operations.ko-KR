---
title: Adobe 개인 정보 JavaScript 라이브러리
description: Adobe Commerce 및 Magento Open Source에서 수집한 고객 개인 정보에 액세스하고 삭제하는 데 사용자 지정 도구를 사용하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Adobe 개인 정보 JavaScript 라이브러리

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

다음 [Adobe 개인 정보 JavaScript 라이브러리](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 는 개인 데이터에 액세스하고 삭제하는 프로세스를 만드는 데 도움이 되는 도구 세트입니다.

Adobe Commerce 및 Magento Open Source 데이터 추적 서비스는 다음과 같은 개인 정보 보호 규정에 적용되는 개인 정보를 저장할 수 있습니다 [일반 데이터 보호 규정(GDPR)](gdpr.md) 및 [캘리포니아 소비자 개인 정보 보호법(CCPA)](ccpa.md).

이 라이브러리는 개인 정보 보호 데이터 요청을 만들고, 각 제품의 구현에 보내고, 응답을 수집하기 위한 통합 함수 세트를 제공합니다. 이 라이브러리를 사용하여 이러한 데이터 추적 서비스에 의해 브라우저에 저장된 데이터를 검색하고 제거합니다.

## 설치

다음 방법 중 하나를 사용하여 라이브러리 파일을 다운로드합니다.

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

파일이 있으면 Adobe Commerce 및 Magento Open Source 인스턴스에 설치된 사용자 지정 모듈이나 테마에 파일을 추가해야 합니다. 다음 설명서에 설명된 지침을 따르십시오. [사용자 지정 JavaScript 사용](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) 이 작업을 수행할 주제입니다.

## 사용

AdobePrivacy JS 라이브러리는 브라우저에 저장된 ID 데이터를 관리하는 다양한 기능을 제공합니다.

`retrieveIdentities()`
: 서비스에서 찾을 수 없는 ID 배열과 함께 서비스의 ID 배열을 반환합니다

`removeIdentities()`
: 브라우저에서 ID를 제거하고 `isDeleteClientSide` 데이터를 삭제했는지 여부를 나타내는 부울 속성입니다.

`retrieveThenRemoveIdentities()`
: 이 함수는 `removeIdentities()` 에서는 일련의 ID를 검색하고 브라우저에서 제거합니다.

이러한 함수를 사용하는 방법에 대한 자세한 내용 및 예는 [공식 도서관 문서](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### 초기화

새 인스턴스 `AdobePrivacy` 구현 코드에서 AdobePrivacy JS 라이브러리를 사용하는 개체.

```js
var adobePrivacy = new AdobePrivacy({});
```

생성자는 인스턴스화 중에 매개 변수와 함께 구성 개체를 허용합니다.
자세한 내용은 [공식 도서관 문서](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) 를 참조하십시오.
