---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 보안 개선 사항

현재까지 이러한 문제와 관련된 확인된 공격은 발생하지 않았습니다. 그러나 특정 취약성은 고객 정보에 액세스하거나 관리자 세션을 인수하는 데 잠재적으로 악용될 수 있습니다. 이러한 문제의 대부분은 공격자가 먼저 관리자에 대한 액세스 권한을 얻어야 합니다. 따라서 이러한 노력을 포함하되 이에 국한되지 않고 관리자를 보호하기 위해 필요한 모든 조치를 취해야 함을 알려드립니다.

* IP 허용 목록에 추가
* [이중 인증](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* VPN 사용
* 대신 고유한 위치 사용 `/admin`
* 올바른 암호 위생

이 릴리스의 보안 개선 사항은 최신 보안 모범 사례를 통해 규정 준수를 향상시킵니다.

* **생성되지 않은 캐시 키 동작 변경**:

   * 이제 블록에 대해 생성되지 않은 캐시 키에는 자동으로 생성되는 키의 접두사와 다른 접두사가 포함됩니다. (생성되지 않은 캐시 키는 템플릿 지시문 구문 또는 `setCacheKey` 또는 `setData` 메서드.)
   * 이제 블록의 생성되지 않은 캐시 키에는 문자, 숫자, 하이픈(-) 및 밑줄(_)만 사용해야 합니다.  <!-- AC-9831 -->

* **자동 생성된 쿠폰 코드 수 제한**. 이제 Commerce에서 자동으로 생성되는 쿠폰 코드 수를 제한합니다. 기본 최대값은 250,000입니다. 상인은 새 제품을 사용할 수 있습니다 **[!UICONTROL Code Quantity Limit]** 구성 옵션 (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)를 클릭하여 많은 쿠폰으로 시스템을 압도할 가능성을 방지할 수 있습니다. <!-- AC-8753 -->

* **기본 관리 URL 생성 프로세스의 최적화**. 기본 관리 URL의 생성은 무작위성의 증가에 맞게 최적화되므로 생성된 URL의 예측 가능성이 줄어듭니다. <!-- AC-9028 -->

* **SRI(Subresource Integrity) 지원이 추가됨** 결제 페이지에서 스크립트 무결성을 확인하기 위한 PCI 4.0 요구 사항을 준수합니다. SRI(Subresource Integrity) 지원은 로컬 파일 시스템에 있는 모든 JavaScript 자산에 무결성 해시를 제공합니다. 기본 SRI 기능은 관리자 및 상점 영역의 결제 페이지에서만 구현됩니다. 그러나 판매자는 기본 구성을 다른 페이지로 확장할 수 있습니다. 다음을 참조하십시오 [하위 리소스 무결성](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) 다음에서 _Commerce PHP 개발자 안내서_.<!--AC-1153-->

* **CSP(콘텐츠 보안 정책) 변경 사항**—PCI 4.0 요구 사항을 준수하는 Adobe Commerce CSP(콘텐츠 보안 정책)의 구성 업데이트 및 개선 사항입니다. 자세한 내용은 [컨텐츠 보안 정책](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 다음에서 _Commerce PHP 개발자 안내서_. <!--AC-11513-->

   * Commerce 관리 및 상점 영역의 결제 페이지에 대한 기본 CSP 구성은 이제 입니다. `restrict` 모드. 다른 모든 페이지의 경우 기본 구성은 입니다. `report-only` 모드.  2.4.7 이전 릴리스에서 CSP는에 구성되었습니다. `report-only` 모든 페이지의 모드.

   * CSP에서 인라인 스크립트를 실행할 수 있도록 임시 공급자를 추가했습니다. nonce 공급자는 각 요청에 대해 고유한 nonce 문자열을 쉽게 생성할 수 있습니다. 그러면 문자열이 CSP 헤더에 연결됩니다.

   * 관리자의 주문 만들기 페이지와 상점 첫 화면의 체크아웃 페이지에 대한 CSP 위반을 보고하도록 사용자 지정 URI를 구성하는 옵션이 추가되었습니다. 관리자에서 또는 URI를에 추가하여 구성을 추가할 수 있습니다 `config.xml` 파일.

     >[!NOTE]
     >
     >CSP 구성 업데이트 `restrict` 모드는 관리 및 상점 첫 화면의 결제 페이지에서 기존 인라인 스크립트를 차단할 수 있으며, 이로 인해 페이지가 로드될 때 다음과 같은 브라우저 오류가 발생합니다. `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 필수 스크립트를 허용하도록 화이트리스트 구성을 업데이트하여 이러한 오류를 수정합니다. 다음을 참조하십시오 [문제 해결](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) 다음에서 _Commerce PHP 개발자 안내서_.

* 새로운 전체 페이지 캐시 구성 설정을 사용하면 HTTP와 관련된 위험을 완화할 수 있습니다 `{BASE-URL}/page_cache/block/esi` 엔드포인트. 이 끝점은 상거래 레이아웃 핸들 및 블록 구조에서 제한되지 않고 동적으로 로드된 콘텐츠 조각을 지원합니다. 새로운 **[!UICONTROL Handles params size]** 구성 설정은 이 끝점의 값을 설정합니다. `handles` API당 허용되는 최대 핸들 수를 결정하는 매개 변수입니다. 이 속성의 기본값은 100입니다. 판매자는 관리자( )에서 이 값을 변경할 수 있습니다.**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). 다음을 참조하십시오 [Vannish를 사용하도록 Commerce 애플리케이션 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **REST 및 GraphQL API를 통해 전송되는 결제 정보에 대한 기본 요금 제한**. 상인은 이제 [속도 제한 구성](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) REST 및 GraphQL을 사용하여 전송된 결제 정보입니다. 이렇게 추가된 보호 계층은 카드 공격의 예방을 지원하고 한 번에 여러 신용카드 번호를 테스트하는 카드 공격의 양을 잠재적으로 줄입니다. 기존 REST 끝점의 기본 동작이 변경된 것입니다. 다음을 참조하십시오 [속도 제한](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* 의 기본 동작 [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL 쿼리 및 ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST 끝점이 변경되었습니다. 기본적으로 이제 API는 항상 반환됩니다 `true`. 판매자는 를 설정하여 원래 동작을 활성화할 수 있습니다. *[게스트 체크아웃 로그인 활성화](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* 관리 대상 옵션 `yes`를 사용하지만 그렇게 하면 인증되지 않은 사용자에게 고객 정보가 노출될 수 있습니다.
