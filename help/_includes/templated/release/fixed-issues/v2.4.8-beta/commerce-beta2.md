---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Adobe Commerce 수정 문제(v2.4.8-beta2)

## v2.4.8-beta2의 문제가 해결되었습니다.

Adobe Commerce 2.4.8 코어 코드에서 206개 문제를 해결했습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

* _ACP2E-3236_: 페이로드에 SKU가 없으면 비동기 작업이 실패합니다
   * _참고 사항 수정_: 페이로드에서 sku가 누락된 경우 제품 저장 오류로 인해 비동기 및 동기화 작업이 이전에 실패했습니다. 수정 후 비동기 및 동기화 제품 저장 rest api 작업이 관련 예외 메시지와 함께 실패합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] REST API를 사용하여 기본 가격을 업데이트할 수 없습니다(&#39;catalog_product_entity_decimal&#39;의 &#39;value_id&#39; 값이 올바르게 증가하지 않음).
   * _수정 참고_: 이전에 이 수정 사항에 대해 rest api /rest/default/V1/products/base-prices가 호출되었을 때 값 사이에 간격을 두고 증가 ID가 잘못 증가했습니다. 수정 후 증분 ID가 예상대로 증가합니다(증분). 또한 value_id 필드 범위가 증가했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: 제품 RestAPI를 사용하는 날짜 및 시간 특성에 대한 기본값이 설정되지 않았습니다.
   * _참고 사항 수정_: 이제 RestAPI를 통해 날짜 및 날짜 및 시간 특성에 대해 기본값이 올바르게 설정됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### API, 카트 및 체크아웃

* _ACP2E-3343_: Accept HTTP 헤더와 관련된 심각한 500 오류: Magento\Framework\Webapi\Exception
   * _참고 사항 수정_: 수정 후에는 &quot;Accept&quot; 헤더를 지정하는 데 문제가 없습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>

### API, GraphQL

* _ACP2E-3348_: 고객의 보상 포인트 업데이트를 구독하는 데 사용할 수 있는 graphQl이 없습니다.
   * _참고 사항 수정_: 이전에 이 수정 사항에 대해 GraphQL 돌연변이 및 Rest API 호출을 통해 고객 특성 reward_warning_notification을 업데이트할 수 없습니다. 이제 고객 속성 reward_update_notification과 동일하게 업데이트할 수 있습니다.

### 계정

* _AC-10886_: 관리자 암호를 업데이트했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: URL이 대문자인 경우 리디렉션 루프
   * _참고 사항 수정_: 이제 시스템에서 URL의 대문자를 소문자로 자동 변환하여 홈 페이지에 액세스할 때 리디렉션 루프가 발생하지 않도록 합니다. 이전에는 Secure Base URL에 대문자가 있으면 홈 페이지에 액세스하려고 할 때 리디렉션 루프가 계속 발생합니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: 고객 옵트인 확인란으로 로그인 확인란을 번역할 수 없습니다.
   * _참고 사항 수정_: 이제 시스템에서 &quot;고객 옵트인 확인란으로 로그인&quot; 및 &quot;고객 확인란으로 로그인&quot; 도구 설명 필드를 &quot;스토어 보기&quot; 범위에서 설정할 수 있도록 하여 다양한 스토어 보기에 대한 번역을 활성화합니다. 이전에는 이러한 필드가 &quot;웹 사이트&quot; 범위에서만 설정되어 개별 스토어 조회수에 대한 번역을 방지했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: 로그인한 후 비교 목록에 게스트 사용자로 추가된 제품이 표시되지 않습니다.
   * _참고 사항 수정_: 고객으로 로그인하기 전에 제품 비교 목록에 추가된 제품은 로그인 후 유지됩니다.
이전에는 로그인 후 게스트 사용자로 비교 목록에 추가된 제품이 표시되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: 국가 구성을 허용하면 고객 주소 구성에 문제가 발생합니다.
   * _참고 사항 수정_: 이제 국가 구성 허용을 선택하면 해당 범위를 벗어나는 국가에 영향을 주지 않습니다. 이전에 허용 국가 구성이 지정된 범위를 벗어나는 고객 주소 속성에 영향을 주었습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: 공유 선물 레지스트리는 이벤트 날짜를 1일 이전으로 표시합니다
   * _메모 수정_: 선물 등록 날짜가 상점 앞에 올바르게 표시됩니다.

### 계정, API, GraphQL

* _ACP2E-3246_: 고객 API - 로그인 실패 번호를 로그인 성공 후 0으로 재설정할 수 없음
   * _참고 사항 수정_: 이제 고객이 API 끝점을 통해 성공적으로 로그인한 후 고객 엔터티 테이블에서 실패 번호가 0으로 재설정됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>

### 계정, 관리자 UI, B2B

* _ACP2E-3038_: 제한된 관리자는 사용자 지정 공유 카탈로그를 항상 볼 수 없습니다.
   * _참고 사항 수정_: 이제 제한된 관리자는 특정 저장소에 액세스할 수 있는 경우 제품과 제품이 할당된 모든 공유 카탈로그를 일관되게 보고 관리할 수 있습니다. 이전에는 특정 상점에 대한 액세스 권한이 있는 제한된 관리자가 제품이 할당된 모든 공유 카탈로그를 항상 볼 수 없거나 저장할 수 없는 고객을 볼 수 없어서 시스템에 불일치가 발생했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>

### 계정, 장바구니 및 체크아웃

* _AC-2341_: &quot;select&quot; 사용자 지정 고객 주소 특성이 새 고객 주소에 대해 렌더링되지 않습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/34950>

### 관리자 UI

* _AC-10705_: [문제] &quot;데이터 다시 로드&quot; 데이터 단추에 대한 권한 확인 추가
   * _참고 사항 수정_: 이제 시스템에서 &quot;데이터 다시 로드&quot; 단추에 대한 권한 검사를 포함하여 해당 권한이 있는 사용자만 표시하고 액세스할 수 있도록 합니다. 이전에는 모든 사용자에 대해 &quot;데이터 다시 로드&quot; 단추가 표시되고 클릭할 수 있으므로 필요한 권한 없이 사용자가 클릭할 때 &quot;허용되지 않는&quot; 페이지가 표시됩니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38283>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38279>
* _AC-13131_: [문제] 수정 경고: 정의되지 않은 배열 키 &quot;필터&quot;
   * _참고 사항 수정_: 이제 시스템에서 새 사용자가 아직 책갈피와 상호 작용하지 않은 시나리오를 처리하여 정의되지 않은 배열 키 &quot;필터&quot; 경고가 기록되지 않도록 합니다. 이전에는 신규 사용자가 책갈피와 상호 작용하지 않으면 이 경고가 기록되었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: Validate.php 파일의 코드 변경으로 인해 특수 문자가 포함된 제품 가져오기 csv 파일이 실패합니다
   * _참고 사항 수정_: 이제 시스템에서 특수 문자가 포함된 제품 CSV 파일을 올바르게 확인하고 가져와서 데이터를 성공적으로 전송할 수 있습니다. 이전에는 제품 CSV 파일을 특수 문자로 가져오려고 하면 오류가 발생하여 가져오기 프로세스가 진행되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: 최대 암호 재설정 요청 수&quot;가 0보다 크게 설정된 경우 예: 3, &quot;제한을 초과하는 오류 메시지가 제한을 다시 시작하기 전에(즉, 두 번째부터) 전송됩니다.
* _AC-13768_: 최대 암호 재설정 요청 수가 0( 사용 안 함)으로 설정되어 있지만 &quot;한도 초과 오류 메시지가 두 번째로 전송됩니다.&quot;
* _AC-7962_: 휴대폰 보기에서 결제 시 배송 링크가 없습니다.
   * _참고 사항 수정_: 이제 시스템에서 체크아웃 제목/링크 &quot;배송&quot; 및 &quot;검토 및 결제&quot;가 모바일 보기의 페이지 맨 위에 항상 표시되도록 하여 사용자가 단계를 쉽게 탐색하고 필요한 사항을 수정할 수 있습니다. 이전에는 이러한 제목/링크가 모바일 보기에 숨겨져 있어서 사용자가 현재 단계를 확인하거나 이전 단계로 돌아가기 어려웠습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: 고객 주문 쿼리 배송 설명 created_at가 스토어에서 구성한 시간대가 아닌 +0 시간대에 반환됨
   * _참고 사항 수정_: 이제 고객 주문 쿼리를 사용할 때 시스템에서 고객의 구성된 시간대에 있는 배송 주석의 &#39;created_at&#39; 필드를 올바르게 표시합니다. 이전에는 고객이 구성한 시간대에 관계없이 &#39;created_at&#39; 필드가 +0 시간대에 표시되었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: 배송 주소 상태가 자동으로 업데이트되지 않습니다.
   * _참고 사항 수정_: 수정 전에 배송 주소 영역(또는 지역 ID)이 주소 청구 정보와 동기화되지 않았습니다. 이제 청구지 주소 정보가 변경되면 배송 주소 지역과 지역 ID가 모두 올바르게 업데이트됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: 관리자 추가/편집 사용자에서 재설정 단추가 작동하지 않습니다.
   * _참고 사항 수정_: 이전에는 관리자 사용자 추가/편집 페이지에서 재설정 단추가 작동하지 않았습니다. 이제 시스템 -> 권한 -> 모든 사용자 아래의 관리 패널에서 재설정 단추가 관리자 사용자 추가/편집 페이지에서 올바르게 작동합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: &quot;장바구니에서 허용되는 최대 수량&quot;에 대한 유효성 검사가 잘못되었습니다.
   * _참고 사항 수정_: 이전에는 `Maximum Qty Allowed in Shopping Cart`을(를) 비워 두면 여기에 빈 값이 허용되지 않지만 예외를 throw하지 않았습니다. 이 수정 사항이 적용되면 빈 문자열을 넣으면 예외가 발생하고 제품 저장이 허용되지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [페이지 빌더 미리 보기 UI 문제] 페이지 빌더 열의 단추가 올바르게 정렬되지 않습니다.
   * _참고 사항 수정_: 이제 페이지 빌더 열의 단추가 올바르게 정렬되었습니다. 이전에는 페이지 빌더 열 내에서 맞춤이 일치하지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: 순서가 지정된 제품 보고서를 내보내지 않습니다. 대신 404 오류가 발생했습니다.
   * _참고 사항 수정_: 이제 CSV 및 XML로 제품 주문 보고서 내보내기가 예상대로 작동합니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: 프로덕션 모드에서 Js 축소를 활성화한 후 콘솔에 TinyMCE JS 오류가 발생했습니다.
   * _참고 사항 수정_: 이전에는 관리 패널 내의 프로덕션 모드에서 JavaScript 축소를 활성화하면 TinyMCE 7과 관련된 JavaScript 오류가 브라우저 콘솔에 표시되어 기능과 사용자 환경에 영향을 주었습니다. 이제 이 문제가 해결되어 JS 축소가 활성화된 경우에도 TinyMCE 7이 오류를 생성하지 않고 원활하게 작동할 수 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: ACP2E-3375 수정 사항을 완전히 완료하기 위한 추가 변경 요청
   * _메모 수정_: &#39;-
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>

### 관리자 UI, 결제/결제 방법, 주문

* _AC-13520_: PayPal 스마트 단추 순서 후 거래 탭에 거래 승인이 표시되지 않습니다.
   * _참고 사항 수정_: 이제 PayPal 스마트 단추를 사용하여 주문을 넣으면 시스템에서 트랜잭션 탭에 트랜잭션 인증을 올바르게 표시합니다. 이전에는 인증 트랜잭션이 &quot;승인&quot; 버튼을 클릭한 후 트랜잭션 탭에 표시되지 않고 &quot;승인&quot; 유형의 새 트랜잭션이 만들어지지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### 관리자 UI, 스테이징 및 미리보기

* _ACP2E-3424_: [클라우드] 누락된 이미지가 있는 템플릿을 제거하면 pub/media가 삭제됩니다.
   * _참고 사항 수정_: 이 수정 사항에 대한 이전에 pagebuilder 템플릿에 대한 미리 보기 이미지 이름이 없으면 pub/media 폴더가 삭제되었습니다. 수정 후에는 템플릿만 삭제되고 미리보기 이미지(있는 경우)가 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/보고

* _AC-9922_: Google Analytics CSP 오류 https://region1.analytics.google.com
   * _참고 사항 수정_: 이제 Google Analytics이 활성화된 경우 시스템에서 &#39;https://region1.analytics.google.com&#39;에 대한 연결을 올바르게 허용하므로 CSP(콘텐츠 보안 정책) 오류가 발생하지 않습니다. 이전에는 Google Analytics을 활성화하고 EU에서 웹 사이트를 보면 &#39;https://region1.analytics.google.com&#39;에 대한 연결 거부로 인해 CSP 콘솔 오류가 발생했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_: 사용자 지정 옵션을 사용하여 구성 가능한 제품에 대한 GTM의 dataLayer에 addToCart 이벤트가 없습니다.
   * _참고 사항 수정_: 이전에는 구성 가능한 제품에 대해 addToCart 이벤트가 트리거되지 않았습니다. 이제 이벤트가 GTM dataLayer 변수에 올바르게 추가됩니다.
* _ACP2E-3183_: NewRelic 브라우저 모니터링 inlineJS 스크립트로 인해 CSP 오류가 발생합니다
   * _참고 사항 수정_: 이제 CSP(콘텐츠 보안 정책) 준수를 위해 APM 에이전트 대신 응용 프로그램에서 NewRelic Browser Monitoring 스크립트가 삽입됩니다. 이전에는 APM 에이전트에서 삽입한 NewRelic 브라우저 모니터링 스크립트가 CSP를 준수하지 않아 스크립트가 실행되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: sales_bestsellers_aggregated_daily 테이블에 대한 INSERT 쿼리가 큰 판매 주문 거래량이 있는 프로젝트에서 느려집니다.
   * _참고 사항 수정_: 이전에는 베스트셀러 집계 일일 보고서를 대량으로 주문하면 생성하는 데 많은 시간이 소요되었습니다. 이제 보고서가 적시에 생성됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: 잘못된 통화 기호를 표시하는 주문 보고서
   * _참고 사항 수정_: 주문 보고서의 주문 금액에 대한 통화 기호가 통화/옵션/기본에서 잘못 사용되었습니다. 이제 정확한 보고를 위해 통화/옵션/기본값을 사용하도록 수정되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cloud] 쿠폰 사용 보고서에서 잘못된 계산
   * _참고 사항 수정_: 이제 쿠폰 보고서 그리드의 판매 합계가 &quot;할인 세금 보상 금액&quot;과 &quot;배송 할인 세금 보상 금액&quot;을 모두 통합하여 정확하게 계산됩니다. 이전에는 이러한 금액이 계산에서 누락되어 판매 합계와 판매 주문 데이터 간의 불일치가 발생했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: 공유 &quot;&lt;project_id>/var/tmp&quot; 관련 문제
   * _참고 사항 수정_: Analytics DataExport 임시 파일은 sys tmp 디렉터리를 사용하게 되며, 이 디렉터리는 자주 액세스하고 변경하는 데 더 적합합니다. 동일한 서버에서 여러 인스턴스가 실행 중인 경우 충돌을 방지하기 위해 인스턴스의 고유 ID를 사용하도록 tmp 경로가 업데이트되었습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/보고, 클라우드

