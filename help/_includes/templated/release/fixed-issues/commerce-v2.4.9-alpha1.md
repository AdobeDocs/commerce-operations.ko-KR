---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Adobe Commerce 해결 문제(v2.4.9-alpha1)

## v2.4.9-alpha1의 문제가 해결되었습니다.

Adobe Commerce 2.4.9-alpha1 코어 코드에서 84개의 문제가 해결되었습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

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

### 계정

#### [클라우드] 고객 계정을 만드는 동안 현재 영역 오류로 인해 삭제 작업을 사용할 수 없습니다.

잘못된 주소로 고객을 저장한 후 수정 사항이 관련되지 않은 &quot;현재 영역에 대해 삭제 작업이 금지됨&quot; 대신 무효화 이유를 설명하는 메시지를 반환합니다.

_ACP2E-3791 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6ea61121)_

### 관리자 UI

#### [문제] 역할 트리로 사용자 경험 개선

이 끌어오기 요청에는 모두 축소, 모두 확장 및 선택한 항목으로 분기 확장을 위한 버튼이 추가됩니다. 이 기능은 범주 트리(카탈로그 -> 재고 -> 범주)에서 제공하는 기능과 유사합니다.

_AC-14020 - [GitHub 문제](https://github.com/magento/magento2/issues/39654) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot; 헤더는 &quot;Symfony\Component\Mime\Header\MailboxHeader&quot;의 인스턴스여야 합니다(got &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [GitHub 문제](https://github.com/magento/magento2/issues/39823) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1e14bd72)_

#### 그리드를 사용하여 세율을 일괄 삭제하는 기능을 제공합니다

이제 관리 사용자는 관리 세율 그리드에서 여러 세율을 동시에 삭제할 수 있습니다.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub 문제](https://github.com/magento/magento2/issues/33399) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33484) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 조건 SKU가 있는 장바구니 가격 규칙은 SKU의 &quot;선행 0&quot;을 고려하지 않습니다(sku: 01234은 1234와 동일).

이제 시스템은 SKU의 &quot;선행 0&quot;을 고려하여 조건 SKU를 사용하여 장바구니 가격 규칙을 올바르게 처리합니다

_AC-9428 - [GitHub 문제](https://github.com/magento/magento2/issues/37919) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39525)_

#### 다중 선택을 위한 기본 속성 옵션 값 동작 문제

이전에는 여러 옵션 속성에 대한 고정 기본값이 제대로 저장되지 않았습니다. 이제 수정 후 값이 데이터베이스에 제대로 저장됩니다.

_ACP2E-3523 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 백엔드 관리 메뉴 자막이 표시되지 않음

이제 주 메뉴 그룹의 모든 제목이 올바르게 표시됩니다. 기존에는 메인 메뉴의 두 번째 또는 세 번째 열에 하나의 링크 그룹만 포함된 경우 그룹 제목이 표시되지 않았다.

_ACP2E-3540_

#### 관리자의 제품 수량을 장바구니로 다시 이동하는 동안 문제가 발생했습니다.

관리자에서 주문을 생성할 때 사이드바의 고객 장바구니 내 제품은 주문에 추가되어도 사라지지 않습니다.

_ACP2E-3563 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/c8ba4ab1)_

### 관리자 UI, B2B

#### 고객 헤더로 B2B 로그인에 여전히 Magento 브랜딩이 있음

이전에는 상점 헤더 표시에 Magento 브랜딩이 &quot;이제 &lt;store name>에서 &lt;customer name>(으)로 연결되었습니다&quot;라는 메시지가 표시되었습니다. 이제 수정되었으며 머리글에 ADOBE 브랜딩이 표시됩니다.

_AC-14361 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fadcfa8b)_

### 관리자 UI, 콘텐츠

#### 이미지를 삽입하는 동안 &quot;미디어 자산 경로에 대한 렌디션을 만들 수 없음&quot; 예외가 발생했습니다.

미디어 갤러리 이미지 최적화 구성의 최대 너비 및 최대 높이 값을 제거한 후 이미지 최적화 프로세스 중에 더 이상 오류가 발생하지 않습니다.

_ACP2E-3781 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

### 관리자 UI, 보안

#### 취약한 암호 관리

동일한 암호를 사용하는 경우 관리자 사용자를 저장할 수 없습니다. 이전에는 제대로 확인하지 않고 저장되었습니다.

