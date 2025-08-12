---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4173'
ht-degree: 0%

---
# Magento Open Source 릴리스 노트(v2.4.9-alpha2)

## v2.4.9-alpha2의 문제가 해결되었습니다

Magento Open Source 2.4.9-alpha2 코어 코드에서 109개의 문제가 해결되었습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

#### ApplySpecialPrice에서 현재까지 특별 가격이 잘못 검증되었습니다.

시스템은 특별 가격에 대해 잘 작동하며 제품 특별 가격은 관리자가 설정한 날짜 또는 REST API에 의해 서드파티 시스템에서 설정한 날짜에 만료됩니다

_AC-13130 - [GitHub 문제](https://github.com/magento/magento2/issues/39169) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39690)_

#### 잘못된 요청 본문 또는 매개 변수로 인해 &quot;내부 서버 오류&quot;가 발생했습니다.

_AC-746 - [GitHub 문제](https://github.com/magento/magento2/issues/32784) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

#### 주문 &quot;base_row_total&quot; 및 &quot;row_total&quot;은 REST API 응답에서 단일 품목 가격을 보여줍니다.

이제 동일한 여러 항목이 주문된 경우 주문 세부 사항에 대한 REST API 응답에 &quot;base_row_total&quot; 및 &quot;row_total&quot; 속성에 대한 올바른 값이 포함됩니다

_ACP2E-3874 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### API, 순서

#### [CLOUD] 주문 정보의 행 합계 표시 관련 주문 정보 000075568

항목이 완전히 할인된 경우 주문 API 응답의 row_total_incl_tax 값이 0.00 대신 거의 0에 가까운 잔차 값으로 반환되는 문제를 해결했습니다.

_ACP2E-3950 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 계정

#### 관리자 패널에서 고객 이메일을 ö 및 .swiss 도메인으로 업데이트할 때 문제 발생

_AC-13409 - [GitHub 문제](https://github.com/magento/magento2/issues/39394) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/d3ea191d)_

#### 웹 사이트/스토어별로 뉴스레터 구독 활성화 스위치가 작동하지 않음

시스템은 글로벌 수준에서 비활성화되었을 때 여러 웹 사이트/스토어 뷰가 있을 때 뉴스레터를 사용하여 구독을 올바르게 처리합니다

_AC-14283 - [GitHub 문제](https://github.com/magento/magento2/issues/39751) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39752)_

#### [문제]에서 전자 메일 공개를 제거함

이제 고객의 존재 여부와 관계없이, 계정 확인에 입력된 이메일이 필요하지 않은 경우 시스템에 잘못된 이메일을 나타내는 오류 메시지가 표시됩니다.

_AC-14561 - [GitHub 문제](https://github.com/magento/magento2/issues/39574) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39570)_

### 관리자 UI

#### 장바구니 페이지와 제품 페이지의 FPT 값은 간단한 제품에 대한 동일한 구성에 대해 다릅니다

_AC-13066 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### [견본] 모듈을 비활성화하면 다중 선택/선택 속성 옵션을 저장할 수 없습니다.

_AC-13071 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### 장바구니 페이지와 제품 페이지의 FPT 값이 동적 제품에 대한 동일한 구성에 대해 다릅니다

_AC-13075 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8953613e)_

#### 관리자의 정적 그리드에 호버 색상이 적용되지 않음

이제 마우스로 가리키면 표시되는 색상이 관리자 정적 그리드의 행에 예상대로 적용됩니다.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub 문제](https://github.com/magento/magento2/issues/35358) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35384)_

#### [스테이징2] 저장된 카드가 관리 패널에 표시되지 않습니다.

업그레이드 후 &quot;저장된 카드&quot; 결제 옵션이 백엔드 주문 배치 양식에 더 이상 표시되지 않던 문제를 수정했습니다.

_ACP2E-3830 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### 게스트 체크아웃에 대한 회사 필드 유효성 검사 실패

_AC-14987 - [GitHub 문제](https://github.com/magento/magento2/issues/40011) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

### 번들

#### 테마 간 번들 출력에서 Hugerte Editor JS 파일 제외

_AC-15128 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/43648891) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2bc584af)_

### 장바구니 및 체크아웃

#### 그룹화된 제품 프론트엔드 수량 유효성 검사가 누락되었습니다.

이제 시스템이 제대로 작동하며 음수 수량과 최대 수량을 추가하려고 할 때 유효성 검사 오류가 표시됩니다

_AC-13524 - [GitHub 문제](https://github.com/magento/magento2/issues/39479) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39480)_

#### 게스트 접두사가 견적 주소 2.4.8에 저장되지 않음

_AC-14705 - [GitHub 문제](https://github.com/magento/magento2/issues/39915) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/f1adb44e)_

#### [문제] base_price 대신 견적 항목에 대한 가격 설정

프론트엔드의 한 웹 사이트에 여러 개의 통화가 있는 경우, 시스템은 가격 대신 base_price로 설정된 견적 항목을 올바르게 처리합니다

_AC-9985 - [GitHub 문제](https://github.com/magento/magento2/issues/38094) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36878)_

#### [클라우드] 주문이 하나의 스토어 보기에서 만들어진 경우 최근 주문이 다른 스토어 보기에 표시되지 않습니다.

&quot;내 계정&quot; 페이지에 동일한 스토어 내 다른 스토어 보기의 최근 주문이 표시되지 않던 문제를 해결했습니다. 주문 검색 논리가 업데이트되어 &quot;내 주문&quot; 페이지의 비헤이비어에 맞게 모든 스토어 보기에서 일관된 주문 가시성을 보장합니다.

_ACP2E-3807 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 수량 표시 형식  번들 제품을 추가하는 동안 관리자 고객 장바구니 섹션에서 0개  

이제 고객 활동의 장바구니 섹션에 올바른 수량이 표시됩니다. 이전에는 수량이 0으로 표시되었습니다.

_ACP2E-3872 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### 장바구니 및 체크아웃, GraphQL

#### GraphQL을 통해 주문할 때 오류 코드에 메시지를 매핑하는 도중 오류 발생

존재하지 않거나 비활성 장바구니를 주문하기 위해 호출된 GraphQL은 이제 모든 스토어 보기에서 CART_NOT_ACTIVE 또는 CART_NOT_FOUND 오류 코드를 올바르게 반환하며, 이전에 번역된 오류 메시지로 인해 정의되지 않은 코드가 표시되던 문제를 해결합니다.

_ACP2E-3942 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

### 장바구니 및 체크아웃, GraphQL, 인벤토리 / MSI

#### cartItemInterface의 is_available 속성은 판매 가능한 재고가 높은 경우에도 false를 반환합니다.

is_available 속성은 매출 가능한 재고가 높을 때 true를 반환합니다. 이전에는 항상 false를 반환했습니다.

_ACP2E-3885 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### 카탈로그

#### 카탈로그 URL 리소스의 범위 버그(_getCategories)

이 PR은 범주 URL 리소스의 저장소 범위에 값이 정의되어 있지 않은 경우 기본 범위에 대체를 추가합니다.

_AC-11011 - [GitHub 문제](https://github.com/magento/magento2/issues/38393) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38394)_

#### [문제] OpenGraph에서 가격을 표시할 수 있는지 확인

가격을 숨기고 이 변경 가격이 OG 태그에 표시되지 않는 플러그인을 사용하면 시스템이 제대로 작동합니다.

_AC-11635 - [GitHub 문제](https://github.com/magento/magento2/issues/38512) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38510)_

#### [버그] REST API: 특별 가격 업데이트는 모든 스토어 조회수에 대한 값을 설정하지 않습니다

_AC-13671 - [GitHub 문제](https://github.com/magento/magento2/issues/39521) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP 오류가 게시되지 않음

이 PR은 루프 변수 이름을 변경하여 후속 호출에 사용할 지정된 제품의 &quot;_cache_instance_product_ids&quot; 데이터를 올바르게 추가합니다.

_AC-14159 - [GitHub 문제](https://github.com/magento/magento2/issues/39641) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD] 이미지 크기 조정을 수행하면 400GB 이상의 디스크 공간이 사용됩니다.

수정 후 —skip_hidden_images 플래그와 함께 사용되는 `catalog:images:resize` 명령은 이미지가 없는 웹 사이트에 대한 이미지 캐시를 생성하지 않습니다.

_ACP2E-3869 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

#### 제공된 CountryID가 존재하지 않음 - 아일랜드 (IE)

수정 후 아일랜드 우편 번호를 사용하여 픽업 위치를 검색할 수 있습니다.

_ACP2E-3932 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/d2f1d6c6)_

### 카탈로그, 성능

#### 관리자의 범주 로드 속도가 매우 느립니다.

카테고리 로드 성능이 크게 개선되었습니다. 이전에는 범주를 로드하는 데 너무 오래 걸려 시간 초과 문제가 발생했습니다.

_ACP2E-3891 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### 카탈로그, 가격 책정

#### 잘못된 카탈로그 가격 규칙 할인이 하위 제품에 적용됨

두 규칙 모두 우선순위가 동일한 경우 변형에 대한 카탈로그 가격 규칙이 상위 구성 가능한 제품에 의해 재정의되는 문제를 수정합니다.

_ACP2E-3693 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2)_

### 카탈로그, 검색

#### RestApi 요청 &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39;이(가) 시간 초과 오류로 실패합니다.

_AC-13358 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

### 콘텐츠

#### Magento 2.4.7 p2로 업그레이드한 후 새로 업로드한 파일 미디어 갤러리를 볼 수 없음

_AC-13262 - [GitHub 문제](https://github.com/magento/magento2/issues/39275)_

#### be에서 갤러리 이미지를 완전히 제거하면 범위 역할/유형(기본/작은/썸네일)이 설정되고 &quot;이전&quot; 역할/유형이 다시 추가된 후에 표시됩니다

시스템은 저장소 범위에서 예상대로 작동하며 이미지는 기본 범위에 따라 새로 추가된 이미지의 역할/유형을 상속합니다

_AC-13556 - [GitHub 문제](https://github.com/magento/magento2/issues/39481) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39680)_

#### 필드 값에 [이(가) 포함된 경우 관리 패널 ]의 `listing component`작은 버그`\` 필터를 누를 수 없습니다.

슬래시가 있는 페이지 제목을 필터링하면 시스템이 제대로 작동합니다(예: Magento\Store).

_AC-13661 - [GitHub 문제](https://github.com/magento/magento2/issues/39513) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39535)_

#### &quot;ID가 &quot;0&quot;인 CMS 페이지가 존재하지 않습니다.&quot; 로그 플러드

시스템은 관리자 사용자를 만든 후 새 페이지를 만들 때 예상대로 작동합니다. system.log에는 오류 메시지가 없습니다

_AC-14254 - [GitHub 문제](https://github.com/magento/magento2/issues/39743) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39746)_

#### 카탈로그 링크 위젯이 잘못된 URL을 사용함

이제 시스템은 카탈로그 제품 링크 및 카탈로그 범주 링크를 추가한 후 위젯을 올바르게 처리하며 html 소스에도 올바른 URL이 표시됩니다

_AC-14437 - [GitHub 문제](https://github.com/magento/magento2/issues/39464) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39710)_

#### 사용자에게 위젯 권한이 없는 경우 페이지 빌더의 제품 구성 요소가 작동하지 않음

수정 이전에는 권한이 없는 위젯에 액세스할 때 페이지에 일반 오류가 발생하고 &quot;로드 중&quot; GIF이 표시되었습니다. 이제 수정 후 모달 창에 &quot;죄송합니다. 이 콘텐츠를 볼 수 있는 권한이 필요합니다.&quot;가 표시됩니다. 메시지.

_ACP2E-3664 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### GraphQL에서 Page Builder 제품 위젯 순서 지정이 적용되지 않음

GraphQL &quot;경로&quot; 쿼리 응답이 페이지 빌더 제품 콘텐츠 유형 내에서 올바른 정렬 순서로 제품을 반환하지 않던 문제를 해결했습니다.

_ACP2E-3898 - [GitHub 코드 기여도](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### ICU 라이브러리 버전으로 인한 비영어 상점 가격 표시 문제

수정 후에는 히브리어(이스라엘) 로케일에 제품 가격이 올바르게 표시됩니다.

_ACP2E-3938 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 스토어 코드 삭제 디자인 구성 업데이트

구성 캐시가 제대로 새로 고쳐지지 않아 저장소 보기 코드를 업데이트하면 디자인 구성 설정이 지워지는 문제가 해결되었습니다.

_ACP2E-3941 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 프레임워크

#### 사용자 지정 DB 트리거로 명령 setup:upgrade을(를) 실행할 때 오류 발생

_AC-11487 - [GitHub 문제](https://github.com/magento/magento2/issues/38481)_

#### 웹 사이트/그룹/저장소 엔터티 양식은 확장 특성에 대한 여러 값 양식 요소로 확장할 수 없습니다.

이 PR을 사용하면 값이 여러 개인 양식 요소가 웹 사이트/그룹/스토어 양식에 데이터를 제출할 수 있습니다.

_AC-11657 - [GitHub 문제](https://github.com/magento/magento2/issues/24070) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/24094)_

#### [문제] 범위 확인자 사용 제거

이 PR은 현재 저장소 대신 전역으로 관리 URL 설정을 확인합니다

_AC-11736 - [GitHub 문제](https://github.com/magento/magento2/issues/38566) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38554)_

#### 기본 Nginx 구성을 통한 설정 라우트를 통한 Magento 버전 노출

시스템이 현재 예상대로 작동하며 사이트에서 실행 중인 Magento의 정확한 버전은 노출하지 않습니다

_AC-13205 - [GitHub 문제](https://github.com/magento/magento2/issues/39227) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39228)_

#### [문제] 리팩터링 견적 주소 유효성 검사 방법

이 PR에는 doValidate 메서드에 대한 가독성 개선 사항이 포함되어 있습니다.

_AC-13214 - [GitHub 문제](https://github.com/magento/magento2/issues/38230) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38219)_

#### Magento 옵션 —cli를 실행할 때 magento-init-params가 사용되지 않음

_AC-13231 - [GitHub 문제](https://github.com/magento/magento2/issues/39248) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue 잘못된 형식 선언

이제 시스템에서 입력 매개 변수 $value를 getItemsByColumnValue 함수에서 배열이 아닌 기본 형식으로 올바르게 정의하여 함수가 예상 컬렉션을 반환하도록 합니다. 이전에는 단일 값을 갖는 배열이 입력 매개 변수로 사용되면 함수가 null을 반환하고 IDE가 이를 오류로 표시했습니다.

_AC-13240 - [GitHub 문제](https://github.com/magento/magento2/issues/33070) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33120)_

#### Magento 2.4.7 다중 스토어 구현에서 FPC와 연결된 캐시 키

_AC-13719 - [GitHub 문제](https://github.com/magento/magento2/issues/39456) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ae6f305b)_

#### Magento REST API 노출 PII

_AC-13904 - [GitHub 문제](https://github.com/magento/magento2/issues/39336)_

#### 엄청난 수의 업데이트가 있는 고객의 경우 부분 인덱싱이 작동하지 않음

_AC-14424 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 모듈 내에서 &quot;strict 사용&quot;이 불필요함 조사

_AC-14517 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/77c589a6)_

#### MView 메커니즘은 트리거 실행 시 오류를 자동으로 무시합니다.

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

#### [문제] Microsoft IIS와 관련된 코드 제거

이 PR은 Microsoft Windows OS가 지원되지 않는다는 Magento 시스템 요구 사항 문서에 따라 Microsoft IIS와 관련된 코드를 정리합니다

_AC-14702 - [GitHub 문제](https://github.com/magento/magento2/issues/39910) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js 구문 오류

시스템 돋보기 기능은 이전에 작동했던 방식으로 계속 작동해야 하며 magnifierOptions를 전역 범위에서 사용할 수 없어야 합니다

_AC-14722 - [GitHub 문제](https://github.com/magento/magento2/issues/36200) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI 명령의 Verbose 모드 백업

_AC-14807 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### tls 및 2.4.8을 사용하여 SMTP 메일 보내기

_AC-14883 - [GitHub 문제](https://github.com/magento/magento2/issues/39947) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/8b453942) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/d3ea191d)_

#### [문제] 정적 콘텐츠 배포의 동시성 문제 해결

이 PR은 부모와 함께 테마를 정의하는 방법에 따라 여러 동시 프로세스가 회전하면서 동일한 테마 패키지를 처리하는 버그를 수정합니다.

_AC-14944 - [GitHub 문제](https://github.com/magento/magento2/issues/39990) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39954)_

#### [문제] PHP 버전 &lt; 8.1의 레거시 호환성 코드 제거

이 가져오기 요청은 PHP &lt;8.1에서 실행되도록 디자인된 코드를 제거합니다.
또한 모든 PHP 버전에서 사용할 수 있으므로 PHP_VERSION_ID 연락처 가용성에 대한 검사를 제거했습니다

_AC-14971 - [GitHub 문제](https://github.com/magento/magento2/issues/39891) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39882)_

#### 로그인 시 FPC가 작동하지 않음

_AC-14999 - [GitHub 문제](https://github.com/magento/magento2/issues/40007) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/)_

#### [문제] SchemaBuilder 처리 오류 개선

이 PR은 db 스키마의 오류 메시지 처리를 개선합니다. 많은 디버깅 없이 문제를 식별하는 데 도움이 됩니다.

_AC-15020 - [GitHub 문제](https://github.com/magento/magento2/issues/39816) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39799)_

#### CliStateTest 수정으로 인해 2.4.9-alpha2용 동기화 PR의 통합 테스트 실패

_AC-15136 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1 유형 버그 수정

이제 엄격한 처리 모드가 활성화되지 않았거나 제품 정보를 사용할 수 있을 때 연결된 제품이 false 대신 빈 배열로 초기화됩니다. 이러한 변경은 후속 논리 처리 관련 제품이 일관되게 동작하여 제품 준비 프로세스의 안정성과 예측 가능성을 향상시킵니다.

_AC-6017 - [GitHub 문제](https://github.com/magento/magento2/issues/35808) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/35842)_

#### [문제] 프레임워크에서 금지된 `@author` 태그를 제거합니다(3부).

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8343 - [GitHub 문제](https://github.com/magento/magento2/issues/37270) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37020)_

#### [문제] 친구 그래프 보내기 모듈에서 생성자 속성 프로모션을 사용합니다.

이제 시스템에서 &quot;친구 보내기&quot; GraphQL 모듈의 생성자 속성 프로모션을 사용하여 코드 가독성을 높이고 복잡성을 줄입니다. 이전에는 모듈에서 많은 줄을 사용하는 속성을 사용했기 때문에 코드가 더 복잡해지고 가독성이 감소했습니다.

_AC-8346 - [GitHub 문제](https://github.com/magento/magento2/issues/37235) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37197)_

#### [문제] `@author`에서 금지된 `Magento_Downloadable` 태그를 제거하십시오.

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8355 - [GitHub 문제](https://github.com/magento/magento2/issues/37251) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37001)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 코드 품질 및 일관성을 향상시켜 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8358 - [GitHub 문제](https://github.com/magento/magento2/issues/37264) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37014)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8360 - [GitHub 문제](https://github.com/magento/magento2/issues/37261) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37011)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 보다 깨끗하고 표준화된 코드를 만들어 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8361 - [GitHub 문제](https://github.com/magento/magento2/issues/37260) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37010)_

#### [문제] 금지된 `@author` 태그 제거

이제 시스템에서 특정 모듈에서 금지된 `@author` 태그를 제거하여 전체 코드 품질을 개선하여 코딩 표준을 준수합니다. 이전에는 일부 모듈에 이 태그가 있으면 설정된 코딩 표준을 위반했습니다.

_AC-8363 - [GitHub 문제](https://github.com/magento/magento2/issues/37258) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37008)_

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

#### 새로운 유효성 검사로 인한 업그레이드 2.4.7-p5 문제

SchemaBuilder 클래스에서 스키마를 만들거나 업데이트하는 동안 정의되지 않은 배열 키 &quot;column&quot;으로 인해 충돌이 발생하는 문제를 해결했습니다. 이 문제는 &quot;열&quot; 키를 포함하지 않은 테이블 데이터를 처리할 때 발생했습니다.

_ACP2E-3871 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4 사용 중단 오류: Adobe Commerce 2.4.8로 업그레이드한 후 E_USER_ERROR

고객 응대 시나리오는 수정 사항의 영향을 받지 않습니다.

_ACP2E-3963 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

### 프레임워크, 검색

#### 단일 가격 범주에 대한 Opensearch 2.19.1 illegal_argument_exception

Opensearch는 더 이상 가격이 같은 모든 제품을 포함하는 범주에 illegal_argument_exception을 throw하지 않습니다. 이전에는 이 예외 &quot;[from] 매개 변수는 음수일 수 없습니다.&quot;가 있었습니다.

_ACP2E-3896 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 위시리스트 항목은 GraphQL 요청의 한 웹 사이트 내에 있는 스토어 보기 간에 공유되지 않습니다

수정하기 전에 위시리스트 항목이 저장소 ID로 필터링되었습니다. 이제 수정 후 위시리스트 항목이 웹 사이트별로 필터링됩니다.

_ACP2E-3987 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, 제품

#### MediaGalleryInterface에서 제품 graphql에 media_type 누락

이제 MediaGallery GraphQL 요청에 제품 이미지 유형의 &quot;유형&quot; 필드가 포함됩니다. 이전에는 이 &quot;유형&quot; 필드가 MediaGallery GraphQL 요청에 존재하지 않았습니다.

_ACP2E-3880 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/3ad96f6a)_

### 인벤토리/MSI

#### 홈페이지로 리디렉션하고 체크아웃한 후에는 스토어를 사용할 수 없습니다.

고객이 결제 페이지로 이동한 다음, 홈 페이지로 돌아간 다음, 최종적으로 체크아웃 페이지로 돌아오면, 이제 &quot;스토어에서 선택&quot; 배송에서 이전에 선택한 스토어가 미리 선택됩니다. 이전에는 체크아웃 페이지로 반복적으로 돌아간 후 &quot;스토어 선택&quot;에서 선택한 스토어가 지워졌습니다.

_ACP2E-3793 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/62c0d79b)_

### 주문

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[])가 customAttributes를 나눕니다.

_AC-10568 - [GitHub 문제](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento 순서 바꾸기 -1 순서 번호

시스템이 예상대로 작동하며 백엔드에서 순서를 재정렬하면 주문 번호가 고유 8자리가 됩니다

_AC-12854 - [GitHub 문제](https://github.com/magento/magento2/issues/39089) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39399)_

#### Adobe 신용카드 결제 방법으로 체크아웃 시 제품 사용자 정의 옵션 파일 업로드 손실

_AC-14306 - [GitHub 문제](https://github.com/magento/magento2/issues/39647)_

#### 처리 중 주문 상태 중단

수정 전에는 &quot;함께 배송&quot; 옵션이 활성화된 번들 제품을 주문할 때 송장 및 선적 후 주문 상태가 자동으로 &quot;완료&quot;로 전환되지 않았습니다. 이제, 수정 후 주문 상태가 자동으로 주문 송장이 발행되고 배송된 후 &quot;완료&quot;로 전환됩니다.

_ACP2E-3947 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a252ae6)_

#### [클라우드]Magento OOTB 코드 - 전자 메일 템플릿 설정 문제

수정 전에 비동기 이메일 전송을 사용할 때 배송 이메일이 스토어 주문과 일치하지 않았습니다. 이제, 수정 후, 적절한 매장 선적 이메일 주문이 전달됩니다.

_ACP2E-3998 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 기타 개발자 도구

#### [문제] 보호된 멤버 $_urlHelper에 대한 잘못된 유형 힌트

이제 생성자에서도 사용되는 올바른 힌트로 잘못된 유형 힌트가 수정됩니다

_AC-10716 - [GitHub 문제](https://github.com/magento/magento2/issues/32503) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32496)_

### 성능

#### [문제] Store.php 업데이트

이 PR은 현재 저장소 해상도를 건너뛰어 성능을 향상시킵니다.

_AC-14791 - [GitHub 문제](https://github.com/magento/magento2/issues/39949) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38717)_

### 가격 책정

#### 주문 REST API에서 동적 가격이 없는 번들 제품 항목에 대한 가격은 항상 0입니다.

_AC-11925 - [GitHub 문제](https://github.com/magento/magento2/issues/38687) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7da46f52)_

### 제품

#### 선택한 옵션 없이 원래 가격으로 계산된 계층 가격 및 카탈로그 가격 규칙의 할인율입니다.

_AC-12004 - [GitHub 문제](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 min허용된 누락 제품 주문 수량

시스템이 정상적으로 작동하며 페이지 소스가 제품의 최소 수량을 올바르게 표시함

_AC-12909 - [GitHub 문제](https://github.com/magento/magento2/issues/39142) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39480)_

#### 관리 패널의 제품 페이지에서 사용자 지정 가능한 옵션 표 문제

유형 드롭다운으로 사용자 지정 가능한 옵션을 만들 때 시스템이 예상대로 작동합니다

_AC-14003 - [GitHub 문제](https://github.com/magento/magento2/issues/39640) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39694)_

#### 다른 고객의 모든 비교 목록은 관리자를 통해 로그인한 후 고객에게 할당됩니다

이전에는 관리자가 백엔드에서 &quot;고객으로 로그인&quot; 기능을 사용하면 이전에 로그인한 고객의 비교 목록에 있는 제품이 현재 가장한 고객에게 잘못 할당되었습니다.  수정 후 올바른 로그인한 고객에 대해 비교 목록이 올바르게 로드됩니다.

_ACP2E-3818 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### REST API를 통해 제품 url_key를 업데이트해도 301 URL 다시 쓰기가 생성되지 않음

REST API를 통해 제품의 URL 키를 업데이트할 때 &quot;URL 키가 변경된 경우 URL에 대한 영구 리디렉션 만들기&quot; 설정이 예로 설정되면 제품 URL 재작성은 이전 URL에서 새 URL로 리디렉션을 만듭니다.

_ACP2E-3900 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 보안

#### 번들/병합된 JS가 SRI 해시의 일부가 아님

수정 이전에 생성된 번들 또는 병합된 파일이 SRI 해시 목록에 추가되지 않았습니다. 이제 파일이 SRI 해시에 제대로 추가되고 있습니다.

_ACP2E-3854 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### 배송

#### [QUANS] - Magento_Fedex 코어 모듈이 새 토큰 가져오기 요청을 보내기 전에 올바른 활성 토큰을 확인합니까?

Adobe Commerce은 액세스 토큰에 대해 FedEx API 서비스에 더 이상 많은 요청을 하지 않습니다. 이전에는 액세스 토큰이 여전히 유효하더라도 Adobe Commerce이 항상 FedEx API에 새 요청을 하여 속도 제한 문제를 일으켰습니다.

_ACP2E-3930 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/4ca73607)_

### 스테이징 및 미리보기

#### 범주 권한이 활성화된 예약된 제품 업데이트를 미리 볼 수 없음

수정 전 활성화된 향후 제품이 미리보기 모드에서 표시되지 않았습니다. 현재 상태가 비활성화된 경우에도 표시됩니다.

_ACP2E-3786 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/7accebfa)_

#### 카탈로그 가격 규칙 할인 금액 필드에 대한 유효성 검사 누락

이전에는 스테이징 스케줄 업데이트의 discount_amount 필드가 현재 검증 규칙으로 올바르게 검증되지 않았습니다. 그러나 이 수정 사항을 적용하면 discount_amount 필드의 유효성이 적절하게 검사됩니다.

_ACP2E-3867 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/462ede94)_

### 세금

#### 주문 합계가 잘못되었습니다. 가격 계산에 라운드가 적용되지 않습니다.

이제 시스템에서 price_after_discount, discount_amount 및 세금 금액을 계산할 때 를 올바르게 처리합니다.
주문의 실제 합계

_AC-11389 - [GitHub 문제](https://github.com/magento/magento2/issues/38455) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39687)_

### 테스트 프레임워크

#### [문제] Lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en 무시...

이제 시스템은 단위 테스트를 실행할 때 생성되는 &#39;env.php&#39; 파일을 무시하여 테스트 실행 후에도 git 상태가 깔끔하게 유지되도록 합니다. 이전에는 단위 테스트를 실행하면 새 파일 &#39;env.php&#39;가 생성되어 git 상태가 발견된 새 파일을 표시하고 더럽혀진 것처럼 보이게 했습니다.

_AC-13293 - [GitHub 문제](https://github.com/magento/magento2/issues/39304) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37631)_

#### [문제] 인터셉터 통합 테스트 문제 해결

이제 시스템은 통합 테스트에서 \Magento\TestFramework\App\Config\Interceptor 을 올바르게 식별하고 처리하므로 클래스에 플러그인이 있는 경우에도 테스트가 필요한 데이터에 액세스할 수 있습니다. 이전에는 시스템이 \Magento\TestFramework\App\Config 이 \Magento\TestFramework\App\Config\Interceptor 일 가능성을 고려하지 않았으므로 $data 속성에 액세스하려고 할 때 오류가 발생했습니다.

_AC-13305 - [GitHub 문제](https://github.com/magento/magento2/issues/39324) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37187)_

#### [문제] MFTF: captcha가 활성화된 친구 양식에 전자 메일 제출

테스트 케이스는 CAPTCHA가 활성화되어 있을 때 &quot;친구에게 이메일&quot; 양식의 기능을 해결하여 양식 제출 프로세스가 잘못되고 올바른 CAPTCHA 값에서 모두 올바르게 작동하도록 합니다.

_AC-13492 - [GitHub 문제](https://github.com/magento/magento2/issues/39462) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32830)_

#### phpunit v10 이후 TestCase::getTestResultObject의 [TestFramework] 사용이 잘못되었습니다.

_AC-13502 - [GitHub 문제](https://github.com/magento/magento2/issues/39463)_

#### AC 2.4.7-p3의 환경별 단위 테스트 오류

이 문제는 모든 버전 및 환경에서 재현되지 않는 단위 테스트 오류를 수정합니다. 이전에는 일부 단위 테스트를 수정하지 못했습니다. 라이브러리 버전이 다르거나 이후 버전에서 추가된 기능이 누락되었기 때문입니다.

_ACP2E-3712 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/9ad7d277)_

### UI 프레임워크

#### WYSIWYG이 동적 행에서 비어 있습니다.

_AC-12336 - [GitHub 문제](https://github.com/magento/magento2/issues/38893) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [문제] MIME 유형 오타 수정

gif 이미지에 대한 mime 유형 및 오타가 올바르게 처리되고 수정되었습니다

_AC-8001 - [GitHub 문제](https://github.com/magento/magento2/issues/36899) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36669)_

#### [문제] 검토 목록 Ajax에 직접 액세스하지 마십시오.

시스템이 를 올바르게 처리하고 검토 목록 Ajax에 직접 액세스하지 않음

_AC-9381 - [GitHub 문제](https://github.com/magento/magento2/issues/37920) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33876)_

### 업그레이드 - 업그레이드 호환성 도구

#### 사용되지 않는 기능: 동적 속성 Magento\Framework\Acl::$_roleRegistry 만들기

_AC-12343 - [GitHub 문제](https://github.com/magento/magento2/issues/37469)_