* _ACP2E-3187_: NR의 지표가 백그라운드 트랜잭션에 대해 오해의 소지가 있을 수 있음- ACP2E-3067의 후속 조치
   * _참고 사항 수정_: 백그라운드 트랜잭션(cron)이 구성 설정에 정의된 New Relic 앱 이름을 사용합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: 2.4.8-beta102 패키지 Enterprise 버전이 응용 프로그램 예외로 인해 실패했습니다.
* _AC-13816_: 백 엔드 관리자의 B2B 기능을 처음으로 활성화할 수 없습니다.
* _ACP2E-2139_: 부분 인덱스를 실행할 때 공유 카탈로그에 할당된 제품이 프런트 엔드에 반영되지 않습니다.
   * _참고 사항 수정_: 이제 부분 인덱싱이 완료된 후 REST API를 통해 공유 카탈로그에 할당된 제품이 바로 상점 앞에 표시됩니다. 이전에는 전체 색인 재지정 후에만 제품이 표시되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron은 아직 승인된 구매 발주에서 견적을 삭제합니다.
   * _참고 사항 수정_: 이제 구매 주문에 사용된 견적은 sales_clean_quotes cron 작업에 의해 삭제되지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: 주문 버튼이 구매 주문 세부 정보에서 사라짐
   * _참고 사항 수정_: 제품 변형에 지정된 카드의 최소 숫자가 있을 때 승인된 구매 주문의 주문 버튼이 표시되지 않는 문제가 수정되었습니다
* _ACP2E-3474_: [CLOUD] ID가 0인 엔터티(b2b 모듈 포함) 없음
   * _참고 사항 수정_: 공유된 카탈로그 기능을 사용하도록 설정하면 로그인한 사용자가 장바구니에 제품을 추가할 수 있습니다.
이전에 장바구니에 제품을 추가하면 &#39;ID = 0인 해당 엔티티가 없음&#39; 오류가 발생했습니다.

### B2B, 장바구니 및 체크아웃

* _AC-13817_: b2b 모든 기능이 활성화된 경우 장바구니에서 제품을 볼 수 없습니다.

### B2B, GraphQL

* _ACP2E-3391_: [Cloud] graphql 호출을 통해 회사를 만드는 동안 custom_attributes를 설정할 수 없습니다.
   * _참고 사항_: 수정 후 graphql 요청을 사용하여 회사를 만드는 동안 회사 관리자에 대해 &quot;custom_attributes&quot; 특성을 설정할 수 있습니다.

### 번들

* _AC-10826_: Storefront 번들 확인란 유효성 검사 오류 메시지 수가 1보다 많음
   * _참고 사항 수정_: 이제 번들 제품에 대한 확인란 옵션을 선택하지 않고 &#39;장바구니에 추가&#39; 단추를 클릭할 때 유효성 검사 오류 메시지가 하나만 표시됩니다. 이전에는 선택하지 않은 각 확인란에 대해 여러 개의 유효성 검사 오류 메시지가 표시되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: 일부 순서 관련 테스트 사례에서 Magento 예외가 발생했습니다.
   * _참고 사항 수정_: 이제 시스템에서 다양한 테스트 사례의 &#39;sendGuestPaymentInformation&#39; 단계를 올바르게 처리하여 Magento 예외가 throw되지 않도록 합니다. 기존에는 이러한 예외가 null 결제 방식으로 인해 발생하면서 여러 테스트 사례에서 오류가 발생하기도 했다.

