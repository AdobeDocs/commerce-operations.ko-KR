---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 보안 개선 사항

* **SRI(Subresource Integrity) 지원이 추가됨** 결제 페이지에서 스크립트 무결성을 확인하기 위한 PCI 4.0 요구 사항을 준수합니다. SRI(Subresource Integrity) 지원은 로컬 파일 시스템에 있는 모든 JavaScript 자산에 무결성 해시를 제공합니다. 기본 SRI 기능은 관리자 및 상점 영역의 결제 페이지에서만 구현됩니다. 그러나 판매자는 기본 구성을 다른 페이지로 확장할 수 있습니다. [Commerce PHP 개발자 안내서](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/)의 _하위 리소스 무결성_&#x200B;을 참조하십시오.<!--AC-1153-->

* **CSP(콘텐츠 보안 정책)에 대한 변경 사항**—PCI 4.0 요구 사항을 준수하도록 Adobe Commerce CSP(콘텐츠 보안 정책)에 대한 구성 업데이트 및 개선 사항입니다. 자세한 내용은 [Commerce PHP 개발자 안내서](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)의 _콘텐츠 보안 정책_&#x200B;을 참조하십시오. <!--AC-11513-->

   * Commerce 관리 및 상점 영역의 결제 페이지에 대한 기본 CSP 구성은 이제 `restrict` 모드입니다. 다른 모든 페이지의 경우 기본 구성은 `report-only` 모드입니다.  2.4.7 이전 릴리스에서 CSP는 모든 페이지에 대해 `report-only` 모드로 구성되었습니다.

   * CSP에서 인라인 스크립트를 실행할 수 있도록 임시 공급자를 추가했습니다. nonce 공급자는 각 요청에 대해 고유한 nonce 문자열을 쉽게 생성할 수 있습니다. 그러면 문자열이 CSP 헤더에 연결됩니다.

   * 관리자의 주문 만들기 페이지와 상점 첫 화면의 체크아웃 페이지에 대한 CSP 위반을 보고하도록 사용자 지정 URI를 구성하는 옵션이 추가되었습니다. 관리자 또는 URI를 `config.xml` 파일에 추가하여 구성을 추가할 수 있습니다.

     >[!NOTE]
     >
     >CSP 구성을 `restrict` 모드로 업데이트하면 Admin 및 Storefront의 결제 페이지에서 기존 인라인 스크립트가 차단될 수 있으며, 이로 인해 페이지가 로드될 때 다음 브라우저 오류가 발생합니다. `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 필수 스크립트를 허용하도록 화이트리스트 구성을 업데이트하여 이러한 오류를 수정합니다. [Commerce PHP 개발자 안내서](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting)의 _문제 해결_&#x200B;을 참조하십시오.
