---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '9924'
ht-degree: 0%
---
# Magento Open Source 해결 문제(v2.4.10-alpha1)

## v2.4.10-alpha1의 문제가 해결되었습니다.

Magento Open Source 2.4.10-alpha1 코어 코드에서 152개의 문제가 해결되었습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

#### [문제] 문자열 수량의 min()으로 인해 Creditmemo\Validation\QuantityValidator에 TypeError가 발생했습니다.

일괄 자동화된 주문 환불 중 재무 로깅 파이프라인을 안정화하고 API 요청 실패를 방지하기 위해 데이터 유형 캐스팅 가드레일이 내부 판매 대변 메모 팩토리 및 유효성 검사 계층에 추가되었습니다.

_AC-16056 - [GitHub 문제](https://github.com/magento/magento2/issues/40302) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40429) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40303)_

#### attribute_id 없이 REST API 속성 업데이트가 실패함

attribute_id가 제공되지 않은 경우 REST API를 통해 기존 제품 속성을 업데이트하지 못하는 문제를 해결했습니다. 이제 API가 URL의 attribute_code를 사용하여 속성을 올바르게 식별하고 성공적으로 업데이트합니다.

_AC-16424 - [GitHub 문제](https://github.com/magento/magento2/issues/40458) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c10554e1)_

#### REST API를 통해 옵션을 업데이트할 때 시각적 견본이 삭제됩니다.

카탈로그 데이터 무결성을 보호하고 자동화된 통합을 간소화하기 위해 표준 옵션 업데이트 중에 기존 시각적 또는 텍스트 견본 값이 실수로 지워진 EAV 견본 관리 계층에서 버그가 해결되었습니다.

_AC-9199 - [GitHub 문제](https://github.com/magento/magento2/issues/37794) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40872)_

#### 하나의 SKU가 누락된 경우 벌크 계층 가격 API가 전체 배치에 실패합니다

이전에는 벌크 계층 가격 업데이트 API(POST /V1/products/tier-prices)가 페이로드의 SKU가 없는 경우 전체 요청에 실패하여 업데이트 없이 유효한 SKU가 남았습니다. 이제 유효한 SKU가 성공적으로 처리되고 누락된 SKU는 항목별 오류로 보고되므로 하나의 잘못된 항목이 더 이상 전체 배치를 중단하지 않습니다.

_ACP2E-4998 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/51f6d191)_

#### 레이블 값이 기존 옵션 값 ID와 일치하는 경우 속성 업데이트가 실패합니다.

레이블이 기존 옵션의 ID와 일치할 때 REST API를 통해 새 드롭다운/다중 선택 제품 속성 옵션을 만들 수 없는 문제를 해결했습니다. 이전에는 관리 UI를 통해 동일한 옵션을 성공적으로 만들 수 있어도 API가 &quot;이미 있음&quot; 오류를 반환했으며(그리고 잘못된 옵션 ID를 반환할 수 있음),

_ACP2E-5107 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4d0357d7)_

### API, 가져오기 및 내보내기

#### REST API는 관리자 UI가 차단하면서 부정적인 제품 가격을 허용합니다

REST API 끝점을 통한 제품 가져오기는 이제 관리 UI 가져오기의 동작과 일관되게 가격 유형 속성(price, special_price, cost 및 관련 MSRP 필드)에 대한 음수 값을 거부합니다. 이전에는 API가 음수 가격을 묵묵히 수락하고 지속했습니다.

_ACP2E-4941 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/08b91f1a)_

### API, 순서

#### 주문 속도 제한 기능이 Valkey 캐시 백엔드와 호환되지 않음

이전에는 이 수정 속도 제한이 자동으로 무시되었으며 구성된 제한에 관계없이 각 요청이 허용되었습니다. 수정 후 구성된 제한을 초과하는 요청은 HTTP 429에서 올바르게 거부됩니다.

_ACP2E-4899 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 계정

#### [문제] 수정: 로그인 양식 암호 레이블이 잘못됨

고객 로그인 페이지의 암호 필드에 잘못된 레이블 연결이 있는 문제를 해결했습니다. 이제 암호 레이블이 암호 필드를 올바르게 타겟팅하여 자동화된 테스트 도구를 통해 올바로 식별할 수 있습니다.

