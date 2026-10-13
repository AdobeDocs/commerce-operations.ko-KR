---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Magento Open Source 하이라이트(v2.4.10)

## v2.4.10-alpha1의 주요 특징

Magento Open Source 2.4.10-alpha1 릴리스에는 다음 강조 사항이 적용됩니다.

### Braintree

#### 패스트레인

보다 빠르고 안전한 게스트 체크아웃 경험을 위해 PayPal의 Fastlane 지원이 추가되었습니다.
고객은 결제 및 배송 세부 정보를 저장하여 향후 더 빠른 구매를 원할 수 있습니다.
재방문 Fastlane 고객은 일회용 코드를 사용하여 인증하고 저장된 정보를 검색할 수 있습니다.
또한 체크아웃 중에 저장된 카드와 배송 주소를 추가하거나 변경할 수 있습니다.
Fastlane 스타일링 및 구성 옵션도 지원됩니다.

_BUNDLE-3521_

#### Braintree Insights

판매자에게 Magento Admin에서 중앙 집중식 결제 성능 보고를 제공하기 위해 Braintree Insights가 도입되었습니다.
거래, 결제, 거절, 게이트웨이 거부 및 결제 방법 데이터를 볼 수 있습니다.
웹 사이트, 날짜 범위 및 일별, 주별 또는 월별 간격으로 필터링을 지원합니다.
판매자가 보고를 위해 최대 13개월 동안의 내역 거래 데이터를 가져올 수 있습니다.
데이터 보존 및 자동화된 정리를 포함하여 최대 3년의 트랜잭션 데이터를 유지 관리합니다.

_BUNDLE-3522_

#### Swish - 로컬 결제 방법

Braintree Magento 확장에서 새로운 스웨덴 로컬 결제 방법으로 Swish 를 도입했습니다.
필요한 스웨덴 상인, 국가, 통화 및 결제 구성이 충족될 때 스윗을 사용할 수 있습니다.
스웨덴어 배송 또는 청구 주소가 있는 고객은 체크아웃 중에 Swish를 사용하여 결제를 완료할 수 있습니다.
적절한 체크아웃 응답으로 결제 흐름을 성공적, 취소적 및 실패한 경우에 대한 지원이 추가되었습니다.
전환은 필요한 모든 구성 조건이 충족될 때만 표시됩니다.

_BUNDLE-3523_

#### 버전을 v4.9.0으로 업그레이드했습니다.

Braintree 모듈이 v4.8.0에서 v4.9.0으로 업그레이드되었습니다.
업그레이드에는 최신 Braintree 모듈 변경 사항 및 개선 사항이 포함되어 있습니다.
업그레이드 후에도 Braintree 체크아웃 및 결제 처리가 예상대로 계속 작동하는지 확인했습니다.
기존 고객 체크아웃 및 주문 생성 흐름은 업그레이드된 모듈에서 정상적으로 작동합니다.
업그레이드에 의해 문제가 발생하지 않도록 기본 회귀 테스트를 수행했습니다

_BUNDLE-3530_

### 프레임워크

#### 업그레이드 NPM 종속성: underscore.js (1.13.7 → 1.13.8)

최신 업스트림 수정 사항 및 안정성 개선 사항을 포함하도록 underscore.js가 1.13.7에서 1.13.8로 업데이트되었습니다.

_AC-17486 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 업그레이드 NPM 종속성: imagemin-svgo (9.0.0 → 12.0.0)

최신 업스트림 수정 사항, 보안 업데이트 및 SVG 최적화 개선 사항을 포함하도록 imagemin-svgo를 9.0.0에서 12.0.0으로 업데이트했습니다.

_AC-17657 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### NPM 종속성 업그레이드: eslint-formatter-junit(8.40.0 → 9.0.1)

ESLint 보고에 대한 최신 업스트림 수정 사항 및 호환성 개선 사항을 포함하도록 eslint-formatter-junit을 8.40.0에서 9.0.1로 업데이트했습니다.

_AC-17659 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 업그레이드 NPM 종속성: glob(11.0.0 → 13.0.0)

최신 업스트림 수정 사항, 성능 개선 및 호환성 개선 사항을 포함하도록 glob를 11.0.0에서 13.0.0으로 업데이트했습니다.

_AC-17660 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 업그레이드 NPM 종속성: grunt-eslint (25.0.0 → 26.0.0)

최신 업스트림 수정 사항 및 호환성 개선 사항을 포함하도록 grunt-eslint를 25.0.0에서 26.0.0으로 업데이트했습니다.

_AC-17661 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 업그레이드 NPM 종속성: 정적 서비스(1.16.2 → 2.2.1)

최신 업스트림 수정 사항, 보안 업데이트 및 호환성 개선 사항을 포함하도록 1.16.2에서 2.2.1로 정적 제공 이 업데이트되었습니다.

_AC-17662 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### 최신 NPM 종속성 을 업그레이드하여 비용 절감

Grunt 및 Less를 지원되는 최신 버전으로 업데이트하여 프론트엔드 빌드 안정성 및 호환성을 개선했습니다.

_AC-17663 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

#### NPM 재정의 종속성을 지원되는 최신 버전으로 업그레이드

여러 NPM 재정의 종속성을 지원되는 최신 버전으로 업데이트하여 보안, 빌드 안정성 및 호환성을 향상했습니다.

_AC-17664 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c69ec9c5)_

### 기타

#### predis/predis를 2.x에서 3.x로 업그레이드합니다.

Redis 클라이언트 라이브러리 predis/predis가 버전 2.x에서 3.x로 업그레이드되었습니다. 이 주요 버전 업그레이드는 최신 종속성 표준에 맞고, 호환성을 개선하며, 장기 유지 관리를 보장합니다.

_AC-17101 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/de7188da)_

#### 녹아웃.js를 버전 3.5.1에서 3.5.3으로 업그레이드

녹아웃.js 라이브러리가 버전 3.5.1에서 3.5.3으로 업그레이드되었습니다. 이 업데이트는 상점 및 관리자 모두에서 녹아웃 바인딩을 사용하여 모든 UI 구성 요소에 대한 업스트림 버그 수정 및 안정성 개선을 제공합니다.

_AC-17366 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/de7188da)_