_ACP2E-3657 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 관리 UI, 보안, 스테이징 및 미리보기

#### 컨텐츠 스테이징에 대한 작업 로그

이제 작업 로그에 스테이징 업데이트 활동이 표시됩니다. 이전에는 스테이징 업데이트 로그가 관리 작업 로그에 기록되지 않았습니다.

_ACP2E-3679_

### B2B

#### PayFlow Pro 신용 카드 결제 방법으로 협상가능 견적을 통해 체크아웃 진행

_AC-11973_

#### 견적 이름 변경 후 성공 메시지가 간헐적으로 사라짐

_AC-13447_

#### 총계 계산에는 세액이 포함되지 않습니다

교차 거래가 활성화된 기존 구매 발주의 위치에 주문 합계가 포함됩니다.

_ACP2E-3727_

#### REST API를 통해 B2B 공유 카탈로그에서 범주 할당을 취소하면 속도가 느립니다

이제 B2B에서 카테고리 지정을 해제할 때 성능이 크게 향상됩니다. 이전에는 B2B 공유 카탈로그에서 범주 할당을 취소하는 데 시간이 오래 걸렸습니다.

_ACP2E-3796_

#### B2B의 새 설치 패치 성능 문제

company_structure 테이블에서 많은 레코드(~10만+)를 처리할 때 B2B 1.5.2로 업데이트한 후 Magento_Company 모듈을 업그레이드하는 데 시간이 너무 오래 걸렸던 성능 문제를 수정했습니다.

_ACP2E-3850_

### 장바구니 및 체크아웃

#### Magento 2.4.7 업데이트(미니)장바구니, 허용되는 소수 수량 없음

이제 Magento은 로케일이 NL(네덜란드어)일 때 미니 장바구니에서 소수로 수량을 업데이트할 때 을 올바르게 처리합니다

_AC-13238 - [GitHub 문제](https://github.com/magento/magento2/issues/39236) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39669)_

#### [문제] subtotal.phtml 업데이트

시스템이 subtotal.phtml을 올바른 간격으로 업데이트합니다

_AC-13907 - [GitHub 문제](https://github.com/magento/magento2/issues/39619) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39612)_

#### 손님에게 주문을 할 수 없습니다.

_AC-14241 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/27217d0e)_

#### 만료된 영구 견적은 cron job sales_clean_quotes에 의해 정리되지 않습니다.

이제 &#39;persistent_clear_expired&#39; cron 작업이 실행될 때 만료된 영구 견적이 지워집니다. 이전에는 다른 cron 작업에서 만료된 영구 견적을 지우지 않았습니다.

_ACP2E-3493 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/11be3dff)_

#### 비활성 회사에 대한 체크아웃 시 &quot;문제가 발생했습니다&quot; 오류 발생

문제 해결 이전에는 로그인한 사용자 회사가 더 이상 활성화되지 않을 경우 장바구니에서 로그아웃 작업이 제대로 완료되지 않았습니다. 이제 회사를 더 이상 사용할 수 없는 경우 로그아웃이 제대로 수행됩니다.

_ACP2E-3541 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### &quot;여러 주소로 체크아웃&quot;하면 주소 선택이 저장되지 않습니다.

멀티배송 옵션을 취소하는 경우 이 문제를 해결하기 전에 멀티배송으로 되돌릴 때 주소가 미리 선택되지 않았습니다. 이제 기본 주소가 다중 배송 화면에서 선택한 항목 중 하나로 바뀝니다.

_ACP2E-3646 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6ea61121)_

### 장바구니 및 체크아웃, SEO

#### 보조 웹 사이트에서 구입할 때 이메일의 기프트 카드 코드 URL이 올바르지 않음

이전에는, 기본 스토어가 아닌 스토어에 대한 다중 스토어 설정 및 기프트 카드가 항상 기프트 카드 청구를 기본 웹 사이트로 리디렉션했습니다. 이 수정 사항이 적용되면 이메일은 기프트 카드 청구 링크를 올바른 범위 또는 웹 사이트로 리디렉션합니다.

_ACP2E-3699_

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

#### URL 재작성으로 인해 제품 페이지에 오류가 발생합니다.

이제 URL 재작성을 할 때 제품 페이지가 성공적으로 로드됨