### 장바구니 및 체크아웃

* _AC-11914_: [문제] 판매 규칙 CartFixed 계산: 잘못된 할인 금액
   * _참고 사항 수정_: 이제 시스템에서 장바구니 고정 금액이 있는 판매 규칙에 대한 할인 금액을 올바르게 계산하므로 장바구니 항목의 변경 사항에 관계없이 정확한 할인이 적용됩니다. 이전에는 장바구니 품목을 변경할 때 할인 금액이 잘못 변경되어 예상보다 할인 금액이 크게 변경되기도 했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_: 사용 약관 확인란에서 상점 첫 화면의 HTML을 허용하지 않습니다.
   * _참고 사항 수정_: 이제 시스템에서 상점 앞의 &quot;약관&quot; 확인란 텍스트에서 HTML 서식을 지원하여 향상된 사용자 지정 및 가독성을 허용합니다. 이전에는 확인란 텍스트가 사용된 HTML 태그를 무시하고 일반 텍스트 형식으로 표시되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: 로그인한 사용자에 대해 만들어진 장바구니 가격 규칙이 로그인되지 않은 사용자에 대해 잘못 적용됩니다
   * _참고 사항 수정_: 이제 쿠키 만료로 인해 자동으로 로그아웃되는 로그인 사용자에 대한 장바구니 가격 규칙이 올바르게 제거되므로, 로그인하지 않은 사용자에게는 할인이 적용되지 않습니다. 이전에는 장바구니 가격 규칙이 사용자가 로그아웃된 경우에도 계속 적용되어 로그인하지 않은 사용자에게 잘못된 할인이 적용되었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38944>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [문제] [기능] 방지 기능을 통해 성능 최적화 대형 장바구니...
   * _참고 사항 수정_: 이제 시스템에서 중복 getActions 호출을 방지하여 대형 장바구니에 대한 성능을 최적화하여 장바구니 작업의 속도와 효율성을 개선합니다. 이전에는 여러 항목이 있는 장바구니의 경우 getActions 함수를 여러 번 호출하여 시스템 성능을 느리게 했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39292>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39290>
* _AC-13797_: 선물 레지스트리 링크가 제대로 작동하지 않습니다.
* _ACP2E-3176_: [Cloud] 빠른 주문 대량의 SKU 성능
   * _참고 사항 수정_: 장바구니 가격 규칙 조건에 사용된 특성이 모든 제품에 대해 존재하지 않고 MAP(광고된 최소 가격) 기능이 활성화된 경우 체크아웃 성능이 향상되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: 장바구니에 항목이 중복되었습니다.
   * _참고 사항 수정_: 이제 시스템에서 여러 병렬 요청을 올바르게 처리하여 동일한 제품을 장바구니에 하나의 라인 항목으로 추가하므로 동일한 SKU에 대해 별도의 라인 항목이 생성되지 않습니다. 이전에는 Storefront에서 장바구니에 동일한 제품을 추가하도록 동시에 요청하면 동일한 SKU에 대해 여러 라인 항목이 생성됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: 체크아웃 주문 전자 메일 확인이 성/이름에 입력한 전자 메일로 전송됩니다.
   * _참고 사항 수정_: 이전에 전자 메일과 유사한 패턴을 성 필드에 입력했을 때 전송된 체크아웃 주문 전자 메일 확인이 더 이상 전송되지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: 체크아웃 배송 주소 양식을 잘못된 주소로 업데이트하세요.
   * _참고 사항 수정_: 이제 shippingAddressFromData가 웹 사이트별 로컬 저장소에 저장됩니다. 이전에는, 저장소 코드가 URL에서 사용되고 동일한 게스트 세션 중에 여러 웹 사이트에서 체크아웃이 시작된 경우 체크아웃 중에 잘못된 웹 사이트의 주소가 배송 주소 양식에 자동으로 채워질 수 있었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_: [CLOUD] 주소 검색을 사용하도록 설정한 경우 체크 아웃에서 선택한 청구 주소를 보존하지 않습니다.
   * _메모 수정_: 주소 검색을 사용하도록 설정하면 결제 페이지에서 선택한 청구 주소를 유지합니다. 이전에는 &quot;고객 주소 수 제한&quot;이 1로 구성되어 있고 고객에게 두 개 이상의 주소가 있는 경우 페이지를 다시 로드하면 선택한 청구 주소가 사라졌습니다.
* _ACP2E-3407_: 기프트 카드 제품 | 장바구니 병합에서 기프트 카드를 병합하는 중입니다.
   * _참고 사항 수정_: 이제 Giftcard 제품이 장바구니에서 올바르게 병합됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: 기존 견적 데이터가 업데이트되지 않거나 표시되지 않습니다. 대신 trigger_recolect = 1일 때 새 견적 레코드를 만드십시오.
   * _참고 사항 수정_: 장바구니에 추가된 후 제품이 삭제되어 고객의 장바구니 항목이 더 이상 사라지지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### 카탈로그

* _AC-11970_: 하나의 확인란을 선택한 사용자 지정 옵션으로 구성 가능한 제품의 순서를 변경할 수 없습니다.
   * _참고 사항 수정_: 이제 시스템에서 선택한 확인란 사용자 지정 옵션 하나로 구성 가능한 제품의 순서 변경을 올바르게 처리하여 바구니를 성공적으로 만들 수 있습니다. 이전에는 이러한 제품을 재정렬하려고 하면 오류가 발생하여 장바구니에 항목이 추가되지 않았습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_: 드롭다운 옵션 누락
   * _참고 사항 수정_: 이제 값이 20개가 넘는 새 특성을 만들 때 시스템이 드롭다운에 모든 값을 올바르게 표시합니다. 이전에는 처음 20개 값 또는 다른 선택한 페이지 값만 표시되어 나머지 값이 누락되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [문제] 범주 런타임 캐시에 현재 저장소 ID를 사용합니다.
   * _참고 사항 수정_: 이제 시스템에서 범주 런타임 캐시에 현재 저장소 ID를 올바르게 사용하므로 에뮬레이션을 사용하거나 사용자 지정 코드가 다른 저장소에 범주를 저장할 때 데이터를 재정의할 수 없습니다. 이전에는 런타임에 저장된 개체가 잘못된 저장소에서 가져와서 데이터를 재정의했을 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update에서 예외가 발생합니다.
   * _참고 사항 수정_: 이제 sampledata:deploy 명령에서 —no-update 옵션을 사용할 때 시스템이 부울 값을 올바르게 허용하므로 샘플 데이터 배포 중에 오류가 발생하지 않습니다. 이전에는 시스템에서 정수 값을 잘못 예상하여 이 명령을 사용할 때 오류가 발생했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [문제] EAV 캐시 유형 사용 수정
   * _참고 사항 수정_: 이제 시스템에서 모든 관련 위치에서 EAV 캐시 유형을 올바르게 사용하여 일관되고 효율적인 데이터 캐싱을 보장합니다. 이전에는 EAV 캐시 유형을 일관되게 사용하지 않아 데이터 캐싱의 비효율성과 불일치가 발생할 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: 데이터가 비어 있는 카탈로그 고급 검색이 검색 결과 페이지로 이동[2.4.dev 분기]
   * _참고 사항 수정_: 이제 고급 검색 페이지에서 사용자가 올바르게 유지되고 데이터를 입력하지 않고 검색을 수행하려고 하면 오류 메시지가 표시됩니다. 이전에는 빈 검색을 수행하면 사용자가 검색을 수정하라는 메시지와 함께 카탈로그 고급 검색 페이지로 리디렉션됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_: 사용자 지정 테마에 대해 product_image_white_borders를 사용하지 않도록 설정한 후 흰색 테두리가 제거되지 않습니다.
