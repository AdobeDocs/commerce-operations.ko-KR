---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6077'
ht-degree: 0%

---
# Adobe Commerce 해결 문제(v2.4.9-alpha3)

## v2.4.9-alpha3의 문제가 해결되었습니다

Adobe Commerce 2.4.9-alpha3 코어 코드에서 129개의 문제가 해결되었습니다. 이 릴리스에 포함된 해결된 문제의 하위 집합은 아래에 설명되어 있습니다.

### API

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

#### REST API 끝점 export-stock-salable-qty가 잘못된 항목 total_count를 반환합니다.

total_count가 페이지 크기로 잘못 제한된 재고 내보내기 재고 예약 가능 수량 API의 페이지 매김 문제가 수정되었습니다. 이전에는 page_size=5와 같은 페이지 매김 매개 변수와 함께 /rest/all/V1/inventory/export-stock-salable-qty/website/base 끝점을 사용할 때 응답의 total_count 필드는 검색 기준과 일치하는 실제 총 제품 수 대신 5를 반환합니다. 이 수정 후 total_count 필드는 이제 page_size 매개 변수에 상관없이 사용 가능한 총 제품 수를 올바르게 반영하므로 모든 Magento REST API 엔드포인트에서 일관된 페이지 매김 동작이 보장됩니다.

_ACP2E-4086 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

#### 장바구니 항목 REST API의 사용자 지정 옵션 ID에 대한 유효성 검사 문제

REST API V1/guest-carts/&lt;cartId>/items/ 및 V1/carts/mine/items/ 이제 &quot;product_options.extension_attributes.custom_options를 확인합니다.*.option_id&quot;를 사용하여 장바구니 항목 SKU에 대한 유효한 option_id를 참조하는지 확인합니다. 이전에는 이 매개 변수가 유효성 검사 없이 처리되어 데이터베이스에 저장되었습니다.

_ACP2E-4138 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

### 계정

#### [문제] 백 엔드 그리드에서 불필요한 간격을 제거했습니다.

이제 선택한 항목이 있을 때 백엔드 격자에서 불필요한 간격이 제거됩니다

