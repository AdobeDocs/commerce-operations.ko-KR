---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '25720'
ht-degree: 0%

---
# Magento Open Source 릴리스 노트(v2.4.8)

## 강조 표시

다음 31개의 강조 표시가 Magento Open Source 2.4.8 릴리스에 적용됩니다.

### 프레임워크

#### League/flysystem Composer 종속성을 최신 버전으로 업그레이드

2.x league/flysystem Composer 종속성을 최신 버전 3.x로 업그레이드

_AC-10721 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/91cb4d46>)_

#### php-amqplib/php-amqplib 최신 버전을 조사합니다.

최신 버전 php-amqplib/php-amqplib :^3.x 업데이트

_AC-11673 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### 업그레이드 라이브러리로 마이그레이션 후 jQuery/fileuploader css 정리

jQuery/fileUploader 라이브러리가 Uppy 라이브러리로 마이그레이션되어 제거되었습니다.

_AC-11911 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### Magento CE용 MySQL 8.4 LTS와의 호환성 추가

_AC-11995 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### jsTree 라이브러리로 마이그레이션 후 ExtJs 폴더 정리

관련 기능이 jsTree로 마이그레이션되어 extJs 폴더가 제거되었습니다.

_AC-12015 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/7cabfb46>)_

#### 모노로그/모노로그 시스템 종속성을 최신 주요 버전으로 업그레이드

시스템이 &quot;monolog/monolog:^3.x&quot; 라이브러리의 최신 주요 버전을 사용하도록 업데이트되어 호환성이 보장되고 성능이 향상되었습니다. 이전에는 시스템에서 잠재적인 문제 및 제한을 초래할 수 있는 &quot;monolog/monolog&quot; 라이브러리의 이전 버전을 사용했습니다.

_AC-12022 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### wikimedia/less.php 종속성을 최신 주요 버전으로 업그레이드

&quot;wikimedia/less.php&quot; 라이브러리의 최신 주요 버전 5.x를 사용하도록 시스템을 업데이트하여 호환성과 최신 기능을 보장합니다. 이전에는 시스템에서 보안 문제가 발생할 수 있는 오래된 버전의 라이브러리를 사용하고 있었습니다.

_AC-12023 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### jquery/validate 라이브러리 종속성을 최신 부 버전으로 업그레이드

jquery/validate 라이브러리 종속성을 최신 부 버전 1.20.0으로 업그레이드

_AC-12024 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### moment.js 시스템 종속성을 최신 부 버전으로 업그레이드

moment.js 시스템 종속성을 최신 부 버전 2.30.1로 업그레이드

_AC-12025 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/de4dfb8e>)_

#### MySQL 8.4 LTS for EE와의 호환성 추가

_AC-12032 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### B2B용 MySQL 8.4 LTS와의 호환성 추가

_AC-12034 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### 번들 확장용 MySQL 8.4 LTS와의 호환성 추가

_AC-12074 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### CE용 MariaDB 11.4 LTS와의 호환성 추가

Adobe Commerce 및 확장의 MariaDB 11.4 지원이 추가됨

_AC-12085 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### 구독자 최적화 - PhpUnit10

_AC-12165 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/90e25b6b>)_

#### Redis 세션에 대한 연결 재시도를 지원하고 colinmollenhour/php-redis-session-abstract v2.0.0과 호환됩니다.

adobe commerce와 호환되는 colinmollenhour/php-redis-session-abstract v2.0.0 최신 버전 업데이트

_AC-12267 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### MySQL 8.4 LTS를 사용하여 자동화 테스트 실패 조사

_AC-12576 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/672a2e61>)_

#### MariaDB 11.4 LTS For EE와의 호환성 추가

Adobe Commerce 및 확장의 MariaDB 11.4 지원이 추가됨

_AC-12595 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### Laminas 작성기 종속성을 최신 버전으로 업데이트

이제 시스템에서 최신 버전의 laminas composer 종속성을 지원합니다.
laminas/laminas-servicemanager
라미나스/라미나스 서버
laminas/laminas-stdlib
laminas/laminas-validator
호환성 및 최신 기능 보장. 이전에는 이러한 종속 항목의 최신 버전으로 업데이트하면 이전 버전과의 호환성 문제 및 테스트 오류가 발생할 수 있었습니다.

_AC-12715 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### 구성 요소 업그레이드 중 phpunit 패치 업데이트로 인한 단위 테스트 실패를 조사합니다.

_AC-12823 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/b34c0a75>)_

#### [파트1] - 사용 가능한 최신 버전으로 모든 js 라이브러리 및 npm 종속성 업데이트

composer 버전 지원은 composer 버전 2.2.x에만 해당됩니다. 이제 지원도 2.4.x 버전으로 확장되었습니다.

_AC-13076 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/19844aa0>)_

### 주문

#### [기능 요청] 주문 세부 사항 페이지의 댓글 제출 단추가 혼동되어 다른 것으로 변경해야 한다고 고객이 제안함

혼란을 최소화하기 위해 주문 세부 사항 페이지에서 &quot;댓글 제출&quot; 버튼 레이블을 &quot;업데이트&quot;로 변경했습니다.

_ACP2E-2709 - [GitHub 코드 기여도](<https://github.com/magento/magento2/commit/488c1034>)_

### 기타

#### 새 버전의 Adobe Commerce이 설치되면 인덱서 설정이 기본적으로 준비 상태로 표시됩니다.

Magento 설치 후 인덱서의 상태는 기본적으로 *준비* 상태여야 합니다.

_AC-11420 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/71432aeb>)_

#### 기존 Magento 설치 시 타사 인덱서 모듈을 설치하면 기본적으로 일정에 따라 인덱서가 업데이트됩니다.

모든 새 인덱서는 기본적으로 [일정별 업데이트] 모드에 있습니다. 이전에는 기본 모드가 [저장 시 업데이트]였습니다. 사용자 지정 인덱서와도 동일합니다.

_AC-11421 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/71432aeb>)_

#### Elasticsearch 7 및 8 옵션은 관리자 구성에서 더 이상 사용되지 않습니다.

관리자 구성 옵션의 Elasticsearch 8 옵션은 더 이상 사용되지 않는 텍스트와 함께 표시되므로 사용자에게 Elasticsearch 8은 더 이상 권장되지 않는 옵션입니다.

_AC-12480 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/0611e750>)_

#### 관리자 구성에서 Elasticsearch 옵션을 선택한 경우 텍스트 메모 추가

Adobe Commerce 관리자 사용자에게 elasticsearch가 더 이상 Adobe에서 지원되지 않으며 더 이상 사용되지 않는다는 것을 알리기 위해 텍스트 메모가 추가되었습니다.

_AC-12481 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/0611e750>)_

#### 2.4.8로 계층 가격 운영 성능 향상 패치 제공

이제 시스템에서 &quot;/V1/products/tier-prices&quot; REST API 엔드포인트를 사용할 때 성능 문제나 사이트 무응답을 초래하지 않고 계층 가격을 더 효율적으로 대량 업데이트할 수 있습니다. 이전에는 이 끝점을 사용하여 많은 가격을 업데이트하면 성능 문제와 사이트 응답이 없을 수 있었습니다.

_AC-13448 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/082d981c>)_

#### Magento Open Source 저장소에서 Adobe 기밀 저작권 고지를 모두 제거합니다

모든 Adobe 기밀 저작권 공지가 오픈 소스 저장소에서 제거되어 축소된 형태의 Adobe 저작권만 사용됩니다. 이전에는 공개 저장소의 일부 파일에 Adobe 기밀 저작권 고지가 포함되어 있어 해당 커뮤니티에서 에스컬레이션이 발생했습니다.

_AC-13550 - [GitHub 문제](https://github.com/magento/magento2/issues/39493) - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/4bca5dfe>)_

### UI 프레임워크

#### [2.4.8-beta1] TinyMCE 5에서 TinyMCE 7로 마이그레이션

TinyMCE 5를 TinyMCE 7.3.0으로 마이그레이션하여 Adobe Commerce의 지원 버전으로, 이전 시스템에서는 오래되어 보안 취약성이 보고된 5.10.2를 사용하고 있었습니다

_AC-12726 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### TinyMCE 7 페이지 빌더로 [2.4.8-beta1] TinyMCE 5 마이그레이션

TinyMCE 5를 TinyMCE 7.3.0으로 마이그레이션하여 Adobe Commerce의 지원 버전으로, 이전 시스템에서는 오래되어 보안 취약성이 보고된 5.10.2를 사용하고 있었습니다

_AC-12825 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### [2.4.8-beta1] TinyMCE 5에서 TinyMCE 7 - Magento2-infra로 마이그레이션 - 금지된 단어

TinyMCE 5를 TinyMCE 7.3.0으로 마이그레이션하여 Adobe Commerce의 지원 버전으로, 이전 시스템에서는 오래되어 보안 취약성이 보고된 5.10.2를 사용하고 있었습니다

_AC-12844 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/edcd0dcc>)_

#### 최신 버전 2.3.7로 업그레이드해야 합니다(보안 취약점 CVE-2024-38999)

require.js가 최신 버전 2.3.7로 업데이트되었습니다. 이전 버전에서 보안 취약성이 보고되었습니다.

_AC-12901 - [GitHub 코드 기여](<https://github.com/magento/magento2/commit/b34c0a75>)_

## v2.4.8의 문제가 해결되었습니다.

Magento Open Source 2.4.8 코어 코드에서 497개의 문제가 해결되었습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

#### /V1/transactions REST API가 parent_txn_id = txn_id일 때 오류를 반환합니다.

이제 시스템은 상위 트랜잭션 ID가 트랜잭션 ID와 동일한 상위 및 하위 개념 트랜잭션을 올바르게 처리하므로 /V1/transactions REST API 끝점을 쿼리할 때 무한 루프가 발생하지 않습니다. 이전에는 이 시나리오가 최대 실행 시간을 초과하여 치명적인 오류를 초래했습니다.

_AC-10042 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bafc571)_

#### 2.4.7의 [Graphql] 유형 문제

이제 시스템은 GraphQL 쿼리를 실행할 때 GetCustomSelectedOptionAttributes 함수의 정수 값을 올바르게 처리하여 유형 관련 오류를 방지합니다. 이전에는 정수 인수와 함께 GetCustomSelectedOptionAttributes를 사용하는 GraphQL 쿼리를 실행하면 형식 오류가 발생했습니다.

_AC-11878 - [GitHub 문제](https://github.com/magento/magento2/issues/38662) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38663)_

#### 범주 url_key의 특수 문자(REST API를 통해 만든 경우)

이전 In category_url_key 특수 문자는 수정 후 존재하지 않으며 category_url_key에 특수 문자를 표시합니다.

_AC-3223 - [GitHub 문제](https://github.com/magento/magento2/issues/35577) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c699c206)_

#### 2FA Duo 활성화 후 rest api 문제

2FA(듀오 보안 옵션 포함)는 이제 Rest API에 대한 올바른 서명을 생성합니다.

_ACP2E-2755 - [GitHub 코드 기여도](https://github.com/magento/security-package/commit/412fa642)_

#### [REST API]: 구성 가능한 제품에 대한 구성을 추가한 후 저장소 보기에서 기본값 사용이 선택된 상태로 유지되지 않습니다.

기본값이 아닌 저장소에 대해 사용자 정의 가능한 옵션에 대해 올바른 데이터베이스 항목을 보장함으로써 문제가 해결되었습니다. 사용자 지정 스토어의 옵션 제목이 기본 스토어와 동일하게 유지되더라도 정확하지 않은 데이터베이스 항목으로 인해 이전에 &quot;관리 > 카탈로그 > 제품 편집 > 사용자 지정 가능 옵션&quot; 섹션의 사용자 지정 스토어에 대한 확인란이 선택되지 않았습니다.

_ACP2E-2927 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3056e9cb)_

#### REST API에서 Oauth1을 사용할 때 SKU에서 슬래시(/)로 요청을 수행할 수 없음

수정 전에는 SKU에 &quot;/&quot;가 있는 제품에 대해 성공적인 API 호출을 수행할 수 없었습니다. 이제, SKU에 슬래시가 포함되어 있어도 제품 세부 사항에 대한 성공적인 API get 요청을 실행할 수 있습니다.

_ACP2E-2969 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b21e5d91)_

#### &quot;validateDefaultAddress&quot;가 활성화된 경우 REST API를 통해 업데이트할 때 고객 주소 업데이트가 실패했습니다.

API 페이로드에서 누락된 ID 키 문제가 해결된 후 API 엔드포인트가 의도한 대로 작동합니다.

_ACP2E-3079 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9af794a4)_

#### [클라우드] 계층 가격 Api에서 중복 웹 사이트 그룹 가격 고객 그룹을 만드는 중입니다.

이제 계층 가격 할인 Api는 중복 웹 사이트 그룹 가격 고객 그룹을 생성할 수 없습니다.
이전에는 제품 저장 중에 관리자의 유효성 검사를 통과하지 않는 계층 가격 API에 중복 웹 사이트 그룹 가격 고객 그룹을 만들 수 있었습니다.

_ACP2E-3091 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/148c3ead)_

#### REST API를 통해 상태로 주문 주석을 추가할 수 없음

현재 상태에서만 주문 상태 변경을 허용하여 문제가 해결되었습니다. 이전에는, 동일한 상태에서라도 주문 상태를 준수하고 어떤 주문 상태에서도 변경을 방지하지 않았습니다.

_ACP2E-3130 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/93d50f8d)_

#### 페이로드에서 SKU가 누락된 경우 비동기 작업이 실패합니다

페이로드에서 sku가 누락된 경우 제품 저장 오류로 인해 이전에 비동기 및 동기화 작업이 실패했습니다. 수정 후 비동기 및 동기화 제품 저장 rest api 작업이 관련 예외 메시지와 함께 실패합니다.

_ACP2E-3236 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD] REST API를 사용하여 기본 가격을 업데이트할 수 없습니다(&#39;catalog_product_entity_decimal&#39;의 &#39;value_id&#39; 값이 올바르게 증가하지 않음).

이전에는 rest api /rest/default/V1/products/base-prices가 호출되면 값 사이에 간격이 없도록 증가 ID가 잘못 증가했습니다. 수정 후 증분 ID가 예상대로 증가합니다(증분). 또한 value_id 필드 범위가 증가했습니다.

_ACP2E-3376 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 주문 항목이 API POST V1/order/:orderId/refund에 대한 대변 메모 이메일에 표시되지 않음

이전에는 고객이 send_email을 알리는 API 요청에서 대변 메모를 만들 때 제품 세부 정보 그리드가 포함되지 않았습니다. 이 수정 사항이 적용되면 고객은 대변 메모 API 요청을 보내고 이메일에 표시되는 제품 항목 세부 사항을 찾습니다.

_ACP2E-3460 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152)_

#### 제품 RestAPI를 사용하는 날짜 및 시간 속성에 대한 기본값이 설정되지 않음

이제 기본값이 RestAPI를 통해 날짜 및 날짜 및 시간 속성에 대해 제대로 설정됩니다

_ACP2E-3486 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

### API, 카트 및 체크아웃

#### 중요 500 오류: Magento\Framework\Webapi\Exception Accept HTTP 헤더와 관련이 있습니다.

수정 후에는 &quot;Accept&quot; 헤더를 지정하는 데 문제가 없습니다.

_ACP2E-3343 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

### 계정

#### 고객 주소 양식에서는 이름 필드에 무작위 코드를 사용할 수 있습니다.

이제 시스템이 고객 주소 양식의 이름 및 성 필드에 입력된 내용을 확인하여 무작위 코드를 사용할 수 없습니다. 이전에는 시스템에서 오류가 발생하지 않고 이러한 필드에서 무작위 코드를 사용할 수 있었습니다.

_AC-10782 - [GitHub 문제](https://github.com/magento/magento2/issues/38331) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38345)_

#### 관리자 암호를 업데이트했습니다.

_AC-10886 - [GitHub 문제](https://github.com/magento/magento2/issues/38352) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/4bca5dfe)_

#### 저장 시 내 계정 추가 주소 충돌

영역 필드가 표시되지 않는 경우에도 시스템이 고객 주소를 올바르게 저장하여 저장 프로세스 중에 충돌을 방지합니다. 이전에는 표시된 영역 필드 없이 주소를 추가하거나 편집하려고 하면 예외 오류가 발생했습니다.

_AC-10990 - [GitHub 문제](https://github.com/magento/magento2/issues/38406) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38407)_

#### URL에 대문자가 있으면 루프 리디렉션

이제 시스템에서 URL의 대문자를 소문자로 자동 변환하여 홈 페이지에 액세스할 때 리디렉션 루프가 발생하지 않도록 합니다. 이전에는 Secure Base URL에 대문자가 있으면 홈 페이지에 액세스하려고 할 때 리디렉션 루프가 계속 발생합니다.

_AC-11718 - [GitHub 문제](https://github.com/magento/magento2/issues/38538) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38539)_

#### 게스트 계정에 대해 middlename이 저장되지 않음

이제 시스템은 체크아웃 중에 게스트 계정의 가운데 이름을 올바르게 저장하므로 이메일 템플릿에서 액세스할 수 있습니다. 이전에는 중간 이름이 견적 테이블에 저장되지 않았으며 게스트 계정의 이메일 템플릿에서 액세스할 수 없었습니다.

_AC-11755 - [GitHub 문제](https://github.com/magento/magento2/issues/38593) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39067)_

#### 관리자: 페이지 작업 버튼이 오른쪽 대신 왼쪽으로 부동됨

이제 시스템이 페이지 작업 버튼을 관리 패널의 고정 헤더 오른쪽에 올바르게 정렬하여 전문적인 모양과 느낌을 개선합니다. 이전에는 이러한 버튼이 고정 헤더의 왼쪽으로 잘못 이동했습니다.

_AC-11919 - [GitHub 문제](https://github.com/magento/magento2/issues/38701) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/44cef3a9)_

#### magento 2.4.7의 `dev:di:info` 오류

이제 시스템에서 `dev:di:info` 명령을 실행할 때 생성자 매개 변수를 올바르게 표시하여 오류가 발생하지 않도록 합니다. 이전에는 인수의 형식 불일치로 인해 이 명령을 실행하면 오류가 발생했습니다.

_AC-11999 - [GitHub 문제](https://github.com/magento/magento2/issues/38740) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 고객 옵트인 확인란으로 로그인 을 번역할 수 없음

이제 시스템에서 &quot;고객 옵트인 확인란으로 로그인&quot; 및 &quot;고객 확인란으로 로그인&quot; 툴팁 필드를 &quot;스토어 보기&quot; 범위에서 설정할 수 있도록 하여 다양한 스토어 보기에 대한 번역을 활성화합니다. 이전에는 이러한 필드가 &quot;웹 사이트&quot; 범위에서만 설정되어 개별 스토어 조회수에 대한 번역을 방지했습니다.

_AC-13000 - [GitHub 문제](https://github.com/magento/magento2/issues/32329) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32359)_

#### 고객이 로그인되어 있지만 프론트엔드에 404 오류가 표시됩니다.

이제 고객이 로그인할 때 상점 고객 대시보드 페이지가 예상대로 로드됩니다. 이전에는 고객이 로그인할 수 있었지만 이 페이지에는 404 오류가 표시됩니다. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [GitHub 문제](https://github.com/magento/magento2/issues/35838) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36263)_

#### 고객 속성 정보를 관리자 고객 편집 섹션에 저장할 수 없음;

고객의 스토어 ID가 이제 관리자 고객 편집 양식에 대한 웹 사이트 범위별로 올바르게 구현됩니다.

_ACP2E-2791 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/488c1034)_

#### 로그인 후 게스트 사용자로 비교 목록에 추가된 제품이 표시되지 않습니다.

고객으로 로그인하기 전에 제품 비교 목록에 추가된 제품은 로그인 후 유지됩니다.
이전에는 로그인 후 게스트 사용자로 비교 목록에 추가된 제품이 표시되지 않았습니다.

_ACP2E-3329 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### 국가 구성 허용으로 인해 고객 주소 구성에 문제가 발생합니다.

이제 국가 구성 허용을 선택하면 해당 범위를 벗어나는 국가에 영향을 주지 않습니다. 이전에 허용 국가 구성이 지정된 범위를 벗어나는 고객 주소 속성에 영향을 주었습니다

_ACP2E-3433 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### VAPT: 비즈니스 논리 오류 - 고객 생년월일로 표시되는 미래 일자

고객의 생년월일을 오늘보다 늦출 수 없습니다.

_ACP2E-3501 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

### 계정, API, GraphQL

#### 고객 API - 로그인 실패 횟수 로그인이 성공적으로 수행된 후 0으로 재설정할 수 없음

이제 고객이 API 끝점을 통해 성공적으로 로그인한 후 고객 엔티티 테이블에서 실패 번호가 0으로 재설정됩니다.

_ACP2E-3246 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

### 계정, 관리자 UI, B2B

#### 제한된 관리자는 사용자 지정 공유 카탈로그를 항상 볼 수 없습니다.

이제 제한된 관리자는 특정 스토어에 액세스할 수 있는 경우 제품과 제품이 할당된 모든 공유 카탈로그를 일관되게 보고 관리할 수 있습니다. 이전에는 특정 상점에 대한 액세스 권한이 있는 제한된 관리자가 제품이 할당된 모든 공유 카탈로그를 항상 볼 수 없거나 저장할 수 없는 고객을 볼 수 없어서 시스템에 불일치가 발생했습니다.

_ACP2E-3038 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

### 계정, 장바구니 및 체크아웃

#### 새 고객 주소에 대해 &quot;select&quot; 사용자 지정 고객 주소 특성이 렌더링되지 않음

_AC-2341 - [GitHub 문제](https://github.com/magento/magento2/issues/34950)_

### 관리자 UI

#### [문제] &quot;데이터 다시 로드&quot; 데이터 단추에 대한 권한 확인 추가

이제 시스템에는 &quot;데이터 다시 로드&quot; 버튼에 대한 권한 검사가 포함되어 있으므로 적절한 권한이 있는 사용자만 데이터를 표시하고 액세스할 수 있습니다. 이전에는 모든 사용자에 대해 &quot;데이터 다시 로드&quot; 단추가 표시되고 클릭할 수 있으므로 필요한 권한 없이 사용자가 클릭할 때 &quot;허용되지 않는&quot; 페이지가 표시됩니다.

_AC-10705 - [GitHub 문제](https://github.com/magento/magento2/issues/38283) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38279)_

#### [문제] 마케팅 규칙의 특성에 일관되지 않은 레이블

이제 시스템에서 장바구니 가격 규칙의 범주 및 속성 옵션에 대한 레이블을 일관되게 올바르게 채웁니다

_AC-11427 - [GitHub 문제](https://github.com/magento/magento2/issues/31232) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31231)_

#### 데이터 유효성 검사 성공 및 [가져오기] 버튼은 [바꾸기] 동작이 있는 제품 가져오기 중에 표시됩니다

이제 시스템에서 데이터를 올바르게 확인하고 제품 가져오기 프로세스 중에 &quot;가져오기&quot; 단추를 &quot;바꾸기&quot; 동작으로 숨겨 의도하지 않은 데이터 대체를 방지합니다. 이전에는 시스템에서 데이터의 유효성을 잘못 검사하고 &quot;가져오기&quot; 단추를 표시했기 때문에 데이터가 일치하지 않을 수 있었습니다.

_AC-11588 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

#### [버그] Magento 2.4.7에서는 대문자 파일 확장명을 가진 제품 사진을 사용할 수 없습니다.

이제 시스템에서 대문자 파일 확장자를 사용한 제품 이미지 업로드를 허용하여 원활한 제품 생성 프로세스를 보장합니다. 이전에는 대문자로 된 파일 확장자를 사용한 이미지 업로드가 거부되어 사용자가 파일 확장자를 소문자로 변경해야 했습니다.

_AC-12167 - [GitHub 문제](https://github.com/magento/magento2/issues/38831) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c8f87c25)_

#### 선택 작업(예: 컨텐츠 > 요소 > 페이지)이 있는 그리드의 숨겨진 드롭다운

이제 모든 그리드에 대해 유사한 모든 드롭다운이 수정되었습니다.

_AC-12319 - [GitHub 문제](https://github.com/magento/magento2/issues/38891) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39371)_

#### [문제] 수정 경고: 배열 키 &quot;filters&quot;가 정의되지 않았습니다.

이제 시스템은 새 사용자가 아직 책갈피와 상호 작용하지 않은 시나리오를 처리하여 정의되지 않은 배열 키 &quot;필터&quot; 경고가 기록되지 않도록 합니다. 이전에는 신규 사용자가 책갈피와 상호 작용하지 않으면 이 경고가 기록되었습니다.

_AC-13131 - [GitHub 문제](https://github.com/magento/magento2/issues/39013) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38996)_

#### Validate.php 파일의 코드 변경으로 인해 특수 문자가 있는 제품 가져오기 csv 파일이 실패합니다

이제 시스템에서 특수 문자가 포함된 제품 CSV 파일을 올바르게 확인하고 가져와서 데이터를 성공적으로 전송할 수 있습니다. 이전에는 제품 CSV 파일을 특수 문자로 가져오려고 하면 오류가 발생하여 가져오기 프로세스가 진행되지 않았습니다.

_AC-13529 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### 필수 전화 번호 필드에 빨간색 별표가 없습니다.

이전 빨간색 별표는 전화 번호에 표시되지 않지만  전화 번호는 필수입니다. 이제 고정된 빨간색 별표가 전화 번호에서 필수 필드로 표시됩니다.

_AC-13850 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c699c206)_

#### [문제] 기본 인덱서 모드를 &#39;일정&#39;으로 설정

모든 새 인덱서는 기본적으로 **[!UICONTROL Update by Schedule]** 모드에 있습니다.  이전에는 기본 모드가 **[!UICONTROL Update on Save]**&#x200B;이었습니다. 기존 인덱서는 영향을 받지 않습니다. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [GitHub 문제](https://github.com/magento/magento2/issues/36419) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0b410856)_

#### [문제] mview 구독 취소에 인덱서 변경 로그 테이블을 삭제합니다.

이제 인덱스가 &#39;일정에 따라 업데이트&#39;에서 &#39;저장 시 업데이트&#39;로 전환되면 사용되지 않은 변경 로그 테이블이 자동으로 제거되며, 누락된 항목이 없도록 인덱스가 유효하지 않은 것으로 표시됩니다. 이전에는 색인을 &#39;저장 시 업데이트&#39;로 전환하면 시스템에 사용되지 않은 변경 로그 테이블이 남고 변경된 모든 색인이 &#39;유효함&#39;으로 표시되었습니다.

_AC-7700 - [GitHub 문제](https://github.com/magento/magento2/issues/29789) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/25859)_

#### 휴대폰 보기에서 결제 시 배송에 대한 링크가 없습니다.

이제 시스템에서 체크아웃 제목/링크 &quot;배송&quot; 및 &quot;검토 및 결제&quot;가 모바일 보기의 페이지 상단에 항상 표시되도록 하여 사용자가 단계를 쉽게 탐색하고 필요한 사항을 수정할 수 있습니다. 이전에는 이러한 제목/링크가 모바일 보기에 숨겨져 있어서 사용자가 현재 단계를 확인하거나 이전 단계로 돌아가기 어려웠습니다.

_AC-7962 - [GitHub 문제](https://github.com/magento/magento2/issues/36856) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36982)_

#### customer Orders 쿼리 선적 주석 created_at 은(는) 스토어 구성 시간대에 없는 +0 시간대에 반환됩니다.

이제 시스템은 고객 주문 쿼리를 사용할 때 고객이 구성한 시간대에 출하 주석의 &#39;created_at&#39; 필드를 올바르게 표시합니다. 이전에는 고객이 구성한 시간대에 관계없이 &#39;created_at&#39; 필드가 +0 시간대에 표시되었습니다.

_AC-8109 - [GitHub 문제](https://github.com/magento/magento2/issues/36947) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases이(가) 번역 무결성을 중단합니다.

이제 `bin/magento i18n:collect-phrases -o` 명령이 JavaScript 및 .phtml 파일에서 새 구문을 올바르게 수집하고 추가하여 번역이 번역 파일에 정확하게 반영되도록 합니다. 이전에는 시스템이 JavaScript 파일의 여러 줄 번역 구문과 .phtml 파일의 구문을 번역 파일에 포함하지 못해 번역이 완료되지 않았거나 잘못되었습니다.

_AC-9843 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 저장소 보기 이름의 아포스트로피가 &#039;(으)로 대체됨

이제 격자의 저장소 보기 필터에 아포스트로피가 올바르게 표시됩니다

_ACP2E-2787 - [GitHub 문제](https://github.com/magento/magento2/issues/38395) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/39d54c2d)_

#### Favicon 업로드가 .ico 파일의 유효성을 검사하지 못했습니다.

파일 유효성 검사 오류가 &quot;파일 유효성 검사 실패&quot;로 업데이트되었습니다. 저장소 구성에서 이미지 처리 설정을 확인하십시오.&quot; 이전에는 단순히 &quot;파일 유효성 검사 실패&quot;였습니다.

_ACP2E-2847 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/39d54c2d)_

#### PageBuilder의 갤러리에 새로 업로드한 이미지 대신 이전 이미지 썸네일이 표시됩니다.

페이지 빌더 콘텐츠의 미디어 갤러리를 통해 삭제되고 동일한 이름으로 다시 업로드된 이미지에 대한 이미지 미리 보기를 다시 생성합니다.

_ACP2E-2957 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/001e5188)_

#### 역할 범위가 다른 관리자가 제품을 저장하면 제품의 기존 관련 제품 정보가 덮어쓰기되거나 삭제됩니다.

이전에는 수정 전에 보조 관리자 사용자가 관련 제품에서 변경하지 않고 저장 버튼을 클릭하면 관련 제품이 재설정되고 비어 있었습니다. 이 수정 후 보조 관리자가 저장 버튼을 클릭하면 제품이 재설정되지 않고 정상적으로 저장됩니다.

_ACP2E-2978 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3056e9cb)_

#### 200개 이상의 주문을 내보낼 수 없음

문제를 해결하기 위해 GET에서 POST로 HTTP 요청을 변경하여 이전에 제출된 선택한 ID의 요청 크기에 대한 서버 제한을 무시했습니다. 이전에는 GET 요청 크기에 대한 서버 제한으로 인해 문제가 발생했습니다.

_ACP2E-3033 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/93d50f8d)_

#### 체크아웃 페이지 유효성 검사 메시지가 잘못되었습니다.

&quot;주소&quot;와 같은 필수 필드를 비워 두면 서버측 유효성 검사가 메시지를 표시하지 않습니다. 클라이언트측 유효성 검사는 &quot;필수 필드입니다.&quot;라는 필수 필드 오류 알림이 표시되는지 확인합니다. 이전에는 클라이언트측 유효성 검사 메시지 외에 필수 필드를 비워 두면 &quot;주소가 필요합니다&quot;라는 메시지가 표시되었습니다.

_ACP2E-3037 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9af794a4)_

#### 관리자 암호 재설정 템플릿 문제

이제 이메일 템플릿에 관리자 사용자 이름을 포함하고 제목을 올바르게 완료하는 올바른 키를 사용하여 문제가 해결되었습니다. 이전에는 사용 중인 오래된 키에서 문제가 발생했습니다.

_ACP2E-3125 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/93d50f8d)_

#### 고객 세그먼트 URL의 더블 슬래시

표에서 &#39;필터 재설정&#39;을 클릭할 경우 URL에 이중 슬래시가 표시되지 않습니다.

_ACP2E-3149 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8459b17d)_

#### 허용된 특정 국가에서는 COD를 사용할 수 없습니다.

이제 필요할 때마다 허용된 특정 국가에서만 배달 현금을 사용할 수 있습니다.   AC-3216이 예상대로 작동합니다.

_ACP2E-3171 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6f4805f8)_

#### 사용자 정의 생성 주문 상태를 업데이트할 수 없음

&#39;이제 사용자 지정 생성 주문 상태를 업데이트할 수 있습니다. 반면, 이전에는 현재 상태가 &quot;처리 중&quot; 또는 &quot;사기&quot;인 경우에만 상태를 변경할 수 있었습니다.

_ACP2E-3178 - [GitHub 문제](https://github.com/magento/magento2/issues/38659) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8459b17d)_

#### 배송 주소 상태가 자동 업데이트되지 않음

수정 전 배송 주소 영역(또는 지역 ID)이 주소 청구 정보와 동기화되지 않았습니다. 이제 청구지 주소 정보가 변경되면 배송 주소 지역과 지역 ID가 모두 올바르게 업데이트됩니다.

_ACP2E-3294 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

#### 관리자 추가/편집 사용자에서 재설정 단추가 작동하지 않음

이전에는 재설정 단추가 관리자 사용자 추가/편집 페이지에서 작동하지 않았습니다. 이제 시스템 -> 권한 -> 모든 사용자 아래의 관리 패널에서 재설정 단추가 관리자 사용자 추가/편집 페이지에서 올바르게 작동합니다.

_ACP2E-3364 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### Magento 관리자 URL 라우팅 오류 감지 및 CORS 오류

수정 후 사용자 정의 관리 도메인이 주 도메인의 하위 도메인인 경우 구성된 하위 도메인에서만 관리자에 액세스할 수 있습니다.

_ACP2E-3373 - [GitHub 문제](https://github.com/magento/magento2/issues/37663) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3f12d152)_

#### &#39;장바구니에서 허용되는 최대 수량&#39;에 대한 유효성 검사 중단

이전에는 `Maximum Qty Allowed in Shopping Cart`을(를) 비워 두면 여기에 빈 값이 허용되지 않지만 예외를 throw하지 않았습니다. 이 수정 사항이 적용되면 빈 문자열을 넣으면 예외가 발생하고 제품 저장이 허용되지 않습니다.

_ACP2E-3392 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [페이지 빌더 미리 보기 UI 문제] 페이지 빌더 열의 단추가 올바르게 정렬되지 않습니다

이제 페이지 빌더 열의 버튼이 올바르게 정렬됩니다. 이전에는 페이지 빌더 열 내에서 맞춤이 일치하지 않았습니다.

_ACP2E-3408 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### 제품 주문 보고서를 내보내고 있지 않습니다. 대신 404 오류가 발생했습니다.

CSV 및 XML로 제품 주문 보고서 내보내기가 이제 예상대로 작동합니다

_ACP2E-3431 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/88660e79)_

#### 프로덕션 모드에서 Js 축소를 활성화한 후 콘솔에 TinyMCE JS 오류 발생

이전에는 관리 패널 내의 프로덕션 모드에서 JavaScript 축소를 활성화하면 TinyMCE 6과 관련된 JavaScript 오류가 브라우저 콘솔에 표시되어 기능과 사용자 경험에 영향을 주었습니다. 이제 이 문제가 해결되어 JS 축소가 활성화된 경우에도 TinyMCE 6이 오류를 생성하지 않고 원활하게 작동할 수 있습니다.

_ACP2E-3457 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/56463d5e)_

#### ACP2E-3375 수정을 완전히 완료하기 위한 추가 변경 요청

&#39;-

_ACP2E-3459 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 새 ACL 권한 자동 활성화

사용자 지정 모듈에 추가된 새 권한은 명시적으로 구성되지 않는 한 더 이상 기존의 모든 사용자 역할에 대한 액세스 권한을 자동으로 부여하지 않습니다.

_ACP2E-3503 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152)_

#### 관리자 작업 로그 사용자 보고서에 adminhtml_user_delete에 대한 세부 정보가 표시되지 않습니다.

이제 adminhtml_user_delete가 중요한 세부 정보를 올바르게 기록합니다. 이전에는 사용자 삭제에 대한 로그가 생성되지 않았습니다.

_ACP2E-3509 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4de008a9)_

#### 책임자로부터 주문을 할 때 배송 조건이 적용되지 않는 장바구니 규칙

기존에는 장바구니 가격 규칙에 쿠폰이 포함된 배송 방법 할인이 있는 경우 관리자 UI를 통해 적용할 수 없었다. 이 수정 사항이 적용되면 특정 배송 방법에 대한 쿠폰이 포함된 장바구니 가격 규칙 할인이 관리 UI에서 성공적으로 적용됩니다.

_ACP2E-3536 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/11ce816b)_

#### [FRESH] HEX 코드가 SWATCH에서 올바르게 업데이트되지 않음

시각적 견본 색상 선택기에서 사용자가 수동으로 입력한 16진수 코드는 시스템에서 더 이상 변경하지 않습니다. 이전에는 특정 HEX 코드가 색상 모델 간의 변환 오류로 인해 약간의 조정을 경험했습니다.

_ACP2E-3559 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/344fce23) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/1ef984c0)_

### 관리자 UI, B2B

#### 고객 헤더로 B2B 로그인에 여전히 Magento 브랜딩이 있음

이전에는 상점 헤더 표시에 Magento 브랜딩이 &quot;이제 &lt;store name>에서 &lt;customer name>(으)로 연결되었습니다&quot;라는 메시지가 표시되었습니다. 이제 수정되었으며 머리글에 ADOBE 브랜딩이 표시됩니다.

_AC-13628 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/96dec499)_

### 관리자 UI, 결제/결제 방법, 주문

#### PayPal 스마트 단추 주문 후 거래 탭에 거래 승인이 표시되지 않음

이제 PayPal 스마트 버튼을 사용하여 주문을 하면 트랜잭션 탭에 트랜잭션 승인이 올바르게 표시됩니다. 이전에는 인증 트랜잭션이 &quot;승인&quot; 버튼을 클릭한 후 트랜잭션 탭에 표시되지 않고 &quot;승인&quot; 유형의 새 트랜잭션이 만들어지지 않았습니다.

_AC-13520 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6cfb9b6b)_

### 관리자 UI, 성능

#### 2.4.5-p8로 업데이트한 후 관리자에서 주문을 만들 때 500 오류가 발생합니다

이전에는 HTML 축소를 활성화할 때 관리자의 주문을 넣을 수 없었습니다. 이제 HTML 축소가 활성화되면 관리자의 주문을 성공적으로 수행할 수 있습니다.

_ACP2E-3169 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b21e5d91)_

### 관리자 UI, 배송

#### 쿠폰 코드 카운트가   주문이 복수 배송으로 이루어진 경우 쿠폰 코드 관리 탭의 &quot;사용된 시간&quot; 열.

앞서 멀티배송으로 주문이 들어오면 쿠폰코드 관리 탭의 &#39;사용한 시간&#39; 열에서 쿠폰코드 카운트가 업데이트되지 않았다. 이제 다중 배송과 함께 원하는 값이 반영된 &quot;사용한 시간&quot; 모두에 올바른 카운트가 표시됩니다.

_ACP2E-2519 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4745100c)_

