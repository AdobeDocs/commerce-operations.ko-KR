---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '24355'
ht-degree: 0%

---
# Magento Open Source 수정 문제(v2.4.9-beta1)

## v2.4.9-beta1의 문제가 해결되었습니다.

Magento Open Source 2.4.9-베타1 코어 코드에서 501개의 문제를 해결했습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

#### ApplySpecialPrice에서 현재까지 특별 가격이 잘못 검증되었습니다.

시스템은 특별 가격에 대해 잘 작동하며 제품 특별 가격은 관리자가 설정한 날짜 또는 REST API에 의해 서드파티 시스템에서 설정한 날짜에 만료됩니다

_AC-13130 - [GitHub 문제](https://github.com/magento/magento2/issues/39169) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39690)_

#### WebAPI Paradox를 통해 [WebAPI] 고객 이메일 확인

확인 전에 토큰이 필요한 인증 역설로 인해 고객이 WebAPI를 통해 계정을 활성화할 수 없는 문제를 해결했습니다. 업데이트를 통해 확인되지 않은 고객이 API를 통해 계정을 성공적으로 활성화할 수 있으므로 일관되고 기능적인 확인 흐름이 보장됩니다.

_AC-13281 - [GitHub 문제](https://github.com/magento/magento2/issues/39255) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 결제 정보만 있는 REST API를 통해 주문을 만들 때 관리 대시보드에 청구 주소 누락 오류 발생

청구 주소 없이 API를 통해 주문을 만들 수 있어 관리자 대시보드 충돌이 발생하는 문제를 해결했습니다.
이제 청구 주소가 없는 주문은 제한되며 더 이상 생성되지 않습니다.

_AC-14049 - [GitHub 문제](https://github.com/magento/magento2/issues/39651) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Rest API의 장바구니에 제품 추가 문제

특정 웹 사이트에 할당되지 않은 제품을 장바구니에 추가하고 구매할 수 있는 문제가 수정되었습니다.
이제 오류 메시지가 표시됩니다. &quot;추가하려는 제품을 사용할 수 없습니다.&quot;

_AC-15054 - [GitHub 문제](https://github.com/magento/magento2/issues/40029) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f5cc09fc)_

#### 저장소 레이블을 업데이트할 때 속성 옵션 레이블을 덮어씁니다.

REST API를 통해 다중 선택 제품 속성을 업데이트하면 모든 store_labels를 덮어쓰게 되어 기존 스토어 특정 레이블이 제거되는 문제를 해결했습니다.
이제 기본 스토어 보기 레이블을 업데이트할 때 Magento은 제공된 레이블을 완전히 덮어쓰는 대신 기존 레이블과 병합합니다.
이렇게 하면 업데이트 후 다른 스토어 보기에 대한 스토어 특정 레이블이 그대로 유지됩니다.

_AC-15208 - [GitHub 문제](https://github.com/magento/magento2/issues/40093) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [문제] 명확한 특성 옵션이 이미 있습니다.

이제 시스템에서 &quot;동일한 파일 이름이 이미 있는 경우 새 파일 이름 가져오기&quot;라는 어색한 구문을 &quot;새 파일 이름이 이미 있는 경우 새 파일 이름 가져오기&quot;라는 보다 명확하고 문법적으로 올바른 버전으로 대체했습니다. 이는 가독성과 사용자 이해를 향상시킵니다.
속성 옵션 응답에 대해서도 동일합니다.

_AC-15473 - [GitHub 문제](https://github.com/magento/magento2/issues/39943) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39941)_

#### /V1/products/special-price API Endpoint에 내부 서버 오류가 있습니다.

Null TypeError로 인해 /V1/products/special-price 및 관련 가격 책정 API에 대한 잘못된 요청이 500 내부 서버 오류를 반환하는 문제를 해결했습니다.
이제 API가 입력을 올바르게 확인하고 잘못된 페이로드에 대해 400 오류를 반환하여 오류 처리 및 API 안정성이 향상됩니다.

_AC-6419 - [GitHub 문제](https://github.com/magento/magento2/issues/35934) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a7ef6300)_

#### `/V1/order/{orderId}/ship` API 끝점에 내부 서버 오류

이제 시스템에서 `/V1/order/{orderId}/ship` API 끝점의 내부 서버 오류를 수정하고 요청이 잘못된 경우 400 오류를 반환합니다.

_AC-6420 - [GitHub 문제](https://github.com/magento/magento2/issues/35931) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38282)_

#### /V1/creditmemo API 끝점에 내부 서버 오류

/V1/creditmemo API에 대한 잘못된 요청 형식이 500 내부 서버 오류를 반환하는 문제를 해결했습니다.
이제 API가 요청을 제대로 확인하고 잘못된 페이로드에 대해 400 오류를 반환하여 오류 처리 및 안정성이 향상됩니다.

_AC-6422 - [GitHub 문제](https://github.com/magento/magento2/issues/35924) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a7ef6300)_

#### Rest API 및 Magento 백엔드는 새 속성을 만들 때 attribute_code에 대해 다른 유효성 검사 메서드를 사용합니다

Magento 관리자가 attribute_code에 대문자를 허용했지만 REST API가 제품 속성을 만드는 동안 대문자를 거부하는 불일치를 수정했습니다.
이제 Admin과 REST API 모두 동일한 유효성 검사를 따르므로 대문자로 특성을 성공적으로 만들 수 있습니다.

_AC-6660 - [GitHub 문제](https://github.com/magento/magento2/issues/33138) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### REST API를 통한 속성 생성과 업데이트 간의 다른 유효성 검사

REST API를 통해 특성을 만드는 동안 일관성 없는 유효성 검사가 발생하여 잘못된 backend_type이 지정되는 문제가 해결되었습니다.
이제 유효한 경우 시스템이 올바른 백엔드 유형을 설정하고, 잘못된 값에 대해 예외를 throw하거나, 제공되지 않은 경우 적절하게 폴백하여 일관된 속성 동작이 보장됩니다.

_AC-6885 - [GitHub 문제](https://github.com/magento/magento2/issues/36327) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64823f95)_

#### 잘못된 요청 본문 또는 매개 변수로 인해 &quot;내부 서버 오류&quot;가 발생했습니다.

잘못된 형식의 요청 본문 또는 매개 변수가 이제 명확한 &quot;400 잘못된 요청&quot; 응답을 반환합니다.
이전에는 잘못된 형식의 요청 본문이나 매개 변수를 다양한 REST API 끝점(예: /V1/carts/search, /V1/orders, /V1/products 등)으로 보내면 일반적인 &quot;내부 서버 오류&quot;(500)가 발생하여 입력 문제를 진단하기 어려웠습니다.
이제 Adobe Commerce은 &quot;400 잘못된 요청&quot; 응답을 반환하여 요청이 유효하지 않을 때 더 명확한 피드백을 제공합니다.

_AC-746 - [GitHub 문제](https://github.com/magento/magento2/issues/32784) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders`(또는 `/orders/:id`) 끝점에 &quot;state&quot; 및 &quot;status&quot; 필드가 없습니다.

데이터베이스 값이 null일 때 `/orders` 및 `/orders/{id}` API 응답이 상태 및 상태 필드를 생략하는 문제가 해결되었습니다.
이제 두 필드 모두 응답에서 일관되게 반환되므로 API 설명서 준수를 보장하고 데이터 안정성을 향상시킬 수 있습니다.

_AC-9244 - [GitHub 문제](https://github.com/magento/magento2/issues/37807) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/01cee3c3)_

#### 비동기 대량 작업은 async.magento.configurableproduct.api.optionrepositoryinterface.save.post에 대해 열린 상태로 유지됩니다.

이제 요청 본문이 배열이 아닌 경우 벌크 API 엔드포인트에서 오류가 발생하므로 벌크 항목 키가 0부터 시작하는 연속된 숫자여야 합니다. 이전에는 벌크 요청에서 임의의 항목 키가 제출되어 벌크 항목 상태가 업데이트되지 않았습니다.

_ACP2E-3544 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### searchCriteria를 사용하여 현재 스토어에서 고려하지 않는 is_subscribed 값의 [CLOUD] API REST 버그

API REST 고객 쿼리는 searchCriteria를 사용하여 올바른 저장소에서 올바른 &quot;is_subscribed&quot; 값을 가져옵니다.
이전에는 API REST 고객 쿼리가 is_subscribed&quot; 값을 가져올 때 저장을 고려하지 않았습니다.

_ACP2E-3621 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all은 1개의 SKU에 대해 여러 항목을 만들 수 있습니다.

이제 데이터 불일치 또는 제품 중복을 초래할 수 있는 경합 조건을 방지하기 위해 동일한 제품을 저장하고 업데이트하는 동시 요청이 일련화됩니다

_ACP2E-3744 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

#### 주문 &quot;base_row_total&quot; 및 &quot;row_total&quot;은 REST API 응답에서 단일 품목 가격을 보여줍니다.

이제 동일한 여러 항목이 주문된 경우 주문 세부 사항에 대한 REST API 응답에 &quot;base_row_total&quot; 및 &quot;row_total&quot; 속성에 대한 올바른 값이 포함됩니다

_ACP2E-3874 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API 끝점 export-stock-salable-qty가 잘못된 항목 total_count를 반환합니다.

total_count가 페이지 크기로 잘못 제한된 재고 내보내기 재고 예약 가능 수량 API의 페이지 매김 문제가 수정되었습니다. 이전에는 page_size=5와 같은 페이지 매김 매개 변수와 함께 /rest/all/V1/inventory/export-stock-salable-qty/website/base 끝점을 사용할 때 응답의 total_count 필드는 검색 기준과 일치하는 실제 총 제품 수 대신 5를 반환합니다. 이 수정 후 total_count 필드는 이제 page_size 매개 변수에 상관없이 사용 가능한 총 제품 수를 올바르게 반영하므로 모든 Magento REST API 엔드포인트에서 일관된 페이지 매김 동작이 보장됩니다.

_ACP2E-4086 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

#### 장바구니 항목 REST API의 사용자 지정 옵션 ID에 대한 유효성 검사 문제.

REST API V1/guest-carts/&lt;cartId>/items/ 및 V1/carts/mine/items/ 이제 &quot;product_options.extension_attributes.custom_options를 확인합니다.*.option_id&quot;를 사용하여 장바구니 항목 SKU에 대한 유효한 option_id를 참조하는지 확인합니다. 이전에는 이 매개 변수가 유효성 검사 없이 처리되어 데이터베이스에 저장되었습니다.

_ACP2E-4138 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 장바구니에서 제품을 가져오고 스토어 헤더 언어를 변경하는 동안 변경되지 않음

이제 GraphQL customerCart 쿼리는 스토어 헤더 값에 따라 제품 속성 값을 반환합니다. 이전에는 GraphQL을 통해 장바구니에서 제품을 검색하는 동안 스토어 헤더 언어를 변경해도 업데이트된 언어가 반영되지 않아 현지화 기능이 일관되지 않았습니다.

_ACP2E-4227 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6e134409)_

#### 기프트 카드 제품에 대한 REST API/미디어 끝점이 실패함 - &quot;제품을 저장할 수 없습니다.&quot;를 반환합니다.

수정 전에는 글로벌 범위에 금액이 포함되지 않은 기프트 카드 제품을 만들 수 있었습니다. 이 수정과 함께 글로벌 범위의 금액을 확인하는 유효성 검사가 추가되었습니다.

_ACP2E-4395 - [GitHub 문제](https://mcstaging.panini.it/shp_ita_it/)_

### API, 카트 및 체크아웃

#### 배송 정보의 경우 REST API를 사용하여 서버측 유효성 검사가 작동하지 않음

배송 주소 정보 유효성 검사가 관리 백엔드에 정의된 특성 구성을 준수하지 않는 REST API 문제를 해결했습니다. 이제 유효성 검사가 구성된 설정을 올바르게 따릅니다.

_ACP2E-4156 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

### API, 카탈로그

#### 기본 웹 사이트/스토어가 계층 가격 API 엔드포인트를 삭제합니다.

이전에는 기본 기본 웹 사이트를 삭제하고 보조 웹 사이트를 기본 웹 사이트로 사용하면 보조 웹 사이트의 계층 가격을 업데이트하려고 할 때 오류가 발생했습니다. 그러나 이 수정 사항을 적용한 후 기본 웹 사이트가 삭제되거나 비활성화되더라도 계층 가격을 성공적으로 업데이트할 수 있습니다.

_ACP2E-4334 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

### API, 프레임워크

#### 응용 프로그램 서버에서 RedisRequestLogger\RedisClient(속도 제한) 예외

수정 후에는 PHP redis 확장이 설치된 경우 GraphQL 애플리케이션 서버와 함께 속도 제한 기능을 사용할 수 있습니다.

_ACP2E-4237 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

### API, 가져오기/내보내기

#### 비동기 송장 환불 API는 온라인 환불 대신 오프라인 환불을 생성합니다.

`is_online` 매개 변수를 사용한 환불 요청이 올바르게 처리되지 않는 비동기 환불 작업을 수정했습니다.

_ACP2E-4394 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

### API, 순서

#### [CLOUD] 주문 정보의 행 합계 표시 관련 주문 정보 000075568

항목이 완전히 할인된 경우 주문 API 응답의 row_total_incl_tax 값이 0.00 대신 거의 0에 가까운 잔차 값으로 반환되는 문제를 해결했습니다.

_ACP2E-3950 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 계정

#### [문제] 카탈로그 위젯 템플릿 옵션의 오타 수정

이제 시스템에서 카탈로그 위젯 템플릿 옵션의 오타가 수정됩니다.

_AC-11576 - [GitHub 문제](https://github.com/magento/magento2/issues/38185) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38178)_

#### [문제] 백 엔드 그리드에서 불필요한 간격을 제거했습니다.

이제 선택한 항목이 있을 때 백엔드 격자에서 불필요한 간격이 제거됩니다

_AC-11579 - [GitHub 문제](https://github.com/magento/magento2/issues/38502) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32622)_

#### 저장된 고객 그룹 코드가 멀티바이트 문자를 사용할 때 입력과 일치하지 않습니다.

멀티바이트 문자를 사용하는 고객 그룹 코드가 잘리고 입력한 값과 일치하지 않는 문제를 해결했습니다. 이 업데이트를 통해 전체 입력이 올바로 저장되므로 멀티바이트 이름을 사용하는 고객 그룹을 정확하게 만들 수 있습니다.

_AC-13335 - [GitHub 문제](https://github.com/magento/magento2/issues/39342) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a06a4a57)_

#### 관리자 패널에서 고객 이메일을 ö 및 .swiss 도메인으로 업데이트할 때 문제 발생

이제 관리 패널에서 특수 문자 및 .swiss 도메인이 포함된 고객 이메일을 승인할 수 있습니다.
이전에는 고객 이메일을 max@möstermann.swiss와 같은 주소로 업데이트하지 못했으며, 잘못된 호스트 이름 및 TLD에 대한 오류가 발생했습니다.
AC-13409

_AC-13409 - [GitHub 문제](https://github.com/magento/magento2/issues/39394) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/d3ea191d)_

#### 웹 사이트/스토어별로 뉴스레터 구독 활성화 스위치가 작동하지 않음

시스템은 글로벌 수준에서 비활성화되었을 때 여러 웹 사이트/스토어 뷰가 있을 때 뉴스레터를 사용하여 구독을 올바르게 처리합니다

_AC-14283 - [GitHub 문제](https://github.com/magento/magento2/issues/39751) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39752)_

#### [문제]에서 전자 메일 공개를 제거함

이제 고객의 존재 여부와 관계없이, 계정 확인에 입력된 이메일이 필요하지 않은 경우 시스템에 잘못된 이메일을 나타내는 오류 메시지가 표시됩니다.

_AC-14561 - [GitHub 문제](https://github.com/magento/magento2/issues/39574) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39570)_

#### `updateProductsInWishlist` GraphQL 돌연변이를 통해 위시리스트 항목 주석을 지울 수 없습니다.

위시리스트 댓글이 GraphQL 돌연변이를 통해 업데이트되지 않았던 문제를 수정했습니다.
이제 주석이 올바르게 업데이트되고 API 응답과 상점 첫 화면 모두에 반영됩니다.

_AC-14682 - [GitHub 문제](https://github.com/magento/magento2/issues/39911) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 모바일에서 제거된 제품은 다시 로그인할 때까지 웹의 미니 비교 섹션에 계속 표시됩니다.

이제 시스템은 미니 비교 섹션을 포함하여 모바일과 웹 모두에서 모든 비교 보기에서 제품이 즉시 사라지도록 제거합니다.

_AC-14703 - [GitHub 문제](https://github.com/magento/magento2/issues/39905) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40023)_

#### 아니요로 설정할 때 무시된 접두어/접미어 표시 설정

구성에서 고객 이름 접두사/접미사가 비활성화된 경우에도 주문에 계속 표시되는 문제를 해결했습니다.
이제 구성 설정에 따라 접두사/접미사 값이 주문 세부 사항에서 제거됩니다.

_AC-15074 - [GitHub 문제](https://github.com/magento/magento2/issues/40036) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront 고객 계정 등록: 다른 도메인 포맷으로 전환되는 이메일 주소 포맷

이 버그는 도메인(예: òbe.com)에 특수 문자가 있는 고객 이메일이 punycode 형식(tec55241@xn--adbe-mqa.com)으로 자동 변환되는 문제를 해결했습니다.
Magento 2.4.9-alpha3에서는 이러한 이메일 ID가 변경되지 않고 유효하게 유지되므로 게재 오류가 발생하지 않습니다.

_AC-15177 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 등록 양식에 유효성 검사 메시지(mage-error) 누락

고객 계정 만들기 페이지의 필수 필드에 비워 둘 때 유효성 검사 메시지가 표시되지 않던 문제를 수정했습니다.
이제 모든 비어 있거나 잘못된 필드에 적절한 오류 메시지가 표시됩니다.

_AC-15185 - [GitHub 문제](https://github.com/magento/magento2/issues/40076) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 주문 취소 양식 제목에 번역 누락

이제 시스템에서 상점 첫 화면의 주문 취소 모달에서 누락된 번역을 수정합니다. 고객이 내 계정 > 내 주문 페이지에서 &quot;취소&quot; 버튼을 클릭하면 취소 사유를 묻는 모달이 표시됩니다. 그러나 양식 제목은 이전에 하드코딩되어 번역할 수 없었습니다. 이렇게 하면 모달 제목이 적절한 번역 방법을 사용하도록 할 수 있습니다.

_AC-15260 - [GitHub 문제](https://github.com/magento/magento2/issues/40098) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40100)_

#### magento 2.4.8-p1에서 로그인 후 문제

로그인 후 홈페이지에서 &quot;계정 만들기&quot; 링크가 여전히 표시되는 Magento 2.4.8-p1 문제를 수정했습니다.
이제 링크가 다른 페이지와 일관되게 로그인 후 올바르게 숨겨집니다.

_AC-15292 - [GitHub 문제](https://github.com/magento/magento2/issues/40120)_

#### 고객을 삭제하기 전에 [문제] isSecureArea 설정

이제 시스템이 정상적으로 작동하며 이 PR은 삭제 프로세스에 대해 isSecureArea를 설정하며 고객은 다시 등록할 수 있습니다.

_AC-15723 - [GitHub 문제](https://github.com/magento/magento2/issues/40211) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38462)_

#### [클라우드] 고객 계정을 만드는 동안 현재 영역 오류로 인해 삭제 작업을 사용할 수 없습니다.

잘못된 주소로 고객을 저장한 후 수정 사항이 관련되지 않은 &quot;현재 영역에 대해 삭제 작업이 금지됨&quot; 대신 무효화 이유를 설명하는 메시지를 반환합니다.

_ACP2E-3791 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6ea61121)_

#### &#39;eav&#39; 캐시가 비활성화되면 로그인한 고객에 대해 [B2B] Webapi 요청이 무한 루프로 이동합니다.

수정 후 eav 캐시를 비활성화하면 특정 REST 요청 중에 무한 루프가 발생하지 않습니다.

_ACP2E-4191 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 일부 로케일을 로드하는 중 오류

아랍어 로케일을 사용할 때 고객 계정을 만들지 못하고 생년월일 속성이 상점 정면에 표시되도록 설정된 문제가 수정되었습니다. 이제 이 구성에서 계정을 성공적으로 만들 수 있습니다.

_ACP2E-4311 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2687b487)_

#### 오류 계정 정보를 업데이트할 때 잘못된 날짜

이제 고객은 아랍어 로케일을 사용할 때 계정을 성공적으로 업데이트할 수 있습니다. 이전에는 계정 정보를 저장하려고 했지만 잘못된 날짜 오류로 인해 생년월일이 실패했습니다.

_ACP2E-4344 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

### 계정, 관리자 UI

#### [클라우드] cartId가 있는 해당 엔터티가 없습니다.

동일한 세션에서 두 개의 회사 관리자 계정을 사용하여 고객으로 로그인을 사용할 때 &quot;cartId가 있는 해당 엔티티 없음&quot; 오류가 발생하는 문제가 해결되었습니다.

_ACP2E-4137 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

#### 고객 생성 양식 오류 메시지는 번역되지 않습니다.

고객 유효성 검사 오류 메시지가 서로 다른 인터페이스에서 제대로 번역되고 포맷되지 않던 문제를 수정했습니다. 이제 유효성 검사 오류에 상점, adminhtml, rest api 및 graphql과 같은 애플리케이션의 모든 영역에 올바르게 번역된 메시지가 표시됩니다.

_ACP2E-4354 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

### 관리자 UI

#### 이름으로 정렬할 때 카테고리 제품 그리드 > 상태 및 가시성 열이 비어 있음

제품 이름별로 정렬할 때 카테고리 제품 그리드에서 상태 및 가시성 열이 비어 있는 것으로 표시되는 문제를 해결했습니다.
이제 정렬한 후 격자에 모든 열 데이터가 올바르게 표시되므로 관리 패널에서 정확한 제품 정보를 확인할 수 있습니다.

_AC-10659 - [GitHub 문제](https://github.com/magento/magento2/issues/38233) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3cf1a106)_

#### 이메일 템플릿 store-switcher

사용되지 않는 jQuery 코드로 인해 클릭 시 뉴스레터 이메일 템플릿 미리 보기의 스토어 전환기가 열리지 않는 문제가 수정되었습니다. 로드 이벤트를 업데이트하면 적절한 기능이 복원되어 사용자가 예상대로 스토어 전환기에 액세스할 수 있습니다.

_AC-12334 - [GitHub 문제](https://github.com/magento/magento2/issues/38892) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### 장바구니 페이지와 제품 페이지의 FPT 값은 간단한 제품에 대한 동일한 구성에 대해 다릅니다

이제 FPT 값이 간단한 제품의 장바구니와 제품 페이지 간에 일관됩니다.
이전에는 고정 제품 세금(FPT) 값이 동일한 구성이 적용되는 경우에도 장바구니와 제품 페이지 간에 소수점 이하 자리 수가 다를 수 있었습니다.
AC-13066

_AC-13066 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### [견본] 모듈을 비활성화하면 다중 선택/선택 속성 옵션을 저장할 수 없습니다.

이제 [견본] 모듈이 비활성화되면 다중 선택/선택 속성 옵션을 저장할 수 있습니다.
이전에는 견본 모듈을 비활성화하면 새 다중 선택/선택 속성 옵션을 만들 때 예외가 발생했습니다.
AC-13071

_AC-13071 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### 장바구니 페이지와 제품 페이지의 FPT 값이 동적 제품에 대한 동일한 구성에 대해 다릅니다

이제 동적 제품에 대한 장바구니와 제품 페이지 간에 FPT 값이 일관됩니다.
이전에는 FPT(고정 제품 세금) 값이 동일한 구성에 대해 장바구니와 제품 페이지 간에 소수점 이하 자리 수가 다를 수 있었습니다.
AC-13075

_AC-13075 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### 날짜 ui 구성 요소에서 날짜 형식이 적용되지 않음

날짜 UI 구성 요소가 구성된 형식을 무시하고 잘못된 값을 표시하던 문제를 해결했습니다. 이 수정은 이제 날짜 필드가 표시 및 입력 모두에 대해 지정된 형식(예: Y-m-d)을 준수하도록 합니다.

_AC-13174 - [GitHub 문제](https://github.com/magento/magento2/issues/39218) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### 소스를 삭제하는 데 사용할 수 있는 옵션 없음

관리자가 활성화 또는 비활성화만 하는 대신 추가 소스를 제거할 수 있도록 관리자 UI에 인벤토리 소스에 대한 삭제 옵션을 추가했습니다. 이러한 향상된 기능은 사용되지 않는 소스에 대한 제어 기능을 향상시켜 인벤토리 관리를 향상시킵니다.

_AC-13354 - [GitHub 문제](https://github.com/magento/magento2/issues/32362) - [GitHub 코드 기여](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### 관리자의 범주 트리는 수준 3에서 선택한 모든 중첩된 범주를 표시하도록 확장되지 않습니다.

관리자 범주 트리가 수준 3 이상의 선택한 중첩 범주를 표시하도록 확장되지 않았던 문제를 해결했습니다. 수정 후에는 선택한 모든 카테고리가 자동으로 확장되어 카테고리 관련 조건 전반에서 가시성과 유용성이 향상됩니다.

_AC-13363 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### [문제] 역할 트리로 사용자 경험 개선

이 끌어오기 요청에는 모두 축소, 모두 확장 및 선택한 항목으로 분기 확장을 위한 버튼이 추가됩니다. 이 기능은 범주 트리(카탈로그 -> 재고 -> 범주)에서 제공하는 기능과 유사합니다.

_AC-14020 - [GitHub 문제](https://github.com/magento/magento2/issues/39654) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36511)_

#### 가져오기/내보내기 작업 로그는 시스템 > 작업 로그 > 보고서 그리드에서 만들어지지 않습니다

가져오기/내보내기 관리 작업에 대한 로깅을 구현하여 이제 시스템 > 작업 로그 > 보고서에 표시됩니다. 이렇게 하면 이전에 누락된 가져오기 활동을 기록하여 감사 추적을 개선할 수 있습니다.

_AC-14266 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot; 헤더는 &quot;Symfony\Component\Mime\Header\MailboxHeader&quot;의 인스턴스여야 합니다(got &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

이제 사용자 지정 반환 경로 주소가 SMTP에 대해 구성된 경우 Adobe Commerce에서 등록 이메일을 성공적으로 보냅니다. 이전에는 vanilla Adobe Commerce 2.4.8에서 system/smtp/set_return_path가 2로 설정되고 system/smtp/return_path_email이 사용자 지정 주소로 설정되면 고객 등록이 완료되었지만 등록 이메일이 전송되지 않았고 Adobe Commerce에서 이 오류가 기록되었습니다. Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot; 헤더가 &quot;Symfony\Component\Mime\Header\MailboxHeader&quot;의 인스턴스여야 합니다(&quot;Symfony\Component\Mime\Header\MailboxListHeader&quot; 수신).

_AC-14520 - [GitHub 문제](https://github.com/magento/magento2/issues/39823) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1e14bd72) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1514117f)_

#### 새로 고침 순서가 최신 사용자 지정 특성 데이터를 가져오지 않음

주문 페이지를 새로 고치면 최신 고객 사용자 지정 속성 데이터가 표시되지 않는 문제가 해결되었습니다. 문제 해결 후 업데이트된 속성 값이 이제 주문을 취소하고 다시 만들 필요 없이 반영됩니다.

_AC-14690 - [GitHub 문제](https://github.com/magento/magento2/issues/30301)_

#### [문제] 더 이상 사용되지 않는 이스케이프 장치를 바꿉니다.

더 이상 사용되지 않는 getEscaper()를 제거하고 생성자 삽입을 통해 추가했습니다.

_AC-15132 - [GitHub 문제](https://github.com/magento/magento2/issues/40062) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38135)_

#### 모바일 보기의 제품 범주와 겹치는 환영 메시지

모바일 보기에서 시작 이름이 제품 범주와 겹쳐서 클릭이 차단되는 UI 문제가 해결되었습니다.
이제 카테고리가 중복 문제 없이 완전히 표시되고 클릭할 수 있습니다.

_AC-15166 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Ui 양식 재설정 버튼이 예상대로 작동하지 않음

이제 전체 페이지를 다시 로드하지 않고 재설정 단추를 클릭하면 양식 데이터가 재설정되므로 시스템이 잘 작동합니다.

_AC-15204 - [GitHub 문제](https://github.com/magento/magento2/issues/40092) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40094)_

#### [문제] PageCache/AccessList: CIDR 지원 추가

이제 시스템에서 네트워크 내의 제거 요청을 수락하므로 CIDR 범위를 더 쉽게 제공할 수 있습니다.

_AC-15804 - [GitHub 문제](https://github.com/magento/magento2/issues/39953) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37809)_

#### [문제] 캐시 관리 단추에 설명 제목 추가

이제 시스템에서는 커서를 이동할 때 캐시 관리 버튼에 설명 제목을 추가합니다

_AC-16212 - [GitHub 문제](https://github.com/magento/magento2/issues/38607) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38598)_

#### 그리드를 사용하여 세율을 일괄 삭제하는 기능을 제공합니다

이제 관리 사용자는 관리 세율 그리드에서 여러 세율을 동시에 삭제할 수 있습니다.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub 문제](https://github.com/magento/magento2/issues/33399) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33484) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 관리자의 정적 그리드에 호버 색상이 적용되지 않음

이제 마우스로 가리키면 표시되는 색상이 관리자 정적 그리드의 행에 예상대로 적용됩니다.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub 문제](https://github.com/magento/magento2/issues/35358) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35384)_

#### Google reCAPTCHA 관리 패널의 exception.log에서 &quot;reCAPTCHA 매개 변수를 해결할 수 없음&quot; 항목

Google V3 reCAPTCHA 관리자 로그인에 대한 `var/log/exception.log` 파일의 reCaptcha 오류가 해결되었으며 오류 메시지가 기록되지 않습니다. 이전에는 관리 사용자가 **구성** > **보안** > **Google reCAPTCHA 관리 패널** 설정을 구성할 때 몇 초마다 다음 오류가 발생했습니다. `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub 문제](https://github.com/magento/magento2/issues/34975) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub 코드 기여](https://github.com/magento/security-package/commit/804dbc2a)_

#### 조건 SKU가 있는 장바구니 가격 규칙은 SKU의 &quot;선행 0&quot;을 고려하지 않습니다(sku: 01234은 1234와 동일).

이제 시스템은 SKU의 &quot;선행 0&quot;을 고려하여 조건 SKU를 사용하여 장바구니 가격 규칙을 올바르게 처리합니다

_AC-9428 - [GitHub 문제](https://github.com/magento/magento2/issues/37919) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39525)_

#### 다중 선택을 위한 기본 속성 옵션 값 동작 문제

이전에는 여러 옵션 속성에 대한 고정 기본값이 제대로 저장되지 않았습니다. 이제 수정 후 값이 데이터베이스에 제대로 저장됩니다.

_ACP2E-3523 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 관리자의 제품 수량을 장바구니로 다시 이동하는 동안 문제가 발생했습니다.

관리자에서 주문을 생성할 때 사이드바의 고객 장바구니 내 제품은 주문에 추가되어도 사라지지 않습니다.

_ACP2E-3563 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [스테이징2] 저장된 카드가 관리 패널에 표시되지 않습니다.

업그레이드 후 &quot;저장된 카드&quot; 결제 옵션이 백엔드 주문 배치 양식에 더 이상 표시되지 않던 문제를 수정했습니다.

_ACP2E-3830 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 제한된 관리자는 저장소별 권한에도 불구하고 기본 구성을 저장/업데이트할 수 있습니다.

제한된 관리자가 특정 웹 사이트 범위에만 할당되었지만 &quot;기본 구성&quot; 범위를 보고 업데이트하려고 하여 혼동을 일으킬 수 있는 문제를 해결했습니다.

_ACP2E-4011 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 모든 스토어 보기 범위에 대해 DB에 구성 가능한 제품 가격이 저장되므로, 저장된 가격이 프론트엔드와 관련이 없는 카테고리 정렬 기능의 문제가 발생합니다.

웹 사이트별로 가격이 구성되고 관리 UI 구성 가능한 제품 편집 페이지에서 스토어 보기가 선택된 경우 구성 가능한 제품에 대해 &quot;기본값 사용&quot; 확인란이 제거되었습니다.

_ACP2E-4036 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]관리자 암호 정책이 PCI DSS 4.0 규정 준수(최소 12자)를 충족하지 않습니다.

이제 관리자는 저장소 > 구성 > 고급 > 관리 > 보안을 통해 관리자 사용자의 최소 암호 길이 요구 사항을 구성할 수 있습니다. 이러한 향상된 기능은 기존 암호 정책을 유지하면서 보다 높은 보안 유연성을 제공합니다. 유효성 검사는 관리자 사용자 생성/수정 및 구성 저장 중에 시행되며, 개선된 사용자 경험을 위한 실시간 프론트엔드 유효성 검사가 제공됩니다.

_ACP2E-4044 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### 관리 인터페이스 언어가 일본어일 때 날짜 필터 문제

생일 필터 및 열은 &quot;이후 고객&quot; 필터/열과 동일한 통합 형식 M/d/y를 사용합니다.

_ACP2E-4052 - [GitHub 문제](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/52f46328)_

#### 관리자 그리드 헤더의 양쪽에 표시되는 흰색 블록

관리 그리드의 시각적 정렬 문제를 해결했습니다. 이전에는 관리 패널에서 제품 그리드를 가로로 스크롤할 때 그리드 헤더의 왼쪽과 오른쪽에 흰색 블록이 어긋나게 표시됩니다. 이제 그리드 헤더 요소는 스크롤할 때 적절한 세로 정렬을 유지하여 큰 제품 카탈로그를 관리하는 관리자에게 더 깔끔한 시각적 경험을 제공합니다.

_ACP2E-4104 - [GitHub 문제](https://mcprod.pap-store.acer.com/index.html)_

#### Ui 구성 요소 fileUploader가 2.4.8-p1/ 2.4-develop에서 올바르게 작동하지 않음

업로드 영역 클릭에 대한 업로드를 허용하도록 다중 선택으로 사용자 정의 UI 구성 요소의 파일 업로드가 개선되었습니다.

_ACP2E-4162 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ee918f0d)_

#### [미리 보기]에서 새로 만든 주문/회사/고객 선택 프로세스 중에 자동으로 &quot;모두 선택&quot; 범위에 포함됨

오래된 관리 그리드 페이지에서 모든 레코드를 수동으로 선택하면 대량 작업을 수행할 때 의도하지 않게 모든 레코드가 삭제되는 문제를 해결했습니다. 이전에는 선택한 항목 수가 총 카운트와 일치하면 그리드가 내부적으로 &quot;모두 선택&quot; 모드로 자동 전환되므로 대량 작업이 명시적으로 선택한 항목만 영향을 주는 것이 아니라 모든 레코드에 영향을 미칩니다.

_ACP2E-4202 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6e134409)_

#### ACP2E-3362의 솔루션은 MariaDB 10.6에서 느리게 작동합니다

내역 검색 요청이 많은 경우 프론트엔드 검색 페이지의 성능이 개선되었습니다.

_ACP2E-4225 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ab891304)_

#### 대변 메모 그리드의 저장 시간대에 따라 날짜 필터가 작동하지 않음

이전에는 날짜 속성별 수정 필터링 목록에서 선택한 날짜와 저장된 날짜 사이의 시간대 차이로 인해 항목이 누락되었습니다. 이제 수정 날짜 필터가 제대로 적용된 후에.

_ACP2E-4239 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 페이지 빌더가 설치되면 파일 업로더 대화 상자가 두 번 열립니다

사용자 지정 구성 요소 업로드 수정 버튼이 두 번 트리거되기 전에. 수정 후 업로드 버튼이 예상대로 작동합니다.

_ACP2E-4241 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### 고객 데이터를 변경할 때 삭제된 고객 특성에 대한 유효성 검사 오류.

수정하기 전에 삭제된 속성 옵션이 여러 개 포함된 경우 고객 및 고객 주소를 저장하지 못했습니다. 수정 후에는 여러 속성 옵션이 있는 경우에도 두 옵션을 성공적으로 저장할 수 있습니다.

_ACP2E-4281 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 관리 대시보드의 JS 경고: &quot;로더가 시작될 것으로 예상되지만 dom에서 로더를 찾을 수 없음&quot;

관리 대시보드에 대해 차트를 활성화할 때 브라우저 콘솔에 표시되는 JavaScript 경고를 수정했습니다. 이전에는 차트가 활성화된 관리 대시보드에 액세스할 때 기능이 올바르게 작동하지만 사용되지 않는 디버그 검사에 대해 &quot;로더가 시작되어야 하지만 dom에서 찾지 못했습니다&quot;라는 경고가 잘못 표시되었습니다.

_ACP2E-4336 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2687b487)_

#### 저장소 구성에서 기본적으로 선택된 경우 종속성 구성이 있는 [클라우드] 구성을 편집할 수 있습니다.

&quot;기본/웹 사이트 사용&quot;을 선택했지만 페이지 로드 후 시스템 구성 필드가 활성화될 수 있는 문제를 해결했습니다.

_ACP2E-4337 - [GitHub 문제](https://mcstaging.pap-store.acer.com) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/31258bf6)_

#### 관리 대시보드 순서 그래프가 최종 크기로 애니메이션됨

이제 불필요한 크기 조정 애니메이션 없이 관리 대시보드 순서 그래프가 즉시 표시됩니다.

_ACP2E-4398 - [GitHub 문제](https://github.com/magento/magento2/issues/38860) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### JS 오류로 인해 페이지 빌더가 모바일 보기에 컨텐츠를 저장하지 못했습니다(TypeError: 정의되지 않은 속성을 읽을 수 없음).

모바일 보기에서 배너를 추가할 때 페이지 빌더에 페이지를 저장할 수 없는 문제를 해결했습니다.

_ACP2E-4399 - [GitHub 문제](https://github.com/magento/magento2/issues/38565) - [GitHub 코드 기여](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### 관리자 UI, B2B

#### 고객 헤더로 B2B 로그인에 여전히 Magento 브랜딩이 있음

이전에는 상점 헤더 표시에 Magento 브랜딩이 &quot;이제 &lt;store name>에서 &lt;customer name>(으)로 연결되었습니다&quot;라는 메시지가 표시되었습니다. 이제 수정되었으며 머리글에 ADOBE 브랜딩이 표시됩니다.

_AC-14361 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fadcfa8b)_

### 관리자 UI, 카탈로그

#### 카탈로그 규칙이 활성화되고 실시간 모드가 활성화된 경우 제품 저장이 실패합니다.

제품 트랜잭션에서 카탈로그 규칙 인덱싱을 분리하여 제품 저장 작업 중에 DDL 트랜잭션 오류로 카탈로그 규칙 인덱싱이 실패할 수 있는 문제를 해결했습니다.

_ACP2E-4378 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 관리자 UI, 콘텐츠

#### 이미지를 삽입하는 동안 &quot;미디어 자산 경로에 대한 렌디션을 만들 수 없음&quot; 예외가 발생했습니다.

미디어 갤러리 이미지 최적화 구성의 최대 너비 및 최대 높이 값을 제거한 후 이미지 최적화 프로세스 중에 더 이상 오류가 발생하지 않습니다.

_ACP2E-3781 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

### 관리자 UI, 순서

#### 관리 순서 만들기: 20개 이상의 제품을 추가할 때 세션 크기 오버플로(세션 크기가 256KB 제한을 초과함)

대규모 HTML 응답이 JSON 요청에 대한 세션에 저장되지 않도록 하여 관리자 로그아웃 없이 일괄 제품 추가가 원활하게 작동하도록 함으로써 관리자 주문 생성 중 세션 크기 오버플로를 해결했습니다.

_AC-15893_

### 관리자 UI, 보안

#### 취약한 암호 관리

동일한 암호를 사용하는 경우 관리자 사용자를 저장할 수 없습니다. 이전에는 제대로 확인하지 않고 저장되었습니다.

_ACP2E-3657 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 관리자 UI, 세금

#### 세율 관리자 ui 오류

이 티켓을 통해 국가(예: 미국→ 영국)를 전환해도 이전에 선택한 미국 주가 표시되므로 사용자가 오인할 수 있는 세율 관리자 UI 문제가 해결되었습니다.
2.4.9-alpha3에서 선택한 국가에 상태가 없으면 상태 필드는 이제 *로 재설정됩니다.

_AC-8440 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/보고

#### [문제] Google Analytics만 사용하는 경우 Analytics에 대한 허용 목록에 추가하다를 추가했습니다.

이 PR은 Google Analytics 모듈에 CSP 허용 목록을 추가하여 Google Adwords 종속성 없이 독립적으로 작동할 수 있도록 합니다. 이제 Google Analytics Adwords 모듈이 비활성화된 경우에도 Google이 올바르게 작동합니다.

_AC-16311 - [GitHub 문제](https://github.com/magento/magento2/issues/40051) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40032)_

#### 고급 보고서 CSV 파일의 중복 파일 헤더로 인해 빈 보고서가 생성됨

수정 후 고급 보고 기능에 대해 생성된 보고서에는 행 수가 배치 크기를 초과하는 경우 중복 머리글 행이 더 이상 포함되지 않습니다.

_ACP2E-4187 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 포기한 장바구니 보고서에 잘못된 문자가 포함되어 있습니다.

CSV 파일로 내보낸 중단된 장바구니 보고서에는 이제 MS Excel에서 열 때 인도 루피와 같은 통화 기호에 대해 올바르게 렌더링된 문자가 포함되어 있습니다.

_ACP2E-4288 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 2.4.8 호환성에 대한 MDVA-19640 업데이트

이 수정 작업으로 분석 크론 작업 작업이 기본 그룹에서 분석 그룹으로 이동되었습니다

_ACP2E-4309 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c135fc3a)_

#### 캐나다 웹 사이트/통화에 대한 관리자의 주문/송장 보고서에 수익이 표시되지 않음

일부 주문 관련 보고서는 스토어 통화 환율이 적용되지 않았습니다. 수정 후 보고서는 구성된 저장소 비율을 올바르게 적용합니다.

_ACP2E-4361 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### 게스트 체크아웃에 대한 회사 필드 유효성 검사 실패

이제 게스트 체크아웃이 회사 필드의 유효성을 올바르게 확인합니다.
이전에는 회사 속성이 필수인 경우 필드가 채워져 있더라도 &quot;회사가 필수 값입니다.&quot;라는 오류가 발생하여 게스트 체크아웃이 실패했습니다.
AC-14987

_AC-14987 - [GitHub 문제](https://github.com/magento/magento2/issues/40011) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

#### Rest API 제품-렌더링-정보가 로그인한 고객에 대해 잘못된 최종 가격을 반환함

티켓에 Rest API 제품-렌더링-정보에 대한 수정 사항이 있습니다. 로그인한 고객에 대한 잘못된 최종 가격을 반환하십시오.

_AC-5979 - [GitHub 문제](https://github.com/magento/magento2/issues/35757)_

### B2B, 장바구니 및 체크아웃

#### 관리자 기능 &quot;고객으로 로그인&quot;에서 B2B 회사 사용자에 로그인할 때 Storefront에 cartId = X 오류가 표시되는 엔티티가 없습니다.

이제 &quot;고객으로 로그인&quot; 기능을 사용할 때 관리 백엔드에서 성공적으로 로그인된 후 &quot;cartId = X인 해당 엔티티 없음&quot; 오류가 더 이상 표시되지 않습니다.

_ACP2E-3994 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 청구 주소 누락으로 인해 &quot;매장 배송&quot; 배송 방법으로 주문을 할 수 없음

매장 내 픽업을 게재 방법으로 선택한 경우 체크아웃 중에 청구 주소가 자동으로 채워지지 않는 문제를 해결했습니다. 청구 주소가 없으면 체크아웃을 완료할 수 없습니다.

_ACP2E-4030 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/42d23211)_

### 장바구니 및 체크아웃

#### Magento 2.4.7 업데이트(미니)장바구니, 허용되는 소수 수량 없음

이제 Magento은 로케일이 NL(네덜란드어)일 때 미니 장바구니에서 소수로 수량을 업데이트할 때 을 올바르게 처리합니다

_AC-13238 - [GitHub 문제](https://github.com/magento/magento2/issues/39236) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39669)_

#### [문제] 계약 모델 체크아웃에 EventPrefix 및 EventObject 추가

이제 시스템에 체크아웃 계약 모델에 대한 EventPrefix와 EventObject가 포함되어 있으므로 이벤트 접두사로 이벤트를 트리거할 수 있습니다. 이 개선 사항은 체크아웃 계약 이벤트로 작업할 때 개발자에게 보다 유연함을 제공합니다. 이전에는 체크아웃 계약 모델이 EventPrefix 및 EventObject를 지원하지 않아 이벤트 처리를 사용자 지정하는 기능이 제한되었습니다.

_AC-13252 - [GitHub 문제](https://github.com/magento/magento2/issues/32510) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32451)_

#### [문제] 개발자 경험: Quote AbstractItem 코드 스타일(SwiftOtter의 SOP-348)

이 끌어오기 요청은 추상 항목 메서드에 대한 잘못된 메서드 선언을 수정합니다.

_AC-13334 - [GitHub 문제](https://github.com/magento/magento2/issues/39340)_

#### 그룹화된 제품 프론트엔드 수량 유효성 검사가 누락되었습니다.

이제 시스템이 제대로 작동하며 음수 수량과 최대 수량을 추가하려고 할 때 유효성 검사 오류가 표시됩니다

_AC-13524 - [GitHub 문제](https://github.com/magento/magento2/issues/39479) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39480)_

#### [문제] subtotal.phtml 업데이트

시스템이 subtotal.phtml을 올바른 간격으로 업데이트합니다

_AC-13907 - [GitHub 문제](https://github.com/magento/magento2/issues/39619) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39612)_

#### 손님에게 주문을 할 수 없습니다.

이제 Adobe Commerce에서는 관리자의 필요에 따라 중간 이름 필드를 구성할 때 게스트 쇼퍼가 성공적으로 주문을 할 수 있습니다. 기존에는 Adobe Commerce 2.4.8-beta1(PHP 8.3/8.4)에서 필요에 따라 중간 이름을 구성하고 게스트로 체크아웃할 경우 중간 이름이 제공되더라도 주문 배치를 할 수 없어 체크아웃 완료가 차단됐다. AC-14241

_AC-14241 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql]은(는) Null을 허용하지 않는 필드 &quot;SelectedCustomizableOption.label&quot;에 대해 null을 반환할 수 없습니다.

이제 선택한 옵션이 더 이상 존재하지 않을 때 시스템에서 내부 서버 오류가 발생하지 않습니다.

_AC-14256 - [GitHub 문제](https://github.com/magento/magento2/issues/39729) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39888)_

#### 하나의 위시리스트 항목이 잘못된 경우 GraphQL addWishlistItemsToCart가 기존 장바구니 항목에 대한 수량을 업데이트하지 못했습니다(Magento 2.4.7-p3).

잘못된 구성 가능한 제품이 발견될 때 GraphQL addWishlistItemsToCart 돌연변이가 처리를 중지하는 문제가 해결되었습니다. 수정 후 유효한 위시리스트 항목이 장바구니에 추가되고 수량이 업데이트되는 반면, 유효하지 않은 항목은 건너뛰고 적절한 오류가 반환됩니다.

_AC-14464 - [GitHub 문제](https://github.com/magento/magento2/issues/39820) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] 도시 이름에 0~9 자릿수, 앰퍼샌드, 전체 중지 또는 괄호가 있는 경우 주문을 할 수 없습니다.

. , &amp; 또는 괄호와 같은 특수 문자가 포함된 도시 이름에 대해 체크아웃하지 못하던 문제를 수정했습니다.
이제 이러한 도시 이름을 가진 주문이 검증 오류 없이 성공적으로 주문됩니다.

_AC-14495 - [GitHub 문제](https://github.com/magento/magento2/issues/39854) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 게스트 접두사가 견적 주소 2.4.8에 저장되지 않음

이제 체크아웃 중에 게스트 고객 접두사(Mr/Mrs)가 저장됩니다.
이전에는 게스트 고객이 선택한 인사말이 최종 주문에 도달하기 전에 손실되었으며 다른 모든 주소 필드가 올바르게 전송되었습니다.
AC-14705

_AC-14705 - [GitHub 문제](https://github.com/magento/magento2/issues/39915) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

#### 수량 조건이 있는 Salesrule 하위 선택 적용 실패

제품 하위 선택 조건이 있는 장바구니 가격 규칙이 체크아웃 시 적용되지 않는 문제를 해결했습니다.
이제 구성된 규칙에 따라 할인이 성공적으로 적용됩니다.

_AC-14884 - [GitHub 문제](https://github.com/magento/magento2/issues/39965) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

#### [문제] 클래스 특성에서 공백 제거

이제 클래스 특성에서 추가 공백이 제거됩니다

_AC-14939 - [GitHub 문제](https://github.com/magento/magento2/issues/39977) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39970)_

#### Graphql - 미납주문이 활성화된 경우 장바구니 병합이 제대로 작동하지 않음

GraphQL을 통한 장바구니 병합 중에 게스트 장바구니 항목이 고객 장바구니와 병합되지 않던 문제를 수정했습니다.
이제 고객 장바구니에는 고객 장바구니와 고객 장바구니의 결합 수량이 올바르게 반영됩니다.

_AC-15148 - [GitHub 문제](https://github.com/magento/magento2/issues/40064) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [통합] [체크아웃] 실패한 결제 전자 메일 템플릿에서 종속 지시문이 업데이트되었습니다.

실패한 결제 이메일 템플릿이 종속 지시어를 올바르게 처리하도록 업데이트되었습니다.
수정 사항을 통해 해당되는 경우 배송 주소와 배송 방법이 올바르게 표시됩니다.
이전에는 실패한 결제 이메일에서 이러한 필드가 누락되었습니다.

_AC-15363 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 고정 제품 세금이 활성화된 경우 [장바구니] 장바구니 페이지가 로드되지 않음

FPT(Fixed Product Tax)가 활성화된 경우 장바구니 페이지가 무한 로딩으로 전환되는 문제를 해결했습니다. 문제는 세금이 품목 가격과 동일한 HTML 요소에 포함되어 중앙 소계와 요약 소계의 불일치로 인해 잘못된 소계 계산이 발생하였다. 수정 후 장바구니가 올바르게 로드되고 정확한 합계가 표시됩니다.

_AC-16096 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/01cee3c3)_

#### 장바구니 가격 규칙 작업 &quot;장바구니에서 가격&quot; 조건, 허용되지 않을 때 적용

&quot;보다 낮은 장바구니 가격&quot; 조건의 장바구니 가격 규칙이 부적격 제품에 잘못 적용되는 문제가 수정되었습니다.
이제 장바구니 품목 가격이 구성된 규칙 조건을 충족하지 않을 때 쿠폰이 제대로 검증되고 거부됩니다.

_AC-6997 - [GitHub 문제](https://github.com/magento/magento2/issues/36433) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/01cee3c3)_

#### [문제] base_price 대신 견적 항목에 대한 가격 설정

프론트엔드의 한 웹 사이트에 여러 개의 통화가 있는 경우, 시스템은 가격 대신 base_price로 설정된 견적 항목을 올바르게 처리합니다

_AC-9985 - [GitHub 문제](https://github.com/magento/magento2/issues/38094) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36878)_

#### 만료된 영구 견적은 cron job sales_clean_quotes에 의해 정리되지 않습니다.

이제 &#39;persistent_clear_expired&#39; cron 작업이 실행될 때 만료된 영구 견적이 지워집니다. 이전에는 다른 cron 작업에서 지워지지 않는 만료된 영구 따옴표였습니다.

_ACP2E-3493 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/11be3dff)_

#### 비활성 회사에 대한 체크아웃 시 &quot;문제가 발생했습니다&quot; 오류 발생

수정 전에는 사용자 회사의 장기 기능이 더 이상 활성화되지 않은 경우 장바구니에서 로그아웃 작업이 제대로 완료되지 않았습니다. 이제 회사를 더 이상 사용할 수 없는 경우 로그아웃이 제대로 수행됩니다.

_ACP2E-3541 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### &quot;여러 주소로 체크아웃&quot;하면 주소 선택이 저장되지 않습니다.

멀티배송 옵션을 취소하는 경우 이 문제를 해결하기 전에 멀티배송으로 되돌릴 때 주소가 미리 선택되지 않았습니다. 이제 기본 주소가 다중 배송 화면에서 선택한 항목 중 하나로 바뀝니다.

_ACP2E-3646 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6ea61121)_

#### [클라우드] 주문이 하나의 스토어 보기에서 만들어진 경우 최근 주문이 다른 스토어 보기에 표시되지 않습니다.

&quot;내 계정&quot; 페이지에 동일한 스토어 내 다른 스토어 보기의 최근 주문이 표시되지 않던 문제를 해결했습니다. 주문 검색 논리가 업데이트되어 &quot;내 주문&quot; 페이지의 비헤이비어에 맞게 모든 스토어 보기에서 일관된 주문 가시성을 보장합니다.

_ACP2E-3807 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 수량 표시 형식  번들 제품을 추가하는 동안 관리자 고객 장바구니 섹션에서 0개  

이제 고객 활동의 장바구니 섹션에 올바른 수량이 표시됩니다. 이전에는 수량이 0으로 표시되었습니다.

_ACP2E-3872 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

#### 장바구니가 더 이상 요구 사항을 충족하지 않을 때 [클라우드] 무료 배송 할인이 올바르게 제거되지 않음

소계(제외) 장바구니 가격 규칙의 세금)에는 이제 이전 규칙의 할인이 포함됩니다.

_ACP2E-3973 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 다중 배송에서 동일한 고객에 대해 중복 주문 발견

여러 배송 주소가 있는 주문을 동시에 요청해도 더 이상 동일한 고객에 대한 주문이 중복되지 않습니다

_ACP2E-4117 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 재고 부족 임계값에 도달하면 [Cloud] 재고 제한 초과 알림 메시지가 두 번 표시됩니다

장바구니 업데이트에 중복 오류 배너가 표시되는 문제를 해결했습니다. 이전에는 AJAX 유효성 검사 오류 후 백엔드가 양식 제출 중에 동일한 메시지를 다시 추가했으므로 쇼핑객에게 두 개의 동일한 경고가 표시되었습니다. 이제 추가 백엔드 메시지 추가를 건너뛰고 장바구니 페이지를 하나의 명확한 오류 배너에 유지합니다.

_ACP2E-4192 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

#### 청구 정보의 경우 배송 정보 REST API를 사용하여 서버 측 유효성 검사가 작동하지 않음

고객 주소 데이터 유효성 검사가 REST와 체크아웃용 GraphQl 간에 더 일관되도록 개선되었습니다.

_ACP2E-4223 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 장바구니 페이지의 [Cloud] 번들 제품 가격 문제

여러 통화 스토어의 장바구니 페이지에서 번들 제품 가격 문제를 해결했습니다

_ACP2E-4245 - [GitHub 문제](https://www.techbuyer.com/) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/cbca0396)_

#### 장바구니 저장소 범위 문제 관리

이제, 기본이 아닌 웹 사이트에 할당된 고객의 장바구니를 관리할 때 장바구니 오류가 관리자 사용자에게 표시됩니다. 이전에는 오류가 표시되지 않았습니다.

_ACP2E-4348 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

#### 부분 송장 취소 후 쿠폰 times_used 재설정

주문이 부분적으로 취소되면 쿠폰 times_used 카운트가 올바르게 업데이트됩니다.

_ACP2E-4365 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

### 장바구니 및 체크아웃, GraphQL

#### GraphQL을 통해 주문할 때 오류 코드에 메시지를 매핑하는 도중 오류 발생

존재하지 않거나 비활성 장바구니를 주문하기 위해 호출된 GraphQL은 이제 모든 스토어 보기에서 CART_NOT_ACTIVE 또는 CART_NOT_FOUND 오류 코드를 올바르게 반환하며, 이전에 번역된 오류 메시지로 인해 정의되지 않은 코드가 표시되던 문제를 해결합니다.

_ACP2E-3942 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 가상 견적에 대한 [GraphQl] 장바구니 쿼리 장바구니 항목 할인 문제

GraphQL 장바구니 쿼리가 가상 견적에 대해 잘못된 할인 금액을 반환하는 문제를 해결했습니다. 기존에는 자격이 없는 특정 가상 상품에 할인이 잘못 적용됐다.

_ACP2E-4248 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/cbca0396)_

#### [클라우드] ACSD-68499_2.4.8-p2에서 다른 문제가 생성됨

수량이 부족한 항목에 대해 graphQL 요청을 수행하면 오류 코드가 있는 적절한 오류 메시지가 반환되고, 요청된 수량이 사용 가능한 경우 장바구니 업데이트가 성공했습니다.

_ACP2E-4404 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1c547060)_

### 장바구니 및 체크아웃, GraphQL, 인벤토리 / MSI

#### cartItemInterface의 is_available 속성은 판매 가능한 재고가 높은 경우에도 false를 반환합니다.

is_available 속성은 매출 가능한 재고가 높을 때 true를 반환합니다. 이전에는 항상 false를 반환했습니다.

_ACP2E-3885 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### 장바구니 및 체크아웃, 인벤토리/MSI

#### 장바구니 크기가 큰 &#39;픽업 위치 검색&#39; 엔드포인트에 414 오류

장바구니에 많은 제품이 있을 때 긴 URL로 인해 &quot;매장 선택&quot;을 사용하여 체크아웃 중에 매장을 선택하는 작업이 더 이상 실패하지 않습니다.
이전에는 이렇게 하면 스토어 선택 중에 과도하게 긴 URL이 생성되어 414 오류가 발생하여 고객이 체크아웃을 완료할 수 없었습니다.

_ACP2E-4266 - [GitHub 문제](https://mcstaging.casamyers.com.mx/) - [GitHub 코드 기여](https://github.com/magento/inventory/commit/ae1f272f)_

### 장바구니 및 체크아웃, 프로모션

#### 기프트 카드의 표시 잔액은 웹 사이트 범위에 의해 제한되지 않습니다.

지정된 웹 사이트 범위에서 기프트 카드 잔액 검사를 제한했습니다.

_ACP2E-4379 - [GitHub 문제](https://www.panini.it)_

### 장바구니 및 체크아웃, 보안

#### [클라우드] sri 패치를 구현한 후 첫 번째 시도에서 체크아웃 페이지에서 JS용 404 파일 가져오기

수정 전 mixin은 축소 및 번들링을 활성화할 때 장바구니 및 체크아웃에 로드되지 않았습니다. 수정 후 모든 mixin이 예상대로 로드됩니다.

_ACP2E-4128 - [GitHub 문제](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/e457c5e2)_

### 장바구니 및 체크아웃, 배송

#### [Mainline] 장바구니 가격 규칙이 다중 배송을 준수하지 않습니다.

이 수정이 실행되기 전에 하위 선택 조건이 적용되고 무료 배송이 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않았습니다. 다만, 보정치를 적용하였기 때문에 다품운반카트에 대한 장바구니 가격규정은 이제 의도한 대로 기능하게 되었다.

_ACP2E-3666 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

### 카탈로그

#### 동일한 쿼리가 있는 동일한 페이지에 대한 캐시 fpc가 중복됨

이제 시스템은 순서 또는 후행 문자에 관계없이 동일한 쿼리 매개 변수가 있는 페이지에 대해 동일한 FPC(전체 페이지 캐시)를 올바르게 식별하고 사용합니다. 이렇게 하면 페이지 캐시 폴더 크기가 불필요하게 증가하는 것을 방지할 수 있습니다. 이전에는 쿼리 매개 변수의 순서가 다르거나 후행 문자가 있는 경우 동일한 페이지에 대해 다른 FPC 식별자를 만들면 페이지 캐시 폴더 크기가 증가했습니다.

_AC-10722 - [GitHub 문제](https://github.com/magento/magento2/issues/38269) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38270)_

#### catalog_product_entity_int 테이블에 필요한 열의 인덱싱이 누락됨

catalog_product_entity_int 테이블에 필수 열의 누락된 인덱싱이 추가되었습니다.

_AC-10844 - [GitHub 문제](https://github.com/magento/magento2/issues/38315) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38316)_

#### 카탈로그 URL 리소스의 범위 버그(_getCategories)

이 PR은 범주 URL 리소스의 저장소 범위에 값이 정의되어 있지 않은 경우 기본 범위에 대체를 추가합니다.

_AC-11011 - [GitHub 문제](https://github.com/magento/magento2/issues/38393) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38394)_

#### [문제] OpenGraph에서 가격을 표시할 수 있는지 확인

가격을 숨기고 이 변경 가격이 OG 태그에 표시되지 않는 플러그인을 사용하면 시스템이 제대로 작동합니다.

_AC-11635 - [GitHub 문제](https://github.com/magento/magento2/issues/38512) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38510)_

#### 가격을 표시하기 위해 세금을 추가할 때 가격에 대한 반올림 문제

시스템은 이제 가격을 표시하기 위해 세금을 추가할 때 가격에 대한 반올림 문제를 수정합니다

_AC-11725 - [GitHub 문제](https://github.com/magento/magento2/issues/18025) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35730)_

#### [문제] 사용자 지정 카탈로그 규칙 조건 허용

엄격한 유형 확인으로 인해 사용자 지정 카탈로그 규칙 조건을 사용할 수 없는 문제를 해결했습니다. 이 수정 사항은 클래스 같음 검사를 instanceof로 대체하므로 사용자 지정 조건 클래스가 올바르게 작동할 수 있고 규칙 유효성 검사 및 인덱싱이 성공적으로 수행될 수 있습니다.

_AC-13338 - [GitHub 문제](https://github.com/magento/magento2/issues/39339) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### 위시리스트에 추가 시 구성 가능한 제품 손실 옵션

구성 가능한 제품 옵션이 위시리스트에 제품을 추가한 후에 손실되는 문제를 해결했습니다. 이제 선택한 옵션이 유지되므로 사용자가 옵션을 다시 선택하라는 메시지를 표시하지 않고 제품을 장바구니에 매끄럽게 추가할 수 있습니다.

_AC-13373 - [GitHub 문제](https://github.com/magento/magento2/issues/39363) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/cc0ec250)_

#### 구성 가능한 제품의 하위 제품(단순 제품)에 대한 특별 가격이 올바르게 표시되지 않음

&quot;제품 목록에서 사용됨&quot;을 아니요로 설정한 경우 구성 가능한 제품의 하위(단순) 제품에 대한 특별 가격이 제품 목록 페이지에 올바르게 표시되지 않는 문제가 해결되었습니다. 이제 특별 가격이 일반 가격과 함께 올바르게 표시되므로 제품 유형 간에 일관된 가격 표시가 보장됩니다.

_AC-13594 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3cf1a106)_

#### [버그] REST API: 특별 가격 업데이트는 모든 스토어 조회수에 대한 값을 설정하지 않습니다

이제 REST API는 웹 사이트의 모든 스토어 조회수에 대해 특별 가격을 업데이트합니다.
이전에는 REST API를 통해 특별 가격을 업데이트하면 웹 사이트의 모든 스토어 보기가 아닌 지정된 스토어 보기에만 영향을 주었습니다.
AC-13671

_AC-13671 - [GitHub 문제](https://github.com/magento/magento2/issues/39521) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 가격 범위 및 config.php와 관련된 문제

Magento 2.4.2에서 config.php를 통해 가격 범위를 변경해도 가격 속성에 대한 catalog_eav_attribute의 is_global 값이 제대로 업데이트되지 않습니다.
따라서 제품 가격은 전 세계적으로 유지되며 가격 범위가 웹 사이트로 설정되어 있더라도 웹 사이트당 저장할 수 없습니다.
이 문제를 해결하려면 데이터베이스에서 is_global 열을 수동으로 업데이트해야 합니다. 이는 프로덕션 환경에 적합하지 않습니다.
이 동작은 가격 범위가 글로벌 또는 웹 사이트이지만 스토어 보기별이 아닌 Magento의 기본 디자인과 일치합니다.

_AC-13857 - [GitHub 문제](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP 오류가 게시되지 않음

후속 호출에 사용할 특정 제품의 &quot;_cache_instance_product_ids&quot; 데이터를 올바르게 추가하도록 루프 변수 이름을 변경했습니다.

_AC-14159 - [GitHub 문제](https://github.com/magento/magento2/issues/39641) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39642)_

#### 탄력적인 검색이 제품의 기본 정렬 순서를 방해합니다(최신 항목을 오래된 항목부터 변경).

이제 시스템이 정렬합니다. 데이터베이스의 최신 제품(entity_id가 가장 높은 제품)이 먼저 표시됩니다

_AC-14411 - [GitHub 문제](https://github.com/magento/magento2/issues/31043) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36900)_

#### 스토어 전환 페이지가 2.4.8의 캐시에서 옴(스토어 전환기가 작동하지 않음)

캐시를 수동으로 지울 때까지 storefront 헤더에서 저장소 보기 전환을 수행하지 못했던 문제를 수정했습니다.
이제 캐시 정리를 수행하지 않고도 저장소 보기 전환이 올바르게 작동합니다.

_AC-14426 - [GitHub 문제](https://github.com/magento/magento2/issues/39806)_

#### 최소 너비: (@screen__l)인 .less 스타일이 무시됨

카테고리 페이지의 행당 세 개의 제품만 표시되던 문제를 수정했습니다.
이제 예상대로 행당 4개의 제품이 표시됩니다.

_AC-14463 - [GitHub 문제](https://github.com/magento/magento2/issues/39817) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 고객 메뉴의 위시리스트 페이지를 제외하고 홈페이지/기타 페이지에 위시리스트 수가 표시되지 않음

위시리스트가 아닌 페이지에서 위시리스트 수가 빈 괄호로 표시되던 문제를 수정했습니다.
이제 모든 페이지의 &quot;내 위시리스트&quot; 옆에 올바른 위시리스트 항목 수가 표시됩니다.

_AC-14607 - [GitHub 문제](https://github.com/magento/magento2/issues/39892) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b3774fbe)_

#### store-level 값 없이 REST API를 사용할 때 catalog_product_save_before observer에서 날짜 관련 오류가 발생합니다(getFinalPrice() 문제).

이 PR은 날짜가 DateTimeInterface 인스턴스로 제공될 때 적절한 서식이 지정되도록 SpecialFromDate의 처리를 조정합니다. 이를 통해 특정 시나리오에서 getFinalPrice() 실행 중에 발생하는 오류를 방지할 수 있습니다.

_AC-14847 - [GitHub 문제](https://github.com/magento/magento2/issues/39959) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40003)_

#### 긴급 - 추가할 제품에 사용자 정의 가능한 옵션이 있는 경우 번들에 제품을 추가할 수 없음

사용자 지정 가능한 옵션이 있는 제품을 번들 제품에 추가할 수 없는 문제를 해결했습니다.
이전에는 이러한 제품이 번들 생성의 &quot;옵션에 제품 추가&quot; 목록에서 제외되었습니다.
이제 맞춤형 옵션이 포함된 제품을 맞춤형 옵션을 포함하지 않고 번들에 추가할 수 있어 적절한 재고 관리가 가능하다.
따라서 제품을 복제하거나 재고 수준에 영향을 주지 않고 번들을 만들 수 있습니다.

_AC-14958 - [GitHub 문제](https://github.com/magento/magento2/issues/39993)_

#### 음수 `?p=` 쿼리 문자열로 인해 Elasticsearch 예외가 발생합니다.

이제 시스템에서 범주 페이지 매김의 음수 ?p= 값을 해결합니다. 그러면 현재 예외가 발생하고 유효한 요청으로 간주됩니다

_AC-15191 - [GitHub 문제](https://github.com/magento/magento2/issues/40079) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40080)_

#### 단일 옵션이 있는 구성 가능한 제품에 대해 &#39;다음으로 낮음&#39; 가격 레이블이 표시됨

구성 가능한 제품이 PDP/PLP에 잘못된 &quot;As low as&quot; 레이블과 함께 가격을 표시하는 문제가 해결되었습니다.
이제 이 제품은 오해의 소지가 있는 라벨 없이 정확한 가격(500달러)을 보여주고 있다.

_AC-15237 - [GitHub 문제](https://github.com/magento/magento2/issues/40104) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [비교에 추가] 단추에 대해 잘못된 메서드가 호출되었습니다.

\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect()에 사용된 메서드를 수정했습니다.
이전에는 getAddToCartButton() 대신 getAddToCartButton()이 잘못 호출되었습니다.
이렇게 하면 제품 목록에서 &quot;비교에 추가&quot; 단추를 렌더링하기 위한 올바른 동작이 보장됩니다.
기능 동작 변경 사항이 도입되지 않았습니다. 업데이트는 개발자 경험 및 코드 수정을 개선합니다.

_AC-15323 - [GitHub 문제](https://github.com/magento/magento2/issues/39754) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 잘못된 제품 가격이 다른 스토어 보기에서 다른 통화로 장바구니에 표시됨

스토어 조회수 간에 서로 다른 통화를 사용할 때 장바구니에 잘못된 제품 가격이 표시되던 문제를 수정했습니다. 수정 후 장바구니에 구성된 통화를 기반으로 올바른 전환 가격이 표시되므로 제품 페이지와 장바구니 간에 일관성이 보장됩니다.

_AC-15385 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### FPT가 활성화된 경우 구성 가능한 제품에 대한 &quot;최저 가격&quot; 표시가 잘못됨

FPT가 활성화된 경우 구성 가능한 제품에 대한 잘못된 &quot;낮은 가격&quot;이 세금이 두 번 적용되어 발생했음을 확인했습니다. 이 수정 사항은 최종 가격 계산이 세금 구성을 준수하는지 확인하며 이제 올바른 가격을 표시합니다.

_AC-15718 - [GitHub 문제](https://github.com/magento/magento2/issues/40171) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a06a4a57)_

#### Eav\Model\Entity\Collection\AbstractCollection의 _loadAttributes 시간 복잡성은 장바구니 및 속성의 제품 수에 따라 증가합니다

이 PR은 중첩된 루프를 배열 결합(+)으로 바꾸고 _setItemAttributeValue 호출을 줄여 Eav\Model\Entity\Collection\AbstractCollection에 _loadAttributes를 최적화함으로써 대형 제품 카트의 성능을 개선했습니다.

_AC-15833 - [GitHub 문제](https://github.com/magento/magento2/issues/40216) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40217)_

#### 컬렉션 캐시와 구성 가능한 제품 갤러리 간의 디버깅 상호 작용

media_gallery_images 가 항상 컬렉션으로 처리되도록 방어 유형 검사를 추가하여 구성 가능한 제품 갤러리의 캐싱 문제를 해결했습니다. 이로 인해 손상된 캐시 데이터로 인한 치명적인 오류가 방지되었습니다.

_AC-16066 - [GitHub 문제](https://github.com/magento/magento2/issues/33965) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3b5ac075)_

#### URL 재작성으로 인해 제품 페이지에 오류가 발생합니다.

이제 URL 재작성을 할 때 제품 페이지가 성공적으로 로드됨

_AC-2950 - [GitHub 문제](https://github.com/magento/magento2/issues/35371) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39670)_

#### MAGE_INDEXER_THREADS_COUNT에서 indexer_update_all_views cron 오류가 발생했습니다.

고객 세그먼트 인덱서가 있는 MAGE_INDEXER_THREADS_COUNT > 2에 대한 문제가 해결되었습니다.

_ACP2E-3538 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 페이지 빌더 제품 위젯 조건에 &quot;조건 조합&quot;을 추가하는 동안 예외 발생

누락되거나 불완전한 조건을 건너뛰기 위한 검사를 추가하여 문제를 해결했습니다. 이전에는 시스템에서 불완전한 조건을 처리하여 오류 로그가 생성되었습니다.

_ACP2E-3545 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/11be3dff)_

#### 속성 집합을 로드할 때 브라우저 충돌이 발생했습니다.

4k개가 넘는 제품 속성이 있는 경우 속성 세트 편집 페이지에서 브라우저가 더 이상 충돌하지 않습니다.

_ACP2E-3633 - [GitHub 문제](https://github.com/magento/magento2/issues/38810) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b12ffe36)_

#### 새 스토어에 대해 [CLOUD] 제품 URL 다시 쓰기가 만들어지지 않음: Go Live Blocker

새 스토어에 대한 제품 URL 재작성에 성공했습니다.
이전 작업이 메모리 누수 또는 시간 초과로 종료되었습니다.

_ACP2E-3669 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### 옵션의 속성 기본값이 작동하지 않음

이전에는 제품 선택 속성의 기본값을 변경했을 때 이전 값이 있는 배열 요소로 표시되었습니다. 이 수정 사항이 적용된 후 제품 속성 값을 업데이트하면 eav_attribute 테이블에 단일 요소로 저장됩니다.

_ACP2E-3688 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

#### [Mainline] [CLOUD] 이미지 크기 조정을 수행하면 400GB 이상의 디스크 공간이 사용됩니다.

수정 후 `catalog:images:resize` 플래그와 함께 사용된 `--skip_hidden_images` 명령은 이미지가 없는 웹 사이트에 대한 이미지 캐시를 생성하지 않습니다.

_ACP2E-3869 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

#### 동적 이미지 생성으로 많은 수의 이미지를 생성합니다.

수정 후에는 제품이 지정된 웹 사이트에 대해서만 이미지가 생성됩니다.

_ACP2E-3927 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fab20b00)_

#### 제공된 CountryID가 존재하지 않음 - 아일랜드 (IE)

수정 후 아일랜드 우편 번호를 사용하여 픽업 위치를 검색할 수 있습니다.

_ACP2E-3932 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### 레이아웃에 캐시된 잘못된 레이아웃 구조로 인해 프론트엔드에 500 오류가 발생합니다.

레이아웃에서 캐시되는 잘못된 레이아웃 구조로 인해 페이지가 500 오류 코드를 반환하는 문제를 해결했습니다

_ACP2E-4040 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### 제품 보기 보고서 잘못됨 - GA에 비해 낮은 수

report_viewed_product_index 테이블에 올바른 제품 페이지 보기 수가 표시되지 않던 버그를 수정했습니다.

_ACP2E-4045 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6e134409)_

#### 예약된 업데이트의 카탈로그 가격 규칙 할인 금액 필드에 대한 유효성 검사 오류

이전에는 이 문제를 수정하기 전에 카탈로그 가격 규칙에 대한 일정 업데이트에 대해 할인 금액이 by_fixed인 경우 검증 번호 범위 규칙으로 인해 제대로 검증되지 않았습니다. 이 수정 사항이 적용되면 고정 가격 카탈로그 가격 규칙에 대해 유효성 검사가 제대로 작동합니다.

_ACP2E-4054 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### VAT API 요금 제한기로 인해 VAT 유효성 검사에 실패했습니다. 거짓 양성 고객 그룹 변경을 트리거합니다.

Europa Vat 유효성 검사 도구에 대한 요청을 최적화했으므로 &quot;환율 제한기&quot; 오류가 줄어듭니다.

_ACP2E-4072 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ee918f0d)_

#### 프로덕션에서 최대 쓰기 집합 크기 오류를 트리거하는 코어 인덱서의 대량 삭제

데이터 볼륨을 기반으로 두 가지 삭제 전략을 구현하여 카탈로그 규칙 제품 인덱스 정리를 최적화합니다.

_ACP2E-4085 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

#### 비활성화 후 제품이 품절로 표시됨

수정 후 비활성화된 제품이 제품 위젯에 없습니다.

_ACP2E-4136 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [클라우드] 중복 항목이 있는 오류(temp_category_descendants_%)

중첩된 범주가 많은 환경에 대해 예약된 업데이트를 만드는 동안 중복 항목이 발생하는 문제를 해결했습니다.

_ACP2E-4159 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] 제품 수 비교에 다른 스토어의 불일치 문제가 있습니다

이제 다른 저장소로 전환하면 제품 목록 비교가 제대로 작동합니다.

_ACP2E-4249 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/98f028ab)_

#### 이미지 역할 할당을 위해 &#39;이미지 및 비디오&#39;에서 &#39;기본값 사용&#39; 옵션이 없음

제품 이미지 및 비디오 섹션에 &quot;기본값 사용&quot; 옵션이 추가되어 기본 범위의 설정을 상속할 수 있습니다.

_ACP2E-4280 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

#### 고객 그룹을 업데이트한 후에도 제한된 범주 제품이 여전히 위시리스트에서 카운트됨

수정 전에는 범주 권한이 고객 위시리스트 항목에 제대로 적용되지 않았습니다. 이제 수정 후 위시리스트 항목이 웹과 GraphQL 모두에서 올바르게 표시되고 페이지가 지정됩니다.

_ACP2E-4294 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c135fc3a)_

#### PDP 및 PLP의 [Cloud] 번들 제품 가격 문제

기본 가격이 아닌 통화의 경우 PDP/PLP에 일반 가격이 있는 번들 제품의 가격이 올바르게 표시됩니다.

_ACP2E-4298 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

#### 고객 그룹이 변경된 후 액세스할 수 없는 제품을 주문할 수 있습니다.

이전에는 관리에서 고객 그룹을 변경할 때 프론트엔드 카탈로그 및 장바구니가 카탈로그 권한의 변경 사항을 반영하지 않았습니다. 그러나 이 수정 사항을 적용한 후 고객 그룹이 관리자로부터 변경될 때 업데이트된 카탈로그 권한에 따라 프론트엔드 견적이 변경됩니다.

_ACP2E-4300 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 높은 메모리 사용으로 인해 색인 재지정이 중단됨

카탈로그 규칙 인덱서가 메모리를 과도하게 소모하여 완료하지 못하여 불안정 및 메모리 부족 오류가 발생하는 문제를 해결했습니다.

_ACP2E-4303 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS] 예약된 업데이트 미리 보기 링크가 유지 관리 페이지로 리디렉션됨

구성 가능한 제품이 있는 홈페이지 링크의 일정이 잡힌 업데이트 미리보기에는 제품 목록이 올바르게 표시됩니다. 이전에는 사용자를 유지 관리 페이지로 리디렉션했습니다.

_ACP2E-4401 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1c547060)_

### 카탈로그, GraphQL

#### GraphQl 잘못된 할인 계산

이제 카탈로그 가격이 세금을 포함하도록 구성되면 GraphQL에 할인 비율과 기본 가격이 올바르게 표시됩니다. 기존에는 20%가 아닌 19.99%를 표시하는 등 반올림 오류가 발생했다.

_ACP2E-3993 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL 미디어 갤러리 필드는 캐시 플러시 후 빈 데이터를 반환합니다.

수정 후 장바구니 요청에 대한 GraphQL 응답에서 예상대로 제품의 media_gallery가 반환됩니다.

_ACP2E-4185 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

### 카탈로그, GraphQL, 검색

#### Products graphql이 범주 집계에서 비활성화된 범주를 반환했습니다.

이후 제품 GraphQl 요청에 대해 수정 비활성화된 카테고리가 반환되지 않습니다.

_ACP2E-2885 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

### 카탈로그, 성능

#### 관리자의 범주 로드 속도가 매우 느립니다.

카테고리 로드 성능이 크게 개선되었습니다. 이전에는 범주를 로드하는 데 너무 오래 걸려 시간 초과 문제가 발생했습니다.

_ACP2E-3891 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### 카탈로그, 가격 책정

#### 잘못된 카탈로그 가격 규칙 할인이 하위 제품에 적용됨

두 규칙 모두 우선순위가 동일한 경우 변형에 대한 카탈로그 가격 규칙이 상위 구성 가능한 제품에 의해 재정의되는 문제를 수정합니다.

_ACP2E-3693 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Cloud] 번들 제품 가격 문제

특별 가격이 포함된 번들 제품의 가격이 기본값이 아닌 통화에 대해 PDP/PLP에 올바르게 표시됩니다.

_ACP2E-4110 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6e134409)_

### 카탈로그, 제품

#### [임의 버그] Fotorama 라이브러리가 로드되지 않음

이제 시스템에서 Fotorama 라이브러리가 제대로 로드되었는지 확인하므로 첨부된 모든 이미지가 예상대로 이미지 갤러리에 표시됩니다. 이전에는 Fotorama 라이브러리가 제대로 로드되지 않는 문제로 인해 첫 번째 이미지만 표시되었습니다.

_AC-12124 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/27217d0e)_

#### &quot;수동으로 제품 추가&quot; 링크가 항상 표시되어야 함

기존 구성이 없는 구성 가능한 제품을 만들 때 &quot;수동으로 제품 추가&quot; 링크가 표시되지 않는 문제가 수정되었습니다. 이제 링크가 항상 표시되어 관리자가 더미 구성을 만들지 않고도 간단한 제품을 쉽게 연결할 수 있습니다.

_AC-13866 - [GitHub 문제](https://github.com/magento/magento2/issues/39595) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef666cd9)_

#### 백엔드에서 제품 편집 제품 옵션 가격에서 소수점 이하 자리 수를 추가로 제거합니다.

관리자 잘림 제품 옵션 가격에서 제품을 편집할 때 소수점 이하 두 자리로 가격이 조정되는 문제를 해결했습니다. 이제 시스템은 더 높은 소수점 정밀도로 가격을 유지하여 저장 후 정확한 값이 유지되도록 합니다.

_AC-14050 - [GitHub 문제](https://github.com/magento/magento2/issues/39655) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3b5ac075)_

### 카탈로그, 검색

#### RestApi 요청 &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39;이(가) 시간 초과 오류로 실패합니다.

범주 REST API 요청이 시간 초과 오류와 함께 더 이상 실패하지 않습니다.
이전에는 /rest/default/V1/categories?searchCriteria[page_size]=1에 대한 요청이 특정 코드를 변경한 후 시간 초과로 실패할 수 있었습니다.
AC-13358

_AC-13358 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

### 콘텐츠

#### graphql(magento 2.4.6-p4 ) - 활성 상태가 아닌 cms 페이지를 가져오려고 할 때 오류 발생

비활성화된 CMS 페이지에 대한 GraphQL 쿼리에서 내부 서버 오류가 반환되던 문제를 수정했습니다.
이제 쿼리가 오류 없이 적절한 응답을 가져옵니다.

_AC-12302 - [GitHub 문제](https://github.com/magento/magento2/issues/38877) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 위시리스트 공유 양식에서 이름 필드에 임의의 코드를 사용할 수 있습니다.

메시지 필드에 악성 코드를 입력하고 이메일을 통해 보낼 수 있는 위시리스트 공유 양식의 중요한 서버측 템플릿 삽입(SSTI) 취약점을 해결했습니다. 업데이트는 템플릿 지시문과 안전하지 않은 패턴을 차단하기 위해 입력 유효성 검사를 추가하므로 이제 잘못된 콘텐츠가 검색될 때 오류 메시지가 표시됩니다.

_AC-12730 - [GitHub 문제](https://github.com/magento/magento2/issues/39024) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/01cee3c3)_

#### 테마에 csp_whitelist.xml을 넣는 것은 작동하지 않으며 간헐적인 문제를 만듭니다

웹 사이트 영역당 CSP 허용 목록 캐싱을 구현했습니다.

_AC-13069 - [GitHub 문제](https://github.com/magento/magento2/issues/38933) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39672)_

#### Magento 2.4.7 p2로 업그레이드한 후 새로 업로드한 파일 미디어 갤러리를 볼 수 없음

이제 업그레이드 후 새로 업로드한 파일이 미디어 갤러리에 표시됩니다.
이전에는 Magento 2.4.7 p2로 업그레이드한 후 수동 동기화를 수행할 때까지 새로 업로드한 이미지가 미디어 갤러리에 표시되지 않았습니다.
AC-13262

_AC-13262 - [GitHub 문제](https://github.com/magento/magento2/issues/39275)_

#### 미디어 갤러리에 이름이 같지만 대/소문자가 다른 디렉터리에서 잘못된 이미지가 표시됨

이제 시스템에서는 미디어 갤러리의 특정 디렉터리에 업로드된 파일이 이름이 유사하지만 대/소문자가 다른 디렉터리에도 표시되는 문제를 해결합니다.

_AC-13489 - [GitHub 문제](https://github.com/magento/magento2/issues/39382) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39502)_

#### be에서 갤러리 이미지를 완전히 제거하면 범위 역할/유형(기본/작은/썸네일)이 설정되고 &quot;이전&quot; 역할/유형이 다시 추가된 후에 표시됩니다

시스템은 저장소 범위에서 예상대로 작동하며 이미지는 기본 범위에 따라 새로 추가된 이미지의 역할/유형을 상속합니다

_AC-13556 - [GitHub 문제](https://github.com/magento/magento2/issues/39481) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39680)_

#### 필드 값에 [이(가) 포함된 경우 관리 패널 ]의 `listing component`작은 버그`\` 필터를 누를 수 없습니다.

슬래시가 있는 페이지 제목을 필터링하면 시스템이 제대로 작동합니다(예: Magento\Store).

_AC-13661 - [GitHub 문제](https://github.com/magento/magento2/issues/39513) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39535)_

#### 오류: 제품 로드가 있는 관리 콘텐츠 페이지 빌더의 &quot;Magento_Catalog/js/validate-product&quot;에 대한 스크립트 오류

이 PR에서는 제품 조건으로 페이지 빌더를 편집할 때 catalogAddToCart에 대한 스크립트 오류를 수정합니다

_AC-13891 - [GitHub 문제](https://github.com/magento/magento2/issues/39604) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39677)_

#### 제품 위젯을 구성할 때 catalogAddToCart 스크립트 오류가 발생합니다.

페이지 빌더에서 &quot;조건 조합&quot;으로 제품 위젯을 구성할 때 발생하는 스크립트 오류를 수정했습니다. 이 문제는 프론트엔드 JS 파일이 누락되어 콘솔 오류가 발생했기 때문에 발생했습니다. 수정 후 콘솔 오류 없이 위젯이 올바르게 로드됩니다.

_AC-13892 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/528af81a)_

#### 동일한 식별자를 가진 위젯에서 선택 차단

이제 동일한 식별자 블록이 있는 경우 시스템이 위젯을 생성하는 동안 선택 블록을 올바르게 처리합니다

_AC-14132 - [GitHub 문제](https://github.com/magento/magento2/issues/39692) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39722)_

#### &quot;ID가 &quot;0&quot;인 CMS 페이지가 존재하지 않습니다.&quot; 로그 플러드

시스템은 관리자 사용자를 만든 후 새 페이지를 만들 때 예상대로 작동합니다. system.log에는 오류 메시지가 없습니다

_AC-14254 - [GitHub 문제](https://github.com/magento/magento2/issues/39743) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] 루트 쿼리 무한 루프

이 티켓은 동일한 요청 경로와 대상 경로를 사용하는 GraphQL 경로 쿼리가 무한 루프를 유발하여 결국 시간이 초과되는 문제를 해결했습니다.
2.4.9-alpha3에서 이제 쿼리가 루핑 대신 올바른 오류 응답을 반환합니다.

_AC-14269 - [GitHub 문제](https://github.com/magento/magento2/issues/39707) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 존재하지 않는 사이트 맵이 제품 이미지로 응답함

존재하지 않는 사이트 맵에 액세스하면 시스템이 수정됩니다. 응답: 404 찾을 수 없음

_AC-14295 - [GitHub 문제](https://github.com/magento/magento2/issues/39756) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40135)_

#### 카탈로그 링크 위젯이 잘못된 URL을 사용함

이제 시스템은 카탈로그 제품 링크 및 카탈로그 범주 링크를 추가한 후 위젯을 올바르게 처리하며 html 소스에도 올바른 URL이 표시됩니다

_AC-14437 - [GitHub 문제](https://github.com/magento/magento2/issues/39464) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39710)_

#### 테이블 접두사는 고려되지 않습니다.

이제 Adobe Commerce은 관리자에서 디자인 > 구성 테마 그리드를 로드할 때 데이터베이스 테이블 접두사를 올바르게 따릅니다. 이전에는 Adobe Commerce 2.4.8에서 app/etc/env.php에 테이블 접두사가 구성된 경우 콘텐츠 > 디자인 > 구성으로 이동하면 테이블 접두사를 고려하지 않고 테마 그리드가 렌더링되지 않아 오류가 발생했습니다.

_AC-14556 - [GitHub 문제](https://github.com/magento/magento2/issues/39847) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 유연성을 높이기 위해 상수 IMAGE_FILE_NAME_PATTERN을 공개 표시로 변경합니다.

GenerateRenditions.php의 상수 IMAGE_FILE_NAME_PATTERN은 개발자가 이미지 표현물로 작업할 때 보다 유연하게 사용할 수 있도록 공개되었습니다. 이 수정 사항은 전체 단위 및 통합 테스트 범위가 있는 Magento 2.4.9-alpha3에 포함되어 있습니다.

_AC-15338 - [GitHub 문제](https://github.com/magento/magento2/issues/39733) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 잘못된 배송 방법이 다중 배송의 주문 검토 페이지에 표시됩니다.

리뷰 주문 페이지에 잘못된 배송 비용(10 INR이 아닌 5 INR)이 표시되는 다중 배송 체크아웃 문제가 해결되었습니다. 업데이트는 각 주소에 대해 올바른 배송 금액이 표시되도록 합니다.

_AC-15664 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento 구성:show(또는 설정) 디자인/테마/theme_id 실패

구성이 있음에도 불구하고 design/theme/theme_id 경로에 대해 CLI 명령 bin/magento config:show 및 config:set이(가) 실패하는 문제가 해결되었습니다.
이제 명령이 성공적으로 실행되어 테마 ID를 오류 없이 보고 설정할 수 있습니다.

_AC-5915 - [GitHub 문제](https://github.com/magento/magento2/issues/35751) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64823f95)_

#### 상대적으로 작은 너비의 이미지를 업로드할 수 없습니다.

시스템에서 더 이상 이미지 크기를 이미지 높이까지 상대적으로 작은 너비로 조정하지 못합니다.

_ACP2E-3558 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 사용자에게 위젯 권한이 없는 경우 페이지 빌더의 제품 구성 요소가 작동하지 않음

수정 이전에는 권한이 없는 위젯에 액세스할 때 페이지에 일반 오류가 발생하고 &quot;로드 중&quot; GIF이 표시되었습니다. 이제 수정 후 모달 창에 &quot;죄송합니다. 이 콘텐츠를 볼 수 있는 권한이 필요합니다.&quot;가 표시됩니다. 메시지.

_ACP2E-3664 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 원격 저장소 경로 스타일 구성에 대한 구성 경로가 잘못되었습니다.

수정 후 원격 저장소 경로 스타일 구성을 설정하면 실제 AWS S3 경로 스타일 구성에 영향을 줍니다.

_ACP2E-3734 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### GraphQL에서 Page Builder 제품 위젯 순서 지정이 적용되지 않음

GraphQL &quot;경로&quot; 쿼리 응답이 페이지 빌더 제품 콘텐츠 유형 내에서 올바른 정렬 순서로 제품을 반환하지 않던 문제를 해결했습니다.

_ACP2E-3898 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### ICU 라이브러리 버전으로 인한 비영어 상점 가격 표시 문제

수정 후에는 히브리어(이스라엘) 로케일에 제품 가격이 올바르게 표시됩니다.

_ACP2E-3938 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 스토어 코드 삭제 디자인 구성 업데이트

구성 캐시가 제대로 새로 고쳐지지 않아 저장소 보기 코드를 업데이트하면 디자인 구성 설정이 지워지는 문제가 해결되었습니다.

_ACP2E-3941 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

#### 페이지 빌더 - 제품 조건 논리 문제(또는 논리가 더 적은 제품을 잘못 표시함)

이제 Page Builder 제품 위젯은 전역 범위의 속성이 &quot;모든 항목 일치&quot; 조건에 사용되면 올바른 결과를 반환합니다

_ACP2E-4096 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

#### 제품 캐러셀이 페이지 빌더에 잘못된 제품을 추가합니다.

수정 전에, 구성 가능한 제품은 하위 항목 중 하나라도 필터링 조건을 충족한 경우 PageBuilder 제품 캐러셀 목록에 자동으로 포함되었을 것입니다. 이제 수정 후 상위 제품은 하위 제품이 스스로 표시되지 않는 경우에만 포함됩니다.

_ACP2E-4341 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

#### 여러 카테고리가 카테고리 조건에 나열된 경우 제품 목록 위젯이 잘못된 결과를 반환합니다.

이제 &quot;카테고리가 중 하나임&quot; 조건에 나열된 여러 카테고리가 있을 때 &quot;카탈로그 제품 목록&quot; 위젯에 정확한 결과가 표시됩니다. 이전에는 목록의 첫 번째 범주만 처리되었습니다.

_ACP2E-4353 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [클라우드] 미디어 갤러리 폴더를 만들려면 새 미디어 갤러리에서 delete_folder 권한이 필요합니다. create_folder만 있는 역할은 폴더를 만들 수 없습니다.

이전에는 이 수정 사항이 구현되기 전에 콘텐츠 만들기 폴더 권한만 있는 관리자가 CMS 미디어 갤러리에서 폴더를 만들 수 없었습니다. 그러나 수정 후 미디어 갤러리의 콘텐츠 작성자는 이제 폴더 만들기 권한으로만 폴더를 만들 수 있습니다.

_ACP2E-4376 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

#### CMS 페이지 복제 [QUAN]

이 수정 이전에는 사용자 지정 레이아웃 업데이트가 있는 cms 페이지 복제가 실패했습니다. 이제 사용자 정의 레이아웃 업데이트가 있는 CMS 페이지를 오류 없이 복제할 수 있습니다.

_ACP2E-4449 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 고객/고객

#### 관리자가 CMS 페이지 콘텐츠를 통해 CustomerCustomAttribute 블록을 추가할 때 Storefront에 예외가 발생합니다.

CMS 페이지 콘텐츠를 통해 CustomerCustomAttribute 블록을 추가하면 상점 예외 문제가 발생하여 페이지가 로드되지 않는 문제가 해결되었습니다.
이제 Storefront가 정상적으로 표시되고 콘텐츠를 렌더링할 수 없을 때 의미 있는 메시지를 표시하므로 심각한 오류가 발생하지 않습니다.

_AC-11004_

#### 이제 Customers Online Admin Grid에는 사용자가 로그인한 다음 로그아웃한 다음 로그인할 때마다 중복 행이 표시됩니다

고객이 로그아웃했다가 다시 로그인할 때 Customers Now Online 관리 그리드에 중복 행이 표시되는 문제가 해결되었습니다.
이제 그리드는 중복 항목을 만드는 대신 최신 활동으로 기존 레코드를 업데이트하여 정확한 고객 세션 추적을 보장합니다.

_AC-11511 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/528af81a)_

#### Storefront의 DOB 속성에 대해 최소값 및 최대값 유효성 검사가 작동하지 않음

이 버그는 생년월일(DOB) 특성에 대한 최소 및 최대 날짜 유효성 검사가 상점 첫 화면에서 작동하지 않는 문제를 해결했습니다(관리에서는 작동했지만).
2.4.9-alpha3에서 이제 유효성 검사는 허용된 범위를 벗어나는 DOB로 고객을 저장하는 것을 올바르게 차단하며 오류 메시지를 표시합니다.

_AC-13535 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 고객으로 로그인 권한이 취소되는 동안 관리 패널의 경고 화면에 Ajax 401 오류 로드

이 버그는 고객 권한으로 취소된 로그인이 경고 팝업에 원시 HTML으로 Ajax 401 오류를 표시하던 문제를 해결했습니다.
수정 사항이 적용되면 이제 원시 HTML 대신 정상 경고 메시지가 올바르게 표시됩니다.
솔루션은 Magento 2.4.9-alpha3로 제공됩니다

_AC-15336 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

### 프레임워크

#### 비활성화된 모듈의 코드를 완료합니다.

이 가져오기 요청은 코드를 컴파일하기 전에 비활성화된 모듈을 이스케이프 처리합니다.

_AC-10933 - [GitHub 문제](https://github.com/magento/magento2/issues/38241) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39723)_

#### 사용자 지정 DB 트리거로 명령 setup:upgrade을(를) 실행할 때 오류 발생

사용자 지정 데이터베이스 트리거로 인해 설치:upgrade 중에 더 이상 오류가 발생하지 않습니다.
이전에는 사용자 지정 데이터베이스 트리거로 bin/magento setup:upgrade을(를) 실행하면(예: 스토어 테이블의 AFTER INSERT) 다음 오류가 발생할 수 있습니다.
&quot;경고: 357행의 vendor/magento/framework/Mview/View/Subscription.php에서 null 유형의 값에 대한 배열 오프셋에 액세스하려고 합니다.&quot;
AC-11487

_AC-11487 - [GitHub 문제](https://github.com/magento/magento2/issues/38481)_

#### [문제] 메서드의 시그니처를 인터페이스와 일치하도록 만들기

이제 getAttributes에 대한 메서드 시그니처가 인터페이스와 일관되어 메서드를 덮어쓸 때 오류가 발생하지 않습니다. 이전에는 메서드 시그니처가 일치하지 않아 getAttributes 메서드를 덮어쓰려고 할 때 오류가 발생했습니다.

_AC-11578 - [GitHub 문제](https://github.com/magento/magento2/issues/38501) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31955)_

#### 웹 사이트/그룹/저장소 엔터티 양식은 확장 특성에 대한 여러 값 양식 요소로 확장할 수 없습니다.

이 PR을 사용하면 값이 여러 개인 양식 요소가 웹 사이트/그룹/스토어 양식에 데이터를 제출할 수 있습니다.

_AC-11657 - [GitHub 문제](https://github.com/magento/magento2/issues/24070) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/24094)_

#### [문제] ui 구성 요소에 대한 유효성 검사 전자 메일 규칙 수정

이제 시스템에서 UI 구성 요소에 입력된 여러 이메일 주소를 올바르게 확인하여 각 이메일을 올바르게 트리밍하고 유효성을 검사합니다. 이전에는 시스템에서 이메일 주소를 트리밍하는 잘못된 방법을 사용했으며, 이로 인해 유효성 검사 오류가 발생할 수 있었습니다.

_AC-11719 - [GitHub 문제](https://github.com/magento/magento2/issues/38528) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33470)_

#### [문제] 범위 확인자 사용 제거

이 PR은 현재 저장소 대신 전역으로 관리 URL 설정을 확인합니다

_AC-11736 - [GitHub 문제](https://github.com/magento/magento2/issues/38566) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38554)_

#### [문제] 중복 메서드 제거

코드 품질: 기능을 추가하지 않고 상위 메서드만 호출한 AsynchronousOperations 및 Sales 구성 요소에서 중복 메서드를 제거하여 코드 유지 관리를 개선했습니다.

_AC-11915 - [GitHub 문제](https://github.com/magento/magento2/issues/29748) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml 템플릿이 PHP 8.2에 적합하지 않습니다.

이 끌어오기 요청은 Php 8.x에서와 같이 null 머리글로 생성된 CMS 페이지가 null을 trim()에 전달하면서 예외 발생: 더 이상 사용되지 않는 기능: trim(): 유형 문자열의 매개 변수 #1($string)에 null 전달 시 문제를 해결합니다.

_AC-12856 - [GitHub 문제](https://github.com/magento/magento2/issues/39092) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39398)_

#### 필드 항목 아래에 주석이 포함된 etc/adminhtml/system.xml 파일에서 xsd 유효성 검사가 실패합니다.

이 PR은 설명 노드에 대한 phpstorm의 XML 스키마 정의를 수정합니다

_AC-12945 - [GitHub 문제](https://github.com/magento/magento2/issues/39148) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39867)_

#### 기본 Nginx 구성을 통한 설정 라우트를 통한 Magento 버전 노출

시스템이 현재 예상대로 작동하며 사이트에서 실행 중인 Magento의 정확한 버전은 노출하지 않습니다

_AC-13205 - [GitHub 문제](https://github.com/magento/magento2/issues/39227) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39228)_

#### [문제] 명명된 매개 변수로 개체 인수 압축 풀기

이제 시스템은 명명된 매개 변수로 배열을 압축 해제하는 PHP 8.1 기능을 사용하므로, array_values 호출이 필요 없고 전체 성능이 향상될 수 있습니다. 이전에는 시스템에 필요한 array_values가 개체 인수의 압축을 푸는 를 호출했습니다.

_AC-13210 - [GitHub 문제](https://github.com/magento/magento2/issues/39233) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37411)_

#### [문제] 리팩터링 견적 주소 유효성 검사 방법

이 PR에는 doValidate 메서드에 대한 가독성 개선 사항이 포함되어 있습니다.

_AC-13214 - [GitHub 문제](https://github.com/magento/magento2/issues/38230) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38219)_

#### Magento 옵션 —cli를 실행할 때 magento-init-params가 사용되지 않음

이제 CLI 명령을 실행할 때 —magento-init-params 옵션이 사용됩니다.
이전에는 —magento-init-params 를 CLI 명령에 전달해도 MAGE_MODE 와 같은 매개 변수에는 영향을 주지 않았습니다.
AC-13231

_AC-13231 - [GitHub 문제](https://github.com/magento/magento2/issues/39248) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue 잘못된 형식 선언

이제 시스템에서 입력 매개 변수 $value를 getItemsByColumnValue 함수에서 배열이 아닌 기본 형식으로 올바르게 정의하여 함수가 예상 컬렉션을 반환하도록 합니다. 이전에는 단일 값을 갖는 배열이 입력 매개 변수로 사용되면 함수가 null을 반환하고 IDE가 이를 오류로 표시했습니다.

_AC-13240 - [GitHub 문제](https://github.com/magento/magento2/issues/33070) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33120)_

#### Lock Provider에 파일 스토리지를 사용하면 정리 작업 없이 파일 디렉토리가 계속 늘어납니다.

이 가져오기 요청으로 인해 하루에 한 번 실행되는 새 cronjob이 도입되며 지난 24시간 동안 수정되지 않았으므로 안전하게 제거할 수 있는 잠금 파일을 검색합니다. 이렇게 하면 잠금 파일 디렉터리의 내용이 제어됩니다.
이 cronjob은 잠금 공급자가 파일을 사용하도록 구성된 경우에만 실행되며, 데이터베이스(기본값, Zookeeper 또는 캐시)가 사용되는 경우에는 실행되지 않습니다.

_AC-13367 - [GitHub 문제](https://github.com/magento/magento2/issues/39369) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39372)_

#### [문제] 정리: 메서드 호출에서 void 반환 값을 사용하지 마십시오.

이 PR은 사소한 정리를 수행합니다. 때때로 아무 것도 반환하지 않는 메서드(void)를 호출한 다음 해당 결과 값을 사용합니다. 그건 정말 필요없어.

_AC-13664 - [GitHub 문제](https://github.com/magento/magento2/issues/39524) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39516)_

#### Magento 2.4.7 다중 스토어 구현에서 FPC와 연결된 캐시 키

다중 저장소 설정의 FPC(전체 페이지 캐시) 캐시 키에 MAGE_RUN_CODE 및 MAGE_RUN_TYPE이 포함되지 않아 이전 버전과 비교하여 캐시 키 동작이 일치하지 않는 문제가 해결되었습니다. 이제 캐시 키에 저장소 컨텍스트가 올바르게 포함되어 저장소 간에 캐시가 적절하게 격리됩니다.

_AC-13719 - [GitHub 문제](https://github.com/magento/magento2/issues/39456) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ae6f305b)_

#### [문제] [PHPDOC] Magento\Framework\Message\ManagerInterface에 대한 잘못된 phpdoc 수정

이 PR은 \Magento\Framework\Message\ManagerInterface에 대한 잘못된 phpdoc을 수정하고 \Magento\Framework\Message\Manager에서 모든 중복 phpdoc을 제거합니다(inheritdoc 구문 사용).

_AC-14312 - [GitHub 문제](https://github.com/magento/magento2/issues/39593) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39153)_

#### 엄청난 수의 업데이트가 있는 고객의 경우 부분 인덱싱이 작동하지 않음

이제 부분 인덱싱은 많은 수의 업데이트가 있는 고객에게 작동합니다.
이전에는 changeLog 테이블에서 version_id 열의 최대값에 도달하여 색인 업데이트가 중지되었습니다.
AC-14424

_AC-14424 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8에서는 시맨틱 버전 관리를 따르지 않는 개발 패키지를 사용합니다

Magento 2.4.8을 사용하려면 PHP 8.4 호환성을 위해 pdepende/pdepende 및 phpmd/phpmd(3.x-dev) 개발 버전이 필요합니다.
이러한 개발 버전은 SemVer 호환 패키지를 예상하는 타사 도구와 충돌하여 일부 업그레이드를 방지합니다.
임시 해결 방법은 composer.json의 개발 버전(예: &quot;3.x-dev as 3.99.0&quot;)에 별칭을 지정하여 시맨틱 버전 관리를 충족하면서 호환성을 허용하는 것입니다.
이를 통해 PHP 8.4를 지원하고 안정적인 릴리스가 제공될 때까지 충돌을 피할 수 있습니다.

_AC-14519 - [GitHub 문제](https://github.com/magento/magento2/issues/39796)_

#### MView 메커니즘은 트리거 실행 시 오류를 자동으로 무시합니다.

이제 MView 메커니즘이 트리거 실행 시 오류를 올바르게 보고합니다.
이전에는 트리거 실행 중 오류가 자동으로 무시되어 알림 없이 색인 업데이트가 누락될 수 있었습니다.
AC-14567

_AC-14567 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ae6f305b)_

#### [문제] 레이아웃 XML 병합 로드 중에 불필요한 예외를 많이 방지하십시오

이 PR에서는 로드할 새 함수(B/C 컴퓨터의 경우 보호된 _loadXmlString을 덮어쓰지 않음)를 소개하고 예외를 throw하지 않습니다

_AC-14580 - [GitHub 문제](https://github.com/magento/magento2/issues/39877) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37570)_

#### [문제] 모듈 Vault Graph Ql에서 생성자 속성 프로모션을 사용합니다.

이 PR은 생성자 속성을 VaultGraphQl 모듈의 속성 프로모션으로 대체합니다

_AC-14616 - [GitHub 문제](https://github.com/magento/magento2/issues/39900) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36996)_

#### [문제] 모듈 프론트엔드 레이아웃에 대한 코드 중복성을 제거했습니다.

이 PR은 Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter 및 Magento_Sitemap 모듈 프론트엔드 레이아웃에 대한 테마 레이아웃에 대한 코드 중복을 제거합니다.

_AC-14625 - [GitHub 문제](https://github.com/magento/magento2/issues/30673) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30644)_

#### [문제] 생성자를 `CommandListInterface` API의 일부로 포함하고 인라인 설명서를 확장합니다.

이 PR 업데이트는 Magento\Framework\Console\CommandList 을 API로 표시하고 더 나은 확장성을 위해 CommandListInterface에 생성자를 도입합니다. 또한 인라인 설명서를 개선하여 개발자가 콘솔 명령을 확장할 때 명확성과 유지 관리 기능을 향상시킬 수 있습니다.

_AC-14680 - [GitHub 문제](https://github.com/magento/magento2/issues/31102) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37901)_

#### [문제] Microsoft IIS와 관련된 코드 제거

이 PR은 Microsoft Windows OS가 지원되지 않는다는 Magento 시스템 요구 사항 문서에 따라 Microsoft IIS와 관련된 코드를 정리합니다

_AC-14702 - [GitHub 문제](https://github.com/magento/magento2/issues/39910) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js 구문 오류

시스템 돋보기 기능은 이전에 작동했던 방식으로 계속 작동해야 하며 magnifierOptions를 전역 범위에서 사용할 수 없어야 합니다

_AC-14722 - [GitHub 문제](https://github.com/magento/magento2/issues/36200) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI 명령의 Verbose 모드 백업

이제 `setup:db:status` CLI 명령이 verbose 모드를 지원합니다.
기존에는 업그레이드에 필요한 데이터베이스 변경을 이해하는 것이 어려웠다. 이제 `bin/magento setup:db:status -v`을(를) 실행하면 스키마 및 데이터 차이에 대한 자세한 정보가 제공됩니다.
AC-14807

_AC-14807 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### tls 및 2.4.8을 사용하여 SMTP 메일 보내기

TLS를 사용한 SMTP 이메일 전송이 이제 예상대로 작동합니다.
이전에는 TLS를 사용하여 SMTP를 통해 전자 메일을 보내면 오류 :1408F10B:SSL 루틴:ssl3_get_record:잘못된 버전 번호가 발생했습니다.
AC-14883

_AC-14883 - [GitHub 문제](https://github.com/magento/magento2/issues/39947) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8b453942) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/d3ea191d)_

#### [문제] 정적 콘텐츠 배포의 동시성 문제 해결

이 PR은 부모와 함께 테마를 정의하는 방법에 따라 여러 동시 프로세스가 회전하면서 동일한 테마 패키지를 처리하는 버그를 수정합니다.

_AC-14944 - [GitHub 문제](https://github.com/magento/magento2/issues/39990) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39954)_

#### [문제] PHP 버전 &lt; 8.1의 레거시 호환성 코드 제거

이 가져오기 요청은 PHP &lt;8.1에서 실행되도록 디자인된 코드를 제거합니다.
또한 모든 PHP 버전에서 사용할 수 있으므로 PHP_VERSION_ID 연락처 가용성에 대한 검사를 제거했습니다

_AC-14971 - [GitHub 문제](https://github.com/magento/magento2/issues/39891) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39882)_

#### 로그인 시 FPC가 작동하지 않음

이제 로그인한 고객에 대해 FPC(전체 페이지 캐시)가 올바르게 작동합니다.
이전에는 로그인 후 홈페이지가 캐시에서 로드되지 않고 x-magento-cache-debug 헤더에서 HIT 대신 MISS를 표시했습니다.
AC-14999

_AC-14999 - [GitHub 문제](https://github.com/magento/magento2/issues/40007)_

#### 향상된 정적 분석 지원을 위해 특정 php 클래스에 제네릭 형식을 추가합니다.

이제 시스템에서는 제네릭 형식 정의를 사용하여 메서드 호출이 반환하는 정확한 클래스로 해석하여 이 문제를 크게 개선합니다

_AC-15013 - [GitHub 문제](https://github.com/magento/magento2/issues/40017) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40119)_

#### [문제] SchemaBuilder 처리 오류 개선

이 PR은 db 스키마의 오류 메시지 처리를 개선합니다. 많은 디버깅 없이 문제를 식별하는 데 도움이 됩니다.

_AC-15020 - [GitHub 문제](https://github.com/magento/magento2/issues/39816) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39799)_

#### Rest API: null에서 멤버 함수 getVideoProvider()를 호출합니다.

구성 가능한 제품 하위 API를 호출하면 하위 제품에 YouTube 비디오만 있고 다른 이미지는 없는 경우 500 내부 서버 오류가 반환되던 문제를 수정했습니다.
ExternalVideoEntryConverter의 null 참조로 인해 오류가 발생했습니다.
이제 API는 오류를 발생시키지 않고, 외부 비디오 데이터를 포함한 미디어 갤러리 항목이 있는 하위 제품을 올바르게 반환합니다.
이렇게 하면 REST API를 통해 하위 제품에 대한 모든 미디어 유형을 적절하게 검색할 수 있습니다.

_AC-15046 - [GitHub 문제](https://github.com/magento/magento2/issues/40021)_

#### [W3C] 쿠키 스크립트 태그 선언에서 text/javascript 제거

이 PR은 HTML5 준수를 위해 쿠키 스크립트 태그에서 불필요한 type=&quot;text/javascript&quot; 속성을 제거했습니다.

_AC-15061 - [GitHub 문제](https://github.com/magento/magento2/issues/39982) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39983)_

#### [문제] PHPDoc 댓글의 몇 가지 오타 수정

이 PR은 phpdoc에 있는 몇 가지 오타를 수정합니다

_AC-15075 - [GitHub 문제](https://github.com/magento/magento2/issues/40042) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38809)_

#### [문제] 구문 호출에서 sprintf 사용을 제거하십시오.

이 PR은 Magento 코어의 구 함수 호출에서 sprintf의 사용을 제거합니다.

_AC-15183 - [GitHub 문제](https://github.com/magento/magento2/issues/40050) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40033)_

#### 활성 응용 프로그램 잠금이 있는 다중 스레드 인덱서에서 잘못된 모든 인덱스를 다시 인덱싱할 수 없습니다.

이 문제는 use_application_lock이 활성화된 경우 다중 스레드 인덱서 오류를 해결했습니다.
이전에는 병렬 처리 중에 DB 잠금이 손실되어 인덱서가 &quot;작동 중&quot; 상태로 유지되며 SQL 오류가 발생합니다(테이블을 찾을 수 없음).
Magento 2.4.9-alpha3에서 이 수정 사항을 사용하면 응용 프로그램 잠금이 활성화된 상태에서 인덱서가 올바르게 다시 인덱싱됩니다.

_AC-15270 - [GitHub 문제](https://github.com/magento/magento2/issues/40102) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### Magento\Framework\Escaper의 반환 형식이 명확하지 않거나 잘못되었습니다.

시스템은 레벨 5에서 phpstan을 사용하여 정적 분석을 수행할 때 이스케이프 메서드 형식을 허용합니다

_AC-15272 - [GitHub 문제](https://github.com/magento/magento2/issues/40012) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40114)_

#### [문제] 큐별 구성이 기본 최대 메시지 값을 초과하도록 허용합니다.

이제 시스템에서 대기열별 구성이 기본 최대 메시지 값을 초과하도록 허용합니다.

_AC-15284 - [GitHub 문제](https://github.com/magento/magento2/issues/40121) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40110)_

#### [문제] 바니시를 사용할 때 쿼리가 같은 동일한 페이지에 대한 캐시 fpc가 중복되었습니다.

이 PR은 쿼리 매개 변수 순서를 표준화하여 Varnish를 사용할 때 중복된 전체 페이지 캐시 항목을 수정하여 동일한 요청에 대해 일관된 캐시 키를 보장합니다.
다른 시퀀스에서 동일한 매개 변수를 사용하는 URL의 캐시 적중률 및 성능을 개선합니다.

_AC-15325 - [GitHub 문제](https://github.com/magento/magento2/issues/39706) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39704)_

#### 커뮤니티 테마에는 Commerce 에디션 모듈에 대한 리소스가 포함되어 있습니다

커뮤니티 테마에서 Commerce 전용 스타일 리소스를 해당 모듈 디렉터리로 재배치하여 제거했습니다. 이렇게 하면 사용하지 않는 CSS가 Community Edition에 번들로 제공되지 않으므로 불필요한 페이로드를 줄이고 Commerce 모듈이 활성화될 때 적절한 스타일을 하는 동시에 데드 스타일 규칙을 제거할 수 있습니다.

_AC-15347 - [GitHub 문제](https://github.com/magento/magento2/issues/21446) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9bcd880a)_

#### [문제] Url에 저장소 코드 추가는 글로벌이어야 합니다.

이 PR은 &quot;Add Store Code to Url&quot; 설정이 코어 코드의 전역 범위를 사용하여 검색되도록 함으로써 문제를 해결합니다

_AC-15365 - [GitHub 문제](https://github.com/magento/magento2/issues/40069) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40065)_

#### [문제] 로그 선언되지 않은 플러그인은 비활성화되지 않은 경우에만

이 PR은 실제로 선언되지 않고 사용되지 않는 플러그인을 수정합니다(활성화 및 누락된 인스턴스).

_AC-15386 - [GitHub 문제](https://github.com/magento/magento2/issues/40086) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40081)_

#### [문제] 작은 정리, 배열에서 중복 키 제거됨

이제 시스템에서 작은 정리가 수행되었으며 Array와 관련된 오류가 없습니다. 값이 &#39;Weight(이상)&#39;인 중복 키가 2개 있습니다.

_AC-15414 - [GitHub 문제](https://github.com/magento/magento2/issues/39851) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework 버전 103.0.8-p2: 존재하지 않는 메서드를 호출하는 EmailMessage 클래스

이제 EmailMessage 클래스가 이메일 본문 검색을 올바르게 처리합니다.
이전에는 magento/framework 버전 103.0.8-p2가 있는 Magento 2.4.8-p2에서 Magento\Framework\Mail\EmailMessage 클래스에서 Symfony 메일 메시지 개체에 존재하지 않는 메서드(getTextBody)를 호출하려고 했습니다. 이로 인해 서드파티 모듈 또는 사용자 정의가 이메일 처리에 이 방법을 사용할 때 오류가 발생했습니다.
이제 EmailMessage 클래스는 더 이상 정의되지 않은 메서드를 호출하지 않으므로 이러한 오류가 발생하지 않습니다. AC-15446

_AC-15446 - [GitHub 문제](https://github.com/magento/magento2/issues/40170) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/059fd469) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] 데이터/스키마 패치 getAliases()로 인해 `setup:upgrade` 중 오류가 발생합니다.

getAliases()로 인해 :upgrade 설정 중에 오류가 발생합니다. 이 PR은 이를 수정합니다

_AC-15559 - [GitHub 문제](https://github.com/magento/magento2/issues/31396) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38239)_

#### 작업에 대한 잘못된 색상 혼합

_AC-15614 - [GitHub 문제](https://github.com/magento/magento2/issues/40138) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/44329e9d)_

#### [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

이 PR은 \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()에 대한 PHPDoc를 업데이트하여 $alias 매개 변수가 문자열 외에 null일 수 있음을 올바르게 반영합니다. 이렇게 하면 레벨 5+에서 PHPStan 문제가 해결되고 코드 품질 도구 호환성이 향상됩니다.

_AC-15626 - [GitHub 문제](https://github.com/magento/magento2/issues/39598) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39581)_

#### urlrewrite 모듈에서 잘못된 색상 혼합

_AC-15647 - [GitHub 문제](https://github.com/magento/magento2/issues/40189) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/44329e9d)_

#### `\Magento\Framework\Escaper::escapeScriptIdentifiers`에서 조건이 충족되지 않음

\Magento\Framework\Escaper::escapeScriptIdentifiers에서 연결할 수 없는 조건을 수정했습니다. false에 대한 검사를 null로 바꾸고, preg_replace 반환 값에 맞추고, 기능에 영향을 주지 않고 코드 정확도를 개선했습니다.

_AC-15667 - [GitHub 문제](https://github.com/magento/magento2/issues/40195) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/cc0ec250)_

#### Vannish 7.3(최신 버전) - 기본 범주의 하위 범주 링크/옵션이 스토어 초기 홈 페이지에 표시되지 않음

Varnish 7.3을 사용할 때 상점 홈 페이지의 하위 범주 링크가 누락된 것이 Magento 코드 결함이 아닌 ESI 요청 처리 및 서버 구성으로 인해 발생했음을 확인했습니다. 이 문제는 코어 코드 변경이 필요하지 않은 권장 Varnish 구성 조정을 통해 해결됩니다.

_AC-15674 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/9a62604c)_

#### [문제] `cache_invalidate` 로그에 추가 디버그 데이터 추가

이 PR은 전체 캐시 삭제에 대한 요청 컨텍스트 및 스택 추적을 포함하도록 cache_invalidate 로그를 개선하여 디버깅 및 가시성을 개선했습니다.
이렇게 하면 기존 기능을 변경하지 않고 예기치 않은 전체 캐시 무효화의 소스를 식별하는 데 도움이 됩니다.

_AC-15719 - [GitHub 문제](https://github.com/magento/magento2/issues/40204) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40196)_

#### [문제] 작성기의 자동 로더 제외 목록이 약간 개선되었습니다.

이 PR은 Composer 자동 로더 제외를 세분하여 테스트 클래스를 건너뛰고 불필요한 클래스 맵 항목을 줄이고 PSR-4 경고를 방지합니다.

_AC-15743 - [GitHub 문제](https://github.com/magento/magento2/issues/40109) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40107)_

#### [문제] `db_schema.xml`을(를) 사용한 `comment=""` 선언이 가동 중지 시간이 없는 배포를 중단하지 않도록 합니다.

이제 시스템은 comment=&quot;&quot;인 db_schema.xml 선언이 중단 없는 배포를 중단하지 않도록 합니다

_AC-15980 - [GitHub 문제](https://github.com/magento/magento2/issues/40254) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40242)_

#### `\Magento\Framework\Filesystem\Glob::glob(...)` 캐시를 지울 수 없습니다.

이 PR 업데이트에서는 \Magento\Framework\Filesystem\Glob에서 사용되는 내부 정적 캐시를 지워 파일 구조가 변경될 때 새롭고 정확한 결과를 얻을 수 있는 방법을 도입했습니다. 특히 glob 결과가 최신 상태를 유지해야 하는 테스트 시나리오 및 장기 실행 프로세스에서 안정성과 개발자 경험을 향상시킵니다.

_AC-15989 - [GitHub 문제](https://github.com/magento/magento2/issues/35741) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35742)_

#### ReadME 리더 링크 URL에는 영구 리디렉션이 있습니다.

영구적으로 리디렉션되고 만료된 URL을 올바른 작동 링크로 대체하여 README Leaders 링크를 업데이트했습니다. 이렇게 하면 기여자 및 유지 관리자 페이지가 제대로 열립니다.

_AC-16046 - [GitHub 문제](https://github.com/magento/magento2/issues/40292) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

적절한 배열 정의를 허용하도록 속성 컬렉션의 joinLeft()에 대한 PHPDoc 주석을 수정하여 코드 수정 및 PHPStan과 같은 도구와의 호환성을 개선했습니다.

_AC-16187 - [GitHub 문제](https://github.com/magento/magento2/issues/40354) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39155)_

#### 단일 명령 장애가 후속 CLI 명령의 실행을 중지하지 않고 오류(파일 또는 stderr)를 기록하는지 확인합니다.

이제 시스템에서 단일 명령 실패가 후속 CLI 명령의 실행을 중지하지 않고 오류(파일 또는 stderr)를 기록하는지 확인합니다.

_AC-16244 - [GitHub 문제](https://github.com/magento/magento2/issues/40006) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40063)_

#### [문제] PageCache 커널의 $maxAge에 int 형식 추가

이 PR은 PageCache 커널의 $maxAge 매개 변수를 정수로 엄격하게 입력하여 형식 안전성을 높이고 캐시 처리에서 PHPStan/정적 분석 오류를 방지합니다.

_AC-16313 - [GitHub 문제](https://github.com/magento/magento2/issues/40438) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36600)_

#### 장바구니에 추가 이벤트: 빈 가격

장바구니에 추가 프로세스 중에 checkout_cart_product_add_after 이벤트 관찰자에서 제품 가격이 null로 반환되던 문제를 해결했습니다.
이제 기본 가격 및 관련 가격 값이 올바르게 검색되므로 관찰자 및 사용자 정의 구현에 정확한 데이터를 사용할 수 있습니다.

_AC-5966 - [GitHub 문제](https://github.com/magento/magento2/issues/35638) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1 유형 버그 수정

이제 엄격한 처리 모드가 활성화되지 않았거나 제품 정보를 사용할 수 있을 때 연결된 제품이 false 대신 빈 배열로 초기화됩니다. 이러한 변경은 후속 논리 처리 관련 제품이 일관되게 동작하여 제품 준비 프로세스의 안정성과 예측 가능성을 향상시킵니다.

_AC-6017 - [GitHub 문제](https://github.com/magento/magento2/issues/35808) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35842)_

#### &#39;Magento\Customer\Api\Data\GroupInterface&#39; 형식이 필요합니다. &#39;Magento\Customer\Model\Group&#39;를 찾았습니다.

GroupFactory를 사용하여 GroupRepositoryInterface를 통해 고객 그룹을 저장하면 유형 오류가 발생하는 문제가 해결되었습니다.
이전에는 리포지토리에서 GroupInterface를 예상했지만 그룹 모델 인스턴스가 전달되어 치명적인 오류가 발생했습니다.
이제 적절한 인터페이스 구현을 보장하여 저장소를 통해 고객 그룹을 성공적으로 저장할 수 있습니다.
이렇게 하면 고객 그룹을 프로그래밍 방식으로 만들거나 업데이트할 때 IDE 경고와 런타임 오류가 해결됩니다.

_AC-6909 - [GitHub 문제](https://github.com/magento/magento2/issues/36269)_

#### 크레딧 메모의 필드 유효성 검사

필수 사용자 정의 필드가 채워진 후에도 대변 메모 페이지의 필드 유효성 검사로 인해 제출할 수 없는 문제를 해결했습니다.
이제 유효성 검사가 올바르게 작동하고 모든 필수 필드가 완료되면 제출 버튼이 활성화됩니다.

_AC-8308 - [GitHub 문제](https://github.com/magento/magento2/issues/37182) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64823f95)_

#### [문제] 프레임워크에서 금지된 `@author` 태그를 제거합니다(3부).

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8343 - [GitHub 문제](https://github.com/magento/magento2/issues/37270) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37020)_

#### [문제] 친구 그래프 보내기 모듈에서 생성자 속성 프로모션을 사용합니다.

이제 시스템에서 &quot;친구 보내기&quot; GraphQL 모듈의 생성자 속성 프로모션을 사용하여 코드 가독성을 높이고 복잡성을 줄입니다. 이전에는 모듈에서 많은 줄을 사용하는 속성을 사용했기 때문에 코드가 더 복잡해지고 가독성이 감소했습니다.

_AC-8346 - [GitHub 문제](https://github.com/magento/magento2/issues/37235) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37197)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8349 - [GitHub 문제](https://github.com/magento/magento2/issues/37266) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37016)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8350 - [GitHub 문제](https://github.com/magento/magento2/issues/37265) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37015)_

#### [문제] `@author`에서 금지된 `Magento_Downloadable` 태그를 제거하십시오.

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8355 - [GitHub 문제](https://github.com/magento/magento2/issues/37251) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37001)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 코드 품질 및 일관성을 향상시켜 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8358 - [GitHub 문제](https://github.com/magento/magento2/issues/37264) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37014)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8359 - [GitHub 문제](https://github.com/magento/magento2/issues/37262) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37012)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8360 - [GitHub 문제](https://github.com/magento/magento2/issues/37261) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37011)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 보다 깨끗하고 표준화된 코드를 만들어 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8361 - [GitHub 문제](https://github.com/magento/magento2/issues/37260) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37010)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8362 - [GitHub 문제](https://github.com/magento/magento2/issues/37259) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37009)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8363 - [GitHub 문제](https://github.com/magento/magento2/issues/37258) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37008)_

#### [문제] `@author` 및 `Magento_Backup`에서 금지된 `Magento_Bundle` 태그를 제거합니다.

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8367 - [GitHub 문제](https://github.com/magento/magento2/issues/37244) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36979)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8375 - [GitHub 문제](https://github.com/magento/magento2/issues/37257) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37007)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8376 - [GitHub 문제](https://github.com/magento/magento2/issues/37256) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37006)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8400 - [GitHub 문제](https://github.com/magento/magento2/issues/37254) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37004)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8401 - [GitHub 문제](https://github.com/magento/magento2/issues/37255) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37005)_

#### [문제] 서비스 URL 생성의 확장성 개선

이제 시스템에서 플러그인을 통해 서비스 URL 생성 기능을 사용자 정의할 수 있으므로, 보다 유지 관리 가능한 수정 접근 방식을 제안할 수 있습니다. 이전에는, 이 기능의 사용자 지정이 환경 설정을 통해 이루어졌는데, 이는 효율적이거나 유지 관리되지 않았을 수 있습니다.

_AC-8813 - [GitHub 문제](https://github.com/magento/magento2/issues/37404) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37403)_

#### [문제] catalogsearch에서 변수 이름 수정

이제 시스템에서 검색 엔진 모듈에서 변수의 이름을 올바르게 지정하므로 코드 명확성과 유지 관리가 향상됩니다. 이전에는 검색 엔진 모듈에 관련 없는 변수 이름 $defaultCountry가 사용되면서 혼동이 발생하기도 했습니다.

_AC-9215 - [GitHub 문제](https://github.com/magento/magento2/issues/37810) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33533)_

#### 환경 변수를 통해 allow_parallel_generation을 설정해야 합니다.

수정 후 &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; 환경 변수를 사용하여 &quot;allow_parallel_generation&quot; 구성을 설정할 수 있습니다.

_ACP2E-3673 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

#### [클라우드] Magento 2에서 db_schema.xml 파일을 사용하여 테이블 열 유형을 Int에서 Decimal로 변경하면 오류가 발생합니다.

열 데이터 형식 변경이 제대로 작동하지 않습니다. 이전에는 &#39;id&#39; 특성이 허용되지 않는다는 오류가 발생했습니다.

_ACP2E-3709 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### Adobe의 새로운 통화(XCG) 지원

카리브해 길더(XCG)가 통화 목록에 추가됩니다.

_ACP2E-3790 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

#### 새로운 유효성 검사로 인한 업그레이드 2.4.7-p5 문제

SchemaBuilder 클래스에서 스키마를 만들거나 업데이트하는 동안 정의되지 않은 배열 키 &quot;column&quot;으로 인해 충돌이 발생하는 문제를 해결했습니다. 이 문제는 &quot;열&quot; 키를 포함하지 않은 테이블 데이터를 처리할 때 발생했습니다.

_ACP2E-3871 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

#### 잘못된 S3 액세스 키로 인해 [QUANS]서버 문제가 발생할 수 있습니다.

잘못된 AWS S3 자격 증명으로 인해 더 이상 페이지가 상점 앞에 무한히 로드되지 않습니다.

_ACP2E-3890 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] 축소 js가 작동하지 않음

이제 JS 축소가 활성화되면 mage/backend/tabs.min.j, jquery/jquery.validate.min.js 및 Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js JS 파일이 완전하고 올바르게 축소됩니다. 따라서 페이지 빌더 CSS 클래스 필드 유효성 검사는 예상대로 작동합니다.

_ACP2E-3925 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4 사용 중단 오류: Adobe Commerce 2.4.8로 업그레이드한 후 E_USER_ERROR

*릴리스 정보가 필요하지 않습니다*
고객 응대 시나리오는 수정 사항의 영향을 받지 않습니다.

_ACP2E-3963 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron 작업이 데이터베이스 테이블을 지우지 않아 Galera 충돌로 인해 중단됨

많은 삭제 작업을 방지하기 위해 변경 로그 테이블 정리가 이제 일괄적으로 실행되고 있습니다.

_ACP2E-3995 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### 축소되지 않은 JS는 때로 &#39;js 축소 활성화&#39;를 무시하면서 로드됩니다.

수정 전에 축소를 활성화했더라도 &quot;min&quot; 접두사 없이 일부 JS 파일이 요청되어 404 상태 코드가 발생합니다. 수정 후 축소가 활성화되면 축소되지 않은 JS 리소스가 요청되지 않습니다.

_ACP2E-4058 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 사용자 지정 속성 그룹의 날짜 속성이 관리자에 날짜 선택기를 표시하지 못함

사용자 지정 속성 그룹에 할당할 때 날짜 속성에 대한 달력 팝업이 화면 밖으로 표시되는 문제를 해결했습니다.

_ACP2E-4060 - [GitHub 문제](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 프로덕션 ACL 권한 검사로 인해 성능이 저하되었습니다. populateAcl 메서드가 병목 지점입니다.

최적화된 ACL 규칙 처리

_ACP2E-4114 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/98f028ab)_

#### AC-15867 + ACP2E-4296 및 SCD compact를 사용하는 최신 버전에서 체크 아웃이 로드되지 않음

수정 전에 헤드 섹션을 통해 사용자 지정 javascript를 로드하면 문제가 발생할 수 있습니다. 새 설정이 도입된 후에는 이러한 스크립트를 자동으로 재정의할 수 있으므로 Magento 2 프레임워크와의 호환성을 높일 수 있습니다.

_ACP2E-4319 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1c547060)_

#### 사용 중단 경고: moment.updateLocale(localeName, config)을 사용하여 기존 로케일을 변경합니다. moment.defineLocale(localeName, config)

수정 전에 브라우저 콘솔에서 더 이상 사용되지 않는 경고가 발생했습니다. 이제, 수정 후, 더 이상 그러한 경고가 표시되지 않습니다.

_ACP2E-4338 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2687b487)_

#### MariaDB 10.11과의 비호환성

이전에는 MariaDB 10.11을 사용할 때 최신 Magento 2 버전을 설치하지 못해 설정 프로세스가 완료되지 못했습니다. 설치 중에 MariaDB 10.11.x를 지원하도록 데이터베이스 호환성 처리를 업데이트하여 이 문제를 해결했습니다.

_ACP2E-4367 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

### 프레임워크, 검색

#### 단일 가격 범주에 대한 Opensearch 2.19.1 illegal_argument_exception

Opensearch는 더 이상 가격이 같은 모든 제품을 포함하는 범주에 illegal_argument_exception을 throw하지 않습니다. 이전에는 이 예외 &quot;[from] 매개 변수는 음수일 수 없습니다.&quot;가 있었습니다.

_ACP2E-3896 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### GraphQL에서 주문하면 잘못된 배송 방법으로 성공합니다

비활성화 또는 잘못된 배송 방법을 사용하여 GraphQL을 통해 주문을 할 수 있는 문제를 해결했습니다.
이제 시스템에서 선택한 배송 방법을 확인하고 사용할 수 없는 경우 오류를 반환하여 주문이 생성되지 않도록 합니다.

_AC-10472 - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38268) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### GraphQl 쿼리를 실행할 때 예외가 throw됨

GraphQL 쿼리에서 잘못된 정렬 매개 변수로 인해 예외가 발생하는 문제가 해결되었습니다. 수정 후 오류 또는 예외 로그를 생성하지 않고 쿼리가 성공적으로 실행됩니다.

_AC-14835 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### custom_attributesV2를 포함한 AddProductsToCart 돌연변이를 통해 기프트 카드 제품을 장바구니에 추가할 때 내부 서버 오류 발생

기프트 카드(및 유사한 사용자 지정 옵션) 제품을 custom_attributesV2와 함께 GraphQL을 통해 장바구니에 추가할 때 트리거되는 내부 서버 오류를 해결했습니다. 이 수정 사항은 복잡한 속성 값을 제대로 처리하므로 오류 없이 제품을 추가할 수 있습니다.

_AC-15856 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7fa400a7)_

#### `Country` 쿼리의 Null 필드

가상 품목을 출하 수량 계산에 포함하여 처리 중인 가상, 환불 및 출하 품목이 포함된 주문이 주문 상태가 완료로 올바로 전환되도록 하는 문제를 해결했습니다.

_AC-7731 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef666cd9)_

#### &quot;number&quot; 속성이 있는 GraphQL 쿼리 &quot;customerOrders&quot;로 인해 내부 서버 오류가 발생합니다

번호 필드를 요청할 때 GraphQL customerOrders 쿼리가 내부 서버 오류를 반환하는 문제를 해결했습니다.
이제 해결자가 순서 증가 ID를 올바르게 반환하여 쿼리가 성공적으로 실행되고 순서 번호가 검색되도록 합니다.

_AC-8949 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3b5ac075)_

#### 주문 배치에 대한 GraphQL 응답에는 예외 메시지가 포함되지 않습니다

다른 형식으로 오류를 반환하는 이전 변경 사항을 되돌렸습니다. 이제 잠재적인 오류가 GraphQL 스키마를 손상시키지 않고 일관된 방식으로 반환됩니다. 이는 알려진 BIC로 추가되어야 하며 PM이 승인하는 경우 https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&amp;page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 주문 배치에 대한 GraphQL 응답이 부분적으로 현지화되었습니다.

placeOrder GraphQl 돌연변이에 의해 반환된 오류가 완전히 현지화되지 않았습니다. 이제 다국어 컨텍스트에서 오류가 올바르게 번역됩니다.

_ACP2E-3506 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL API 순서를 변경하는 동시 호출 - 동일한 제품이 다른 행에 추가됨

GraphQL API 순서 재지정에 대한 동시 호출로 인해 동일한 제품이 다른 행으로 추가되어 데이터 불일치가 발생하는 문제를 해결했습니다.

_ACP2E-3774 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL 돌연변이(이메일 주소 변경)가 이메일 알림을 트리거하지 않음

이전에는 고객이 계정에 이메일 주소를 업데이트한 후 이메일을 보내지 않았습니다. 이 수정 사항이 적용되면 고객은 이제 이메일 주소를 성공적으로 업데이트한 후 이메일 알림을 받게 됩니다.

_ACP2E-3785 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateGiftRegistry 돌연변이를 통해 동적 특성이 Gift Registry에서 업데이트되지 않음

이전에는 updateGiftRegistry 돌연변이를 통해 이 수정 작업을 수행하기 전에는 선물 레지스트리의 사용자 지정 속성이 GraphQL 돌연변이를 통해 수정되거나 업데이트되지 않았습니다. 이 수정 사항이 적용되면 updateGiftRegistry 돌연변이를 통해 선물 레지스트리의 동적 속성을 성공적으로 업데이트할 수 있습니다.

_ACP2E-3805 - [GitHub 문제](https://mcstaging.briscoes.co.nz/)_

#### 고객 주문 GraphQL : 연결된 제품에 대한 제품 범주 검색은 &quot;개별적으로 표시되지 않음

수정 전에 주문에 숨겨진 제품이 포함된 경우 해당 카테고리가 고객 주문 GraphQl 응답에 빈 배열을 표시합니다.
이제 수정 후에는 제품이 숨겨져 있더라도 제품 카테고리가 고객 주문 GraphQl 요청의 응답에 포함됩니다.

_ACP2E-3945 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 위시리스트 항목은 GraphQL 요청의 한 웹 사이트 내에 있는 스토어 보기 간에 공유되지 않습니다

수정하기 전에 위시리스트 항목이 저장소 ID로 필터링되었습니다. 이제 수정 후 위시리스트 항목이 웹 사이트별로 필터링됩니다.

_ACP2E-3987 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a252ae6)_

#### 프로덕션에서 [클라우드] getRemoteAddress 반환 127.0.0.1

이 수정 전에는 응용 프로그램 서버를 사용할 때 원격 주소가 올바르게 확인되지 않았습니다. 수정 후 원격 주소가 올바르게 결정되고 nginx 및 헤더 구성에서 적절한 헤더 설정과 결합됩니다.

_ACP2E-3991 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] GQL 주문 배치 예외 처리 동작 되돌리기 확인

placeOrder 돌연변이에 대한 이전 버전과 호환되지 않는 변경 사항이 해결되었습니다.

_ACP2E-4031 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### GraphQL을 통해 주문할 때 번역된 메시지를 오류 코드에 매핑하는 문제

번역된 예외 메시지를 사용하여 GraphQL 요청에 대한 오류 코드를 매핑할 때 알려진 오류에 대해 알 수 없는 오류 코드가 발생하는 문제를 해결했습니다.

_ACP2E-4033 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD] 고객 주문 필터가 날짜에 대해 작동하지 않음

수정 후 날짜 범위 필터를 사용하여 GraphQL을 통해 주문을 검색하면 올바른 결과가 반환됩니다.

_ACP2E-4090 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### ACP2E-4031에서 제기된 주소 문제

이 문제를 해결하기 전에는 오류 노드 위치가 2.4.7 및 2.4.9 버전과의 완벽한 호환성을 제공하지 않았습니다. 이제 수정 후 오류 노드가 두 버전을 모두 수용하도록 올바르게 배치됩니다.

_ACP2E-4115 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

#### Graphql 호출에 하위 항목에 재고가 있어도 재고가 없음을 표시하는 번들 상위

수정 후 GraphQL을 사용하여 제품 목록을 요청하면 번들 제품에 대한 올바른 재고 상태가 반환됩니다.

_ACP2E-4168 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

#### SWAT의 GraphQL 예외

수정 후 GraphQL 요청에 대한 응답은 HTTP 사양을 통해 GraphQL에 정렬됩니다. 요청을 구문 분석할 수 없거나, 요청이 승인되지 않았거나, 요청에 다른 일반적인 문제가 있는 경우 4XX 응답 코드가 반환됩니다. 요청이 구문 분석되어 처리될 수 있는 경우 200 응답 코드가 반환됩니다.

_ACP2E-4194 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 목록이 고객에게 할당된 후 비교 목록에서 제품이 제거되지 않음

게스트 사용자의 비교 목록이 고객 계정에 할당되면 이제 게스트로 추가된 제품을 고객이 제거할 수 있습니다.
이전에는 할당 후 게스트가 추가한 항목이 고객의 계정에 제대로 연결되지 않아 제거 작업이 실패했습니다.

_ACP2E-4244 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQL 잘못된 오류 응답

이전에는 수량이 부족한 품목에 대해 graphQL 요청을 할 때 해당 품목을 사용할 수 없는 경우에도 요청 수량 및 가격 계산과 함께 오류 코드가 있는 적절한 오류 메시지가 반환되었습니다. 이 수정 사항이 적용되면 이제 오류 코드가 있는 적절한 오류 메시지가 반환되고, 응답에서 사용할 수 없는 경우 항목의 수량이 이전 값으로 설정됩니다.

_ACP2E-4283 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/cbca0396)_

#### MergeGuestOrder 플러그인의 웹 사이트 간 게스트 주문 할당 버그

이 문제를 해결하기 전에는 게스트 주문 고객 할당에서 계정 공유 옵션을 고려하지 않았습니다. 이제 수정 후 고객과 주문 저장소가 일치하는 경우 주문이 고객에게 할당됩니다(고객 계정 공유 옵션이 &quot;웹 사이트당&quot;으로 설정된 경우).

_ACP2E-4312 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, 인벤토리/MSI

#### Magento 2 GraphQL의 only_x_left_in_stock 문제 - 임계값 사용 시 잘못된 계산

MinQty의 잘못된 이중 공제로 인해 only_x_left_in_stock GraphQL 필드가 null을 반환하는 문제가 해결되었습니다. 이제 계산이 수정되어 임계값을 기준으로 정확한 재고 값이 반환됩니다.

_AC-15832 - [GitHub 코드 기여](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart 돌연변이 불일치

수정 후 GraphQL 요청은 재고 구성을 고려하여 제품 수량을 제대로 확인합니다.

_ACP2E-4184 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, 제품

#### MediaGalleryInterface에서 제품 graphql에 media_type 누락

이제 MediaGallery GraphQL 요청에 제품 이미지 유형의 &quot;유형&quot; 필드가 포함됩니다. 이전에는 이 &quot;유형&quot; 필드가 MediaGallery GraphQL 요청에 존재하지 않았습니다.

_ACP2E-3880 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, 보안

#### GraphQL을 통해 재설정된 고객 암호는 제한 사항을 준수하지 않습니다

GraphQL 돌연변이를 통해 수행된 고객 암호 재설정 요청이 스토어 > 구성 > 고객 > 고객 구성 > 암호 옵션에 구성된 암호 재설정 제한을 준수하지 않던 문제를 해결했습니다. 이제 이러한 설정이 올바르게 적용됩니다.

_ACP2E-3992 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

### 가져오기/내보내기

#### [문제] 매개 변수 형식 수정

이전에 문자열로 정의된 값이 이제 배열로 올바르게 설정되는 가져오기/내보내기 모듈의 매개 변수 유형 불일치가 수정되었습니다. 이는 내보내기 컨트롤러의 예상 입력에 맞추고 정적 분석 경고를 방지합니다.

_AC-11665 - [GitHub 문제](https://github.com/magento/magento2/issues/38529) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64823f95)_

#### [문제] 복사: &quot;coping&quot;을 &quot;복사&quot;로 변경합니다.

PR은 &quot;복사&quot;의 철자를 수정하기 위해 Minor copyedit를 수정합니다.

_AC-13300 - [GitHub 문제](https://github.com/magento/magento2/issues/39311) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39307)_

#### REST 끝점 제품 가져오기 Json이 필수 필드의 유효성을 검사하지 않음

이제 가져오기 프로세스(관리자 또는 API)를 통해 새 제품을 만들 때 이름 필드가 필요합니다. 수정 전에 이름 없이 새 제품을 만들 수 있습니다. 이렇게 하면 관리 인터페이스가 손상되고 잘못된 제품이 생성되었을 수 있습니다.

_ACP2E-3660 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### 내보내기 프로세스에 웹 사이트 필터 옵션 누락

이제 제품 내보내기를 만들 때 웹 사이트별로 제품을 필터링할 수 있습니다.

_ACP2E-3720 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

#### AC-13913의 복제 - 정적 속성을 비동기적으로 정리합니다.

수정 후에는 \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType의 많은 인스턴스가 생성될 때 &#39;정의되지 않은 배열 키 &quot;apply_to&quot;&#39; 오류가 없습니다.

_ACP2E-3752 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv 제품 가져오기 : 견본 이미지를 설정 해제할 수 없음

수정 전에는 제품 가져오기를 통해 제품의 견본 이미지를 업데이트할 수 없었습니다. 이제, 수정 후 제품 견본 이미지 열에 구성된 빈 마커를 표시하면 이미지가 숨겨짐으로 설정됩니다.

_ACP2E-3972 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 제품 가져오기로 스토어 범위에 대한 빈 URL이 생성됨

가져오기 데이터 소스에서 url_key에 빈 값이 있는 경우 스토어 보기의 제품 URL 키는 이제 기본 범위에 설정된 값을 상속합니다. 이전에 스토어 보기 레코드에 대한 가져오기 데이터 소스에서 url_key를 빈 값으로 설정하면 url_key가 해당 범위의 빈 값으로 재정의됩니다.

_ACP2E-4038 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### 다중 선택 속성이 필요에 따라 구성된 경우 제품 가져오기 프로세스에 오류가 발생합니다

다중 선택 유형의 필수 속성이 포함된 경우 제품 가져오기가 실패하는 문제를 해결했습니다. 이제 데이터 유효성 검사가 정상적으로 통과되어 제품 가져오기 프로세스가 정상적으로 완료됩니다.

_ACP2E-4057 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 재고를 관리할 때 선택한 미납주문이 없는 [CLOUD] 제품을 가져왔을 때 고객이 재고 수준을 초과하여 주문할 수 있도록 여전히 허용

수정 후에는 제품의 &quot;allow_backorders&quot; 속성에 대해 더 이상 허용되지 않는 값을 가져올 수 없습니다.

_ACP2E-4116 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 설명 길이가 65,536자를 초과하여 제품 가져오기가 실패했습니다. 유효성 검사

수정 후 값이 65,536자를 초과하는 텍스트 유형의 제품 속성을 가져올 수 있습니다.

_ACP2E-4119 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 제품 예-아니오 속성에 대한 내보내기 필터 가 예상대로 작동하지 않음

수정 후 예/아니요 속성으로 필터링된 내보낸 제품에는 적용된 필터와 관련된 예상 제품이 포함됩니다.

_ACP2E-4160 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ee918f0d)_

#### 가져오기를 통해 웹 사이트당 번들 옵션 가격 업데이트 문제

이제 웹 사이트당 번들 옵션 선택 가격을 내보내고 가져올 수 있습니다

_ACP2E-4243 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/98f028ab)_

#### 대문자 이메일 주소로 고객을 가져올 수 없음

[계정 공유]가 [전역]으로 설정된 경우 대문자를 사용하여 고객을 가져올 때 정의되지 않은 배열 키 오류를 수정했습니다. 이제 가져오기 프로세스 전체에서 이메일 표준화가 일관되어 이메일 사례에 관계없이 고객을 가져올 수 있습니다. 웹 사이트 수준 계정 공유 동작은 변경되지 않습니다.

_ACP2E-4373 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

### 가져오기/내보내기, 고객/고객

#### 관리자는 생년월일이 현재 날짜보다 큰 고객을 가져올 수 있습니다.

관리자가 나중에 생년월일이 설정된 고객을 가져올 수 있는 문제를 해결했습니다. 이제 시스템이 가져오는 동안 DOB를 확인하고, 잘못된 레코드에 대한 오류를 표시하며, 미래의 생년월일이 있는 고객을 가져오지 않도록 하여 정확한 고객 데이터를 보장합니다.

_AC-13641 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

### 인벤토리/MSI

#### 체크아웃 시 주소가 변경되면 스토어 픽업이 최대 검색 반경을 따르지 않음

이제 배송 주소가 변경되면 &quot;매장 선택&quot;에서 미리 선택한 매장이 업데이트됩니다. 기존에는 매장을 사전 선정하면 새 배송지 주소가 선택한 매장 반경 내에 없더라도 변경되지 않았다

_ACP2E-3728 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/07620383)_

#### 홈페이지로 리디렉션하고 체크아웃한 후에는 스토어를 사용할 수 없습니다.

고객이 결제 페이지로 이동한 다음, 홈 페이지로 돌아간 다음, 최종적으로 체크아웃 페이지로 돌아오면, 이제 이전에 선택한 저장소가 &quot;스토어 내 선택&quot; 배송에서 미리 선택됩니다. 이전에는 체크아웃 페이지로 반복적으로 돌아간 후 &quot;스토어 선택&quot;에서 선택한 스토어가 지워졌습니다.

_ACP2E-3793 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/62c0d79b)_

#### 재고 삭제 작업이 완료되지 않았습니다.

수정 후 소스 항목을 삭제해도 전체 색인 재지정이 되지 않고 영향을 받는 제품만 업데이트되어 성능이 향상됩니다.

_ACP2E-3917 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] 고객이 비동기적으로 주문 픽업 준비됨 알림을 받은 경우 관리자에 표시가 없습니다.

고객에 대한 주문 내역 알림이 주문 준비가 되었습니다.에 대해 비동기적으로 알림되었습니다.

_ACP2E-3968 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/29653b1d)_

#### 견적 로드 시 중복되는 재고 상태 쿼리

상점 전면에서 견적을 로드할 때 cataloginventory_stock_status 쿼리의 중복 실행을 수정하여 중복 DB 호출을 발생시켰습니다.

_ACP2E-4102 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/fc15a9ae)_

#### 패치 이후 ACP2E-4118: 관리자의 재고 임계값 변경으로 인해 음수 판매 수량 및 재고 상태 불일치가 발생합니다

이제 글로벌 재고 구성 수량, 미납주문 및 재고 부족 임계값이 임포트를 통해 업데이트될 때 재고 재고 상태가 자동으로 조정됩니다.

_ACP2E-4142 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

#### 인벤토리가 업데이트될 때 [CLOUD] 관리 보고서에 세부 정보가 표시되지 않습니다.

제품 인벤토리 소스 변경 사항이 이제 로깅 모듈에 의해 기록됩니다. 수정 이전에는 제품을 저장하고 인벤토리 관련 변경 작업을 수행할 때 세부 사항이 기록되지 않았습니다.

_ACP2E-4167 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/cbca0396) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/76b88f7c)_

#### 재고로 표시되는 동안 번들 제품을 장바구니에 추가할 수 없음

이제 번들 제품 재고 상태가 하위 제품 예약 및 재고 부족 임계값을 올바르게 반영합니다.
기존에는 1개 이상 아동용품이 충분한 판매가능 수량이 부족할 때도 묶음상품을 &#39;재고&#39;로 표시했다. 이로 인해 장바구니에 번들을 추가할 때 &quot;판매할 항목이 충분하지 않음&quot; 오류가 발생했습니다.

_ACP2E-4220 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/cbca0396) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/76b88f7c)_

#### 하위 항목이 사용자 지정 소스/재고에 할당되면 그룹화된 제품이 CSV에서 가져온 후 PDP에서 재고 없음으로 잘못 표시됩니다(수동 재인덱싱 후 수정됨).

수정 후 가져오기를 사용하여 복합 제품을 생성하면 자동으로 재고 재인덱싱이 수행되므로 수동으로 재인덱싱할 필요 없이 제품을 사용할 수 있습니다.

_ACP2E-4233 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/98f028ab) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] 최신 기본 줄 변경 내용과 관련된 MTF 테스트가 실패했습니다.

고정 게스트 고객이 배송 주소 없이 매장 내 픽업을 선택하기 전에는 청구 주소가 매장 주소로 자동 채워져 변경할 수 없었고, 이로 인해 잘못된 송장 세부 정보가 표시되었습니다. 청구 주소 수정 후에는 이 시나리오에서 편집할 수 있으며, 게스트가 직접 세부 정보를 입력할 수 있습니다. 등록된 사용자는 스토어 대신 저장된 청구 주소를 보게 됩니다.

_ACP2E-4260 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ab891304) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/13e432a6)_

#### 가상 기프트 카드에 대해 잘못된 인벤토리 예약이 생성됨

이 수정 사항을 구현하기 전에 여러 항목이 들어 있는 가상 기프트 카드의 수량이 재고 예약에 정확하게 반영되지 않았습니다. 그러나 픽스가 적용된 이후 재고 예약 수량과 재고가 동기화됐다.

_ACP2E-4267 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5704166a)_

#### 재고 예약 보상 명령이 Null 및 존재하지 않는 제품 참조와 함께 실패함

처리된 조합에 주문 ID가 누락된 경우 재고 예약 보상 CLI에서 예외를 발생시키는 문제가 해결되었습니다.

_ACP2E-4301 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/76b88f7c)_

#### SKU 케이스를 변경한 후 제품이 품절되었습니다.

SKU 사례를 수정해도 더 이상 상점 진열대에서 제품이 품절되지 않습니다.

_ACP2E-4375 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/0836c2ed)_

#### 잘못된 데이터가 있는 가격/가격 패싯별 주문

이 문제 이전에는 하위 제품이 사용자 정의 소스에 따라 재고를 보유할 때 번들 가격이 제대로 색인화되지 않았습니다. 이제 수정 후 번들 가격은 하위 제품 재고 할당과 관계없이 올바르게 색인화됩니다.

_ACP2E-4380 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1c547060) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/1f83ed24)_

### 주문

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[])가 customAttributes를 나눕니다.

이제 체크아웃 및 API 작업 중 주소의 사용자 지정 속성이 올바르게 처리됩니다.
이전에는 $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes)를 사용하면 사용자 지정 속성 처리가 중단되어 속성 값이 잘못 구조화될 수 있었습니다.
AC-10568

_AC-10568 - [GitHub 문제](https://github.com/magento/magento2/issues/31644)_

#### 고객이 견적 주문에 대해 설정된 경우에도 여전히 게스트 주문입니다.

_AC-11689 - [GitHub 문제](https://github.com/magento/magento2/issues/38540)_

#### 가상, 환불 및 배송된 품목을 혼합하는 경우 주문이 완료되지 않음

가상 품목을 출하 수량 계산에 포함하여 처리 중인 가상, 환불 및 출하 품목이 포함된 주문이 주문 상태가 완료로 올바로 전환되도록 하는 문제를 해결했습니다.

_AC-11691 - [GitHub 문제](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento 순서 바꾸기 -1 순서 번호

시스템이 예상대로 작동하며 백엔드에서 순서를 재정렬하면 주문 번호가 고유 8자리가 됩니다

_AC-12854 - [GitHub 문제](https://github.com/magento/magento2/issues/39089) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39399)_

#### Adobe 신용카드 결제 방법으로 체크아웃 시 제품 사용자 정의 옵션 파일 업로드 손실

이제 Adobe 신용카드 결제 방법으로 체크아웃할 때 제품 사용자 지정 옵션 파일 업로드를 유지합니다.
기존에는 이 결제 방식을 사용할 때 파일 업로드가 유실됐지만, 다른 사람과 함께 작업했다.
AC-14306

_AC-14306 - [GitHub 문제](https://github.com/magento/magento2/issues/39647)_

#### 관리자 주문 - 의지를 검색할 수 없음

관리 주문 그리드에서 고객 이름(예: &quot;의지&quot;)별로 주문을 검색해도 결과가 반환되지 않던 문제를 수정했습니다. 수정 후에는 고객 이름으로 필터링할 때 관련 주문이 올바르게 표시됩니다.

_AC-14360 - [GitHub 문제](https://github.com/magento/magento2/issues/36596) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - 주문 항목 order_date 잘못된 서식

GraphQL 응답의 order_date 필드가 yyyy-mm-dd 형식으로 반환되던 문제를 수정했습니다.
이제 order_date가 dd-mm-yyyy 형식으로 올바르게 표시됩니다.

_AC-14431 - [GitHub 문제](https://github.com/magento/magento2/issues/39805) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### nullable이 아닌 필드 \&quot;AppliedCoupon.code\&quot;에 대해 null을 반환할 수 없습니다. 예기치 않은 문제

이제 Adobe Commerce은 고객 주문을 쿼리할 때 GraphQL을 통해 적용된 쿠폰 코드를 올바르게 반환합니다. 이전에는 Adobe Commerce 2.4.8에서 apply_coupons.code 필드가 있는 주문을 가져오는 데(예: customer.orders 쿼리를 통해) 내부 서버 오류가 발생하여 실패할 수 있었으며 null을 허용하지 않는 필드 &quot;ApplyCoupon.code&quot;에 대해 null을 반환할 수 없습니다 라는 메시지가 표시되었으며, apply_coupons는 쿠폰 코드가 포함된 목록 대신 [null]&#x200B;(으)로 반환되었습니다. AC-14484

_AC-14484 - [GitHub 문제](https://github.com/magento/magento2/issues/39841) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/97b2ea42)_

#### 스토어 구성에서 활성화되었지만 관리 주문 보기에서 제출할 때 선적 이메일이 전송되지 않음

이제 주문이 이루어진 스토어 구성에서 출하 확인 이메일을 사용할 수 있으므로 시스템이 출하 확인 이메일을 전송합니다.

_AC-14563 - [GitHub 문제](https://github.com/magento/magento2/issues/39861) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39897)_

#### 모호한 필드 이름으로 인해 날짜 필터링이 작동하지 않음

Magento 2.4.7-p6에서 날짜별로 순서 그리드를 필터링하면 Braintree 모듈과의 조인으로 인해 오류가 발생하는 것으로 보고되었습니다.
날짜 필터를 적용할 때 braintree_transaction_details 및 sales_order 테이블을 조인하는 쿼리와 관련된 문제입니다.
Adobe Commerce 엔지니어링이 사례를 검토했지만 환경에서 오류를 재현할 수 없었습니다.
예상 동작은 날짜별로 필터링하면 오류 없이 필터와 일치하는 순서가 반환되어야 한다는 것입니다.

_AC-15037 - [GitHub 문제](https://github.com/magento/magento2/issues/40024)_

#### 하나 이상의 제품에 사용자 지정 옵션이 포함되어 있는 백오피스에서 주문을 만들면 주문에서 원치 않는 추가 제품이 추가됩니다.

사용자 지정 옵션이 있는 제품을 포함하여 여러 제품이 있는 백오피스에서 주문을 만들면 의도하지 않게 추가 제품이 추가되고 오류가 발생하는 문제가 해결되었습니다. 이제 시스템에서 선택한 제품만 추가하여 예기치 않은 항목 없이 주문을 만들 수 있습니다.

_AC-15286 - [GitHub 문제](https://github.com/magento/magento2/issues/40122) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: 프로모션 규칙을 만들 수 없음

이 PR은 다음과 같이 수정됩니다.
\Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions 메서드에서 \Magento\Catalog\Model\ResourceModel\Eav\Attribute 대신 \Magento\Catalog\Model\ResourceModel\Eav\Attribute 모델

_AC-15358 - [GitHub 문제](https://github.com/magento/magento2/issues/12176) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30479)_

#### Magento이 $invoice = $this->_invoiceService->prepareInvoice($order) 호출 후 $order의 엔티티 유형을 변경했습니다.

하위 범주에 대한 기존 예약된 업데이트를 편집하면 데이터베이스의 상위 범주에 대한 children_count가 잘못 증가하던 문제를 수정했습니다. 이 문제로 인해 업데이트를 저장한 후 부정확한 범주 계층 구조 데이터가 발생했습니다. 수정 후에도 자녀 수가 올바르게 유지되며 더 이상 예기치 않게 증가하지 않습니다.

_AC-15401 - [GitHub 문제](https://github.com/magento/magento2/issues/40154)_

#### 품목이 부분적으로 환불되는 경우 주문은 배송 후 &#39;처리 중&#39; 상태로 유지됩니다.

부분적으로 품목을 환불하고 나머지를 배송한 후 주문이 처리 중 상태에 있는 문제를 해결했습니다. 이제 총 출하 및 환불 수량이 송장 발행 수량과 일치하면 주문 상태가 완료로 올바르게 업데이트되므로 정확한 주문 수명 주기 관리가 보장됩니다.

_AC-15419 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/cc0ec250)_

#### 백엔드에서 판매 이메일을 보내면 항상 성공(비활성화될 경우에도)이 제공됩니다

주문 또는 송장 발부 이메일이 비활성화되어 전송되지 않을 때 사용자에게 알려지도록 이메일 서비스 결과를 확인하여 정확한 메시지를 표시하도록 백엔드 판매 이메일 알림을 수정했습니다.

_AC-16059 - [GitHub 문제](https://github.com/magento/magento2/issues/40309) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 재주문 시 사용자 지정 가격 0이 원래 가격으로 재설정됩니다.

재주문 중에 사용자 지정 가격이 0인 제품이 원래 가격으로 되돌아온 문제를 해결했습니다.
이제 사용자 지정 가격이 올바로 유지되므로 항목을 재정렬할 때 정확한 가격이 책정됩니다.

_AC-8147 - [GitHub 문제](https://github.com/magento/magento2/issues/36970) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/01cee3c3)_

#### 비활성화된 결제 방법이 작동하는 주문

GraphQL을 통해 비활성화된 결제 방법을 사용하여 주문을 할 수 있는 문제가 해결되었습니다.
이제 사용할 수 없는 결제 방법을 설정하거나 사용하려고 할 때 오류가 반환되어 주문이 생성되지 않습니다.

_AC-9605 - [GitHub 문제](https://github.com/magento/magento2/issues/37983) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### 처리 중 주문 상태 중단

수정 전에는 &quot;함께 배송&quot; 옵션이 활성화된 번들 제품을 주문할 때 송장 및 선적 후 주문 상태가 자동으로 &quot;완료&quot;로 전환되지 않았습니다. 이제, 수정 후 주문 상태가 자동으로 주문 송장이 발행되고 배송된 후 &quot;완료&quot;로 전환됩니다.

_ACP2E-3947 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a252ae6)_

#### [클라우드]Magento OOTB 코드 - 전자 메일 템플릿 설정 문제

수정 전에 비동기 이메일 전송을 사용할 때 배송 이메일이 스토어 주문과 일치하지 않았습니다. 이제, 수정 후, 적절한 매장 선적 이메일 주문이 전달됩니다.

_ACP2E-3998 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

#### 송장 리디렉션을 404로 취소

캡처되지 않은 유형의 송장을 취소하면 더 이상 404페이지가 표시되지 않습니다.

_ACP2E-4001 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### REST API를 사용하여 구성 가능한 옵션이 있는 업데이트된 주문 문제

rest api 끝점을 통해 주문을 업데이트할 때 판매 주문 항목에 대한 기존 제품 옵션을 유지합니다.

_ACP2E-4061 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### ID별 비동기 삽입 기능은 cron 실행당 100개의 항목으로 제한됨

영업 그리드 비동기 삽입의 처리가 개선되었습니다. 이제 한 cron run은 엄격한 실행당 100개가 아닌 보류 중인 모든 행을 배치로 삽입합니다.

_ACP2E-4360 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/31258bf6)_

#### 오류 메시지 &quot;ID가 &quot;1&quot;인 제품이 존재하지 않습니다.&quot; exception.log에 반복적으로 로그인되고 있습니다.

수정하기 전에 삭제된 제품이 마지막 주문 항목 섹션에서 발생했을 때 심각한 오류가 기록되었습니다. 수정 후 판매자는 di.xml의 `skipDeletedProductLogging` 매개 변수를 통해 삭제된 제품을 기록할지 또는 건너뛰는지 여부를 구성할 수 있습니다. 기본적으로 이전 버전과의 호환성을 위해 동작은 변경되지 않지만 판매자는 삭제된 제품을 자동으로 건너뛰고 로그 노이즈를 방지하기 위해 매개 변수를 `true`(으)로 설정할 수 있습니다.

_ACP2E-4366 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

#### 두 번째 대변 메모 환급에 대한 이중 세금

주문 보기 페이지에서 이전 대변 메모가 생성된 후 송장에서 부분 환불을 생성할 때 대변 메모의 잘못된 세금 계산을 수정했습니다.

_ACP2E-4384 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

### 주문, 가격 책정

#### 책임자가 반환 생성 시 잘못된 통화 기호가 표시됨

다른 통화(EUR/USD/GBP)를 사용하는 다중 웹 사이트 설정에서 관리자의 반환 제품 선택 페이지에 이제 올바른 통화 기호가 표시됩니다. 이전에는 기본 통화 기호를 표시했습니다.

_ACP2E-3658 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 순서, 반환

#### 오프라인 환불에 대한 대변 메모를 만들 때 오류 발생

동적 가격 = 아니오로 설정된 번들 제품에 대해 대변 메모를 생성하지 못하는 문제가 해결되었습니다. 이제 대변 메모를 오류 없이 성공적으로 생성할 수 있습니다.

_ACP2E-4157 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

### 기타 개발자 도구

#### [문제] 보호된 멤버 $_urlHelper에 대한 잘못된 유형 힌트

이제 생성자에서도 사용되는 올바른 힌트로 잘못된 유형 힌트가 수정됩니다

_AC-10716 - [GitHub 문제](https://github.com/magento/magento2/issues/32503) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32496)_

#### [문제] 사용하지 않는 코드를 정리하는 중입니다.

이제 시스템에서 사용되지 않은 가져오기와 관련된 사용되지 않은 코드를 제거합니다.

_AC-10980 - [GitHub 문제](https://github.com/magento/magento2/issues/38424) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33499)_

#### 등대 접근성 오류

이제 시스템이 100의 접근성 점수로 전달됩니다.

_AC-12783 - [GitHub 문제](https://github.com/magento/magento2/issues/39054) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39164)_

#### Captcha storefont 구성 비활성화(captcha js 파일 로드)

이제 captcha를 비활성화하면 시스템이 captcha js 파일을 로드하지 않습니다
for storefont

_AC-14267 - [GitHub 문제](https://github.com/magento/magento2/issues/32987) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39154)_

#### [문제] 접근성: WAI-ARIA 역할이 메뉴에 잘못 중첩되었습니다.

이제 시스템은 메뉴 오류에 잘못 중첩되고 보고서가 녹색이 되어야 하는 WAI-ARIA 역할 없이 등대 접근성을 생성합니다

_AC-15082 - [GitHub 문제](https://github.com/magento/magento2/issues/40045) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38617)_

#### Magento 관리자의 이메일 미리 보기에 콘솔 오류가 있습니다.

이메일 템플릿을 미리 볼 때 시스템에서 콘솔 오류가 발생하지 않습니다.

_AC-9245 - [GitHub 문제](https://github.com/magento/magento2/issues/37820) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37933)_

### 결제/결제 방법

#### 백엔드에서 성공적으로 구성하는 동안 나중에 메시지가 상점 앞에 표시되지 않습니다.

백엔드에 PayPal 나중에 지불 메시지가 구성되어 있어도 홈 및 장바구니 페이지에 표시되지 않는 문제를 수정했습니다. 기본 주소가 없는 손님 또는 고객에 대해 구매자 국가가 null일 때 배너를 렌더링하지 못했습니다. 수정 후 나중에 지급 메시지가 상점 앞에 올바르게 표시됩니다.

_AC-12335 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/528af81a)_

### 결제

#### [문제] 오프라인 인보이스 캡처 수정(404)

Magento 관리자의 오프라인 결제 방법에 대한 송장을 캡처하는 동안 404 페이지 오류가 수정되었습니다

_AC-13336 - [GitHub 문제](https://github.com/magento/magento2/issues/39298) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39297)_

#### PayPal의 알 수 없는 IPN 남용 응용 프로그램 IPN 프로세서

이제 IPN 처리기에서 지원되지 않거나 알 수 없는 IPN 형식을 무시합니다. 500 오류를 반환하는 대신 문제를 기록하고 중단 없이 계속 처리합니다.

_ACP2E-4049 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 결제 시 PayflowPro 저장 카드 토큰 실패

PayPal PayFlow Pro 거래 ID(PNREF)는 이제 12개월의 고정 기간 동안 참조 거래에서 사용할 수 있습니다. 만료되면 저장된 카드가 더 이상 표시되지 않으므로 다시 추가해야 합니다. 기존에는 원래 거래에서 사용된 결제카드의 유효기간에 따라 유효성이 결정됐다.

_ACP2E-4064 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### 책임자에게 주문할 때 저장된 카드 문제

다른 결제 작업 구성으로 웹 사이트에 저장된 신용 카드로 주문하면 더 이상 오류 또는 잘못된 거래 유형이 발생하지 않습니다

_ACP2E-4270 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] PayflowPro 저장 카드(Vault) 마지막 4자리가 순서대로 표시되지 않습니다.

이제 판매 결제 액션과 함께 저장된 카드를 사용할 때 카드 정보가 올바르게 유지되고 표시되므로 PayflowPro에 대한 인증 결제 액션을 사용할 때의 비헤이비어와 일치합니다.

_ACP2E-4346 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

### 성능

#### [문제] Store.php 업데이트

이 PR은 현재 저장소 해상도를 건너뛰어 성능을 향상시킵니다.

_AC-14791 - [GitHub 문제](https://github.com/magento/magento2/issues/39949) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38717)_

#### [문제] 업데이트 정적 사이트에 대해 캐시 컨트롤을 변경할 수 없습니다.

이 PR은 변경될 때까지 및 변경되지 않는 한 각 페이지 로드 시 정적 콘텐츠의 유효성을 검사하지 않으므로 성능이 향상됩니다.

_AC-15171 - [GitHub 문제](https://github.com/magento/magento2/issues/39486) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39484)_

#### [문제] isCachable 호출의 결과를 캐시하여 성능을 개선합니다.

이 PR은 isCachable() 메서드에 대한 캐싱을 추가하면 레이아웃 렌더링 프로세스가 수행되어 중복 검사를 줄이고 전반적인 페이지 렌더링 성능을 향상시킵니다.

_AC-16054 - [GitHub 문제](https://github.com/magento/magento2/issues/40156) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40112)_

#### [문제] 비동기 주문 그리드 처리 성능이 약간 개선되었습니다.

이 PR에서는 임시 캐시 기반 last_updated_at 조회를 플래그 테이블에 저장된 영구 DB 지원 플래그로 대체하여 Magento의 비동기 주문 그리드 처리에 대한 성능 최적화를 도입했습니다. 이렇게 하면 캐시 플러시 또는 배포 후에도 시스템에서 마지막으로 처리된 타임스탬프를 일관되게 유지하여 대규모 sales_order 데이터 세트에서 불필요한 전체 테이블 스캔을 방지할 수 있습니다. 따라서, 특히 주문 활동이 빈번한 대량 스토어에서 비동기 그리드 업데이트가 더욱 효율적이고 예측 가능합니다.

_AC-16109 - [GitHub 문제](https://github.com/magento/magento2/issues/40282) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40271)_

#### [CLOUD] 범주에 제품을 추가할 수 없습니다.

Visual Merchandiser를 통해 제품을 카테고리에 추가할 때의 성능이 향상되었습니다.

_ACP2E-3946 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/29653b1d)_

#### ACP2E-3995 이후 로그 정리 성능 문제

수정 후 indexer_clean_all_changelogs cron job은 일괄 처리를 적절하게 유지하면서 변경 로그를 완전히 정리합니다.

_ACP2E-4211 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ee918f0d)_

#### [클라우드] 2.4.8로 업그레이드한 후 Fastly 캐시가 작동하지 않습니다.

캐시 가능한 페이지가 Fastly 캐시에서 제대로 저장되지 않거나 제공되지 않아 캐싱 동작이 일관되지 않고 성능이 저하되는 문제를 해결했습니다.

_ACP2E-4324 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2687b487)_

#### Redis 키 및 캐시 키 생성이 증가하는 이유를 조사합니다.

이 문제를 해결하기 전에는 원격 스토리지 메타데이터에 사용된 캐시 키가 만료되지 않았습니다. 이제 수정 후 종속성 삽입을 통해 이러한 캐시 키에 대한 TTL을 설정할 수 있습니다.

_ACP2E-4345 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

### 가격 책정

#### 주문 REST API에서 동적 가격이 없는 번들 제품 항목에 대한 가격은 항상 0입니다.

이제 주문 REST API는 동적 가격 없이 번들 제품 항목에 대한 올바른 가격을 반환합니다.
이전에는 REST API를 통해 주문을 내보낼 때 동적 가격책정이 없는 번들 제품 품목의 가격이 번들 페이지에 표시된 실제 가격 대신 항상 0으로 반환되었습니다.
AC-11925

_AC-11925 - [GitHub 문제](https://github.com/magento/magento2/issues/38687) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7da46f52)_

#### 생성 시 가격 속성에 잘못된 범위 할당

새로 만든 가격 속성이 구성에 관계없이 스토어 보기 범위에 잘못 지정되던 문제가 해결되었습니다. 수정 후 속성 범위가 이제 기본적으로 카탈로그 가격 범위 설정 (전역 또는 웹 사이트)과 일치합니다.

_AC-14945 - [GitHub 문제](https://github.com/magento/magento2/issues/39986) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### 일괄 조치를 사용하여 특별 가격 시작 일자 가 종료 일자 이후인 경우에도 제품이 저장되고 있습니다.

유효성 검사 없이 잘못된 특별 가격 날짜 범위로 제품을 저장할 수 있는 문제를 해결했습니다.
이제 오류 메시지가 표시됩니다. &quot;종료 날짜가 시작 날짜보다 이후이거나 동일한지 확인하십시오.&quot;

_AC-15252 - [GitHub 문제](https://github.com/magento/magento2/issues/40113) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 특가를 적용해도 정가는 보이지 않는다.

특별 가격이 적용되었을 때 정가가 표시되지 않던 문제를 해결했습니다. 이제 예상대로 특가와 나란히 정가가 올바르게 등장한다.

_ACP2E-4100 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

### 제품

#### 프런트엔드에서 잘못된 비헤이비어로 구성 가능한 제품

색상 견본 속성이 포함될 때 구성 가능한 제품에 잘못된 프론트엔드 동작이 표시되어 가격 책정, 드롭다운 레이아웃 및 필수 필드 표시기가 제대로 표시되지 않는 문제를 해결했습니다.
이제 구성 가능한 제품이 적절한 가격 책정, 조정된 드롭다운 및 예상 UI 동작을 통해 올바르게 렌더링됩니다.

_AC-1014 - [GitHub 문제](https://github.com/magento/magento2/issues/14296) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef666cd9)_

#### 구성 가능한 제품이 품절 제품 표시 옵션이 활성화된 테스트 재고 및 테스트 웹 사이트에 할당된 경우 가격 어설션 문자열 불일치

모든 하위 제품의 가격이 동일한 경우 구성 가능한 제품에 대한 실제 가격 책정 동작과 일치하도록 실패한 테스트를 업데이트했습니다.
이제 어설션이 표시된 가격을 올바르게 검증하여 기능에 영향을 주지 않고 잘못된 테스트 실패를 방지합니다.

_AC-10843 - [GitHub 코드 기여](https://github.com/magento/inventory/commit/1ccc786b)_

#### 테스트 사례 AC-6158의 구성 가능한 제품에 대해 &#39;낮음&#39; 레이블이 여전히 표시됨

각 변형 및 범주 할당으로 구성 가능한 제품(P1-P7)을 구현하고 검증했습니다. 카테고리 C 아래에 있는 제품에 대해 올바른 상점 가격 표시 및 &quot;최저 가격&quot; 레이블 동작을 확인했습니다.

_AC-10847 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 선택한 옵션 없이 원래 가격으로 계산된 계층 가격 및 카탈로그 가격 규칙의 할인율입니다.

계층 가격 및 카탈로그 가격 규칙에 대한 퍼센트 할인에는 이제 선택한 사용자 지정 옵션이 포함됩니다.
기존에는 선택한 맞춤형 옵션을 고려하지 않은 채 기존 제품 가격에 퍼센트 할인이 계산돼 최종 가격이 잘못 산정됐다.
AC-12004

_AC-12004 - [GitHub 문제](https://github.com/magento/magento2/issues/38750)_

#### [문제] 유효성 검사 평가가 작동하지 않습니다. 검토 등급 선택기가 변경되었습니다.

변경된 선택기로 인해 검토 등급 유효성 검사가 트리거되지 않던 문제를 수정했습니다. 이전에는 등급을 선택하지 않고 리뷰를 저장할 수 있었습니다. 수정 후에는 유효성 검사가 올바르게 작동하며, 등급을 선택하지 않은 경우 검토를 저장할 수 없습니다.

_AC-12686 - [GitHub 문제](https://github.com/magento/magento2/issues/33424) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 min허용된 누락 제품 주문 수량

시스템이 정상적으로 작동하며 페이지 소스가 제품의 최소 수량을 올바르게 표시함

_AC-12909 - [GitHub 문제](https://github.com/magento/magento2/issues/39142) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39480)_

#### 제품 컬렉션 - 컬렉션이 로드되거나 로드될 때 addMediaGalleryData가 getSize를 호출합니다(카운트를 사용하여 추가 DB 쿼리를 방지할 수 있음).

이 PR은 media_gallery 필드가 포함된 제품 Graphql을 호출할 때 제품 컬렉션이 이미 로드된 경우 count()를 사용하여 추가 쿼리 호출을 줄입니다.

_AC-13055 - [GitHub 문제](https://github.com/magento/magento2/issues/39111) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39681)_

#### Magento의 연결된 제품에 대한 잘못된 SKU 처리

잘못된 SKU 유효성 검사로 인해 SKU가 &quot;0&quot;인 제품을 관련 항목, 상향 판매 또는 교차 판매 항목으로 연결할 수 없는 문제를 해결했습니다. 업데이트에서는 이러한 제품이 성공적으로 연결되어 오류 없이 제품을 저장할 수 있도록 합니다.

_AC-13311 - [GitHub 문제](https://github.com/magento/magento2/issues/39329) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

#### 관리 패널의 제품 페이지에서 사용자 지정 가능한 옵션 표 문제

유형 드롭다운으로 사용자 지정 가능한 옵션을 만들 때 시스템이 예상대로 작동합니다

_AC-14003 - [GitHub 문제](https://github.com/magento/magento2/issues/39640) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39694)_

#### 모든 제품 특성이 전역 범위로 설정된 경우 관리 제품 페이지 오류 발생

모든 제품 속성이 전역 범위로 설정된 경우 관리 제품 편집 페이지에 오류가 표시되는 문제를 해결했습니다. 빈 데이터베이스 쿼리로 인해 오류가 발생하여 페이지를 사용할 수 없습니다. 수정 후 제품 페이지가 올바르게 렌더링되고 문제 없이 제품을 만들 수 있습니다.

_AC-14011 - [GitHub 문제](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] cron 작업 catalog_product_alert에 대한 콜백이 없습니다.

이제 Adobe Commerce은 제품 경고 cron job이 product_alert로 이름이 변경된 후에 잘못된 catalog_product_alert cron job이 예약되지 않도록 올바르게 차단합니다. 이전에는 Adobe Commerce 2.4.8에서 [저장소] > [구성] > [카탈로그] > [카탈로그] > [제품 경고 실행 설정]을 구성하면 catalog_product_alert cron 항목이 core_config_data에 생성되었으며, cron이 실행할 때 오류 Magento_Cron이 기록되었습니다.CRITICAL: 예외: 유효한 product_alert 작업이 올바르게 실행 중인데도 cron 작업 catalog_product_alert에 대한 콜백이 없습니다.

_AC-14494 - [GitHub 문제](https://github.com/magento/magento2/issues/39800) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [제품 비교] 비교 목록을 사용할 수 없습니다.

서로 다른 스토어 보기에서 동일한 제품을 추가할 때 비교 목록을 사용할 수 없게 되는 문제가 해결되었습니다. 수정 후 비교 목록이 올바르게 로드되고 특정 스토어를 기반으로 항목이 표시됩니다.

_AC-14885 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### 저장소를 통해 제품 요청 실패 시 추가 로깅

SKU 또는 ID를 찾을 수 없는 경우 ProductRepository::get 및 getById에 대한 오류 메시지가 개선되었습니다.
이전에는 오류가 발생한 SKU 또는 ID에 대한 컨텍스트가 없는 예외가 제공되었습니다.
이제 예외 메시지에는 누락된 SKU 또는 ID가 포함되어 있어 디버깅 및 개발자 경험 개선에 도움이 됩니다.
이 변경 사항은 API의 기능 동작에 영향을 주지 않습니다.

_AC-15199 - [GitHub 문제](https://github.com/magento/magento2/issues/40090) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 속성 세트가 존재하지 않음 오류 발생 시 페이지가 중단됨

URL에 잘못된 속성 세트 ID를 입력하면 치명적인 오류가 발생하는 문제가 해결되었습니다. 이제 시스템이 페이지를 중단하는 대신 속성 세트가 존재하지 않는다는 적절한 오류 메시지를 표시합니다.

_AC-15753 - [GitHub 문제](https://github.com/magento/magento2/issues/40213) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a06a4a57)_

#### 음수 수량 환불 할인 포함 환불

수량이 음수인 대변 메모를 만드는 경우 할인 금액을 잘못 환급하는 문제가 해결되었습니다.
지금은 음수 수량에 대해서는 할인이 환불되지 않으며, 환불 수량은 0으로 정확히 설정되어 있다.

_AC-9424 - [GitHub 문제](https://github.com/magento/magento2/issues/37917) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef666cd9)_

#### 페이지 빌더를 통해 제품 위젯이 포함되면 느린 쿼리가 실행됩니다

제품 SKU를 포함한 제품 위젯 만들기에 대한 쿼리가 최적화되었습니다.

_ACP2E-3449 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### 구성 가능한 제품으로 추가될 때 제품 이미지 크기가 조정되지 않음

이전에는 관리 패널의 구성을 통해 추가된 이미지가 최대 업로드 크기 제한을 준수하지 않아 일관성 및 관리 문제가 발생할 수 있었습니다. 이제 업로드 중에 최대 크기 제한을 준수하도록 이미지 크기가 자동으로 조정되도록 수정하여 프로세스를 간소화하고 시스템 표준을 유지 관리합니다.

_ACP2E-3504 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### 다른 고객의 모든 비교 목록은 관리자를 통해 로그인한 후 고객에게 할당됩니다

이전에는 관리자가 백엔드에서 &quot;고객으로 로그인&quot; 기능을 사용하면 이전에 로그인한 고객의 비교 목록에 있는 제품이 현재 가장한 고객에게 잘못 할당되었습니다.  수정 후 올바른 로그인한 고객에 대해 비교 목록이 올바르게 로드됩니다.

_ACP2E-3818 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

#### [B2B] 공유 카탈로그 저장이 더 이상 사용되지 않는 기능 오류를 반환합니다.

관리자가 공유 카탈로그에서 제품 할당을 취소할 수 있습니다.
이전에는 공유 카탈로그에서 긴 제품 SKU가 많은 제품의 할당을 취소하면 오류가 발생했습니다

_ACP2E-4097 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ab891304)_

#### [클라우드] 사이트 맵 생성 성능이 크게 저하되었습니다.

이미지가 있는 제품의 사이트 맵 생성으로 인해 더 이상 기하급수적인 둔화가 발생하지 않습니다. 이전에는 이미지 포함이 활성화된 스토어에 대해 사이트맵을 생성하면 처리 시간이 길어졌습니다.

_ACP2E-4153 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

### 제품, 세금

#### 고정 제품 세금(FPT)이 구성 가능한 제품과 함께 별도로 표시되지 않음

옵션을 선택한 후 구성 가능한 제품에 대해 고정 제품 세금(FPT)이 별도로 표시되지 않던 문제를 수정했습니다. 이제 FPT 분류가 제품 목록 및 세부 사항 페이지에 올바르게 표시되며, 단순 제품의 표시 형식과 일치합니다.

_AC-13171 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b5e99d20)_

### 프로모션

#### 구매 X 장바구니 가격 규칙을 가져오면 다른 규칙이 이미 적용되었을 때 잘못된 할인이 추가됩니다.

X Get Y 장바구니 가격 구매 규칙이 다른 규칙이 이미 할인된 후에도 원래 제품 가격을 사용하여 할인을 계산하던 문제를 해결했습니다. 업데이트에서는 이제 두 번째 규칙이 조정된 가격에 할인을 적용하여 여러 프로모션이 활성 상태일 때 정확한 총 할인을 제공합니다.

_AC-12325 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### GraphQl 고객 요청을 통해 고객 주문에 대해 적용된 주문 항목 할인(_To)을 가져오는 도중 오류 발생

이전에는 GraphQl을 통해 고객 주문에 대해 할인이 apply_to로 적용되던 경우, 이제 가 수정되고 할인이 적용된 적절한 고객 주문 데이터를 가져오는 내부 서버 오류가 관찰되었습니다

_AC-14888 - [GitHub 문제](https://github.com/magento/magento2/issues/39963) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQl 고객 요청을 통해 고객 주문에 대한 주문 항목 쿠폰 코드를 가져오는 도중 오류 발생

GraphQL을 통해 쿠폰 세부 사항이 있는 주문을 가져오면 내부 서버 오류가 반환되던 문제를 수정했습니다.
이제 쿼리가 성공적으로 실행되고 응답에 올바른 쿠폰 정보를 반환합니다.

_AC-14889 - [GitHub 문제](https://github.com/magento/magento2/issues/39962) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

#### `[Cloud][experienceleague]` 카탈로그 가격 규칙이 적용되지 않음

`special_price`이(가) 웹 사이트 수준(&quot;모든 스토어 보기&quot;가 아님)에서만 설정된 경우 고정 카탈로그 가격 규칙이 적용되지 않았습니다. `special_price`이(가) 웹 사이트의 기본 스토어를 먼저 확인하여 웹 사이트 수준에서 설정된 경우 이제 고정 카탈로그 가격 규칙이 올바르게 적용됩니다.

_ACP2E-4372 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath()에 entity_type 필터링이 없으므로 CMS 페이지가 범주 URL의 제품으로 처리됩니다.

DynamicStorage가 entity_type을 기준으로 필터링하지 않아 CMS 페이지가 범주 URL의 제품으로 잘못 처리되던 문제가 해결되었습니다. 잘못된 형식의 URL은 이제 CMS 콘텐츠를 제공하는 대신 404를 올바르게 반환합니다.

_AC-14991 - [GitHub 문제](https://github.com/magento/magento2/issues/39996) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/64823f95)_

#### 제품 URL에서 카테고리 경로를 활성화하면 스토어 전환기가 여러 방식으로 중단됩니다.

제품 URL에서 카테고리 경로를 활성화하면 스토어 전환기가 실패하는 문제가 해결되었습니다. 이제 스토어 전환은 홈페이지로 리디렉션하거나 오류를 반환하지 않고 스토어 보기 간에 제품 URL을 올바르게 확인합니다.

_AC-15110 - [GitHub 문제](https://github.com/magento/magento2/issues/40037) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a7ef6300)_

#### ProductRepository getById에 정의되지 않은 배열 키

123abc와 같은 잘못된 ID로 ProductRepository::getById()가 호출되어 &quot;정의되지 않은 배열 키&quot; 오류가 발생하는 경우 문제가 발생했습니다.
Magento 2.4.9-alpha3가 수정된 후 이러한 요청은 이제 예외를 발생시키는 대신 404 페이지를 올바르게 반환합니다.
QA가 유효한 ID와 잘못된 ID로 확인되었으며 추가 문제는 관찰되지 않았습니다.

_AC-15345 - [GitHub 문제](https://github.com/magento/magento2/issues/40146) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### Storefront 비교 제품에서 Google SEO 오류 생성 - 링크가 크롤링되지 않음

href 특성이 없거나 잘못 바인딩되어 있어 검색 엔진에서 상점 &quot;제품 비교&quot; 링크를 크롤링할 수 없었던 SEO 문제를 해결했습니다. 업데이트는 이제 링크에 유효한 크롤링 URL이 포함되어 있는지 확인하여 사이트 검색 기능을 개선하고 Google SEO 감사를 전달할 수 있도록 합니다.

_AC-15547 - [GitHub 문제](https://github.com/magento/magento2/issues/40185) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/c95ed7d7)_

#### REST API를 통해 제품 url_key를 업데이트해도 301 URL 다시 쓰기가 생성되지 않음

REST API를 통해 제품의 URL 키를 업데이트할 때 &quot;URL 키가 변경된 경우 URL에 대한 영구 리디렉션 만들기&quot; 설정이 예로 설정되면 제품 URL 재작성은 이전 URL에서 새 URL로 리디렉션을 만듭니다.

_ACP2E-3900 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

#### [클라우드] 사이트 맵 생성이 끝나지 않음

수정 전에, 카탈로그에 백만 개 이상의 제품이 포함된 경우 사이트 맵 생성을 성공적으로 완료할 수 없습니다. 수정 후 사이트 맵 생성은 낮은 메모리 할당과 매장당 최대 100만 개의 제품으로 완료됩니다.

_ACP2E-3902 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### FAQ 페이지에 대한 EN에서 FR로 [Cloud] 스토어 전환기가 작동하지 않음

스토어 보기 간 전환으로 사용자가 번역된 해당 CMS 페이지 대신 홈 페이지로 리디렉션되는 문제를 해결했습니다. 이제 스토어 전환기가 대상 스토어에서 URL 재작성을 확인하여 올바른 리디렉션이 수행되는지 확인합니다(예: 영어의 FAQ 페이지 → 프랑스어의 FAQ 페이지).

_ACP2E-4112 - [GitHub 문제](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [클라우드] 이전 사이트 맵 생성 비활성화

이제 표준 사이트맵 생성 프로세스와 새로 구현된 배치 모드 간에 전환하는 새 구성 옵션을 사용할 수 있습니다. 이러한 향상된 기능을 통해 사이트 맵 생성 워크플로우에서 유연성과 확장성을 높일 수 있습니다.

_ACP2E-4132 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 의심스러운 요청으로 exception.log에서 예외가 발생합니다.

악의적이거나 잘못된 URL 요청으로 인해 데이터베이스 데이터 정렬 오류가 발생하고 예외 로그가 채워지는 문제가 해결되었습니다.
이전에는 잘못된 문자 인코딩이나 지원되지 않는 문자가 포함된 의심스러운 요청이 수신되면 시스템에서 디코딩하고 처리하려고 하면 MySQL 데이터 정렬이 충돌했습니다.

_ACP2E-4328 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2687b487)_

### 판매

#### 주문 수준에서 선물 메시지를 사용할 수 있지만 사용자가 데이터를 입력하지 않고 주문을 하면 관리자의 [보낸 사람 이름] 및 [받는 사람 이름]에 고객의 이름과 성이 표시됩니다.

선물 메시지를 입력하지 않아도 선물 메시지 발신자 및 수신자 필드에 고객 이름이 자동으로 채워지는 문제가 해결되었습니다. 사용자가 세부 정보를 제공하지 않는 경우 필드는 비어 있습니다.

_AC-15140 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a8cf637b)_

### 검색

#### &quot;범주 페이지 매김 기억&quot;을 사용하여 카탈로그 검색에서 &quot;양식 재제출 확인&quot;

도구 모음 설정을 수정한 후 제품 페이지에서 카탈로그 검색 결과 페이지로 다시 이동하면 &quot;범주 페이지 매김 저장&quot;이 활성화된 경우 더 이상 &quot;양식 재제출 확인&quot; 대화 상자가 트리거되지 않습니다.
이전에는 정렬 순서와 같은 도구 모음 매개 변수를 변경한 후 검색 결과 페이지로 돌아갈 때 브라우저 오류가 발생하거나 양식 재제출에 대한 경고가 발생했습니다.

_ACP2E-4208 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

#### 집계된 검색 필드 &quot;_search&quot;가 더 이상 검색 쿼리에 사용되지 않습니다.

이제 전체 텍스트 검색은 단일 필드에서 조건을 충족하도록 요구하지 않고, 검색 가능한 모든 필드에서 최소값 일치 조건이 일괄적으로 충족되어야 하는 경우 일치하는 제품을 반환합니다.

_ACP2E-4285 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/cbca0396)_

### 보안

#### 내부 서버 오류

이제 Magento은 비동기 REST 끝점 POST /rest/default/async/V1/carts/mine/items를 사용할 때 고객의 장바구니에 제품을 성공적으로 추가합니다. 이전에는 이 비동기 &quot;장바구니에 추가&quot; 요청으로 인해 내부 서버 오류가 발생했으며, Magento에서 다음 오류가 기록되었습니다. 오류: app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162에서 null에 대한 멤버 함수 setFinalPrice()를 호출했습니다.

_AC-16344 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### 번들/병합된 JS가 SRI 해시의 일부가 아님

수정 이전에 생성된 번들 또는 병합된 파일이 SRI 해시 목록에 추가되지 않았습니다. 이제 파일이 SRI 해시에 제대로 추가되고 있습니다.

_ACP2E-3854 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] newrelic에서 쓰기 가능한 권한 문제를 가져왔습니다.

수정 전에는 예외로 인해 로그가 복잡해졌습니다. 이 수정 사항을 적용한 후 로그는 이제 정리되었으며 예외가 없습니다.

_ACP2E-4296 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/61c96348)_

### 배송

#### 몇 개의 대변 메모 후 출하할 수량이 잘못됨

여러 대변 메모 후 납품할 수량 값이 잘못 계산되어 환불 항목을 납품할 수 있었던 문제를 해결했습니다.
이제 시스템은 출하 및 환불 품목을 기준으로 잔여 출하 가능 수량을 정확하게 갱신하여 유효하지 않은 출하를 방지합니다.

_AC-1479 - [GitHub 문제](https://github.com/magento/magento2/issues/34289) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### 배송 방법 로드 시 발생할 수 있는 성능 문제

요청할 때 활성 운송업자만 로드되도록 하여 배송 방법 로드 프로세스를 최적화했습니다. 기존에는 모든 운송수단에 대한 공장이 초기화돼 불필요한 성능 오버헤드가 발생했다. 이 수정 사항은 활성 운송 회사만 조건부로 로드하여 로드 시간과 리소스 사용량을 줄임으로써 효율성을 향상시킵니다.

_AC-15415 - [GitHub 문제](https://github.com/magento/magento2/issues/40153) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/cc0ec250)_

#### [문제] 상업용 대상은 주거용으로 취급되지 않아야 합니다.

UPS REST 배송 통합에서 상업용 목적지가 거주지로 잘못 처리되는 문제가 해결되었습니다. ResidentialAddressIndicator는 현재 거주 주소에 대해서만 UPS 요금 요청에 포함되어 있으며, 의도하지 않은 거주 할증료를 방지하고 정확한 상업 배송 요금을 보장합니다.

_AC-16285 - [GitHub 문제](https://github.com/magento/magento2/issues/40314) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40307)_

#### UPS 배송 레이블을 생성하는 도중 예외 발생

수정 경고: UPS 배송 레이블을 만드는 동안 배열에서 문자열로 변환

_ACP2E-3676 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Magento_Fedex 코어 모듈이 새 토큰 가져오기 요청을 보내기 전에 올바른 활성 토큰을 확인합니까?

Adobe Commerce은 액세스 토큰에 대해 FedEx API 서비스에 더 이상 많은 요청을 하지 않습니다. 이전에는 액세스 토큰이 여전히 유효하더라도 Adobe Commerce이 항상 FedEx API에 새 요청을 하여 속도 제한 문제를 일으켰습니다.

_ACP2E-3930 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### 스테이징 및 미리보기

#### 카탈로그 가격 규칙의 영향을 받는 장바구니의 제품 가격은 스테이징 업데이트에 의해 규칙이 조정될 때 변경되지 않습니다

스테이징 업데이트를 통해 카탈로그 가격 규칙을 수정한 후 장바구니의 제품 가격이 완전히 업데이트되지 않던 문제를 수정했습니다. 이전에는 중앙 장바구니에서 이전 값을 표시하는 동안 업데이트된 가격이 요약 섹션에만 표시되었습니다. 이제 수정된 규칙이 전체 장바구니에 대한 제품 가격을 올바르게 업데이트합니다.

_AC-15304 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/913bf1a6)_

#### 범주에 대해 예약된 업데이트가 삭제되면 상위 범주에 대해 하위 항목 수가 감소되지 않습니다

범주에 대한 예약된 업데이트를 삭제해도 상위 범주의 하위 항목 수가 줄어들지 않아 예약된 업데이트 또는 하위 범주가 제거될 때 카운트가 올바르게 업데이트되는 문제가 수정되었습니다.

_AC-15670 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ef666cd9)_

#### 범주에 대한 예약된 업데이트를 편집할 때 상위 범주에 하위 금액이 추가됩니다

하위 범주에 대한 기존 예약된 업데이트를 편집하면 데이터베이스의 상위 범주에 대한 children_count가 잘못 증가하던 문제를 수정했습니다. 이 문제로 인해 업데이트를 저장한 후 부정확한 범주 계층 구조 데이터가 발생했습니다. 수정 후에도 자녀 수가 올바르게 유지되며 더 이상 예기치 않게 증가하지 않습니다.

_AC-16239 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8670a2b4)_

#### 예약된 업데이트를 미리 보면 관심 있는 스토어 보기가 아닌 알파벳 순서로 첫 번째 스토어 보기가 열립니다

수정 전에는 예약된 업데이트 미리보기가 할당된 스토어 보기가 아닌 알파벳 순서로 첫 번째 스토어 보기에서 열렸습니다.
수정 사항이 적용되면 이제 CMS 블록 스테이징 업데이트에 지정된 스토어 보기에서 미리보기가 올바르게 열립니다.

_ACP2E-3671 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

#### 범주 권한이 활성화된 예약된 제품 업데이트를 미리 볼 수 없음

수정 전 활성화된 향후 제품이 미리보기 모드에서 표시되지 않았습니다. 현재 상태가 비활성화된 경우에도 표시됩니다.

_ACP2E-3786 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 카탈로그 가격 규칙 할인 금액 필드에 대한 유효성 검사 누락

이전에는 스테이징 스케줄 업데이트의 discount_amount 필드가 현재 검증 규칙으로 올바르게 검증되지 않았습니다. 그러나 이 수정 사항을 적용하면 discount_amount 필드의 유효성이 적절하게 검사됩니다.

_ACP2E-3867 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

#### 예약된 업데이트가 있는 번들 제품은 제품 저장 작업에서 번들 항목 옵션을 제거합니다.

예약된 업데이트에서 번들 제품 옵션 또는 관련 제품을 제거하면 더 이상 원래 번들 옵션 및 관련 제품에 영향을 주지 않으며 그 반대의 경우도 마찬가지입니다. 또한 업데이트 예약 후 원래 제품에서 번들 프로덕션 옵션을 제거하고 다른 옵션으로 교체해도 새로 추가된 옵션이 더 이상 제거되지 않습니다

_ACP2E-4212 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ab891304)_

#### 업데이트 예약 미리 보기에서 웹 사이트 사이를 탐색할 수 없음

이 수정 전에 사용자 정의 도메인이 있는 스토어의 콘텐츠를 미리 보는 경우 예약된 업데이트 미리 보기가 중단됩니다. 이 수정 후 사용자 지정 스토어 도메인을 있는 그대로 미리 보고 미리보기 iframe 내에서 탐색할 수 있습니다. 이 수정 사항은 제품, 카테고리, CMS 페이지 및 CMS 블록을 포함하며, `{{store url}}`Adobe Commerce 변수 및 마크업 태그[에 설명된 대로 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags) 마크업 태그를 사용하는 탐색 링크를 지원합니다.

_ACP2E-4308 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/0a3b7032)_

### 세금

#### 주문 합계가 잘못되었습니다. 가격 계산에 라운드가 적용되지 않습니다.

이제 시스템에서 price_after_discount, discount_amount 및 세금 금액을 계산할 때 를 올바르게 처리합니다.
주문의 실제 합계

_AC-11389 - [GitHub 문제](https://github.com/magento/magento2/issues/38455) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39687)_

#### [문제] 수정: 대변 메모 항목의 base_weee_tax_applied_row_amnt 값이 올바르지 않습니다.

base_weee_tax_applied_row_amnt에 적절한 setter를 사용하여 대변 메모 계산을 수정하고 세금 값이 환급 수량만 반영되도록 했습니다. 이전에는 행 금액이 부분 대변 메모 금액 대신 전체 주문 값을 잘못 사용했습니다.

_AC-12049 - [GitHub 문제](https://github.com/magento/magento2/issues/38765) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3b5ac075)_

#### 미니 장바구니의 품목에는 환전 없이 외화 가격이 표시됩니다.

이제 Mini-Cart가 통화를 올바르게 전환하고 구성된 전환율에 따라 정확한 금액을 표시합니다.

_ACP2E-4364 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/1c547060)_

### 테스트 프레임워크

#### [문제] MTF 테스트 AdminSetUpWatermarkForSwatchImageTest에서 중복된 &lt;severity> 태그를 제거합니다.

이제 시스템에서는 AdminSetUpWatermarkForSwatchImageTest에 단일 심각도 태그만 포함하므로 코드 명확성과 일관성이 향상됩니다. 이전에는 이 테스트에 동일한 심각도 태그가 두 개 포함되어 있어 필요하지 않으며 혼동을 초래할 수 있습니다.

_AC-11873 - [GitHub 문제](https://github.com/magento/magento2/issues/38504) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31862)_

#### [문제] Lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en 무시...

이제 시스템은 단위 테스트를 실행할 때 생성되는 &#39;env.php&#39; 파일을 무시하여 테스트 실행 후에도 git 상태가 깔끔하게 유지되도록 합니다. 이전에는 단위 테스트를 실행하면 새 파일 &#39;env.php&#39;가 생성되어 git 상태가 발견된 새 파일을 표시하고 더럽혀진 것처럼 보이게 했습니다.

_AC-13293 - [GitHub 문제](https://github.com/magento/magento2/issues/39304) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37631)_

#### [문제] 인터셉터 통합 테스트 문제 해결

이제 시스템은 통합 테스트에서 \Magento\TestFramework\App\Config\Interceptor 을 올바르게 식별하고 처리하므로 클래스에 플러그인이 있는 경우에도 테스트가 필요한 데이터에 액세스할 수 있습니다. 이전에는 시스템이 \Magento\TestFramework\App\Config 이 \Magento\TestFramework\App\Config\Interceptor 일 가능성을 고려하지 않았으므로 $data 속성에 액세스하려고 할 때 오류가 발생했습니다.

_AC-13305 - [GitHub 문제](https://github.com/magento/magento2/issues/39324) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37187)_

#### [문제] MFTF: captcha가 활성화된 친구 양식에 전자 메일 제출

테스트 케이스는 CAPTCHA가 활성화되어 있을 때 &quot;친구에게 이메일&quot; 양식의 기능을 해결하여 양식 제출 프로세스가 잘못되고 올바른 CAPTCHA 값에서 모두 올바르게 작동하도록 합니다.

_AC-13492 - [GitHub 문제](https://github.com/magento/magento2/issues/39462) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32830)_

#### 작성기 빌드에서 하드코딩된 고정장치 경로 실패

_AC-16488_

#### [문제] magento/magento2#: GraphQl 돌연변이. 고객 storeConfig 설정에 대한 추가 테스트 범위.

이제 시스템에서 다음 customer storeConfig 옵션에 대한 추가 테스트 범위를 추가합니다.
required_character_class_number
minimum_password_length

_AC-9370 - [GitHub 문제](https://github.com/magento/magento2/issues/37915) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/28761)_

#### AC 2.4.7-p3의 환경별 단위 테스트 오류

이 문제는 모든 버전 및 환경에서 재현되지 않는 단위 테스트 오류를 수정합니다. 이전에는 일부 단위 테스트를 수정하지 못했습니다. 라이브러리 버전이 다르거나 이후 버전에서 추가된 기능이 누락되었기 때문입니다.

_ACP2E-3712 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

### UI 프레임워크

#### [문제] 적은 파일 중 하나에서 중복된 변수를 제거합니다.

이제 시스템에서 더 적은 수의 파일에서 중복 변수를 제거하여 보다 깔끔하고 효율적인 코드를 만듭니다. 이전에는 이러한 중복 변수가 적은 파일에 있어 코드에서 불필요한 중복이 발생했습니다.

_AC-11743 - [GitHub 문제](https://github.com/magento/magento2/issues/31154) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG이 동적 행에서 비어 있습니다.

이제 다이내믹 행의 WYSIWYG 필드가 올바르게 초기화되고 채워집니다.
이전에는 동적 행(예: 디자인 구성 양식)의 WYSIWYG 필드가 비어 있거나 특정 작업 후 콘텐츠가 손실되어 데이터를 복원하는 데 수동으로 개입해야 했습니다.
AC-12336

_AC-12336 - [GitHub 문제](https://github.com/magento/magento2/issues/38893) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [문제] MIME 유형 오타 수정

gif 이미지에 대한 mime 유형 및 오타가 올바르게 처리되고 수정되었습니다

_AC-8001 - [GitHub 문제](https://github.com/magento/magento2/issues/36899) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36669)_

#### [문제] `@author`에서 금지된 `Magento_Backend` 태그를 제거하십시오.

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8814 - [GitHub 문제](https://github.com/magento/magento2/issues/37522) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36976)_

#### [문제] 검토 목록 Ajax에 직접 액세스하지 마십시오.

시스템이 를 올바르게 처리하고 검토 목록 Ajax에 직접 액세스하지 않음

_AC-9381 - [GitHub 문제](https://github.com/magento/magento2/issues/37920) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33876)_

#### 공유 쿠키가 있는 다중 스토어 설정에서 헤더 로그인/로그아웃이 업데이트되지 않음

구성 설정에 따라 로그아웃 시 로그인 헤더가 올바르게 업데이트됩니다. 고객 계정이 전역적으로 공유되는 경우 customer-data.js는 쿠키를 사용하여 &#39;mage-customer-login&#39; 값을 저장합니다. 그렇지 않으면 로컬 저장소가 사용됩니다.

_ACP2E-4149 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama가 이미지 뷰어 닫기 작업에서 미니 장바구니를 열 수 있습니다.

Fotorama 문제를 해결했습니다. 이전에는 이미지 뷰어의 닫기 작업에서 미니 장바구니가 열렸습니다

_ACP2E-4231 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e885088b)_

#### 여러 스토어가 있는 프로젝트에서 병합된 js 파일이 제대로 생성되지 않습니다.

이제 여러 스토어가 구성된 경우 JavaScript 파일 병합이 올바르게 작동합니다.
이전에는 파일이 다중 저장소 설정에서 제대로 병합되지 않아 불완전하거나 일관되지 않은 결과가 발생하기도 했습니다.

_ACP2E-4246 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/ab891304)_

### 업그레이드 - 업그레이드 호환성 도구

#### 사용되지 않는 기능: 동적 속성 Magento\Framework\Acl::$_roleRegistry 만들기

더 이상 사용되지 않는 기능 오류로 인해 업그레이드 후 관리자 패널에 액세스할 수 없습니다.
이전에는 Magento 2.4.6으로 업그레이드한 후 관리 패널에 액세스하려고 하면 다음 오류가 발생할 수 있습니다.
&quot;사용되지 않는 기능: 동적 속성 Magento\Framework\Acl::$_roleRegistry의 생성은 vendor/magento/framework/Session/SessionManager.php의 186행에서 더 이상 사용되지 않습니다.&quot;
이로 인해 관리자가 로그인할 수 없습니다.
AC-12343

_AC-12343 - [GitHub 문제](https://github.com/magento/magento2/issues/37469)_
