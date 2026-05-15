---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Source 하이라이트(v2.4.9)

## v2.4.9의 주요 특징

Magento Open Source 2.4.9 릴리스에는 다음과 같은 사항이 적용됩니다.

### API

#### 스토어 보기 수준에서 제품을 업데이트할 때 REST API에서 제품 갤러리의 상속을 유지할 수 있는 가능성 추가

스토어 범위에서 REST API를 통해 제품을 업데이트하면 해당 범위의 제품 갤러리가 변경되지 않도록 media_gallery_entries가 페이로드에서 생략되거나 NULL로 설정된 경우 제품 이미지와 비디오가 글로벌 범위의 변경 사항을 상속하지 않습니다. 또한 이제 해당 필드를 NULL로 설정하여 REST API를 통해 제품 이미지 및 비디오에 대한 범위 상속을 복원할 수 있습니다.

_ACP2E-4358 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### 계정 영역을 통해 Google 지급 저장

Adobe Commerce 2.4.9에서 이제 Braintree에서 Google Pay Vault가 활성화되면 고객이 계정 영역을 통해 Google Pay 카드를 소산할 수 있습니다. 저장된 카드는 저장된 결제 방법 아래에 표시되며 체크아웃 시 향후 구매에 사용할 수 있으며 고객이 삭제할 수 있습니다. 이는 보관 지원을 Cards 및 PayPal을 넘어 Google Pay로 확장합니다.

_BUNDLE-3459_

#### RTAU(실시간 계정 업데이트 프로그램)

Adobe Commerce 2.4.9 for Braintree의 RTAU(Real Time Account Updater) 기능을 사용하면 카드가 만료되거나 교체될 때 저장된 Visa, Mastercard 및 Discover 카드 세부 사항이 자동으로 업데이트됩니다. 이렇게 하면 실패한 결제를 최소화하고, Magento Vault를 최신 상태로 유지하며, 지원되지 않는 유형(선불, Apple Pay, Google Pay)을 오류 없이 건너뜁니다.

_BUNDLE-3462_

#### Braintree 카드 결제에 대한 ELO 카드 유형 지원

Adobe Commerce 2.4.9에서 ELO 카드 유형에 대한 지원이 Braintree 결제에 추가되었습니다. 이제 관리자는 신용 카드 구성에서 ELO를 활성화할 수 있으며 고객은 체크아웃 시 ELO 카드를 사용하여 성공적으로 주문할 수 있으므로 Braintree을 통해 원활한 거래가 보장됩니다.

_BUNDLE-3464_

#### 청구서 지불

Adobe Commerce 2.4.9(Braintree 확장)의 경우 독일 구매자를 위한 새로운 현지 결제 방법 &quot;Pay On Invoice&quot;가 추가되었습니다. Pay On Invoice는 PayPal 계정이 없어도 고객이 먼저 물품을 수령하고 30일 이내에 송장을 결제할 수 있는 PayPal + Ratepay(&quot;Rechnungskauf mit Ratepay&quot;)에서 제공하는 지금 구매, 나중에 지급(BNPL) 옵션입니다. 즉석 결제가 아니기 때문에 주문 확정은 페이팔에서 서버측 웹후크로 구동됩니다.

_BUNDLE-3475_

#### Google Pay Express Pay Sheet에 오퍼 추가

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 이제 Google Pay Express Pay Sheet에서 프로모션/오퍼 코드를 지원합니다. 구매자는 Google Pay Sheet에서 직접 Magento 장바구니 프로모션을 적용, 조회 및 삭제할 수 있으므로, 익스프레스 체크아웃 고객이 표준 체크아웃 플로우와 동일한 할인 및 인센티브를 받을 수 있습니다.

_BUNDLE-3476_

#### Apple Pay Express Pay Sheet에 오퍼 추가

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 이제 Apple Pay Express Pay Sheet에서 프로모션/오퍼 코드를 지원합니다. 쇼핑객은 Apple Pay 시트 내에서 직접 쿠폰을 적용할 수 있으므로 익스프레스 체크아웃 사용자는 표준 체크아웃 플로우와 동일한 할인 및 캠페인의 혜택을 받을 수 있습니다.

_BUNDLE-3477_

#### Chrome 및 Firefox에서 Apple으로 결제

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 이제 Safari뿐만 아니라 Chrome 및 Firefox에서 Apple Pay를 사용할 수 있습니다. Apple Pay Express가 활성화되면 지원되는 상점 위치 전체에서 Apple Pay 버튼을 사용할 수 있으며 고객은 iPhone으로 코드를 스캔하여 결제를 완료합니다.