### 관리자 UI, 스테이징 및 미리보기

#### [클라우드] 누락된 이미지가 있는 템플릿을 제거하면 pub/media가 삭제됩니다

이 수정 이전에 pagebuilder 템플릿에 대한 미리보기 이미지 이름이 누락된 경우 pub/media 폴더가 삭제되었습니다. 수정 후에는 템플릿만 삭제되고 미리보기 이미지(있는 경우)가 표시됩니다.

_ACP2E-3424 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/보고

#### Google Analytics CSP 오류 https://region1.analytics.google.com

이제 Google Analytics이 활성화되면 시스템에서 &#39;https://region1.analytics.google.com&#39;에 대한 연결을 올바르게 허용하므로 CSP(콘텐츠 보안 정책) 오류가 발생하지 않습니다. 이전에는 Google Analytics을 활성화하고 EU에서 웹 사이트를 보면 &#39;https://region1.analytics.google.com&#39;에 대한 연결 거부로 인해 CSP 콘솔 오류가 발생했습니다.

_AC-9922 - [GitHub 문제](https://github.com/magento/magento2/issues/37750) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38991)_

#### 고급 보고서가 작동하지 않음

이제 시스템은 10,000개의 배치로 보고서를 로드 및 작성하여 초대형 데이터 세트에 대한 사전 보고 데이터 파일 생성을 지원합니다. 이전에는 Advance Reporting 모듈에서 초대형 데이터 세트에 대한 데이터 파일을 생성할 수 없어 analytics_collect_data cron 작업을 실행하는 동안 &quot;MySQL Server가 없어졌습니다.&quot; 오류가 발생했습니다.

_ACP2E-2570 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a12063bd)_

#### 관리 주문 제품 날짜 범위 가시성 문제를 보고합니다.

사용자는 주문 제품 보고서에서 원하는 날짜를 선택할 수 있습니다. 이전에는 테이블을 새로 고친 후 &#39;시작&#39; 날짜를 선택하면 &#39;종료&#39; 날짜가 재설정됩니다.

_ACP2E-3080 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6f4805f8)_

#### `newrelic:create:deploy-marker`을(를) 만드는 잘못된 curl 헤더가 작동하지 않음

이제 시스템에서 curl 헤더 형식을 올바르게 지정하여 `newrelic:create:deploy-marker` 명령이 New Relic에서 배포 마커를 성공적으로 만들 수 있습니다. 이전에는 잘못된 curl 헤더로 인해 New Relic에서 배포 마커를 만들 수 없었습니다.

_ACP2E-3096 - [GitHub 문제](https://github.com/magento/magento2/issues/37641) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6a185204)_

#### InlineJS 스크립트를 모니터링하는 NewRelic 브라우저로 인해 CSP 오류가 발생합니다

이제 NewRelic 브라우저 모니터링 스크립트가 CSP(콘텐츠 보안 정책) 준수를 위해 APM 에이전트 대신 애플리케이션에 의해 삽입됩니다. 이전에는 APM 에이전트에서 삽입한 NewRelic 브라우저 모니터링 스크립트가 CSP를 준수하지 않아 스크립트가 실행되지 않았습니다.

_ACP2E-3183 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

#### sales_bestsellers_aggregated_daily 테이블에 대한 INSERT 쿼리는 판매 주문 수량이 많은 프로젝트에서 느려집니다.

이전에는 매일 보고서를 집계하는 베스트셀러가 대량의 주문량에 대해 보고서를 생성하는 데 많은 시간이 소요되었습니다. 이제 보고서가 적시에 생성됩니다.

_ACP2E-3189 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

#### 잘못된 통화 기호를 표시하는 주문 보고서

주문 보고서의 주문 금액에 대한 통화 기호가 통화/옵션/기준에서 잘못 사용되었습니다. 이제 정확한 보고를 위해 통화/옵션/기본값을 사용하도록 수정되었습니다.

_ACP2E-3276 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] 쿠폰 사용 보고서에서 잘못된 계산

쿠폰 보고서 그리드의 매출액 합계는 이제 &quot;할인세 보상액&quot;과 &quot;해운할인세 보상액&quot;을 모두 통합하여 정확하게 계산된다. 이전에는 이러한 금액이 계산에서 누락되어 판매 합계와 판매 주문 데이터 간의 불일치가 발생했습니다.

_ACP2E-3302 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d75cff27)_

#### 공유 &quot;&lt;project_id>/var/tmp&quot; 관련 문제

Analytics DataExport 임시 파일은 sys tmp 디렉토리를 사용하며, 이는 빈번한 액세스 및 변경에 더 적합합니다. 동일한 서버에서 여러 인스턴스가 실행 중인 경우 충돌을 방지하기 위해 인스턴스의 고유 ID를 사용하도록 tmp 경로가 업데이트되었습니다

_ACP2E-3339 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/보고, B2B

#### B2B - 사이트 맵에 공유 카탈로그에 할당되지 않은 제품/카테고리가 포함됨

사이트맵에서 생성된 범주 및 제품을 공개 공유 카탈로그 및/또는 카탈로그 범주 권한 설정에만 할당된 범주 및 제품으로 제한합니다.

_ACP2E-2300 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/보고, 클라우드

#### Magento이 대부분의 New Relic cron 트랜잭션을 #34108

AC가 cron 작업 관련 트랜잭션을 NewRelic에 올바르게 보고하고 있습니다. 이전에는 일부 cron job 관련 트랜잭션이 NR에서 &quot;OtherTransaction/Action/unknown&quot;으로 표시되었습니다

_ACP2E-3067 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/35b1b1da)_

#### NR의 지표가 백그라운드 트랜잭션에 대해 오해의 소지가 있을 수 있음 - ACP2E-3067의 후속 조치

백그라운드 트랜잭션(cron)은 구성 설정에 정의된 New Relic 앱 이름을 사용합니다

_ACP2E-3187 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### 부분 색인이 실행될 때 공유 카탈로그에 할당된 제품이 프런트 엔드에서 반영되지 않습니다.

이제 부분 인덱싱이 완료된 후 REST API를 통해 공유 카탈로그에 할당된 제품이 상점 첫 화면에서 바로 표시됩니다. 이전에는 전체 색인 재지정 후에만 제품이 표시되었습니다.

_ACP2E-2139 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

#### 내 주문 섹션의 불필요한 테두리

이전에는 추가 CSS 클래스를 적용하는 추가 컨테이너(주문 참조)가 만들어졌고, 이로 인해 불필요한 테두리 라인이 현재 표시되지 않는 내 주문 섹션의 주문 번호 아래에 표시됩니다.

_ACP2E-3044 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron 은 아직 승인된 구매 발주에서 견적을 삭제합니다.

구매 발주에 사용된 견적은 이제 sales_clean_quotes cron 작업에 의해 삭제되지 않습니다.

_ACP2E-3247 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

### B2B, 프레임워크

#### 회사 그리드를 필터링한 다음 그리드 CSV 내보내기를 시도하면 실패하고 예외가 발생합니다.

이제 &#39;미결 잔액&#39; 및 &#39;회사 유형&#39;과 같은 필터가 적용된 경우에도 시스템에서 관리 패널의 회사 그리드 데이터를 CSV로 내보낼 수 있습니다. 이전에는 특정 필터를 적용하고 그리드 데이터를 내보내려고 하면 오류가 발생하고 예외가 발생합니다.

_AC-9607 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/44cef3a9)_

### 번들

#### Storefront 번들 확인란 유효성 검사 오류 메시지 수가 1보다 큼

이제 번들 제품에 대한 확인란 옵션을 선택하지 않고 &#39;장바구니에 추가&#39; 버튼을 클릭하면 시스템에 하나의 유효성 검사 오류 메시지만 표시됩니다. 이전에는 선택하지 않은 각 확인란에 대해 여러 개의 유효성 검사 오류 메시지가 표시되었습니다.

_AC-10826 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3ea26621)_

### 장바구니 및 체크아웃

#### 제품 비교 페이지에서 장바구니에 제품을 추가하는 동안 예외가 제대로 처리되지 않습니다.

이제 시스템은 제품 비교 페이지에서 제품을 장바구니에 추가할 때 예외를 올바르게 처리하고 컨트롤러에 메시지 관리자 메시지를 표시합니다. 이전에는 예외를 제외하면 JSON으로 인코딩된 페이지가 제대로 포착되고 처리되지 않고 반환됩니다.

_AC-10660 - [GitHub 문제](https://github.com/magento/magento2/issues/38200) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38257) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 거래 가격 및 합계를 보내지 마십시오.

이제 GTag가 활성화되면 시스템이 거래 가격과 합계를 Google 태그에 올바르게 보내어 전자 상거래 데이터를 정확하게 추적할 수 있습니다. 이전에는 통화가 개별 주문과 연결되지 않고 &quot;모든&quot; 주문의 일부로 잘못 전송되었습니다.

_AC-10698 - [GitHub 문제](https://github.com/magento/magento2/issues/37348) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37504) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37349)_

#### [문제] [체크아웃] 실패한 결제 전자 메일 템플릿에서 종속 지시문이 업데이트되었습니다.

이제 시스템에서 가상 제품에 대한 실패한 결제 이메일 템플릿에서 배송 주소와 배송 방법을 올바르게 생략하여 관련 정보만 이메일에 포함되도록 합니다. 기존에는 가상 제품에 대한 결제 이메일에 배송 주소와 배송 방법이 잘못 포함됐다.

_AC-11641 - [GitHub 문제](https://github.com/magento/magento2/issues/32781) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32511)_

#### 기존 고객과 함께 체크아웃 내에서 Magento 2 로그인 Firefox 브라우저에서 콘솔 오류 발생

이제 시스템에서 체크아웃 프로세스 중에 Firefox 브라우저에서 콘솔 오류가 발생하지 않고 로그인할 수 있습니다. 이전에는 체크아웃 중에 기존 고객으로 로그인하려고 하면 Firefox에서 콘솔 오류가 발생합니다.

_AC-11717 - [GitHub 문제](https://github.com/magento/magento2/issues/38557) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39509)_

#### 2.4.7의 [문제] 판매 규칙 회귀

이제 시스템에서 판매 규칙을 올바르게 검증하여 제품 조건이 제품 이름과 일치하지 않을 때 장바구니에 쿠폰 코드를 적용할 수 없습니다. 기존에는 상품 조건이 상품명과 일치하지 않아도 판매 규정을 적용해 배송 금액에 대한 할인을 받을 수 있었다.

_AC-11876 - [GitHub 문제](https://github.com/magento/magento2/issues/38671) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

#### [문제] 판매 규칙 CartFixed 계산: 잘못된 할인 금액

이제 시스템에서 장바구니 고정 금액이 있는 판매 규칙에 대한 할인 금액을 올바르게 계산하므로 장바구니 항목의 변경에 관계없이 정확한 할인이 적용됩니다. 이전에는 장바구니 품목을 변경할 때 할인 금액이 잘못 변경되어 예상보다 할인 금액이 크게 변경되기도 했습니다.

_AC-11914 - [GitHub 문제](https://github.com/magento/magento2/issues/38694) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/581b7ef1)_

#### [문제] 포스트코드가 변경된 후 로더가 배송 방법을 차단합니다. 배송 속도 유효성 검사 규칙

이제 시스템은 배송률 검증 규칙 없이 맞춤형 배송 방법을 올바르게 처리하므로 체크아웃 중에 배송 주소에서 우편 번호가 변경된 후 로더가 배송 방법을 차단하지 않도록 합니다. 이전에는 체크아웃 중에 배송 주소에서 우편번호를 변경하면 로더가 배송 방법을 차단하고 배송률 검증 규칙이 없는 사용자 지정 배송 방법을 사용하면 로더가 사라지지 않습니다.

_AC-11993 - [GitHub 문제](https://github.com/magento/magento2/issues/38742) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bafc571)_

#### 쿠폰 코드 기능이 Magento 2.4.7의 체크아웃 페이지에서 제대로 작동하지 않음

이제 시스템은 가상 및 다운로드 가능한 제품에 대한 체크아웃 페이지에서 할인 코드/쿠폰 입력 필드를 활성화하여 사용자가 예상대로 할인 코드를 적용할 수 있습니다. 기존에는 할인코드/쿠폰 입력이 비활성화되고, 버튼 제목 텍스트가 &#39;쿠폰 취소&#39;로 표시돼 사용자가 할인코드를 적용하지 못했다.

_AC-12170 - [GitHub 문제](https://github.com/magento/magento2/issues/38826) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bafc571)_

#### 약관 확인란에서 상점 첫 화면의 HTML을 허용하지 않습니다.

이제 시스템은 상점 첫 화면의 &quot;약관&quot; 확인란 텍스트에서 HTML 서식을 지원하여 향상된 사용자 지정 및 가독성을 가능하게 합니다. 이전에는 확인란 텍스트가 사용된 HTML 태그를 무시하고 일반 텍스트 형식으로 표시되었습니다.

_AC-12479 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### 로그인한 사용자에 대해 생성된 장바구니 가격 규칙이 로그인되지 않은 사용자에 대해 잘못 적용됨

이제 시스템은 쿠키 만료로 인해 자동으로 로그아웃되는 경우 로그인한 사용자에 대한 장바구니 가격 규칙을 올바르게 제거하여 로그인되지 않은 사용자에게 할인이 적용되지 않도록 합니다. 이전에는 장바구니 가격 규칙이 사용자가 로그아웃된 경우에도 계속 적용되어 로그인하지 않은 사용자에게 잘못된 할인이 적용되었습니다.

_AC-12541 - [GitHub 문제](https://github.com/magento/magento2/issues/38944) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7d5e3906)_

#### [문제] [기능] 방지 기능을 통해 성능 최적화 대형 장바구니...

이 시스템은 이제 중복 getActions 호출을 방지하여 대형 장바구니에 대한 성능을 최적화하여 장바구니 작업의 속도와 효율성을 개선합니다. 이전에는 여러 항목이 있는 장바구니의 경우 getActions 함수를 여러 번 호출하여 시스템 성능을 느리게 했습니다.

_AC-13302 - [GitHub 문제](https://github.com/magento/magento2/issues/39292) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39290)_

#### 주소 렌더러의 번역 VAT

이제 시스템에서 주소 렌더러의 텍스트 &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot;를 번역할 수 있으므로 사용자가 이러한 용어를 상점의 특정 언어로 번역할 수 있습니다. 이전에는 이러한 용어를 번역할 수 없어 사용자가 해결 방법을 사용해야 했습니다.

_AC-8103 - [GitHub 문제](https://github.com/magento/magento2/issues/36942) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36943)_

#### 동일한 Quote ID로 시간 차이가 거의 없는 동시에 주문을 복제합니다.

Adobe Commerce 고객이 동일한 QuoteID로 주문된 중복 주문을 발견할 경우 발생하는 문제를 해결했습니다

_ACP2E-2055 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### 체크아웃 단계에서 영구 장바구니가 지워짐

수정 후 로그인하지 않은 상태에서 체크아웃 중에 결제 방법을 선택하면 영구 세션이 종료되지 않습니다.

_ACP2E-2470 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

#### 순서 바꾸기가 장바구니에 할당되지 않은 제품을 추가합니다.

이전에는 서로 다른 상점의 경우 다른 상점에서 제품을 재주문할 수 있었습니다. 이 수정 사항이 동일한 스토어에만 적용된 후 고객 계정 공유가 활성화되면 동일한 범위 제품을 재정렬할 수 있습니다

_ACP2E-2518 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### 관리자의 경우, 오른쪽에서 항목 및 &quot;장바구니로 이동&quot;을 선택할 때 왼쪽의 &quot;장바구니&quot;가 업데이트되지 않습니다

관리자 측면의 오른쪽에서 항목 및 &quot;장바구니로 이동&quot;을 선택하면 왼쪽의 &quot;장바구니&quot;가 업데이트됩니다. 이전에는 변환된 장바구니 항목이 세션에서 비어 있지 않으므로 이 기능이 작동하지 않았습니다.

_ACP2E-2620 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Cloud] 판매 규칙이 다중 배송의 첫 번째 주문에 적용되지 않음

수정 후에는 동일한 다중 배송 견적의 각 주문에 대해 할인이 올바르게 표시됩니다.

_ACP2E-2646 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### 장바구니에 동일한 제품을 추가하도록 [Cloud] 프로덕션 병렬 요청을 수행하면 장바구니 Rest API에 두 개의 개별 항목이 생성됩니다

이제 시스템에서 여러 병렬 요청을 올바르게 처리하여 동일한 제품을 장바구니에 단일 라인 항목으로 추가하므로 동일한 SKU에 대해 별도의 라인 항목이 생성되지 않습니다. 이전에는 REST API를 통해 동일한 제품을 장바구니에 추가하도록 동시에 요청하면 동일한 SKU에 대해 여러 라인 항목이 생성됩니다.

_ACP2E-2664 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### 쿠키를 보낼 수 없습니다. 순서를 재지정하는 동안 &#39;이미지 메시지&#39; 크기

지금 순서 조정 프로세스에서는 자체 오류가 생성되지 않습니다. 장바구니에 기본 제공 항목 검사를 나열합니다.

_ACP2E-2704 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### 체크아웃 시 기본 배송 주소가 선택되지 않음

이제 활성화된 주소 검색 컨텍스트에서 기본 배송 주소가 선택된 이벤트로 바뀌었습니다.

_ACP2E-2798 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7e0e5582)_

#### 사용자 지정 옵션이 있는 [CLOUD] graphql addProductsToCart api 문제

GraphQL은 사용자 지정 옵션이 다른 동일한 제품을 장바구니에 올바르게 추가합니다

_ACP2E-2897 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e)_

#### 새 고객으로 체크아웃할 때 계정에 여러 주소가 추가됨

이제 주문이 생성되지 않은 경우 새 고객 주소가 한 번만 저장되므로 주문 배치 오류가 발생할 경우 동일한 주소가 여러 개 생성되지 않습니다. 이전에는, 주문이 성공적으로 생성되었는지 여부에 관계없이 주문 배치가 시도될 때마다 새 주소가 저장되었습니다.

_ACP2E-2923 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/001e5188) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/2ebcef39)_

#### 고객 주문 양식을 통해 고객 주문을 재정렬하면 빈 장바구니가 생성됩니다.

이전에는 주문 및 반품 페이지를 통해 재주문을 할 때 고객이 로그인 페이지로 리디렉션되었습니다. 이 수정 사항이 적용되면 재주문을 하면 등록된 고객이 장바구니 보기 페이지로 올바르게 리디렉션됩니다. 흐름은 게스트 고객과 동일하게 작동합니다.

_ACP2E-3004 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6a185204)_

#### 역할 리소스가 제한된 관리 사용자가 장바구니를 볼 수 없음

이전에는 제한된 관리자가 연결된 웹 사이트의 관리 패널에서 구매하지 않은 장바구니를 볼 수 없었습니다. 이 수정 사항이 적용되면 제한된 관리자는 관리 패널에서 구매하지 않은 장바구니를 볼 수 있습니다.

_ACP2E-3025 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d1f7dc95)_

#### [클라우드] 빠른 주문 대량의 SKU 성능

장바구니 가격 규칙 조건에 사용된 속성이 모든 제품에 대해 존재하지 않고 MAP(광고된 최소 가격) 기능이 활성화된 경우 체크아웃 성능이 개선되었습니다.

_ACP2E-3176 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

#### 장바구니의 중복 항목

이제 시스템에서 여러 병렬 요청을 올바르게 처리하여 동일한 제품을 장바구니에 단일 라인 항목으로 추가하므로 동일한 SKU에 대해 별도의 라인 항목이 생성되지 않습니다. 이전에는 Storefront에서 장바구니에 동일한 제품을 추가하도록 동시에 요청하면 동일한 SKU에 대해 여러 라인 항목이 생성됩니다.

_ACP2E-3211 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

#### 체크아웃 주문 이메일 확인은 성/이름에 입력한 이메일에 전송됩니다.

이전에 이메일과 유사한 패턴을 이름 및 성 필드에 입력했을 때 전송된 체크아웃 주문 이메일 확인은 더 이상 전송되지 않습니다.

_ACP2E-3296 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### 체크아웃 배송 주소 양식이 잘못된 주소로 업데이트됨

이제 shippingAddressFromData가 웹 사이트당 로컬 저장소에 저장됩니다. 이전에는, 저장소 코드가 URL에서 사용되고 동일한 게스트 세션 중에 여러 웹 사이트에서 체크아웃이 시작된 경우 체크아웃 중에 잘못된 웹 사이트의 주소가 배송 주소 양식에 자동으로 채워질 수 있었습니다.

_ACP2E-3402 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### 기프트 카드 제품 | 장바구니 병합에서 기프트 카드를 병합하는 중입니다.

이제 기프트 카드 제품이 장바구니에서 올바르게 병합됩니다.

_ACP2E-3407 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/88660e79)_

#### 로그아웃 시 장바구니 지속성이 적용되지 않음

고객 로그인부터 인증 팝업 및 체크아웃 로그인에 이르기까지 기억하기 기능이 추가되었습니다.

_ACP2E-3415 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/344fce23)_

#### 기존 견적 데이터가 업데이트되지 않거나 표시되지 않는 대신 trigger_recolect = 1일 때 새 견적 레코드를 만듭니다.

장바구니에 추가된 후 제품이 삭제되어 고객의 장바구니 항목이 더 이상 사라지지 않습니다.

_ACP2E-3488 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

#### [클라우드] 순서 조정 단추 기능

원래 주문에 더 이상 재고가 없는 제품이 있더라도 관리자 영역에서 주문을 재주문하면 재고가 있는 제품이 견적에 추가됩니다. 수정 전에는 재고가 없는 제품이 원래 주문에 포함된 경우 새 견적에 추가된 제품이 없었습니다.

_ACP2E-3618 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a52ff98f)_

#### 검색 저장소가 우편 번호로 작동하지 않음

우편번호로 픽업 위치 검색이 네덜란드어 현지화에 대해 제대로 작동하지 않았습니다. 수정 후 픽업 위치 검색은 우편 번호를 기반으로 결과를 제공합니다.

_ACP2E-3622 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/344fce23)_

