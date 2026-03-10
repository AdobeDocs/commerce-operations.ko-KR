---
source-git-commit: fd421e8c2455a2b45d3f3cc93573d2a609e4936d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Adobe Commerce 하이라이트(v2.4.9-beta1)

## v2.4.9-beta1의 주요 특징

Adobe Commerce 2.4.9-beta1 릴리스에는 다음과 같은 사항이 적용됩니다.

### API

#### 스토어 보기 수준에서 REST API 제품 갤러리 상속 제어

스토어 범위에서 REST API를 통해 제품을 업데이트하면 `media_gallery_entries`이(가) 페이로드에서 생략되거나 `NULL`(으)로 설정된 경우 더 이상 제품 이미지 및 비디오가 글로벌 범위에서 변경 사항을 상속하지 않습니다. 이제 해당 필드를 `NULL`(으)로 설정하여 REST API를 통해 제품 이미지 및 비디오에 대한 범위 상속을 복원할 수도 있습니다.

_ACP2E-4358 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 관리자 UI

#### 카탈로그 가격 규칙 그리드에 대한 작업 메뉴

이제 Commerce 관리자의 카탈로그 가격 규칙 그리드에 작업 메뉴가 포함되어 있어, 판매자는 한 번에 여러 카탈로그 가격 규칙을 활성화, 비활성화 또는 삭제할 수 있습니다. 이렇게 하면 장바구니 가격 규칙에 사용할 수 있는 기존 대량 작업에 맞춰 카탈로그 가격 규칙 관리를 가져오므로 큰 규칙 세트를 관리하는 데 필요한 시간을 크게 줄일 수 있습니다.

_AC-13916_

#### 콘텐츠 스테이징을 위한 모바일 보기 미리 보기

이제 관리자의 스테이징 미리 보기 기능을 사용하여 브라우저에서 시뮬레이션된 모바일 장치 미리 보기를 정확하게 렌더링하여 모바일 장치에 스테이징 업데이트가 표시되는 방식을 시각적으로 나타낼 수 있습니다.

_ACP2E-3397 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### 빠른 체크아웃

- **Google Pay Express Pay Sheet의 프로모션 오퍼**

  이제 Google Pay Express Pay Sheet에서 프로모션 및 오퍼 코드를 지원합니다. 구매자는 Google Pay Sheet에서 직접 Commerce 장바구니 프로모션을 적용, 조회 및 삭제할 수 있으므로, 익스프레스 체크아웃 고객이 표준 체크아웃 플로우와 동일한 할인 및 인센티브를 받을 수 있습니다.

  _BUNDLE-3476_

- **Apple Pay Express Pay Sheet의 프로모션 오퍼**

  이제 Apple Pay Express Pay Sheet에서 프로모션 및 오퍼 코드를 지원합니다. 쇼핑객은 Apple Pay 시트 내에서 직접 쿠폰을 적용할 수 있으므로 익스프레스 체크아웃 사용자는 표준 체크아웃 플로우와 동일한 할인 및 캠페인의 혜택을 받을 수 있습니다.

  _BUNDLE-3477_

- **Chrome 및 Firefox에서 Apple 결제**

  이제 Apple 페이는 Safari뿐만 아니라 Chrome 및 Firefox에서 사용할 수 있습니다. Apple Pay Express가 활성화되면 지원되는 상점 위치 전체에서 Apple Pay 버튼을 사용할 수 있으며 고객은 iPhone으로 코드를 스캔하여 결제를 완료합니다.

  _BUNDLE-3478_

- **PayPal Express용 서버측 전달 콜백**

  PayPal Express 배송 콜백이 클라이언트측에서 서버측으로 이동되었습니다. 이렇게 하면 PayPal 모달에서 직접 동적 배송 방법, 실시간 비용 계산, 정확한 장바구니 수준 세부 정보를 제공하여 신뢰성을 향상시키고 연락처 모듈 지원, 앱 전환 흐름, Venmo Express와 같은 향후 기능을 위한 기반을 마련할 수 있습니다.

  _BUNDLE-3479_