_BUNDLE-3478_

#### 서버 측 전달 콜백

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 PayPal Express 배송 콜백이 클라이언트측에서 서버측으로 이동되었습니다. 이렇게 하면 PayPal 모달에서 직접 동적 배송 방법, 실시간 비용 계산, 정확한 장바구니 수준 세부 정보를 제공하여 신뢰성을 향상시키고 연락처 모듈 지원, 앱 전환 흐름, Venmo Express와 같은 향후 기능을 위한 기반을 마련할 수 있습니다.

_BUNDLE-3479_

#### PayPal 연락처 모듈

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 미국 판매자를 위한 새로운 PayPal 연락처 모듈이 도입됩니다. 활성화된 경우 PayPal Express를 사용하는 구매자는 PayPal 양식 내에서 직접 판매자와 공유한 이메일 주소와 전화 번호를 빠른 흐름(PDP, 미니 카트, 장바구니, 체크아웃 익스프레스) 중에 보고 업데이트할 수 있습니다. 선택한 연락처 세부 정보는 Adobe Commerce 주문에 저장됩니다.

_BUNDLE-3480_

#### BLIK(현지 결제 방법)

Adobe Commerce 2.4.9의 Braintree 확장 프로그램의 경우 폴란드 쇼핑객을 위한 새로운 현지 결제 방법으로 BLIK가 추가되었습니다. 이를 통해 기존 Braintree 현지 결제 방식(LPM) 플로우 내에서 은행 기반의 안전한 BLIK 결제가 가능해져 폴란드 고객의 체크아웃 편의성과 전환율을 향상시킬 수 있다.

_BUNDLE-3481_

#### Cardinal 통합 업데이트 CSP 정책

Adobe Commerce 2.4.9의 Braintree 확장 기능의 경우 최신 Cardinal(3-D Secure) 통합 요구 사항을 지원하도록 CSP(콘텐츠 보안 정책)가 업데이트되었습니다. 이렇게 하면 3-D 보안 흐름 동안 사용되는 모든 카디날 호스팅 스크립트, iframe 및 관련 리소스를 브라우저의 CSP에서 허용하여 차단된 요청과 끊어진 요청/확인 경험을 방지할 수 있습니다.

_BUNDLE-3485_

### 프레임워크

#### 웹 토큰/jwt 프레임워크 라이브러리를 최신 주요 버전으로 업그레이드했습니다.

지속적인 보안 검토 프로세스의 일환으로 향후 호환성을 보장하고 강력한 보안 표준을 유지하기 위해 JWT 프레임워크의 최신 주요 릴리스를 평가했습니다. 이 릴리스에는 기존 기능에 영향을 주지 않습니다.

_AC-13209 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2bac8114) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/33b81f28)_

#### [파트2] - 사용 가능한 최신 버전으로 모든 js 라이브러리 및 npm 종속성 업데이트

composer 버전 지원은 composer 버전 2.2.x에만 해당됩니다. 이제 지원도 2.4.x 버전으로 확장되었습니다.

_AC-13792 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/19844aa0)_

#### PHP 기본 함수로 carlos-mg89/oauth 바꾸기

보안을 개선하고 외부 의존성을 줄이며 플랫폼 안정성을 높이기 위해 타사 carlos-mg89/oauth 라이브러리를 기본 PHP OAuth 기능으로 대체했습니다.

_AC-14075 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7b8064f7)_

#### jquery/uppy 업그레이드 및 라이브러리 최신 버전 업데이트

파일 업로드 기능을 개선하고 사용자 경험을 개선하며 Adobe Commerce 관리 인터페이스 및 프론트엔드 구성 요소에서 파일 처리의 보안 취약점을 해결하기 위해 Uppy 파일 업로드 라이브러리를 버전 4.13.4로 업그레이드했습니다.

_AC-14307 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/eb491c05)_

#### jquery-validate 라이브러리를 최신 버전으로 업그레이드

jQuery Validate 라이브러리를 버전 1.21.0으로 업그레이드하여 양식 유효성 검사 기능을 강화하고, 사용자 경험을 개선하고, 관리 및 프론트엔드 인터페이스 모두에서 모든 Adobe Commerce 양식에서 최신 브라우저 호환성을 유지할 수 있습니다.

_AC-14403 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### jquery-ui 라이브러리를 최신 버전으로 업그레이드

