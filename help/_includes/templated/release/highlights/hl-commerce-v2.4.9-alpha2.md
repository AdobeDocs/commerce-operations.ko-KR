---
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Adobe Commerce 릴리스 노트(v2.4.9-alpha2)

## v2.4.9-alpha2의 강조 표시

Adobe Commerce 2.4.9-alpha2 릴리스에는 다음과 같은 사항이 적용됩니다.

### 프레임워크

#### OpenSearch 3에 대한 지원 추가

Adobe Commerce 2.4.9는 이제 OpenSearch 3.x와 완전히 호환됩니다. 이 업데이트는 OpenSearch 2.x와의 이전 버전과의 호환성을 유지하면서 성능, 보안 및 장기 지원 향상 효과를 누릴 수 있도록 해 줍니다.

_AC-11846_

#### Nginx 버전을 1.26에서 1.28로 업데이트

현재 지원되는 모든 Adobe Commerce 버전의 개발 및 테스트 환경에서 사용되는 Nginx 버전은 사용 가능한 최신 안정적인 Nginx 릴리스에 맞춰 1.26에서 1.28로 업데이트됩니다.
이제 PR 수준 테스트가 Nginx 1.28에 대해 실행되어 모든 Adobe Commerce 버전에 대한 완전한 호환성과 지원을 확인할 수 있습니다.

_AC-14104_

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

#### TinyMCE에서 Hugerte.org으로 마이그레이션

TinyMCE 5 및 6에 대한 지원 종료 및 TinyMCE 7과의 라이선스 비호환성으로 인해 Adobe Commerce WYSIWYG 편집기의 현재 구현은 TinyMCE에서 오픈 소스 HugeRTE 편집기(https://hugerte.org/)로 마이그레이션됩니다.
이러한 마이그레이션은 Adobe Commerce이 오픈 소스 라이센싱을 준수하도록 하며 알려진 TinyMCE 6 취약점을 방지하고 판매자와 개발자에게 현대적이고 지원되는 편집 환경을 제공합니다.

_AC-14568_

#### 2.4.9-alpha2에 대한 전체 Valkey 8.x 지원 추가

Adobe Commerce 2.4.9에는 Valkey에 대한 전체 CLI 명령이 지원되며, 기존 Redis 기능을 미러링합니다. 원활한 Valkey 설정을 허용하도록 관리 및 클라우드 구성이 업데이트되었습니다.
이 업데이트는 Valkey 8.x를 지원함으로써 Adobe Commerce이 미래를 대비하고 성능을 유지할 수 있도록 해주며, Redis가 수명이 다함에 따라 판매자와 개발자에게 신뢰할 수 있는 대안을 제공합니다.

_AC-14604_

### 기타

#### CNS 빌드 및 테스트용 AWS Valkey 8.x 서비스 업데이트

CNS Build용 AWS Valkey 8.x 서비스 업데이트

_AC-14470_

#### 2.4.9-alpha2 - 8월 코어 품질 개선 사항

_AC-14700_

### 보안

#### 2.4.9-alpha2의 보안 개선 사항

_AC-14610_

### 배송

#### 오래된 웹 도구 API에서 새로운 RESTful USPS API로 USPS 통합 마이그레이션

USPS가 2026년 1월 25일까지 레거시 Web Tools API의 종료를 발표한 것을 준수하기 위해 Adobe Commerce USPS 통합은 새로운 RESTful USPS API로 마이그레이션됩니다.

주요 개선 사항:

* 이중 API 지원: 이제 관리자는 구성 설정을 통해 기존 Web Tools API와 새로운 RESTful USPS API 중에서 선택할 수 있습니다.
* 인증 업그레이드: 보안 API 액세스를 위해 OAuth 2.0을 구현했습니다.
* 향상된 데이터 형식: 보다 깔끔하고 효율적인 커뮤니케이션을 위해 XML에서 JSON으로 전환되었습니다.
* 새 관리자 필드:
   * 게이트웨이 REST URL(모드 기준: 개발 또는 라이브)
   * 클라이언트 ID &amp;amp; 암호
   * 계정 유형, 계정 번호
   * CRID, MID, Mailer 식별 코드
   * 국제 배송에 대한 AES/ITN
   * REST별 허용된 배송 방법

이 마이그레이션을 통해 Adobe Commerce은 USPS 표준을 지속적으로 준수하고 시스템 안정성을 향상시키며 판매자를 위한 미래 지향적 배송 통합을 실현할 수 있습니다.

_AC-13257_