* _ACP2E-3103_: 캐시로 인해 새 제품 RSS 피드가 새 제품으로 업데이트되지 않습니다.
   * _참고 사항 수정_: 이제 제품을 새 제품으로 설정하고 저장하면 새 제품에 대한 Rss 피드가 업데이트됩니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [클라우드] 실제 모바일 장치에서 두 손가락 확대/축소 및 이동 문제
   * _참고 사항 수정_: 이제 시스템이 모바일 장치에서 일관된 이미지 확대/축소 기능을 보장하여 부드럽고 예측 가능한 사용자 환경을 제공합니다. 이전에는 이미지 확대/축소 기능이 일관되지 않았으며 모바일 디바이스에서 볼 때 특정 지점 후에 갑자기 축소되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: 공유 카탈로그에서 제품 할당을 취소하면 위시리스트 제품이 지워지지 않습니다
   * _참고 사항 수정_: 이제 공유 카탈로그에서 제품을 사용할 수 없는 경우 위시리스트에 항목이 표시되지 않습니다. 이전에는 위시리스트에서 실제로 사용할 수 있는 항목이 없는 경우에도 위시리스트 페이지에 &quot;1개 항목&quot;이 잘못 표시되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: 관련 제품 모두 선택/모든 문제 선택 취소
   * _참고 사항 수정_: 이전에는 제품을 수동으로 선택한 경우 관련 제품에 대한 &quot;모두 선택&quot;/&quot;모두 선택 취소&quot; 단추가 제대로 작동하지 않았습니다. 수정 후 이러한 버튼은 이제 수동 선택 후에도 일관되게 작동하여 모든 제품을 올바르게 선택 또는 선택 취소하도록 합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] 잘못된 언어로 스톡 경고 전자 메일 번역
   * _참고 사항 수정_: 서로 다른 언어를 사용하는 여러 스토어 보기를 사용하는 웹 사이트에 대해 주식/가격 알림을 보낼 때 알림을 만든 스토어 보기의 언어가 전자 메일에 사용됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: 비활성화된 범주의 이름이 범주 트리에 더 이상 회색으로 표시되지 않습니다.
   * _참고 사항 수정_: 이전에는 비활성화된 범주가 범주 트리에서 회색으로 표시되지 않았습니다. 이제 회색 효과가 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: 구성 가능한 제품 편집 양식 로드로 인해 시간 초과 및 메모리 소진이 발생합니다
   * _참고 사항 수정_: 수정 전에 가능한 모든 특성 옵션 조합을 기반으로 구성 가능한 제품 변형이 생성되었습니다. 속성에 옵션이 많은 경우 이로 인해 시간이 오래 걸리고 리소스가 소모되는 작업이 발생했습니다. 이제 구성 가능한 제품 변형이 기존 하위 제품 속성을 기반으로 구성됩니다. 따라서 계산이 훨씬 적으므로 리소스 사용이 개선됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: [견본]을 사용할 때 Fotorama가 비디오를 올바르게 로드하지 않고 URL을 통해 옵션이 미리 선택되어 있습니다.
   * _참고 사항 수정_: 이제 URL에 선택한 옵션이 포함된 경우 구성 가능한 제품 세부 정보 페이지에서 제품 비디오가 올바르게 렌더링됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: PageBuilder 회전 위젯에 조건과 일치하지 않는 제품이 표시됩니다.
   * _참고 사항 수정_: 이제 위젯에 사용되는 제품 목록이 범주 조건을 따릅니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: 그룹의 모든 제품에 잘못된 수량이 있을 때 유효성 검사 오류가 트리거되었습니다.
   * _참고 사항 수정_: 이제 한 제품에 이전에 발생하지 않은 잘못된 수량이 있는 경우 그룹의 모든 제품에 대해 유효성 검사 오류가 올바르게 트리거됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: 프로세스가 종료되면 인덱서 임시 테이블이 정리되지 않습니다.
   * _참고 사항 수정_: 인덱서 프로세스가 종료되면 CatalogRule 인덱서 임시 테이블이 정리됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] 코어 단위 테스트 실패(2.4.7-p3)
   * _참고 사항 수정_: 이 테스트는 단위 테스트 개선 사항이므로 릴리스 정보가 필요하지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### 카탈로그, 컨텐츠

* _ACP2E-3063_: [Cloud] 캐시가 무효화되지 않습니다.
   * _참고 사항 수정_: 이전에는 CMS 페이지를 업데이트된 디자인 레이아웃으로 저장할 때 프런트 엔드에 적절히 반영되지 않았습니다. 이 수정 사항이 적용되면 디자인 레이아웃을 변경하고 CMS 페이지를 저장하면 적절한 디자인 레이아웃이 프런트 엔드에 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Cloud] 앵커/비앵커 범주가 콘텐츠 위젯에서 반전됨
   * _참고 사항 수정_: 이전에는 [표시 위치] -> [앵커 범주]를 선택했을 때 앵커와 비앵커 간의 부모-자식 관계를 반영하지 않은 모든 범주가 표시되었습니다. 이 수정 사항이 적용되면 [표시 켜기] -> [앵커 범주]에는 [앵커 범주](선택 가능)만 표시되고, [표시 켜기] -> [앵커 이외의 범주] 에는 [앵커 이외의 범주](선택 가능)가 표시됩니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: 범주가 위젯과 작동하지 않음
   * _참고 사항 수정_: 이전에는 다른 앵커/비앵커 범주에 대한 CMS 블록을 저장했지만, 이 블록은 맨 앞에 표시되었을 때 하위 범주에 대해 작동하지 않았습니다. 이 수정 사항이 적용되면 블록은 다른 카테고리의 프런트 엔드에 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d01ee51e>

### 카탈로그, GraphQL

* _ACP2E-3312_: 계층 가격이 제품 GraphQL에서 잘못된 값을 반환함(Storefront와 비교)
   * _참고 사항_: 수정 후 graphql 요청에 대해 반환된 제품의 계층 가격은 한 항목당 가격이 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: GraphQL을 통한 범주 문제
   * _참고 사항 수정_: 수정 후 범주 graphql 쿼리는 루트 범주에 허용 권한이 없는 경우에도 허용 권한이 있는 범주를 반환합니다.

### 카탈로그, 검색

* _ACP2E-3345_: 개체를 만드는 동안 형식 오류가 발생했습니다. Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor 예외
   * _참고 사항_: 수정 후 $data를 지정하지 않고 Magento\CatalogSearch\Model\Indexer\Fulltext 클래스의 인스턴스를 만들 수 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: Magento 관리자에 저장한 후 [CLOUD] 제품 문제가 프런트 엔드에 표시되지 않습니다.
   * _참고 사항 수정_: 수정 후 긴 이름의 하위 제품이 있는 구성 가능한 제품은 상점 앞에 표시되지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### 카탈로그, 배송

* _ACP2E-3195_: 선물 등록 항목을 주문하는 동안 배송 주소가 비어 있습니다.
   * _참고 사항 수정_: 이전에는 게스트 사용자 선물 레지스트리 항목에 대해 전자 메일 기능에서 반환되면 빈 주소가 생성되었으며, 이는 주문을 할 때 잘못된 주소입니다. 이 수정 사항이 적용되면 선물 레지스트리는 로그인한 사용자/게스트 사용자 및 할당된 주소가 있는지 확인합니다.

### 콘텐츠

* _AC-12692_: 위젯 범주 트리가 올바르게 렌더링되지 않음
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39008>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: 디자인 구성 페이지에서 테마를 변경할 때 &quot;기본값 사용&quot; 메시지를 볼 수 없음
   * _참고 사항 수정_: 이제 디자인 구성 페이지에서 선택한 테마에 따라 &quot;기본값 사용&quot; 메시지를 표시하는 별도의 열이 시스템에 포함됩니다. 이를 통해 기본값 상태를 명확하고 가시적으로 확인할 수 있습니다. 이전에는 &quot;기본값 사용&quot; 메시지가 표시되지 않아 선택한 테마의 상태에 대한 혼동이 발생했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [문제]이(가) TinyMCE 플러그인과의 이전 버전과의 호환성을 다시 복원합니다(그 후)...
   * _참고 사항 수정_: 이제 시스템에서 TinyMCE 플러그인과의 이전 버전과의 호환성을 복원하므로 다른 위치에서 위젯을 사용할 때 플러그인 내에 정의된 함수를 호출할 수 있습니다. 이전에는 TinyMCE 버전 변경으로 인해 플러그인이 위젯을 객체로 반환하지 않아 위젯 인스턴스에서 특정 함수를 호출하려고 할 때 오류가 발생했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39262>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [CLOUD] 이미지 업로드 단추가 작동하지 않습니다.
   * _참고 사항 수정_: PageBuilder의 배너 및 슬라이더에 대한 이미지 업로드 단추가 예상대로 작동하지 않기 전에 단추를 누르면 로컬 파일 관리자가 열려 업로드할 이미지를 선택합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] - CMS 슬라이더가 최신 변경 사항을 반영하지 않음
   * _참고 사항 수정_: 슬라이드 편집 화면에서 저장 이벤트가 트리거되는 동안 슬라이더 목록이 새로 고쳐지도록 하여 문제를 해결했습니다. 이전에는 이 문제가 트리거되어 발생했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: 페이지 빌더를 사용하여 CMS 블록을 특정 순서로 삽입하면 CSM 페이지에 오류가 발생합니다
   * _참고 사항 수정_: 이전에는 일부 PHP 및 OS(Linux) 버전에서 PageBuilder를 통해 다른 cms 블록을 참조한 블록을 렌더링하지 못했습니다. &quot;알 수 없는 오류가 발생했습니다. 다시 시도하십시오.&quot; 이제 cms 블록의 콘텐츠가 PageBuilder 제어 콘텐츠 내에서 올바르게 렌더링됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [Cloud] 동적 블록이 제대로 작동하지 않습니다.
   * _참고 사항 수정_: 이제 로그아웃한 고객 세그먼트가 지워져 게스트 세션이 이전에 로그인한 세그먼트를 상속할 수 없습니다.
* _ACP2E-3430_: TinyMCE 7에 글꼴 크기가 없는 최신 보안 업데이트
   * _참고 사항 수정_: 이제 WYSIWYG 편집기에서 글꼴 크기 및 글꼴 모음 선택기를 사용할 수 있습니다. 이 수정 이전에는 TinyMCE 7을 사용하여 편집기 인터페이스에서 사용할 수 없었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### 고객/고객