jQuery UI 라이브러리를 버전 1.14.1로 업그레이드하여 사용자 인터페이스 위젯을 개선하고, 접근성을 개선하며, 모든 Adobe Commerce 관리 및 프론트엔드 인터페이스 구성 요소에서 최신 브라우저 호환성을 보장합니다.

_AC-14417 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/77c589a6)_

#### less.js 라이브러리를 최신 버전으로 업그레이드

Less.js CSS 전처리기를 버전 4.2.2로 업그레이드하여 CSS 컴파일 성능을 높이고, 구문 지원을 개선하고, 모든 Adobe Commerce 프론트엔드 및 관리 테마에 걸쳐 테마 빌드 프로세스를 현대화했습니다.

_AC-14418 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### moment-timezone-with-data.js 라이브러리를 최신 버전으로 업그레이드

시간대 처리 기능을 강화하고, 최신 IANA 시간대 데이터베이스 변경 사항으로 시간대 데이터를 업데이트하며, 모든 Adobe Commerce 국제 및 다중 시간대 작업에서 날짜/시간 처리 정확도를 개선하기 위해 모멘트 시간대 라이브러리를 버전 0.5.43으로 업그레이드했습니다.

_AC-14419 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### underscore.js 라이브러리를 최신 버전으로 업그레이드

Underscore.js 유틸리티 라이브러리를 버전 1.13.7로 업그레이드하여 JavaScript 기능 프로그래밍 기능을 개선하고, 데이터 조작 성능을 개선하며, 모든 Adobe Commerce 프론트엔드 및 관리 인터페이스 구성 요소에서 최신 브라우저 호환성을 보장합니다.

_AC-14420 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### allure-framework/allure-phpunit 버전을 3으로 업데이트하고 2.4.9-alpha1에서 기본 종속성을 제거합니다.

Adobe Commerce 2.4.9에서 allure-framework/allure-phpunit 종속성이 PHP 8.4, PHP 8.5에 대한 지원을 추가하고 Allure 기반 테스트 보고 스택을 현대화하는 주요 버전 3으로 업그레이드되었습니다. 이전 Allure PHPUnit 버전에서 이전에 필요했던 기본 종속성이 적용 가능한 경우 제거되어 설정 및 유지 관리가 간소화되었습니다.

_AC-14548 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/87b8b34e)_

#### chart.js 종속성을 최신 버전으로 업그레이드

chart.js 종속성이 최신 버전 4.5.0으로 업그레이드되었습니다.

_AC-15133 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/657f983e)_

#### Adobe Commerce 2.4.9의 Symfony 7.4 LTS 및 PHP 8.5에 대한 공식 지원 추가

Adobe Commerce 2.4.9 플랫폼 업데이트의 일부로, magento/composer 패키지에 사용된 모든 Symfony 종속성이 최신 Symfony LTS 7.4 버전으로 업데이트되었습니다. 이렇게 하면 Commerce의 작성기 툴이 현재 Symfony LTS 라인에 맞추고 이전 Symfony 버전과 관련된 이전 종속성 제약 조건이 제거됩니다. 또한 Symfony 코어 클래스를 확장하는 모든 사용자 지정 클래스는 Adobe Commerce 2.4.9로 업그레이드하기 전에 최신 Symfony 요구 사항에 맞게 형식 선언 및 메서드 서명을 업데이트했습니다. 이렇게 하면 호환성 문제가 방지되고 업데이트된 프레임워크 구성 요소로 원활하게 전환할 수 있습니다.

_AC-15170 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Open Source에서 clearCart GraphQL 돌연변이를 사용할 수 있는지 확인합니다.

Adobe Commerce 2.4.9를 사용하면 이제 모든 오픈 Source 사용자가 clearCart GraphQL 돌연변이를 사용할 수 있습니다. 이전에는 이 돌연변이에 Adobe Commerce에서만 액세스할 수 있었지만, 이제 Open Source에 대한 표준 GraphQL 장바구니 기능의 일부입니다.
돌연변이에 대한 설명서가 Open Source for 버전 2.4.9의 가용성을 반영하도록 업데이트되었습니다.
[clearCart GraphQL 돌연변이 설명서](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/)를 참조하십시오.

_AC-16683 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9] 관리자 구성을 사용하여 게스트 및 고객 장바구니 논리 병합

쇼핑객이 로그인할 때 게스트 및 고객 카트를 병합하는 방법을 제어하기 위해 새로운 관리자 구성 옵션이 도입되었습니다. 이 향상된 기능을 통해 비즈니스 요구 사항에 가장 적합한 장바구니 병합 동작을 정의할 수 있습니다.