### 장바구니 및 체크아웃, 체크아웃/ 한 페이지 체크아웃

#### [무작위 버그] 전자 메일 필드가 렌더링되지 않았거나 체크아웃 배달 또는 결제 페이지에 표시되는 데 많은 시간이 소요됩니다

이제 Commerce에서 예상대로 체크아웃 배송 및 결제 페이지의 **[!UICONTROL Email]** 필드를 렌더링합니다. 이전에는 이 필드가 없거나 느리게 표시되었습니다.

_AC-9386 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/e1babcfd)_

### 장바구니 및 체크아웃, 주문

#### 관리자 주문 시 날짜 필드가 작동하지 않는 사용자 지정 가능 옵션이 여러 개 있는 제품에 대한 날짜 선택기

이제 시스템은 관리 주문 생성 프로세스에서 사용자 정의 가능한 날짜 옵션이 여러 개인 제품을 구성할 때 모든 날짜 필드에 대해 날짜 선택기를 올바르게 표시합니다. 이전에는 날짜 선택기가 날짜 선택기 없이 나머지 필드는 남겨두고 첫 번째 날짜 필드에만 표시되었습니다.

_ACP2E-3097 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b21e5d91)_

### 장바구니 및 체크아웃, 배송

#### 구성 가능한 제품에 대해 즉시 구매 &quot;가장 저렴한 배송&quot;이 중단됨

즉시 구매 기능이 가장 저렴한 정액 요금 방법 대신 구성 가능한 제품에 대해 더 비싼 매장 내 배달 옵션을 잘못 선택했습니다. 이 수정 사항을 통해 실제 가격을 기준으로 올바른 배송 방법을 선택할 수 있습니다.&quot;

_AC-12119 - [GitHub 문제](https://github.com/magento/magento2/issues/38811) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38819) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/29fe9097)_

### 카탈로그

#### cron_schedule 데이터베이스 테이블을 정리하면 존재하지 않는 작업이 정리되지 않습니다.

이제 시스템에서 cron_schedule 데이터베이스 테이블을 자동으로 정리하여 시스템에 더 이상 존재하지 않는 작업에 대한 항목을 제거합니다. 이렇게 하면 테이블에서 최소한의 행 수를 유지하여 최적의 성능을 보장합니다. 이전에는 비활성 또는 제거된 모듈의 작업에 대한 항목이 정리되지 않아 cron_schedule 테이블에 불필요한 데이터가 누적되었습니다.

_AC-10910 - [GitHub 문제](https://github.com/magento/magento2/issues/38217) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38693)_

#### 구성 가능한 제품에서 계층 가격이 삭제되지 않음

이제 시스템은 단순한 제품에서 구성 가능한 제품으로 전환될 때 제품의 계층 가격을 올바르게 제거하여 프론트엔드에 정확한 가격을 표시할 수 있도록 합니다. 이전에는 구성 가능한 제품의 계층 가격이 제품이 단순 제품에서 구성 가능한 제품으로 전환되어 표시된 가격이 일치하지 않을 때 삭제되지 않았습니다.

_AC-10953 - [GitHub 문제](https://github.com/magento/magento2/issues/38390) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38427)_

#### 범주 설명 WYSIWYG이 기본이 아닌 스토어뷰에서 비어 있습니다.

이제 스토어 보기 수준에서 카테고리를 편집할 때 WYSIWYG 편집기에 카테고리 설명이 올바르게 저장되고 표시됩니다. 이전에는 스토어 보기 수준에서 카테고리 설명을 저장하면 WYSIWYG 편집기가 비어 있게 표시됩니다.

_AC-11804 - [GitHub 문제](https://github.com/magento/magento2/issues/38622) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38623)_

#### 하나의 확인란을 선택한 경우 구성 가능한 제품의 순서를 사용자 지정 옵션으로 변경할 수 없음

이제 시스템에서 선택한 단일 확인란 사용자 지정 옵션으로 구성 가능한 제품의 순서 재지정을 올바르게 처리하여 바구니를 성공적으로 만들 수 있습니다. 이전에는 이러한 제품을 재정렬하려고 하면 오류가 발생하여 장바구니에 항목이 추가되지 않았습니다.

_AC-11970 - [GitHub 문제](https://github.com/magento/magento2/issues/38736) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1d144bce)_

#### [문제] 계층화된 탐색에서 필터 항목의 단어를 수정했습니다.

이제 시스템에서 계층화된 탐색 필터 항목의 &quot;item&quot; 및 &quot;items&quot;라는 단어를 올바르게 사용하므로 필터 설명의 명확성과 정확성이 향상되었습니다. 이전에는 이러한 단어가 잘못 사용되었기 때문에 필터 옵션을 탐색하는 사용자에게 잠재적인 혼동을 주었습니다.

_AC-12076 - [GitHub 문제](https://github.com/magento/magento2/issues/38789) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37852)_

#### 사용자 지정 옵션의 날짜 및 시간 형식이 작동하지 않음

이제 시스템에서 구성된 날짜 형식을 날짜 유형의 제품 사용자 정의 옵션에 올바르게 적용하여 프론트엔드에 날짜 형식이 올바르게 표시되도록 합니다. 이전에는 날짜 형식 구성에 대한 변경 사항이 날짜 유형의 제품 사용자 정의 옵션에 대한 프런트 엔드에 반영되지 않았습니다.

_AC-12164 - [GitHub 문제](https://github.com/magento/magento2/issues/32990) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38925)_

#### 드롭다운 옵션 누락

이제 20개 이상의 값으로 새 속성을 만들 때 드롭다운에 모든 값이 올바르게 표시됩니다. 이전에는 처음 20개 값 또는 다른 선택한 페이지 값만 표시되어 나머지 값이 누락되었습니다.

_AC-13068 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/47b448e2)_

#### [문제] 범주 런타임 캐시에 현재 저장소 ID를 사용합니다.

이제 시스템은 범주 런타임 캐시에 현재 저장소 ID를 올바르게 사용하므로 에뮬레이션을 사용하거나 사용자 지정 코드가 다른 저장소에 범주를 저장할 때 데이터가 재정의되지 않도록 합니다. 이전에는 런타임에 저장된 개체가 잘못된 저장소에서 가져와서 데이터를 재정의했을 수 있었습니다.

_AC-13296 - [GitHub 문제](https://github.com/magento/magento2/issues/39310) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata:deploy —no-update에서 예외가 발생합니다.

sampledata:deploy 명령에서 —no-update 옵션을 사용할 때 시스템이 부울 값을 올바르게 허용하므로 샘플 데이터 배포 중 오류가 발생하지 않습니다. 이전에는 시스템에서 정수 값을 잘못 예상하여 이 명령을 사용할 때 오류가 발생했습니다.

_AC-13324 - [GitHub 문제](https://github.com/magento/magento2/issues/39344) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39345)_

#### [문제] EAV 캐시 유형 사용 수정

이제 시스템에서 모든 관련 위치에서 EAV 캐시 유형을 올바르게 사용하여 일관되고 효율적인 데이터 캐싱을 보장합니다. 이전에는 EAV 캐시 유형을 일관되게 사용하지 않아 데이터 캐싱의 비효율성과 불일치가 발생할 수 있었습니다.

_AC-13355 - [GitHub 문제](https://github.com/magento/magento2/issues/32322) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31264)_

#### 빈 데이터가 있는 카탈로그 고급 검색이 검색 결과 페이지[2.4.dev 분기]&#x200B;(으)로 이동합니다.

이제 시스템이 고급 검색 페이지에 사용자를 올바르게 유지하고 데이터를 입력하지 않고 검색을 수행하려고 하면 오류 메시지를 표시합니다. 이전에는 빈 검색을 수행하면 사용자가 검색을 수정하라는 메시지와 함께 카탈로그 고급 검색 페이지로 리디렉션됩니다.

_AC-13596 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### attribute_set에 따른 [문제] 제품 레이아웃

이제 시스템에서는 속성 세트를 기반으로 제품 레이아웃을 조정할 수 있으므로 프론트엔드 스토어의 제품 표시를 보다 실용적이고 효율적으로 관리할 수 있습니다. 이전에는 레이아웃을 SKU 또는 제품 유형별로만 조정할 수 있었지만, 많은 제품이나 특정 문서에 대해 항상 실용적이지는 않았습니다.

_AC-13622 - [GitHub 문제](https://github.com/magento/magento2/issues/38790) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36244)_

#### eav_attribute_option_value 테이블에 고유 키 누락

이제 시스템에서 &#39;eav_attribute_option_value&#39; 테이블의 &#39;option_id&#39; 및 &#39;store_id&#39; 열에 고유 키를 포함하므로 옵션이 동일한 저장소 보기에 대해 여러 값을 가질 수 없습니다. 이전에는 코드가 잘못되면 동일한 스토어 보기에 대해 옵션이 여러 값을 갖게 되어 제품이나 특성을 편집할 때 문제가 발생할 수 있었습니다.

_AC-6738 - [GitHub 문제](https://github.com/magento/magento2/issues/24718) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/28796)_

#### [문제] 하드코딩된 값 대신 카테고리 제품 인덱서에 가시성 클래스를 사용합니다.

이제 시스템은 하드코딩된 값 대신 카테고리 제품 인덱서에 대한 가시성 클래스를 사용하여 모듈화를 개선합니다. 이전에는 카테고리 제품 인덱서에서 하드코딩된 값을 사용하여, 유연성과 적응성을 제한했습니다.

_AC-8297 - [GitHub 문제](https://github.com/magento/magento2/issues/37200) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37199)_

#### 통화 코드가 새 제품 위젯에서 변경되지 않음

이제 프론트엔드에서 통화가 변경되면 시스템에서 새 제품 위젯의 통화 코드를 올바르게 업데이트하므로 사이트 전체에 걸쳐 통화가 일관되게 표시됩니다. 이전에는 프론트엔드의 통화를 변경해도 새 제품 위젯에 표시되는 통화 코드에는 영향을 주지 않았습니다.

_AC-9375 - [GitHub 문제](https://github.com/magento/magento2/issues/37898) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37899)_

#### 구성 가능한 제품에 대한 PLP에 정기 가격이 표시되지 않음

이제 특별 가격이 있는 하위 제품이 있는 구성 가능한 제품의 제품 목록 페이지에 일반 가격이 표시됩니다.

_ACP2E-2224 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

#### Visual Merchandising Grid에 스톡 정보가 올바르게 표시되지 않음

이제 선택한 스토어에 따라 스톡이 표시됩니다.

_ACP2E-2478 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/bdbf97ea)_

#### 위젯 콘텐츠가 cms 페이지에서 업데이트되지 않음

이제 시스템이 제품이 새 것으로 설정되어 저장될 때 CMS 페이지의 위젯 콘텐츠를 업데이트하여 페이지에 업데이트된 제품 컬렉션이 표시되도록 합니다. 이전에는 캐시의 위젯에 사용된 캐시 ID가 잘못되어 새 제품을 표시하도록 페이지가 업데이트되지 않았습니다.

_ACP2E-2621 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### 번들 제품의 고급 가격 절감 문제

번들 제품 절약 성능 개선.

_ACP2E-2630 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### 카탈로그 가격 규칙을 만들 때 [온-프레미스] 색인 재지정 프로세스가 비효율적입니다.

이제 카탈로그 가격 규칙을 저장하면 인덱서가 무효화되지 않고 영향을 받는 제품만 다시 인덱싱됩니다.

_ACP2E-2652 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

#### CSV 가져오기를 통해 날짜 및 시간 유형 제품 속성 업데이트

이제 datetime 속성은 내보낸 데이터의 시간 부분을 가집니다. 가져오기를 사용하여 이러한 속성에 대한 시간을 업데이트할 수도 있습니다. 또한 &quot;Fields Enclosure&quot;가 활성화된 경우 &quot;additional_attributes&quot; 열의 속성 값은 큰따옴표로 묶입니다.

_ACP2E-2679 - [GitHub 문제](https://github.com/magento/magento2/issues/38306) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 요청에서 웹 사이트 ID가 잘못된 경우 적절한 오류 메시지 없음

이제 요청에서 웹 사이트 ID가 잘못된 경우 표시할 적절한 오류 메시지가 추가되었습니다. 이전에는 요청에서 웹 사이트 ID가 잘못되었을 때 유효성 검사가 없었습니다.

_ACP2E-2689 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/39d54c2d)_

#### 이미지에 영향을 주지 않는 기존 예약된 업데이트를 삭제하면 제품 이미지가 손실됩니다

스테이징 업데이트를 삭제하는 동안 제품 이미지가 제거되지 않습니다.

_ACP2E-2785 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8931218)_

#### [클라우드] 계층 가격과 함께 사용할 때 잘못된 번들 제품 가격

이전에는 특정 백분율 할인을 소수점 2로 반올림할 때 장바구니 및 제품 목록 페이지/제품 세부 사항 페이지에 대해 다른 최종 가격이 생성되었습니다. 이 수정 사항이 적용되면 번들 제품의 최종 가격은 제품 세부 사항 페이지, 제품 목록 페이지 및 미니 장바구니 페이지와 동일합니다.

_ACP2E-2799 - [GitHub 문제](https://github.com/magento/magento2/issues/38091) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b2286ecf)_

#### 카탈로그 프로모션 규칙이 quantity_and_stock_status 속성과 함께 작동하지 않음

이제 admin 측에서 새 제품을 생성할 때 이전에 고려하지 않았던 quantity_and_stock_status 속성을 카탈로그 프로모션 규칙으로 고려합니다.

_ACP2E-2805 - [GitHub 문제](https://github.com/magento/magento2/issues/35627) - [GitHub 코드 기여](https://github.com/magento/inventory/commit/cf34971d)_

#### REST API를 통해 가격을 업데이트하는 동안 제품 엔티티 updated_at 열 값이 업데이트되지 않음

관리자의 &#39;마지막 업데이트 날짜&#39; 열은 REST API를 통해 기존 제품을 업데이트하는 동안 적절한 날짜/시간으로 업데이트됩니다. 이전에는 &#39;마지막 업데이트 날짜&#39; 열이 제대로 업데이트되지 않았습니다.

_ACP2E-2837 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/39d54c2d)_

#### 제품 가져오기를 통해 고유하지 않은 값을 설정할 수 있습니다

이제 시스템은 제품 가져오기 중에 고유 제품 속성에 대해 고유 값 제약 조건을 올바르게 적용하여 해당 속성에 대한 중복 값을 표시하지 않습니다. 이전에는 제품 가져오기를 통해 고유 값을 갖도록 구성된 제품 속성에 대해 고유하지 않은 값을 설정할 수 있었습니다.

_ACP2E-2840 - [GitHub 문제](https://github.com/magento/magento2/issues/38445) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7e0e5582)_

#### 단일 스토어 모드가 활성화되면 프론트엔드의 제품은 스토어별 데이터를 사용합니다

이전에는 기본 스토어 보기에 대해 단일 스토어 모드를 활성화했을 때 변경 사항이 웹 사이트 수준 범위로 마이그레이션되지 않았습니다. 이 수정 사항이 적용된 후 단일 스토어 모드를 활성화하면 기본 스토어 보기 관련 데이터가 웹 사이트 수준별 데이터와 동기화되어 제품 및 카테고리에 대해 가능한 충돌을 해결합니다.

_ACP2E-2843 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8931218)_

#### rest API를 사용하여 범주에서 &quot;기본 정렬 기준&quot;을 설정할 수 없음

REST / SOAP API 요청을 통해 범주에서 default_sort_by를 올바르게 업데이트

_ACP2E-2857 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/57a32313)_

#### [클라우드] 판매자가 위시리스트 수 관련 문제에 직면했습니다.

한 스토어에서 위시리스트에 제품을 추가해도 동일한 브라우저에 열려 있는 다른 스토어의 위시리스트 수가 더 이상 증가하지 않습니다. 이전에는 두 스토어가 동일한 브라우저에 로드되면 다른 스토어에서도 위시리스트 수가 증가했습니다.

_ACP2E-2871 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 번들 제품을 사용할 때 프론트엔드의 카테고리 페이지에 빈 슬롯이 표시됩니다.

현재 스토어 컨텍스트에서 구입할 수 없는 번들 제품은 더 이상 색인화되지 않습니다.

_ACP2E-2874 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/bc37ec76)_

#### 다중 웹 사이트 아키텍처에서 견적의 [클라우드] 문제

기존에는 서로 다른 통화와 고객 그룹을 가진 다중 웹 사이트 아키텍처가 매장에 할인을 제대로 적용하지 못했다. 이 수정 사항이 구현되면 다른 고객 그룹 가격 할인이 적용된 다중 웹 사이트 아키텍처가 다른 스토어에 성공적으로 적용됩니다.

_ACP2E-2905 - [GitHub 문제](https://github.com/magento/magento2/issues/38506) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658 찾을 수 없는 TypeError: 번들 제품을 편집하는 동안 dataRecord.slice

번들 제품에서 옵션을 삭제하는 동안 브라우저 콘솔에 Javascript 오류가 없습니다.

_ACP2E-2909 - [GitHub 문제](https://github.com/magento/magento2/issues/38505) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/93d50f8d)_

#### 주문 확인 시 [Cloud] 번들 제품의 가격이 잘못됨

기본 통화 이외의 통화가 사용된 경우 Storefront의 번들 옵션에 대해 올바른 금액이 순서대로 표시됩니다.

_ACP2E-2950 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

#### YouTube 비디오 추가 버그

제품 이미지 및 비디오는 전역 범위로 구성됩니다. 한 범위에서는 제품 비디오를 사용할 수 없고 다른 범위에서는 사용할 수 없는 경우 Youtube API 키 설정이 전역 범위로 설정되었습니다.

_ACP2E-2956 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

#### store_id=0에 대해서만 [Cloud] URL 업데이트

이제 &quot;URL 경로&quot;가 올바른 저장소 ID와 함께 저장됩니다. 이전에는 저장소 ID가 잘못되어 범주를 이동할 때 데이터베이스에 잘못된 URL 경로가 남아 있었습니다.

_ACP2E-2964 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all이 실행되어 오류가 발생했습니다.

REST API 호출에서 잘못된 제품 링크 데이터가 더 이상 심각한 오류를 일으키지 않습니다.

_ACP2E-3009 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] 모바일 문제에서 PDP 이미지만 고정할 수 없습니다.

이제 시스템에서 Chrome의 모바일 보기에서 제품 세부 사항 페이지 이미지에 대한 핀치-투-줌 기능을 지원하여 모바일 사용자 경험을 향상시킵니다. 이전에는 Chrome에서 모바일 보기에서 이미지를 두 번 탭해도 예상대로 이미지가 확대되지 않았습니다.

_ACP2E-3029 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/148c3ead)_

#### 옵션 이름이 0인 LayeredNavigation에 레이블이 없습니다.

속성 값 0에 대해 빈 값 검사기를 건너뛰어 문제를 해결했습니다. 이전에는 비어 있는 것으로 간주되어 문제가 발생했습니다.

_ACP2E-3058 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 고객은 다른 고객 그룹의 가격을 확인합니다

요청의 X-Magento-Vary 이전 값으로 인해 고객 그룹 관련 정보가 잘못된 세그먼트에 저장된 문제가 해결되었습니다.

_ACP2E-3069 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d1f7dc95)_

#### 번들 옵션을 삭제할 때 오류 발생

이제 시스템에서 오류를 트리거하거나 페이지가 응답하지 않도록 하지 않고 번들 옵션을 올바르게 삭제합니다. 이전에는 번들 옵션을 삭제하려고 하면 &quot;페이지가 응답하지 않음&quot; 오류가 발생하여 제품이 저장되지 않았습니다.

_ACP2E-3076 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] 이미지 파일이 New Relic 오류 로그에 없습니다.

이제 시스템에서 사용자 지정 자리 표시자 이미지를 로컬 스토리지에 동기화하여 AWS S3와 같은 원격 스토리지를 사용할 때 올바르게 렌더링되도록 합니다. 이전에는 원격 스토리지를 사용할 때 사용자 지정 자리 표시자 이미지를 렌더링하지 못해 이미지 표시 및 오류 로그가 끊어졌습니다.

_ACP2E-3100 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d1f7dc95)_

#### 새 제품 RSS 피드가 캐시로 인해 새 제품으로 업데이트되지 않습니다.

이제 제품이 새 제품으로 설정되어 저장될 때 새 제품에 대한 RSS 피드가 업데이트됩니다

_ACP2E-3103 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d01ee51e)_

#### [Cloud] 제품 미디어 갤러리 GQL 응답이 이미지 위치별로 정렬되지 않음

이제 시스템에서 GraphQL 응답의 위치별로 미디어 갤러리의 항목을 올바르게 정렬하여 정확한 표시 순서를 보장합니다. 이전에는 미디어 갤러리의 항목이 위치별로 정렬되지 않아 표시 순서가 잘못되었습니다.

_ACP2E-3126 - [GitHub 문제](https://github.com/magento/magento2/issues/37671) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b21e5d91)_

#### [Cloud] 하위 범주 항목은 관리 백엔드의 위젯 편집에 표시되지 않습니다.

새 위젯 페이지의 카테고리 트리에는 더 이상 레벨 5 이상의 카테고리 로드 문제가 없어야 합니다. 이전에는, 레벨 5 이상의 범주를 포함하는 트리를 로드할 때 일부 범주가 누락되었습니다.

_ACP2E-3136 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/148c3ead)_

#### [클라우드] 실제 모바일 장치에서 두 손가락 확대/축소 및 이동 문제

이제 시스템은 모바일 장치에서 일관된 이미지 확대/축소 기능을 보장하여 부드럽고 예측 가능한 사용자 경험을 제공합니다. 이전에는 이미지 확대/축소 기능이 일관되지 않았으며 모바일 디바이스에서 볼 때 특정 지점 후에 갑자기 축소되었습니다.

_ACP2E-3198 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

#### 공유 카탈로그에서 제품 할당을 취소하면 위시리스트 제품이 지워지지 않습니다

이제 공유 카탈로그에서 제품을 사용할 수 없는 경우 위시리스트에 항목이 표시되지 않습니다. 이전에는 위시리스트에서 실제로 사용할 수 있는 항목이 없는 경우에도 위시리스트 페이지에 &quot;1개 항목&quot;이 잘못 표시되었습니다.

_ACP2E-3282 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### 관련 제품 모두 선택/모두 선택 취소

이전에는 제품을 수동으로 선택한 경우 관련 제품에 대한 &quot;모두 선택&quot;/&quot;모두 선택 해제&quot; 버튼이 제대로 작동하지 않았습니다. 수정 후 이러한 버튼은 이제 수동 선택 후에도 일관되게 작동하여 모든 제품을 올바르게 선택 또는 선택 취소하도록 합니다.

_ACP2E-3286 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [클라우드] 잘못된 언어로 스톡 경고 전자 메일 번역

서로 다른 언어를 사용하는 여러 스토어 보기가 있는 웹 사이트에 대해 스톡/가격 경고를 보낼 때 경고가 생성된 스토어 보기에 대한 언어가 이메일에 사용됩니다.

_ACP2E-3336 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/9f3e63d1)_

#### 비활성화된 범주는 더 이상 범주 트리에 해당 이름이 회색으로 표시되지 않습니다

이전에는 비활성화된 카테고리가 카테고리 트리에서 회색으로 표시되지 않았습니다. 이제 회색 효과가 표시됩니다.

_ACP2E-3350 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d75cff27)_

#### 구성 가능한 제품 편집 양식 로드로 인해 시간 초과 및 메모리 소진 발생

수정 이전에는 가능한 모든 속성 옵션 조합을 기반으로 구성 가능한 제품 변형이 구성되었습니다. 속성에 옵션이 많은 경우 이로 인해 시간이 오래 걸리고 리소스가 소모되는 작업이 발생했습니다. 이제 구성 가능한 제품 변형이 기존 하위 제품 속성을 기반으로 구성됩니다. 따라서 계산이 훨씬 적으므로 리소스 사용이 개선됩니다.

_ACP2E-3410 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### 색상 견본을 사용할 때 Fotorama가 비디오를 올바로 로드하지 않고 URL을 통해 옵션이 미리 선택되어 있습니다.

이제 URL에 선택한 옵션이 포함된 경우 구성 가능한 제품 세부 사항 페이지에서 제품 비디오가 제대로 렌더링됩니다.

_ACP2E-3454 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### PageBuilder 캐러셀 위젯에 조건과 일치하지 않는 제품이 표시됨

위젯에 사용되는 제품 목록은 이제 카테고리 조건을 따릅니다

_ACP2E-3461 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### 그룹에 잘못된 수량이 있는 경우 그룹의 모든 제품에 대해 유효성 검사 오류가 트리거됨

이제 하나의 제품에 이전에 발생하지 않았던 잘못된 수량이 있을 때 그룹의 모든 제품에 대해 유효성 검사 오류가 올바르게 트리거됩니다.

_ACP2E-3469 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/56463d5e)_

#### 구성 가능한 제품에 [CLOUD] 특별 가격이 표시되지 않음

수정 후 특별 가격 속성에 대한 &quot;제품 목록에 사용됨&quot; 값을 변경해도 구성 가능한 제품에 대한 특별 가격이 표시되는 데는 영향을 주지 않습니다.

_ACP2E-3513 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

#### 프로세스가 종료되면 인덱서 임시 테이블이 정리되지 않습니다.

이제 인덱서 프로세스가 종료되면 CatalogRule 인덱서 임시 테이블이 정리됩니다.

_ACP2E-3516 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

#### 2.4.7-p3의 [QUANS] 코어 단위 테스트 실패

이 테스트는 단위 테스트 개선 사항이므로 릴리스 노트가 필요하지 않습니다.

_ACP2E-3520 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

#### 여러 출처가 있는 그룹화된 제품에 대한 재고 수량 검색의 성능 문제

그룹화된 제품 및 번들 제품 편집 페이지는 이제 할당된 제품에 많은 인벤토리 소스가 있을 때 최적화됩니다.

_ACP2E-3533 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/0208e433)_

#### ACP2E-3389 수정

앵커 범주가 많은 경우 관리자 범주 페이지의 성능이 개선되었습니다.

_ACP2E-3641 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/982b1c42)_

### 카탈로그, 컨텐츠

#### [Cloud] 캐시가 무효화되지 않습니다.

이전에는 CMS 페이지를 업데이트된 디자인 레이아웃으로 저장할 때 프런트 엔드에 적절히 반영되지 않았습니다. 이 수정 사항이 적용되면 디자인 레이아웃을 변경하고 CMS 페이지를 저장하면 적절한 디자인 레이아웃이 프런트 엔드에 표시됩니다.

_ACP2E-3063 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

#### 콘텐츠 위젯에서 [Cloud] 앵커/비앵커 범주가 반전됨

이전에는 [표시 위치] -> [앵커 범주]를 선택했을 때 앵커와 비앵커 간의 상위-하위 관계를 반영하지 않은 모든 범주가 표시되었습니다. 이 수정 사항이 적용되면 [표시 켜기] -> [앵커 범주]에는 [앵커 범주] (선택 가능)만 표시되고, [표시 켜기] -> [앵커 이외의 범주] 에는 [앵커 이외의 범주] (선택 가능)가 표시됩니다

_ACP2E-3131 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

#### 위젯과 작동하지 않는 카테고리

이전에는 다른 앵커/비 앵커 범주에 대해 CMS 블록을 저장한 경우 맨 앞에 표시될 때 하위 카테고리에 대해 작동하지 않았습니다. 이 수정 사항이 적용되면 블록은 다른 카테고리의 프런트 엔드에 표시됩니다.

_ACP2E-3152 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d01ee51e)_