* _AC-13060_: 고객 세그먼트 > 조건 > 제품 내역* > &quot;제품을 조회함&quot;이 작동하지 않습니다.
   * _참고 사항 수정_: 이제 조건이 충족되면 시스템에서 고객 세그먼트 아래의 &quot;제품 확인함&quot; 조건에 일치하는 등록된 고객을 올바르게 표시합니다. 기존에는 조건이 충족된 경우에도 매칭 등록 고객 수가 0에 머물렀다.
* _AC-8499_: 국가 드롭다운이 변경되면 지역 텍스트 필드가 재설정되지 않습니다.
   * _참고 사항 수정_: 이제 드롭다운 메뉴에서 국가가 변경되면 지역 텍스트 필드가 재설정되므로 이전 값이 유지되지 않습니다. 이전에는 드롭다운 목록에서 국가를 변경하면 영역 필드가 재설정되지 않아 마지막으로 저장된 값이 유지되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: 고객을 삭제해도 로그인 및 삭제된 고객에 대한 Storefront의 모든 브라우저 세션 데이터가 정리되지 않습니다.
   * _참고 사항 수정_: 이제 고객을 삭제하면 로그인한 고객과 삭제된 고객에 대한 상점 첫 화면에서 모든 브라우저 세션 데이터가 예상대로 정리됩니다. 쇼핑객은 쇼핑을 계속할 수 있고, 브라우저는 자신의 세션을 게스트 세션으로 처리합니다. 이전에는 로그인한 쇼핑객의 고객 계정이 관리자에서 삭제되면 쇼핑객의 브라우저에서 JavaScript 오류가 발생했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7d5e3906>

### 프레임워크

* _AC-10738_: 바니시 구성에서는 모든 마케팅 매개 변수를 제외하지 않습니다.
   * _참고 사항 수정_: 이제 시스템에서 바니시 구성의 모든 일반 마케팅 매개 변수를 올바르게 제외하여 정확한 추적 및 분석을 보장합니다. 이전에는 gad_source, srsltid 및 msclkid와 같은 특정 마케팅 매개 변수가 제외되지 않아 데이터 수집이 부정확해질 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [문제] 설정 중에 올바른 환경 설정만 허용:di:컴파일
   * _참고 사항 수정_: 이제 존재하지 않거나 특별히 제외된 클래스에 대한 기본 설정이 만들어지면 setup:di:compile 명령을 실행하는 동안 시스템에서 오류가 발생하여 올바른 기본 설정만 허용됩니다. 이전에는 이러한 시나리오가 자동으로 실패하여 원래 클래스와 관련된 플러그인이 무용지물이 될 가능성이 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [문제] XML을 통해 현재 링크에 사용자 지정 특성을 전달합니다.
   * _참고 사항 수정_: 이제 시스템에서 사용자 지정 특성을 XML을 통해 현재 링크에 전달할 수 있으므로 링크가 현재 페이지인 경우에도 이러한 특성이 올바르게 표시되도록 합니다. 이전에는 getAttributesHtml() 메서드가 현재 링크에 사용되지 않아 현재 페이지 링크에 대한 사용자 지정 속성이 표시되지 않았습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/30070>
* _AC-12127_: [문제] 잘못된 구성의 무한 루프를 방지합니다.
   * _참고 사항 수정_: 이제 시스템은 가상 형식 구성에서 자체 참조 매핑을 방지하여 무한 루프를 방지합니다. 이렇게 하면 자체 참조 노드를 역참조할 때 애플리케이션이 무한 루프에 걸리지 않습니다. 이전에는 가상 유형 구성이 자체 참조인 경우 애플리케이션이 무기한 회전합니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38822>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: 개체 관리자는 Magento\Csp\Model\Mode\Data\ModeConfigured에 사용되지 않습니다.
   * _참고 사항 수정_: 이제 시스템에서 ModeConfigured 개체를 만들 때 개체 관리자를 올바르게 사용하므로 이 개체에 플러그인을 사용할 수 있습니다. 이전에는 개체 관리자가 사용되지 않아 플러그인이 ModeConfigured 개체에 적용되지 않았습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38875>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: 제품 재고 및 가격 알림에서 문서 차단 댓글이 부정확합니다.
   * _참고 사항 수정_: 제품 재고 및 가격 알림에서 deleteCustomer 메서드에 대한 문서 블록 설명이 수정되어 해당 메서드가 웹 사이트의 고객이 아니라 특정 고객 및 웹 사이트와 관련된 모든 재고 제품 또는 가격 알림을 삭제함을 정확하게 반영했습니다. 앞서 댓글에는 해당 방법이 홈페이지에서 고객을 삭제하기 위한 것임을 부정확하게 명시했다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39001>
* _AC-12857_: PHP 8.2.15에서 FTP 확장을 제거함
   * _참고 사항 수정_: 이제 시스템에서 FTP 확장을 composer.json 파일에 종속성으로 포함하므로 FTP를 통해 CSV 가져오기를 성공적으로 구성할 수 있습니다. 이전에는 PHP 패키지에서 FTP 확장이 누락되어 FTP를 통해 CSV 가져오기를 구성하려고 할 때 오류가 발생했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: dev의 영역을 정의하는 기능:di:info CLI 명령
   * _참고 사항 수정_: 이제 시스템에서 개발자가 dev:di:info CLI 명령의 영역을 정의할 수 있으므로 개발 및 디버깅 프로세스가 향상됩니다. 이전에는 이 명령을 사용하여 전역 영역에 대한 정보만 표시할 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: charset 및 데이터 정렬 변경 사항으로 인해 MariaDB 11.4 버전에서 setup:upgrade가 실패했습니다.
* _AC-13279_: [문제] 캐시를 최소화하려면 모든 마케팅 가져오기 매개 변수를 제거하십시오
   * _참고 사항 수정_: 이제 시스템에서 모든 마케팅 get 매개 변수를 제거하여 캐시 사용률을 최적화하고, Varnish가 사용 중일 때 사용되는 논리를 미러링합니다. 이전에는 이러한 매개 변수로 인해 캐시 확장이 발생하고 성능이 저하될 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _참고 사항 수정_: 정확한 정보를 제공하기 위해 AllowedCountries::getAllowedCountries() 메서드에 대한 PHPDoc가 수정되어 설명서의 명확성과 유용성이 향상되었습니다. 이전에는 이 방법에 대한 PHPDoc에 잘못된 정보가 포함되어 있어 방법의 혼동이나 오용을 초래할 수 있었다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [문제] 더 이상 지원되지 않는 PHP 버전에 대한 일부 코드를 제거합니다.
   * _참고 사항 수정_: Magento에서 더 이상 지원되지 않는 PHP 버전의 코드 제거
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39361>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [문제] ImageMagick 어댑터가 php8과 호환되도록 합니다(float에서 int로의 암시적 변환).
   * _참고 사항 수정_: 이제 시스템은 이미지 크기를 계산할 때 부동 소수점을 올바르게 처리하여 float에서 int로의 암시적 변환으로 인한 오류를 방지함으로써 PHP8과의 호환성을 보장합니다. 이전에는 이미지 차원을 계산하면 부동 소수가 발생할 수 있으며, 이 경우 암시적으로 반올림되면 오류가 발생합니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [문제] [PHPDOC] 잘못된 phpdoc 수정 Magento\Framework\App\Config\ScopeConfigInterface
   * _참고 사항 수정_: 이 업데이트는 getValue 및 isSetFlag 메서드에 대한 $scopeCode 인수 형식을 정확하게 반영하도록 Magento\Framework\App\Config\ScopeConfigInterface에서 PHPDoc 주석을 수정합니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39492>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [문제] cron 오류 로깅 개선
   * _참고 사항 수정_: 이제 시스템에서 cron 프로세스에 대해 STDERR과 STDOUT을 모두 캡처하고 기록하여 cron 프로세스가 실패한 시나리오에서 중요한 진단 정보를 제공합니다. 이전에는 cron 프로세스 내에 오류 메시지가 기록되지 않았으며 별도의 프로세스에서 실행 중인 cron 그룹에 대한 STDERR 및 STDOUT이 손실되었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_: 외래 키의 경우 db_schema.xml을 통해 열 길이 수정이 작동하지 않습니다.
   * _메모 수정_: 이제 선언적 스키마를 통해 외래 키로 열을 수정해도 MariaDB에 오류가 발생하지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: 주문 레코드를 저장할 때 일부 관계 레코드가 DB에 저장됩니다
   * _참고 사항 수정_: 성능에 영향을 줄 수 있는 불필요한 업데이트 수정 쿼리가 트리거되기 전에. 수정 후 불필요한 UPDATE 쿼리가 제거되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] 관리자의 경우 콘솔에 많은 javascript 오류가 있습니다.
   * _참고 사항 수정_: 이전에는 관리 패널에서 콘솔에 Javascript 오류가 많이 발생했습니다. 이제 관리 패널에서는 콘솔에 JavaScript 오류가 발생하지 않으며 모든 기본 JavaScript 기능이 문제 없이 성공적으로 실행됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: 큐 메시지가 삭제되었습니다.
   * _참고 사항 수정_: 큐 메시지가 이제 제대로 지워지고 있습니다. 수정 전에 SQL 큐 시스템이 사용되고 있는 경우 정리 큐 메시지가 동시에 실행되고 있으면 새 메시지가 삭제되었을 수 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>