- **미국 판매자 익스프레스 체크아웃을 위한 PayPal 연락처 모듈**

  미국 상인을 위한 새로운 PayPal 연락처 모듈이 도입되었습니다. 활성화된 경우 PayPal Express를 사용하는 구매자는 PayPal 양식 내에서 직접 판매자와 공유한 이메일 주소와 전화 번호를 빠른 흐름(PDP, 미니 카트, 장바구니, 체크아웃 익스프레스) 중에 보고 업데이트할 수 있습니다. 선택한 연락처 세부 정보는 Commerce 주문에 저장됩니다.

  _BUNDLE-3480_

#### 결제 방법

- **Braintree 결제에 대한 ELO 카드 유형 지원**

  Braintree 결제에 ELO 카드 유형에 대한 지원을 추가했습니다. 이제 관리자는 신용 카드 구성에서 ELO를 활성화할 수 있으며 고객은 체크아웃 시 ELO 카드를 사용하여 성공적으로 주문할 수 있으므로 Braintree을 통해 원활한 거래가 보장됩니다.

  _BUNDLE-3464_

- **폴란드 쇼핑객을 위한 현지 결제 방법**

  폴란드 쇼핑객을 위한 새로운 현지 결제 방법으로 BLIK를 추가했습니다. 이를 통해 기존 Braintree 현지 결제 방식(LPM) 플로우 내에서 은행 기반의 안전한 BLIK 결제가 가능해져 폴란드 고객의 체크아웃 편의성과 전환율을 향상시킬 수 있다.

  _BUNDLE-3481_

- **청구서 지불 - 새로운 독일용 BNPL 지불 방법**

  새로운 현지 결제 방법인 독일 구매자를 위한 청구서 지불(Pay On Invoice)이 추가되었습니다. Pay On Invoice는 PayPal 및 Ratepay(&quot;Rechnungskauf mit Ratepay&quot;)에서 제공하는 지금 구매, 나중에 지급(BNPL) 옵션으로, PayPal 계정이 없어도 고객이 먼저 물품을 수령하고 30일 이내에 송장을 지급할 수 있습니다. 즉시 결제가 아니기 때문에 주문 확정은 페이팔에서 서버측 웹후크로 구동됩니다.

  _BUNDLE-3475_

#### 카드 보관

- **계정 영역을 통해 Google 결제 저장**

  이제 Braintree에서 Google Pay Vault가 활성화되면 고객은 계정 영역을 통해 Google Pay 카드를 소산할 수 있습니다. 저장된 카드는 저장된 결제 방법 아래에 표시되며 체크아웃 시 향후 구매에 사용할 수 있으며 고객이 삭제할 수 있습니다. 이는 보관 지원을 Cards 및 PayPal을 넘어 Google Pay로 확장합니다.

  _BUNDLE-3459_

- **Braintree 저장 카드용 RTAU(실시간 계정 업데이트 프로그램)**

  Braintree에 추가된 RTAU(Real-Time Account Updater) 기능을 사용하면 카드 만료 또는 교체 시 저장된 Visa, Mastercard 및 Discover 카드 세부 사항이 자동으로 업데이트됩니다. 이렇게 하면 실패한 결제를 최소화하고, Commerce Vault를 최신 상태로 유지하며, 지원되지 않는 유형(선불, Apple Pay, Google Pay)을 오류 없이 건너뜁니다.

  _BUNDLE-3462_

#### 관리 도구

- **Braintree 포털에 Commerce 주문 연결**

  이제 Braintree 포털 링크가 Commerce 관리자의 주문 세부 사항에 추가됩니다. 이 링크를 클릭하면 Braintree 주문의 판매자 ID 및 거래 ID를 사용하여 Commerce 포털(새 탭)에서 관련 거래가 열립니다. 이렇게 하면 두 시스템에 별도로 로그인하지 않고도 직접 상호 참조할 수 있습니다.

  _BUNDLE-3461_