### 카탈로그, 프레임워크

#### 주문 가져오기(선적|대변 메모|송장)수집 - 수집이 로드되지 않아야 함

이제 시스템에서 선적 및 대변 메모에 대한 수집이 주문에서 검색될 때 미리 로드되지 않도록 하여 이러한 수집에 추가 필터 또는 주문을 적용할 수 있습니다. 이전에는 이러한 컬렉션이 자동으로 로드되어 더 이상 수정되지 않았습니다.

_AC-9111 - [GitHub 문제](https://github.com/magento/magento2/issues/37561) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37562)_

#### [클라우드]후속 작업: 데이터에 변경 사항이 있는지 확인할 때 데이터 비교가 일치하지 않습니다.

이전에는 데이터 변경 없이 항상 저장 개체가 호출되었습니다(int/float/double과 같은 숫자 데이터 필드의 경우). _hasDataChanges 플래그를 true로 트리거하고 저장 함수를 호출합니다. 또한 문자열로 캡슐화된 부동 수치는 확인하지 않습니다. 이 수정 사항이 적용되면 데이터가 변경되는 경우에만 저장 함수가 호출됩니다. int/float/double-check에 대한 데이터 값은 함수에 전달되고 엄격한 유형 일치를 수행합니다

_ACP2E-2949 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8931218)_

### 카탈로그, GraphQL

#### GraphQL에서 카테고리 필터 처리: includeDirectChildrenOnly 및 category_uid

category_uid로 필터링하는 동안 직접 하위 카테고리만 가져옵니다.

_ACP2E-3090 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] Graphql 제품 정렬이 작동하지 않음

변수가 필드를 전달할 때 여러 필드를 기준으로 한 GraphQl 제품 정렬이 이제 예상대로 작동합니다.

_ACP2E-3166 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8459b17d)_

#### GraphQL 제품에서 계층 가격이 잘못된 값을 반환함(Storefront와 비교)

수정 후 graphql 요청에 대해 반환된 제품의 계층 가격은 한 항목당 가격을 가집니다.

_ACP2E-3312 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

### 카탈로그, 가격 책정, 스테이징 및 미리보기

#### 동시에 많은 수의 제품을 업데이트할 때 [Cloud] 특별 가격 API 끝점이 오류를 반환함

이제 특별 가격 벌크 업데이트 API는 각 제품 및 날짜 범위에 대해 여러 개의 예정된 업데이트 대신 각 날짜 범위에 대한 단일 캠페인을 만듭니다. 또한, 많은 SKU를 더 빨리 처리하기 위해 동시 API 요청을 지원합니다.

_ACP2E-2672 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f89a447e)_

### 카탈로그, 제품

#### 제품 편집의 범주 선택 트리가 카탈로그->범주에 설정된 순서와 다릅니다.

이제 시스템에서 카탈로그->범주에 설정된 것과 동일한 순서로 제품 편집 섹션에 범주 선택 트리를 올바르게 표시하므로 큰 카탈로그에서 제품을 보다 쉽게 관리할 수 있습니다. 이전에는 카탈로그->범주에 설정된 표시 순서에 관계없이 제품 편집 섹션의 범주 트리가 범주 생성 순서로 표시되었습니다.

_AC-7050 - [GitHub 문제](https://github.com/magento/magento2/issues/36101) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36104)_

### 카탈로그, SEO

#### 페이지 > 1일 때 범주의 잘못된 표준 URL

이전에는 다중 페이지 콘텐츠에 대한 표준 URL이 제대로 작동하지 않아 기본 URL이 일관되게 표시되었습니다. 그러나 수정 사항이 구현되면 이제 다중 페이지 콘텐츠의 표준 URL에 페이지 ID가 있는 URL이 올바르게 표시됩니다.

_ACP2E-3653 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/982b1c42)_

### 카탈로그, 검색

#### 카테고리 및 검색에 표시되지 않지만 직접 연결되는 링크가 작동하는 제품

이전에는 price_* attribute_code가 있는 Yes/No 사용자 지정 속성이 색인화에서 작동하지 않았습니다. 이 수정 후에는 Yes/No 사용자 지정 속성이 예상대로 작동합니다.

_ACP2E-2757 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### 특정 범주 페이지의 [클라우드] 탄력적인 검색 오류

이전에는 구성 티켓을 사용할 때 여러 제품에 대해 가격을 0으로 지정하면 프론트엔드 카테고리 페이지에서 예외가 발생합니다. 여러 제품 가격이 0이고 프론트엔드에 카테고리 페이지를 로드할 때 이 수정 사항이 적용되면 예외가 발생하지 않고 카테고리 페이지를 성공적으로 로드합니다.

_ACP2E-3053 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8931218)_

#### 개체를 만드는 동안 형식 오류가 발생했습니다. Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor 예외

수정 후 $data를 지정하지 않고 Magento\CatalogSearch\Model\Indexer\Fulltext 클래스의 인스턴스를 만들 수 있습니다.

_ACP2E-3345 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

#### Magento 관리자에 저장한 후 제품에 대한 [CLOUD] 문제가 프론트엔드에 표시되지 않습니다.

수정 후 긴 이름의 하위 제품이 있는 구성 가능한 제품은 상점 앞에 표시되지 않습니다.

_ACP2E-3521 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

### 클라우드

#### [Cloud] PHPSESID가 각 POST 요청을 변경하고 있습니다.

L2 Redis 캐시가 활성화되고 고객이 백엔드에서 업데이트된 경우 PHPSESID는 더 이상 로그인한 고객의 프론트엔드 영역에서 POST 요청을 다시 생성하지 않습니다

_ACP2E-3010 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6a185204)_

#### 사이트 맵 생성 경고

수정 후 사이트 맵이 시스템 tmp 디렉토리에 생성되고 최종 대상에 복사됩니다.

_ACP2E-3532 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

### 콘텐츠

#### 최근에 본 위젯의 가격 표시와 관련된 [문제]

이제 시스템에서 &quot;최근에 본 제품&quot; 위젯에 품절 단순 제품의 가격을 올바르게 표시하므로 모든 위젯과 제품 목록 페이지에서 일관성을 유지할 수 있습니다. 기존에는 가격 로딩 템플릿의 조건 때문에 품절 간편 상품 가격이 &#39;최근 본 상품&#39; 위젯에 표시되지 않았다.

_AC-10539 - [GitHub 문제](https://github.com/magento/magento2/issues/38167) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38159)_

#### [문제] acl.xsd 파일에서 올바른 오타 및 문법

이제 시스템이 acl.xsd 파일의 오타 및 문법 오류를 수정하여 설명서의 명확성과 정확성을 향상시킵니다. 이전에는 acl.xsd 파일에 오류 및 잘못된 문법이 포함되어 있어 혼동을 일으킬 수 있었습니다.

_AC-10596 - [GitHub 문제](https://github.com/magento/magento2/issues/38061) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38046)_

#### Pagebuilder 배너 이미지가 갤러리에 표시되지 않음

이제 시스템에서 Pagebuilder 갤러리에서 새로 만든 폴더에 업로드된 배너 이미지를 올바르게 표시하므로 이전 콘솔 오류가 제거됩니다. 이 수정 이전에는 배너 이미지가 새 폴더에 업로드된 경우 갤러리에 표시되지 않아서 콘솔 오류가 발생했습니다.

_AC-10845 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c8f87c25)_

#### 2.4.5-p8로 업데이트한 후 &quot;영역 코드가 설정되지 않음&quot;

이제 시스템은 Magento_CSP 모듈이 활성화되고 &quot;dev/js/translate_strategy&quot;가 &quot;embedded&quot;로 설정된 경우, &quot;Area code not set&quot; 오류를 트리거하지 않고 정적 콘텐츠 배포 프로세스를 성공적으로 완료합니다. 이전에는 이러한 조건에서 정적 콘텐츠 배포 프로세스가 실패하고 &quot;영역 코드가 설정되지 않음&quot; 오류가 발생했습니다.

_AC-12283 - [GitHub 문제](https://github.com/magento/magento2/issues/38845) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38922)_

#### 위젯 범주 트리가 올바르게 렌더링되지 않음

_AC-12692 - [GitHub 문제](https://github.com/magento/magento2/issues/39008) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/58e40ceb)_

#### 디자인 구성 페이지에서 테마를 변경할 때 &quot;기본값 사용&quot; 메시지를 볼 수 없음

이제 디자인 구성 페이지에서 선택한 테마에 따라 &quot;기본값 사용&quot; 메시지를 표시하는 별도의 열이 시스템에 포함됩니다. 이를 통해 기본값 상태를 명확하고 가시적으로 확인할 수 있습니다. 이전에는 &quot;기본값 사용&quot; 메시지가 표시되지 않아 선택한 테마의 상태에 대한 혼동이 발생했습니다.

_AC-13054 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/47b448e2)_

#### [문제] TinyMCE 플러그인과의 이전 버전과의 호환성을 다시 복원합니다(그 후)...

이제 시스템은 TinyMCE 플러그인과의 이전 버전과의 호환성을 복원하므로 다른 위치에서 위젯을 사용할 때 플러그인 내에서 정의된 함수를 호출할 수 있습니다. 이전에는 TinyMCE 버전 변경으로 인해 플러그인이 위젯을 객체로 반환하지 않아 위젯 인스턴스에서 특정 함수를 호출하려고 할 때 오류가 발생했습니다.

_AC-13569 - [GitHub 문제](https://github.com/magento/magento2/issues/39262) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39258)_

#### 제품 페이지의 WYSIWYG 편집기에서 [문제] 파일 업로드 문제

이제 시스템에서 폴더 트리를 올바르게 표시하고 &#39;이미지 및 비디오&#39; 탭을 먼저 확장한 후에도 제품 페이지의 WYSIWYG 편집기에서 이미지를 업로드할 수 있습니다. 이전에는 &#39;이미지 및 비디오&#39; 탭을 먼저 확장하면 폴더 트리가 표시되지 않고 WYSIWYG 편집기에서 이미지를 업로드하려고 할 때 오류 메시지가 표시되었습니다.

_AC-9638 - [GitHub 문제](https://github.com/magento/magento2/issues/38026) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38025)_

#### [On-PREM] 동적 차단 문제

이제 동적 블록 내에서 위젯이 제대로 렌더링되고 있습니다.

_ACP2E-2392 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a12063bd)_

#### 뉴스레터 템플릿의 문제로 인해 [클라우드] 프론트엔드가 로드되지 않음

CMS 페이지 콘텐츠 섹션을 통해 블록을 추가해도 더 이상 예외가 발생하지 않습니다

_ACP2E-2693 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Cloud] 로그에 발견된 예외 조사: InvalidArgumentException: vendor/magento/module-rule/Model/ConditionFactory.php에 클래스가 없습니다.

PageBuilder 제품 콘텐츠 설정에서 조건을 제거해도 더 이상 예외가 로그 파일에 기록되지 않습니다. 이전에는 PageBuilder 제품 콘텐츠 설정에서 조건을 제거하면 프론트엔드에 문제를 일으키지 않지만 중요한 예외가 로그에 기록되었습니다.

_ACP2E-2836 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### 단일 스토어 모드로 전환 - 글로벌 콘텐츠가 더 이상 표시되지 않음

이제 시스템은 단일 스토어 모드를 활성화할 때 스토어 보기 디자인 구성을 웹 사이트 디자인 구성과 동기화하여 컨텐츠 업데이트가 프론트엔드에 표시되도록 합니다. 이전에는 단일 스토어 모드로 전환하면 콘텐츠 업데이트가 상점 앞에 반영되지 않았습니다.

_ACP2E-2842 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7e0e5582)_

#### 링크 및 기타 유용성 결함을 추가하려고 하면 페이지 빌더가 이미지를 대체합니다.

이제 이미지를 클릭하면 페이지 빌더 텍스트 요소에 있는 wysiwyg 편집기의 링크가 이미지, 링크 구성 대화 상자에 적절한 데이터를 로드합니다. 또한 편집기에서 이미지에 대한 링크 추가도 제대로 작동합니다. 이전에는 이미지가 링크로 대체되었습니다.

_ACP2E-2903 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### 디렉터리에 0바이트 이미지가 배치되면 이전 미디어 갤러리에서 이미지를 렌더링하지 못했습니다.

이제 시스템은 기능을 중단하지 않고 미디어 갤러리에서 0바이트 이미지를 처리하므로 디렉터리의 다른 이미지를 예상대로 표시하고 선택할 수 있습니다. 이전에는 미디어 갤러리에 0바이트 이미지가 있으면 디렉터리의 모든 이미지를 표시하거나 선택할 수 없었습니다.

_ACP2E-2970 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/35b1b1da)_

#### CMS 블록을 편집할 때 페이지 빌더 오류 발생

이제 시스템은 &quot;페이지 빌더가 잠금을 해제하지 않고 5초 동안 렌더링하고 있습니다.&quot;라는 오류 메시지를 표시하지 않고 페이지 빌더를 사용하여 관리 영역에 변경 사항을 올바르게 저장합니다. 을 클릭합니다. 이전에는 변경 사항을 저장하려고 할 때 이 오류가 발생하여 콘텐츠를 성공적으로 업데이트할 수 없었습니다.

_ACP2E-3064 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [클라우드] 장바구니 섹션에 체크 아웃 또는 장바구니 편집 단추가 없습니다.

이제 번들 제품이 오류 없이 위젯을 통해 장바구니에 추가됩니다.

_ACP2E-3092 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### [클라우드] 이미지 업로드 단추가 작동하지 않습니다

이전에는 PageBuilder의 배너 및 슬라이더에 대한 이미지 업로드 단추가 예상대로 작동하지 않았으며 지금은 이 단추를 누르면 로컬 파일 관리자가 열려 업로드할 이미지를 선택합니다.

_ACP2E-3122 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor(): 인수 #2($height)는 0보다 커야 합니다. 특정 이미지를 업로드할 수 없음

미디어 갤러리를 통해 높이가 0인 이미지를 업로드할 때 관리자에서 오류가 발생하는 문제를 해결하고 sync 명령을 사용하여 에셋을 동기화했습니다. 이전에는 미디어 갤러리를 통해 이미지를 업로드할 수 없었고 특정 이미지가 갤러리에 있는 경우 동기화 명령도 실패합니다.

_ACP2E-3127 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6f4805f8)_

#### Google Maps API와 충돌하는 Prototype.js Array.from

이제 Google 맵이 PageBuilder 편집기에서 제대로 렌더링됩니다. 이전에는 Javascript 오류로 인해 Google 맵이 올바르게 렌더링되지 않았습니다.

_ACP2E-3154 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/148c3ead)_

#### [클라우드] - CMS 슬라이더가 최신 변경 내용을 반영하지 않음

슬라이드 편집 화면에서 저장 이벤트가 트리거되는 동안 슬라이더 목록이 새로 고쳐지도록 하여 문제가 해결되었습니다. 이전에는 이 문제가 트리거되어 발생했습니다.

_ACP2E-3275 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### 페이지 빌더를 사용하여 CMS 블록을 특정 순서로 삽입하면 CSM 페이지에 오류가 발생합니다

이전에 PHP 및 OS(Linux)의 일부 버전에서 PageBuilder를 통해 다른 cms 블록을 참조한 블록의 렌더링이 &quot;알 수 없는 오류가 발생했습니다. 다시 시도하십시오.&quot; 이제 cms 블록의 콘텐츠가 PageBuilder 제어 콘텐츠 내에서 올바르게 렌더링됩니다.

_ACP2E-3326 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### 대형 콘텐츠에 대한 Pagebuilder의 템플릿 미리 보기 실패

큰 컨텐츠로 인해 캔버스 요소가 브라우저 제한을 초과하고 잘못된 값이 반환되어 백엔드 코드가 손상되었습니다(이미지를 제대로 디코딩할 수 없음). 캔버스 크기를 범용 브라우저의 제한으로 제한하여 수정되었습니다.

_ACP2E-3428 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### TinyMCE 7에 글꼴 크기가 없는 최신 보안 업데이트

이제 WYSIWYG 편집기에서 글꼴 크기 및 글꼴 모음 선택기를 사용할 수 있습니다. 이 수정 이전에는 TinyMCE 7을 사용하여 편집기 인터페이스에서 사용할 수 없었습니다.

_ACP2E-3430 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### TinyMCE 7 편집기 글꼴 크기는 관리자가 PX가 아닌 PT로 설정해 주십시오.

수정하기 전에는 WYSIWYG 영역에서 글꼴 크기를 px 단위로 지정할 수 없었습니다. 이제 pt 대신 px로 글꼴 크기를 설정할 수 있습니다.

_ACP2E-3483 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### 페이지 빌더의 제품 콘텐츠 유형이 올바른 메시지 없이 축소됩니다.

수정 전 위젯에 제품이 없을 때 미리보기 html이 제대로 생성되지 않았습니다. 이제 빈 응답이 제대로 생성되고 제품 위젯이 미리보기에서 제대로 표시되고 있습니다.

_ACP2E-3490 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [페이지 빌더]결과를 차단하기 위해 제품 목록을 추가하는 중 오류가 발생했습니다.

이제 페이지 빌더를 통해 차단할 번들 제품 목록을 추가해도 오류가 발생하지 않습니다

_ACP2E-3534 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/344fce23)_

### 고객/고객

#### 프론트엔드 - 고객 생성 페이지에서 생년월일 유효성 검사 실패

moment.js 시스템 종속성을 최신 부 버전으로 업그레이드한 후 모든 유효성 검사가 작동해야 합니다

_AC-12162 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/de4dfb8e)_

#### 국가 드롭다운이 변경되면 지역 텍스트 필드가 재설정되지 않음

이제 드롭다운 메뉴에서 국가가 변경되면 지역 텍스트 필드가 재설정되므로 이전 값이 지속되지 않습니다. 이전에는 드롭다운 목록에서 국가를 변경하면 영역 필드가 재설정되지 않아 마지막으로 저장된 값이 유지되었습니다.

_AC-8499 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3ea26621)_

#### 고객을 삭제해도 로그인 및 삭제된 고객을 위한 Storefront의 모든 브라우저 세션 데이터가 정리되지 않음

이제 고객을 삭제하면 로그인된 고객과 삭제된 고객에 대한 상점 첫 화면에서 모든 브라우저 세션 데이터가 예상대로 정리됩니다. 쇼핑객은 쇼핑을 계속할 수 있고, 브라우저는 자신의 세션을 게스트 세션으로 처리합니다. 이전에는 로그인한 쇼핑객의 고객 계정이 관리자에서 삭제되면 쇼핑객의 브라우저에서 JavaScript 오류가 발생했습니다.

_AC-9240 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7d5e3906)_

### 프레임워크

#### [질문]`app/code/Magento/Translation/etc/di.xml`에서 사용되지 않은 형식 구성

이제 시스템에서 구성에서 사용되지 않는 종속성을 제거하여 전체 코드 청정도 및 효율성을 개선합니다. 이전에는 구성에 기능에 기여하지 않는 사용되지 않는 종속성이 있었습니다.

