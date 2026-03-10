---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Magento Open Source 하이라이트(v2.4.9-beta1)

## v2.4.9-beta1의 주요 특징

Magento Open Source 2.4.9-beta1 릴리스에는 다음과 같은 사항이 적용됩니다.

### API

#### 스토어 보기 수준에서 제품을 업데이트할 때 REST API에서 제품 갤러리의 상속을 유지할 수 있는 가능성 추가

스토어 범위에서 REST API를 통해 제품을 업데이트하면 해당 범위의 제품 갤러리가 변경되지 않도록 media_gallery_entries가 페이로드에서 생략되거나 NULL로 설정된 경우 제품 이미지와 비디오가 글로벌 범위의 변경 사항을 상속하지 않습니다. 또한 이제 해당 필드를 NULL로 설정하여 REST API를 통해 제품 이미지 및 비디오에 대한 범위 상속을 복원할 수 있습니다

_ACP2E-4358 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 프레임워크

#### 웹 토큰/jwt 프레임워크의 최신 주요 버전 조사

지속적인 보안 검토 프로세스의 일환으로 향후 호환성을 보장하고 강력한 보안 표준을 유지하기 위해 JWT 프레임워크의 최신 주요 릴리스를 평가했습니다. 이 릴리스에는 기존 기능에 영향을 주지 않습니다.

_AC-13209 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2bac8114) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/33b81f28)_

#### PHP 기본 함수로 carlos-mg89/oauth 바꾸기

보안을 개선하고 외부 의존성을 줄이며 플랫폼 안정성을 높이기 위해 타사 carlos-mg89/oauth 라이브러리를 기본 PHP OAuth 기능으로 대체했습니다.

_AC-14075 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7b8064f7)_

#### 최신 버전 chart.js 조사

Chart.js JavaScript 차트 라이브러리를 최신 버전 4.4.8로 업그레이드하여 차트 렌더링 성능을 개선하고 시각적 기능을 향상하며 관리 대시보드 및 보고 모듈의 보안 취약점을 해결했습니다.

_AC-14304 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/768b4442)_

#### 최신 버전 jquery/uppy 및 업데이트 조사

파일 업로드 기능을 개선하고 사용자 경험을 개선하며 Adobe Commerce 관리 인터페이스 및 프론트엔드 구성 요소에서 파일 처리의 보안 취약점을 해결하기 위해 Uppy 파일 업로드 라이브러리를 버전 4.13.4로 업그레이드했습니다.

_AC-14307 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/eb491c05)_

#### 최신 버전 조사 jquery-validate

jQuery Validate 라이브러리를 버전 1.21.0으로 업그레이드하여 양식 유효성 검사 기능을 강화하고, 사용자 경험을 개선하고, 관리 및 프론트엔드 인터페이스 모두에서 모든 Adobe Commerce 양식에서 최신 브라우저 호환성을 유지할 수 있습니다.

_AC-14403 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### 최신 버전 jquery-ui 조사

jQuery UI 라이브러리를 버전 1.14.1로 업그레이드하여 사용자 인터페이스 위젯을 개선하고, 접근성을 개선하며, 모든 Adobe Commerce 관리 및 프론트엔드 인터페이스 구성 요소에서 최신 브라우저 호환성을 보장합니다.

_AC-14417 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/77c589a6)_

#### 최신 버전 investigate less.js

Less.js CSS 전처리기를 버전 4.2.2로 업그레이드하여 CSS 컴파일 성능을 높이고, 구문 지원을 개선하고, 모든 Adobe Commerce 프론트엔드 및 관리 테마에 걸쳐 테마 빌드 프로세스를 현대화했습니다.

_AC-14418 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### 최신 버전 moment-timezone-with-data.js 조사

시간대 처리 기능을 강화하고, 최신 IANA 시간대 데이터베이스 변경 사항으로 시간대 데이터를 업데이트하며, 모든 Adobe Commerce 국제 및 다중 시간대 작업에서 날짜/시간 처리 정확도를 개선하기 위해 모멘트 시간대 라이브러리를 버전 0.5.43으로 업그레이드했습니다.

_AC-14419 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/98b2848a)_

#### 최신 버전 underscore.js 조사

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

### 기타

#### API/GraphQl에 대해 CAPTCHA/reCaptha가 작동하지 않음

Adobe Commerce 2.4.9에서 계정 만들기 양식에 대해 CAPTCHA(또는 reCAPTCHA)가 활성화되면 이제 REST 및 GraphQL API를 통한 고객 계정 만들기에 대해 동일한 CAPTCHA 유효성 검사가 시행됩니다.

_AC-16245 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fd7f30ee)_

### 보안

#### 비동기/벌크 요청 성능 개선

APSB25-08 보안 패치 이후 도입된 벌크 비동기 웹 엔드포인트의 성능 저하를 수정하여 실행 시간을 늘립니다.

_AC-14078 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9a7352b7)_

#### 사용자당 하나의 활성화된 2FA 공급자만 구성해야 함

이제 관리자는 관리 패널에 액세스할 수 있도록 판매자의 활성화된 2FA 공급자 중 하나(예: Google Authenticator 또는 U2F)만 구성해야 합니다. 필요에 따라 나중에 활성화된 추가 공급자를 구성할 수 있습니다. 이전에는 여러 2FA 공급자가 활성화된 경우(예: Google Authenticator 및 U2F) 모든 관리 사용자가 로그인한 이전에 활성화된 모든 공급자를 구성해야 했습니다. 이로 인해 모든 요소(예: U2F용 하드웨어 키)에 액세스할 수 없는 사용자가 마찰을 겪게 되었습니다.

_AC-8253 - [GitHub 코드 기여](https://github.com/magento/security-package/commit/71e7936b)_

### 스테이징 및 미리보기

#### 모바일 보기에서 [기능 요청] 콘텐츠 스테이징 미리 보기

이제 관리 패널의 스테이징 미리 보기 기능을 사용하여 브라우저에서 시뮬레이션된 모바일 장치 미리 보기를 정확하게 렌더링하여 스테이징 업데이트가 모바일 장치에 표시되는 방식을 시각적으로 나타낼 수 있습니다.

_ACP2E-3397 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_