#### 보안 및 호환성

- 3차원 보안을 위한 **카디날 통합 콘텐츠 보안 정책 업데이트**

  CSP(콘텐츠 보안 정책)가 최신 Cardinal (3-D Secure) 통합 요구 사항을 지원하도록 업데이트되었습니다. 이렇게 하면 3-D 보안 흐름 동안 사용되는 모든 카디날 호스팅 스크립트, iframe 및 관련 리소스를 브라우저의 CSP에서 허용하여 차단된 요청과 끊어진 챌린지 또는 확인 경험을 방지할 수 있습니다.

  _BUNDLE-3485_

- **Braintree 결제 확장 프로그램 PHP 8.5 호환성**

  Braintree 결제 확장 기능이 PHP 8.4와의 호환성을 유지하면서 PHP 8.5 런타임을 지원하도록 업데이트되었습니다.

  _BUNDLE-3493_

### 플랫폼 및 인프라

#### OpenSearch 3.x 지원

Adobe Commerce 2.4.9-beta1은 OpenSearch 3.x와 완전히 호환됩니다. 이 업데이트는 OpenSearch 2.x와의 이전 버전과의 호환성을 유지하면서 성능, 보안 및 장기 지원 향상 효과를 누릴 수 있도록 해 줍니다.

_AC-11846_

#### 전체 Valkey 8.x 지원

Adobe Commerce 2.4.9-beta1은 Redis와의 전체 CLI 명령 패리티를 포함하여 Redis 호환 캐시 백엔드로 Valkey 8.x에 대한 포괄적인 지원을 추가합니다. 원활한 Valkey 설정을 위해 관리 및 클라우드 구성 옵션이 업데이트되었습니다. 이 지원은 Redis 7.2의 지원 종료 및 라이선스 변경에 따라 이루어지며, 판매자는 Commerce 릴리스 라인 2.4.5부터 2.4.9-Beta1까지 Redis에 대한 안정적이고 완전히 지원되는 대안을 제공합니다.

_AC-14103, AC-14604_

#### RabbitMQ를 대체하는 Apache ActiveMQ Artemis 지원

RabbitMQ 4와 관련된 지원 종료 위험에 의해 구동되는 RabbitMQ에 대한 전략적 대안으로 Apache ActiveMQ Artemis에 대한 지원이 추가되었습니다. 이제 ActiveMQ Artemis는 클라우드 기반 배포용 Commerce ActiveMQ가 포함된 Adobe Commerce Cloud를 포함하여 AWS 릴리스 라인 2.4.6부터 2.4.9 베타1까지 완전히 지원되며, 큐 소비자 및 게시자를 위한 STOMP 구성을 지원합니다. 기존 RabbitMQ 4 설치는 현재 메시지 대기열 서비스를 계속 사용하고자 하는 가맹점을 위해 호환됩니다.

_AC-14558_

### PHP 및 Composer

#### PHP 8.5 호환성

Adobe Commerce 2.4.9-beta1부터 이 플랫폼은 PHP 8.5와 완벽하게 호환되며, PHP 8.4에 대한 지원은 유지하고 업그레이드 전용 시나리오에 PHP 8.3을 사용할 수 있습니다. 이 작업은 코어 코드, 종속성 및 도구를 현대화하여 판매자가 PHP 8.4 지원 종료 전에 새로운 PHP 버전으로 안전하게 이동하여 PCI 규정 준수 및 장기적인 플랫폼 상태를 유지할 수 있도록 합니다.

_AC-15615_

#### PHP 8.2 지원 제거됨

Adobe Commerce 2.4.9-beta1부터 PHP 8.2는 더 이상 지원되지 않습니다. 이제 이 플랫폼은 PHP 8.3 이상을 대상으로 하며, 코어 코드, 종속성 및 도구가 업데이트되어 PHP 8.4 및 8.5에서 깔끔하고 안정적으로 실행됩니다.