_AC-2950 - [GitHub 문제](https://github.com/magento/magento2/issues/35371) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39670)_

#### 범주에 제품을 추가할 때 [Cloud] 버그 발생

이제 팝업 그리드를 통해 범주에 제품을 추가할 때 페이지 매김 및 레코드 수 레이블이 올바르게 작동합니다. 이전에는 페이지 크기와 동일한 항목이 있는 단일 페이지만 로드하면 항목 선택 드롭다운에 문제가 발생했습니다.

_ACP2E-3526_

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

#### 천 단위 구분 기호로 인해 편집할 때 기프트 카드 유효성 검사에 실패합니다.

기프트 카드 금액이 1,000 이상일 때 기프트 카드 제품 유형 저장 관련 문제를 해결했습니다.

_ACP2E-3704_

### 카탈로그, GraphQL, 검색

#### Products graphql이 범주 집계에서 비활성화된 범주를 반환했습니다.

이후 제품 GraphQl 요청에 대해 수정 비활성화된 카테고리가 반환되지 않습니다.

_ACP2E-2885 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

### 카탈로그, 제품

#### [임의 버그] Fotorama 라이브러리가 로드되지 않음

이제 시스템에서 Fotorama 라이브러리가 제대로 로드되었는지 확인하므로 첨부된 모든 이미지가 예상대로 이미지 갤러리에 표시됩니다. 이전에는 Fotorama 라이브러리가 제대로 로드되지 않는 문제로 인해 첫 번째 이미지만 표시되었습니다.

_AC-12124 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/27217d0e)_

### 콘텐츠

#### 테마에 csp_whitelist.xml을 넣는 것은 작동하지 않으며 간헐적인 문제를 만듭니다

웹 사이트 영역당 CSP 허용 목록 캐싱을 구현했습니다.