### 프레임워크, UI 프레임워크

* _ACP2E-3324_: 구성 값이 잠겨 있더라도 덮어쓸 수 있습니다.
   * _참고 사항 수정_: 이 수정 사항에 앞서 bin/magento config:set 명령을 통해 디자인 구성을 설정할 수 없으며, 잠긴 값은 표시되는 양식을 조작하여 변경할 수 있습니다. cli에서 —lock-env 또는 —lock-conf로 설정된 고정 잠금 값은 더 이상 업데이트할 수 없습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: 고객 반환 특성에 대한 번역이 각 StoreView의 GraphQL API에 반영되지 않음
   * _참고 사항 수정_: 고객 반환 특성에 대한 번역이 각 StoreView의 GraphQL API에 반영됩니다.
이전에는 각 StoreView에 대한 고객 반환 특성이 GraphQL API에 반영되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: 다중 사이트 설정에서 사용자 인증 및 사이트 간 토큰 액세스와 관련된 [클라우드] 문제
   * _참고 사항 수정_: 다중 사이트 설정의 GraphQl 고객 정보 및 장바구니 쿼리는 기본이 아닌 웹 사이트에 고객이 있는지 확인합니다.
이전에 여러 사이트 설정에서 고객이 기본값이 아닌 웹 사이트에 존재하는지 확인하지 않고 쿼리가 작동했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: customerCart를 가져올 때 [GRAPHQL] 모델 값을 지정해야 합니다.
   * _참고 사항 수정_: 이제 데이터베이스에서 견적을 사용할 수 없는 경우에도 GraphQL &#39;customerCart&#39; 쿼리에서 빈 장바구니를 만들 수 있습니다. 이전에는 빈 장바구니를 만드는 동안 국가 유효성 검사 문제로 인해 이 작업이 실패했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQl] 위시리스트 항목은 GraphQl을 통해 표시되지만 상점 앞에는 표시되지 않습니다.
   * _참고 사항 수정_: GraphQL을 통해 요청할 때 올바르게 나열되지 않는 제품을 위시리스트합니다. 이제 위시리스트 제품은 제공된 스토어 컨텍스트를 기반으로 필터링됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] 콘텐츠와 주체/링크 간 암호 재설정 이메일 불일치
   * _참고 사항 수정_: 웹 사이트 스토어에 관계없이 암호 재설정 요청을 보낼 때 고객의 계정이 등록된 올바른 스토어를 시뮬레이션하여 문제를 해결했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] 제품 GraphQL 쿼리가 현재 웹 사이트에 할당되지 않은 관련 제품을 반환합니다.
   * _참고 사항 수정_: 이전에는 graphQL 쿼리의 경우 다중 스토어 관련 제품이 제품 쿼리에 대해 제대로 표시되지 않았습니다. 이 수정 사항이 적용된 후 제품의 경우 graphQL 쿼리는 그에 따라 표시되는 다중 스토어 관련 제품을 보여 줍니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: GraphQL 헤더에서 잘못된 저장소 ID를 사용하면 치명적인 메모리 오류가 발생합니다
   * _참고 사항 수정_: GraphQL 요청에서 잘못된 스토어 코드를 보내도 더 이상 과도한 메모리 사용이 발생하지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Cloud] 2.4.7에서 빈 Graphql 응답에 대한 500 응답
   * _수정 참고_: 수정 후에는 잘못된 graphql 요청이 exception.log 파일에 로그되지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_: 최대 기본 GraphQL 쿼리 복잡성을 1000개로 늘립니다.

### GraphQL, 검색

* _ACP2E-948_: GraphQL 쿼리가 total_count 10,000개의 제품으로만 제한되는 제품 목록
   * _참고 사항 수정_: 수정 후에는 검색 결과가 10000 제품으로 제한되지 않으며 개수가 10000개 이상인 경우에도 검색 기준과 일치하는 모든 제품을 가져올 수 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, 테스트 프레임워크

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php 통합 테스트 실패
   * _메모 수정_: &#39;-
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/a4cf5e62>

### 가져오기/내보내기

* _ACP2E-3172_: 가져오기 단추가 없습니다.
   * _참고 사항 수정_: CSV에서 올바르고 잘못된 레코드가 있는 데이터를 확인한 후 가져오기 단추에 누락된 문제를 해결하십시오. 이전에는 데이터가 CSV에서 올바르고 잘못된 레코드를 확인하면 가져오기 단추가 표시되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: 내보낸 고객 주소를 가져올 수 없습니다.
   * _메모 수정_: 고객 주소 가져오기가 예상대로 진행됩니다. 이전에는 고객 계정 공유 = 글로벌인 경우, 기본 웹 사이트에 제한된 국가 목록이 있는 두 개의 웹 사이트가 있고 가져올 주소는 허용된 국가가 다른 다른 웹 사이트의 주소인 경우 고객 주소 가져오기 파일이 유효성 검사를 통과하지 못했습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] CSV 파일의 잘못된 수량은 오류를 제공하지 않습니다.
   * _참고 사항 수정_: 이제 재고 소스 가져오기로 수량 열의 숫자가 아닌 값에 대한 유효성 검사 오류가 발생합니다. 이전에는 수량 열에서 숫자 값이 아닌 재고 출처를 임포트하면 수량이 0으로 설정되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: 제품 내보내기로 인해 4G 메모리 제한이 있는 경우에도 OOM이 발생합니다
   * _참고 사항_: 이 수정 이전에 제품 특성에 사용 가능한 메모리가 4G인 경우에도 수천 개의 옵션 값이 있는 경우 제품을 내보내지 못했습니다. 이 수정 사항이 적용되면 제품 내보내기에서 csv 파일 내보내기를 완료해야 합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### 가져오기/내보내기, 성능

* _ACP2E-3476_: [Cloud] 제품 가져오기 시간이 크게 증가했습니다.
   * _참고 사항 수정_: 이 문제를 해결하기 전에 10,000개 이상의 항목이 포함된 카탈로그 제품 가져오기에서 시간이 크게 단축되었습니다. 수정 후 카탈로그 제품 가져오기가 적시에 실행됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/87d012e5>

### 설치 및 관리

* _AC-13242_: MariaDB 11.4 + 2.4.8-beta1에서 Magento 업그레이드가 실패합니다.
   * _참고 사항 수정_: 업그레이드는 오류 없이 수행되어야 합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7b336d0a>

### 인벤토리/MSI

* _ACP2E-3335_: MSI 픽업 스토어를 사용하도록 설정한 경우 주문을 전달할 수 없습니다.
   * _참고 사항 수정_: 매장 내 픽업이 있는 소스가 많은 경우 만들기 배송의 인벤토리 성능이 향상되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: Cron 다시 색인이 프론트엔드에서 제품 가용성을 업데이트하지 못했습니다.
   * _참고 사항 수정_: 이전에는 REST API를 통해 미납 주문 상태를 업데이트한 후 프런트 엔드에서 제품이 품절 상태입니다. 이제 REST API를 통해 미납 주문 상태를 업데이트하면 제품이 재고로 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: MSI가 활성화된 경우 구성 가능한 이미지 추가가 작동하지 않습니다.
   * _참고 사항 수정_: 이제 인벤토리 모듈을 사용할 때 구성 가능한 제품에 대한 이미지 업로드가 예상대로 작동합니다. 이전에는 이미지 업로드가 작동하지 않았습니다
   * _GitHub 코드 기여_: <https://github.com/magento/inventory/commit/fdf409aa>

### 인벤토리/MSI, 검색

* _ACP2E-3413_: SKU가 검색 가능한 특성으로 설정되지 않은 경우 모든 제품이 [is_out_of_stock] = 1로 인덱싱됩니다.
   * _참고 사항 수정_: 수정 후 sku를 검색할 수 없는 경우에도 카탈로그 검색 색인의 &quot;is_out_of_stock&quot;이 올바릅니다.
   * _GitHub 코드 기여_: <https://github.com/magento/inventory/commit/5b21b7af>

### 주문

* _ACP2E-3311_: [Cloud] 기본 청구 주소만 설정되지 않은 경우 한 스토어에서 관리자 주문을 만들 수 없습니다.
   * _메모 수정_: 이제 관련 오류 메시지 &quot;연결된 웹 사이트에 동일한 전자 메일 주소를 가진 고객이 이미 있습니다.&quot; 고객이 기본 청구 주소를 가지고 있지 않고 다른 스토어에서 주문을 만들려고 할 경우 이 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: 관리자가 중복된 주문 요청을 보냈습니다.
   * _참고 사항 수정_: 이전에는 관리 패널에서 &quot;주문 제출&quot; 단추를 여러 번 클릭하거나 &quot;Enter&quot; 키를 반복해서 눌러 활성화할 수 있었습니다. 이로 인해 중복 또는 주문 제출이 오류가 발생했습니다. 이제 주문이 완전히 처리될 때까지 추가 작업을 방지하여 하나의 주문만 제출되도록 합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: 관리자는 결제 방법 없이도 주문할 수 있습니다.
   * _참고 사항 수정_: 사용 가능한 결제 목록에 결제 방법이 다시 나타나면 이전에 선택한 결제 방법이 보존됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d50f6b5d>