_AC-15758_

#### Composer 2.9 호환성 확인됨

Adobe Commerce 2.4.9-beta1은 Composer 2.9를 포함하여 Composer 2.x와 완전히 호환됩니다. 이 맞춤은 이전 버전과의 호환성을 유지하고 최신 Composer 릴리스를 사용하여 판매자와 개발자에게 안정적인 빌드 및 배포 환경을 제공합니다.

_AC-14481_

### 프레임워크

#### JWT 프레임워크 보안 및 호환성 업데이트

지속적인 플랫폼 보안 검토의 일환으로 웹 토큰 JWT 프레임워크 종속성이 평가되고 최신 주요 버전으로 업데이트되어 Commerce 통합 전반에 걸친 토큰 기반 인증을 위한 향후 호환성과 강력한 보안 표준이 보장되었습니다. 기존 기능은 완전히 유지됩니다.

_AC-13209 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2bac8114) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce 기능 테스트 프레임워크가 Symfony LTS 종속성으로 업데이트되었습니다.

Adobe Commerce 기능 테스트 프레임워크(MTF)가 웹 토큰/jwt 프레임워크 업그레이드에 따라 symfony/config를 비롯한 최신 Symfony LTS 종속성을 사용하도록 업데이트되었습니다. 따라서 이전의 종속성 충돌이 해결되고 기능 테스트를 위해 안정적이고 지원되는 스택이 보장됩니다.

_AC-13244_

#### 기본 PHP OAuth 함수가 타사 라이브러리를 대체합니다.

타사 `carlos-mg89/oauth` 라이브러리가 기본 PHP OAuth 함수로 대체되어 보안이 향상되고 외부 의존성이 감소되며 플랫폼 안정성이 향상되었습니다.

_AC-14075 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7b8064f7)_

#### Zend_Cache를 대체하는 글꼴 캐시 구성 요소

Adobe Commerce 2.4.9-beta1부터 더 이상 사용되지 않는 Zend_Cache 구성 요소는 Symfony 캐시 구성 요소로 대체되었습니다. 이 업데이트는 캐시 성능 및 유지 관리 가능성을 향상시키고 PHP 8.x 및 향후 플랫폼 업데이트와의 장기적인 호환성을 보장합니다. 기존 캐시 백엔드 및 캐시 관리 명령은 현재 통합에 필요한 변경 사항 없이 완전히 지원됩니다.

_AC-15823_

#### WYSIWYG 편집기가 TinyMCE에서 HugeRTE로 마이그레이션되었습니다.

TinyMCE 5 및 6에 대한 지원 종료 및 TinyMCE 7과의 라이선스 비호환성으로 인해 Adobe Commerce WYSIWYG 편집기가 오픈 소스 [HugeRTE](https://hugerte.org/) 편집기로 마이그레이션되었습니다. 이러한 마이그레이션은 Adobe Commerce이 오픈 소스 라이센싱을 준수하도록 하며 알려진 TinyMCE 6 취약점을 방지하고 판매자와 개발자에게 현대적이고 지원되는 편집 환경을 제공합니다.

_AC-14568_

#### 기본 MVC 구현은 Laminas MVC를 대체합니다.

Adobe Commerce은 PHP 8.5 이상의 장기적인 호환성과 안정성을 보장하기 위해 레거시 Laminas MVC를 대체하는 기본 MVC 구현을 도입했습니다. 이러한 변경 사항은 성능을 강화하고, 외부 의존성을 감소시키며, Commerce에 미래를 대비할 수 있는 기반을 제공합니다.

_AC-15160_

#### 공식 Symfony 7.4 LTS 지원

Adobe Commerce 2.4.9-beta1 플랫폼 업데이트의 일부로 모든 Symfony 종속성이 최신 Symfony LTS 7.4 버전으로 업데이트되었습니다. Symfony 핵심 클래스를 확장하는 모든 사용자 지정 클래스에는 최신 Symfony 요구 사항에 맞게 형식 선언 및 메서드 시그니처가 업데이트되어 호환성 문제가 발생하지 않고 업데이트된 프레임워크 구성 요소로 원활하게 전환할 수 있습니다.

_AC-15170 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c127d10b)_