_AC-10037 - [GitHub 문제](https://github.com/magento/magento2/issues/38030) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38064)_

#### V1/customers/password 끝점 질문/문제

이제 시스템은 API를 통해 암호 변경 요청을 처리할 때 관리 GUI 내에 설정된 제한을 준수하여 암호 재설정 기능의 잠재적인 남용을 방지합니다. 이전에는 API가 관리 GUI에 정의된 규칙 외부에서 암호 변경 요청을 처리할 수 있었으므로 유효한 이메일을 알고 있는 경우 끊임없이 재설정 이메일을 보낼 수 있었습니다.

_AC-10654 - [GitHub 문제](https://github.com/magento/magento2/issues/38238) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 니스 구성은 모든 마케팅 매개 변수를 제외하지 않습니다.

이제 시스템에서 바니시 구성의 모든 공통 마케팅 매개변수를 올바르게 제외하여 정확한 추적 및 분석을 보장합니다. 이전에는 gad_source, srsltid 및 msclkid와 같은 특정 마케팅 매개 변수가 제외되지 않아 데이터 수집이 부정확해질 수 있었습니다.

_AC-10738 - [GitHub 문제](https://github.com/magento/magento2/issues/38298) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39188)_

#### 카탈로그 검색 색인 프로세스 오류 색인 지정 프로세스

이제 시스템은 PHP로 컴파일된 libxml 버전에 관계없이 오류가 발생하지 않고 색인 재지정 명령을 성공적으로 완료합니다. 이전에는, 리인덱싱 명령을 실행하면 특정 버전의 libxml로 PHP를 컴파일할 때 &quot;색인 프로세스 동안 카탈로그 검색 색인 프로세스 오류&quot; 오류가 발생했습니다.

_AC-10838 - [GitHub 문제](https://github.com/magento/magento2/issues/38254) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38553) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

#### created_at, status 및 grand_total 필터를 고객 주문 쿼리에 추가하고 여러 필터 오류를 수정했습니다.

이제 시스템은 고객 주문 쿼리에서 created_at, status 및 grand_total 필터의 사용을 지원하며 여러 필터가 올바르게 적용되지 않던 문제를 해결했습니다. 이전에는 시스템에서 이러한 필터를 지원하지 않으며, 쿼리에 이 두 개 이상 사용된 경우 모든 필터를 적용하지 못했습니다.

_AC-10941 - [GitHub 문제](https://github.com/magento/magento2/issues/38392) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36949)_

#### 관련 / 업셀 / 크로스셀 블록 및 가격 인덱싱에서 무작위로 쿼리가 쇄도함

이제 시스템은 관련 블록, 업셀 및 크로스셀 블록의 쿼리를 최적화하여 성능을 개선하고 과도한 쿼리로 인해 사이트가 다운되는 것을 방지합니다. 이전에는 이러한 블록의 쿼리로 시스템이 오버로드되어 상당한 속도 저하가 발생하고 사이트의 가동이 중단될 가능성이 있었습니다.

_AC-10991 - [GitHub 문제](https://github.com/magento/magento2/issues/36667) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38050)_

#### 예외: 경고: ICU 74.1 (PHP Intl)로 업그레이드한 이후 배열 오프셋에 액세스하려고... -> Calendar.php

Commerce은 쇼핑객 또는 판매자가 상점 또는 관리자를 방문할 때마다 exception.log에 다음 예외를 더 이상 기록하지 않습니다. `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [GitHub 문제](https://github.com/magento/magento2/issues/38214) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38364)_

#### [문제] 양식에 이름이 `method`인 요소가 포함되어 있는 경우 고객 데이터 관련 문제를 수정합니다

이제 &#39;method&#39;라는 이름의 요소가 양식에 있는 경우에도 시스템이 양식 제출에서 &#39;method&#39; 속성을 올바르게 식별합니다. 이렇게 하면 고객 데이터를 정확하게 처리할 수 있습니다. 이전에는 양식 요소의 이름이 &#39;method&#39;인 경우 양식 제출에서 &#39;method&#39; 속성의 식별을 방해하여 고객 데이터 처리에 문제가 발생할 수 있었습니다.

_AC-11476 - [GitHub 문제](https://github.com/magento/magento2/issues/38484) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38449)_

#### [문제] \Magento\Framework\Data\Collection::getItemById에 대한 PHPDocs 수정

\Magento\Framework\Data\Collection::getItemById 메서드에 대한 PHPDocs가 정적 분석 도구의 문제를 해결하면서 가능한 반환 형식으로 null을 포함하도록 업데이트되었습니다. 이전에는 메서드의 PHPDocs가 null을 가능한 반환 형식으로 지정하지 않아 메서드를 조건문에서 사용할 때 정적 분석에서 경고 또는 오류가 발생했습니다.

_AC-11489 - [GitHub 문제](https://github.com/magento/magento2/issues/38485) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38439)_

#### [문제] `setup:di:compile` 동안 올바른 환경 설정만 허용

이제 존재하지 않거나 특별히 제외된 클래스에 대한 기본 설정이 만들어지면 `setup:di:compile` 명령 중에 오류가 발생하여 유효한 기본 설정만 허용됩니다. 이전에는 이러한 시나리오가 자동으로 실패하여 원래 클래스와 관련된 플러그인이 무용지물이 될 가능성이 있었습니다.

_AC-11592 - [GitHub 문제](https://github.com/magento/magento2/issues/38517) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33161)_

#### Magento이 LoggerProxy의 __wakeup 메서드에서 읽기 전용 속성을 수정하려고 합니다.

이제 시스템에서 LoggerProxy의 __절전 모드 해제 방법 중 이전에 읽기 전용 속성을 수정할 수 있으므로 사용자가 문제를 해결하지 않고도 원활한 작업을 수행할 수 있습니다. 이전에는 LoggerProxy의 __wakeup 메서드에서 읽기 전용 속성 값을 재할당하려고 하면 문제가 발생합니다.

_AC-11651 - [GitHub 문제](https://github.com/magento/magento2/issues/38526) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c8f87c25)_

#### [문제] AC-2039 AC-1667 업그레이드 TinyMCE 참조

composer.json에서 tinymce 최신 버전을 업데이트했습니다.

_AC-11681 - [GitHub 문제](https://github.com/magento/magento2/issues/38533) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36543) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker는 여러 스레드에서 작동하지 않습니다.

이제 시스템에서 MView 인덱싱을 위한 프로세스 포크를 지원하여 여러 스레드에서 작업할 때 인덱서 실행 중에 오류가 발생하지 않도록 합니다. 이전에는 여러 스레드에서 ChangelogBatchWalker를 실행하면 다른 스레드에서 사용하는 테이블이 삭제되어 인덱서 실행 중에 오류가 발생했습니다.

_AC-11696 - [GitHub 문제](https://github.com/magento/magento2/issues/38246) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38248)_

#### [문제] 이름이 잘못된 변수 이름 바꾸기

이제 시스템에서 아직 환불될 수 있는 금액이 포함된 변수의 이름을 올바르게 지정하여 디버깅 중에 혼동을 방지할 수 있습니다. 기존에는 이 변수를 totalRefund로 잘못 명명하여 개발자의 오해를 불러일으킬 수 있었다.

_AC-11781 - [GitHub 문제](https://github.com/magento/magento2/issues/38609) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36205)_

#### [문제] XML을 통해 현재 링크에 사용자 지정 특성을 전달합니다.

이제 시스템에서 사용자 지정 속성을 XML을 통해 현재 링크에 전달할 수 있으므로 링크가 현재 페이지인 경우에도 이러한 속성이 올바르게 표시되도록 할 수 있습니다. 이전에는 getAttributesHtml() 메서드가 현재 링크에 사용되지 않아 현재 페이지 링크에 대한 사용자 지정 속성이 표시되지 않았습니다.

_AC-11809 - [GitHub 문제](https://github.com/magento/magento2/issues/38500) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30070)_

#### 기본 제공 FPC 캐시가 일부 구성의 경우 2.4.7에서 손상되었습니다.

이제 MAGE_RUN_CODE 매개변수가 설정되면 시스템이 페이지를 올바르게 캐시하여 최적의 성능을 보장합니다. 이전에는 이러한 조건에서 페이지가 캐시되지 않아 잠재적인 성능 문제가 발생했습니다.

_AC-11819 - [GitHub 문제](https://github.com/magento/magento2/issues/38626) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38646) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [문제] 개발자와 프로덕션 모드 간의 불일치를 처리하는 예외 수정

이제 시스템은 개발자와 프로덕션 모드 간에 예외를 일관되게 처리하므로 예외가 throw될 때 로그인 페이지로 예기치 않은 리디렉션을 방지할 수 있습니다. 이전에는 예외 처리가 일치하지 않으면 예외 메시지가 표시되지 않고 프로덕션 모드에서 로그인 페이지로 리디렉션될 수 있었습니다.

_AC-11829 - [GitHub 문제](https://github.com/magento/magento2/issues/38639) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37712)_

#### token_list.phtml에서 &#39;PayPal 계정&#39; 번역 바꾸기

이제 시스템은 토큰화 가능한 계정 결제 방법에 대한 섹션에 &quot;PayPal 계정&quot; 대신 &quot;계정&quot;으로 레이블을 지정하여 해당 기능을 더 잘 나타낼 수 있도록 합니다. 기존에는 이 부분에 &#39;PayPal 계정&#39;이라는 딱지가 붙었는데, 이는 다른 토큰화 가능한 계정 결제 수단이 추가됐을 때 오해의 소지가 있었다.

_AC-11852 - [GitHub 문제](https://github.com/magento/magento2/issues/35622) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37959)_

#### Magento\Catalog\Model\ProductRepository 클래스에서 이전 버전과의 호환성이 손실되었습니다.

이제 ProductRepository 클래스는 Initialization Helper 클래스를 두 번째 매개 변수로 복원하여 이전 버전과의 호환성을 유지하므로 이 클래스에서 확장하는 모듈이 예상대로 작동하도록 합니다. 이전에는 ProductRepository 클래스의 생성자에서 Initialization Helper를 제거하면 이전 버전과의 호환성이 손실되어 사용자가 해결 방법을 사용해야 했습니다.

_AC-11874 - [GitHub 문제](https://github.com/magento/magento2/issues/38669)_

#### [문제] 정적 콘텐츠 배포 - 유형 오류

이제 시스템은 정적 콘텐츠 배포 중에 빈 LESS 파일을 올바르게 처리하며 &quot;LESS 파일이 비어 있습니다&quot; 오류 메시지를 표시합니다. 이전에는 배포 중에 빈 LESS 파일이 발생하면 잘못된 유형 오류가 발생했습니다.

_AC-11905 - [GitHub 문제](https://github.com/magento/magento2/issues/38682) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38683)_

#### [문제] [보기] 링크 및 스크립트 태그에서 추가 공간을 제거함

이제 시스템에서는 링크 및 스크립트 태그에 추가 공백이 없도록 하여 보다 깔끔하고 효율적인 코드를 제공합니다. 이전에는 링크와 스크립트 태그의 속성 사이에 이중 공백을 사용할 수 있었습니다.

_AC-12002 - [GitHub 문제](https://github.com/magento/magento2/issues/32920) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32919)_

#### [문제] 무제한 루프 구성 오류 방지

이제 시스템은 가상 유형 구성에서 자체 참조 매핑을 방지하여 무한 루프를 방지합니다. 이렇게 하면 자체 참조 노드를 역참조할 때 애플리케이션이 무한 루프에 걸리지 않습니다. 이전에는 가상 유형 구성이 자체 참조인 경우 애플리케이션이 무기한 회전합니다.

_AC-12127 - [GitHub 문제](https://github.com/magento/magento2/issues/38822) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38794)_

#### 개체 관리자는 Magento\Csp\Model\Mode\Data\ModeConfigured에 사용되지 않음

이제 ModeConfigured 개체를 만들 때 개체 관리자가 올바르게 사용되므로 이 개체에서 플러그인을 사용할 수 있습니다. 이전에는 개체 관리자가 사용되지 않아 플러그인이 ModeConfigured 개체에 적용되지 않았습니다.

_AC-12299 - [GitHub 문제](https://github.com/magento/magento2/issues/38875) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38886)_

#### 제품 재고 및 가격 알림에서 부정확한 문서 차단 댓글

제품 재고 및 가격 경고의 deleteCustomer 메서드에 대한 문서 블록 주석은 해당 메서드가 웹 사이트에서 고객이 아닌 특정 고객 및 웹 사이트와 관련된 모든 재고 제품 또는 가격 경고를 삭제함을 정확하게 반영하도록 수정되었습니다. 앞서 댓글에는 해당 방법이 홈페이지에서 고객을 삭제하기 위한 것임을 부정확하게 명시했다.

_AC-12540 - [GitHub 문제](https://github.com/magento/magento2/issues/38939) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39001)_

#### [문제] 일반 구성 대신 생성된 데이터에 대해 컴파일된 구성을 사용합니다.

이제 시스템에서 일반 구성 대신 생성된 데이터에 대해 컴파일된 구성을 사용하므로 특정 코드 버전에 의존하는 데이터 오버헤드와 네트워크 전송을 줄일 수 있습니다. 이러한 변경 사항으로 인해 컨테이너 교체 중 공유 인스턴스의 캐시 오버라이드가 방지되므로 안정성이 향상되고 다운타임이 줄어듭니다. 이전에는 특정 코어 클래스에서 공유 구성 유형을 사용했기 때문에 여러 서버에서 코드 버전의 차이로 인해 캐시 재정의 또는 애플리케이션 다운타임이 발생할 수 있었습니다.

_AC-12594 - [GitHub 문제](https://github.com/magento/magento2/issues/38785) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/29954)_

#### [문제] e1ccdb에서 제거된 extjs에서 파일에 대한 참조를 제거하십시오.

이제 시스템은 이전에 제거된 extjs에서 파일에 대한 참조를 제거하여 브라우저의 콘솔 및 시스템 로그 파일에서 오류를 제거합니다. 이전에는 이러한 참조가 참조된 파일의 부재로 인해 오류가 발생했습니다.

_AC-12597 - [GitHub 문제](https://github.com/magento/magento2/issues/38960) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38951)_

#### [문제] 사소한 정리: sprintf의 잘못된 사용이 수정되었습니다. 여기에 자리 표시자 2개만 필요합니다.

이제 시스템에서 적절한 자리 표시자 수와 함께 sprintf 함수를 올바르게 사용하여 코드 청결도와 일관성을 개선합니다. 이전에는 sprintf 함수가 추가 인수와 함께 잘못 사용되었으며, 이로 인해 큰 문제는 발생하지 않았지만 올바른 사용법이 아닙니다.

_AC-12778 - [GitHub 문제](https://github.com/magento/magento2/issues/39062) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38628)_

#### PHP 8.2.15가 FTP 확장을 제거함

이제 시스템에서 FTP 확장을 composer.json 파일의 종속성으로 포함하여 FTP를 통해 CSV 가져오기를 성공적으로 구성합니다. 이전에는 PHP 패키지에서 FTP 확장이 누락되어 FTP를 통해 CSV 가져오기를 구성하려고 할 때 오류가 발생했습니다.

_AC-12857 - [GitHub 문제](https://github.com/magento/magento2/issues/39083) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/47b448e2)_

#### [문제] Magento 모듈에서 참조되는 잘못된 클래스를 수정합니다.

이제 시스템에서 모듈의 클래스를 올바르게 참조하므로 더 원활한 작업을 수행할 수 있으며 클래스가 없는 경우에도 충돌이 발생하지 않습니다. 여기에는 Indexer 및 Creditmemo 모듈의 버그 수정과 PrintAction 클래스의 HttpGetActionInterface 구현이 포함됩니다. 이전에는 잘못된 클래스 참조를 사용하면 오류가 발생하고 잠재적인 시스템 충돌이 발생했으며 creditmemo PDF 파일의 파일 이름 및 재인덱싱 주식과 같은 특정 기능이 예상대로 작동하지 않았습니다.

_AC-12869 - [GitHub 문제](https://github.com/magento/magento2/issues/39126) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37784)_

#### `dev:di:info` CLI 명령의 영역을 정의하는 기능

이제 시스템에서 개발자가 `dev:di:info` CLI 명령의 영역을 정의할 수 있으므로 개발 및 디버깅 프로세스를 향상시킬 수 있습니다. 이전에는 이 명령을 사용하여 전역 영역에 대한 정보만 표시할 수 있었습니다.

_AC-12964 - [GitHub 문제](https://github.com/magento/magento2/issues/38758) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38759)_

#### [문제] 이미지 양식 요소 템플릿에 isMultipleFiles 속성 추가

이 수정 사항으로 이미지가 여러 파일 이미지 양식 요소에 추가되면 &quot;이미지를 찾거나 여기로 드래그하려면 찾아보기&quot; 버튼이 사라지지 않습니다.

_AC-13149 - [GitHub 문제](https://github.com/magento/magento2/issues/39219) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36325)_

#### [문제] 캐시를 최소화하려면 모든 마케팅 가져오기 매개 변수를 제거하십시오.

이제 시스템은 모든 마케팅 get 매개 변수를 제거하여 캐시 활용도를 최적화하고, Varnish가 사용 중일 때 사용되는 논리를 미러링합니다. 이전에는 이러한 매개 변수로 인해 캐시 확장이 발생하고 성능이 저하될 수 있었습니다.

_AC-13279 - [GitHub 문제](https://github.com/magento/magento2/issues/39266) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39099)_

#### [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Directory\Model\AllowedCountries::getAllowedCountries()

정확한 정보를 제공하기 위해 AllowedCountries::getAllowedCountries() 메서드에 대한 PHPDoc가 수정되어 설명서의 명확성과 유용성이 향상되었습니다. 이전에는 이 방법에 대한 PHPDoc에 잘못된 정보가 포함되어 있어 방법의 혼동이나 오용을 초래할 수 있었다.

_AC-13345 - [GitHub 문제](https://github.com/magento/magento2/issues/39246) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39241)_

#### [문제] 더 이상 지원되지 않는 PHP 버전에 대한 일부 코드를 제거합니다.

Magento에서 더 이상 지원되지 않는 PHP 버전의 코드 제거

_AC-13348 - [GitHub 문제](https://github.com/magento/magento2/issues/39361) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39202)_

#### [문제] ImageMagick 어댑터가 php8과 호환되도록 합니다(float에서 int로의 암시적 변환).

이제 시스템은 이미지 치수를 계산할 때 부동 소수를 올바르게 처리하여 부동 소자에서 int로의 암시적 변환으로 인한 오류를 방지하여 PHP8과의 호환성을 보장합니다. 이전에는 이미지 차원을 계산하면 부동 소수가 발생할 수 있으며, 이 경우 암시적으로 반올림되면 오류가 발생합니다.

_AC-13417 - [GitHub 문제](https://github.com/magento/magento2/issues/39402) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37362)_

#### [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Framework\App\Config\ScopeConfigInterface

이 업데이트는 getValue 및 isSetFlag 메서드에 대한 $scopeCode 인수 유형을 정확하게 반영하도록 Magento\Framework\App\Config\ScopeConfigInterface에서 PHPDoc 주석을 수정합니다.

_AC-13537 - [GitHub 문제](https://github.com/magento/magento2/issues/39492) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http 은 이유 구에 따라 다릅니다. 확인

Magento\Framework\Filesystem\Driver\Http::isExists에서 &quot;OK&quot; 구문 검사를 제거했습니다.

_AC-13725 - [GitHub 문제](https://github.com/magento/magento2/issues/39546) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39558)_

#### 고객 그리드 인덱서가 예약별 업데이트 모드에서 제대로 작동하지 않음

이전 고객 그리드는 즉시 업데이트되었지만 수정 후 고객 그리드는 cron 실행 후 업데이트되지만 즉시 반영되지 않습니다.

_AC-13810 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1da9ba6f)_

#### js 파일에 오타가 발생했습니다.

이제 시스템에서 JavaScript 파일의 &quot;구독자&quot;라는 용어를 올바르게 사용하여 관련 기능이 적절히 작동하도록 합니다. 이전에는 JavaScript 파일에 오타가 발생하여 &quot;구독자&quot;라는 용어가 잘못 사용되었습니다.

_AC-6754 - [GitHub 문제](https://github.com/magento/magento2/issues/36163) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36171)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 보다 깔끔하고 표준화된 코드를 만들어 코딩 표준을 준수합니다. 이전에는 `@author` 태그가 일부 모듈에 있었으며, 이는 설정된 코딩 표준에 맞지 않습니다.

_AC-8353 - [GitHub 문제](https://github.com/magento/magento2/issues/37253) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37003)_

#### [문제] `@author`에서 금지된 `Magento_Customer` 태그 제거(2부)

이제 시스템은 특정 모듈에서 금지된 `@author` 태그를 제거하여 보다 깨끗하고 표준화된 코드를 보장함으로써 코딩 표준을 준수합니다. 이전에는 `@author` 태그가 일부 모듈에 있었으며, 이는 설정된 코딩 표준에 맞지 않습니다.

_AC-8356 - [GitHub 문제](https://github.com/magento/magento2/issues/37250) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37000)_

#### editorconfig 구문의 공백이 `[&lbrace;composer,auth&rbrace;.json]`에 대한 규칙을 어깁니다.

이제 편집기의 구문 오류가 해결된 후 시스템에서 작성기 및 auth.json 파일에 4공간 들여쓰기를 올바르게 적용합니다. 이전에는 editorconfig 구문의 공백으로 인해 이러한 파일의 형식이 2칸 들여쓰기로 잘못 지정되었습니다.

_AC-8659 - [GitHub 문제](https://github.com/magento/magento2/issues/37394) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37395)_

#### [문제] cron 오류 로깅 개선

이제 시스템은 cron 프로세스에 대해 STDERR 및 STDOUT를 모두 캡처하고 기록하여 cron 프로세스가 실패한 시나리오에서 중요한 진단 정보를 제공합니다. 이전에는 cron 프로세스 내에 오류 메시지가 기록되지 않았으며 별도의 프로세스에서 실행 중인 cron 그룹에 대한 STDERR 및 STDOUT이 손실되었습니다.

_AC-8662 - [GitHub 문제](https://github.com/magento/magento2/issues/37453) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32690)_

#### [문제] 특정 설치 cli 명령의 출력에 색상을 더 추가합니다.

이제 시스템에서 특정 CLI(Setup Command Line Interface) 명령의 출력에 더 많은 색상을 추가하여 가독성과 사용자 경험을 향상시킵니다. 이전에는 이러한 명령의 출력이 색상 분화의 부족으로 인해 읽기 더 어려웠습니다.

_AC-8984 - [GitHub 문제](https://github.com/magento/magento2/issues/29335) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/29298)_

#### 필요한 주/지역이 있는 새 국가가 추가되면 Magento을 업그레이드하면 general/region/state_required가 재설정됩니다.

이제 필요한 상태의 새 국가가 추가되면 시스템에서 수정된 국가만 &#39;general/region/state_required&#39; 구성에 추가되므로 해당 지역이 비활성화되었다고 가정하는 사용자 정의 코드가 중단되지 않습니다. 이전에는 필수 상태의 새 국가를 추가하면 &#39;general/region/state_required&#39; 구성이 필수 상태의 기본 국가로 재설정되므로 구입이 중단될 가능성이 있었습니다.

_AC-9630 - [GitHub 문제](https://github.com/magento/magento2/issues/37796) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38076)_

#### 복잡한 `calc` 식을 사용하는 php 및 nodejs 라이브러리(grunt) 간의 컴파일 감소 차이

업데이트 wikimedia/less.php:^5.x 후 php &amp; nodejs 라이브러리(grunt) 간의 컴파일 감소 차이를 수정하십시오.

_AC-9712 - [GitHub 문제](https://github.com/magento/magento2/issues/37841) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b34c0a75)_

#### 부분 인덱싱을 실행할 때 &quot;기본 테이블 또는 뷰를 찾을 수 없음&quot; 오류 발생

이제 부분 색인 재지정은 보조 db 연결의 경우 큰 변경 로그에 올바르게 작동합니다

_ACP2E-2692 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### MariaDB를 10.5.1 이상으로 업그레이드한 후 문제 발생

Mysql 업그레이드 후 DB의 날짜/시간 값이 0000-00-00 00:00:00으로 변환되는 문제를 해결했습니다.

_ACP2E-2844 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a12063bd)_

#### 데이터에 변경 사항이 있는지 확인할 때 데이터 비교에서 유형 불일치

이전에는 데이터 변경 없이 항상 저장 개체가 호출되었습니다(int/float/double과 같은 숫자 데이터 필드의 경우). _hasDataChanges 플래그를 true로 트리거하고 저장 함수를 호출합니다. 이 수정 사항이 적용되면 데이터가 변경되는 경우에만 저장 함수가 호출됩니다. int/float/double-check에 대한 데이터 값은 함수에 전달되고 엄격한 유형 일치를 수행합니다.

_ACP2E-2855 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] 가져오기는 디렉터리 변수와 함께 사용할 수 없습니다.

파일 이름과 관계없이 제품을 성공적으로 가져올 수 있습니다.

_ACP2E-2959 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3a7c4d17)_

#### ipad mini에서 메뉴 및 헤더는 모바일로 로드되지만, 대신 데스크톱으로 로드되어야 합니다.

이제 시스템에서 너비가 768px인 장치를 데스크탑으로 처리하여 메뉴와 헤더가 올바르게 로드되도록 합니다. 이전에는 너비가 768px인 장치가 모바일로 처리되어 모바일 보기에서 메뉴 및 헤더가 로드되었습니다.

_ACP2E-2966 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### 외래 키의 경우 db_schema.xml을 통해 열 길이 수정이 작동하지 않음

선언적 스키마를 통해 외래 키로 열을 수정해도 MariaDB에 오류가 발생하지 않습니다

_ACP2E-3230 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

#### 주문 레코드를 저장하면 일부 관계 레코드가 DB에 저장됩니다

성능에 영향을 줄 수 있는 불필요한 업데이트 수정 쿼리가 트리거되기 전에. 수정 후 불필요한 UPDATE 쿼리가 제거되었습니다.

_ACP2E-3361 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

#### [클라우드] 관리자의 경우 콘솔에 JavaScript 오류가 많습니다

이전에는 관리 패널에서 콘솔에 많은 Javascript 오류가 있습니다. 이제 관리 패널에서는 콘솔에 JavaScript 오류가 발생하지 않으며 모든 기본 JavaScript 기능이 문제 없이 성공적으로 실행됩니다.

_ACP2E-3375 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d75cff27)_

#### [클라우드] Magento: 큐 메시지가 삭제되었습니다.

큐 메시지가 이제 제대로 지워지고 있습니다. 수정 전에 SQL 큐 시스템이 사용되고 있는 경우 정리 큐 메시지가 동시에 실행되고 있으면 새 메시지가 삭제되었을 수 있습니다.

_ACP2E-3387 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 캐시 태그에서 해당 캐시 키 항목을 사용할 수 없으므로 캐시 정리가 제대로 작동하지 않습니다

이제 경합 조건을 방지하기 위해 Redis 캐시 가비지 수집기에 대해 LUA 모드가 기본적으로 활성화됩니다

_ACP2E-3537 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a52ff98f)_

#### MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK 값이 무시됩니다.

수정 후 &quot;false&quot;로 설정된 ENV 변수는 문자열 &#39;false&#39;가 아닌 부울 false로 처리됩니다.

_ACP2E-3681 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/982b1c42)_

### 프레임워크, GraphQL

#### [문제] GraphQL 스키마에 대한 사용자 지정 스칼라 유형 지원이 도입됨

이제 시스템은 GraphQL 스키마에 대한 사용자 지정 스칼라 유형을 지원하므로 개발자가 사용자 지정 스칼라 유형 및 구현을 정의할 수 있습니다. 이 기능은 HTML, 이메일, URL, 날짜 등과 같이 유효성 검사가 필요할 수 있는 값을 표시하고 EAV 속성과 같은 고급 사례에 특히 유용합니다. 이전에는 시스템이 GraphQL에서 사용자 지정 스칼라 유형 처리를 지원하지 않았습니다.

_AC-7976 - [GitHub 문제](https://github.com/magento/magento2/issues/36877) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/34651) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

### 프레임워크, UI 프레임워크

#### 구성 값이 잠겨 있더라도 덮어쓸 수 있음

이전에는 bin/magento config:set 명령을 통해 디자인 구성을 설정할 수 없었고, 잠긴 값은 표시된 양식을 조작하여 변경할 수 있었습니다. cli에서 —lock-env 또는 —lock-conf로 설정된 고정 잠금 값은 더 이상 업데이트할 수 없습니다.

_ACP2E-3324 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl은 헤더 값이 유효성 검사를 통과하지 못하더라도 헤더 처리를 실행합니다

이제 시스템에서는 헤더 값이 유효성 검사를 통과하는 경우에만 헤더 처리가 한 번만 실행되도록 하여 보안을 강화하고 잠재적인 취약점을 방지합니다. 이전에는 헤더 값이 유효성 검사를 통과하지 않더라도 헤더 처리가 실행되어 헤더 값의 이중 처리로 인한 잠재적인 취약성과 예기치 않은 동작이 발생했습니다.

_AC-11729 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c8f87c25)_

#### 실제 기프트 카드 옵션에 올바른 정렬 순서가 없습니다.

이제 GraphQL을 통해 쿼리할 때 시스템에서 실제 기프트 카드 제품의 옵션을 올바르게 정렬하여 Luma 테마와 일관된 렌더링을 보장합니다. 이전에는 luma 테마에 따라 정렬 순서가 잘못되어 발신자 이름, 수신자 이름 및 금액과 같은 옵션이 잘못 표시되고 순서가 지정되었습니다.

_AC-8951 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bafc571)_

#### 스테이징 업데이트를 만들기/편집/이동/삭제할 때 [GraphQL] 확인자 캐시가 무효화되었습니다.

이제 시스템은 스테이징 업데이트를 작성, 편집, 이동 또는 삭제할 때 확인자 캐시가 무효화되지 않고 스테이징 업데이트가 엔티티에 적용되는 경우에만 무효화되도록 합니다. 이전에는 스테이징 업데이트가 적용되기 전이라도 확인자 캐시가 조기에 무효화되어 캐시가 불필요하게 무효화되었습니다.

_AC-9157 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 컨텐츠 스테이징 업데이트를 위해 Fastly 캐시가 지워지지 않음

이제 PageBuilder 콘텐츠 관련 엔티티가 업데이트되면 PageBuilder 콘텐츠 응답 캐시가 있는 GraphQL이 무효화됩니다.

_ACP2E-2642 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### 계층화된 선명 비활성화 - Graphql에서 합계를 제거하지 않음

GraphQL 쿼리를 통해 카테고리 집계가 있는 제품 검색을 요청하는 동안 &quot;카탈로그 > 계층화된 탐색 > 디스플레이 카테고리 필터&quot;의 관리 구성 설정이 있을 때 검사를 적용한 후 문제가 해결되었습니다.

_ACP2E-2653 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/12e071c3)_

#### 가격 필터 `&lbrace;from:&quot;0&quot;&rbrace;`이(가) 포함된 GraphQL 제품 호출이 결과를 반환하지 않습니다.

이전에 필터가 있는 0가 제품 검색은 throw된 예외로 인해 결과를 전혀 반환하지 않았습니다. 이제 검색은 예상대로 결과를 반환합니다.

_ACP2E-2928 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e)_

#### 각 StoreView에 대한 GraphQL API에 반영되지 않은 고객 반환 속성에 대한 번역

고객 반환 속성에 대한 번역은 각 StoreView에 대한 GraphQL API에 반영됩니다.
이전에는 각 StoreView에 대한 고객 반환 특성이 GraphQL API에 반영되지 않았습니다.

_ACP2E-2974 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] 노드 견적이 있는 getPurchaseOrder에 대한 GraphQL 호출이 끊어졌습니다.

구매 주문 GraphQL 호출에서는 내부 서버 오류가 발생하지 않고 작업을 실행할 수 있습니다.

_ACP2E-3128 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6f4805f8)_

#### &quot;모든 스토어 보기&quot;에서 제품을 사용할 수 없는 경우 [Cloud] 구성 가능한 제품이 프로덕션 사이트에 표시되지 않습니다.

이제 시스템은 제품이 &quot;모든 스토어 보기&quot;에서 활성화되지 않았지만 특정 스토어 보기 범위에서 활성화되어 있더라도 구성 가능한 제품을 사이트에 올바르게 표시합니다.
이전에는 제품이 &quot;모든 스토어 보기&quot;에서 비활성화되고 특정 스토어 보기 범위에서만 활성화된 경우 GraphQL 응답에 제품 속성이 올바르게 표시되지 않아서 제품이 제대로 표시되지 않았습니다.

_ACP2E-3184 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/3f300077)_

#### 동일한 간단한 제품이 구성 가능한 여러 제품에 할당된 경우 [Cloud] 제품 graphql에서 오류가 발생했습니다.

이전에는, 동일한 간단한 제품을 사용하여 구성 가능한 제품을 별도로 만들면 grapQL이 오류를 반환합니다. 이 수정 사항이 적용되면 동일한 간단한 제품을 사용하여 서로 다른 구성 가능한 제품이 반환됩니다. grapQL은 오류 없이 결과를 반환합니다.

_ACP2E-3190 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/148c3ead)_

#### 다중 사이트 설정에서 사용자 인증 및 사이트 간 토큰 액세스와 관련된 [클라우드] 문제

다중 사이트 설정의 GraphQl 고객 정보 및 장바구니 쿼리는 기본이 아닌 웹 사이트에 고객이 있는지 확인합니다.
이전에 여러 사이트 설정에서 고객이 기본값이 아닌 웹 사이트에 존재하는지 확인하지 않고 쿼리가 작동했습니다.

_ACP2E-3215 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

#### GraphQL 장바구니 항목V2 페이지 매김이 제대로 작동하지 않음

컬렉션 쿼리에서 현재 페이지 인수에 대한 올바른 값을 전달하여 문제를 해결했습니다. 이전에는 현재 페이지를 설정하는 데 잘못된 값이 전달되어 문제가 발생했습니다.

_ACP2E-3253 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8459b17d)_

#### customerCart를 가져올 때 [GRAPHQL] 모델 값을 지정해야 합니다.

이제 데이터베이스에서 견적을 사용할 수 없는 경우에도 GraphQL &#39;customerCart&#39; 쿼리가 빈 장바구니를 만들 수 있습니다. 이전에는 빈 장바구니를 만드는 동안 국가 유효성 검사 문제로 인해 이 작업이 실패했습니다.

_ACP2E-3255 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [GraphQl] 위시리스트 항목은 GraphQl을 통해 표시되지만 상점 앞에는 표시되지 않습니다.

GraphQL을 통해 요청할 때 제대로 나열되지 않는 제품을 위시리스트합니다. 이제 위시리스트 제품은 제공된 스토어 컨텍스트를 기반으로 필터링됩니다.

_ACP2E-3380 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL] 내용과 제목/링크 간 암호 재설정 이메일 불일치

웹 사이트 스토어에 관계없이 암호 재설정 요청을 전송할 때 고객 계정이 등록된 올바른 스토어를 시뮬레이션하여 문제를 해결했습니다.

_ACP2E-3404 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### [Cloud] 제품 GraphQL 쿼리가 현재 웹 사이트에 할당되지 않은 관련 제품을 반환합니다.

이전에는 graphQL 쿼리의 경우 다중 스토어 관련 제품이 제품 쿼리에 대해 제대로 표시되지 않았습니다. 이 수정 사항이 적용된 후 제품의 경우 graphQL 쿼리는 그에 따라 표시되는 다중 스토어 관련 제품을 보여 줍니다.

_ACP2E-3419 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### GraphQL 헤더에 잘못된 스토어 ID를 사용하면 치명적인 메모리 오류가 발생합니다

GraphQL 요청에서 잘못된 스토어 코드를 보내도 더 이상 과도한 메모리 소비가 발생하지 않습니다.

_ACP2E-3447 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 2.4.7의 빈 Graphql 응답에 대한 [Cloud] 500 응답

수정 후에는 잘못된 graphql 요청이 exception.log 파일에 로그되지 않습니다.

_ACP2E-3467 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

#### Graphql API의 [클라우드] 문제

Graphql 애플리케이션 서버를 사용하여 수정하기 전에 고객 주소 요청에서 최신 데이터를 반환하지 않았습니다.

_ACP2E-3492 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152)_

#### 비활성화된 제품이 GraphQL 쿼리의 관련, 상향 판매 및 교차 판매 항목에 여전히 표시됨

이제 Graphql은 비활성화된 관련, 상향 판매 및 교차 판매 제품에 대해 올바른 응답을 제공합니다

_ACP2E-3505 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD]: GraphQl 오류 내부 서버 오류 placeOrder 돌연변이

요청에 쿠폰 코드 정보가 있는 &quot;placeOrder&quot; 돌연변이가 더 이상 내부 오류 예외를 표시하지 않고, 주문이 성공적으로 완료되었습니다. 이전에는 &quot;내부 서버 오류&quot;로 실패했습니다.

_ACP2E-3647 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/982b1c42)_

#### discount_percentage 는 동적 가격이 있는 번들 제품에 대해 계산되지 않습니다

product.price_details의 discount_percentage에 대한 수정 사항이 동적 가격이 활성화되고 할인 쿠폰이 적용된 번들 제품에 대한 올바른 값을 표시하지 않습니다.

_LYNX-426_

#### 번들 제품 중 하나가 품절되었을 때 번들 제품에 여전히 &quot;IN_STOCK&quot;이 표시됩니다.

번들 제품 중 하나가 품절되어도 번들 제품에 여전히 &quot;IN_STOCK&quot;이 표시되던 문제를 해결했습니다.

_LYNX-485_

#### not_available_message 및 only_x_left_in_stock에 동일한 사용 가능한 재고가 표시되지 않습니다.

not_available_message 및 only_x_left_in_stock에서 일관되지 않은 재고 가용성을 표시하는 문제가 해결되었습니다.

_LYNX-486_

#### original_row_total 필드가 잘못된 값을 반환함

사용자 지정 옵션을 선택할 때 잘못된 값을 반환하는 original_row_total 필드의 문제를 해결했습니다

_LYNX-488_

#### 구성에 따라 그룹화된 제품 썸네일이 표시됩니다     .

구성 설정에 따라 그룹화된 제품 썸네일이 표시되도록 하는 문제가 해결되었습니다

_LYNX-503_

#### original_item_price는 할인을 포함하지 않습니다.

할인을 포함하도록 original_item_price 가 업데이트되었습니다.

_LYNX-512_

#### 사용할 수 없음 메시지에 사용 가능한 재고 수량이 표시되지 않습니다.

AddProductsToCart 돌연변이에 대한 오류 메시지와 오류 코드를 &quot;사용할 수 없음&quot; 메시지 구성과 일치하도록 해결했습니다

_LYNX-530_

#### &quot;OUT_OF_STOCK&quot; 상태가 다중 선택 옵션이 있는 사용자 정의 옵션 제품이 있는 단순에서 반환됩니다.

사용자 지정 옵션이 있는 간단한 제품에 대한 stock_status를 수정하도록 인벤토리 패키지의 StockStatusProvider 해결사를 업데이트했습니다.

_LYNX-532_

#### 오류(GQL): cart.itemsV2.items.product.custom_attributesV2가 서버 오류를 반환합니다.

장바구니 쿼리가 사용자 지정 특성 없이 제품을 추가하여 제품의 사용자 지정 특성을 포함할 때 발생하는 서버 오류를 해결했습니다.

_LYNX-533_

#### orders/date_of_first_order는 항상 null을 반환합니다.

orders > date_of_first_order가 항상 null을 반환하는 문제가 해결되었습니다.

_LYNX-536_

#### 고객은 부분적으로 배송된 주문을 취소할 수 없습니다.

고객이 부분적으로 배송된 주문을 취소할 수 없도록 제한하기 위해 유효성 검사가 추가되었습니다.

_LYNX-544_

#### 오류 메시지에 기반한 주문 취소를 위한 오류 코드

이제 주문 취소를 위한 오류 코드는 특정 오류 메시지를 기반으로 합니다.

_LYNX-548_

#### 쿠키 관련 속성을 비공개에서 보호로 다시 이동

Magento\Framework\App\PageCache\Version 클래스 생성자 속성 가시성을 private에서 protected로 되돌립니다.

_LYNX-581_

#### 최대 기본 GraphQL 쿼리 복잡성을 1000개로 늘림

기본 최대 GraphQL 쿼리 복잡도를 300개에서 1000개로 늘렸습니다.

_LYNX-600_

#### GQL - itemsV2 > 원래 행 합계, 가격 범위 가격은 별도의 가격이 있는 파일 옵션이 있는 다운로드 가능한 제품의 경우 $0.00로 반환됩니다.

별도의 링크 구매 옵션이 활성화된 다운로드 가능한 제품이 itemsV2 > 원래 행 합계에 대해 $0를 반환하던 문제가 해결되었습니다. 별도의 가격이 있는 파일 옵션이 있는 제품에 대해 가격 범위가 $0.00로 반환되었습니다.

_LYNX-620_

#### PHP-8.4 버전용 GraphQl 호환성

여러 해결사에서 PHP 8.4와 관련된 GraphQL 호환성 문제를 해결하여 원활한 기능을 보장합니다. CatalogRule, Customer, GiftMessage, GiftCard 및 GiftWrapping 모듈에서 영향을 받은 파일을 업데이트했습니다.

_LYNX-772_

### GraphQL, 인벤토리/MSI

#### 소스 및 대상 장바구니에 동일한 번들 항목이 있는 경우 MergeCart 돌연변이에 예외가 발생합니다.

&#39;-

_ACP2E-2607 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, 인벤토리/MSI, 성능

#### 업그레이드 후 사이트 다운

GraphQl을 통해 번들 제품을 가져오는 성능이 향상되었습니다.

_ACP2E-1716 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, 성능

#### [GraphQL Resolver] Customer Resolver 데이터가 가져오기에서 무효화되지 않음

이제 가져오기를 통해 고객을 편집하거나 삭제할 때 GraphQL customer resolver 캐시가 예상대로 무효화됩니다. 이전에는 캐시가 무효화되지 않았으며 고객 데이터를 가져오는 동안 편집하거나 삭제할 수 있었습니다.

_AC-9569 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, 검색

#### 여러 매개 변수별로 GraphQL 제품 목록을 정렬할 수 없습니다

이제 GraphQl에서 여러 필드를 기준으로 한 제품 정렬이 설명서에 설명된 대로 작동합니다

_ACP2E-2809 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e)_

#### 제품 목록 GraphQL 쿼리는 total_count 10,000개의 제품으로만 제한됩니다.

수정 후에는 검색 결과가 10000 제품에 국한되지 않고 카운트가 10000 이상이더라도 검색 기준과 일치하는 모든 제품을 가져올 수 있습니다.

_ACP2E-948 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, 테스트 프레임워크

#### Magento\GraphQl\App\GraphQlCustomerMutationsTest.php 통합 테스트 실패

&#39;-

_ACP2E-3363 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4cf5e62)_

### 가져오기/내보내기

#### 사용자 지정 옵션 유형: 파일이 제공될 때 제품 가져오기 시 문제 발생(작성된 제품에는 사용자 지정 옵션 가격이 포함되지 않고 제공된 첫 번째 파일 유형 확장명만 표시됨)

이제 시스템에서 &#39;file&#39; 유형의 사용자 지정 옵션으로 제품 데이터를 올바르게 가져오므로 제공된 모든 파일 확장명이 표시되고 사용자 지정 옵션의 가격이 포함됩니다. 이전에는 제품 가져오기 중에 &#39;file&#39; 유형의 사용자 정의 옵션이 두 개 이상의 파일 확장자와 함께 제공된 경우 첫 번째 확장자만 표시되고 사용자 정의 옵션의 가격이 누락되었습니다.

_AC-12172 - [GitHub 문제](https://github.com/magento/magento2/issues/38805) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38926)_

#### 가져오기 작업 내역 그리드의 가져오기 작업 실행 시간이 잘못되었습니다.

보고서 가져오기 실행 시간이 관리자 로케일에 관계없이 올바르게 표시됩니다.

_ACP2E-2710 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 가져오기를 사용하여 동일한 이메일 주소로 중복 고객을 만드는 중

계정 공유가 글로벌로 설정되어 있는 동안 고객 가져오기를 수행하면 시스템에 있는 가져온 고객이 업데이트됩니다.
이전에 가져온 고객이 중복되었습니다.

_ACP2E-2737 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e)_

#### 사용자 정의 가능한 옵션을 복제하는 제품에 대한 가져오기 추가/업데이트

제품 옵션 CSV를 가져오는 동안 제품 옵션에 올바른 저장소를 할당하여 문제를 해결했습니다.
이전에는 해당 저장소 대신 관리자 저장소에 할당되었습니다.

_ACP2E-2902 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 고객 &quot;created_at&quot; 일자 내보내기 시 저장 시간대로 변환되지 않음

열 &#39;created_at&#39; 날짜 값은 고객 내보내기 CSV 섹션의 스토어 시간대를 기반으로 적절한 날짜 형식으로 변환됩니다.

_ACP2E-2990 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3056e9cb)_

#### [클라우드] CSV를 사용하여 데이터 가져오기에서 데이터를 확인하는 동안 오류가 발생했습니다.

CSV 가져오기 중에 데이터를 확인할 때 오류가 발생하지 않습니다. 이전에는, 관리자의 CSV를 사용하여 가져오기 섹션의 데이터를 확인할 때 &quot;이 이메일 및 웹 사이트 코드와 일치하는 고객을 행 1에서 찾을 수 없습니다.&quot;라는 오류 메시지가 표시되었습니다.

_ACP2E-3165 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8459b17d)_

#### 가져오기 단추 누락

데이터가 CSV에서 정확하고 잘못된 레코드로 검사한 후 가져오기 버튼에 누락된 문제를 해결합니다. 이전에는 데이터가 CSV에서 올바르고 잘못된 레코드를 확인하면 가져오기 단추가 표시되지 않았습니다.

_ACP2E-3172 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1819fe73)_

#### 내보낸 고객 주소를 가져올 수 없음

고객 주소 가져오기는 예상대로 진행됩니다. 이전에는 고객 계정 공유 = 글로벌인 경우, 기본 웹 사이트에 제한된 국가 목록이 있는 두 개의 웹 사이트가 있고 가져올 주소는 허용된 국가가 다른 다른 웹 사이트의 주소인 경우 고객 주소 가져오기 파일이 유효성 검사를 통과하지 못했습니다

_ACP2E-3382 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [클라우드] CSV 파일의 잘못된 수량이 오류를 표시하지 않았습니다.

이제 스톡 소스 가져오기로 수량 열의 숫자가 아닌 값에 대한 유효성 검사 오류가 발생합니다. 이전에는 수량 열에서 숫자 값이 아닌 재고 출처를 임포트하면 수량이 0으로 설정되었습니다.

_ACP2E-3448 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5b21b7af)_

#### URL 키가 이미 범주에 속해 있는 경우 제품을 가져올 때 중복되는 URL 키 오류 메시지가 올바르지 않습니다

제품의 URL 키가 이미 범주에 속하는 경우 고객이 제품을 가져오려고 할 때 제품 가져오기 확인 중에 올바른 오류 메시지가 표시됩니다.

_ACP2E-3455 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

#### 제품 내보내기로 인해 4G 메모리 제한이 있는 경우에도 OOM이 발생

이 수정 이전에는 4G 사용 가능한 메모리가 있어도 제품 속성에 수천 개의 옵션 값이 있는 경우 제품 내보내기가 실패했습니다. 이 수정 사항이 적용되면 제품 내보내기에서 csv 파일 내보내기를 완료해야 합니다.

_ACP2E-3475 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

#### [클라우드] 가져오기 프로세스가 서로 충돌함

동일한 관리 사용자가 동일한 사용자 세션을 사용하여 두 개 이상의 가져오기 작업을 수행하는 경우 올바른 메시지가 표시됩니다.

_ACP2E-3527 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

### 가져오기/내보내기, 성능

#### [Cloud] 제품 가져오기 시간이 크게 늘어남

이 문제를 해결하기 전에 10만 개 이상의 항목이 포함된 카탈로그 제품 가져오기의 시간이 크게 단축되었습니다. 수정 후 카탈로그 제품 가져오기가 적시에 실행됩니다.

_ACP2E-3476 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/87d012e5)_

### 설치 및 관리

#### Magento 업그레이드가 MariaDB 11.4 + 2.4.8-beta1에서 실패함

오류 없이 업그레이드해야 합니다.

_AC-13242 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7b336d0a)_

#### 관리 패널에 VCL for Varnish 7 내보내기 버튼 없음

관리 패널에 &quot;Export VCL for Varnish 7&quot; 버튼이 추가되었습니다.

_ACP2E-2102 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

### 인벤토리/MSI

#### 데이터베이스에서 접두사를 사용할 때 구성 가능한 제품의 인벤토리 업데이트에 실패함

이제 데이터베이스에서 접두사를 사용할 때 구성 가능한 제품의 인벤토리를 올바르게 업데이트하므로 오류 메시지가 발생하지 않고 올바른 수량이 저장됩니다. 이전에는 데이터베이스에서 접두사를 사용하는 경우 구성 가능한 제품 내에 단순 제품에 대한 재고 수량을 저장하려고 할 때 오류가 발생했습니다.

_AC-10750 - [GitHub 문제](https://github.com/magento/magento2/issues/38045)_

#### 속성이 있는 맵을 추가하는 동안 Google google API 키가 작동하지 않습니다

이제 시스템에서 최신 Google Maps API 버전 3.56을 지원하므로 사용자가 오류가 발생하지 않고 PageBuilder 메뉴의 맵 콘텐츠 블록을 단계에 성공적으로 추가할 수 있습니다. 이전에는 Google Maps API 버전과의 호환성 문제로 인해 사용자가 맵 콘텐츠 블록을 추가할 수 없어 &quot;문제가 발생했습니다&quot; 오류 메시지가 표시되었습니다.

_AC-11593 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

#### 여러 원본과 손상된 SKU가 있는 주문 항목에 대한 배송을 만들 수 없음

이전에는 데이터베이스를 통해 sku에 공백을 실수로 추가하면 선적 페이지의 오류가 발생하고 자동 트리밍이 사용자에게 친숙한 오류로 간주되어 영향이 없습니다. 따라서 선적이 정상적으로 생성되었습니다.

_AC-13922 - [GitHub 코드 기여](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [테스트] 매장 앞에 재고가 0인 번들 제품 표시

번들 제품은 추가 재고를 사용하여 추가 웹 사이트에 표시되지 않습니다.

_ACP2E-1411_

#### 빈 공간이 있는 제품 목록에 [Cloud] 심각한 문제

이제 제품이 &#39;재고 부족&#39;으로 설정되면 빈 칸이 없는 제품 목록이 올바르게 표시되므로 사용 가능한 제품을 일관되고 정확하게 표시할 수 있습니다. 이전에는 제품을 &#39;재고 부족&#39;으로 설정하면 제품 목록에 빈 공간이 표시되어 레이아웃이 중단되고 고객에게 혼란을 줄 수 있었습니다.

_ACP2E-2794 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/b59e48ca)_

#### MSI 픽업 스토어가 활성화된 경우 주문을 배송할 수 없음

매장 내 픽업이 많은 소스의 경우 생성 배송의 재고 성능 향상

_ACP2E-3335 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Cron reindex가 프론트엔드에서 제품 가용성을 업데이트하지 못했습니다.

이전에는 REST API를 통해 미납 주문 상태를 업데이트한 후 프론트엔드에서 제품이 품절 상태로 남아 있었습니다. 이제 REST API를 통해 미납 주문 상태를 업데이트하면 제품이 재고로 표시됩니다.

_ACP2E-3355 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### MSI가 활성화된 경우 구성 가능한 이미지에 이미지 추가가 작동하지 않습니다.

구성 가능한 제품에 대한 이미지 업로드는 이제 인벤토리 모듈을 사용할 때 예상대로 작동합니다. 이전에는 이미지 업로드가 작동하지 않았습니다

_ACP2E-3357 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/fdf409aa)_

#### 정리 M2.4.7-p3에서 번들 제품 + MSI 문제

기존에는 동일한 간편 제품으로 중복 후 재고 번들 제품의 경우 간편 제품을 저장할 수 없었다. 이 수정 사항이 적용되면 예외 없이 간단한 제품을 성공적으로 저장할 수 있습니다.

_ACP2E-3470 - [GitHub 문제](https://github.com/magento/magento2/issues/39358) - [GitHub 코드 기여](https://github.com/magento/inventory/commit/0208e433)_

### 인벤토리/MSI, 검색

#### SKU가 검색 가능한 속성으로 설정되지 않은 경우 모든 제품이 [is_out_of_stock] = 1로 색인화됩니다.

수정 후에는 sku를 검색할 수 없는 경우에도 카탈로그 검색 색인의 &quot;is_out_of_stock&quot;이 올바릅니다.

_ACP2E-3413 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5b21b7af)_

### 주문

#### 백엔드 주문 개요 화면: 주문 품목 레벨에 미납 주문 수량이 표시되지 않음

이제 백엔드 주문 개요 화면의 수량 열에 미납 주문 품목 수가 표시됩니다. 이렇게 하면 사용자가 모든 항목의 상태를 순서대로 정확하게 추적할 수 있습니다. 이전에는 수량 열에 주문, 송장 발행 및 출하된 품목의 수만 표시되었지만 미납주문 품목의 수는 표시되지 않았습니다.

_AC-10828 - [GitHub 문제](https://github.com/magento/magento2/issues/38252) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38320)_

#### [문제] 잘못된 저장소 ID가 주문 주소 렌더러에서 사용되었습니다.

이제 시스템은 주문 주소를 렌더링할 때 주문과 연관된 스토어 ID를 올바르게 사용하여 주소의 형식이 해당 스토어 ID에 따라 올바르게 지정되었는지 확인합니다. 이전에는 시스템이 현재 스토어 ID를 잘못 사용했으며, 이로 인해 서로 다른 스토어의 여러 주문 이메일을 전송해야 하는 경우 잘못된 주소 포맷이 발생할 수 있었습니다.

_AC-10994 - [GitHub 문제](https://github.com/magento/magento2/issues/38412) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37932)_

#### JoinProcessor 캐싱 문제

이제 연속 호출에서도 각 반복에 대해 JoinProcessor를 올바르게 적용하여 정확한 데이터 검색을 보장합니다. 이전에는 JoinProcessor가 이미 연속적으로 적용된 것으로 잘못 표시되어 데이터 검색 시 오류가 발생했습니다.

_AC-11690 - [GitHub 문제](https://github.com/magento/magento2/issues/27504) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37550)_

#### [문제] 인쇄 pdf에 다른 가격을 표시하는 배송 가격

이제 세금 구성 설정에 따라 시스템이 인쇄된 PDF로 출하 가격을 올바르게 표시하므로 판매 주문 송장 조회 페이지와 인쇄된 송장 간의 일관성이 보장됩니다. 기존에는 인쇄된 PDF에 표시된 배송가격이 세금 구성 설정과 관계없이 세금을 제외한 것이었다.

_AC-11798 - [GitHub 문제](https://github.com/magento/magento2/issues/38608) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38595) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bafc571)_

#### 구성 가능한 상위 제품을 삭제하고 순서 바꾸기

이제 삭제된 제품으로 재정렬하는 동안 재정렬할 순서 변경 버튼이 표시되지 않습니다

_AC-13839 - [GitHub 문제](https://github.com/magento/magento2/issues/39568) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39601)_

#### [문제] 수정 잘못된 \Magento\Sales\Model\Order\Email\Container\Template::$id 속성

이렇게 하면 \Magento\Sales\Model\Order\Email\Container\Template:$id에 대한 잘못된 phpdoc가 수정됩니다. 실제로 $id는 int 유형이지만 실제로는 string입니다.

_AC-13924 - [GitHub 문제](https://github.com/magento/magento2/issues/39151) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39150)_

#### 기존 주문 세부 사항에 전화 번호에 대한 변경 사항을 저장할 수 없음

이제 사용자는 주문 주소의 전화 필드에 국제 접두사 00을 추가할 수 있습니다

_ACP2E-2622 - [GitHub 문제](https://github.com/magento/magento2/issues/38201) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/12e071c3)_

#### 이메일을 보낼 수 없음

이제 시스템에는 중지 전 이메일 전송 시도 횟수를 지정하는 async_sending_attempts 구성 옵션이 포함되어 &quot;비동기 전송&quot;이 활성화된 경우 실패한 이메일 전송 처리를 개선합니다. 이전에는 이메일을 보내지 못하면 시스템에서 계속해서 다시 보내려고 시도하므로 시스템 로그에 오류 메시지가 계속 반복됩니다.

_ACP2E-2734 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### 부분적으로 배송된 주문을 부분 환불하는 경우 [Cloud] 주문 상태가 완료로 변경됨

대변 메모를 발행할 때 아직 출하되지 않은 품목이 있으면 주문 상태가 더 이상 &#39;완료&#39;로 바뀌지 않는다.

_ACP2E-2756 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD]은(는) 개발 문서가 표시하는 것처럼 관리자 UI에서 전자 메일 보내기를 비활성화할 수 없습니다.

이제 시스템은 이메일 통신이 비활성화될 때 판매 이메일이 전송되지 않도록 올바르게 예방합니다. 전자 메일 통신이 다시 활성화되면 이러한 전자 메일은 더 이상 전송되지 않습니다. 이전에는 이메일 커뮤니케이션이 비활성화된 상태에서 시작된 판매 이메일은 이메일 커뮤니케이션이 다시 활성화된 후에도 계속 전송됩니다.

_ACP2E-3002 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8931218)_

#### 완전히 환불되지 않고 종료된 주문

이제 시스템에서 캡처되지 않은 지급이 있는 주문에 납품이 생성되면 주문 상태를 &#39;처리 중&#39;으로, 송장 상태를 &#39;보류 중&#39;으로 올바르게 관리합니다. 이렇게 하면 주문이 전액 환불 된 후에만 &#39;마감됨&#39;으로 표시됩니다. 이전에는 보류 중인 송장이 있는 주문에 대해 납품을 생성하면 주문 상태가 &#39;마감됨&#39;으로 잘못 변경됩니다.

_ACP2E-3045 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] 기본 청구 주소만 설정되지 않은 경우 한 스토어에서 관리자 주문을 만들 수 없습니다.

이제 관련 오류 메시지 &quot;연결된 웹 사이트에 동일한 이메일 주소를 가진 고객이 이미 있습니다.&quot; 고객이 기본 청구 주소를 가지고 있지 않고 다른 스토어에서 주문을 만들려고 할 경우 이 표시됩니다.

_ACP2E-3311 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d75cff27)_

#### 관리자가 복제한 주문 요청 전송됨

이전에는 관리 패널에서 &quot;주문 제출&quot; 버튼을 여러 번 클릭하거나 &quot;Enter&quot; 키를 반복적으로 눌러 활성화할 수 있으므로 중복 또는 주문 제출이 오류가 발생했습니다. 이제 주문이 완전히 처리될 때까지 추가 작업을 방지하여 하나의 주문만 제출되도록 합니다.

_ACP2E-3416 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### 관리자는 결제 방법이 없어도 주문할 수 있습니다.

이전에 선택한 결제 방법은 이제 결제 방법이 사용 가능한 결제 목록에 다시 나타나면 유지됩니다.

_ACP2E-3425 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d50f6b5d)_

### 주문, 결제

#### 관리자는 결제 방법이 없어도 주문할 수 있습니다.

이전에는 가맹점이 결제 방법을 선택하지 않고 관리자 패널에서 주문을 할 수 있었습니다. 이제는 가맹점이 주문을 진행하기 위해 결제 방법을 요구받는다.

_ACP2E-3233 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fd5cf3af)_

### 순서, 반환

#### 주문 환불 결과 대변 메모가 중복됨

두 개의 동일한 요청이 동시에 실행된 경우 REST API를 통해 환불을 발행하면 더 이상 중복 대변 메모가 생성되지 않습니다.

_ACP2E-2982 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a4fbf702)_

### 주문, 세금

#### [CLOUD] 교차 거래를 활성화하고 쿠폰 할인을 적용할 때 RESTFUL 주문 API의 잘못된 base_row_total

이제 교차 국경 거래가 활성화되고 쿠폰 할인이 적용되면 올바른 base_row_total이 RESTFUL 주문 API에서 반환됩니다.

_ACP2E-3003 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9af794a4)_

### 기타

#### gql 쿼리에서 private_content_version 쿠키가 반환됨

세션 쿠키가 비활성화된 경우에도 GraphQL 쿼리에서 private_content_version 쿠키가 반환되던 문제를 수정했습니다. 예상대로 세션이 비활성화될 때 쿠키는 더 이상 GraphQL 응답에 포함되지 않습니다.

_LYNX-339_

#### cartItemInterface의 is_available 속성은 구성 가능한 제품에 대해 항상 false를 반환합니다.

CartItemInterface의 is_available 속성이 재고 구성 가능한 제품에 대해 항상 false를 반환하는 문제가 해결되었습니다. 이제 해당되는 경우 가용성이 true로 올바르게 반영됩니다.

_LYNX-380_

#### 판매 가능한 재고가 제품 수량보다 낮은 경우에도 CartItemInterface의 is_available 속성이 true를 반환합니다.

장바구니 항목 수량이 판매 가능한 재고를 초과하는 경우에도 CartItemInterface의 is_available 속성이 true를 잘못 반환하던 문제가 해결되었습니다.

_LYNX-382_

#### 자리 표시자 썸네일은 간단한 제품이 그룹화된 제품 내의 장바구니에 추가되면 반환됩니다

제품에 지정된 이미지가 있더라도 간단한 제품(그룹화된 제품의 일부)을 장바구니에 추가하면 자리 표시자 썸네일 이미지가 반환되던 문제를 수정했습니다.
수정 세부 사항:
- 사용 가능한 경우 이제 제품 썸네일에 할당된 이미지가 올바르게 표시됩니다.
- 썸네일 선택 사항은 아래의 관리 구성을 따릅니다.
스토어 > 구성 > 판매 > 체크아웃 > 장바구니 > 그룹화된 제품 이미지.
이렇게 하면 스토어 설정에 따라 그룹화된 제품에 대해 일관된 썸네일 동작이 보장됩니다.

_LYNX-399_

#### 고객의 사용자 지정 옵션 속성이 정수 값으로 작동하지 않음

반환된 값이 정수일 때 고객의 사용자 지정 옵션 속성이 작동하지 않던 문제를 수정했습니다. 이제 사용자 지정 옵션이 예상대로 정수 값을 올바르게 처리하고 반환합니다.

_LYNX-400_

#### 동적 가격이 적용된 번들 제품의 priceDetails를 가져오려고 할 때 내부 서버 오류 발생

GraphQL을 통해 동적 가격책정이 포함된 번들 제품에 대한 price_details를 쿼리하면 내부 서버 오류가 발생하는 문제가 해결되었습니다. 이러한 향상된 기능을 통해 동적 가격책정으로 구성된 번들 제품으로 작업할 때 장바구니 쿼리가 안정적이 됩니다.

_LYNX-402_

#### only_x_left_in_stock은 구성 가능한 제품에 대해 항상 0을 반환합니다.

옵션이 있는 상위 SKU를 사용하여 추가할 때 only_x_left_in_stock 속성이 구성 가능한 제품에 대해 항상 0을 반환하는 문제가 해결되었습니다.
수정 세부 사항:
- 이제 only_x_left_in_stock 값은 상위 SKU 대신 선택한 하위 변형의 스톡을 정확하게 반영합니다.
- 이렇게 하면 장바구니 및 제품 페이지에서 구성 가능한 제품 변형에 대해 재고 수준이 올바르게 표시됩니다.

_LYNX-403_

#### GraphQL 쿼리가 사용자 정의 가능한 제품에 대해 올바른 계산된 일반 가격을 반환하지 않음

GraphQL에서 사용자 지정 가능한 제품에 대해 올바르게 계산된 정가를 반환하지 않던 문제를 수정했습니다. 이제 쿼리는 기본 가격과 추가 사용자 지정 비용을 모두 반영하여 가격 속성에 사용자 지정 가능한 값(예: $125)이 적용된 계산된 일반 가격을 올바르게 포함합니다.

_LYNX-411_

#### EstimatedTotals를 통한 AppliedTaxes는 업데이트된 돌연변이로 유지됩니다

지역 또는 우편 번호를 업데이트한 후에도 장바구니에서 적용된 세금이 지속되는 EstimatedTotals 돌연변이 문제를 해결했습니다. 돌연변이는 이제 지역 및 우편 번호 값 사이를 변경할 때 적용된 세금을 올바르게 업데이트하여 현재 장바구니 데이터를 기반으로 올바른 세금 규칙만 적용되도록 합니다.

_LYNX-412_

#### 판매 가능한 재고가 제품 수량보다 낮은 경우에도 CartItemInterface의 is_available 속성이 true를 반환합니다.

판매 가능한 재고가 요청된 제품 수량보다 낮은 경우에도 CartItemInterface의 is_available 속성이 true를 잘못 반환하던 문제가 해결되었습니다. 이제 is_available 필드는 제품의 수량이 사용 가능한 재고를 초과할 때 올바르게 false를 반환합니다.

_LYNX-420_

#### 12개의 소수 자릿수와 잘못된 값을 포함한 제품 정가

여러 세율이 적용되었을 때 product.price_range.maximum_price 및 minimum_price GraphQL 경로의 regular_price 값이 카탈로그 가격과 일치하지 않던 문제를 수정했습니다. 이제 regular_price는 모든 세금 구성에서 카탈로그 가격을 일관되게 반영하므로 장바구니 요약에서 정확한 단가 책정, 총 행 비용 계산 및 할인 확인을 보장할 수 있습니다.

_LYNX-425_

#### 품절 번들 제품이 있는 장바구니에 GraphQL 서버 오류 발생

특히 쿼리에 itemsV2 속성이 포함된 경우 GraphQL이 재고 부족 항목이 있는 번들 제품이 포함된 장바구니를 가져올 때 내부 서버 오류가 반환되는 문제를 해결했습니다. 이제 GraphQL은 예상대로 번들 제품 항목 항목에 연결된 관련 오류 메시지가 있는 항목 목록을 올바르게 반환합니다.

_LYNX-430_

#### 사용자 지정 속성으로 주소를 만들 수 없습니다.

필요한 사용자 지정 특성이 있는 주소를 만들 수 없는 createCustomerAddress 돌연변이 문제를 수정했습니다. 이제 적절한 페이로드가 제공되면 돌연변이가 사용자 지정 주소 속성을 올바르게 처리합니다.

_LYNX-441_

#### 번들 제품의 only_x_left_in_stock이 있는 장바구니에 GraphQL 서버 오류 발생

GraphQL 쿼리에서 only_x_left_in_stock 필드가 있는 번들 제품이 포함된 장바구니를 가져오는 경우 내부 서버 오류가 발생하는 문제를 해결했습니다. 이제 GraphQL은 오류 없이 only_x_left_in_stock 필드에 대해 float 또는 null을 올바르게 반환합니다.

_LYNX-447_

#### 장바구니에서 구성 가능한 제품이 부족한 다른 제품을 제거할 때 GraphQL 오류 발생

장바구니에 재고량이 부족한 구성 가능한 제품이 포함되어 있는 경우, 장바구니에서 재고 내 제품을 제거하려고 하면 &#39;요청된 수량을 사용할 수 없음&#39; GraphQL 오류가 발생하는 문제를 해결했습니다. 이제 제거 가 오류를 트리거하지 않고 예상대로 작동합니다.

_LYNX-464_

#### 대/소문자를 구분하는 돌연변이의 SKU로 인해 제품을 추가할 수 없음

대/소문자가 다른 SKU를 사용할 때 addProductsToCart 돌연변이가 &#39;PRODUCT_NOT_FOUND&#39; 오류를 반환하는 문제를 해결했습니다. 돌연변이는 이제 SKU를 대소문자 구분 없이 처리하여 카탈로그 서비스 쿼리 및 PDP 비헤이비어와 일관성을 보장합니다.

_LYNX-469_

#### Product attribute > trademark short form &trade;는 &trade;로 반환됩니다

GraphQL API의 제품 이름에 대한 문자 인코딩 문제가 해결되었습니다.

_LYNX-603_

#### updateCustomerEmail 돌연변이 문제

필수 사용자 지정 특성(계정 생성 후 추가됨)이 없는 고객이 이메일을 업데이트할 수 없는 updateCustomerEmail 돌연변이 문제를 해결했습니다.

_LYNX-619_

#### pickup_location_code를 사용할 때 돌연변이 setShippingAddressesOnCart에 오류가 발생합니다.

customer_address_id 또는 주소를 지정하지 않고 pickup_location_code를 사용할 때 setShippingAddressesOnCart 돌연변이가 오류를 반환하는 문제가 해결되었습니다. 돌연변이는 이제 pickup_location_code만으로 배송 주소를 설정할 수 있습니다.

_LYNX-626_

#### Storefront 호환성 - 접두사가 있는 테이블 이름을 가져오도록 로직을 업데이트하고 기타 사소한 개선 사항

SCP 변경 사항과 관련하여 접두사로 테이블 이름을 검색하는 논리를 업데이트했습니다.

_LYNX-637_

#### setBillingAddressOnCart GQL의 same_as_shipping 필드를 사용할 때 주소록에 저장이 작동하지 않습니다.

same_as_shipping 필드가 true로 설정된 setBillingAddressOnCart GraphQL 돌연변이를 사용할 때 배송 주소가 고객 주소록에 저장되지 않는 문제를 해결했습니다. 이제 배송 주소가 예상대로 정확하게 저장됩니다.

_LYNX-643_

#### 돌연변이의 order_id 표준화

순서에서 order_id 입력을 표준화하고 주문 ID 대신 증분 ID를 노출하도록 주문 취소 확인 이메일 템플릿을 업데이트했습니다.

_LYNX-650_

#### CustomerOrder에 주문 주석이 표시되지 않습니다.

게스트 및 고객 주문 GraphQL 쿼리에 주문 주석을 포함하는 CustomerOrder 문제를 해결했습니다.

_LYNX-651_

#### original_item_price에는 할인이 포함되지 않아야 합니다.

할인을 제외하기 위해 GraphQL 장바구니 품목 가격의 original_item_price에 대한 논리를 업데이트했습니다.

_LYNX-652_

#### 번들 제품 중 하나가 품절되었을 때 번들 제품에 여전히 &quot;IN_STOCK&quot;이 표시됩니다.

번들 제품 중 하나가 품절되어도 번들 제품의 product.stock_status에 여전히 &quot;IN_STOCK&quot;이 표시되던 문제를 해결했습니다.

_LYNX-681_

#### 삭제된 사용자 지정 특성의 값이 고객에 대해 존재하는 경우 고객 쿼리가 내부 서버 오류를 반환합니다.

삭제된 사용자 지정 특성에 저장된 값이 있을 때 고객 쿼리가 내부 서버 오류를 반환하던 문제를 수정했습니다. 이제 존재하지 않는 속성이 요청되면 적절한 오류 메시지가 반환됩니다. 고객 사용자 지정 특성을 삭제하면 필요한 캐시가 무효화됩니다.

_LYNX-686_

#### 반환 및 취소 확인 링크에 대한 작업 매개 변수

반환 및 취소 확인 이메일 관련 링크에 대한 작업 매개 변수가 추가됨

_LYNX-687_

#### Guest 사용자 확인 url은 orderRef가 누락되어 주문 상태 페이지로 리디렉션됩니다.

게스트 주문 취소 확인 이메일의 링크에 orderRef 매개 변수를 추가했습니다.

_LYNX-689_

#### placeOrder GQL에서 null을 허용하지 않는 필드 &quot;TaxItem.title&quot;에 대해 null을 반환할 수 없음

null을 허용하지 않는 필드 TaxItem.title에 대한 null 값으로 인해 내부 서버 오류로 인해 placeOrder 돌연변이가 실패하는 문제가 해결되었습니다. 이제 필드가 항상 유효한 값을 반환하여 성공적인 주문 배치를 보장합니다.

_LYNX-699_

#### 예상 총계: 가상 제품 유형의 경우 할인이 null입니다.

가상 제품이 포함된 장바구니에 할인 코드가 적용될 때 approximateTotals 돌연변이가 할인용으로 null을 반환하는 문제를 해결했습니다.

_LYNX-702_

#### 번들 제품이 올바른 할인 백분율 및 금액을 반환하지 않음

신규 속성 &quot;catalog_discount&quot; 및 &quot;row_catalog_discount&quot;가 카탈로그 품목 가격에 대해 도입되어 행 및 단일 품목 레벨 모두에서 올바른 할인 금액 및 퍼센트를 표시합니다.

_LYNX-703_

#### 제품 수준의 선물 메시지 구성

전역으로 비활성화할 때 제품 수준에서 선물 메시지가 적용되지 않던 문제를 수정했습니다. 이제 특정 제품에 대해 선물 메시지를 사용할 수 있는 경우 updateCartItems 돌연변이를 사용하여 성공적으로 추가할 수 있으며 올바르게 저장 및 반영됩니다.

_LYNX-714_

#### 활성 장바구니 규칙이 적용되지 않는 경우 cart.rules 쿼리가 빈 배열 대신 오류를 반환합니다

활성 장바구니 규칙이 적용되지 않을 때 오류 대신 빈 배열을 반환하도록 cart.rules 쿼리를 수정했습니다.

_LYNX-757_

#### adobe-commerce/storefront-compatibility 패키지가 설치되면 OPTIONS 메서드를 사용한 GraphQL 호출에서 500개의 응답 코드를 반환합니다

adobe-commerce/storefront-compatibility 패키지가 설치될 때 OPTIONS 메서드를 사용한 GraphQL 호출에서 500 내부 서버 오류를 반환하던 문제를 수정했습니다. 이제 끝점이 예상대로 200/204 응답을 올바르게 반환합니다.

_LYNX-778_

### 기타 개발자 도구

#### [문제] visual.phtml에서 HTML 구문 오류를 수정하십시오.

이제 시스템에서 visual.phtml 파일의 시작 태그를 올바르게 닫아 적절한 HTML 구문을 확인합니다. 이전에는 시작 태그가 제대로 닫히지 않아 HTML 구문 오류가 발생했습니다.

_AC-10658 - [GitHub 문제](https://github.com/magento/magento2/issues/38247) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37457)_

#### [문제] bin/magento maintenance:status 명령에서 &quot;active&quot;를 &quot;enabled&quot;로 변경함

이제 시스템에서 유지 관리 모드 명령에 대해 보다 정확한 상태 메시지를 제공하여 상태를 &quot;활성&quot;에서 &quot;활성화됨&quot;으로, &quot;활성화되지 않음&quot;에서 &quot;비활성화됨&quot;으로 변경합니다. 이전에는 유지 관리 모드 명령에 대한 상태 메시지가 &quot;활성&quot; 또는 &quot;활성화되지 않음&quot;으로 표시되어 혼동을 일으킬 수 있었습니다.

_AC-11474 - [GitHub 문제](https://github.com/magento/magento2/issues/38486) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38410)_

#### 범주 트리를 탐색하면 Redis에서 오류가 발생합니다. &quot;Redis 세션 초과 동시 연결&quot;

_AC-12571 - [GitHub 문제](https://github.com/magento/magento2/issues/38851) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0611e750)_

#### dev/css/use_css_critical_path와 결합된 CSP 문제

이제 &#39;dev/css/use_css_critical_path&#39; 설정이 활성화된 경우에도 시스템은 체크아웃 페이지에 CSS 파일을 비동기적으로 올바르게 로드하여 이러한 페이지가 적절한 CSS 스타일로 렌더링되도록 합니다. 이전에는 제한된 CSP(콘텐츠 보안 정책)를 사용하여 인라인 JavaScript을 실행할 수 없으므로 CSS 파일이 예상대로 로드되지 않았습니다.

_AC-12731 - [GitHub 문제](https://github.com/magento/magento2/issues/39020) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39040)_

#### 가상 형식을 사용하여 플러그 인을 구성하면 `setup:di:compile` 명령에서 인터셉터 메서드를 올바르게 생성할 수 없습니다

이제 시스템은 가상 형식을 사용하여 플러그인을 구성할 때 인터셉터 메서드를 올바르게 생성하므로 미리 컴파일했는지 아니면 런타임 컴파일했는지에 관계없이 일관된 결과를 보장합니다. 이전에는 런타임 컴파일과 비교하여 미리 컴파일할 때 시스템에서 잘못된 결과를 생성했습니다.

_AC-13398 - [GitHub 문제](https://github.com/magento/magento2/issues/33980) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38141)_

#### Adobe Commerce 2.4.7-p3 단위 테스트 실패

릴리스 노트는 필요하지 않습니다.

_ACP2E-3631 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/982b1c42)_

### 결제/결제 방법, 주문

#### 나중에 사용하기 위해 저장된 종이 결제 신용카드 세부 정보가 저장된 결제 방법 페이지에 표시되지 않습니다.

이전 Papal Payflow 나중에 사용하기 위해 저장된 신용 카드 세부 사항이 저장된 결제 방법 페이지에 표시되지 않았습니다. 이제 고정 신용 카드 세부 사항이 저장된 결제 방법 페이지에 표시됩니다.

_AC-13699 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/96dec499)_

### 결제

#### 신용 카드(Payflow Link) 결제가 작동하지 않음

수정 주문이 성공적으로 수행된 후 신용 카드로 주문하는 동안 이전에 오류가 발생했습니다(결제가 거부됨).

_AC-13414 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a68324bc)_

#### Payflow는 트랜잭션 보기 화면에서 가져오기 버튼을 클릭할 때마다 새 트랜잭션을 생성합니다.

이제 시스템은 거래 보기 화면에서 가져오기 버튼을 클릭할 때마다 신규 결제 거래를 생성하지 않고 거래 정보를 올바로 가져옵니다. 이전에는 가져오기 버튼을 클릭하면 이미 지불된 주문에 대한 새 결제 거래가 잘못 생성되었습니다.

_ACP2E-2841 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### 캐나다 paypal 상인 계정에 대한 PDP에 페이로드 메시지가 표시되지 않음

이제 구매자의 국가가 계정 청구 주소 또는 납품에서 결정될 수 있는 경우 시스템은 PDP(Product Detail Page)에 캐나다 PayPal 판매자 계정에 대한 PayLater 메시지를 올바르게 표시합니다. 이전에는 매개 변수가 누락되어 PayLater 메시지가 표시되지 않아서 브라우저 콘솔에 오류가 발생했습니다.

_ACP2E-3028 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6a185204)_

#### PayPal 주문 환불 결과 크레딧 메모가 중복됨

PayPal 결제 서비스에 대한 IPN 생성 대변 메모의 동시성 문제를 해결했습니다.

_ACP2E-3143 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d01ee51e)_

#### 장바구니 가격 규칙이 Paypal에 대해 작동하지 않음

결제 방법으로 할인을 적용하면 PayPal 쪽에 정확한 금액이 표시됩니다

_ACP2E-3163 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

#### 특정 역할을 가진 [클라우드] 사용자는 로그인할 수 없습니다.

이제 PayPal 섹션 액세스만 포함하는 역할을 가진 관리자는 오류 없이 로그인할 수 있습니다.

_ACP2E-3208 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/66dea0de)_

### 성능

#### 기본 제품 속성 설정 문제

이제 시스템에서 사용자는 제품 속성에 대한 기본 옵션을 선택 해제할 수 있으므로 속성에 항상 기본 세트가 있지 않도록 합니다. 이전에는 제품 속성에 대해 기본값이 설정되고 나면 이를 선택 해제할 방법이 없으므로 속성에 항상 기본값이 설정됩니다.

_AC-11932 - [GitHub 문제](https://github.com/magento/magento2/issues/38703) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7d5e3906)_

#### [문제] 코드 정리 및 새로운 중요한 헤드 블록 추가, 자산 앞으로 중요한 css 이동

이제 시스템에는 새로운 중요한 헤드 블록이 포함되어 있으며 에셋 이전에 중요한 CSS를 이동하므로 프론트엔드에서 더 많은 사용자 지정 및 성능 최적화를 수행할 수 있습니다. 이전에는 중요한 CSS가 자산 앞에 위치하지 않아 사용자 지정 및 최적화 기회를 제한했습니다.

_AC-12000 - [GitHub 문제](https://github.com/magento/magento2/issues/38748) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35580)_

#### mysql 호스트에 포트 정보가 포함되어 있으면 테마 컴파일이 중단됩니다.

이제 시스템에서 포트 정보가 포함된 MySQL 호스트 구성을 올바르게 처리하여 테마 컴파일을 성공적으로 수행할 수 있습니다. 이전에는 데이터베이스 연결의 MySQL 호스트 구성에 포트 정보가 포함되어 있으면 테마 컴파일이 실패했습니다.

_AC-12176 - [GitHub 문제](https://github.com/magento/magento2/issues/38799) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38842)_

#### Magento CLI에서 Symfony의 CommandLoaderInterface 지원

이 변경 사항은 명령이 필요할 때까지 지연된 초기화를 허용함으로써 Magento CLI 앱의 초기화 시간을 줄입니다.

_AC-13471 - [GitHub 문제](https://github.com/magento/magento2/issues/29266) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/29355)_

#### 장바구니 규칙에서 제품 속성을 로드할 때 성능 문제 발생

판매 규칙에 대한 쿼리 성능이 약 150ms에서 한 자리 ms로 개선되었습니다.

_ACP2E-2494 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### 가격 부분 인덱싱 성능

인덱싱 프로세스 내에서 사용되는 일부 삭제 쿼리를 최적화하여 가격 부분 인덱싱 성능을 개선했습니다.

_ACP2E-2673 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ba25af8a)_

#### 비동기 주문 처리 + 약관을 사용할 때 다중 스토어 설정에서 주문이 거부됩니다.

이제 약관이 활성화된 기본이 아닌 웹 사이트에서 주문된 주문이 처리됩니다.
자동 거부되기 전.

_ACP2E-2850 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/57a32313)_

#### Order Rest API 호출을 실행하는 데 시간이 오래 걸립니다.

이제 시스템에서 적절한 일정 내에 Order Rest API 호출을 실행하여 많은 수의 주문을 가져올 때 성능을 개선합니다. 이전에는 Order Rest API 호출을 실행하는 데 시간이 오래 걸려 많은 수의 주문을 검색할 때 지연이 발생했습니다.

_ACP2E-2910 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/001e5188)_

### 가격 책정

#### Magento2.4.6-p4 주문 API 단순 품목 누락 가격

이제 주문 API를 통해 쿼리할 때 단순 제품의 가격이 올바르게 표시되므로 정확한 데이터 표현이 보장됩니다. 이전에는 API 응답에서 단순 제품의 가격이 0으로 잘못 표시되었습니다.

_AC-11810 - [GitHub 문제](https://github.com/magento/magento2/issues/38603)_

#### 카탈로그 규칙의 페니 반올림 오류

_AC-13855 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/276e0acd)_

### 제품

#### 구성 가능한 연관 제품 이름의 특수 문자가 HTML 엔티티로 변환됩니다.

이제 구성 가능한 제품을 편집할 때 연결된 제품 이름에 특수 문자가 올바르게 유지되므로 HTML 엔티티로 변환되지 않습니다. 이전에는 구성 가능한 제품을 편집할 때 연결된 제품 이름의 특수 문자가 HTML 엔티티로 변환되었습니다.

_AC-10535 - [GitHub 문제](https://github.com/magento/magento2/issues/38146) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38447)_

#### ProductRepository 함수 GetById가 올바른 캐시 키를 만들지 않습니다.

이제 시스템은 저장소 ID가 문자열로 전달되는지 또는 정수로 전달되는지에 관계없이 ProductRepository의 함수 GetById에 캐시 키를 올바르게 만듭니다. 이렇게 하면 후속 호출 시 메모리에서 제품을 검색할 수 있으므로 성능이 향상됩니다. 이전에는 잘못된 캐시 키 생성으로 인해 동일한 매개 변수를 사용해도 함수가 호출될 때마다 데이터베이스에서 제품을 검색했습니다.

_AC-10947 - [GitHub 문제](https://github.com/magento/magento2/issues/38384) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38433)_

#### [문제] [MTF] 추가 AdminClickAddOptionForBundleItemsActionGroup

이제 시스템에 AdminClickAddOptionForBundleItemsActionGroup이 포함되어 관리 패널의 기능이 향상되었습니다. 이전에는 이 작업 그룹을 사용할 수 없었습니다.

_AC-11992 - [GitHub 문제](https://github.com/magento/magento2/issues/30857) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30838)_

#### [문제] PHPDoc 블록의 오타 수정

이제 시스템이 $helper 변수 선언에 대해 PHPDoc에서 알 수 없는 참조 변수를 올바르게 제거하여 코드 명확성과 정확성을 향상시킵니다. 이전에는 PHPDoc에서 알 수 없는 이 참조된 변수가 코드에 혼동과 잠재적인 부정확성을 초래하고 있었다.

_AC-13173 - [GitHub 문제](https://github.com/magento/magento2/issues/38961) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38940)_

#### [문제] Magento >= 2.4.7에서 끊어진 번들 및 다운로드 가능한 제품 페이지 레이아웃을 수정했습니다.

번들 및 다운로드 가능한 제품 페이지의 레이아웃이 수정되어 모든 장치에서 일관되고 올바른 표시가 보장됩니다. 이전에는 이러한 페이지에서 제품 정보 미디어 블록의 재배열로 인해 레이아웃 문제가 발생했습니다.

_AC-13423 - [GitHub 문제](https://github.com/magento/magento2/issues/39403) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - 인수 #2($storeId)는 int, string 형식이어야 합니다.

이제 시스템에서 스토어 식별자가 올바른 데이터 유형인지 확인하여 제품 경고 이메일을 올바르게 트리거합니다. 이전에는 스토어 식별자의 유형 불일치로 인해 제품 경고 이메일이 전송되지 않았습니다.

_AC-5969 - [GitHub 문제](https://github.com/magento/magento2/issues/35602) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/0574ac23)_

#### [Cloud] addFilterToMap 함수가 특정 열에 대해 작동하지 않습니다.

이제 사용자 지정 모듈을 순서 그리드에서 사용할 수 있습니다. 사용자 지정 모듈을 사용하는 동안 이전에 오류가 발생했습니다.

_ACP2E-2944 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3a7c4d17)_

### 프로모션

#### 초대에서 계정을 만들 때 고객 특성이 표시되지 않음

초대를 통해 계정을 만드는 동안 고객 특성을 사용할 수 있습니다.

_ACP2E-2602 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/39d54c2d)_

#### 쿠폰 사용당 쿠폰 한도가 적용되는 쿠폰 코드가 주문 취소로 인해 결제에 대해 릴리스되지 않습니다.

이제 주문이 생성되거나 취소되면 시스템이 쿠폰 사용을 즉시 업데이트하고 규칙 사용을 대기열에 추가하여 교착 상태를 방지할 수 있습니다. 이를 통해 &#39;쿠폰당 사용&#39; 제한이 적용된 쿠폰코드가 출시되고 결제 실패로 주문이 취소될 경우 재사용이 가능하다. 이전에는 이러한 경우 시스템이 재사용을 위해 쿠폰 코드를 릴리스하지 않아 쿠폰 코드가 유효하지 않다는 오류 메시지가 표시되었습니다.

_ACP2E-2627 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] 리인덱싱 카탈로그 규칙 제품 인덱서가 SQLSTATE를 throw합니다[HY000]: 일반 오류: 2006 MySQL 서버가 제거되었습니다.

이제 시스템은 &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;에 대한 di.xml의 사용자 지정 &quot;batchCount&quot; 값을 올바르게 처리하므로 큰 카탈로그의 잘못된 배치 크기로 인해 카탈로그 규칙 제품 인덱서를 다시 인덱싱하는 동안 &quot;일반 오류: 2006 MySQL Server가 없어짐&quot;과 같은 SQL 오류가 발생하지 않습니다

_ACP2E-2811 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### 할인 수량 단계(구매 X) 속성이 있는 판매 규칙으로 인해 다른 규칙이 적용되지 않음

장바구니에 있는 제품의 수량이 규칙을 적용하기에 충분하지 않은 경우 장바구니 가격 규칙은 이전에 적용된 규칙을 취소하지 않습니다.

_ACP2E-3139 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d01ee51e)_

#### 고정 금액 할인과 &quot;최대 수량 할인 적용 대상&quot;이 있는 판매 규칙 발행

장바구니의 제한된 제품 수량에 대해 고정 금액 할인이 적용되도록 구성된 경우 장바구니 규칙 할인 문제를 해결했습니다. 이전에는 &quot;최대 할인 적용 대상&quot; 값을 사용하여 규칙의 할인 계산에만 사용한 것이 아니라 장바구니에서 현재 항목의 가격을 계산했습니다.

_ACP2E-3332 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

#### 장바구니 규칙 &quot;전체 장바구니에 대한 고정 금액 할인&quot;  조치가 할인을 잘못 적용

쿠폰 코드는 관리자 영역에서 주문 생성 시 대문자나 소문자에 관계없이 올바르게 검증됩니다. 이전에는 구성된 장바구니 규칙 코드의 정확한 문자 대/소문자와 일치하지 않으면 쿠폰 코드의 유효성을 검사하지 않았습니다.

_ACP2E-3349 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/581b7ef1)_

#### 백엔드에서 제품 속성에 대한 기본 저장소 값(예상 관리자 값 대신)

이제 백엔드에서 제품 속성에 대한 기본 저장소 값 대신 관리자 값이 사용됩니다.

_ACP2E-3374 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/5184c067)_

#### 장바구니 규칙 &quot;전체 장바구니에 대한 고정 금액 할인&quot; 작업은 번들 제품을 추가할 때 할인을 잘못 적용합니다

고정 금액 장바구니 규칙이 번들 제품에 제대로 적용되지 않았습니다. 이제 총 할인액을 산정할 때 묶음 아동용품을 고려하게 되어 적절한 할인액 산정이 이루어진다.

_ACP2E-3377 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

#### 장바구니 가격 규칙 계산 착오 할인

이제 고정 금액 할인이 제대로 계산되고 있다. 이 문제 해결 이전에는 번들 제품에 대한 고정 금액 할인이 제대로 집계되지 않았습니다.

_ACP2E-3403 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0b488dd1)_

#### 규칙 조건의 중첩된 카테고리가 표시되지 않음

레벨 3 범주 아래에 중첩된 범주가 범주 조건에 대한 마케팅 규칙에 표시되지 않는 문제를 해결했습니다

_ACP2E-3406 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/88660e79)_

#### salesrule_coupon 테이블에서 usage_limit 및 uses_per_customer가 업데이트되지 않음

장바구니에서 쿠폰당 사용량 및 고객당 사용량을 업데이트하면 이제 기존 자동 생성된 쿠폰에 영향을 줍니다. 이전에는 새 값이 새 쿠폰에만 영향을 주었습니다

_ACP2E-3432 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/88660e79)_

#### 장바구니 가격 규칙은 &quot;같음 또는 보다 큼&quot; 조건을 사용할 때 상위 범주를 고려하지 않습니다.

이제 장바구니 가격 규칙이 고급 조건에서 사용될 때 상위 범주를 올바르게 고려합니다.

_ACP2E-3456 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/93359343)_

#### 우선 순위가 있는 잘못된 할인 계산

전체 장바구니 할인 유형에 적용되는 고정 금액의 경우 이전 프로모션으로 이미 할인된 장바구니 품목에 대해서는 금액이 제대로 계산되지 않고 있었다. 이제 할인이 적절히 요약됩니다.

_ACP2E-3463 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

#### [CLOUD] 배송 계산에서 장바구니 규칙을 고려하지 않습니다.

수정 이전에는 지역 조건이 있는 장바구니 규칙이 일관되게 적용되지 않았습니다. 수정 후에는 지역 조건이 있는 장바구니 규칙이 올바르게 적용됩니다.

_ACP2E-3472 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

#### 장바구니 규칙 sku 조건이 송장에 대해 실패했습니다.

동적 가격이 적용된 번들 제품의 할인이 이제 인보이스에 올바르게 반영됩니다. 기존에는 할인액이 인보이스에 반영되지 않았다.

_ACP2E-3491 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3f12d152)_

#### 여러 장바구니 가격 규칙이 할인/특별 가격 제품과 동시에 적용되는 경우 잘못된 할인 값

수정 이전에는 둘 이상의 장바구니 규칙이 적용되는 경우 전체 장바구니 규칙에 대한 고정 금액이 제대로 적용되지 않았습니다. 이제 고정 금액 할인 장바구니 규칙이 제대로 적용되고 있습니다.

_ACP2E-3498 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1984c61c)_

### SEO

#### 악센트로 URL 재작성을 추가하면 무한 로드가 발생합니다.

이제 시스템은 악센트로 URL 재작성을 성공적으로 만들고 작동하므로 저장 프로세스 동안 무한 로드가 발생하지 않습니다. 이전에는 악센트가 있는 URL 재작성을 추가하면 무한 로드 문제가 발생했습니다.

_AC-11907 - [GitHub 문제](https://github.com/magento/magento2/issues/38692) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/44cef3a9)_

#### 다중 스토어 세 번째 수준 범주에 대한 잘못된 범주 URL-재작성

사용자 지정 범위 URL 키를 가진 상위가 있는 하위에 대해 올바른 URL 재작성 생성

_ACP2E-2641 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 제품 이름 필드의 더블바이트 문자(특수 문자)가 백엔드의 제품 생성을 차단합니다

제품 URL에 음역을 적용하거나 적용하지 않을 수 있는 새 설정이 추가되었습니다. 설정은 다음에서 사용할 수 있습니다. 저장 > 구성 > 카탈로그 > 카탈로그 > 검색 엔진 최적화: &quot;제품 URL에 음역 적용&quot;

_ACP2E-2770 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### 하나의 저장소 그룹에 여러 저장소가 있는 잘못된 url_rewrite 항목 생성

수정 이전에는 제품을 편집할 때 웹 사이트 수준에서만 URL 재작성을 생성할 수 있었습니다. 이 수정 사항으로 스토어 보기 또는 웹 사이트 수준에서 URL 재작성을 생성할 수 있는 새 설정(스토어 > 구성 > 카탈로그 > 카탈로그 > 검색 엔진 최적화, &quot;스토어 보기&quot;, &quot;웹 사이트&quot; 옵션이 있는 &quot;제품 URL 재작성 범위&quot;)이 도입되었습니다.

_ACP2E-3383 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2d627301)_

### 검색

#### 검색어를 입력하고 다시 시도하십시오. storefront 2.4.8-beta1의 고급 검색 페이지에 오류

이제 제품 속성이 &quot;No&quot;로 설정되면 검색 결과가 고급 검색 페이지에 올바르게 표시됩니다. 이전에는 제품 속성을 &quot;아니요&quot;로 설정하고 검색을 수행하면 &quot;검색어를 입력하고 다시 시도하십시오.&quot;라는 오류 메시지가 표시되었습니다.

_AC-13053 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search는 존재하지 않는 opensearch-php 분기에 따라 다릅니다.

_AC-13721 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/05dc0bbf)_

#### search_query 테이블 크기가 클 때 로드 시간 프론트엔드에 큰 영향을 미침

검색 목록 페이지 로드 시간이 개선되었습니다. 수정 이전에는 최적화되지 않은 쿼리로 인해 검색 목록 페이지가 지연되었습니다.

_ACP2E-3362 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/55615e61)_

### 보안

#### [문제]에 글꼴 CSP 페이로드 팝업이 없습니다.

이제 시스템에서는 Content Security Policy 지시문을 위반하지 않고 &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; 글꼴을 로드할 수 있으므로 Paylater 팝업이 올바르게 표시됩니다. 이전에는 Content Security Policy 지시문 위반으로 인해 글꼴 로드가 거부되어 Paylater 팝업에 표시 문제가 발생했습니다.

_AC-11855 - [GitHub 문제](https://github.com/magento/magento2/issues/38624) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37401)_

#### [문제] HTML으로 재해석된 js.js DOM 텍스트 업데이트

innerText를 사용하면 이러한 속성이 제공된 텍스트의 모든 HTML 특수 문자를 자동으로 이스케이프 처리하므로 HTML 주입의 위험을 방지할 수 있습니다. 이 수정 사항은 HTML으로 해석되지 않고 입력을 일반 텍스트로 처리하여 XSS(크로스 사이트 스크립팅) 취약성을 방지하는 데 도움이 됩니다.

_AC-12035 - [GitHub 문제](https://github.com/magento/magento2/issues/38767)_

#### ReCaptcha V2가 독일어 체크아웃 시 잘못 표시됨

이전에는 체크아웃 이메일 주소 아래의 recaptcha가 독일어와 같이 긴 단어가 포함된 언어에 대해 스타일이 지정되지 않은 상태로 표시되었습니다. 이 후에 recaptcha는 나머지 영역의 모든 recaptcha 요소와 동일하게 표시됩니다.

_ACP2E-3273 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7377de59)_

#### 관리자 로그인 시 CAPTCHA는 일부 사용자에 대해 상호 작용이 필요하지 않습니다

관리자 로그인에 대한 ReCaptcha가 예상대로 유효합니다.

_ACP2E-3300 - [GitHub 코드 기여도](https://github.com/magento/security-package/commit/8f64ab3c)_

### 배송

#### [문제] tracking.phtml에서 오타가 수정되었습니다. JS-functions가 &quot;currier&quot;로 &quot;carrier&quot;로 이름이 변경되었습니다.

이제 시스템에서 주문 추적 템플릿에 사용된 JavaScript 처리기 함수에서 철자가 잘못된 &quot;currier&quot; 대신 &quot;carrier&quot;라는 용어를 올바르게 사용하여 함수 이름 지정과 코드 명확성을 적절히 보장할 수 있습니다. 이전에는 철자가 잘못된 &quot;currier&quot;라는 용어가 사용되었기 때문에 코드 베이스에 잠재적인 혼동과 불일치가 발생했습니다.

_AC-10757 - [GitHub 문제](https://github.com/magento/magento2/issues/34523) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33414)_

#### UPS REST &quot;배송 시 측정 단위로는 KGS/IN 또는 LBS/CM 또는 OZS/CM를 가질 수 없음&quot;

UPS 요금이 체크아웃 및 장바구니에 표시되는지 확인하십시오.

_AC-11938 - [GitHub 문제](https://github.com/magento/magento2/issues/38618) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/493e01f5)_

#### [문제] 고객 주소에 대한 변수의 맞춤법 수정

이제 시스템에서 고객 주소에 대한 변수의 철자를 올바르게 지정하여 프론트엔드의 계정 영역에 정확하게 표시할 수 있습니다. 이전에는 이러한 변수의 철자가 잘못되면 로컬 코드를 검토하는 동안 오류가 발생할 수 있었습니다.

_AC-13172 - [GitHub 문제](https://github.com/magento/magento2/issues/32817) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32815)_

#### 잘못된 예상 게재 날짜를 표시하는 추적 창

Fedex 통신사의 올바른 배송 날짜를 표시합니다.

_ACP2E-2738 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/57a32313)_

#### 무료 배송이 적용되더라도 테이블 요금은 계속 표시됩니다.

쿠폰 적용 후 무료 배송이 가능해진 경우에도 이제 테이블 요금 배송 방법이 표시됩니다

_ACP2E-2763 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b2286ecf)_

#### Jenkins 환경에 자격 증명이 추가되지 않아 MTF 테스트 AdminCreatingShippingLabelTest가 실패했습니다.

mtf 테스트 수정

_ACP2E-2765 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ea79f7dd)_

#### FedEx Track API가 REST 자격 증명으로 작동하지 않음

이전에는 FedEx 통합에서 API 추적을 위해 추가 API 키가 필요하지 않았습니다. 이제 추적 API 키를 지원하도록 새 구성이 추가되었습니다.

_ACP2E-3340 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [클라우드] FedEx 협상 요금이 REST에서 반환되지 않음

수정되기 전에 FedEx 계정에 특정 요금이 부과됩니다. 단, FedEx 문서에 따라 응답을 보내지 않았더라도 보내야 합니다. 수정 후 계정 특정 요금은 당사의 요청을 변경하여 응답에서 전송됩니다.

_ACP2E-3354 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/55615e61)_

### 스테이징 및 미리보기

#### 고유한 사용자 지정 범주 속성을 사용할 때 예약된 업데이트를 업데이트할 수 없음

범주에 고유한 속성이 있는 경우 범주에 대한 예약된 업데이트를 업데이트할 수 없는 문제가 해결되었습니다

_ACP2E-3453 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

### 타기팅

#### [문제] 유지 관리 허용 목록에서 CIDR 범위 사용 허용

이제 시스템에서 유지 관리 모드 허용 IP 목록에서 CIDR 범위를 사용할 수 있도록 지원하여 IP 주소 범위가 유지 관리 모드를 건너뛸 수 있도록 합니다. 이전에는 유지 관리 모드에서 IP 목록을 허용하면 개별 IP 주소만 유지 관리 모드를 무시합니다.

_AC-9432 - [GitHub 문제](https://github.com/magento/magento2/issues/37943) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30699)_

### 세금

#### [문제] 기능/php8.1 생성자 속성 승격 wee graph ql

모듈 wee graph ql에서 대부분의 모든 속성을 생성자 속성 프로모션으로 바꿉니다.

_AC-13295 - [GitHub 문제](https://github.com/magento/magento2/issues/39309) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36975)_

#### 고정 제품 세금(FPT)이 구성 가능한 제품에서 작동하지 않음

구성 가능한 제품 변형에 대한 FPT가 제대로 작동하는지 확인합니다.

_ACP2E-3193 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec7e32a9)_

### 테스트 프레임워크

#### JSON 열 유형으로 인해 통합 테스트 실패 testDbSchemaUpToDate

이제 통합 테스트 중에 시스템이 데이터베이스 스키마의 JSON 열 유형을 올바르게 인식하므로 데이터베이스 스키마와 선언적 스키마 간의 불일치로 인한 테스트 실패를 방지할 수 있습니다. 이전에는 시스템이 MariaDB에서 JSON 열 유형을 LONGTEXT로 잘못 식별하여 통합 테스트가 실패했습니다.

_AC-11654 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [문제] PHPDoc 수정 맞춤법

이제 시스템은 PHPDoc의 맞춤법 수정으로 인해 IDE에서 더 이상 사용되지 않는 방법을 올바르게 인식합니다. 이전에는 PHPDoc의 철자 오류로 인해 IDE가 특정 메서드를 더 이상 사용되지 않는 것으로 인식하지 못했습니다.

_AC-13362 - [GitHub 문제](https://github.com/magento/magento2/issues/31399) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118: 세션이 만료된 후 지속적인 장바구니로 동작 확인

_AC-13478 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7d5e3906)_

#### 3d 파티 확장에서 사용할 수 있도록 정적 테스트 수정

_AC-13848 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9e383b4d)_

#### 실행 중이나 로그에 [내부] 고정장치 적용 오류가 표시되지 않습니다.

&#39;-

_ACP2E-3334 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest

고정 mftfs

_ACP2E-3458 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/078c387e)_

### UI 프레임워크

#### Prototype.js 보안 취약성 수정 CVE-2020-27511

시스템이 Prototype.js 1.7.3의 보안 취약점 CVE-2020-27511 을 해결하기 위해 업데이트되어 시스템의 전반적인 보안이 향상되었습니다. 이 업데이트 이전에는 제작된 HTML 태그를 제거하여 시스템에 ReDOS(Regular Expression Denial of Service)가 적용되기 쉬웠습니다.

_AC-12128 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less는 sourcemap에 pub/ 접두사를 사용합니다.

이제 grunt를 사용할 때 경로용 /pub 접두사 없이 less/css sourcemap을 생성하므로 웹 서버 구성에서 해결할 필요가 없습니다. 이전에는 sourcemap 경로에서 /pub 접두사를 사용하면 웹 서버의 특정 구성이 올바르게 작동해야 했습니다.

_AC-12189 - [GitHub 문제](https://github.com/magento/magento2/issues/38837) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38840)_

#### Ui 구성 요소 파일 필드

이제 시스템에서 UI 구성 요소 양식의 파일 필드를 올바르게 확인하므로, 파일을 선택할 때 오류 없이 양식을 제출할 수 있습니다. 이전에는 파일을 선택해도 유효성 검사가 실패하여 양식을 제출할 수 없었습니다.

_AC-12432 - [GitHub 문제](https://github.com/magento/magento2/issues/38908) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39004)_

#### [문제] js 콘솔의 날짜 형식 개선: 12시간에서 24시간으로 전환...

js 콘솔의 날짜 형식 개선: 12시간에서 24시간으로 전환

_AC-12645 - [GitHub 문제](https://github.com/magento/magento2/issues/38983) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38972)_

#### [문제] 개발자 모드에서 적은 수의 파일에 대해 sourceMap 생성 추가

이제 시스템은 개발자 모드에 있을 때 더 적은 수의 파일에 대한 소스 맵을 생성하여 스타일의 소스를 더 쉽게 식별할 수 있습니다. 이전에는 서버측 컴파일이 없는 개발자 모드에서 시스템을 실행할 때 스타일의 소스를 식별하는 것이 어려웠습니다.

_AC-12650 - [GitHub 문제](https://github.com/magento/magento2/issues/38982) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38977)_

#### 비활성화된 모듈에 대해 정적 콘텐츠를 배포하고 있습니다.

이제 시스템은 비활성화된 모듈과 관련된 CSS를 최종 CSS 출력 파일에서 제외하여 불필요한 스타일이 로드되지 않도록 합니다. 이전에는 비활성화된 모듈과 관련된 CSS가 최종 CSS 출력 파일에 포함되어 있어 불필요한 추가 스타일이 로드되었습니다.

_AC-1306 - [GitHub 문제](https://github.com/magento/magento2/issues/24666) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32922)_

#### 최소 재고 임계값으로 &quot;재고 부족&quot; 정렬의 일관되지 않은 동작

이제 시스템에서 최소 재고 임계값 설정을 준수하고 품절 항목을 일관되게 목록 맨 아래로 이동하여 재고 수준에 따라 카탈로그의 제품을 올바르게 정렬합니다. 이전에는 정렬 동작이 일관되지 않았으며 항목이 항상 재고 수준에 따라 올바른 순서로 표시되지는 않았고, 범주 계층을 저장, 새로 고침 또는 수정한 후 예상할 수 없었던 정렬 변경이 발생할 수 있었습니다.

_AC-13459 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/47b448e2)_

#### require.js 로드 문제에 대한 오류 보고 개선 제안

이 PR은 요구 사항이 구성 요소를 로드하지 못할 때 오류 메시지를 개선합니다.

_AC-13472 - [GitHub 문제](https://github.com/magento/magento2/issues/36761) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38971)_

#### PHP 8.4 사용 중단 오류로 인해 2.4-develop에서 빌드 오류 발생

_AC-14004 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [문제] 프론트엔드에 백엔드 블록 컨텍스트를 로드하지 않음

이제 시스템에서는 백엔드 블록 컨텍스트가 프론트엔드에 로드되지 않도록 하여 불필요한 백엔드 세션 및 잠재적 세션 잠금의 생성을 방지합니다. 이전에는 시스템이 프론트엔드에 백엔드 블록 컨텍스트를 잘못 로드하여 백엔드 세션을 생성하고 잠재적 세션 잠금이 발생했습니다.

_AC-9007 - [GitHub 문제](https://github.com/magento/magento2/issues/37617) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36368)_

#### [문제] 불필요한 스크립트 검토 요약 제거

이제 시스템은 보다 효율적이고 읽기 쉬운 코드를 위해 인라인 CSS 스타일을 대신 사용하여 등급 섹션에서 불필요한 JavaScript 스크립트를 제거하여 페이지 로드 시간을 최적화합니다. 이전에는 등급 섹션에 JavaScript 스크립트를 사용하면 페이지 로드 시간이 느려질 수 있었습니다.

_AC-9168 - [GitHub 문제](https://github.com/magento/magento2/issues/37776) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/34643)_

#### Recaptcha가 활성화된 경우 기프트 카드 잔액을 확인할 때 예외 발생

사용자는 장바구니 보기 및 편집 화면에서 기프트 카드 잔액을 가져올 수 있습니다. 이전에는 reCAPTCHA를 활성화하는 동안 이러한 세부 사항이 표시되지 않았습니다.

_ACP2E-2529 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [설명] 기능 요청 ADA 규정 준수

이제 시스템에서 지원되지 않는 CSS 속성을 제거하고 print.css 파일에서 지원되는 속성으로 대체하여 ADA를 준수할 수 있습니다. 이전에는 지원되지 않는 CSS 속성을 사용하면 브라우저 호환성 문제가 발생했습니다.

_ACP2E-2729 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/57a32313)_

#### [클라우드] AC 2.4.4-p8의 Effect-drop.js에 혼동 라이브러리 코드가 있습니다.

이제 시스템에서 effect-drop.js 라이브러리를 올바르게 구현하여 jQuery UI 효과가 제대로 작동하는지 확인합니다. 이전에는 effect-drop.js 라이브러리를 effect-clip.js 라이브러리로 잘못 덮어써서 jQuery UI 효과에 문제가 발생할 수 있었습니다.

_ACP2E-3061 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/35b1b1da)_

#### 사이트 헤더 | 고객 환영 섹션을 깨는 특수 문자

수정 후에는 고객 환영 섹션에 특수 문자가 올바르게 표시됩니다.

_ACP2E-3367 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1366ae5e)_

#### Daterange와 함께 고객 세그먼트 에디션 실패

날짜 중 하나만 편집한 경우 날짜 범위 조건으로 고객 세그먼트를 저장할 수 있습니다.

_ACP2E-3561 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a52ff98f)_