_AC-13069 - [GitHub 문제](https://github.com/magento/magento2/issues/38933) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39672)_

#### 오류: 제품 로드가 있는 관리 콘텐츠 페이지 빌더의 &quot;Magento_Catalog/js/validate-product&quot;에 대한 스크립트 오류

이 PR에서는 제품 조건으로 페이지 빌더를 편집할 때 catalogAddToCart에 대한 스크립트 오류를 수정합니다

_AC-13891 - [GitHub 문제](https://github.com/magento/magento2/issues/39604) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39677)_

#### 동일한 식별자를 가진 위젯에서 선택 차단

이제 동일한 식별자 블록이 있는 경우 시스템이 위젯을 생성하는 동안 선택 블록을 올바르게 처리합니다

_AC-14132 - [GitHub 문제](https://github.com/magento/magento2/issues/39692) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39722)_

#### 테이블 접두사는 고려되지 않습니다.

_AC-14556 - [GitHub 문제](https://github.com/magento/magento2/issues/39847) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 상대적으로 작은 너비의 이미지를 업로드할 수 없습니다.

시스템에서 더 이상 이미지 크기를 이미지 높이까지 상대적으로 작은 너비로 조정하지 못합니다.

_ACP2E-3558 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9608ca21)_

#### 원격 저장소 경로 스타일 구성에 대한 구성 경로가 잘못되었습니다.

수정 후 원격 저장소 경로 스타일 구성을 설정하면 실제 AWS S3 경로 스타일 구성에 영향을 줍니다.

_ACP2E-3734 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 프레임워크

#### 비활성화된 모듈의 코드를 컴파일하고 있습니다.

이 가져오기 요청은 코드를 컴파일하기 전에 비활성화된 모듈을 이스케이프 처리합니다.

_AC-10933 - [GitHub 문제](https://github.com/magento/magento2/issues/38241) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39723)_

#### Magento_Theme title.phtml 템플릿이 PHP 8.2에 적합하지 않습니다.

이 끌어오기 요청은 Php 8.x에서와 같이 null 머리글로 생성된 CMS 페이지가 null을 trim()에 전달하면서 예외 발생: 더 이상 사용되지 않는 기능: trim(): 유형 문자열의 매개 변수 #1($string)에 null 전달 시 문제를 해결합니다.

_AC-12856 - [GitHub 문제](https://github.com/magento/magento2/issues/39092) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39398)_

#### Lock Provider에 파일 스토리지를 사용하면 정리 작업 없이 파일 디렉토리가 계속 늘어납니다.

이 가져오기 요청으로 인해 하루에 한 번 실행되는 새 cron 작업이 도입되고 지난 24시간 동안 수정되지 않았으므로 안전하게 제거할 수 있는 잠금 파일이 검색됩니다. 이렇게 하면 잠금 파일 디렉터리의 내용이 제어됩니다.
이 cron 작업은 잠금 공급자가 파일을 사용하도록 구성된 경우에만 실행되며, 데이터베이스(기본값, Zookeeper 또는 캐시)가 사용되는 경우에는 실행되지 않습니다.

_AC-13367 - [GitHub 문제](https://github.com/magento/magento2/issues/39369) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39372)_

#### [문제] 정리: 메서드 호출에서 void 반환 값을 사용하지 마십시오.

이 PR은 사소한 정리를 수행합니다. 때때로 아무 것도 반환하지 않는 메서드(void)를 호출한 다음 해당 결과 값을 사용합니다. 그건 정말 필요없어.

_AC-13664 - [GitHub 문제](https://github.com/magento/magento2/issues/39524) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39516)_

#### [문제] [PHPDOC] Magento\Framework\Message\ManagerInterface에 대한 잘못된 phpdoc 수정

이 PR은 \Magento\Framework\Message\ManagerInterface에 대한 잘못된 phpdoc을 수정하고 \Magento\Framework\Message\Manager에서 모든 중복 phpdoc을 제거합니다(inheritdoc 구문 사용).

_AC-14312 - [GitHub 문제](https://github.com/magento/magento2/issues/39593) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39153)_

#### composer.json에서 베타 최소 안정성 제거됨

composer.json에서 베타 최소 안정성 제거됨

_AC-14450 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1cbbf187)_

#### 환경 변수를 통해 allow_parallel_generation을 설정해야 합니다.

수정 후 &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; 환경 변수를 사용하여 &quot;allow_parallel_generation&quot; 구성을 설정할 수 있습니다.

_ACP2E-3673 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

#### [클라우드] Magento 2에서 db_schema.xml 파일을 사용하여 테이블 열 유형을 Int에서 Decimal로 변경하면 오류가 발생합니다.

열 데이터 형식 변경이 제대로 작동하지 않습니다. 이전에는 &#39;id&#39; 특성이 허용되지 않는다는 오류가 발생했습니다.

_ACP2E-3709 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### Adobe의 새로운 통화(XCG) 지원

카리브해 길더(XCG)가 통화 목록에 추가됩니다.

_ACP2E-3790 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### 주문 배치에 대한 GraphQL 응답에는 예외 메시지가 포함되지 않습니다

다른 형식으로 오류를 반환하는 이전 변경 사항을 되돌렸습니다. 이제 잠재적인 오류가 GraphQL 스키마를 손상시키지 않고 일관된 방식으로 반환됩니다. 이는 알려진 BIC로 추가되어야 하며, ACP2E-3399의 PM에 의해 승인된다

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

### 가져오기/내보내기

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

### 인벤토리/MSI

#### 체크아웃 시 주소가 변경되면 스토어 픽업이 최대 검색 반경을 따르지 않음

이제 배송 주소가 변경되면 &quot;매장 선택&quot;에서 미리 선택한 매장이 업데이트됩니다. 기존에는 매장을 사전 선정하면 새 배송지 주소가 선택한 매장 반경 내에 없더라도 변경되지 않았다

_ACP2E-3728 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/07620383)_

### 주문

#### null을 허용하지 않는 필드 \&amp;quot;AppliedCoupon.code\&amp;quot;예기치 않은 문제에 대해 null을 반환할 수 없습니다.

_AC-14484 - [GitHub 문제](https://github.com/magento/magento2/issues/39841) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/97b2ea42)_

#### [클라우드] magento 2.4.6-p7로 업그레이드한 후 일부 인라인 Javascript가 작동하지 않습니다

관리자의 &quot;SKU별 주문에 추가&quot;에서 &quot;삭제&quot; 버튼을 클릭하면 이제 SKU가 제거됩니다. 이전에는 &quot;SKU별 주문에 추가&quot;에서 &quot;삭제&quot; 버튼을 클릭해도 SKU가 제거되지 않았습니다.

_ACP2E-3515_

#### sales_order 테이블에서 gift_cards 직렬화된 데이터가 일치하지 않음

이제 sales_order 테이블의 gift_cards 데이터가 올바르게 일련화됩니다. 이전에는 주문이 업데이트될 때마다 연재되어 있었다.

_ACP2E-3662_

### 주문, 가격 책정

#### 책임자가 반환 생성 시 잘못된 통화 기호가 표시됨

다른 통화(EUR/USD/GBP)를 사용하는 다중 웹 사이트 설정에서 관리자의 반환 제품 선택 페이지에 이제 올바른 통화 기호가 표시됩니다. 이전에는 기본 통화 기호를 표시했습니다.

_ACP2E-3658 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 기타 개발자 도구

#### 등대 접근성 오류

이제 시스템이 100의 접근성 점수로 전달됩니다.

_AC-12783 - [GitHub 문제](https://github.com/magento/magento2/issues/39054) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39164)_

#### Captcha storefront 구성 비활성화가 Captcha js 파일을 계속 로드함

이제 storefront에 대해 captcha를 비활성화하면 시스템이 captcha js 파일을 로드하지 않습니다

_AC-14267 - [GitHub 문제](https://github.com/magento/magento2/issues/32987) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39154)_

### 패키징

#### [패키징] Fix magento/magento-coding-standard dependency+ page-builder

_ACPLTSRV-6383_

### 결제

#### [문제] 오프라인 인보이스 캡처 수정(404)

Magento 관리자의 오프라인 결제 방법에 대한 송장을 캡처하는 동안 404 페이지 오류가 수정되었습니다

_AC-13336 - [GitHub 문제](https://github.com/magento/magento2/issues/39298) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39297)_

### 성능

#### 카테고리 권한 모듈로 인해 캐싱이 차단될 수 있음

이제 타사 컨트롤러가 고객 세그먼트와 올바르게 캐시됨

_ACP2E-3721_

### 제품

#### 제품 컬렉션 - 컬렉션이 로드되거나 로드될 때 addMediaGalleryData가 getSize를 호출합니다(카운트를 사용하여 추가 DB 쿼리를 방지할 수 있음).

이 PR은 media_gallery 필드가 포함된 제품 Graphql을 호출할 때 제품 컬렉션이 이미 로드된 경우 count()를 사용하여 추가 쿼리 호출을 줄입니다.

_AC-13055 - [GitHub 문제](https://github.com/magento/magento2/issues/39111) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] cron 작업 catalog_product_alert에 대한 콜백이 없습니다.

_AC-14494 - [GitHub 문제](https://github.com/magento/magento2/issues/39800) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 페이지 빌더를 통해 제품 위젯이 포함되면 느린 쿼리가 실행됩니다

제품 SKU를 포함한 제품 위젯 만들기에 대한 쿼리가 최적화되었습니다.

_ACP2E-3449 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

#### 구성 가능한 제품으로 추가될 때 제품 이미지 크기가 조정되지 않음

이전에는 관리 패널의 구성을 통해 추가된 이미지가 최대 업로드 크기 제한을 준수하지 않아 일관성 및 관리 문제가 발생할 수 있었습니다. 이제 업로드 중에 최대 크기 제한을 준수하도록 이미지 크기가 자동으로 조정되도록 수정하여 프로세스를 간소화하고 시스템 표준을 유지 관리합니다.

_ACP2E-3504 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/df92debe)_

### 배송

#### 문서가 공식 문서에서 올바르지 않은 % 구현에 대해 업데이트되어야 합니다.

DHL Rest API 지원을 위해 devdoc을 업데이트했습니다.

_AC-14507_

#### [DHL]-REST와 XML API 통합 간의 일반 크기 설정 및 가격 차이에서 선택적 차원을 처리합니다.

_AC-14601 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1e3bde4c)_

#### UPS 배송 레이블을 생성하는 도중 예외 발생

수정 경고: UPS 배송 레이블을 만드는 동안 배열에서 문자열로 변환

_ACP2E-3676 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

### 스테이징 및 미리보기

#### 예약된 업데이트를 미리 보면 관심 있는 스토어 보기가 아닌 알파벳 순서로 첫 번째 스토어 보기가 열립니다

수정 전에는 예약된 업데이트 미리보기가 할당된 스토어 보기가 아닌 알파벳 순서로 첫 번째 스토어 보기에서 열렸습니다.
수정 사항이 적용되면 이제 CMS 블록 스테이징 업데이트에 지정된 스토어 보기에서 미리보기가 올바르게 열립니다.

_ACP2E-3671 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version 크론 동작 문제 - special_price 무시

수정 후 예약된 제품 업데이트로 특별 가격을 변경하면 견적 합계가 다시 계산됩니다.

_ACP2E-3674_

### 세금

#### 장바구니에서 선물 포장을 제거할 때 세액이 업데이트되지 않음

_AC-14637_