#### Alure PHPUnit 종속성이 버전 3으로 업그레이드됨

`allure-framework/allure-phpunit` 종속성이 PHP 8.4 및 PHP 8.5에 대한 지원을 추가하고 Allure 기반 테스트 보고 스택을 현대화하는 주요 버전 3으로 업그레이드되었습니다. 이전 Allure PHPUnit 버전에 필요했던 기본 종속성이 제거되어 설치 및 유지 관리가 간소화되었습니다.

_AC-14548 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic 보고가 NerdGraph API로 업데이트됨

New Relic 보고 모듈이 기존 REST v2 배포 마커 통합을 완전히 유지하면서 New Relic의 NerdGraph(GraphQL) 변경 추적 API를 지원하도록 업데이트되었습니다. 변경 사항은 기존 설정을 중단하지 않고 관리 설정을 통해 더 풍부한 배포 메타데이터, 지역별 끝점 지원(미국 및 EU) 및 구성 기능을 제공합니다.

_AC-15461_

#### JavaScript 라이브러리 업데이트

- **Chart.js가 버전 4.5.0으로 업데이트되었습니다**

  차트 렌더링 성능을 개선하고 시각적 기능을 향상시키며 관리 대시보드 및 보고 모듈의 보안 취약점을 해결하기 위해 Chart.js JavaScript 차트 라이브러리를 버전 4.5.0으로 업그레이드했습니다.

  _AC-14304, AC-15133 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/768b4442), [GitHub 코드 기여](https://github.com/magento/magento2/commit/657f983e)_

- **파일 업로드 라이브러리를 버전 4.13.4**(으)로 업데이트

  파일 업로드 기능을 개선하고 사용자 경험을 개선하며 Adobe Commerce 관리 인터페이스 및 프론트엔드 구성 요소에서 파일 처리의 보안 취약점을 해결하기 위해 Uppy 파일 업로드 라이브러리를 버전 4.13.4로 업그레이드했습니다.

  _AC-14307 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery 유효성 검사 라이브러리가 버전 1.21.0**(으)로 업그레이드됨

  jQuery Validate 라이브러리를 버전 1.21.0으로 업그레이드하여 양식 유효성 검사 기능을 강화하고, 사용자 경험을 개선하고, 관리 및 프론트엔드 인터페이스 모두에서 모든 Adobe Commerce 양식에서 최신 브라우저 호환성을 유지할 수 있습니다.

  _AC-14403 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI 라이브러리가 버전 1.14.1로 업그레이드됨**

  jQuery UI 라이브러리를 버전 1.14.1로 업그레이드하여 사용자 인터페이스 위젯을 개선하고, 접근성을 개선하며, 모든 Adobe Commerce 관리 및 프론트엔드 인터페이스 구성 요소에서 최신 브라우저 호환성을 보장합니다.

  _AC-14417 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js CSS 전처리기가 버전 4.2.2로 업그레이드되었습니다**

  Less.js CSS 전처리기를 버전 4.2.2로 업그레이드하여 CSS 컴파일 성능을 높이고, 구문 지원을 개선하고, 모든 Adobe Commerce 프론트엔드 및 관리 테마에 걸쳐 테마 빌드 프로세스를 현대화했습니다.

  _AC-14418 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

- **시간 시간대 라이브러리가 버전 0.5.43으로 업그레이드되었습니다**

  시간대 처리 기능을 강화하고, 표준 시간대 데이터를 최신 IANA 표준 시간대 데이터베이스 변경 내용으로 업데이트하며, 모든 Adobe Commerce 국제 및 다중 표준 시간대 작업에서 날짜 및 시간 처리 정확도를 개선하기 위해 모멘트 표준 시간대 라이브러리(`moment-timezone-with-data.js`)를 버전 0.5.43으로 업그레이드했습니다.

  _AC-14419 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

- **Underscore.js 유틸리티 라이브러리가 버전 1.13.7**(으)로 업그레이드됨

  Underscore.js 유틸리티 라이브러리를 버전 1.13.7로 업그레이드하여 JavaScript 기능 프로그래밍 기능을 개선하고, 데이터 조작 성능을 개선하며, 모든 Adobe Commerce 프론트엔드 및 관리 인터페이스 구성 요소에서 최신 브라우저 호환성을 보장합니다.

  _AC-14420 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

### 보안

#### 이제 REST 및 GraphQL API에 대해 CAPTCHA 유효성 검사가 적용됨

계정 만들기 양식에 CAPTCHA(또는 reCAPTCHA)가 활성화되면 이제 REST 및 GraphQL API를 통한 고객 계정 만들기에 대해 동일한 CAPTCHA 유효성 검사가 실행됩니다.

_AC-16245_

#### 비동기/벌크 요청 성능 개선

이 수정 사항은 APSB25-08 보안 패치 이후 도입된 벌크 비동기 웹 API 끝점의 성능 저하를 해결하여 예상 실행 시간을 복원합니다.

_AC-14078 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9a7352b7)_