_AC-11579 - [GitHub 문제](https://github.com/magento/magento2/issues/38502) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32622)_

#### `updateProductsInWishlist` GraphQL 돌연변이를 통해 위시리스트 항목 주석을 지울 수 없습니다.

위시리스트 댓글이 GraphQL 돌연변이를 통해 업데이트되지 않았던 문제를 수정했습니다.
이제 주석이 올바르게 업데이트되고 API 응답과 상점 첫 화면 모두에 반영됩니다.

_AC-14682 - [GitHub 문제](https://github.com/magento/magento2/issues/39911) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 아니요로 설정할 때 무시된 접두어/접미어 표시 설정

구성에서 고객 이름 접두사/접미사가 비활성화된 경우에도 주문에 계속 표시되는 문제를 해결했습니다.
이제 구성 설정에 따라 접두사/접미사 값이 주문 세부 사항에서 제거됩니다.

_AC-15074 - [GitHub 문제](https://github.com/magento/magento2/issues/40036) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront 고객 계정 등록: 다른 도메인 포맷으로 전환되는 이메일 주소 포맷

이 버그는 도메인(예: tec55241@adòbe.com)에 특수 문자가 있는 고객 이메일이 punycode 형식(tec55241@xn--adbe-mqa.com)으로 자동 변환되는 문제를 해결했습니다.
Magento 2.4.9-alpha3에서는 이러한 이메일 ID가 변경되지 않고 유효하게 유지되므로 게재 오류가 발생하지 않습니다.

_AC-15177 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 등록 양식에 유효성 검사 메시지(mage-error) 누락

고객 계정 만들기 페이지의 필수 필드에 비워 둘 때 유효성 검사 메시지가 표시되지 않던 문제를 수정했습니다.
이제 모든 비어 있거나 잘못된 필드에 적절한 오류 메시지가 표시됩니다.

_AC-15185 - [GitHub 문제](https://github.com/magento/magento2/issues/40076) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### magento 2.4.8-p1에서 로그인 후 문제

로그인 후 홈페이지에서 &quot;계정 만들기&quot; 링크가 여전히 표시되는 Magento 2.4.8-p1 문제를 수정했습니다.
이제 링크가 다른 페이지와 일관되게 로그인 후 올바르게 숨겨집니다.

_AC-15292 - [GitHub 문제](https://github.com/magento/magento2/issues/40120)_

### 관리자 UI

#### [문제] 더 이상 사용되지 않는 이스케이프 장치를 바꿉니다.

이 PR은 사용되지 않는 getEscaper()를 제거하고 생성자 삽입을 통해 추가합니다

_AC-15132 - [GitHub 문제](https://github.com/magento/magento2/issues/40062) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38135)_

#### 시작 메시지가 모바일 보기의 제품 범주와 겹칩니다.

모바일 보기에서 시작 이름이 제품 범주와 겹쳐서 클릭이 차단되는 UI 문제가 해결되었습니다.
이제 카테고리가 중복 문제 없이 완전히 표시되고 클릭할 수 있습니다.

_AC-15166 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Google reCAPTCHA 관리 패널의 exception.log에서 &quot;reCAPTCHA 매개 변수를 해결할 수 없음&quot; 항목

Google V3 reCAPTCHA 관리자 로그인에 대한 `var/log/exception.log` 파일의 reCaptcha 오류가 해결되었으며 오류 메시지가 기록되지 않습니다. 이전에는 관리 사용자가 **구성** > **보안** > **Google reCAPTCHA 관리 패널** 설정을 구성할 때 몇 초마다 다음 오류가 발생했습니다. `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub 문제](https://github.com/magento/magento2/issues/34975) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub 코드 기여](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

### 관리자 UI, 세금

#### 세율 관리자 ui 오류

이 티켓을 통해 국가(예: 미국→ 영국)를 전환해도 이전에 선택한 미국 주가 표시되므로 사용자가 오인할 수 있는 세율 관리자 UI 문제가 해결되었습니다.
2.4.9-alpha3에서 선택한 국가에 상태가 없으면 상태 필드는 이제 *로 재설정됩니다.

_AC-8440 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Rest API 제품-렌더링-정보가 로그인한 고객에 대해 잘못된 최종 가격을 반환함

티켓에 Rest API 제품-렌더링-정보에 대한 수정 사항이 있습니다. 로그인한 고객에 대한 잘못된 최종 가격을 반환하십시오.

_AC-5979 - [GitHub 문제](https://github.com/magento/magento2/issues/35757) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/)_

#### 범주 페이지에서 추가하려고 할 때 구매요청에 추가 목록 버튼이 사라짐

이제 고정된 범주 페이지에서 추가하려고 하면 이전에 구매요청에 추가 목록 버튼이 사라지고 범주 페이지에서 구매요청 버튼을 볼 수 있습니다.

_AC-8575_

### B2B, 장바구니 및 체크아웃

#### 관리자 기능 &quot;고객으로 로그인&quot;에서 B2B 회사 사용자에 로그인할 때 Storefront에 cartId = X 오류가 표시되는 엔티티가 없습니다.

이제 &quot;고객으로 로그인&quot; 기능을 사용할 때 관리 백엔드에서 성공적으로 로그인된 후 &quot;cartId = X인 해당 엔티티 없음&quot; 오류가 더 이상 표시되지 않습니다.

_ACP2E-3994 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

### 장바구니 및 체크아웃

#### [문제] 계약 모델 체크아웃에 EventPrefix 및 EventObject 추가

이제 시스템에 체크아웃 계약 모델에 대한 EventPrefix와 EventObject가 포함되어 있으므로 이벤트 접두사로 이벤트를 트리거할 수 있습니다. 이 개선 사항은 체크아웃 계약 이벤트로 작업할 때 개발자에게 보다 유연함을 제공합니다. 이전에는 체크아웃 계약 모델이 EventPrefix 및 EventObject를 지원하지 않아 이벤트 처리를 사용자 지정하는 기능이 제한되었습니다.

_AC-13252 - [GitHub 문제](https://github.com/magento/magento2/issues/32510) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/32451)_

#### [Graphql]은(는) Null을 허용하지 않는 필드 &quot;SelectedCustomizableOption.label&quot;에 대해 null을 반환할 수 없습니다.

이제 선택한 옵션이 더 이상 존재하지 않을 때 시스템에서 내부 서버 오류가 발생하지 않습니다.

_AC-14256 - [GitHub 문제](https://github.com/magento/magento2/issues/39729) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] 도시 이름에 0~9 자릿수, 앰퍼샌드, 전체 중지 또는 괄호가 있는 경우 주문을 할 수 없습니다.

과 같은 특수 문자가 포함된 도시 이름에 대해 체크아웃하지 못하던 문제를 수정했습니다. , &amp; 또는 괄호.
이제 이러한 도시 이름을 가진 주문이 검증 오류 없이 성공적으로 주문됩니다.

_AC-14495 - [GitHub 문제](https://github.com/magento/magento2/issues/39854) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 수량 조건이 있는 Salesrule 하위 선택 적용 실패

제품 하위 선택 조건이 있는 장바구니 가격 규칙이 체크아웃 시 적용되지 않는 문제를 해결했습니다.
이제 구성된 규칙에 따라 할인이 성공적으로 적용됩니다.

_AC-14884 - [GitHub 문제](https://github.com/magento/magento2/issues/39965) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - 미납주문이 활성화된 경우 장바구니 병합이 제대로 작동하지 않음

GraphQL을 통한 장바구니 병합 중에 게스트 장바구니 항목이 고객 장바구니와 병합되지 않던 문제를 수정했습니다.
이제 고객 장바구니에는 고객 장바구니와 고객 장바구니의 결합 수량이 올바르게 반영됩니다.

_AC-15148 - [GitHub 문제](https://github.com/magento/magento2/issues/40064) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [통합] [체크아웃] 실패한 결제 전자 메일 템플릿에서 종속 지시문이 업데이트되었습니다.

실패한 결제 이메일 템플릿이 종속 지시어를 올바르게 처리하도록 업데이트되었습니다.
수정 사항을 통해 해당되는 경우 배송 주소와 배송 방법이 올바르게 표시됩니다.
이전에는 실패한 결제 이메일에서 이러한 필드가 누락되었습니다.

_AC-15363 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 장바구니가 더 이상 요구 사항을 충족하지 않을 때 [클라우드] 무료 배송 할인이 올바르게 제거되지 않음

소계(제외) 장바구니 가격 규칙의 세금)에는 이제 이전 규칙의 할인이 포함됩니다.

_ACP2E-3973 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 다중 배송에서 동일한 고객에 대해 중복 주문 발견

여러 배송 주소가 있는 주문을 동시에 요청해도 더 이상 동일한 고객에 대한 주문이 중복되지 않습니다

_ACP2E-4117 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

### 장바구니 및 체크아웃, 주문, 제품

#### 주문 송장이 실패하더라도 기프트 카드 이메일을 전송합니다.

이 수정 사항이 구현되기 전에 기프트 카드 이메일은 송장이 생성된 후 전송되었습니다. 그러나 수정 사항이 적용되면 이제 송장이 정상적으로 저장되고 커밋된 후 기프트 카드 이메일이 전송됩니다.

_ACP2E-3905_

### 장바구니 및 체크아웃, 보안

#### [클라우드] sri 패치를 구현한 후 첫 번째 시도에서 체크아웃 페이지에서 JS용 404 파일 가져오기

수정 전 mixin은 축소 및 번들링을 활성화할 때 장바구니 및 체크아웃에 로드되지 않았습니다. 수정 후 모든 mixin이 예상대로 로드됩니다.

_ACP2E-4128 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

### 카탈로그

#### 가격 범위 및 config.php와 관련된 문제

Magento 2.4.2에서 config.php를 통해 가격 범위를 변경해도 가격 속성에 대한 catalog_eav_attribute의 is_global 값이 제대로 업데이트되지 않습니다.
따라서 제품 가격은 전 세계적으로 유지되며 가격 범위가 웹 사이트로 설정되어 있더라도 웹 사이트당 저장할 수 없습니다.
이 문제를 해결하려면 데이터베이스에서 is_global 열을 수동으로 업데이트해야 합니다. 이는 프로덕션 환경에 적합하지 않습니다.
이 동작은 가격 범위가 글로벌 또는 웹 사이트이지만 스토어 보기별이 아닌 Magento의 기본 디자인과 일치합니다.

_AC-13857 - [GitHub 문제](https://github.com/magento/magento2/issues/33559)_

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

#### 단일 옵션이 있는 구성 가능한 제품에 대해 &#39;다음으로 낮음&#39; 가격 레이블이 표시됨

구성 가능한 제품이 PDP/PLP에 잘못된 &quot;As low as&quot; 레이블과 함께 가격을 표시하는 문제가 해결되었습니다.
이제 이 제품은 오해의 소지가 있는 라벨 없이 정확한 가격(500달러)을 보여주고 있다.

_AC-15237 - [GitHub 문제](https://github.com/magento/magento2/issues/40104) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [비교에 추가] 단추에 대해 잘못된 메서드가 호출되었습니다.

\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect()에 사용된 메서드를 수정했습니다.
이전에는 getAddToCartButton() 대신 getAddToCartButton()이 잘못 호출되었습니다.
이렇게 하면 제품 목록에서 &quot;Add to Compare&quot; 단추를 렌더링하는 데 필요한 동작이 올바르게 수행됩니다.
기능 동작 변경 사항이 도입되지 않았습니다. 업데이트는 개발자 경험 및 코드 수정을 개선합니다.

_AC-15323 - [GitHub 문제](https://github.com/magento/magento2/issues/39754) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 동적 이미지 생성으로 많은 수의 이미지를 생성합니다.

수정 후에는 제품이 지정된 웹 사이트에 대해서만 이미지가 생성됩니다.

_ACP2E-3927 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/fab20b00)_

#### 레이아웃에 캐시된 잘못된 레이아웃 구조로 인해 프론트엔드에 500 오류가 발생합니다.

레이아웃에서 캐시되는 잘못된 레이아웃 구조로 인해 페이지가 500 오류 코드를 반환하는 문제를 해결했습니다

_ACP2E-4040 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### 예약된 업데이트의 카탈로그 가격 규칙 할인 금액 필드에 대한 유효성 검사 오류

이전에는 이 문제를 수정하기 전에 카탈로그 가격 규칙에 대한 일정 업데이트에 대해 할인 금액이 by_fixed인 경우 검증 번호 범위 규칙으로 인해 제대로 검증되지 않았습니다. 이 수정 사항이 적용되면 고정 가격 카탈로그 가격 규칙에 대해 유효성 검사가 제대로 작동합니다.

_ACP2E-4054 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 비활성화 후 제품이 품절로 표시됨

수정 후 비활성화된 제품이 제품 위젯에 없습니다.

_ACP2E-4136 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [클라우드] 중복 항목이 있는 오류(temp_category_descendants_%)

중첩된 범주가 많은 환경에 대해 예약된 업데이트를 만드는 동안 중복 항목이 발생하는 문제를 해결했습니다.

_ACP2E-4159 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/a1c57b2e)_

### 카탈로그, GraphQL

#### GraphQl 잘못된 할인 계산

이제 카탈로그 가격이 세금을 포함하도록 구성되면 GraphQL에 할인 비율과 기본 가격이 올바르게 표시됩니다. 기존에는 20%가 아닌 19.99%를 표시하는 등 반올림 오류가 발생했다.

_ACP2E-3993 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

### 카탈로그, 제품

#### 관련 제품 규칙을 통한 관련 제품이 GraphQL을 통해 PDP에 표시되지 않음

이전에는 이 수정 사항이 적용되기 전에 상대 제품 규칙이 규칙과 일치하는 제품에 대해 빈/null을 반환했습니다. 이 수정 사항이 적용되면 제품에 대한 상대 규칙이 일치하는 제품에 대해 성공적으로 반환됩니다.

_ACP2E-3949_

### 콘텐츠

#### graphql(magento 2.4.6-p4 ) - 활성 상태가 아닌 cms 페이지를 가져오려고 할 때 오류 발생

비활성화된 CMS 페이지에 대한 GraphQL 쿼리에서 내부 서버 오류가 반환되던 문제를 수정했습니다.
이제 쿼리가 오류 없이 적절한 응답을 가져옵니다.

_AC-12302 - [GitHub 문제](https://github.com/magento/magento2/issues/38877) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] 루트 쿼리 무한 루프

이 티켓은 동일한 요청 경로와 대상 경로를 사용하는 GraphQL 경로 쿼리가 무한 루프를 유발하여 결국 시간이 초과되는 문제를 해결했습니다.
2.4.9-alpha3에서 이제 쿼리가 루핑 대신 올바른 오류 응답을 반환합니다.

_AC-14269 - [GitHub 문제](https://github.com/magento/magento2/issues/39707) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 유연성을 높이기 위해 상수 IMAGE_FILE_NAME_PATTERN을 공개 표시로 변경합니다.

GenerateRenditions.php의 상수 IMAGE_FILE_NAME_PATTERN을 공개하여 개발자가 이미지 표현물로 작업할 때 보다 유연하게 사용할 수 있도록 했습니다.이 수정 사항은 전체 단위 및 통합 테스트 범위를 제공하는 Magento 2.4.9-alpha3에 포함되어 있습니다.

_AC-15338 - [GitHub 문제](https://github.com/magento/magento2/issues/39733) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### 콘텐츠 스테이징 미리 보기가 검색 결과와 작동하지 않음

이제 스테이징 미리 보기의 검색에서 선택한 범위에 따른 제품을 반환합니다. 이전에는 선택한 스토어를 무시하고 기본 범위에서 검색 결과가 반환되었습니다.

_ACP2E-4095_

#### 페이지 빌더 - 제품 조건 논리 문제(또는 논리가 더 적은 제품을 잘못 표시함)

이제 Page Builder 제품 위젯은 전역 범위의 속성이 &quot;모든 항목 일치&quot; 조건에 사용되면 올바른 결과를 반환합니다

_ACP2E-4096 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

### 고객/고객

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

#### [문제] 메서드의 시그니처를 인터페이스와 일치하도록 만들기

이제 getAttributes에 대한 메서드 시그니처가 인터페이스와 일관되어 메서드를 덮어쓸 때 오류가 발생하지 않습니다. 이전에는 메서드 시그니처가 일치하지 않아 getAttributes 메서드를 덮어쓰려고 할 때 오류가 발생했습니다.

_AC-11578 - [GitHub 문제](https://github.com/magento/magento2/issues/38501) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/31955)_

#### [문제] ui 구성 요소에 대한 유효성 검사 전자 메일 규칙 수정

이제 시스템에서 UI 구성 요소에 입력된 여러 이메일 주소를 올바르게 확인하여 각 이메일을 올바르게 트리밍하고 유효성을 검사합니다. 이전에는 시스템에서 이메일 주소를 트리밍하는 잘못된 방법을 사용했으며, 이로 인해 유효성 검사 오류가 발생할 수 있었습니다.

_AC-11719 - [GitHub 문제](https://github.com/magento/magento2/issues/38528) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33470)_

#### [문제] 중복 메서드 제거

코드 품질: 기능을 추가하지 않고 상위 메서드만 호출한 AsynchronousOperations 및 Sales 구성 요소에서 중복 메서드를 제거하여 코드 유지 관리를 개선했습니다.

_AC-11915 - [GitHub 문제](https://github.com/magento/magento2/issues/29748) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/29147)_

#### 필드 항목 아래에 주석이 포함된 etc/adminhtml/system.xml 파일에서 xsd 유효성 검사가 실패합니다.

이 PR은 설명 노드에 대한 phpstorm의 XML 스키마 정의를 수정합니다

_AC-12945 - [GitHub 문제](https://github.com/magento/magento2/issues/39148) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8에서는 시맨틱 버전 관리를 따르지 않는 개발 패키지를 사용합니다

Magento 2.4.8을 사용하려면 PHP 8.4 호환성을 위해 pdepende/pdepende 및 phpmd/phpmd(3.x-dev) 개발 버전이 필요합니다.
이러한 개발 버전은 SemVer 호환 패키지를 예상하는 타사 도구와 충돌하여 일부 업그레이드를 방지합니다.
임시 해결 방법은 composer.json의 개발 버전(예: &quot;3.x-dev as 3.99.0&quot;)에 별칭을 지정하여 시맨틱 버전 관리를 충족하면서 호환성을 허용하는 것입니다.
이를 통해 PHP 8.4를 지원하고 안정적인 릴리스가 제공될 때까지 충돌을 피할 수 있습니다.

_AC-14519 - [GitHub 문제](https://github.com/magento/magento2/issues/39796)_

#### Rest API: null에서 멤버 함수 getVideoProvider()를 호출합니다.

구성 가능한 제품 하위 API를 호출하면 하위 제품에 YouTube 비디오만 있고 다른 이미지는 없는 경우 500 내부 서버 오류가 반환되던 문제를 수정했습니다.
ExternalVideoEntryConverter의 null 참조로 인해 오류가 발생했습니다.
이제 API는 오류를 발생시키지 않고, 외부 비디오 데이터를 포함한 미디어 갤러리 항목이 있는 하위 제품을 올바르게 반환합니다.
이렇게 하면 REST API를 통해 하위 제품에 대한 모든 미디어 유형을 적절하게 검색할 수 있습니다.

_AC-15046 - [GitHub 문제](https://github.com/magento/magento2/issues/40021)_

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

#### 모듈 읽기 및 수정 문서 링크 업데이트

_AC-15340 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/ec9459d0)_

#### [문제] 로그 선언되지 않은 플러그인은 비활성화되지 않은 경우에만

이 PR은 실제로 선언되지 않고 사용되지 않는 플러그인을 수정합니다(활성화 및 누락된 인스턴스).

_AC-15386 - [GitHub 문제](https://github.com/magento/magento2/issues/40086) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework 버전 103.0.8-p2: 존재하지 않는 메서드를 호출하는 EmailMessage 클래스

_AC-15446 - [GitHub 문제](https://github.com/magento/magento2/issues/40170) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/059fd469) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] 데이터/스키마 패치 getAliases()로 인해 `setup:upgrade` 중 오류가 발생합니다.

getAliases()로 인해 :upgrade 설정 중에 오류가 발생합니다. 이 PR은 이를 수정합니다

_AC-15559 - [GitHub 문제](https://github.com/magento/magento2/issues/31396) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38239)_

#### &#39;Magento\Customer\Api\Data\GroupInterface&#39; 형식이 필요합니다. &#39;Magento\Customer\Model\Group&#39;를 찾았습니다.

GroupFactory를 사용하여 GroupRepositoryInterface를 통해 고객 그룹을 저장하면 유형 오류가 발생하는 문제가 해결되었습니다.
이전에는 리포지토리에서 GroupInterface를 예상했지만 그룹 모델 인스턴스가 전달되어 치명적인 오류가 발생했습니다.
이제 적절한 인터페이스 구현을 보장하여 저장소를 통해 고객 그룹을 성공적으로 저장할 수 있습니다.
이렇게 하면 고객 그룹을 프로그래밍 방식으로 만들거나 업데이트할 때 IDE 경고와 런타임 오류가 해결됩니다.

_AC-6909 - [GitHub 문제](https://github.com/magento/magento2/issues/36269)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8349 - [GitHub 문제](https://github.com/magento/magento2/issues/37266) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37016)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8350 - [GitHub 문제](https://github.com/magento/magento2/issues/37265) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37015)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8359 - [GitHub 문제](https://github.com/magento/magento2/issues/37262) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37012)_

#### [문제] 금지된 `@author` 태그 제거

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8362 - [GitHub 문제](https://github.com/magento/magento2/issues/37259) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37009)_

#### [문제] `@author` 및 `Magento_Backup`에서 금지된 `Magento_Bundle` 태그를 제거합니다.

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8367 - [GitHub 문제](https://github.com/magento/magento2/issues/37244) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36979)_

#### [문제] catalogsearch에서 변수 이름 수정

이제 시스템에서 검색 엔진 모듈에서 변수의 이름을 올바르게 지정하므로 코드 명확성과 유지 관리가 향상됩니다. 이전에는 검색 엔진 모듈에 관련 없는 변수 이름 $defaultCountry가 사용되면서 혼동이 발생하기도 했습니다.

_AC-9215 - [GitHub 문제](https://github.com/magento/magento2/issues/37810) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33533)_

#### 잘못된 S3 액세스 키로 인해 [QUANS]서버 문제가 발생할 수 있습니다.

잘못된 AWS S3 자격 증명으로 인해 더 이상 페이지가 상점 앞에 무한히 로드되지 않습니다.

_ACP2E-3890 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] 축소 js가 작동하지 않음

이제 JS 축소가 활성화되면 mage/backend/tabs.min.j, jquery/jquery.validate.min.js 및 Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js JS 파일이 완전하고 올바르게 축소됩니다. 따라서 페이지 빌더 CSS 클래스 필드 유효성 검사는 예상대로 작동합니다.

_ACP2E-3925 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

#### Cron 작업이 데이터베이스 테이블을 지우지 않아 Galera 충돌로 인해 중단됨

많은 삭제 작업을 방지하기 위해 변경 로그 테이블 정리가 이제 일괄적으로 실행되고 있습니다.

_ACP2E-3995 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### 축소되지 않은 JS는 때로 &#39;js 축소 활성화&#39;를 무시하면서 로드됩니다.

수정 전에 축소를 활성화했더라도 &quot;min&quot; 접두사 없이 일부 JS 파일이 요청되어 404 상태 코드가 발생합니다. 수정 후 축소가 활성화되면 축소되지 않은 JS 리소스가 요청되지 않습니다.

_ACP2E-4058 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 사용자 지정 속성 그룹의 날짜 속성이 관리자에 날짜 선택기를 표시하지 못함

사용자 지정 속성 그룹에 할당할 때 날짜 속성에 대한 달력 팝업이 화면 밖으로 표시되는 문제를 해결했습니다.

_ACP2E-4060 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### 고객 주문 GraphQL : 연결된 제품에 대한 제품 범주 검색은 &quot;개별적으로 표시되지 않음

수정 전에 주문에 숨겨진 제품이 포함된 경우 해당 카테고리가 고객 주문 GraphQl 응답에 빈 배열을 표시합니다.
이제 수정 후에는 제품이 숨겨져 있더라도 제품 카테고리가 고객 주문 GraphQl 요청의 응답에 포함됩니다.

_ACP2E-3945 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL, 인벤토리/MSI

#### GraphQL mergeCart 돌연변이 불일치

수정 후 GraphQL 요청은 재고 구성을 고려하여 제품 수량을 제대로 확인합니다.

_ACP2E-4184 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, 보안

#### GraphQL을 통해 재설정된 고객 암호는 제한 사항을 준수하지 않습니다

GraphQL 돌연변이를 통해 수행된 고객 암호 재설정 요청이 스토어 > 구성 > 고객 > 고객 구성 > 암호 옵션에 구성된 암호 재설정 제한을 준수하지 않던 문제를 해결했습니다. 이제 이러한 설정이 올바르게 적용됩니다.

_ACP2E-3992 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

### 가져오기/내보내기

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

### 인벤토리/MSI

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

### 주문

#### Magento 2.4.8 GraphQL - 주문 항목 order_date 잘못된 서식

GraphQL 응답의 order_date 필드가 yyyy-mm-dd 형식으로 반환되던 문제를 수정했습니다.
이제 order_date가 dd-mm-yyyy 형식으로 올바르게 표시됩니다.

_AC-14431 - [GitHub 문제](https://github.com/magento/magento2/issues/39805) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 스토어 구성에서 활성화되었지만 관리 주문 보기에서 제출할 때 선적 이메일이 전송되지 않음

이제 주문이 이루어진 스토어 구성에서 출하 확인 이메일을 사용할 수 있으므로 시스템이 출하 확인 이메일을 전송합니다.

_AC-14563 - [GitHub 문제](https://github.com/magento/magento2/issues/39861) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39897)_

#### 모호한 필드 이름으로 인해 날짜 필터링이 작동하지 않음

Magento 2.4.7-p6에서 날짜별로 순서 그리드를 필터링하면 Braintree 모듈과의 조인으로 인해 오류가 발생하는 것으로 보고되었습니다.
날짜 필터를 적용할 때 braintree_transaction_details 및 sales_order 테이블을 조인하는 쿼리와 관련된 문제입니다.
Adobe Commerce 엔지니어링이 사례를 검토했지만 환경에서 오류를 재현할 수 없었습니다.
예상 동작은 날짜별로 필터링하면 오류 없이 필터와 일치하는 순서가 반환되어야 한다는 것입니다.

_AC-15037 - [GitHub 문제](https://github.com/magento/magento2/issues/40024)_

#### Magento2: 프로모션 규칙을 만들 수 없음

이 PR은 다음과 같이 수정됩니다.
\Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions 메서드에서 \Magento\Catalog\Model\ResourceModel\Eav\Attribute 대신 \Magento\Catalog\Model\ResourceModel\Eav\Attribute 모델

_AC-15358 - [GitHub 문제](https://github.com/magento/magento2/issues/12176) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/30479)_

#### 송장 리디렉션을 404로 취소

캡처되지 않은 유형의 송장을 취소하면 더 이상 404페이지가 표시되지 않습니다.

_ACP2E-4001 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Sales Archive Cron 작업으로 인해 DB 잠금 문제가 발생합니다.

수정 전에 order archive cron에 있는 바인딩되지 않은 DELETE 쿼리로 인해 Galera에 문제가 발생했습니다. 이제 업데이트 후 삭제 쿼리가 제한적으로 실행됩니다.

_ACP2E-4010_

#### REST API를 사용하여 구성 가능한 옵션이 있는 업데이트된 주문 문제

rest api 끝점을 통해 주문을 업데이트할 때 판매 주문 항목에 대한 기존 제품 옵션을 유지합니다.

_ACP2E-4061 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

### 기타 개발자 도구

#### [문제] 사용하지 않는 코드를 정리하는 중입니다.

이제 시스템에서 사용되지 않은 가져오기와 관련된 사용되지 않은 코드를 제거합니다.

_AC-10980 - [GitHub 문제](https://github.com/magento/magento2/issues/38424) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/33499)_

#### [문제] 접근성: WAI-ARIA 역할이 메뉴에 잘못 중첩되었습니다.

이제 시스템은 메뉴 오류에 잘못 중첩되고 보고서가 녹색이 되어야 하는 WAI-ARIA 역할 없이 등대 접근성을 생성합니다

_AC-15082 - [GitHub 문제](https://github.com/magento/magento2/issues/40045) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/38617)_

#### Magento 관리자의 이메일 미리 보기에 콘솔 오류가 있습니다.

이메일 템플릿을 미리 볼 때 시스템에서 콘솔 오류가 발생하지 않습니다.

_AC-9245 - [GitHub 문제](https://github.com/magento/magento2/issues/37820) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/37933)_

### 결제

#### PayPal의 알 수 없는 IPN 남용 응용 프로그램 IPN 프로세서

이제 IPN 처리기에서 지원되지 않거나 알 수 없는 IPN 형식을 무시합니다. 500 오류를 반환하는 대신 문제를 기록하고 중단 없이 계속 처리합니다.

_ACP2E-4049 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 결제 시 PayflowPro 저장 카드 토큰 실패

PayPal PayFlow Pro 거래 ID(PNREF)는 이제 12개월의 고정 기간 동안 참조 거래에서 사용할 수 있습니다. 만료되면 저장된 카드가 더 이상 표시되지 않으므로 다시 추가해야 합니다. 기존에는 원래 거래에서 사용된 결제카드의 유효기간에 따라 유효성이 결정됐다.

_ACP2E-4064 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

### 성능

#### [문제] 업데이트 정적 사이트에 대해 캐시 컨트롤을 변경할 수 없습니다.

이 PR은 변경될 때까지 및 변경되지 않는 한 각 페이지 로드 시 정적 콘텐츠의 유효성을 검사하지 않으므로 성능이 향상됩니다.

_AC-15171 - [GitHub 문제](https://github.com/magento/magento2/issues/39486) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] 범주에 제품을 추가할 수 없습니다.

Visual Merchandiser를 통해 제품을 카테고리에 추가할 때의 성능이 향상되었습니다.

_ACP2E-3946 - [GitHub 코드 기여도](https://github.com/magento/inventory/commit/29653b1d)_

#### [클라우드] 캐시 무효화(10K를 초과하는 로그)

이전에는 각 PLP 또는 장바구니 방문에서 캐시가 지워져 불필요한 성능 오버헤드가 발생했습니다. 이러한 페이지에서 대상 규칙 캐시가 더 이상 무효화되지 않으므로 탐색 효율성을 개선합니다.

_ACP2E-4059_

### 가격 책정

#### 일괄 조치를 사용하여 특별 가격 시작 일자 가 종료 일자 이후인 경우에도 제품이 저장되고 있습니다.

유효성 검사 없이 잘못된 특별 가격 날짜 범위로 제품을 저장할 수 있는 문제를 해결했습니다.
이제, 오류 메시지가 표시됩니다. &quot;종료 날짜가 시작 날짜보다 이후이거나 동일한지 확인하십시오.&quot;

_AC-15252 - [GitHub 문제](https://github.com/magento/magento2/issues/40113) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 협상 가능 견적에 대한 paypal 빠른 체크아웃을 완료한 후 배송 세부 정보가 일치하지 않습니다.

이 문제는 승인된 협상 가능 견적에 대한 PayPal Express 체크아웃을 완료할 때 배송비가 일치하지 않는 문제를 해결했습니다.
수정 전에 배송이 두 배로 잘못 증가하여(5달러 대신 10달러 표시) 합계가 부풀려졌습니다.
Magento 2.4.9-alpha3의 수정 사항을 통해 정확한 배송 비용이 적용됩니다

_AC-15280_

#### 시간대가 다른 웹 사이트에는 특별 가격이 적용되지 않습니다.

수정되기 전에 현재 스토어 타임스탬프 범위에 특별 가격 날짜 유효성이 생성되었습니다. 이제 수정 후에는 기본 스토어 시간대가 고려됩니다.

_ACP2E-4002_

#### 특가를 적용해도 정가는 보이지 않는다.

특별 가격이 적용되었을 때 정가가 표시되지 않던 문제를 해결했습니다. 이제 예상대로 특가와 나란히 정가가 올바르게 등장한다.

_ACP2E-4100 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/47721be6)_

### 제품

#### 테스트 사례 AC-6158의 구성 가능한 제품에 대해 &#39;낮음&#39; 레이블이 여전히 표시됨

각 변형 및 범주 할당으로 구성 가능한 제품(P1-P7)을 구현하고 검증했습니다. 카테고리 C에 해당하는 제품에 대해 올바른 상점 가격 표시 및 &quot;최저 가격&quot; 레이블 동작을 확인했습니다.

_AC-10847 - [GitHub 코드 기여](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 저장소를 통해 제품 요청 실패 시 추가 로깅

SKU 또는 ID를 찾을 수 없는 경우 ProductRepository::get 및 getById에 대한 오류 메시지가 개선되었습니다.
이전에는 오류가 발생한 SKU 또는 ID에 대한 컨텍스트가 없는 예외가 제공되었습니다.
이제 예외 메시지에는 누락된 SKU 또는 ID가 포함되어 있어 디버깅 및 개발자 경험 개선에 도움이 됩니다.
이 변경 사항은 API의 기능 동작에 영향을 주지 않습니다.

_AC-15199 - [GitHub 문제](https://github.com/magento/magento2/issues/40090) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 제한된 역할로 구성 가능한 제품을 편집한 경우 간단한 제품 할당 해제됨

이 수정 이전에 제한된 관리자가 액세스 권한이 없는 간단한 제품이 포함된 구성 가능한 제품을 저장하면 저장 시 구성 가능한 제품에서 제거되었습니다. 수정 후에는 구성 가능한 제품이 전체 오른쪽 관리자의 저장으로 유지됩니다.

_ACP2E-4081_

#### [클라우드] 사이트 맵 생성 성능이 크게 저하되었습니다.

이미지가 있는 제품의 사이트 맵 생성으로 인해 더 이상 기하급수적인 둔화가 발생하지 않습니다. 이전에는 이미지 포함이 활성화된 스토어에 대해 사이트맵을 생성하면 처리 시간이 길어졌습니다.

_ACP2E-4153 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/e457c5e2)_

### 프로모션

#### GraphQl 고객 요청을 통해 고객 주문에 대해 적용된 주문 항목 할인(_To)을 가져오는 도중 오류 발생

이전에는 GraphQl을 통해 고객 주문에 대해 할인이 apply_to로 적용되던 경우, 이제 가 수정되고 할인이 적용된 적절한 고객 주문 데이터를 가져오는 내부 서버 오류가 관찰되었습니다

_AC-14888 - [GitHub 문제](https://github.com/magento/magento2/issues/39963) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQl 고객 요청을 통해 고객 주문에 대한 주문 항목 쿠폰 코드를 가져오는 도중 오류 발생

GraphQL을 통해 쿠폰 세부 사항이 있는 주문을 가져오면 내부 서버 오류가 반환되던 문제를 수정했습니다.
이제 쿼리가 성공적으로 실행되고 응답에 올바른 쿠폰 정보를 반환합니다.

_AC-14889 - [GitHub 문제](https://github.com/magento/magento2/issues/39962) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### ProductRepository getById에 정의되지 않은 배열 키

123abc와 같은 잘못된 ID로 ProductRepository::getById()가 호출되어 &quot;정의되지 않은 배열 키&quot; 오류가 발생하는 경우 문제가 발생했습니다.
Magento 2.4.9-alpha3가 수정된 후 이러한 요청은 이제 예외를 발생시키는 대신 404 페이지를 올바르게 반환합니다.
QA가 유효한 ID와 잘못된 ID로 확인되었으며 추가 문제는 관찰되지 않았습니다.

_AC-15345 - [GitHub 문제](https://github.com/magento/magento2/issues/40146) - [GitHub 코드 기여](https://github.com/magento/magento2/commit/68a45d0a)_

#### [클라우드] 사이트 맵 생성이 끝나지 않음

수정 전에, 카탈로그에 백만 개 이상의 제품이 포함된 경우 사이트 맵 생성을 성공적으로 완료할 수 없습니다. 수정 후 사이트 맵 생성은 낮은 메모리 할당과 매장당 최대 100만 개의 제품으로 완료됩니다.

_ACP2E-3902 - [GitHub 코드 기여도](https://github.com/magento/magento2/commit/52f46328)_

#### FAQ 페이지에 대한 EN에서 FR로 [Cloud] 스토어 전환기가 작동하지 않음

스토어 보기 간 전환으로 사용자가 번역된 해당 CMS 페이지 대신 홈 페이지로 리디렉션되는 문제를 해결했습니다. 이제 스토어 전환기가 대상 스토어에서 URL 재작성을 확인하여 올바른 리디렉션이 수행되는지 확인합니다(예: 영어의 FAQ 페이지 → 프랑스어의 FAQ 페이지).

_ACP2E-4112_

### 스테이징 및 미리보기

#### 다른 관리 도메인을 사용할 때 체크아웃 시 스테이징 업데이트 미리보기가 중단됨

스토어 기본 URL이 관리자 URL과 다른 경우 고객은 스토어 미리보기 모드에서 로그인하여 장바구니를 볼 수 있습니다.

_ACP2E-3906_

#### 컨텐츠 스테이징 대시보드 시간 표시가 잘못됨

이제 &quot;콘텐츠 스테이징 대시보드&quot;의 &quot;시작 시간&quot; 및 &quot;종료 시간&quot; 날짜 필터에 올바른 날짜 및 시간이 표시됩니다. 이전에는 날짜 선택기에서 날짜와 시간을 선택한 후 잘못된 날짜와 시간이 표시되었습니다

_ACP2E-3969_

#### 예약된 업데이트 제품 및 범주에 대한 미리 보기 중 범위에 다른 스토어 보기가 표시됩니다.

이 전에 카테고리 및 제품에 대한 미리보기 링크가 올바른 스토어에 대해 생성되지 않았습니다. 이 수정 사항이 적용되면 미리보기 링크가 미리보기를 만든 스토어를 자동으로 선택합니다.

_ACP2E-4053_

### UI 프레임워크

#### [문제] `@author`에서 금지된 `Magento_Backend` 태그를 제거하십시오.

이 PR은 코드 베이스에서 `@author` 태그를 제거합니다.

_AC-8814 - [GitHub 문제](https://github.com/magento/magento2/issues/37522) - [GitHub 코드 기여](https://github.com/magento/magento2/pull/36976)_