_AC-16193 - [GitHub 문제](https://github.com/magento/magento2/issues/40353) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64eb754d)_

#### [문제] 파일 업로드를 위해 프론트엔드 입력 형식 확인

이제 고객 주소 파일을 업로드하면 처리하기 전에 대상 속성의 입력 유형이 파일 또는 이미지인지 확인할 수 있으므로 텍스트 및 기타 비파일 속성을 업로드 대상으로 남용할 수 없습니다. 잘못된 업로드 시도는 예기치 않게 실패하거나 허용되지 않는 파일 유형을 승인하는 대신 명확한 유효성 검사 오류를 반환합니다.

_AC-17076 - [GitHub 문제](https://github.com/magento/magento2/issues/40795) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40583)_

#### 웹 사이트 A에서 생성된 고객 토큰은 웹 사이트 범위 고객 구성의 웹 사이트 B에서 사용할 수 있습니다

다중 웹 사이트 인스턴스에 엄격한 고객 데이터 격리를 적용하기 위해 별도의 경계를 넘어 토큰의 유효성이 잘못 검사되는 GraphQL 인증 계층에서 보안 공백이 해결되었습니다.

_AC-17299 - [GitHub 문제](https://github.com/magento/magento2/issues/40847) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40858)_

#### [문제] PHP 8.5 사용 중단 수정: array_key_exists()의 키 매개 변수로 null 사용

PHP 8.5에서 게스트 체크아웃 중에 null 키가 있는 더 이상 사용되지 않는 array_key_exists() 호출로 인해 고객 로그인이 실패하는 문제를 해결했습니다. 이제 고객 로그인이 사용 중단 오류를 생성하지 않고 정상적으로 작동합니다.

_AC-17395 - [GitHub 문제](https://github.com/magento/magento2/issues/40875) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/515d3dd3)_

#### [문제] magento/magento2: requestPasswordResetEmail 및 resetPassword GraphQL 돌연변이에 i18 번역 추가

완전히 현지화된 헤드리스 상점 경험을 보장하기 위해 국제화(i18n) 번역 기능이 고객 계정 복구 API 엔드포인트에 추가되었습니다

_AC-9356 - [GitHub 문제](https://github.com/magento/magento2/issues/29658) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/28950)_

### 관리자 UI

#### 집계 데이터가 사용되는 경우 대시보드에 기본적으로 최근 7일이 표시되어야 함

집계된 판매 데이터가 활성화되면 대시보드에 기본적으로 오늘 이 표시되던 문제가 수정되었습니다. 이제 집계된 데이터를 사용할 때 대시보드에 기본적으로 최근 7일이 표시됩니다.

_AC-13799 - [GitHub 문제](https://github.com/magento/magento2/issues/28152) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 장바구니 페이지와 제품 페이지의 FPT 값은 간단한 제품에 대한 동일한 구성에 대해 다릅니다

동일한 세금 구성에 대한 제품 및 장바구니 페이지에 고정 제품 세금(FPT) 값이 다르게 표시되는 문제를 해결했습니다. 이제 FPT 값이 제품, 카탈로그, 미니 장바구니 및 장바구니 페이지에 일관되게 표시됩니다.

_AC-17007 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 레이지 구성 구현

기존 구성 동작을 유지하면서 범위가 지정된 시스템 구성 데이터를 신속하게 해결하여 구성 로드 성능을 향상시키는 성능 최적화.

_ACP2E-4751 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/65f660bd)_

#### HugeRTE 편집기가 이모지를 차단함 - javascript 유효성 검사 실패

PageBuilder 콘텐츠 유형 양식(텍스트, 배너, 슬라이드) 내에서 편집할 때 HugeRTE가 utf8mb4 이모지가 포함된 콘텐츠(예: 🔵⚪🔴)의 저장을 차단했던 문제를 해결했습니다. 이전에는 이러한 양식 형식에 대한 wysiwyg 유효성 검사 구성이 `allowUtf8mb4`에서 `false`(으)로 확인되어 편집기가 데이터베이스가 utf8mb4를 완전히 지원하는 설치에서도 4바이트 UTF-8 문자를 거부했습니다.

_ACP2E-4822 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### 관리자 패널의 고객 편집 페이지에서 큰 주소록이 있는 고객을 볼 때 관리자가 로그아웃됩니다

관리자 패널의 고객 편집 페이지에서 큰 주소록이 있는 고객을 볼 때 관리자가 로그아웃되는 문제를 해결했습니다

_ACP2E-4875 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### 주문이 판매 그리드에 표시되지 않음

비동기 그리드 인덱싱이 활성화된 경우 조정 커서가 가장 최근 엔티티에 도달하면 재설정되므로 판매 그리드에 새 주문이 표시되는 것이 지연되는 문제가 해결되었습니다. 이제 새 항목이 다음 cron 실행 시 격자에 나타납니다.

_ACP2E-4893 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

### 관리자 UI, 순서

#### 두 개의 그룹화된 제품이 동일한 단순 제품을 공유할 때 관리자 생성 주문에서 그룹화된 제품에 대해 잘못된 가격이 표시됨

동일한 단순 제품을 공유하는 두 개의 그룹화된 제품이 장바구니에 추가되지 않고 모두 구성된 경우, 관리자 생성 주문의 그룹화된 제품 가격이 잘못 계산되는 문제가 해결되었습니다.

_ACP2E-4965 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/08b91f1a)_

### 관리 UI, UI 프레임워크

#### Magento2가 잘못된 메뉴 선언에 오류를 표시하지 않고 홈 페이지로 리디렉션됩니다.

확장 개발 워크플로우를 최적화하고 안정적인 백엔드 로드를 보장하기 위해 실행 가능한 진단 메시지를 표시하는 대신 잘못된 관리 메뉴 선언이 자동 브라우저 루프 오류를 트리거하는 구조적 라우팅 결함을 해결했습니다.

_AC-7543 - [GitHub 문제](https://github.com/magento/magento2/issues/36632) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40881)_

### Analytics/보고

#### [QUANS] 고급 보고의 고객 KPI 표에 고객 전자 메일 ID와 이름을 표시할 수 있습니까?

이제 Adobe Commerce은 고급 보고로 내보낸 데이터에 고객의 이름, 중간 및 성을 포함하므로 고객 KPI 테이블에 고객 이름을 표시할 수 있습니다. 이전에는 인코딩된 고객 ID만 내보내므로 판매자는 Advanced Reporting에서 이름으로 고객을 식별할 수 없었습니다.

_ACP2E-3928 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4d0357d7)_

#### sales_bestsellers_aggregated_monthly에 대한 INSERT 증가

aggregate_sales_report_bestsellers_data cron 의 성능이 향상되었습니다.

_ACP2E-4559 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 장바구니에 추가 이벤트 페이로드는 GA4 전자 상거래 형식이 아닌 레거시 Universal Analytics Enhanced Ecommerce 형식입니다.

수정하기 전에 Google Tag Manager를 통해 Google Analytics 4로 전송된 전자 상거래 이벤트는 기존 Universal Analytics 형식을 사용했으며 여러 체크아웃 이벤트가 누락되었습니다. 수정 후 모든 전자 상거래 이벤트는 올바른 GA4 형식을 사용하며, 전체 체크아웃 funnel이 추적됩니다.

_ACP2E-5176 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### B2B, 주문

#### 59M+ 견적 테이블 정리에 대한 도움말(sales_clean_quotes를 실행할 수 없음)

큰 따옴표 테이블이 있는 인스턴스에서 `sales_clean_quotes` cron 작업이 시간 초과되는 문제를 해결했습니다. 이전에는 정리 쿼리가 `negotiable_quote` 테이블에서 모든 열을 불필요하게 선택했기 때문에 MySQL이 수백만 행에 대해 전체 파일 정렬을 수행했으며, PHP 모델 계층을 통해 각 견적이 개별적으로 삭제되어 성능 비용이 증가했습니다.

_ACP2E-4891 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

### 장바구니 및 체크아웃

#### 관련 제품에 대한 장바구니에 추가 알림

제품과 관련 제품을 함께 추가할 때 장바구니에 추가 알림에 관련 제품이 포함되지 않던 문제를 수정했습니다.
이제 알림에 장바구니에 추가된 두 제품의 이름이 표시됩니다.

_AC-11976 - [GitHub 문제](https://github.com/magento/magento2/issues/27164) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/515d3dd3)_

#### [문제] CartRepositoryInterface.php 업데이트

장바구니를 저장할 때 throw될 수 있는 예외를 선언하도록 CartRepositoryInterface.php를 업데이트했습니다. 이렇게 하면 기본 장바구니 저장 구현과 인터페이스가 일관되게 유지됩니다.

_AC-13323 - [GitHub 문제](https://github.com/magento/magento2/issues/39328) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 체크아웃 배송 단계에서 새 주소를 추가할 때 배송 주소의 [버그] 회사 필드가 다중 스토어 설정에서 null로 설정되었습니다.

다중 스토어 설정에서 체크아웃 중에 고객이 새 배송 주소를 추가할 때 회사 필드가 저장되지 않는 문제를 해결했습니다. 이제 회사 값이 견적, 주문 및 고객 주소록에 올바르게 저장됩니다.

_AC-13456 - [GitHub 문제](https://github.com/magento/magento2/issues/39424) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal > 고객 데이터 불일치(접두사, 이름, 성)

PayPal SEPA 체크아웃 흐름 중에 고객 이름 세부 정보가 잘못 매핑되는 문제를 해결했습니다. 이제 접두사, 이름 및 성이 불일치 없이 순서대로 올바르게 채워집니다.

_AC-15366 - [GitHub 문제](https://github.com/magento/magento2/issues/39061) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 가상 제품에 대한 잘못된 free_shipping 플래그

여러 품목을 장바구니에 추가할 때 가상 제품에 대해 free_shipping 플래그가 잘못 설정되는 문제가 해결되었습니다. 적용 가능한 무료 배송 규칙이 적용되면 이제 모든 항목에 대해 플래그가 올바르게 설정됩니다.

_AC-15648 - [GitHub 문제](https://github.com/magento/magento2/issues/40184) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c10554e1)_

#### 게스트 장바구니에 추가: 항목이 올바르게 지속됨에도 불구하고 미니 장바구니/고객 데이터 &quot;장바구니&quot; 섹션의 장바구니가 비어 있음

제품을 장바구니에 추가한 후 바로 게스트 미니 장바구니에 항목이 반영되지 않던 문제를 수정했습니다. 이제 미니 장바구니 카운터와 드롭다운이 올바르게 업데이트되고 추가된 제품이 예상대로 장바구니에 표시됩니다.

_AC-17973 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2b218686)_

#### AJAX 장바구니에 추가 오류 메시지 손실 role=&quot;alert&quot; 의미 체계

AJAX 장바구니 추가 오류 메시지가 상점 첫 화면에 표시되지만 화면 판독기에서 알리지 않는 문제를 해결했습니다. 이제 적절한 액세스 가능성 지원을 위해 액세스 가능한 role=&quot;alert&quot; 영역 내에 장바구니에 추가 오류가 표시됩니다.

_AC-18036 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2b218686)_

#### 배송 금액에 대한 후속 규칙 버리기

정확한 판촉 가격 책정 및 구성된 할인 규칙을 엄격히 준수하기 위해, 낮은 우선 순위 배송 할인이 잘못 적용된 장바구니 가격 규칙 계산기의 결함을 해결했습니다

_AC-9612 - [GitHub 문제](https://github.com/magento/magento2/issues/37985) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40869)_

#### 오류가 트리거되더라도 중복 주문이 생성됨

여전히 잘못된 고객 주소로 주문을 할 수 있는 문제가 해결되었습니다.

_ACP2E-4774 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 체크아웃에 대한 제품의 성능 영향(합계 정보, 예상 배송 모듈) 구성 가능

수정 전에, 첫 번째 판매 가능한 하위 항목이 하위 목록에 늦게 나타날 때 여러 하위 제품이 있는 구성 가능한 제품에 대해 합계 정보 및 예상 배송 방법과 같은 체크아웃 요청이 크게 느려질 수 있습니다. 수정 후에는 이 성능 저하가 더 이상 발생하지 않으며 첫 번째 판매 가능한 하위 항목의 위치에 관계없이 응답 시간이 일관되게 유지됩니다.

_ACP2E-4805 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 모든 장바구니 페이지 보기에서 다시 계산된 장바구니 합계

장바구니 페이지에서 장바구니 합계 요청을 최적화했습니다. 장바구니 합계는 모든 장바구니 페이지 보기에서 두 번 다시 계산되었습니다.

_ACP2E-4817 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### EAV(고객 주소 속성) 도시 및 거리의 유효성 검사 규칙이 하드코딩된 유효성 검사 규칙과 충돌합니다.

도시 유효성 검사기가 100자를 초과하는 유효한 도시 이름(데이터베이스 한도는 255개)을 잘못 거부하고 255자를 초과하는 거리 주소가 데이터베이스에서 없이 자동으로 잘릴 수 있는 문제를 해결했습니다.\
유효성 검사 오류를 반환합니다. 이제 두 유효성 검사기 모두 모든 주소 테이블에 걸쳐 가장 좁은 데이터베이스 열 제약 조건에 맞게 정렬된 제한을 적용합니다.

_ACP2E-4861 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### [Storefront] Add-to-Cart &quot;요청한 수량을 사용할 수 없습니다.&quot; 메시지가 PDP에서 간헐적으로 렌더링되지 않습니다.

재고 비가용성 메시지(&quot;요청된 수량을 사용할 수 없습니다. 수량을 줄이십시오.&quot;)가 표시되는 문제를 해결했습니다. 장바구니에 추가 시도가 실패한 후 제품 세부 사항 페이지에 가 간헐적으로 표시되지 않았습니다. 이전에는 장바구니에 이미 사용 가능한 재고가 완전히 예약된 제품에 대해 장바구니에 추가를 반복적으로 클릭하면 페이지가 오류 피드백 없이 자동으로 새로 고쳐질 수 있었습니다.

_ACP2E-5071 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d70f246)_

#### 로그아웃 시 지속성 지우기 = Yes일 때 지속 장바구니가 자연 세션 만료 시 지워짐

브라우저 세션이 만료되었을 때 영구 장바구니가 지워지는 문제를 해결했습니다. 이전에는 로그아웃 시 지속성 지우기 가 활성화된 상태에서 만료된 세션이 장바구니를 비우고 구매자가 로그아웃하지 않았더라도 영구적인 쿠키를 제거했습니다.

_ACP2E-5088 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

#### 체크아웃을 다시 시도할 때 restoreQuote() 후에 청구 주소에서 게스트 견적 customer_email이 재동기화되지 않음

실패한 게스트 체크아웃을 다시 시도하는 경우 업데이트된 이메일이 아닌 이전에 입력한 이메일로 주문이 처리되던 문제를 해결했습니다.

_ACP2E-5188 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

### 장바구니 및 체크아웃, GraphQL

#### Quote GraphQL API 는 ISO 통화 코드 대신 통화 개체를 견적 필드에 지정할 수 있습니다

통화 개체를 할당하는 대신 ISO 통화 코드를 견적의 스토어 및 견적 통화 필드에 할당하도록 Quote GraphQL API 를 업데이트했습니다.

_ACP2E-5229 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### 카탈로그

#### [문제] Magento_ConfigurableProductGraphQl, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting &amp; Magento_Swatches 모듈에 대한 module.xml 파일 개선 사항.

4개의 핵심 하위 모듈에서 중복 Magento_Catalog 종속성을 제거하여 모듈 선언 아키텍처를 최적화했습니다. 이 정리를 통해 종속성 트리에서 불필요한 중복을 해결하고 모듈 로드 순서 계산을 간소화할 수 있으며, 새로운 변경 사항을 적용하지 않고도 장기 프레임워크 유지 관리를 향상시킬 수 있습니다.

_AC-10762 - [GitHub 문제](https://github.com/magento/magento2/issues/30675) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30638)_

#### 구성을 위한 getUsedProducts 함수에서 메모리 누수가 발생할 수 있습니다.

구성 가능한 여러 제품을 처리하면 시간이 지남에 따라 실행 시간 및 메모리 사용량이 증가하던 문제를 해결했습니다.
이제 구성 가능한 제품을 점진적인 둔화와 메모리 증가 없이 처리할 수 있습니다.

_AC-10942 - [GitHub 문제](https://github.com/magento/magento2/issues/37639) - [GitHub 코드 기여](https://github.com/magento/inventory/commit/8c058c2e)_

#### 비앵커 범주에 표시되는 범주별 쇼핑 필터

관리자에서 카테고리 필터가 비활성화되어 있어도 앵커가 아닌 카테고리에 카테고리 별 쇼핑 필터가 표시되던 문제를 해결했습니다.
이제 구성된 설정에 따라 필터가 상점 맨 앞에 숨겨집니다.

_AC-10945 - [GitHub 문제](https://github.com/magento/magento2/issues/38379) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64eb754d)_

#### 견적 및 견적 항목에 있는 apply_rule_ids의 데이터 유형이 다릅니다.

절대 데이터베이스 스키마 일관성을 보장하고 대량 프로모션 스토어에서 중요한 장바구니 데이터 불일치를 방지하기 위해 데이터 열 추적 활성 프로모션 정의가 상위 체크아웃 구조로 확장되었습니다.

_AC-14518 - [GitHub 문제](https://github.com/magento/magento2/issues/39838) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40540)_

#### 가격이 전체적으로 범위가 지정된 경우 제품 컬렉션 범위 `decimal` 특성을 가져올 수 없습니다.

국제 설정에서 정확한 상점 가격 및 속성 렌더링을 보장하기 위해, 저장소별 십진수 값이 기본 전역 값으로 잘못 대체된 핵심 데이터 수집 버그가 해결되었습니다.

_AC-15806 - [GitHub 문제](https://github.com/magento/magento2/issues/40218) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40419)_

#### GET 매개변수를 잘못 처리함

플랫폼 안정성을 개선하고 체크아웃 funnel을 보호하기 위해 블록 수준의 입력 유효성 검사 레이어를 추가하여 잘못된 형식의 URL 쿼리가 상점 첫 제품 페이지에서 충돌하는 것을 방지했습니다.

_AC-16262 - [GitHub 문제](https://github.com/magento/magento2/issues/40405) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes가 모든 장바구니 쿼리에서 트리거됩니다.

고객 체크아웃 시 데이터베이스 실행 부담을 줄이고 최적화되지 않은 데이터베이스 히트를 제거하기 위해 판매 규칙 제품 구성 플러그인은 조건부로 실행하고 캐싱 구조를 활용하도록 최적화되었습니다.

_AC-16559 - [GitHub 문제](https://github.com/magento/magento2/issues/40226) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40251)_

#### [문제] [PHPDOC] Magento\Sales\Model\Order에서 함수 orderComment 수정

PHPStan(레벨 5 이상)과 같은 엄격한 링크 엔진에서 엄격한 입력 제한을 제거하고 정적 분석 정확도를 향상시키며 개발자 경험을 개선하기 위해, 판매 주문 핵심 하위 시스템 내에서 인라인 구조 설명서 블록이 표준화되었습니다.

_AC-16759 - [GitHub 문제](https://github.com/magento/magento2/issues/39575) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39572)_

#### [문제] [버그] GraphQL SearchCriteriaValidator가 로드되지 않음 - module-graph-ql di.xml 배열 재정의에서 제거됨

강력한 쿼리 유효성 검사를 유지하고 플랫폼 가드레일을 적용하기 위해 SearchCriteriaValidator 레이어가 실수로 비활성화된 DI(종속성 삽입) 구성 오류가 해결되었습니다.

_AC-16959 - [GitHub 문제](https://github.com/magento/magento2/issues/40762) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40742)_

#### strpos()에는 매개 변수 1이(가) 문자열, 배열이 지정되어야 합니다. | magento/module-eav

상점 안정성을 보호하고 중단 없는 고객 검색 환경을 제공하기 위해 고급 카탈로그 검색 처리 엔진 내에서 중요한 유형 불일치 문제가 해결되었습니다.

_AC-1706 - [GitHub 문제](https://github.com/magento/magento2/issues/33588) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40422)_

#### 고객이 페이지를 방문하면 빈 견적 레코드가 생성됩니다.

상점 첫 화면의 제품 페이지를 방문해도 일부 상황에서는 빈 견적 레코드가 생성되지 않습니다.
이전에는 고객이 상점 첫 화면의 제품 페이지를 방문할 때 빈 견적 레코드가 생성되었습니다

_ACP2E-4682 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 제품 세부 정보 페이지 &quot;Weight&quot; 속성에 &quot;Additional Information&quot; 섹션에 단위 접미사가 표시되지 않음

Storefront 제품 페이지의 Weight 속성에 구성된 측정 단위(lbs 또는 kgs) 없이 &quot;추가 정보&quot; 또는 &quot;추가 정보&quot; 섹션의 원시 숫자 값만 표시되는 문제를 수정했습니다.

_ACP2E-4808 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] 다음에 다시 동기화할 때까지 카탈로그 가격 규칙 활성화가 Live Search에 반영되지 않음 — 가격 피드 동기화 지연

카탈로그 가격 규칙을 활성화해도 나중에 강제 재동기화하기 전까지 라이브 검색에서 가격이 업데이트되지 않는 문제를 수정했습니다. 가격 피드 인덱서는 종속된 카탈로그 규칙 인덱서가 완료되어 오래된 가격이 내보내지기 전에 실행될 수 있습니다. 완료되지 않은 종속성이 있는 인덱서는 이제 다음 cron run으로 연기되므로 가격 피드는 항상 최신 가격에 대해 실행됩니다.

_ACP2E-5029 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec436b10)_

#### 새로 추가된 제품 이미지에 대해 대체 텍스트(레이블)가 저장되지 않음

미디어 갤러리에서 파일 이름 충돌로 인해 업로드한 파일의 이름이 저장 시 로 바뀌었을 때 새로 업로드한 제품 이미지의 대체 텍스트(레이블)가 저장되지 않던 문제를 수정했습니다. 이전에는 이미지 역할 속성(image, small_image, thumbnail)이 올바르게 저장되었지만 해당 *_레이블 속성이 자동으로 삭제되어 상점 첫 번째 검색 및 목록 페이지에서 대체 텍스트가 비어 있었습니다. 이제 갤러리 만들기 처리기에서 이름이 변경된 파일을 원래 이미지 항목으로 다시 확인하므로 지정된 모든 이미지 역할에 대해 레이블이 유지됩니다. 따라서 제품 작성 중에 입력된 대체 텍스트가 상점 전면에서 안정적으로 저장되고 렌더링됩니다.

_ACP2E-5216 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

#### 사용자가 제품 상태 편집 리소스가 부족한 경우 관리자에서 제품 추가 페이지를 여는 동안 PHP 8.5 &quot;null as array offset&quot; 사용 중단 오류 발생

이전에는 &quot;제품 상태 편집&quot; 권한이 없는 관리자 사용자가 제품 추가 페이지를 열 때 &quot;null as array offset&quot; 사용 중단 오류가 발생할 수 있었습니다. 사용자의 제품 상태 권한에 관계없이 페이지가 올바르게 로드되도록 이 문제가 수정되었습니다.

_ACP2E-5248 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### 카탈로그, GraphQL

#### [GraphQl] 제품 쿼리 가격 필터 문제(adminhtml에 입력된 순 가격)

GraphQL 제품 쿼리에서 가격 필터를 적용할 때 세금을 고려하지 않는 문제를 해결했습니다.
이제 가격 필터는 표시된 세금 포함 가격을 사용하므로 지정된 가격 범위 내의 제품만 반환됩니다.

_AC-6883 - [GitHub 문제](https://github.com/magento/magento2/issues/36337) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8b67e8ed)_

### 카탈로그, SEO

#### 모든 스토어 보기에 대해 url_key 변경 시 범주 url_path가 동기화되지 않음

이전에는, &quot;모든 스토어 보기&quot; 범위에서 범주의 URL 키를 변경하면 저장소가 범위가 지정된 하위 범주에 오래된 url_path나 접두사가 잘못된 url_path가 지정될 수 있으며, 고유한 저장소별 url_path 재정의로 범주를 편집하면 새로 입력한 URL 키 대신 사전 편집 URL 키가 선택될 수 있습니다. 이제 수정되었습니다. URL 키 변경 사항이 올바른 상위 경로를 사용하여 올바른 계층 순서로 모든 저장소 범위 하위 항목에 올바르게 캐스케이드되고, 방금 변경한 URL 키를 사용하여 범주의 저장소 범위 url_path 재정의가 다시 계산되므로 저장 후 즉시 저장소 범위 URL이 정확하게 유지됩니다.

_ACP2E-5113 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

### 클라우드, 프레임워크

#### SymfonyL2가 활성화된 상태에서 성능 회귀 및 잘못된 캐시 스토리지

L1 캐시 저장소 경로를 절대 경로(예: /dev/shm)로 구성하면 해당 경로가 자동으로 var/ 디렉터리로 리디렉션되는 문제와 큰 카탈로그의 캐시 태그를 무효화하면 Redis 작업 차단으로 인해 상당한 응답 시간 지연이 발생할 수 있는 별도의 성능 문제를 해결했습니다.

_ACP2E-4989 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/51f6d191)_

### 콘텐츠

#### 페이지 빌더 ajax 미리 보기 요청이 번역 캐시가 비활성화된 상태에서 500 오류를 반환함

이제 번역 캐시의 활성화 여부에 관계없이 PageBuilder 미리 보기가 올바르게 렌더링됩니다. 이전에는 번역 캐시가 비활성화되어 있으면 PageBuilder 미리 보기를 렌더링하지 못했습니다.

_ACP2E-5118 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### 이전 미디어 갤러리 활성화가 활성화되면 애니메이션 GIF 업로드가 PNG로 변환됩니다

미디어 갤러리를 통해 업로드된 GIF 애니메이션 이미지가 레거시 미디어 갤러리가 활성화된 경우 PNG로 변환되던 문제를 수정했습니다. 이전에는 [프론트엔드 크기 조정 사용]을 켜면 이전 미디어 갤러리를 통해 업로드된 애니메이션 GIF가 애니메이션을 잃고 정적 PNG 파일로 저장되었습니다. 이제 애니메이션 GIF가 업로드되고 원래 형식으로 저장됩니다.

_ACP2E-5232 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### 컨텐츠 / CMS

#### [문제] 이미지 특성 레이블에 작은 따옴표가 포함된 경우 제품 갤러리 탭을 수정합니다

관리 패널에서 안정적이고 중단 없는 카탈로그 관리 경험을 보장하기 위해 백엔드 제품 작업 영역 인터페이스를 완전히 손상시키는 JavaScript 형식 오류가 해결되었습니다

_AC-16474 - [GitHub 문제](https://github.com/magento/magento2/issues/40519) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40870)_

#### [문제] 크기 조정된 이미지 URL에 액세스했지만 아직 존재하지 않는 경우 성능을 개선합니다.

자산 전달 응답성을 극대화하고 서버 디스크 I/O를 크게 줄이며 심각한 서버 프로세서 스파이크를 방지하기 위해 카탈로그 이미지 생성 하위 시스템은 누락된 미디어 URL을 철저하게 온디맨드로 처리하도록 최적화되었습니다.

_AC-16547 - [GitHub 문제](https://github.com/magento/magento2/issues/40399) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40388)_

#### 회귀: UTF-8이 아닌 인코딩된 URI 구성 요소가 2.4.7-p5의 CatalogWidget에서 여전히 &quot;값을 직렬화할 수 없음&quot;이 발생합니다

잘못된 프로덕션 웹 트래픽으로 인해 발생하는 중요한 렌더링 오류를 방지하기 위해 요청된 URL 내에서 UTF-8이 아닌 데이터 시퀀스를 정상적으로 처리하도록 카탈로그 위젯 블록이 보강되었습니다.

_AC-17264 - [GitHub 문제](https://github.com/magento/magento2/issues/40824) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40825)_

#### 전역 디자인 구성 범위를 편집할 때 `Using null as an array offset is deprecated, use an empty string instead`

콘텐츠 > 디자인 > 구성 아래의 전역 범위를 편집하면 더 이상 사용되지 않는 null 배열 오프셋으로 인해 PHP 8.5에서 HTTP 500 오류가 반환되던 문제를 해결했습니다. 이제 오류 없이 전역 디자인 구성이 성공적으로 열립니다.

_AC-17456 - [GitHub 문제](https://github.com/magento/magento2/issues/40886) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/515d3dd3)_

### 프레임워크

#### 미디어 DB 스토리지가 사용 중이 아니거나 사용하지 않을 때 media_storage_file_storage에서 선택

불필요한 데이터베이스 쿼리 오버헤드를 줄이고 소음이 발생하는 시스템 예외를 없애기 위해 시스템이 로컬 파일 시스템을 사용하도록 명시적으로 구성된 경우 데이터베이스 저장소 검사를 무시하도록 미디어 파일 동기화 계층을 최적화했습니다

_AC-10586 - [GitHub 문제](https://github.com/magento/magento2/issues/38116) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40480)_

#### 쿠키 저장소가 배열인 경우 예외 생성자에 치명적인 오류가 발생했습니다.

잘못된 스토어 쿠키 값으로 인해 PHP에 치명적인 오류가 발생하는 문제가 해결되었습니다.
이제 Magento는 스토어 쿠키에 잘못된 값이 포함되어 있을 때 &quot;잘못된 스토어 매개변수&quot; 예외를 올바르게 발생시킵니다.

_AC-10888 - [GitHub 문제](https://github.com/magento/magento2/issues/38365) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [문제] Magento\Customer\Model\Address\Config에서 정적 const 사용

사용자 지정 주소 템플릿 경로를 사용하기 위해 사용자 지정 주소 구성 클래스에서 getFormats()를 복제해야 하는 문제가 해결되었습니다. 이제 사용자 지정 주소 구성은 메서드를 복제하지 않고 정적 상수를 사용하여 자체 템플릿 경로를 정의할 수 있습니다.

_AC-12906 - [GitHub 문제](https://github.com/magento/magento2/issues/39135) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 제품 컬렉션에 processFilter를 사용할 수 없음

FilterProcessor를 사용하여 제품 컬렉션에 여러 필터를 적용하면 PHP 오류가 발생하는 문제를 해결했습니다. 이제 여러 필터 조건을 사용하여 제품 컬렉션을 올바르게 필터링할 수 있습니다.

_AC-15018 - [GitHub 문제](https://github.com/magento/magento2/issues/40014) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7aecc9f1)_

#### 대형 카탈로그의 잠재적 인덱서 성능 문제 - 최신 버전을 식별하기 위한 대량 삽입 및 잠금 전체 CL 테이블

대규모 엔터프라이즈 규모의 카탈로그에서 데이터베이스 성능을 보호하기 위해 시스템 데이터베이스 인덱서 파이프라인을 강화하여 예약된 데이터 수정 사항을 제한된 배치로 구문 분석하여 고압 데이터베이스 잠금을 제거했습니다.

_AC-16238 - [GitHub 문제](https://github.com/magento/magento2/issues/40331) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40546)_

#### [문제] 성능 개선

불필요한 메모리 할당을 제거하고 런타임 처리 오버헤드를 줄이기 위해 최적화된 PHP 기본 동작을 활용하도록 몇 가지 핵심 문자열 조작 루틴을 리팩터링했습니다.

_AC-16565 - [GitHub 문제](https://github.com/magento/magento2/issues/40383) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40375)_

#### [문제] 비GNU Linux 시스템에서 GLOB_BRACE에 대한 지원 수정

경량 가상화 환경에서 원활한 배포 기능을 보장하기 위해 Alpine Linux Docker 이미지와 같은 비 GNU 라이브러리를 사용하는 시스템에 대한 실행 지원을 완전히 복원하도록 중요한 경로 검색 버그가 수정되었습니다.

_AC-16568 - [GitHub 문제](https://github.com/magento/magento2/issues/40552) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40538)_

#### 기본 제공 FPC 식별자 생성에 사용된 쿼리에 마케팅 매개 변수가 다시 추가되었습니다.

캐시 적중률을 향상시키고 서버 성능 회귀를 제거하기 위해 마케팅 및 추적 쿼리 매개 변수가 실수로 캐시 식별자 서명에 다시 도입된 기본 내장된 전체 페이지 캐시(FPC) 시스템의 구조적 결함이 수정되었습니다.

_AC-16583 - [GitHub 문제](https://github.com/magento/magento2/issues/40350) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40349)_

#### 메시지 대기열 통신에 판촉된 속성이 있는 일반 오브젝트에 대한 지원 추가

최신 PHP 개발 사례를 지원하고 비동기 아키텍처 워크플로를 단순화하기 위해 프레임워크 반사 엔진이 공용, 승격 및 읽기 전용 생성자 속성을 활용하여 DTO(데이터 전송 개체)를 기본적으로 처리하도록 향상되었습니다.

_AC-16672 - [GitHub 문제](https://github.com/magento/magento2/issues/36660) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40457)_

#### [문제] 수정: 실제 열 형식 자체 검사가 부호 없는/nullable 프로세서를 건너뛰고 기본값을 사용합니다.

정확한 시스템 설정 추적을 위해 명시적 정밀도 또는 배율 특성이 없는 DOUBLE UNSIGNED 열에 대해 선언적 스키마 확인 명령이 보류 중인 수정 변경 사항을 지속적으로 보고한 데이터베이스 추상화 오류가 해결되었습니다.

_AC-16758 - [GitHub 문제](https://github.com/magento/magento2/issues/40646) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40582)_

#### [기능] 관리자 구성에서 개별 선택 옵션에 대해 &quot;사용 안 함&quot; 상태를 지원합니다.

백엔드 양식 유연성을 강화하고 개발자에게 세분화된 레이아웃 제어를 제공하기 위해 개별 옵션 태그를 내부 양식 요소로 선택할 수 없도록 표시하는 프레임워크 수준 지원이 도입되었습니다.

_AC-16761 - [GitHub 문제](https://github.com/magento/magento2/issues/40564) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40565)_

#### ⚡ 성능: StoreManager의 메모리 및 저장소 모듈의 플러그 인 오버헤드가 없습니다.

CPU 실행 부담을 크게 줄이고 불필요한 애플리케이션 메모리 이탈을 최소화하기 위해 중복 저장소 확인 프로세스를 가로채는 중요한 구성 값 캐싱 루틴이 구현되었습니다.

_AC-16838 - [GitHub 문제](https://github.com/magento/magento2/issues/40706) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40732)_

#### [문제] 수정: JwkFactory에서 데드 openssl_free_key() 코드 경로 제거

구조적 기술 부채를 정리하고 암호화 도구를 최신 실행 프로필에 맞추기 위해 레거시 리소스 해제 후크를 JSON 웹 키 유틸리티 백엔드에서 제거했습니다.

_AC-16958 - [GitHub 문제](https://github.com/magento/magento2/issues/40761) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40688)_

#### [문제] PHPDoc 수정 맞춤법

높은 코드 품질 표준을 유지하고 IDE(통합 개발 환경) 코드 힌트 정확도를 개선하기 위해 핵심 프레임워크 모듈 전반의 인라인 코드 문서 계층에 구조적 정리가 적용되었습니다.

_AC-16960 - [GitHub 문제](https://github.com/magento/magento2/issues/40763) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40745)_

#### [문제] perf(di:compile): Type, Config/Reader 및 ClassReader의 캐시 ReflectionClass 인스턴스화

컴파일 시간을 크게 단축하고 CI(지속적 통합) 배포 처리량을 최대화하기 위해 내부 종속성 삽입 컴파일러 백 엔드(`setup:di:compile`)가 중복 PHP 반사 주기를 제거하도록 최적화되었습니다.

_AC-17077 - [GitHub 문제](https://github.com/magento/magento2/issues/40796) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40615)_

#### [문제] `{{block template="Magento_Module::path/to/template.phtml"}}`을(를) 허용하도록 Filter.php를 업데이트하고 \Magento\Framework\View\Element\Template을 기본 클래스로 설정합니다.

콘텐츠 생성을 단순화하고 CMS 지시문을 템플릿 레이아웃 표준에 맞게 조정하기 위해 코어 마크업 태그 처리 시스템이 명시적 클래스 정의 없이 블록 선언을 지원하도록 개선되었습니다.

_AC-17078 - [GitHub 문제](https://github.com/magento/magento2/issues/38477) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38469)_

#### [문제] 성능(di:compile): 컴파일 중에 Memoize Interception 구성 범위 읽기

사이트 배포 및 자동화된 백엔드 컴파일 속도를 크게 높이기 위해 종속성 삽입 컴파일러(`setup:di:compile`)를 최적화하여 중복 XML 구문 분석 작업을 제거했습니다.

_AC-17313 - [GitHub 문제](https://github.com/magento/magento2/issues/40852) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40614)_

#### 보안 취약성을 방지하기 위해 underscore.js를 1.13.8로 업그레이드하십시오

번들 Underscore.js 라이브러리(lib/web/underscore.js)가 1.13.7에서 1.13.8로 업그레이드되었습니다. 구성을 변경할 필요가 없습니다.

_AC-17349 - [GitHub 문제](https://github.com/magento/magento2/issues/40857) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/12d0be1e)_

#### 배포 대상이 symlink인 경우 magento-composer-installer는 setup/(및 기타 매핑된 dirs)을 자동으로 채우지 않습니다.

배포 대상이 심볼 링크로 구성된 경우 magento-composer-installer가 setup/ 및 다른 Composer 매핑 디렉터리를 자동으로 채우지 못하는 문제를 해결했습니다. 이로 인해 파일이 누락되고 Commerce 배포가 완료되지 않을 수 있습니다.

_AC-17360 - [GitHub 문제](https://github.com/magento/magento2/issues/40864)_

#### Symfony 캐시 어댑터를 사용할 때 캐시 미리 로드 키에 더 이상 ID 접두사가 필요하지 않음

이제 Symfony 캐시 어댑터에 대한 미리 로드 키(preload_keys)를 캐시 id_prefix 없이 구성할 수 있습니다. 이전에는 문서화된 구성에 따라 각 키의 접두사를 포함하는 경우(예: 061_SYSTEM_DEFAULT)에 키가 미리 로드되지 않았습니다. 이제 애플리케이션이 키를 요청할 때 정확히 키를 지정할 수 있으며(예: SYSTEM_DEFAULT) Adobe Commerce에서 id_prefix를 자동으로 적용합니다.

_AC-17407 - [GitHub 문제](https://github.com/magento/magento2/issues/40877) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3a6b9667)_

#### [문제] 범주 특성에 &#39;frontend_input&#39;이 있는 경우 PHP 8.5 사용 중단 수정 ...

범주 특성에 frontend_input이 null로 설정되어 있을 때 관리 패널에서 범주를 열면 PHP 8.5에서 오류가 발생하는 문제가 해결되었습니다. 이제 카테고리 페이지가 열리고 사용 중단 오류 없이 성공적으로 편집할 수 있습니다.

_AC-17499 - [GitHub 문제](https://github.com/magento/magento2/issues/40908) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [문제] 더 이상 사용되지 않는 PHPUnit 어설션 및 테스트 스텁 구성 바꾸기

더 이상 사용되지 않는 7개의 PHPUnit 사용을 대체하여 향후 PHPUnit 업그레이드를 위해 Magento 2의 코어 유닛 테스트 세트를 업데이트했습니다. 변경 사항은 테스트 스텁에서 `isType()` 어설션 및 `with*()` 구성을 해결합니다. 이 패턴은 현재 PHPUnit 버전에서 사용 중단 알림을 트리거하고 PHPUnit 13 이상에서 제거될 예정입니다.

_AC-17750 - [GitHub 문제](https://github.com/magento/magento2/issues/41040) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/41033)_

#### GraphQL order_date 및 주석 타임스탬프가 en_US가 아닌 로케일에서 잘못된 캘린더 날짜를 반환함(IntlDateFormatter misparse) - AC-14431 수정 불완료

GraphQL 주문 날짜에 프랑스어 및 독일어 로케일에 대한 잘못된 달력 날짜가 표시되는 문제가 해결되었습니다.
이제 주문 날짜 및 관련 주석 타임스탬프가 올바른 날짜 및 시간을 반환합니다.
애플리케이션에서 GraphQL 날짜 값을 안정적으로 구문 분석할 수 있도록 날짜 형식이 개선되었습니다.
en_US 로케일에 대한 기존 동작은 변경되지 않습니다.

_AC-18084 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/d10ab92b)_

#### [문제] 금지된 @author 태그 제거

핵심 기술 지침을 엄격하게 준수하기 위해 증분 코드 유지 관리 스윕을 완료하여 여러 시스템 모듈에서 인라인 리소스 설명서 블록을 정리합니다.

_AC-8366 - [GitHub 문제](https://github.com/magento/magento2/issues/37248) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36993)_

#### [문제] `Magento_Catalog`에서 금지된 `@author` 태그 제거(2부)

Magento의 통합 코드 전달 지침에 완벽하게 부합할 수 있도록 증분 정리 패스가 실행되어 코어 상점 첫 번째 리소스 모델에서 비호환 파일 주석을 체계적으로 제거합니다.

_AC-8370 - [GitHub 문제](https://github.com/magento/magento2/issues/37247) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36988)_

#### 계층 가격 스토리지 인터페이스 삭제 버그가 모든 계층 가격을 삭제하지 않음

지정된 웹 사이트 ID를 고려하여 가격 ID 일치 논리를 업데이트하여 여러 웹 사이트에서 제품 계층 가격을 삭제해도 모든 가격이 삭제되지 않는 TierPriceStorage의 문제를 해결했습니다.

_AC-9738 - [GitHub 문제](https://github.com/magento/magento2/issues/37949) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40557)_

#### [B2B] 구매 주문이 ActiveMQ를 사용하여 판매 주문으로 자동 전환되지 않음

ActiveMQ를 STOMP 프로토콜과 함께 사용할 때 cron으로 시작된 소비자가 메시지를 처리하지 않던 문제를 수정했습니다. 그 결과 자동 승인된 구매 발주는 판매 주문으로 전환되지 않았습니다. 이제 STOMP 대기열에 대한 메시지 처리가 보다 안정적이고 DB 및 AMQP 대기열 구현과 일관됩니다.

_ACP2E-4349 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/08b91f1a) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/239464da)_

#### 구성된 AWS S3 스토리지로 내보내기 실패

이제 AWS S3 원격 스토리지가 구성되면 제품 내보내기가 올바르게 작동합니다. 이전에는 저장소 드라이버의 잘못된 경로 확인으로 인해 내보낸 파일을 S3에 쓸 수 없었습니다.

_ACP2E-4786 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d95ae6e)_

#### &#39;use_application_lock&#39; 및 &#39;file&#39; 공급자로 자동 잠금 루프에 인덱서가 중단됨

파일 잠금 공급자와 함께 인덱서 use_application_lock 설정이 활성화된 경우 리인덱싱하는 동안 인덱서가 무기한 중단되는 문제가 해결되었습니다. 색인 재지정 작업이 예상대로 완료되었습니다.

_ACP2E-5027 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec436b10)_

#### 클라우드 UI 아래에 설정된 MAGENTO_DC 변수로 성능 저하

수정 후 요청한 키가 없고 일부 환경 변수가 정의될 때마다 배포 구성이 다시 로드되지 않습니다.

_ACP2E-5094 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD] 잘못된 URL 경로가 URL 재작성 라우터에서 404 대신 HTTP 500을 반환합니다.

형식이 잘못된 상점 URL이 표준 404 Not Found 대신 HTTP 500 오류 페이지를 반환하는 문제를 해결했습니다. 이전에는 잘못된 특정 요청 경로로 인해 URL 재작성 확인 중에 확인할 수 없는 오류가 발생했습니다.

_ACP2E-5154 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4d0357d7)_

#### [CLOUD] PHP 8.5 호환성 — ComponentRegistrar::getPath() null 배열 오프셋 충돌 설정:static-content:2.4.9에서 배포(컴팩트 전략)

//@magento_import 지시문을 사용하는 모듈 LESS 파일을 컴파일할 때 PHP 8.5에서 &quot;null을 배열 오프셋으로 사용&quot; 오류가 발생하여 `setup:static-content:deploy`이(가) 실패하는 문제를 해결했습니다. 이제 정적 콘텐츠 배포가 PHP 8.5에서 성공적으로 완료됩니다.

_ACP2E-5183 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] 앵커 href 다음에 다른 특성이 있는 CMS 블록을 저장할 때 긍정 오류 &quot;잘못된 HTML 콘텐츠가 제공됨&quot;이 표시됩니다

표준 앵커 링크(예: `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`)가 포함된 CMS 컨텐츠는 cms/wysiwyg/force_valid가 활성화된 경우 더 이상 잘못된 &quot;잘못된 HTML 컨텐츠 제공됨&quot; 유효성 검사 경고 또는 저장 오류를 트리거하지 않습니다.

_ACP2E-5203 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### 프레임워크, GraphQL

#### 이후 구성에서 숫자 키를 사용하면 di.xml 배열 항목이 대체됩니다.

아키텍처 데이터 무결성을 보호하고 모듈 확장성을 향상시키기 위해 모듈 컴파일 중에 숫자 키 &quot;0&quot;을(를) 사용한 배열 구성이 자동으로 덮어쓰거나 삭제되는 DI(Dependency Injection) XML 구문 분석 엔진 내에서 핵심 버그가 해결되었습니다.

_AC-8102 - [GitHub 문제](https://github.com/magento/magento2/issues/36861) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart는 속성 코드가 model인 경우 custom_attributesV2에 오류를 발생시킵니다.

제품에 코드 모델이 있는 사용자 지정 특성이 있을 때 addProductsToCart가 내부 서버 오류를 반환하던 문제를 수정했습니다. 이제 custom_attributesV2를 통해 사용자 지정 속성을 올바르게 검색할 수 있습니다.

_AC-16987 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/809ba93c)_

#### stock_status가 IN_STOCK인 동안 GQL 수량 null

제품 GraphQL 쿼리의 수량 필드에서 사용자 지정 MSI 스톡에 재고가 있는 제품에 대해 null을 잘못 반환했습니다. 확인자가 실제 재고 수량을 가져오기 전에 cataloginventory/options/not_available_message 구성 값에 대한 응답을 게시하고 있었으며 이 구성의 XML 기본값(2 — &quot;판매할 항목이 충분하지 않음&quot;)으로 인해 명시적 관리자 재정의 없이 새 저장소에서 null이 반환되었습니다.
이제 판매 가능 수량이 해결된 후 확인이 평가됩니다. 제품에 사용 가능한 재고가 없고(saleableQty &lt;= 0) 스토어가 명시적으로 &quot;판매할 항목이 충분하지 않음&quot;으로 구성된 경우에만 null이 반환됩니다. 재고가 있는 제품은 이 구성 설정에 관계없이 항상 실제 판매 가능 수량을 반환합니다. 저장소 수준 재정의가 준수되도록 구성 읽기도 저장소 범위를 사용하도록 수정되었습니다.

_ACP2E-4840 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price는 카탈로그 가격 범위 = 웹 사이트일 때 웹 사이트 범위 가격을 무시합니다.

GraphQL의 웹 사이트 범위 번들 옵션 가격 수정: 카탈로그 가격 범위가 웹 사이트로 설정된 경우 GraphQL을 통해 번들 제품 옵션을 쿼리하면 웹 사이트 범위 가격 대신 글로벌 &quot;모든 스토어 조회수&quot; 가격이 반환되던 문제를 해결했습니다. 이제 Magento\BundleGraphQl\Model\Resolver\Links\Collection Resolver가 가격 범위를 올바르게 확인하고 요청된 스토어 범위를 기반으로 웹 사이트별 선택 가격에 참여합니다.

_ACP2E-5057 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

#### 동시 customerCart GraphQL 요청 경합 조건으로 인해 고객에 대해 생성된 중복 활성 장바구니

이제 시스템은 요청 동시성에 관계없이 고객당 하나의 활성 장바구니만 생성하도록 합니다. 이전에는 활성 장바구니가 없는 인증된 동일한 고객에 대해 두 개의 동시 customerCart GraphQL 쿼리 또는 POST /V1/carts/mine REST 요청이 발생하면 데이터베이스에서 활성 장바구니 레코드가 중복될 수 있었습니다.

_ACP2E-5077 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud] QuoteGraphQl에서 GraphQlNoSuchEntityException이 exception.log에 로그되어 무제한 로그 증가가 발생했습니다.

만료된 장바구니 ID 또는 잘못된 장바구니 ID에 대해 반환된 오류와 같은 예상 GraphQlNoSuchEntityException 오류가 var/log/exception.log에 기록되는 문제가 해결되었습니다. 처리된 이러한 오류는 일반적인 GraphQL 오류 응답으로 여전히 클라이언트에 반환되지만 더 이상 예외 로그를 채우지 않습니다.

_ACP2E-5122 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, 인벤토리/MSI

#### GraphQL: ProductStock::isProductAvailable에서 웹 사이트 ID로 전달된 스토어 ID로 인해 &#39;website ... 찾을 수 없음&#39; 오류가 발생합니다.

이전에는, 웹 사이트 ID가 필요한 곳에서 스토어 ID가 사용되기 때문에 장바구니에 항목을 추가하는 동안 제품 재고 가용성을 확인할 때 일부 스토어에서 웹 사이트를 찾을 수 없음 오류가 발생했습니다. 재고 가용성 확인이 올바른 웹 사이트 컨텍스트를 사용하도록 이 문제가 수정되어 오류가 발생하지 않습니다.

_ACP2E-5242 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, 주문

#### 배송 회사를 변경할 때 [기능 요청] 저장소 픽업 데이터의 중복 항목 지우기

매장 내 픽업에서 홈 딜리버리 방식으로 전환하면 픽업 위치와 연관된 매장 주소가 장바구니에서 제거됩니다. 주문을 하기 전에 유효한 배송 주소를 입력해야 합니다.

_ACP2E-4973 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, 제품

#### 위시리스트 값 데이터에 \&quot;model\&quot; 키 누락

GraphQL을 통해 위시리스트 세부 정보를 쿼리하면 내부 서버 오류가 반환되던 문제를 수정했습니다.
이제 위시리스트 쿼리가 &quot;위시리스트 값 데이터에 키 모델 누락&quot; 오류 없이 성공적으로 반환됩니다.

_AC-8062 - [GitHub 문제](https://github.com/magento/magento2/issues/36909) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/515d3dd3)_

### 가져오기 및 내보내기

#### [문제] 가져오기 iframe 가시성 수정

Magento 관리 패널 내에서 깔끔하고 세련된 사용자 인터페이스를 보장하기 위해 데이터 유효성 검사 중에 내부 백그라운드 실행 iframe이 저장소 관리자에게 표시되는 템플릿 레이아웃 결함을 해결했습니다

_AC-13250 - [GitHub 문제](https://github.com/magento/magento2/issues/39267) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39265)_

#### [문제] 수정: 제품 가져오기의 하드 코드 xxh128 해시 알고리즘

내부 하위 시스템을 정리하고 최신 시스템 최적화 기준을 활용하기 위해 제품 가져오기 구성 요소는 단일 영구 해시 알고리즘을 사용하도록 간소화되었습니다.

_AC-16967 - [GitHub 문제](https://github.com/magento/magento2/issues/40770) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40687)_

#### 유효성 검사 전략이 &quot;오류 시 중지&quot;로 설정된 경우 유효성 검사 오류 후 가져오기 단추를 사용할 수 있습니다.

유효성 검사 전략이 &quot;오류 시 중지&quot;로 설정되어 있을 때 데이터 유효성 검사가 실패한 후 가져오기 단추가 유효성 검사 결과에 계속 표시되는 문제를 해결했습니다. 이전에는 모든 레코드의 유효성 검사가 실패했더라도 버튼이 표시되고 클릭할 수 있으므로 가져오기 시도가 즉시 종료되었습니다.

_ACP2E-5124 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2b9e8316)_

### 설치 및 관리

#### [클라우드] 오래된 기존 ISO 하위 분류 코드 수정

ISO 3166-2 표준에 맞게 13개 국가의 지역 코드가 업데이트되었습니다. 이전에는 일부 지역 코드가 표준과 일치하지 않아 서드파티 통합 및 국제 규정 준수에 문제가 발생할 수 있었습니다. 벨기에, 콜롬비아, 스페인, 프랑스, 이탈리아, 라트비아의 새로운 지역이 추가되었다. 오스트리아, 콜롬비아, 코스타리카, 독일, 에스토니아, 스페인, 핀란드, 프랑스, 인도, 아이슬란드 및 라트비아의 지역 코드가 업데이트되었습니다.

_ACP2E-4495 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 인벤토리/MSI

#### [CLOUD] 기프트 카드 및 관련 구매 불가 WF-1688

기본이 아닌 재고/소스가 사용되고 관련(관련 또는 상향 판매 또는 교차 판매) 제품이 저장될 때 제품이 사라지지 않습니다.

_ACP2E-4741 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 번들 제품 스톡 상태 불일치

이전에는 저장소 관리자가 관리자 패널에서 번들 제품의 재고 상태를 수동으로 업데이트할 때 여러 재고 소스로 구성된 저장소의 경우 변경 사항이 상점 앞에 반영되지 않았습니다. 관리자의 변경 사항에도 불구하고 고객은 오래된 재고 상태를 계속 볼 수 있습니다.

이 문제가 수정되었습니다. 이제 관리 패널에서 수행한 번들 제품 재고 상태 변경 사항이 구성된 모든 재고 소스 및 재고 위치에 올바르게 전파되어 고객이 항상 상점에서 정확한 재고 가용성을 확인할 수 있습니다.

_ACP2E-4866 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/db712a46)_

#### GetStockIdForCurrentWebsite.php에서 throw한 NoSuchEntityException &quot;요청한 저장소를 찾을 수 없음&quot;

잘못된 ?store= 쿼리 매개 변수를 사용하여 상점 첫 페이지를 방문하면 이러한 요청마다 NoSuchEntityException이 위험 수준에서 기록되는 문제를 해결했습니다. 이전에는 MSI 스톡 데이터 플러그인이 저장소가 없는 경우를 처리하지 않고 원시 저장소 코드를 StoreManager::getStore()로 직접 전달하여 예외 로그가 복잡해졌습니다.

_ACP2E-5003 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/1bf25e46)_

### 주문

#### 범위가 frontend 또는 webapi_rest 범위인 경우 주문 관찰자 취소가 실행되지 않음

상점 첫 화면 또는 webapi_rest 범위를 통한 주문 취소를 수행하면 취소 관찰자가 제대로 실행되지 않는 문제가 해결되었습니다. 이제 주문 취소시 기프트 카드 금액이 고객의 매장 크레딧으로 복원됩니다.

_AC-16353 - [GitHub 문제](https://github.com/magento/magento2/issues/40414) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64eb754d)_

#### 제한된 사용량의 장바구니 가격 규칙은 관리자의 기존 주문을 편집할 때 적용되지 않습니다(예: &quot;고객당 사용량 = 1&quot;)

관리에서 기존 주문을 편집할 때 사용 제한이 있는 장바구니 가격 규칙 할인이 제거되던 문제를 수정했습니다. 이제 주문이 수정되면 사용 한도에 도달한 후에도 원래 할인이 유지됩니다.

_AC-16671 - [GitHub 문제](https://github.com/magento/magento2/issues/40624) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c10554e1)_

#### 번들 제품에 대한 관리 패널의 최소 수량 유효성 검사 오류

백엔드 주문 경험을 개선하고 수동 견적을 생성할 때 기능 블록을 제거하기 위해 관리 주문 생성 중에 하위 항목 매개변수가 잘못 평가되는 유효성 검사 오류가 해결되었습니다.

_AC-17193 - [GitHub 문제](https://github.com/magento/magento2/issues/40812) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40863)_

#### 프론트엔드 주문 보기에서 번들 제품 하위 항목 수량 불일치

이제 Storefront 주문 세부 사항 페이지에 각 번들 제품 옵션의 총 주문 수량이 표시됩니다. 이전에는 각 하위 옵션의 수량 열에 옵션당 총 주문 수량 대신 상위 번들의 주문 수량이 표시되었습니다.

_ACP2E-4820 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() DeadlockException 재시도 시 영구 ShipOrder/InvoiceOrder 오류 발생-

교착 상태의 경우 ShipOrder 및 InvoiceOrder 작업이 정상적으로 해결되었습니다.
교착 상태로 인해 이전 ShipOrder 및 InvoiceOrder 작업이 영구적으로 실패함

_ACP2E-4913 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/51f6d191)_

#### 송장 생성 중 상위 구성 가능 항목에 대한 잘못된 FPT/WEEE 행 레벨 계산

이제 구성 가능한 제품에 대한 송장 및 대변 메모 총계에 고정 제품 세액이 올바르게 포함됩니다. 이전에는 FPT 행 레벨 금액이 상위 구성 가능한 주문 항목으로 전파되지 않았으므로 송장 및 대변 메모 합계가 FPT 금액만큼 주문 총계보다 낮았습니다.

_ACP2E-4977 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/51f6d191)_

#### 책임자로부터 주문을 생성하는 동안 페이지 새로 고침 시 제품 수량이 수정됨

페이지를 새로 고치면 동일한 SKU가 여러 번 추가될 수 있는 문제를 해결했습니다.

_ACP2E-5046 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec436b10)_

#### 동시 비동기 이메일 cron 작업자는 동일한 주문에 대해 중복 주문 확인 이메일을 보냅니다.

동시 이메일 작업자가 동일한 주문에 대해 중복 주문 확인 이메일을 보낼 수 있는 문제를 해결했습니다.

_ACP2E-5059 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/8d70f246)_

#### [클라우드] sales_clean_quotes cron 작업 메모리가 부족합니다.

만료된 많은 견적을 지울 때 sales_clean_quotes cron 작업에 메모리가 부족하던 문제를 수정했습니다. 이전에는 처리된 모든 견적을 메모리에 유지했으며 만료된 모든 견적이 제거되기 전에 치명적인 메모리 소모 오류로 작업이 종료되었습니다.

_ACP2E-5137 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4d0357d7)_

### 주문, 프로모션

#### 고정 금액 범주 장바구니 가격 규칙은 규칙이 번들 상위와 일치할 때 일치하지 않는 동적 번들 하위를 할인합니다.

범주 조건이 있는 고정 금액 장바구니 가격 규칙이 번들 상위 항목만 일치할 때 동적 가격 번들의 모든 하위 항목에 할인을 잘못 적용하던 문제를 해결했습니다. 이전에는 대상 범주에 속하지 않는 번들 하위 항목이 0이 아닌 비례 할인 혜택을 받았습니다.

_ACP2E-5075 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2b9e8316)_

### 결제

#### config:show 명령은 최신 버전의 부분 경로에서 작동하지 않습니다.

`config:show` 명령은 이제 결제와 같은 부분 구성 경로를 수락하고 해당 경로 아래에 구성 값을 표시합니다. 이전에는 `php bin/magento config:show` 결제를 실행하면 올바른 값을 표시하는 대신 `The "payment" path doesn't exist. Verify and try again.` 오류가 반환되었습니다.

_AC-13908 - [GitHub 문제](https://github.com/magento/magento2/issues/39610) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40432)_

### 성능

#### :upgrade 설치 프로그램이 인덱서 모드를 `schedule`에서 `save`(으)로 변경하고 있어 속도가 매우 느려집니다.

bin/magento 설치:upgrade을(를) 실행하면 실수로 인덱서 모드가 &quot;일정에 따라 저장&quot;에서 &quot;저장 시 저장&quot;으로 변경되고 데이터베이스 트리거를 불필요하게 삭제하고 다시 만드는 오랜 문제가 해결되었습니다. 이로 인해 가동 중지 시간이 크게 줄어들고 큰 카탈로그에 배포하는 동안 성능 병목 현상이 발생하지 않습니다.

_AC-2423 - [GitHub 문제](https://github.com/magento/magento2/issues/33386) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40643)_

#### Valkey LAYOUT 캐시 키는 큰 제품 카탈로그에 많은 공간을 소비합니다.

이전에는 각 제품이 저장소 보기당 고유한 LAYOUT 캐시 항목을 생성함으로써 대용량 카탈로그의 Redis/Valkey에 과도한 메모리 소비를 초래했습니다. 이제 LAYOUT 캐시 항목이 동일한 유형, 속성 세트 및 스토어 뷰를 사용하는 제품 간에 공유되어 카탈로그 크기에 상관없이 캐시 증가를 좌우합니다.

_ACP2E-4908 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### 제품 쿼리의 교착 상태 오류

카테고리별로 필터링된 CatalogWidget 제품 목록이 있는 페이지의 InnoDB 교착 상태를 해결했습니다. 이 문제는 예약 모드 가격 인덱서가 동시에 실행될 때 발생했습니다.

_ACP2E-5052 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] Adobe Commerce URL 확인 쿼리 성능 저하

URL 라우팅 메타데이터(relative_url, redirect_code, type)만 요청된 경우에도 GraphQL 경로 쿼리가 항상 Page Builder 위젯 실행 및 제품 컬렉션 로드를 포함하여 전체 CMS 페이지 콘텐츠를 렌더링하는 문제를 해결했습니다. 이전에는 이로 인해 불필요한 위젯/제품 렌더링이 수행되었으며 Page Builder 위젯이 포함된 CMS 페이지에 대한 요청당 데이터베이스 쿼리가 크게 증가했습니다.

_ACP2E-5143 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/597c7211)_

#### 고객 계정 공유가 글로벌로 설정된 경우 고객 성능 탱크 관리

고객 계정 공유가 글로벌로 설정된 경우 로드 시간 및 HTTP 응답 크기가 이차적으로 증가하는 고객 편집 관리 페이지의 성능 문제를 해결했습니다.

_ACP2E-5164 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/24667df1)_

### 제품

#### &quot;가격 클릭&quot; 팝업 내에서 장바구니에 추가 버튼이 작동하지 않습니다.

제품 목록 페이지의 &quot;가격 클릭&quot; 팝업에 있는 장바구니에 추가 단추가 제품을 장바구니에 추가하지 않던 문제를 수정했습니다.
이제 팝업에서 제품을 장바구니에 추가할 수 있습니다.

_AC-11896 - [GitHub 문제](https://github.com/magento/magento2/issues/30356) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/29a7cdbe)_

#### BundleGraphQL Resolver는 별도의 지연된 제품 인스턴스를 생성하여 쿼리 일괄 처리(N+1) 제거

API 응답 처리량을 크게 가속화하고 서버 오버헤드를 최소화하기 위해 GraphQL 해상도 계층은 번들 제품에 대해 진정한 쿼리 일괄 처리를 수행하도록 최적화되어 성능 저하 N+1 데이터베이스 누수를 방지합니다.

_AC-16647 - [GitHub 문제](https://github.com/magento/magento2/issues/40595) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40867)_

#### EAV 선택 및 다중 선택 속성 유효성 검사가 값이 &quot;0&quot;인 옵션 레이블을 잘못 거부합니다.

데이터 무결성을 향상시키고 고객 및 카탈로그 양식 전체에서 예기치 않은 제출 오류를 방지하기 위해 정확한 문자열 값 &quot;0&quot;이 포함된 옵션 레이블이 EAV 핵심 프레임워크에 의해 잘못 거부된 유효성 검사 결함이 해결되었습니다

_AC-16986 - [GitHub 문제](https://github.com/magento/magento2/issues/40634) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40827)_

#### 사용자 정의 가능한 옵션 레이블 및 사용자 정의 가능한 옵션 제목은 사용자의 역할이 특정 범위로 제한된 경우 저장할 수 없습니다

특정 저장소 범위로 제한된 액세스 권한을 가진 관리자가 편집할 때 사용자 지정 가능한 옵션 레이블 및 제목이 되돌려지는 문제를 해결했습니다.
이제 업데이트된 레이블 및 제목이 선택한 범위에 대해 올바르게 저장됩니다.

_AC-2684 - [GitHub 문제](https://github.com/magento/magento2/issues/35210)_

#### 제품 경고 소비자가 스토어 범위 시스템/stmp/disable을 무시함

이제 제품 경고 소비자가 스토어 범위 시스템/stmp/disable 설정을 고려합니다.

_ACP2E-4870 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ec436b10)_

#### 프론트엔드 비교 페이지에 잘못된 간단한 설명 레이블 번역이 표시됨

이전에는 제품 비교 페이지에서 간단한 설명 과 같은 비슷한 속성 레이블을 사용하면 현재 스토어에 대한 보기 대신 다른 스토어 보기의 번역을 표시할 수 있었습니다. 이제 올바른 저장소별 번역이 표시됩니다.

_ACP2E-4929 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/08b91f1a)_

#### Page Builder 제품 캐러셀은 카테고리 위치 정렬 순서를 무시하고 대신 entity_id DESC 순서로 제품을 표시합니다.

카테고리 위치별로 정렬되도록 설정된 페이지 빌더 캐러셀에 표시된 제품이 상점 첫 화면에서 잘못된 순서로 표시되던 문제를 수정했습니다. 이제 제품이 관리 → 카탈로그 → 범주 → 제품 탭에 구성된 순서로 표시됩니다.

_ACP2E-4980 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/51f6d191)_

### 프로모션 규칙

#### 적용된 장바구니 가격 규칙 중 하나에 할인 수량 단계 값이 있는 경우 잘못된 할인 계산

여러 장바구니 가격 규칙이 적용되었으며 하나의 규칙에 할인 수량 단계(구매 X) 값이 있을 때 할인이 잘못 계산되는 문제가 해결되었습니다.
이제 모든 적격 수량에 대해 할인이 올바르게 계산됩니다.

_AC-12307 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c10554e1)_

### 반환

#### RMA - 반품 주석 추가 API - 이메일이 발신자(영업 담당자)에게는 트리거되지만 고객에게는 트리거되지 않음

반환 API를 통해 전송된 반환 댓글 이메일이 고객이 아닌 영업 담당자에게 전송되는 문제가 수정되었습니다.
이제 고객 알림이 활성화된 API를 통해 반환 댓글이 추가되면 고객이 이메일 알림을 받습니다.

_AC-1138 - [GitHub 문제](https://github.com/magento/magento2/issues/33985)_

### 판매

#### rest api V1/orders 또는 V1/orders/create 끝점에서 주문한 경우 `[Order][REST]` sales_order_items product_options 열에 데이터가 없습니다.

REST API를 통해 생성된 주문 항목에 전체 product_options 데이터가 포함되지 않던 문제를 수정했습니다. 이제 REST API를 통해 생성된 주문에 대해 사용자 지정 옵션 레이블 및 관련 옵션 세부 사항이 올바르게 저장됩니다.

_AC-15187 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8b67e8ed)_

#### 업데이트된_at 타임스탬프가 연결되어 비동기 그리드 인덱싱이 활성화된 경우 판매 주문 그리드가 부실 상태에서 영구적으로 중단됨

비동기 그리드 색인화가 활성화된 경우 판매 주문 그리드가 부실 주문 상태로 남아 있을 수 있는 문제를 해결했습니다. 이제 주문 그리드 상태가 현재 주문 상태와 일치하도록 올바르게 업데이트되며, 동일한 시간 내에 여러 주문 업데이트가 발생하는 경우도 포함됩니다.

_AC-17118 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/478f8e7c)_

### 보안

#### [문제] HTML으로 재해석된 js.phtml DOM 텍스트 업데이트

플랫폼의 보안 기준을 강화하고 악의적인 입력 실행의 위험을 최소화하기 위해 동적 DOM 업데이트를 처리하는 기본 인라인 스크립트 템플릿이 XSS(크로스 사이트 스크립팅) 주입 벡터를 제거하도록 리팩터링되었습니다.

_AC-12118 - [GitHub 문제](https://github.com/magento/magento2/issues/38821) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38804)_

### 배송

#### USPS REST API 문제, 최대 패키지 가중치에 대한 잘못된 비율

주문이 여러 패키지로 분할되는 경우 잘못된 예상 배송(예: &quot;최대 패키지 중량&quot; 이상)이 수정되었습니다. 이제 통신사가 기존 Web Tools 플로우와 일관되게 각 패키지에 대한 요금을 요청하고 금액을 합계합니다.

_ACP2E-4813 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6c67a9b5)_

### 세금

#### base_wee_tax_applied_amount가 상위 제품에 대해 설정되지 않았습니다.

이제 base_weee_tax_apply_amount 값이 하위 항목뿐만 아니라 sales_order_item, sales_invoice_item, sales_creditmemo_item과 같은 데이터베이스 테이블에서 구성 가능한 제품에 대해 채워집니다.

_ACP2E-4922 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/08b91f1a)_

### 테스트 프레임워크

#### [문제] 대/소문자를 구분하지 않는 하위 문자열 비교를 위해 GraphQL 테스트 Client.php를 업데이트합니다.

헤더에서 다른 문자 대/소문자를 사용했을 때 GraphQL API 테스트가 Set-Cookie 헤더를 인식하지 못하는 문제를 해결했습니다. 이제 테스트가 Set-Cookie, set-cookie 및 SET-COOKIE 헤더를 올바르게 처리합니다.

_AC-15337 - [GitHub 문제](https://github.com/magento/magento2/issues/39713) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c10554e1)_

#### 매우 느린 WebAPI GraphQL 기능 테스트

빌드 전달 설정을 최적화하고 CI(지속적 통합) 환경을 가속화하기 위해 외부 시스템 명령 호출에서 기본 처리 중인 메모리 처리로 캐시 지우기 동작을 전환하여 테스트 인프라 병목 현상을 해결했습니다.

_AC-15395 - [GitHub 문제](https://github.com/magento/magento2/issues/39725) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40804)_

### UI 프레임워크

#### 동일한 페이지에서 미니카트를 두 번 사용할 수 없습니다.

프론트엔드 개발자에게 더 큰 레이아웃 유연성을 제공하기 위해 여러 개의 미니카트 블록(예: 머리글에 있는 블록과 바닥글에 있는 블록)이 존재하고 단일 페이지 레이아웃에서 독립적으로 업데이트될 수 있도록 하는 오랜 코어 UI 제한이 해결되었습니다.

_AC-12579 - [GitHub 문제](https://github.com/magento/magento2/issues/38958) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [문제] 수정(pagecache): PATCH을 Varnish VCL에서 유효한 HTTP 메서드로 인식합니다.

Magento의 기본 Varnish VCL은 이제 PATCH을 유효한 HTTP 방법으로 인식하므로 REST API 부분 업데이트 요청(예: PATCH /rest/V1/products/:sku)이 파이프되지 않고 백엔드로 전달됩니다. 이렇게 하면 전체 페이지 캐시가 Vannish로 설정된 경우 PATCH 호출이 실패하거나 잘못 실행되는 것이 수정됩니다.

_AC-16954 - [GitHub 문제](https://github.com/magento/magento2/issues/40757) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40657)_

#### [문제] VCL에서 모든 gad_* 매개 변수 바꾸기

동적 광고 캠페인으로 인한 성능 저하를 방지하기 위해 애플리케이션의 캐싱 계층을 업데이트하여 모든 Google Ads gad_* 쿼리 문자열을 미리 무시합니다. 이렇게 하면 외부 캠페인 링크가 페이지 캐시를 무효화하고 대상 페이지를 느리게 할 수 없습니다

_AC-16980 - [GitHub 문제](https://github.com/magento/magento2/issues/40781) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40780)_

#### [문제] 수정: bootstrap에서 최소 PHP 버전 검사를 8.3으로 업데이트

혼란스러운 런타임 오류를 방지하고 개발자 설치 문제 해결을 개선하기 위해 시스템 부트스트랩 프레임워크 내의 기본 PHP 환경 유효성 검사기를 애플리케이션의 실제 핵심 요구 사항에 맞게 도입했습니다.

_AC-17312 - [GitHub 문제](https://github.com/magento/magento2/issues/40851) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40686)_

#### `igbinary`이(가) 설치되고 기본 파일 캐시가 사용되면 `health_check.php`에서 500을 반환합니다(Varnish 503).

igbinary가 기본 파일 캐시 백엔드와 함께 설치되었을 때 health_check.php가 HTTP 500을 반환하는 문제를 해결했습니다. 상태 검사가 명시적 백엔드 키 없이 유효한 캐시 구성을 허용하여 Varnish가 백엔드를 비정상으로 표시하고 HTTP 503을 반환하지 못하도록 합니다.

_AC-17400 - [GitHub 문제](https://github.com/magento/magento2/issues/40876) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [문제] 수정: gzip 형식을 업데이트하고 nginx 구성에서 IE6 해결 방법을 제거하십시오.

페이지 로드 속도를 개선하고 네트워크 자산 전달을 최적화하기 위해 폴백 서버 구성을 현대화하여 최신 Storefront 구성 요소를 더 잘 지원하고 레거시 기술 오버헤드를 제거했습니다

_AC-17498 - [GitHub 문제](https://github.com/magento/magento2/issues/40774) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40681)_

#### [문제] 불안정한 graphql OrderStatusChangeDateTest를 수정하려고 합니다.

CI(지속적 통합) 안정성을 개선하고 긍정 오류 빌드 오류를 줄이기 위해 WebAPI 기능 테스트 세트에서 경합 조건이 해결되었습니다. 이전에 GraphQL 주문 상태 유효성 검사 테스트(OrderStatusChangeDateTest)에서는 PHP 메모리와 MySQL 타임스탬프 간의 미묘한 타이밍 차이로 인해 간헐적인 오류가 발생했습니다

_AC-17959 - [GitHub 문제](https://github.com/magento/magento2/issues/41126) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40618)_