#### 2단계 인증 구성 간소화

이제 관리자는 관리 패널에 액세스할 수 있도록 판매자의 활성화된 2FA 공급자 중 하나(예: Google Authenticator 또는 U2F)만 구성해야 합니다. 필요에 따라 나중에 활성화된 추가 공급자를 구성할 수 있습니다. 이전에는 여러 2FA 공급자가 활성화되었을 때 로그인할 수 있기 전에 모든 관리 사용자가 활성화된 모든 공급자를 구성해야 하므로 모든 요소에 액세스할 수 없는 사용자가 마찰을 일으켰습니다.

_AC-8253 - [GitHub 코드 기여](https://github.com/magento/security-package/commit/71e7936b)_

### 배송

#### USPS 통합을 RESTful USPS API로 마이그레이션

Adobe Commerce은 USPS가 발표한 기존 Web Tools API 폐기를 준수하기 위해 USPS 통합을 새로운 RESTful USPS API로 마이그레이션했습니다.

주요 개선 사항:

- 이중 API 지원: 이제 관리자는 구성 설정을 통해 기존 Web Tools API와 새로운 RESTful USPS API 중에서 선택할 수 있습니다.
- 인증 업그레이드: 보안 API 액세스에 OAuth 2.0을 사용합니다.
- 향상된 데이터 형식: 보다 깔끔하고 효율적인 커뮤니케이션을 위해 XML 대신 JSON을 사용합니다.
- 새 관리자 필드:
   - 게이트웨이 REST URL(모드 기준: 개발 또는 라이브)
   - 클라이언트 ID 및 암호
   - 계정 유형, 계정 번호
   - CRID, MID, Mailer 식별 코드
   - 국제 배송에 대한 AES/ITN
   - REST별 허용된 배송 방법

이 마이그레이션을 통해 Adobe Commerce은 USPS 표준을 지속적으로 준수하고 시스템 안정성을 향상시키며 판매자를 위한 미래 지향적 배송 통합을 실현할 수 있습니다.

_AC-13257_

#### DHL 통합을 MyDHL RESTful API로 마이그레이션

내장된 DHL 배송 통합은 이제 기존 DHL Express XML API와의 호환성을 유지하면서 MyDHL RESTful API를 지원합니다. 판매자는 관리에서 사용할 DHL API를 선택할 수 있으며, 기존 XML 기반 설정을 손상시키지 않고 최신 REST 기능을 활용할 수 있습니다.

_AC-13258_