_LYNX-889_

#### [AC-2.4.9] 재고 부족 제품으로 이전 주문 받기

현재 품절된 경우에도 주문 내역에 제품 세부 정보가 표시됩니다.

_LYNX-913_

#### [AC-2.4.9] [CE] 누락된 GraphQL 돌연변이에 대해 ReCaptcha 구현

ReCaptcha 유효성 검사가 updateCustomer, updateCustomerV2 및 contactUs 돌연변이에 추가됩니다.

_LYNX-941_

### 기타

#### API/GraphQL에 대해 CAPTCHA/reCAPTCHA가 작동하지 않음

Adobe Commerce 2.4.9에서 계정 만들기 양식에 대해 CAPTCHA(또는 reCAPTCHA)가 활성화되면 이제 REST 및 GraphQL API를 통한 고객 계정 만들기에 대해 동일한 CAPTCHA 유효성 검사가 시행됩니다.

_AC-16245 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fd7f30ee)_

#### braintree 분기는 PHP 8.5 지원으로 업데이트해야 합니다.

Braintree 결제 확장 기능은 PHP 8.4와의 호환성을 유지하면서 최신 PHP 8.5 런타임을 지원하도록 업데이트되었습니다.

_BUNDLE-3493_

#### 위시리스트 지우기 작업 추가

일괄 작업을 지원하기 위해 새로운 clearWishlist 돌연변이를 추가하여 한 번의 작업으로 위시리스트에서 모든 항목을 제거할 수 있습니다.

_LYNX-790_

#### exchangeExternalCustomerToken 돌연변이 도입

통합 토큰을 통해 사용자를 인증하고 고객 토큰과 관련 고객 데이터를 모두 반환하는 새 GraphQL 돌연변이 exchangeExternalCustomerToken이 도입되었습니다

_LYNX-815_

#### [AC] 적용된 그룹, 세그먼트 및 장바구니 규칙 ID를 반환하는 GraphQL 쿼리를 도입합니다.

적용된 고객 그룹, 고객 세그먼트 및 장바구니 규칙의 인코딩된 uid를 검색하기 위해 노출된 GraphQL 쿼리입니다.

_LYNX-867_

#### [AC-2.4.9] OrderTotal.grand_total_excl_tax 필드 소개

새 필드 OrderTotal.grand_total_excl_tax가 GraphQL 주문 응답에 추가되었습니다. 이 필드에서는 세금을 제외한 주문의 총계를 제공하므로 API에서 직접 세금 독점 합계에 더 쉽게 액세스할 수 있습니다.

이점:

- GraphQL을 통해 모든 주문에 대한 세금을 제외한 총계를 쉽게 검색할 수 있습니다.
- 세금 전용 합계가 필요한 외부 시스템과의 통합을 간소화합니다.
- 클라이언트측의 사용자 정의 계산 필요성을 줄입니다.

_LYNX-892_

### PCI, 보안

#### 성능 효율성을 높이기 위해 SRI 스토리지 리팩터링

이제 SRI 해시 저장소는 하나의 큰 sri-hashes.json 대신 영역, 테마 및 로케일별로 별도의 파일을 생성합니다. 이 변경 사항을 사용하면 각 페이지에 대해 관련 해시 파일만 로드되므로 성능이 향상되고 여러 테마나 로케일이 있는 스토어의 메모리 사용량이 줄어듭니다.

_AC-16113 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/bc83cd2c)_

### 보안

#### 비동기/벌크 요청 성능 개선

APSB25-08 보안 패치 이후 도입된 벌크 비동기 웹 엔드포인트의 성능 저하를 수정하여 실행 시간을 늘립니다.

_AC-14078 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9a7352b7)_

#### 사용자당 하나의 활성화된 2FA 공급자만 구성해야 함

이제 관리자는 관리 패널에 액세스할 수 있도록 판매자의 활성화된 2FA 공급자 중 하나(예: Google Authenticator 또는 U2F)만 구성해야 합니다. 필요에 따라 나중에 활성화된 추가 공급자를 구성할 수 있습니다. 이전에는 여러 2FA 공급자가 활성화된 경우(예: Google Authenticator 및 U2F) 모든 관리 사용자가 로그인한 이전에 활성화된 모든 공급자를 구성해야 했습니다. 이로 인해 모든 요소(예: U2F용 하드웨어 키)에 액세스할 수 없는 사용자가 마찰을 겪게 되었습니다.

_AC-8253 - [GitHub 코드 기여](https://github.com/magento/security-package/commit/71e7936b)_