### 주문, 결제

* _ACP2E-3233_: 관리자는 결제 방법 없이도 주문할 수 있습니다.
   * _메모 수정_: 이전에는 판매자가 결제 방법을 선택하지 않고 관리자 패널에서 주문을 할 수 있었습니다. 이제는 가맹점이 주문을 진행하기 위해 결제 방법을 요구받는다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/fd5cf3af>

### 기타

* _LYNX-426_: 동적 가격이 적용된 번들 제품에 대해 discount_percentage가 계산되지 않습니다.
* _LYNX-485_: 번들 제품 중 하나가 품절되었을 때 번들 제품에 여전히 &quot;IN_STOCK&quot;이 표시됨
* _LYNX-486_: not_available_message 및 only_x_left_in_stock에 동일한 사용 가능한 재고가 표시되지 않습니다.
* _LYNX-488_: original_row_total 필드가 잘못된 값을 반환함
* _LYNX-503_: 구성에 따라 그룹화된 제품 썸네일이 표시됩니다.     .
* _LYNX-510_: OrderAddress에서 selected_options를 쿼리하는 동안 오류가 발생했습니다.
* _LYNX-512_: original_item_price에 할인이 포함되지 않음
* _LYNX-530_: 사용할 수 없는 메시지에 사용 가능한 재고 수량이 표시되지 않습니다
* _LYNX-532_: &quot;OUT_OF_STOCK&quot; 상태가 다중 선택 옵션이 있는 사용자 지정 옵션 제품을 사용하는 단순에서 반환됩니다.
* _LYNX-533_: 오류(GQL): cart.itemsV2.items.product.custom_attributesV2가 서버 오류를 반환합니다
* _LYNX-536_: orders/date_of_first_order가 항상 null을 반환함
* _LYNX-544_: 고객은 부분적으로 배송된 주문을 취소할 수 없습니다.
* _LYNX-548_: 오류 메시지를 기반으로 주문 취소를 위한 오류 코드
* _LYNX-581_: 쿠키 관련 속성을 비공개에서 보호로 다시 이동

### 기타 개발자 도구

* _AC-12731_: dev/css/use_css_critical_path와 결합된 CSP 문제
   * _참고 사항 수정_: 이제 &#39;dev/css/use_css_critical_path&#39; 설정이 활성화된 경우에도 시스템이 체크아웃 페이지에 CSS 파일을 비동기적으로 로드하여 이러한 페이지가 적절한 CSS 스타일로 렌더링되도록 합니다. 이전에는 제한된 CSP(콘텐츠 보안 정책)를 사용하여 인라인 JavaScript을 실행할 수 없으므로 CSS 파일이 예상대로 로드되지 않았습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: 가상 형식을 사용하여 플러그 인을 구성하면 setup:di:compile 명령에서 인터셉터 메서드를 올바르게 생성할 수 없습니다.
   * _참고 사항 수정_: 이제 시스템은 가상 형식을 사용하여 플러그인을 구성할 때 인터셉터 메서드를 올바르게 생성하므로 미리 컴파일했는지 아니면 런타임 컴파일했는지에 관계없이 일관된 결과를 보장합니다. 이전에는 런타임 컴파일과 비교하여 미리 컴파일할 때 시스템에서 잘못된 결과를 생성했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: 데이터 수집기에서 파일을 다운로드할 수 없습니다.
   * _참고 사항 수정_: 백업을 다운로드하면 파일을 다운로드하는 대신 빈 페이지가 표시되지 않습니다.

### 결제

* _ACP2E-3143_: PayPal 주문 환불 결과 크레딧 메모가 중복되었습니다.
   * _메모 수정_: PayPal 결제 서비스에 대한 IPN에서 만든 대변 메모의 동시성 문제를 해결했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: 장바구니 가격 규칙이 Paypal에 대해 작동하지 않음
   * _메모 수정_: 결제 방법으로 할인을 적용하면 PayPal에 올바른 금액이 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: 특정 역할을 가진 [Cloud] 사용자가 로그인할 수 없습니다.
   * _메모 수정_: PayPal 섹션 액세스만 포함하는 역할을 가진 관리자는 이제 오류 없이 로그인할 수 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/66dea0de>

### 성능

* _AC-11932_: 기본 제품 특성 설정 문제
   * _참고 사항 수정_: 이제 시스템에서 제품 특성에 대한 기본 옵션을 선택 해제할 수 있으므로 특성에 항상 기본값이 설정되어 있지 않습니다. 이전에는 제품 속성에 대해 기본값이 설정되고 나면 이를 선택 해제할 방법이 없으므로 속성에 항상 기본값이 설정됩니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: Magento CLI에서 Symfony의 CommandLoaderInterface 지원
   * _참고 사항 수정_: 이 변경 사항은 필요할 때까지 명령을 지연된 초기화를 허용하여 Magento CLI 앱의 초기화 시간을 줄입니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/29355>

### 제품

* _AC-13173_: [문제] PHPDoc 블록의 오타 수정
   * _참고 사항 수정_: 이제 시스템에서 $helper 변수 선언에 대해 PHPDoc에서 알 수 없는 참조 변수를 올바르게 제거하여 코드 명확성과 정확성을 향상시킵니다. 이전에는 PHPDoc에서 알 수 없는 이 참조된 변수가 코드에 혼동과 잠재적인 부정확성을 초래하고 있었다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [문제] Magento >= 2.4.7에서 끊어진 번들 및 다운로드 가능한 제품 페이지 레이아웃을 수정했습니다.
   * _참고 사항 수정_: 번들 및 다운로드 가능한 제품 페이지의 레이아웃이 수정되어 모든 장치에서 일관되고 올바르게 표시됩니다. 이전에는 이러한 페이지에서 제품 정보 미디어 블록의 재배열로 인해 레이아웃 문제가 발생했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [Cloud] 범주 - 제품 추가 - 할당 - 모두 선택
   * _참고 사항 수정_: 이제 사용자는 토글을 사용하여 제품을 선택하거나 선택 취소할 수 있습니다.

### 프로모션

* _ACP2E-3139_: 할인 수량 단계(구매 X) 특성이 있는 판매 규칙으로 인해 다른 규칙이 적용되지 않습니다.
   * _참고 사항 수정_: 장바구니에 있는 제품의 수량이 규칙을 적용하기에 충분하지 않은 경우 장바구니 가격 규칙이 이전에 적용된 규칙을 취소하지 않습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: 장바구니 가격 규칙 성능 문제 - 고급 판매 규칙 모듈
   * _참고 사항 수정_: AdvancedSalesRule 필터에 대한 누락된 DB 인덱스가 추가되었습니다.
* _ACP2E-3332_: 고정 금액 할인과 &quot;최대 수량 할인이 적용됨&quot;이 포함된 판매 규칙 발행
   * _참고 사항 수정_: 장바구니의 제한된 제품 수량에 대해 고정 금액 할인이 적용되도록 구성된 경우 장바구니 규칙 할인과 관련된 문제가 해결되었습니다. 이전에는 &quot;최대 할인 적용 대상&quot; 값을 사용하여 규칙의 할인 계산에만 사용한 것이 아니라 장바구니에서 현재 항목의 가격을 계산했습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: [CLOUD] Magento 업그레이드로 인해 쿠폰이 대/소문자를 구분하게 되었습니다
   * _참고 사항 수정_: 수정 전에 쿠폰 코드를 대문자 또는 소문자를 고려하여 구성된 그대로 정확히 입력해야 했습니다. 이제 대문자 또는 소문자 코드 구성에 관계없이 백엔드에서 쿠폰의 유효성이 검사됩니다.
* _ACP2E-3349_: 장바구니 규칙 &quot;전체 장바구니에 대한 고정 금액 할인&quot;  조치가 할인을 잘못 적용
   * _참고 사항 수정_: 관리 영역에서 순서를 만드는 데 사용할 경우 쿠폰 코드는 대문자나 소문자에 관계없이 올바르게 확인됩니다. 이전에는 구성된 장바구니 규칙 코드의 정확한 문자 대/소문자와 일치하지 않으면 쿠폰 코드의 유효성을 검사하지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: 백엔드에서 제품 특성에 대한 기본 저장소 값(예상 관리자 값 대신)
   * _참고 사항 수정_: 이제 백엔드에서 제품 특성에 대한 기본 저장소 값 대신 관리자 값이 사용됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: 장바구니 규칙 &quot;전체 장바구니에 대한 고정 금액 할인&quot; 작업이 번들 제품을 추가할 때 할인을 잘못 적용합니다
   * _참고 사항 수정_: 고정 금액 장바구니 규칙이 번들 제품에 대해 제대로 적용되지 않았습니다. 이제 총 할인액을 산정할 때 묶음 아동용품을 고려하게 되어 적절한 할인액 산정이 이루어진다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: 장바구니 가격 규칙이 할인 계산을 잘못함
   * _메모 수정_: 고정 금액 할인이 이제 제대로 계산되고 있습니다. 이 문제 해결 이전에는 번들 제품에 대한 고정 금액 할인이 제대로 집계되지 않았습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: 규칙 조건에 중첩된 범주가 표시되지 않습니다.
   * _참고 사항 수정_: 수준 3 범주 아래의 중첩된 범주가 범주 조건에 대한 마케팅 규칙에 표시되지 않는 문제를 해결했습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit 및 uses_per_customer가 salesrule_coupon 테이블에서 업데이트되지 않음
   * _참고 사항 수정_: 장바구니에서 쿠폰당 사용 및 고객당 사용 규칙을 업데이트하면 이제 자동 생성된 기존 쿠폰에 영향을 줍니다. 이전에는 새 값이 새 쿠폰에만 영향을 주었습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: 장바구니 가격 규칙이 &quot;같음 또는 보다 큼&quot; 조건을 사용할 때 상위 범주를 고려하지 않습니다.
   * _참고 사항 수정_: 이제 장바구니 가격 규칙이 고급 조건에서 사용될 때 상위 범주를 올바르게 고려합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: 우선 순위가 있는 할인 계산이 잘못되었습니다
   * _참고 사항 수정_: 전체 장바구니 할인 유형에 적용되는 고정 금액의 경우 이전 프로모션에서 이미 할인된 장바구니 항목에 대해 금액이 올바르게 계산되지 않았습니다. 이제 할인이 적절히 요약됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_: 여러 장바구니 가격 규칙이 할인/특별 가격 제품과 동시에 적용되는 경우 잘못된 할인 값
   * _참고 사항 수정_: 수정하기 전에 둘 이상의 장바구니 규칙이 적용되는 경우 전체 장바구니 규칙에 대한 고정 금액이 제대로 적용되지 않았습니다. 이제 고정 금액 할인 장바구니 규칙이 제대로 적용되고 있습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1984c61c>

### 반환

* _ACP2E-3330_: [CLOUD] 제한된 관리자는 반환 메뉴와 단추를 볼 수 있습니다.
   * _참고 사항 수정_: 이제 제한된 관리자는 RMA 관련 컨트롤(메뉴 및 단추)에 액세스할 수 없습니다.
이전에는 제한된 관리자 사용자가 반환 메뉴와 단추를 볼 수 있었습니다.
* _ACP2E-3443_: 화면을 새로 고칠 때 반환 화면이 엉망입니다.
   * _참고 사항 수정_: 사용자가 화면 왜곡 없이 페이지를 새로 고칠 수 있습니다.

### 판매

* _AC-13750_: 총계 및 기본 총계가 테스트 결과 단계와 일치하지 않습니다.
* _AC-13751_: 첫 번째 장바구니 규칙이 이미 적용된 경우 두 번째 장바구니 가격 규칙이 적용되지 않습니다.

### 검색

* _AC-13053_: &quot;검색어를 입력하고 다시 시도하십시오&quot;를 가져오는 중입니다. storefront 2.4.8-beta1의 고급 검색 페이지에 오류
   * _참고 사항 수정_: 이제 제품 특성이 &quot;아니요&quot;로 설정되어 있으면 고급 검색 페이지에 검색 결과가 올바르게 표시됩니다. 이전에는 제품 속성을 &quot;아니요&quot;로 설정하고 검색을 수행하면 &quot;검색어를 입력하고 다시 시도하십시오.&quot;라는 오류 메시지가 표시되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search는 존재하지 않는 opensearch-php 분기에 따라 다릅니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: search_query 테이블의 크기가 클 때 로드 시간 프런트 엔드에 큰 영향을 미칩니다.
   * _메모 수정_: 검색 목록 페이지 로드 시간이 개선되었습니다. 수정 이전에는 최적화되지 않은 쿼리로 인해 검색 목록 페이지가 지연되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/55615e61>

### 보안

* _ACP2E-3273_: ReCaptcha V2가 독일어 체크아웃 시 잘못 표시됨
   * _참고 사항 수정_: 이전에 체크 아웃의 전자 메일 주소 아래에 있는 recaptcha가 독일어 같은 긴 단어가 포함된 언어에 대해 스타일이 지정되지 않은 것으로 나타났습니다. 이 후에 recaptcha는 나머지 영역의 모든 recaptcha 요소와 동일하게 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: 관리자 로그인 시 CAPTCHA는 일부 사용자에 대한 상호 작용이 필요하지 않습니다.
   * _메모 수정_: 관리자 로그인에 대한 ReCaptcha가 예상대로 유효합니다.

### 배송

* _AC-12938_: devdoc의 UPS REST &quot;sandbox&quot; 및 &quot;prod&quot; 설치 지침 업데이트
* _ACP2E-3340_: FedEx Track API가 REST 자격 증명으로 작동하지 않음
   * _참고 사항 수정_: 이전 FedEx 통합에는 추적 API에 추가 API 키가 필요하지 않았습니다. 이제 추적 API 키를 지원하도록 새 구성이 추가되었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] FedEx 협상 요금이 REST에서 반환되지 않음
   * _참고 사항 수정_: 수정 전, FedEx 계정에 대한 특정 요금. FedEx 문서에 따라 응답을 보내지 않았더라도 전송해야 합니다. 수정 후 계정 특정 요금은 당사의 요청을 변경하여 응답에서 전송됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/55615e61>

### 스테이징 및 미리보기

* _ACP2E-3453_: 고유한 사용자 지정 범주 특성을 사용할 때 예약된 업데이트를 업데이트할 수 없습니다.
   * _참고 사항 수정_: 범주에 고유한 특성이 있는 경우 범주에 대한 예약된 업데이트를 업데이트할 수 없는 문제가 해결되었습니다
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>

### 세금

* _ACP2E-3193_: 고정 제품 세금(FPT)이 구성 가능한 제품에서 작동하지 않습니다.
   * _참고 사항 수정_: 구성 가능한 제품 변형에 대한 FPT가 제대로 작동하는지 확인합니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/ec7e32a9>

### 테스트 프레임워크

* _AC-13362_: [문제] PHPDoc 수정 철자
   * _참고 사항 수정_: PHPDoc의 맞춤법 수정으로 인해 이제 시스템에서 IDE에서 더 이상 사용되지 않는 메서드를 올바르게 인식합니다. 이전에는 PHPDoc의 철자 오류로 인해 IDE가 특정 메서드를 더 이상 사용되지 않는 것으로 인식하지 못했습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: 세션이 만료된 후 영구 장바구니로 동작 확인
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: 통합 테스트가 실패했습니다. Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _메모 수정_: 고정 mftfs
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/078c387e>

### UI 프레임워크

* _AC-12432_: Ui 구성 요소 파일 필드
   * _참고 사항 수정_: 이제 시스템에서 UI 구성 요소 양식의 파일 필드를 올바르게 확인하므로, 파일을 선택할 때 오류 없이 양식을 제출할 수 있습니다. 이전에는 파일을 선택해도 유효성 검사가 실패하여 양식을 제출할 수 없었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38908>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [문제] js 콘솔의 날짜 형식 개선: 12시간에서 24시간으로 전환...
   * _참고 사항 수정_: js 콘솔의 날짜 형식이 개선되었습니다. 12시간에서 24시간으로 전환
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38983>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [문제] 개발자 모드에서 적은 수의 파일에 대해 sourceMap 생성 추가
   * _참고 사항 수정_: 이제 개발자 모드에서 시스템이 더 적은 수의 파일에 대한 소스 맵을 생성하므로 스타일의 소스를 더 쉽게 식별할 수 있습니다. 이전에는 서버측 컴파일이 없는 개발자 모드에서 시스템을 실행할 때 스타일의 소스를 식별하는 것이 어려웠습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/38982>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: 최소 재고 임계값으로 &quot;재고 부족&quot; 정렬에서 일관되지 않은 동작
   * _참고 사항 수정_: 이제 시스템에서 재고 수준에 따라 카탈로그의 제품을 올바르게 정렬하고 설정된 최소 재고 임계값을 준수하며 재고 부족 항목을 일관되게 목록의 맨 아래로 이동합니다. 이전에는 정렬 동작이 일관되지 않았으며 항목이 항상 재고 수준에 따라 올바른 순서로 표시되지는 않았고, 범주 계층을 저장, 새로 고침 또는 수정한 후 예상할 수 없었던 정렬 변경이 발생할 수 있었습니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: require.js 로드 문제에 대한 오류 보고 개선 제안
   * _참고 사항 수정_: 이 PR은 요구 사항이 구성 요소를 로드하지 못할 때 오류 메시지를 개선합니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [문제] 불필요한 스크립트 검토 요약 제거
   * _참고 사항 수정_: 이제 시스템은 보다 효율적이고 읽기 쉬운 코드를 위해 인라인 CSS 스타일을 사용하는 대신 등급 섹션에서 불필요한 JavaScript 스크립트를 제거하여 페이지 로드 시간을 최적화합니다. 이전에는 등급 섹션에 JavaScript 스크립트를 사용하면 페이지 로드 시간이 느려질 수 있었습니다.
   * _GitHub 문제_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: 사이트 헤더 | 고객 환영 섹션을 깨는 특수 문자
   * _참고 사항_: 수정 후 고객 환영 섹션에 특수 문자가 올바르게 표시됩니다.
   * _GitHub 코드 기여_: <https://github.com/magento/magento2/commit/1366ae5e>
