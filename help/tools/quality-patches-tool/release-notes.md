---
title: 릴리스 정보
description: Adobe Commerce에 사용할 수 있는 패치와 이러한 패치가 해결하는 문제에 대해 알아봅니다.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 26bde6684b3f38ed16ede6ec9c63cc90fa849fd9
workflow-type: tm+mt
source-wordcount: '19990'
ht-degree: 0%

---

# 릴리스 정보

다음 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 은 Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치를 제공합니다. 설치된 버전의 Adobe Commerce 또는 Magento Open Source에 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리기 및 볼 수 있습니다. 누가 패치를 개발했는지에 관계없이 Adobe Commerce 및 Magento Open Source 프로젝트에 패치를 적용할 수 있습니다. 예를 들어 커뮤니티에서 개발한 패치를 Adobe Commerce 프로젝트에 적용할 수 있습니다.

>[!INFO]
>
>다음을 참조하십시오 [패치 적용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) Adobe Commerce 또는 Magento Open Source 프로젝트에 패치를 적용하는 방법에 대한 지침입니다. 다음을 참조하십시오 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 릴리스된 패치의 전체 목록을 검토하려면 소프트웨어 업데이트 안내서를 참조하십시오.

>[!INFO]
>
>다음에 대한 정보: [!DNL quality patches] 커뮤니티에서 Magento Open Source을 위해 만들었습니다. [릴리스 정보](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 제품이 아직 재고가 있더라도 재고 수량이 변경되면 카테고리 페이지가 캐시되는 문제가 해결됩니다.
* **ACSD-54656** (Adobe Commerce >=2.4.5 &lt;2.4.6) - 체크아웃 중에 보이지 않는 Recaptcha가 실패하여 주문이 이루어지지 않는 문제를 수정합니다.
* **ACSD-55100** (Adobe Commerce >=2.4.6 &lt;2.4.7) - GraphQL이 검색 결과에서 1만 개 이상의 제품을 반환하지 않는 문제를 해결합니다.
* **ACSD-56621** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 회사 관리자의 경우 업데이트된 이름과 성이 인사말 헤더 섹션에 반영되지 않는 문제가 수정되었습니다.
* **ACSD-56842** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 실행 후 지연된 프록시 및 지연된 프록시 팩토리가 누락된 문제를 수정합니다 `setup:di:compile`.
* **ACSD-57003** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 주문 상태가 변경되는 문제를 수정합니다. *[!UICONTROL Complete]* 을 로 변경하지 않고 *[!UICONTROL Processing]* 주문이 일부 환불 및 일부 배송된 경우.
* 업데이트된 패치: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 예약된 업데이트로 인해 두 개의 하위 제품 중 하나가 비활성화될 때 구성 가능한 제품이 품절되는 문제를 수정합니다.
* **ACSD-56616** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 번들 제품이 단순 제품이 품절되었을 때 상점 앞에 재고로 표시되는 문제를 수정합니다.
* **ACSD-56515** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 웹 사이트 수준 권한이 있는 관리자가 동적 블록을 추가하거나 편집할 수 없는 문제를 수정합니다.
* **ACSD-56447** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 병렬 REST 웹 API 요청을 통해 동일한 제품을 장바구니에 추가하면 장바구니에 두 개의 개별 항목이 표시되는 문제를 수정합니다.
* **ACSD-56415** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 다음 이유로 인해 부분 가격 인덱싱의 성능이 느려지는 문제가 해결되었습니다. `DELETE` 데이터베이스에 색인화할 부분 가격 데이터가 많은 경우 쿼리합니다.
* **ACSD-54965** (Adobe Commerce >=2.4.5 &lt;2.4.6) - 제품이 사용자 지정 주식에만 할당된 경우 시각적 머천다이징 그리드에 올바른 재고가 표시되지 않는 문제가 수정되었습니다.
* **ACSD-52824** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 회사 설정에서 결제 방법이 비활성화된 경우 회사 고객을 위해 PayPal Express, Google Pay 및 Apple Pay 버튼이 표시되는 문제를 수정합니다.
* 업데이트된 패치: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 를 사용하여 범주 제품을 정렬할 때 사용자가 관리 대시보드로 리디렉션되는 문제를 해결합니다. **품에서 아래로 이동** 옵션 및 `Invalid security or form key. Please refresh the page` 화면 상단에 오류가 표시됩니다.
* **ACSD-56280** (Adobe Commerce >=2.4.4 &lt;2.4.7) - 선물 레지스트리에서 항목 순서를 변경하면 예외가 발생하는 문제를 수정합니다.
* **ACSD-56246** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 제품에 대한 예정된 업데이트가 활성화될 때 사용자 지정 다중 선택 속성에서 데이터가 제거되는 문제를 해결합니다.
* **ACSD-56193** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4)의 경우 - 예약된 블록이 페이지 빌더를 사용하여 범주 설명에 사용될 때 Varnish/Fastly 캐시가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-56158** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - &quot;장바구니&quot; 쿼리가 각 세금 규칙에 대한 총 세금 값을 반환하는 문제를 수정합니다.
* **ACSD-56023** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 캐시가 활성화되면 CMS 페이지에서 위젯 콘텐츠가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-55427** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 관리 사용자가 관리자의 제품 페이지에서 공유 카탈로그의 제품 할당을 취소할 수 없는 문제를 해결합니다.
* **ACSD-55352** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 고객 보상 포인트가 있는 부분 대변 메모를 만든 후 주문 상태가 마감됨으로 변경되고 대변 메모 옵션이 관리자 주문 페이지에서 사라지는 문제를 수정합니다.
* **ACSD-55231** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 빠른 주문 기능을 사용하여 장바구니에 제품을 추가할 수 없는 문제를 해결했습니다.
* **ACSD-54283** (Adobe Commerce >=2.4.3 &lt;2.4.4)의 경우 - 기본값(일반 그룹)에 대한 공유 카탈로그에 할당되지 않은 제품/범주가 여전히 XML 사이트 맵에 포함되는 문제를 해결합니다.
* 업데이트된 패치: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않는 문제를 해결합니다.
* **ACSD-53636** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5) - 특별 가격이 있는 하위 제품이 구성 가능한 제품의 제품 목록 페이지에 정기 가격이 표시되지 않는 문제를 수정합니다.
* **ACSD-54885** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 관리 사용자가 를 사용할 때 여러 주소 체크아웃 문제를 수정합니다. *고객으로 로그인* 기능.
* **ACSD-55610** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 문제를 수정합니다.
* **ACSD-55334** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - GraphQL 응답의 번역 사전을 통해 레이블에 대한 번역을 수정합니다.
* **ACSD-54739** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 제품 재고 상태 조건이 관련 제품 규칙에 적용되지 않는 문제를 수정합니다.
* **ACSD-53925** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 다음과 같은 경우 관리자가 제품 캐러셀에 CMS 블록을 저장할 수 없는 문제가 해결되었습니다. `catalog_product_price` 차원 모드가 다음으로 설정됨 *웹 사이트*.
* **ACSD-52714** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 날짜 형식이 로 설정된 경우 관리 그리드에서 날짜 필터가 작동하지 않는 문제가 수정되었습니다. *Y-m-d*.
* **ACSD-55055** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 장바구니에서 장바구니 가격 규칙에 제품 속성을 로드하는 성능을 개선합니다.
* **ACSD-53790** (Adobe Commerce >=2.4.6 &lt;2.4.7) - REST API를 통해 단일 제품에 대한 여러 RMA를 만들 수 있는 문제를 수정합니다.
* **ACSD-56090** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5) - GraphQL 요청이 특별히 요청된 스토어 데이터가 아닌 모든 스토어의 데이터로 응답하는 문제를 수정합니다.
* **ACSD-54983** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 사용자 상태가 (으)로 설정된 경우 GraphQL 요청으로 회사 사용자 UID를 가져올 수 없는 문제를 해결했습니다. *[!UICONTROL Inactive]*.
* **ACSD-53309** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 세금이에서 완전히 적용되지 않는 문제를 수정합니다. *[!UICONTROL Regular Price]* 사용자 지정 가능 옵션을 선택한 경우 레이블로 표시합니다.
* **ACSD-55305** (Adobe Commerce >=2.4.4 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. *[!UICONTROL Edit Company User]* 다음에 팝업 **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** 페이지가 화면에 로더로 고정되어 있습니다.
* 업데이트된 패치: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 다음 문제를 수정합니다. *[!UICONTROL Recently Viewed]* 스토어 보기에서 제품 데이터가 제대로 업데이트되지 않습니다.
* **ACSD-54626** (Adobe Commerce >=2.4.6 &lt;2.4.7) - 새 구매 주문 규칙을 만들 수 없는 문제를 수정합니다(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` 속성 [!DNL GraphQL].
* **ACSD-53845** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 수정 사항 [!DNL MySQL] 다음의 경우 연결 시간 초과 문제 `consumer max_messages` = 0.
* **ACSD-54890** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 다음 문제를 수정합니다. `aggregate_sales_report_bestsellers_data` 원인 [!DNL MySQL] 오류로 인해 발생 `/tmp` 디스크 공간이 부족합니다.
* **ACSD-55112** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. *[!UICONTROL Submit review]* 없이 단추를 여러 번 클릭할 수 있습니다. [!DNL Google reCAPTCHA v3] 유효성 검사.
* **ACSD-54264** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - 오류 메시지가 표시되는 문제를 수정합니다 *&quot;요청한 특성을 업데이트할 수 없습니다. 행 ID: store_id&quot;* 고객이 다른 스토어 뷰에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.
* **ACSD-54418** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 문제를 수정합니다.
* **ACSD-55238** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 빈 제품을 저장하는 수정 사항 *[!UICONTROL Meta Description]*.
* **ACSD-54966** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 이전 주문이 실패한 경우 고객당 사용이 제한된 쿠폰 코드를 다시 사용할 수 없는 문제를 수정합니다.
* **ACSD-54060** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 제한된 관리자가 다른 범위에 할당된 다른 제품의 하위 항목인 경우 제품을 저장할 수 없는 문제를 수정합니다.
* **ACSD-48910** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 아직 수량이 0이 아닌 경우에도 주문이 송장발행되어 배송된 후 여러 출처에 할당된 번들 제품의 재고가 소진되는 문제가 해결되었습니다.
* **ACSD-55381** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 쿼리할 때 내부 서버 오류 수정 `configurable_product_option_uid` 및 `configurable_product_option_value_uid` 의 필드 [!DNL B2B] *[!UICONTROL Requisition list]* 경유 [!DNL GraphQL].
* **ACSD-55628** (Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 바꾸는 수정 사항이 있습니다.
* 업데이트된 패치: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 제품이 장바구니에 이미 추가된 후 공유 카탈로그에서 제거될 때 장바구니에서 발생하는 문제를 수정합니다.
* **ACSD-53722** (Adobe Commerce >=2.4.4 &lt;2.4.7) - 다른 범위에 대한 예약된 업데이트가 활성화되면 번들 제품 옵션의 가격이 $0로 변경되는 문제를 수정합니다.
* **ACSD-53643** (Adobe Commerce >=2.4.3 &lt;2.4.7) - 비활성화 또는 재고 부족 제품으로 구매 주문을 할 때 주문 합계가 잘못된 문제를 수정합니다. 다음을 숨김으로써 수정됩니다. *[!UICONTROL Place Order]* 버튼을 클릭합니다.
* **ACSD-54067** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 제품 비디오가 모바일 디바이스에서 재생되지 않는 문제를 수정합니다.
* **ACSD-55414** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - MariaDB가 EAV entity_id를 문자열에서 정수로 캐스팅하려고 할 때 성능이 향상됩니다.
* **ACSD-51819** (Adobe Commerce >=2.4.4 &lt;2.4.4-p4의 경우) - 동일한 견적 ID로 여러 주문을 할 수 있는 문제를 수정합니다.
* **ACSD-53118** (Adobe Commerce >=2.4.0 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. *[!UICONTROL Cart Price Rule]* 은 제품에 빈 속성이 있는 동안 쿠폰 코드를 사용하여 적용됩니다.
* **ACSD-54324** (Adobe Commerce >=2.4.5 &lt;2.4.7) - GraphQL 구매요청 목록 요청이 페이지 매김 설정을 고려하지 않고 모든 결과를 반환하는 문제를 수정합니다.
* 업데이트된 패치: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (Adobe Commerce >=2.4.0 &lt;2.4.6) - 여러 개의 할당된 소스가 있는 제품에 대해 제출된 B2B 견적을 처리할 수 없는 문제를 수정합니다.
* **ACSD-54040** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - 다음과 같은 문제가 해결되었습니다. *[!UICONTROL Created]* B2B 모듈이 활성화되면 필드가 비어 있는 주문 세부 사항.
* **ACSD-54319** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 에서 제품 가격이 0으로 표시되는 문제를 수정합니다. *[!UICONTROL Product in Cart]* 보고서.
* **ACSD-53378** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 주소록이 많은 고객의 체크아웃 페이지 로드 시간을 개선합니다.
* **ACSD-52657** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 하위 도메인을 사용하는 보조 스토어뷰에서 미니 마트가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-53414** (Adobe Commerce >=2.4.6 &lt;2.4.7) - 제한된 관리자가 권한 범위 외부에서 CMS 페이지를 볼 수 있는 문제를 해결했습니다.
* **ACSD-54472** (Adobe Commerce >=2.4.6 &lt;2.4.7) - 거부된 회사의 고객이 계속 인증할 수 있고, 차단되고 거부된 회사의 고객이 여전히 주문을 할 수 있는 문제를 수정합니다. 이 패치는 GraphQL 종단점에 대한 추가 유효성 검사를 추가합니다.
* **ACSD-52801** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - GraphQL에서 제품을 검색할 때 부분 일치를 수행하는 옵션을 추가합니다.
* **ACSD-55004** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 구성된 값보다 큰 가져오기 파일을 업로드하는 동안 유효성 검사기가 충돌하는 문제가 해결되었습니다. `php.ini`.
* **ACSD-54989** (Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - 다음 경우에 회사 관리자가 주문할 수 없는 문제가 해결되었습니다. *[!UICONTROL Enable Purchase Orders]* 이(가) (으)로 설정됨 *[!UICONTROL Yes]* 및 *[!UICONTROL Purchase Order]* 이(가) (으)로 설정됨 *[!UICONTROL No]*.
* **ACSD-54007** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류를 수정합니다. *&quot;정의되지 않은 배열 키 &quot;_scope&quot;&quot;* 고객 데이터 가져오기
* **ACSD-55031** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 수정 사항 *&quot;mixed&quot; 형식은 null을 허용할 수 없습니다.* 컴파일 중 오류가 발생했습니다.
* **ACSD-54961** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 제한된 관리자가 *제품 리뷰* 상태.
* **ACSD-55256** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 이미지 슬라이더에 첫 번째 이미지만 표시되는 문제를 수정합니다.
* 업데이트된 패치: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (Adobe Commerce >=2.4.0 &lt;2.4.7) - 보상 포인트 만료 후 보상 포인트 균형 내역이 잘못 계산되는 문제를 수정합니다.
* **ACSD-53583** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 의 부분 색인 재지정 성능 개선 *범주 제품* 및 *제품 범주* 인덱서입니다.
* **ACSD-54026** (Adobe Commerce >=2.4.6 &lt;2.4.7) - 의 잘못된 오류 메시지를 수정합니다. `updateCompanyRole` 권한이 없는 사용자에 대한 GraphQL 요청입니다.
* **ACSD-54106** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5) - 터키어 악센트 부호가 있는 문자의 이름별 카테고리 제품 정렬이 올바르지 않은 문제를 수정합니다.
* **ACSD-52219** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 책갈피 보기 사이를 자주 전환할 때 관리 그리드 저장 필터가 예상대로 작동하지 않는 문제를 해결했습니다.
* **ACSD-54342** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 잘못된 오류 메시지 수정 *데이터 구조 오류: 값이 혼합되었습니다.* 유효한 데이터가 없는 CSV 파일을 가져올 때.
* **ACSD-54660** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 새 입력 속성이 추가되었습니다. *sort* GraphQL에서 고객 주문 정렬 기준 `sort_field` 및 `sort_direction`.
* **ACSD-54776** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 선택 취소되는 문제가 해결되었습니다. *[!UICONTROL Use Default Value]* 및 기본값이 아닌 제품 필드 값은 두 번째 웹 사이트, 스토어 및 스토어 보기에 대해 저장되지 않습니다.
* **ACSD-53998** (Adobe Commerce 및 Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - 이 발생하는 문제가 해결되었습니다. **[!UICONTROL Dynamic Block]** 를 기반으로 함 **[!UICONTROL Customer Segment]** 은 고객 계정에서 로그아웃한 후 올바르게 작동하지 않습니다.
* **ACSD-53204** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 수정 사항 *제품을 저장할 수 없습니다.* 을(를) 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때 오류 발생 `rest/V1/products/<sku>/media` 엔드포인트.
* **ACSD-47657** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - AWS 자격 증명에 대한 캐싱 메커니즘을 추가했습니다. 이제 자격 증명 공급자는 Magento 캐시를 사용하여 EC2 구성을 위해 AWS에서 검색한 자격 증명을 캐시합니다.
* 업데이트된 패치: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4) - 부분 색인이 실행될 때 공유 카탈로그에 할당된 제품이 상점 앞에 표시되지 않는 문제를 수정합니다.
* **ACSD-54018** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 의 성능 문제를 수정합니다. [!UICONTROL Product List] 위젯 조건에서 비전역 속성을 사용하는 위젯.
* **ACSD-54111** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 워터마크 이미지의 종횡비가 제품 이미지와 일치하지 않을 때 제품 썸네일 이미지가 상점 앞에 표시되지 않는 문제를 수정합니다.
* **ACSD-47669** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 수정 사항 *무결성 제약 조건 위반: 1452 하위 행을 추가하거나 업데이트할 수 없음: 외래 키 제약 조건이 실패합니다* 제품 CSV를 가져오는 중 오류가 발생했습니다.
* **ACSD-53347** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 가격 인덱서를 실행하는 데 시간이 너무 오래 걸리는 문제를 해결했습니다.
* **ACSD-52287** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 비동기 그리드 인덱싱이 활성화되면 보관된 주문 그리드에서 잘못된 주문 상태가 발생하는 문제를 수정합니다.
* **ACSD-52929** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 인벤토리 인덱서가 비동기 모드로 구성된 경우 기본 소스 항목의 인덱스를 다시 인덱싱하는 중복 요청 문제를 수정합니다.
* **ACSD-53824** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 다음 문제를 수정합니다. `UpdateMultiselectAttributesBackendTypes` 다음 기간 동안 마이그레이션 데이터 패치가 데이터베이스 트랜잭션 크기 제한을 초과합니다. `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 업데이트가 없더라도 캐시 및 색인이 새로 고침되는 문제가 수정되었습니다. `Inventory_source` rest API별 항목.
* **ACSD-51884** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - resize 명령을 실행한 후 제품 이미지 캐시 경로가 올바르지 않게 되는 문제를 수정합니다.
* **ACSD-53628** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - CSV 판매 주문 보고서에 잘못된 특수 문자가 표시되는 문제가 수정되었습니다.
* **ACSD-53148** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 구성 가능한 동일한 제품을 장바구니에 추가하기 위해 GraphQL에서 두 개의 병렬 요청이 결과적으로 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목이 표시되는 문제를 해결합니다.
* **ACSD-52606** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류 메시지가 표시되는 문제를 수정합니다 *주문하신 물건이 픽업 준비가 되지 않았습니다* 을 클릭하면 표시됩니다 **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 이미지를 동일한 이름의 다른 이미지로 바꾼 후 프론트엔드에서 이미지가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-53728** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제품 EAV 인덱서를 완료하는 데 시간이 더 오래 걸리는 문제를 해결했습니다.
* **ACSD-53979** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 시작 메시지에 작은 따옴표가 포함된 경우 홈페이지에서 발생하는 JS 문제를 수정합니다.
* **ACSD-52085** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 특별 가격이 있는 구성 가능한 제품이 제품의 슬라이드에 표시되지 않는 문제를 해결했습니다.
* **ACSD-53795** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 의 잘못된 데이터 유형 문제를 수정합니다. `indexer_update_all_views` cron job.
* **ACSD-52143** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 제품 가져오기 후 사용자 지정 옵션이 제거되는 문제를 수정합니다.
* **ACSD-53750** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 수정 사항 *끊어진 파이프 또는 닫힌 연결* 다중 스레드 도중 오류 발생 `catalog_product_price` 색인 재지정.
* **ACSD-49843** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - 온라인 결제 방법으로 주문 품목이 자동 청구된 후 제품 다운로드에 대한 링크를 사용할 수 없는 문제를 해결했습니다. **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** 설정이 활성화되었습니다.
* **ACSD-47054** (Adobe Commerce >=2.4.2 &lt;2.4.6) - 미리보기 색인 재지정이 모든 스토어에 대해 색인 재지정을 실행하여 속도가 느려지는 문제를 수정합니다.
* ACSD-46541, ACSD-47079용 새 버전이 추가되었습니다.
* ACSD-49970-v3이 ACSD-54095으로 대체되었습니다.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt; 2.4.6의 경우) - 인벤토리 인덱서가 업데이트 시 예약 모드에서 모든 캐시를 정리하는 문제를 수정합니다.
* **ACSD-50887** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 제품 속성 속성이 발생하는 문제를 해결합니다. *[!UICONTROL Use in Search Results Layered Navigation]* 을 로 설정할 수 있습니다. *예* 없이 *[!UICONTROL Use in search]* 옵션이 로 설정됨 *예*.
* **ACSD-51846** (Adobe Commerce 및 Magento Open Source >=2.4.3-p2 &lt;2.4.6) - 수정 사항 *내부 오류* 모든 수준의 REST API 페이로드의 유효성을 검사하지 않았기 때문에 발생하는 문제입니다.
* **ACSD-52906** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 동일한 고객 세그먼트에 속하는 로그인한 고객이 일부 페이지에 부적절한 캐싱을 방지하기 위해 X-Magento-Vary 쿠키가 잘못 설정되는 문제가 수정되었습니다.
* **ACSD-52736** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 다음과 같은 문제가 해결되었습니다. *장바구니 가격 규칙* 구성 가능한 제품 수량에 대한 요구 사항이 포함된 이 예상대로 작동하지 않습니다.
* **ACSD-47875** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 재고 관리를 사용하는 특정 스토어 보기 범위에 대해 관리자 사용자가 관리자의 고객 장바구니에 제품을 추가할 수 없는 문제를 해결했습니다.
* **ACSD-53176** (Adobe Commerce >=2.3.7 &lt;2.4.5) - 다음 문제를 수정합니다. *관련 제품 규칙* 포함 *다음 중 하나* 조건이 제품과 일치하지 않습니다.
* **ACSD-51666** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 오류를 수정합니다. *세션이 만료되었습니다. 다시 로그인하십시오.* 이는 고객이 로그인을 시도한 후 발생합니다.
* MDVA-39305-v2에 대한 새 버전이 추가되었습니다.
* ACSD-19640에 대한 요구 사항이 업데이트되었습니다.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 체크아웃 배송 단계의 기본 배송 주소가 이전에 선택한 매장 픽업 주소로 자동 채워지는 문제를 수정합니다.
* **ACSD-52041** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 오류 메시지가 표시되는 문제를 수정합니다. *[오류] [!DNL Page Builder] 은(는) 잠금을 해제하지 않고 5초 동안 렌더링했습니다.* 을 사용하여 편집한 컨텐츠를 저장할 때 Chrome 브라우저에 표시 [!DNL Page Builder].
* **ACSD-52095** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 다음과 같은 문제를 수정합니다. `manage_stock` 제품 내보내기 후 CSV 파일에서 값이 0으로 잘못 설정되었습니다.
* **ACSD-51358** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 종료 날짜 없이 예약된 업데이트를 제거하면 동일한 엔터티에 대해 다른 예약된 업데이트가 제거되는 문제가 해결됩니다.
* **ACSD-48070** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 예약된 업데이트를 편집하면 예외가 트리거되는 문제가 해결됩니다.
* **ACSD-51890** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. [!UICONTROL Submit review] 없이 단추를 여러 번 클릭할 수 있습니다. [!DNL Google reCAPTCHA] v3 유효성 검사.
* **ACSD-51984** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 선택 취소되는 문제가 해결되었습니다. *[!UICONTROL Use Default Value]* 및 *[!UICONTROL non-default product field]* 두 번째 웹 사이트, 스토어 및 스토어 보기에 대한 값은 저장되지 않습니다.
* **ACSD-52398** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류를 수정합니다. *요청한 수량을 사용할 수 없습니다.* 이 문제는 상점 앞의 장바구니에 있는 번들 제품의 수량을 업데이트하려고 할 때 발생합니다.
* **ACSD-52786** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 카탈로그 규칙 조건이 발생하는 문제를 수정합니다. *SKU:* 은 제공된 SKU로 시작하는 모든 제품에 적용됩니다.
* **ACSD-52921** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 장바구니에 품절 구성 가능한 제품이 있을 때 GraphQL에서 장바구니 세부 정보를 요청할 때 내부 오류가 발생하는 문제를 수정합니다.
* **ACSD-51683** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 문제를 해결했습니다.
* **ACSD-52133** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 업그레이드 후 고객 계정을 저장할 수 없는 문제를 수정합니다.
* **ACSD-52202** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 주문 이행 시 기본이 아닌 재고가 0으로 변경되면 기본 재고의 판매 가능 수량이 0으로 잘못 변경되는 문제가 해결됩니다.
* **ACSD-51265** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 문제 해결 `catalog_product_price` 시스템에 번들 제품이 너무 많을 때 성능 리인덱싱
* **ACSD-52831** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 다음과 같은 경우 고객이 협상 가능한 견적 주문을 할 수 없는 문제를 수정합니다. [!DNL Google reCAPTCHA v3 Invisible] 이(가) 활성화되었습니다.
* **ACSD-51845** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 계층 가격과 다른 속성 세트가 있는 후속 제품을 비동기 대량 REST API를 통해 업데이트할 수 없는 문제를 수정합니다.
* **ACSD-52815** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 기본 재고의 경우 8과 달리, 기본값이 아닌 출처의 수량 필드에 대한 입력이 최대 6자리를 지원하는 문제를 수정합니다.
* **ACSD-51149** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 카탈로그 권한이 활성화된 예약된 ImportExport가 인덱서를 무효화한 다음 cron을 통해 캐시 플러시를 활성화하는 문제가 수정되었습니다.
* **ACSD-50815** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 단순 제품의 십진수 수량을 새 번들 제품 옵션에 사용할 수 없는 문제를 수정합니다.
* ACSD-47803용 버전이 업데이트되었습니다.
* ACSD-51892의 제목을 업데이트했습니다.
* ACSD-51379이 업데이트되었습니다.
* ACSD-49970-v2를 업데이트했습니다.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - Admin에서 새 주문을 만들 때 스토어 보기를 선택한 후 관리자 사용자가 제대로 리디렉션되지 않는 문제를 해결했습니다.
* **ACSD-50813** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 관리자가 SKU에서 [!UICONTROL Add Products by SKU] 관리 순서에 대한 기능입니다.
* **ACSD-51630** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 대량의 시스템 메시지가 관리 페이지의 다운로드를 지연시키는 문제를 해결합니다.
* **ACSD-51853** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.7) - 를 사용할 때 복사된 텍스트 스타일이 적용되지 않는 문제를 해결합니다. [!UICONTROL Page Builder].
* **ACSD-52160** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 규칙 조건 &#39;이 모든 조건 중 하나/하나가 참인 장바구니에서 항목을 찾을 수 없음/찾을 수 없음&#39;을 기반으로 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 제대로 평가되지 않는 문제를 수정합니다.
* **ACSD-51636** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 필요한 모든 역할과 권한이 있음에도 불구하고 회사 관리자가 고객 계정 섹션에서 새 사용자를 추가할 수 없는 문제를 해결했습니다.
* **ACSD-51739** (Adobe Commerce >=2.4.6 &lt;2.4.7) - 다음과 같은 경우 오류가 반환되는 문제가 해결됩니다. `structure_id` 은(는) CompanyTeam GraphQL 요청에서 요청됩니다.
* **ACSD-51857** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 의 성능이 저하되는 문제가 해결되었습니다. `aggregate_sales_report_bestsellers_data` 큰 sales_order에 대한 cron 보고서 및 `sales_order_item` 데이터베이스 테이블은 기본 데이터 쿼리가 작성된 방식 때문이었습니다.
* **ACSD-48448** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 주문 취소 중에 경합 조건 문제가 발생하여 `inventory_reservation` 테이블.
* **ACSD-52689** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.6) - REST API를 사용하여 이미지를 Amazon S3 스토리지에 업로드할 수 없는 문제를 해결했습니다.
* **B2B-2674** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 1customAttributeMetadata1 GraphQL 쿼리에 캐싱 기능을 추가합니다.
* ACSD-44938용 새 버전이 추가되었습니다.
* ACSD-46988에 대한 요구 사항이 추가되었습니다.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5) - DB 덤프에 트리거 및 가 포함된 경우에 대한 데이터베이스 롤백 명령을 수정합니다. *구분 기호* SQL 명령.
* **ACSD-50512** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 수정 사항 *오류: 다운로드 가능한 링크가 제품과 관련이 없습니다. 링크를 확인하고 다시 시도하십시오.* 다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 발생하는 오류입니다.
* **ACSD-50949** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - SKU 필터와 함께 사용할 때 고급 검색의 가격 필터가 적절한 결과를 반환하지 않는 문제를 수정합니다.
* **ACSD-51645** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 확장 프로그램인 경우 새 장바구니 가격 규칙을 저장할 때 발생하는 오류를 수정합니다 `Magento_OfflineShipping` 이(가) 비활성화되었습니다.
* **ACSD-50895** (Adobe Commerce >=2.4.5 &lt;2.4.7) - 다음 문제를 수정합니다. [!DNL Google Analytics] 3 다음과 같은 경우에는 GTM 태그가 실행되지 않습니다 [!DNL Google Analytics] 4 GTM이 구성되지 않았습니다.
* **ACSD-51102** (Adobe Commerce >=2.4.2 &lt;2.4.7) - 예약된 업데이트로 인해 규칙이 활성화될 때 많은 수의 제품에 적용되는 카탈로그 규칙이 올바르게 인덱싱되지 않는 문제가 수정되었습니다.
* **ACSD-50368** (Adobe Commerce 및 Magento Open Source >= 2.4.3 &lt;2.4.5) - 고객의 `group_id` 비동기 REST API 또는 비동기 벌크 REST API를 통해 고객을 만들면 이 무시됩니다.
* **ACSD-51497** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - 고객이 드롭다운 유형의 사용자 지정 속성으로 카탈로그 페이지를 정렬할 수 없는 문제를 수정합니다.
* **ACSD-51408** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt; 2.4.7의 경우) - 주문 항목 상태가 로 잘못 설정되는 문제가 수정되었습니다. *[!UICONTROL Backordered]*.
* **ACSD-51735** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 주문 항목 상태가 로 잘못 설정되는 문제가 수정되었습니다. *[!UICONTROL Ordered]* 제품 재고 *0*.
* **ACSD-51792** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 다음과 같은 경우 페이지에 노출 이벤트가 없는 문제가 해결됩니다. [!DNL Google Tag Manager] 4가 활성화되었습니다.
* **ACSD-51471** (Adobe Commerce >=2.4.3 &lt;2.4.7) - 관리자가 자체적으로 예약된 업데이트가 있는 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없는 문제를 수정합니다.
* **ACSD-51700** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 발생하는 오류를 수정합니다.
* **ACSD-51120** (Adobe Commerce >=2.3.7 &lt;2.4.3) - 스테이징 업데이트를 통해 업데이트된 CMS 블록이 포함된 CMS 페이지에 대해 GraphQL GET 요청 캐시가 지워지지 않는 문제를 수정합니다.
* **ACSD-51240** (Adobe Commerce >=2.4.4 &lt;2.4.6) - 회사 등록 양식을 통해 등록한 경우 업로드된 파일이 누락되는 문제를 수정합니다.
* **ACSD-51907** (Adobe Commerce >=2.4.2 &lt;2.4.3) - 제한된 관리 사용자가 오프라인 환불로 대변 메모를 만들 수 없는 문제를 해결했습니다.
* **ACSD-52148** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4) - 다음과 같은 문제를 수정합니다. [!DNL Google V3 reCAPTCHA] 관리자 로그인이 가끔 실패했습니다.
* **ACSD-51431** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 인덱서 상태가 인 문제를 수정합니다. *작업 중* 변경 로그에 새 항목이 없더라도
* **ACSD-51892** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 구성 파일이 여러 번 로드되는 성능 문제를 수정합니다.
* 사용되지 않는 ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. [!UICONTROL Page Builder's] 여러 오류로 인해 관리자는 콘텐츠 권한 없이 제품을 저장할 수 없습니다.
* **ACSD-51305** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - GraphQL 응답에서 품절 구성 가능한 하위 제품을 사용할 수 없는 문제를 수정합니다.
* **ACSD-50621** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 다음 문제를 수정합니다. [!UICONTROL Tier Prices] 공유 카탈로그의 다른 웹 사이트의 경우 다중 웹 사이트 환경에서 편집하려고 하면 표시되지 않습니다.
* **ACSD-51041** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - 가격 인덱서의 성능이 향상됩니다.
* **ACSD-51379** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 를 통해 페이지 텍스트 콘텐츠에 수행된 변경 사항의 문제를 수정합니다. [!UICONTROL Page Builder] 저장되지 않았습니다.
* **ACSD-49480** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 장바구니에 하나의 장바구니 가격 규칙만 적용되는 문제가 수정되었습니다.
* **ACSD-51230** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 주문에서 간단한 제품의 일부 환급이 처리될 때 기프트 카드 계정이 삭제되는 문제를 수정합니다.
* **ACSD-51238** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 문제를 수정합니다.
* **ACSD-50794** (Adobe Commerce >=2.4.1 &lt;2.4.7) - GraphQL을 통해 제거할 때 선물 메시지 또는 선물 포장 세부 사항이 데이터베이스에서 업데이트되지 않는 문제를 수정합니다.
* **ACSD-51528** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. *x_forwarded_for* 열에 null 값이 있습니다. *sales_order* 테이블.
* **ACSD-50849** (Adobe Commerce >=2.4.4 &lt;2.4.6) - 캐시를 지운 후 새 제품을 카테고리에 추가하면 기존 제품의 위치와 선택이 일치하지 않는 문제가 해결됩니다.
* **ACSD-51294** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - GTM/GA 가격, 수량, 세금, 배송 및 수익이 문자열로 전송되는 문제를 수정합니다. [!DNL Google Analytics] 및 GTM을 참조하십시오.
* **ACSD-51204** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 대변 메모를 작성한 후 완전히 판매된 제품이 재고로 돌아오지 않는 문제를 수정합니다.
* **ACSD-51291** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.4-p4의 경우) || >=2.4.5 &lt;2.4.5-p3) - 한 웹 사이트에 대한 액세스 권한이 있는 제한된 관리자가 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있는 문제를 해결했습니다.
* ACSD-50336용 새 버전이 추가되었습니다.
* ACSD-49970 패치를 교체했습니다.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - 실패한 지급을 제출한 후 Recaptcha v2가 다시 로드되지 않는 문제를 수정합니다.
* **ACSD-50817** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - Cron 작업 최적화 `sales_clean_quotes` 더 빨리 달리기 위해서
* **ACSD-49392** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - 번들 제품에 대한 부분 환불 후 주문 상태가 마감으로 변경되는 문제를 수정합니다.
* **ACSD-51036** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 동시 REST API 호출 중 경합 상태가 의 배송 상태 정보를 덮어쓰는 문제를 해결합니다. [!UICONTROL Items Ordered] 테이블.
* **ACSD-50858** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 배너 컨텐츠 로드 성능이 향상됩니다.
* MDVA-39305-v2, ACSD-45169용 새 버전이 추가되었습니다.
* 패치 ACSD-50260-v2를 업데이트했습니다.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (Adobe Commerce 및 Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3)의 경우 - 제품이 재입고되거나 가격이 변경될 때 제품 경고 이메일이 전송되지 않는 문제를 수정합니다.
* **ACSD-50367** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 값이 없는 다중 선택 고객 주소 속성을 만들 때 고객 주소 내보내기가 작동하지 않는 문제를 수정합니다.
* **ACSD-49877** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 모바일에서는 비디오 자동 재생이 작동하지 않는 문제를 수정합니다 [!DNL Safari] 비디오가 스트리밍 서비스가 아닌 원격 비디오 파일에 직접 연결된 경우.
* **ACSD-50165** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류를 수정합니다. *파일을 삭제할 수 없습니다. Warning!unlink: 해당 파일이나 디렉터리가 없습니다.* 관리자에서 JS/CSS 캐시를 플러시하는 경우.
* **ACSD-49737** (Adobe Commerce 및 Magento Open Source >=2.4.1-p1 &lt;2.4.7) - 카드 결제가 실패한 후 쿠폰이 사용된 것으로 잘못 표시되는 문제를 수정합니다.
* **ACSD-50814** (Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 관리 사용자가 대변 메모를 만들 수 없는 문제를 해결했습니다.
* **ACSD-50116** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 관리자 사용자가 하위 범주 레벨 3 이하에 대해 URL 다시 쓰기를 만들 수 없는 문제를 수정합니다.
* **ACSD-49513** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5) - 0바이트 파일로 인해 원격 스토리지 동기화가 실패하는 문제를 수정합니다.
* **ACSD-46683** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 배송 가격이 표시되는 문제를 수정합니다. *아직 계산되지 않음*.
* **ACSD-49129** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 다음과 같은 문제를 수정합니다. *[!UICONTROL content]* attribute(base64 이미지 코드)가 `rest/V1/products/sku/media` product media API 응답.
* **ACSD-50276** (Adobe Commerce >=2.4.0 &lt;2.4.7) - 다중 선택 고객 속성이 생성된 경우 고객 등록 양식이 상점 앞에서 작동하지 않는 문제를 수정합니다.
* **ACSD-50527** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 페이지를 빈 동적 블록으로 저장할 때 발생하는 오류를 수정합니다.
* **ACSD-49973** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - GraphQL을 통해 번들 제품을 가져오는 성능을 개선합니다.
* **ACSD-51114** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 비동기 인덱싱이 활성화되면 무작위 제품이 큰 카탈로그에서 사라지는 문제를 수정합니다. 대규모 카탈로그에 대한 비동기 리인덱싱의 성능을 향상시킵니다.
* **B2B-2598** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 캐시 기능을 [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], 및 [!UICONTROL storeConfig] GraphQL 쿼리
* MDVA-42806, ACSD-48627, ACSD-46815에 대한 새 버전이 추가되었습니다.
* ACSD-49773, ACSD-47179, ACSD-48300에 대한 패치 메타데이터가 업데이트되었습니다.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 주문이 픽업될 준비가 되지 않은 경우 API에서 픽업 준비 이메일이 전송되는 문제를 수정합니다.
* **ACSD-49822** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 의 업데이트 문제가 해결되었습니다. [!UICONTROL Requisition List] 페이지가 다음에 반영되지 않음 [!UICONTROL Print Requisition List].
* **ACSD-48771** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 이전 버전에서 열 블록 컨텐츠 유형을 업그레이드할 때 발생하는 문제를 해결합니다. [!DNL Page Builder] 버전.
* **ACSD-49464** (Adobe Commerce >=2.3.7 &lt;2.4.7) - orderId가 다른 경우 송장, 선적 및 대변 메모가 아카이브에서 다시 이동되지 않는 문제를 수정합니다.
* **ACSD-49773** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - AWS S3를 원격 스토리지로 사용할 때 제품 내보내기가 실패하는 문제를 수정합니다.
* **ACSD-49748** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 초대를 보낼 수 없는 문제를 수정합니다.
* **ACSD-49502** (Adobe Commerce >=2.4.3 &lt;2.4.7) - 스테이징 업데이트가 다운로드 가능한 제품에 적용된 후 다운로드 가능한 링크가 제대로 업데이트되지 않는 문제를 수정합니다.
* **ACSD-49527** (Adobe Commerce >=2.4.2 &lt;2.4.7) - GraphQL 회사 역할이 페이지 매김을 올바르게 표시하지 않는 문제를 해결합니다.
* **ACSD-49706** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 값을 선택하지 않으면 시각적 견본 속성에 대해 기본값이 저장되는 문제가 해결됩니다.
* **ACSD-49835** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 다중 선택 속성에 대해 저장소 수준에서 기본 확인란 값이 올바르게 저장되지 않는 문제를 해결합니다.
* **ACSD-49898** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 번들 제품에 1000을 초과하는 특별 가격이 있을 때 제품 그리드에서 예외가 발생하는 문제를 수정합니다.
* **ACSD-50234** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.5) - (으)로 주문하는 경우 확인 이메일에서 잘못된 고객 이름 관련 문제를 수정합니다. [!DNL PayPal].
* **ACSD-49960** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 고객 주문 그리드에 대해 날짜별 필터링이 작동하지 않는 문제를 수정합니다.
* **ACSD-49849** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 고객 이메일이 로 대체되는 문제가 해결되었습니다. [!DNL PayPal] (으)로 주문 시 이메일 보내기 [!DNL PayPal Express] GraphQL을 통해
* **ACSD-49839** (Adobe Commerce >=2.3.7 &lt;2.4.7) - SKU에서 제품에 작은 따옴표나 큰 따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에 오류가 발생하는 문제를 수정합니다.
* **ACSD-49970** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 다음의 경우에 발생하는 GraphQL 오류의 잘못된 처리가 수정되었습니다. [!DNL New Relic] 보고가 설정되어 있습니다.
* **ACSD-50260** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - GraphQL 제품 검색 결과가 10,000개의 결과로만 제한되는 문제를 해결합니다.
* **ACSD-48813** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 검색에서 속성의 검색 가중치에 따라 관련 결과를 표시하지 않는 문제를 수정합니다.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.3) - 예/아니요 속성에 따라 생성된 카탈로그 가격 규칙이 선택한 범위를 고려하지 않는 문제를 해결합니다.
* **ACSD-47704** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 번들 제품에 재고 제품의 가격만 표시되는 문제가 해결되었습니다.
* **ACSD-49370** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 다음과 같은 문제를 수정합니다. *날짜/시간* 제품 속성에 *필터 일치 유형 입력* GraphQL 스키마를 입력합니다.
* **ACSD-48807** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.7) - 고객 제품 검토가 GraphQL을 통해 상점 보기를 통해 필터링되지 않는 문제를 수정합니다.
* **ACSD-49433** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 미결제 금액이 있는 기프트 카드용 카트에서 기본 금액이 소계로 표시되는 문제가 수정되었습니다.
* **ACSD-48866** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 카테고리에 대한 RSS 피드를 요청할 때 오류가 발생하는 문제를 수정합니다.
* **ACSD-48784** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시되는 문제를 수정합니다.
* **ACSD-48857** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - Page Builder로 편집한 후 사용자가 변경 사항을 저장할 수 없는 문제를 수정합니다.
* **ACSD-49065** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 사용자 지정 주식에만 할당된 경우 관리자에 견적 항목이 표시되지 않는 문제를 수정합니다.
* **ACSD-49179** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 서로 다른 스토어에 대해 서로 다른 통화의 경우 주문 보고서에 잘못된 금액이 표시되는 문제가 수정되었습니다.
* **ACSD-49286** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 문제를 수정합니다.
* **ACSD-49574** (Adobe Commerce >=2.4.4 &lt;2.4.7) - GraphQL을 통해 장바구니에서 기프트 카드 제품 업데이트를 지원하는 기능을 추가합니다.
* 업데이트된 패치: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (Adobe Commerce >=2.4.1 &lt;2.4.7) - 협상 가능 견적을 사용하여 주문할 때 새 주소 대신 기본 배송 주소가 사용되는 문제를 수정합니다.
* **ACSD-48059** (Adobe Commerce >=2.3.7 &lt;2.4.7) - 판매자가 &quot;[!UICONTROL Match product by rule]카테고리에 있는 &quot;입니다.
* **ACSD-48216** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - 다음 문제를 해결합니다. [!UICONTROL AUTO_INCREMENT] / [!UICONTROL inventory_source_item] 다음에서 테이블 증가: [!UICONTROL UPDATE] 작업.
* **ACSD-47908** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - 체크아웃 중에 배송 단계에서 소스 및 수량을 선택할 때 &quot;0보다 작거나 같은 값이 예상됩니다.&quot; 오류가 수정되었습니다.
* **ACSD-49497** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 주문이 선적 후 처리 상태에 있고 부분 환불이 적용되는 문제가 해결되었습니다.
* **ACSD-48694** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - &quot;잘못된 상태 변경 요청됨&quot; 오류로 인해 고객이 주문을 할 수 없는 문제가 해결되었습니다.
* **ACSD-49013** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 벌크 API를 사용하여 고객을 만들 때 이메일 확인이 웹 사이트 로케일로 번역되지 않는 문제를 수정합니다.
* **ACSD-48164** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제한된 관리자가 웹 사이트 수준 값을 저장할 수 없는 문제를 수정합니다.
* **ACSD-48404** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4) - 브라우저의 뒤로 단추를 누를 때 &quot;카테고리 페이지 매김 = 예 저장&quot;으로 인해 오류가 발생하는 문제를 해결했습니다.
* **ACSD-48634** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - &quot;[!UICONTROL Google Analytics Content Experiments]&quot;은(는) 활성화되어 있습니다.
* **ACSD-49042** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 스토어프론트에서 무제한 주문 생산 제품을 주문할 수 없는 문제가 수정되었습니다.
* 업데이트된 패치: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (Adobe Commerce 및 Magento Open Source 2.4.4용) || >=2.4.5 &lt;2.4.6) - 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 항상 전송되지 않는 문제를 해결합니다.
* **ACSD-48661** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 회사의 신용 한도가 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 문제를 해결합니다.
* **ACSD-48773** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 보상 포인트 이메일 템플릿이 잘못된 저장소에서 이동되는 문제를 수정합니다.
* **ACSD-48587** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제품 위젯 일치 규칙의 특수 문자 HTML으로 인해 일치하는 제품을 표시할 수 없는 문제가 해결되었습니다.
* **ACSD-48212** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 제품 가져오기에서 제품을 잘못된 소스에 할당하는 문제를 수정합니다.
* **ACSD-47988** (Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 제품 내보내기가 페이지 빌더 제품 설명의 HTML 태그를 트리밍하는 문제를 수정합니다.
* **ACSD-48366** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 제품 이미지가 Stock으로 돌아가기 이메일 템플릿에 표시되지 않는 문제를 수정합니다.
* **ACSD-48417** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 제품에 대한 일정 변경을 작성하고 다른 제품을 저장한 후 SQL 오류가 표시되는 문제를 수정합니다.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 리색인이 작동하지 않는 문제를 수정합니다.
* **ACSD-48262** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - &quot;Allow All Products Per Page&quot; 설정이 Yes로 설정되어 있을 때 프론트엔드에 제품이 표시되지 않는 문제를 수정합니다.
* **ACSD-48293** (Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4) - 품절된 하위 제품이 재고로 반환될 때 합성 제품이 품절되는 문제를 수정합니다.
* **ACSD-47520** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 대변 메모가 생성될 때 고객이 보상 포인트를 잃는 문제를 수정합니다.
* **ACSD-48044** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4) - 여러 상품권을 다중 배송의 단일 주문에 적용하면 주문이 이루어지지 않는 문제가 해결됩니다.
* **ACSD-48300** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 구성 가능한 제품이 제거될 경우 반환을 만들 수 없는 문제를 수정합니다.
* **ACSD-47910** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 각 개체 그리드에서 주문, 송장, 선적 및 대변 메모가 누락되는 문제를 수정합니다.
* **ACSD-47292** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - &quot;품절 제품 표시&quot;가 예로 설정된 경우 GraphQL 응답에서 품절 번들 제품을 사용할 수 없는 문제를 수정합니다.
* **ACSD-48234** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - &quot;재고 부족 표시&quot; 옵션이 활성화된 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 문제를 해결합니다.
* **ACSD-48313** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5) - 속성 값에 쉼표가 포함되어 있는 경우 &quot;configurable_variations&quot; 열이 구문 분석되지 않는 문제를 수정합니다. &quot;additional_attributes&quot;에도 동일한 구문 분석 알고리즘이 사용됩니다.
* **ACSD-48627** (Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 장바구니 세부 정보를 가져오기 위해 GraphQL 요청을 보낼 때 품절 구성 가능한 제품 때문에 오류가 발생하는 문제를 수정합니다.
* 업데이트된 패치: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 이 있는 제품에 대해 SEO에 친숙한 URL이 생성되지 않는 문제가 수정되었습니다. *url_key* 속성이 스토어-뷰 수준에서 재정의되었습니다.
* **ACSD-46865** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 비동기 인덱싱이 활성화된 경우 배송 및 대변 메모 그리드가 채워지지 않는 문제를 수정합니다.
* **ACSD-47004** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - VAT ID가 없는 청구 주소에 VAT가 적용되지 않는 문제를 수정합니다.
* **ACSD-47803** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 품절 구성 가능한 제품 견본이 사용 가능한 것으로 표시되는 문제를 수정합니다.
* **ACSD-47137** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - pub/media 폴더가 매우 클 때 이미지 갤러리의 로드 속도를 개선합니다.
* **ACSD-46770** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 다음과 같은 경우에도 관리 주문 이메일이 전송되는 문제가 해결되었습니다. *이메일 주문 확인* 이(가) 선택되지 않았습니다.
* **ACSD-47955** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - GraphQL에 장바구니 할인이 올바르게 표시되지 않는 문제가 수정되었습니다.
* **ACSD-46617** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 다음과 같은 문제를 수정합니다. *체크아웃을 계속합니다* 부분합이 구성된 것보다 큰 경우에도 단추는 회색으로 표시됩니다. *최소 주문 금액*.
* **ACSD-47079** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 하위 제품 재고 상태가 REST API POST /rest/V1/inventory/source-items를 통해 변경될 때 복합 제품(번들, 그룹화 및 구성 가능) 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-47336** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 수정 사항 *문제가 발생했습니다.* commerce 관리자의 알림을 해제할 때 오류가 발생했습니다.
* **ACSD-47559** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 이메일 템플릿 미리 보기 영역이 완전히 표시되지 않는 문제를 수정합니다.
* **ACSD-47920** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 다음과 같은 경우에도 Rest API를 통해 게스트 사용자로 주문을 할 수 있는 문제를 수정합니다. *게스트 체크아웃 허용* 이(가) 꺼져 있습니다.
* 교체된 패치: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 특정 범위에 대한 액세스 권한이 제한된 관리자가 제품 검토를 삭제할 수 없는 문제를 수정합니다.
* **ACSD-47107** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5) - 카탈로그 가격 규칙 할인이 사용자 지정 제품 옵션에 적용되는 문제를 수정합니다.
* **ACSD-47232** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 총 가중치 조건이 있는 쿠폰을 관리자에서 적용할 수 없는 문제를 수정합니다.
* **ACSD-46519** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.6) - GraphQL categoryList 요청이 앵커 범주에 대한 잘못된 product_count를 반환하는 문제를 수정합니다.
* **ACSD-47027** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 느린 updateCompanyRole GraphQL 요청을 수정합니다.
* **ACSD-47666** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 관리자 > 시스템 > 권한 > 사용자 역할 > 역할 > 역할 사용자 그리드에서 필터 기능이 작동하지 않는 문제를 수정합니다.
* **ACSD-47497** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - [관리]의 [구성]에 [서비스] 탭이 표시되지 않는 문제가 해결되었습니다.
* 업데이트된 패치: ACSD-47743.
* 교체된 패치: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.3) - 수정 사항 _부울 유형의 값에서 배열 오프셋에 액세스하려고 합니다._ php 7.4에서 알려진 제품에 대해 존재하지 않는 특정 카테고리 경로에 액세스할 때 오류가 발생합니다.
* **ACSD-47332** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 00:00과 00:59 UTC 사이에서 실행할 때만 보고되는 오류와 함께 cron이 실패하는 문제를 수정합니다.
* **ACSD-47280** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 특정 범위에서 공유 카탈로그 기능 비활성화가 제대로 작동하지 않는 문제를 해결했습니다.
* **ACSD-47106** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 회사 만들기 페이지의 새 사용자 지정 특성에 값을 저장할 수 없는 문제를 수정합니다.
* 업데이트된 패치: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 많은 수의 제품 소스를 할당할 때 사용자에게 오류가 발생하는 문제를 수정합니다.
* **ACSD-46856** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 시스템 > 구성 > 가져오기 > 고급 가격을 통해 계층 가격 업데이트 성능을 개선합니다.
* **ACSD-46541** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4) - 주문 항목이 삭제될 경우 관리 사용자가 대변 메모를 만들 수 없는 문제를 수정합니다.
* **ACSD-46581** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 장바구니에서 국가를 선택한 후 예상 총 세액이 업데이트되지 않는 문제를 수정합니다.
* **ACSD-46618** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 로그인한 고객에 대해 제품 목록 위젯에 잘못된 캐시된 가격이 표시되는 문제를 수정합니다.
* **ACSD-46674** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 고객 이메일에서 이미지 유형의 사용자 지정 옵션이 HTML으로 표시되는 문제를 수정합니다.
* **ACSD-46988** (Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - GraphQL &#39;currency&#39; API 요청이 사용자 지정 통화에 대해 NULL 값을 반환하는 문제를 수정합니다.
* **ACSD-47076** (Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5) - 상점 첫 화면에서 Vimeo 비디오를 재생할 수 없는 문제를 수정합니다.
* **ACSD-45071** (Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4) - 가져오는 동안 제품에 기본 소스가 추가되는 문제를 수정합니다.
* **AC-** (Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - DHL 체계를 최신 버전 10.0으로 업데이트합니다.
* 업데이트된 패치: MDVA-42584.
* 교체된 패치: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5의 경우*) - 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 받는 문제를 수정합니다.
* **ACSD-46703** (*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6*) - 제품 편집 페이지에서 사용자 지정 옵션을 드래그하여 놓을 수 없는 문제를 수정합니다.
* **ACSD-44851** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6*) - 하위 범주가 있는 범주가 열거나 확장할 수 없는 문제를 수정합니다.
* **ACSD-46815** (*Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6*) - 카테고리 트리 요청이 20개의 카테고리로 제한되는 문제를 해결합니다.
* **ACSD-45675** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6*) - 제품 내보내기에서 카테고리 이름을 사용하는 문제를 해결했습니다. *기본 스토어 보기* 범위.
* **ACSD-46869** (*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6*) - 장바구니에서 구성 가능한 제품이 *PUT REST API* 제품 수량을 변경하지 않고 요청합니다.
* **MDVA-42768-V2** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 구성 가능한 제품에 일반 가격이 표시되는 문제를 해결했습니다. *0* 조건 *품절 표시* 은(는) *예*.
* 업데이트된 패치: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* 사용되지 않는 패치: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 카테고리 트리 요청이 20개의 카테고리로 제한되는 문제를 해결합니다.
* **ACSD-45781** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.2*) - 모바일에서 스토어 전면 검색 필드가 표시되지 않는 문제를 수정합니다.
* **ACSD-46192** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.6 &lt;2.4.5*) - 를 사용할 때 발생하는 문제를 해결합니다. `async/bulk/V1/configurable-products/bySku/options` 엔드포인트.
* **ACSD-46404** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.5*) - 2.4.4로 업그레이드한 후 관리자가 로그인할 수 없는 문제를 수정합니다.
* 업데이트된 패치: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 특정 스토어에 대한 GraphQL 제품 돌연변이가 요청된 스토어에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환하는 문제를 수정합니다.
* **ACSD-46146** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.6*) - 책임자로부터 주문을 받은 후 두 개의 주문 확인 이메일이 전송되는 문제를 수정합니다.
* **ACSD-45255** (*Adobe Commerce >=2.4.3 &lt;2.4.6*) - 제한된 관리자의 낮은 재고 보고서 페이지에서 예외를 수정합니다.
* **ACSD-45488** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6*) - 구성 가능한 여러 소스 제품이 자동으로 In Stock에 반환되지 않는 문제를 해결했습니다.
* **ACSD-45754** (*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.6*) - 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 수정합니다.
* **ACSD-45849** (*Adobe Commerce >=2.4.3 &lt;2.4.4*) - 스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실되는 문제를 수정합니다.
* **ACSD-45257** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.4*) - GraphQL에 장바구니 할인이 올바르게 표시되지 않는 문제가 수정되었습니다.
* **ACSD-44938** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4의 경우*) - 다음의 문제를 수정합니다. `VAT_ID` 게스트 사용자에 대한 GraphQL 요청에 적용할 수 없습니다.
* 업데이트된 패치: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.4*) - 대변 메모를 작성한 후 가상 제품에 대한 재고 수량이 잘못 계산되는 문제를 수정합니다.
* **ACSD-43887** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 회사 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다.
* **ACSD-45143** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5의 경우*) - 다음과 같은 문제가 해결되었습니다. `setShippingAddressesOnCart` 돌연변이가 숫자 영역 코드를 다음으로 설정할 수 없음 *지역*.
* **ACSD-44591** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.6*) - CAPTCHA 확인 없이 주문을 할 때 발생하는 오류를 수정합니다.
* **ACSD-45520** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.6*) - 사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 미리 선택되지 않는 문제를 수정합니다.
* **ACSD-45169** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.6*) - 다음의 문제를 수정합니다. [!DNL Visual Merchandiser] 는 스테이징 업데이트가 적용된 후 구성 가능한 제품에 대한 올바른 재고 및 가격을 표시하지 않습니다.
* **ACSD-45424** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.6*) - 부분 환불(대변 메모) 후 잘못된 예약 보상이 생성되는 문제를 수정합니다.
* **MDVA-42807** (*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.6*) - 상점 앞에 사용자 정의 통화 기호가 표시되지 않는 문제를 수정합니다.
* 업데이트된 패치: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 제한된 관리자에 대해 주문 보고서의 주문 합계가 잘못 계산되는 문제를 수정합니다.
* **MDVA-44940** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 관리에서 범주를 저장하는 동안 발생하는 SQL 오류를 수정합니다.
* **MDVA-44562** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.2-p2의 경우*) - GraphQL 요청이 기본이 아닌 스토어 보기에서 시작되었음에도 불구하고 견적 항목에 대한 기본이 아닌 스토어 ID가 기본 스토어 ID로 대체되는 문제를 수정합니다.
* **MDVA-43167** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 관리 사용자가 모든 주문을 선택할 때 관리 주문 그리드 일괄 작업이 다중 페이지에 적용되지 않는 문제를 수정합니다.
* **MDVA-44044** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.2-p2의 경우*) - 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 수정합니다.
* **MDVA-42509** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.4*) - 빠른 주문을 위해 CSV를 업로드할 수 없어 문제가 해결되었습니다. *쿠키를 보낼 수 없음* 오류.
* 업데이트된 패치: MDVA-41061, MDVA-42584.
* 새 접두사 [!DNL Quality Patches Tool] 패치 변경 예정 *MDVA* 끝 *ACSD* 내부 프로세스 변경 때문에.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 항목의 최소 수량이 장바구니에 이미 있는 경우 추가 항목을 장바구니에 추가할 수 없는 문제를 수정합니다.
* **MDVA-44887** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.4 &lt;2.4.5*) - 수정 사항 *확인할 수 없는 구문 오류: 예기치 않은 토큰 &quot;const&quot;* 관리자 패널에서 오류가 발생했습니다.
* **MDVA-43718** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 수정 사항 *소비자가 %resources에 액세스할 수 있는 권한이 없습니다.* 사용자 지정 통합에서 공유 카탈로그에 액세스할 때 표시되는 오류입니다.
* **MDVA-44660** (*Adobe Commerce 및 Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - 그레이브 액센트 문자 문제 해결 ``` ` ``` 고객의 이름과 성에 사용할 수 없습니다.
* **MDVA-40896** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 수정 사항 *오류: TypeError: 인수 3이 Magento에 전달되었습니다.* 비동기 제품 벌크 API에 오류가 발생했습니다.
* **MDVA-38559** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.3*) - 수정 사항 */V1/customers/search API* 둘 이상의 구독이 있는 고객에 대한 오류입니다.
* **MDVA-44533** (*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.4*) - 번들 하위 제품에 할인이 잘못 적용되는 문제가 수정되었습니다.
* 업데이트된 패치: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 제품에서 발생하는 문제를 해결합니다. *개별적으로 보이지 않음* 여전히 카탈로그 고급 검색 결과에 나타납니다.
* **MDVA-44100** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 모든 FPT가 장바구니의 마지막 제품에 할당되고 다른 제품에 대해 재설정되는 문제를 수정합니다.
* **MDVA-43605** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.5*) - Rest API를 사용할 때 주문 데이터가 행 합계에 대해 음수 값을 반환하는 문제를 수정합니다.
* **MDVA-43102** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.1 &lt;2.4.5*) - REST API를 통해 환불이 완료되면 판매 가능 수량이 올바르게 업데이트되지 않는 문제를 수정합니다.
* **MDVA-43178** (*Adobe Commerce 및 Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - GraphQL에서 사용자 지정 스토어에 대한 고객 토큰을 검색할 수 없는 문제를 수정합니다.
* **MDVA-43859** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 오류가 발생하는 문제를 수정합니다 *customerId = 인 해당 엔티티 없음* 은 삭제된 고객이 로그인을 시도할 때 기록됩니다.
* **MDVA-44147** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - GraphQL 요청이 구매요청 목록을 반환하지 않는 문제를 수정합니다.
* **MDVA-44505** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - GraphQL 보상 포인트 적용이 총계를 업데이트하지 않으며 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 수정합니다.
* 업데이트된 패치: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - 고객 세그먼트가 로 설정된 경우에만 관련 제품 규칙이 작동하는 문제를 수정합니다. *모두*.
* **MDVA-39605** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있는 문제를 해결합니다.
* **MDVA-43862** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.5*) - GraphQL으로 인해 고객이 장바구니 항목을 업데이트할 수 없는 문제가 해결되었습니다. *UpdateCartItems 돌연변이* 오류.
* **MDVA-43824** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p3의 경우 || >=2.4.1 &lt;2.4.5*) - 할인이 적용된 주문 취소 시 오류가 표시되는 문제를 수정합니다.
* **MDVA-43451** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 오류가 발생하는 문제를 수정합니다 *요청한 스토어를 찾을 수 없습니다. 스토어를 확인하고 다시 시도하십시오.* 특정 웹 사이트에 대한 공유 카탈로그를 구성하는 동안 표시됩니다.
* **MDVA-43491** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.5*) - 다중 스토어 웹 사이트용 제품을 가져올 때 기본 이미지 레이블이 업데이트되지 않는 문제를 수정합니다.
* **MDVA-43601** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 전체 색인 재지정 후 트리거가 누락되는 문제를 수정합니다.
* **MDVA-42046** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2의 경우 || >=2.4.0 &lt;2.4.5*) - 제품을 업데이트하는 동안 날짜 입력 필드가 있는 제품 속성에 잘못된 값이 지정되는 문제를 수정합니다.
* **MDVA-43935** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 업셀 제품이 두 번 표시되는 문제를 수정합니다.
* **MDVA-44188** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 시스템에서 발급한 이메일이 다음과 같은 문제를 수정합니다. `.-` 주소에서 전송되지 않습니다.
* **MDVA-42283** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 프랑스어 로케일에 대한 관리 순서 격자의 날짜-시간 형식이 잘못된 문제를 수정합니다.
* 업데이트된 패치: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* 다음에 대한 패치 메타데이터 추가됨 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.3.6*) - 사용자가 활성 예약 업데이트의 시작 시간을 편집할 수 있는 문제를 수정합니다.
* **MDVA-42410** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 쿠폰 보고서에 기본 기본 통화만 표시되는 문제를 수정합니다.
* **MDVA-41136** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 의 만료일이 인 문제를 수정합니다. `mage-cache-sessid` 가 확장되지 않으므로 고객 데이터가 정리됩니다.
* **MDVA-39993** (*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;=2.3.7-p2의 경우 || >=2.4.0 &lt;2.4.4*) - API를 통해 수행된 인벤토리 변경이 프론트엔드의 제품 페이지에 반영되지 않는 문제를 수정합니다.
* **MDVA-42855** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 체크아웃 중에 새 고객 주소가 주소록에 저장되지 않는 문제를 해결합니다.
* **MDVA-42645** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 스토어 크레딧 기능이 비활성화된 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결했습니다.
* **MDVA-43414** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2의 경우*) - 를 실행할 때 발생하는 PHP 치명적인 오류를 수정합니다. `inventory.reservations.updateSalabilityStatus` 숫자 SKU에 대한 대기열 소비자.
* **MDVA-41628** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5의 경우*) - 새로운 모듈이 추가될 때 기존 제한된 관리 사용자가 새 리소스에 액세스할 수 있는 문제를 해결합니다.
* **MDVA-43348** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 기프트 카드 GraphQL 요청에 오류가 표시되는 다음과 같은 문제를 수정합니다. `gift_card_options` contain *uid*.
* **MDVA-39546** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 편집 중에 스테이징 업데이트 시작 날짜를 현재 날짜보다 이전 날짜로 설정할 수 있는 문제를 수정합니다.
* **MDVA-42950** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 제품 페이지에서 비디오가 재생되지 않는 문제를 수정합니다.
* **MDVA-42689** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - Adobe Commerce에서 오류가 발생하는 문제를 수정합니다. *무결성 제한 위반* 가져오는 동안 제품 카테고리를 업데이트하는 중 오류가 발생했습니다.
* **MDVA-41229** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 구성 가능한 제품을 가져온 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않는 문제를 수정합니다.
* **MDVA-43731** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 다음의 문제를 수정합니다. *동의어 검색* 에 값이 추가되면 더 이상 작동하지 않습니다. *일치시킬 최소 용어*.
* **MDVA-43232** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - 에서 제품을 정렬하는 문제가 해결되었습니다. [!DNL Visual Merchandiser] 하단/상단에 특별 가격별 범주를 저장하는 동안 오류가 발생합니다.
* **MDVA-43726** (*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.3*) - 부분 색인 재지정 후 스토어 수준 속성 일치를 기반으로 하는 카탈로그 가격 규칙이 적용되지 않는 문제를 수정합니다.
* 업데이트된 패치: MDVA-36464, MDVA-37478, MDVA-38608.
* 다음에 대한 패치 메타데이터 추가됨 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - REST API를 통해 특정 웹 사이트에 대해 제품 가격 속성을 업데이트할 수 없는 문제를 수정합니다.
* **MDVA-41350** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 제한된 액세스 권한을 가진 관리자가 SKU로 역할 범위를 벗어난 제품을 주문에 추가하면 예외가 throw되는 문제를 수정합니다.
* **MDVA-42269** (*Adobe Commerce 및 Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - 다음과 같은 이유로 관리자가 관리자에 로그인할 수 없는 문제가 해결됩니다. *TypeError: strtotime()에서는 매개 변수 1이 문자열이어야 하고 null이 주어져야 합니다.* 오류.
* **MDVA-40830** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 수정합니다.
* **MDVA-42237** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - 하위 제품 가격이 변경된 후 구성 가능한 제품 특별 가격이 업데이트되지 않는 문제를 해결합니다.
* **MDVA-42520** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 다음과 같은 경우 세율이 두 번 적용되는 문제를 수정합니다. *국경 간 무역 사용* 를 사용합니다.
* 업데이트된 패치: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* 사용되지 않는 패치: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.2 &lt;2.4.5*) - 대량 속성 업데이트가 변경 후에만 기본 저장소에 대한 URL 재작성을 만드는 문제를 수정합니다 *제품 가시성*.
* **MDVA-43091** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 백엔드의 관리자에서 번들 제품을 주문하면 오류가 발생하는 문제를 수정합니다 *이 제품에 소수점 수량을 사용할 수 없습니다.*.
* **MDVA-40816** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - 관련 제품 규칙이 규칙 조건에 정의되지 않은 범주의 제품을 표시하는 문제를 수정합니다.
* **MDVA-41305** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.5*) - GraphQL 돌연변이가 위시리스트에 추가한 후 구성 가능한 제품 옵션을 반환하지 않는 문제를 수정합니다.
* **MDVA-39181** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 관련 제품 규칙이 규칙 조건에 정의되지 않은 범주의 제품을 표시하는 문제를 수정합니다.
* **MDVA-42584** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 가져오기 또는 API를 통해 수량 및 재고 상태를 변경한 후 백엔드의 구성 가능한 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **MDVA-40175** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.3*) - 다음의 문제를 수정합니다. *배송 방법을 변경하려면 클릭* 재주문 중에 관리자에서 배송 방법을 선택하는 라디오 버튼이 표시되지 않습니다.
* **MDVA-42768** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.5*) - 구성 가능한 제품에 다음과 같은 경우 정가가 0으로 표시되는 문제가 해결되었습니다. *품절 표시* 예.
* **MDVA-43201** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 특정 로케일에 DOB 속성을 사용할 때 고객 로그인에 오류가 발생하는 문제를 수정합니다.
* 업데이트된 패치: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5의 경우*) - Adobe Commerce 시간대가 로컬 환경 시간대와 다를 때 날짜 필터가 제대로 작동하지 않는 문제를 수정합니다.
* **MDVA-42657** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 관리자 사용자가 고객 세그먼트 조건에서 범주를 선택할 수 없는 문제를 수정합니다.
* **MDVA-42806** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 의 문제를 해결합니다. *새 회사 등록* 기존 회사가 REST API를 통해 업데이트될 때마다 이메일이 전송됩니다.
* **MDVA-37984** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 다음과 같은 문제가 해결되었습니다. [!DNL Visual Merchandiser] *규칙별 제품 일치* 기능이 스테이징 업데이트가 있는 제품을 올바르게 필터링하지 않습니다.
* **MDVA-40488** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 기본 제공 하위 제품이 있는 구성 가능한 제품이 올바른 가격 범위에 표시되지 않는 문제를 해결했습니다.
* **MDVA-42507** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되는 문제를 수정합니다.
* **MDVA-39163** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.5*) - 새 사용자가 등록되고 장바구니의 제품이 게스트 세션에서 나왔을 때 배송 방법을 사용할 수 없는 문제를 수정합니다.
* **MDVA-38626** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.3 &lt;2.4.5*) - 관리 사용자가 를 사용하여 백엔드에 주문할 수 없는 문제를 해결합니다. [!DNL PayPal Payflow Pro] 결제.
* **MDVA-38666** (*Adobe Commerce 및 Magento Open Source >=2.3.2 &lt;2.3.6*) - 관리 사용자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결했습니다.
* **MDVA-38526** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 관리 사용자가 다음에 액세스할 수 없는 문제를 수정합니다. [!DNL Site-Wide Analysis tool].
* 업데이트된 패치: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 를 설정한 후 사용자가 500 오류를 가져오는 문제를 해결합니다. *이미지 메시지* 쿠키가 이미 있지만 새 메시지가 없는 경우 쿠키입니다.
* **MDVA-41139** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 구성 가능한 제품의 소스 중 하나에 대해 간단한 제품의 qty=0일 때 제품을 가져온 후 제품이 품절되는 문제를 수정합니다.
* **MDVA-42326** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2의 경우 || >=2.4.1 &lt;2.4.4*) - 영구적 장바구니가 활성화된 경우에도 세션 시간이 초과되면 고객이 체크아웃 시 오류를 발생하는 문제를 수정합니다.
* **MDVA-42341** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 다음과 같은 문제가 해결되었습니다. `categoryList` 요청에 스토어 헤더가 있는 경우 GraphQL 쿼리가 결과를 필터링하지 않습니다.
* **MDVA-38393** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 단순 제품의 이름이 변경된 경우 구성 가능한 제품에 대한 카탈로그 규칙이 작동하지 않는 문제를 해결했습니다.
* **MDVA-39153** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 관리자에서 재주문 중에 할인 금액이 잘못 계산되는 문제가 해결되었습니다.
* 업데이트된 패치: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.0 &lt;2.4.3*) - 관리 사용자가 웹 사이트를 삭제한 후 고객의 그리드에 액세스할 수 없는 문제를 수정합니다.
* **MDVA-40311** (*Adobe Commerce 및 Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - 관리 사용자가 오류 메시지를 받는 문제를 수정합니다 *보안 또는 양식 키가 잘못되었습니다. 페이지를 새로 고치십시오.* 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후.
* **MDVA-41631** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 사용자가 선택 사항 없이 주문 정보를 검색하려고 할 때 오류가 발생하는 문제를 수정합니다 *전화* GraphQL을 통한 가치.
* **MDVA-27239** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.3.6*) - 크로스셀 제품이 표시되지 않는 문제를 수정합니다.
* 업데이트된 패치: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.4*) - 리인덱싱하는 동안 프론트엔드에 제품이 누락된 문제를 수정합니다.
* **MDVA-40120** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - DESC/ASC별 GraphQL 정렬이 동일한 관련성 또는 가격을 갖는 제품에서 작동하지 않는 문제를 수정합니다.
* **MDVA-41399** (*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.2*) - 관리 사용자가 다음에 액세스할 수 없는 문제를 수정합니다. *장바구니 관리* 고객이 위시리스트에 제품을 추가하는 경우 페이지를 표시합니다.
* **MDVA-40609** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 비활성화된 제품 데이터가 `cataloginventory_stock_status` 색인 테이블, 부정확한 사용 불능 제품 수량 표시.
* **MDVA-39031** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 대상 웹 사이트에 할당되지 않은 경우에도 GraphQL을 통해 장바구니에 제품을 추가할 수 있는 문제를 수정합니다.
* **MDVA-41597** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - GraphQL을 사용하여 구성 가능한 제품을 장바구니에 둘 이상 추가할 때 사용자에게 오류가 발생하는 문제를 수정합니다.
* **MDVA-27456** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.3.7*) - 사용자가 로드하려고 할 때 오류가 발생하는 문제를 수정합니다 [!DNL Swagger].
* **MDVA-32776** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.0 &lt;2.4.2*) - 주문이 되었으나 배송되지 않은 경우 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **MDVA-30862** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.0*) - 인쇄된 PDF 송장의 주문 날짜가 잘못된 문제를 수정합니다.
* 의 색인 페이지가 개선되었습니다. [!DNL Quality Patch Tool]. 에 대한 편리한 검색 및 필터링 추가 [!DNL quality patches] 최신 버전의 도구에서 사용할 수 있습니다.
* 업데이트된 패치: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 종료 날짜를 이전에 제거한 경우 제품에 대해 새 업데이트를 만들거나 기존 예약된 업데이트를 편집할 수 없는 문제가 수정되었습니다.
* **MDVA-41046** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 사용자 지정 옵션이 있는 간단한 제품을 구성 가능한/그룹화된 제품에 할당할 수 있는 문제를 해결했습니다.
* **MDVA-40545** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 동일한 페이지에 대한 노드가 두 개 이상 있어도 페이지의 첫 번째 노드만 검색되던 문제를 수정합니다.
* **MDVA-41164** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.4.2 &lt;2.4.3-p1*) - 관리자가 파일 또는 이미지 유형 사용자 정의 고객 속성으로 회사를 저장하거나 편집할 수 없는 문제가 수정되었습니다.
* **MDVA-39229** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 카탈로그 규칙 스테이징 업데이트 시작 시간을 업데이트한 후 다음 오류가 표시되는 문제를 수정합니다. *Cron 작업 staging_synchronize_entities_period에 오류가 있습니다. 활성 업데이트를 삭제할 수 없습니다.*
* **MDVA-40619** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - CMS 페이지에서 인라인 편집을 하려고 할 때 CMS 페이지 계층 구조를 변경하면 500 오류가 발생하는 문제를 수정합니다.
* **MDVA-41061** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 관리자로부터 제품을 저장할 때 재고 상태가 판매 가능으로 재설정되는 문제를 수정합니다.
* **MDVA-31763** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 수동 색인 재지정 전까지 카탈로그 가격 규칙이 되돌아가거나 적용되지 않는 문제를 수정합니다.
* **MDVA-37748** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - GraphQL 쿼리가 공유 카탈로그에 할당되지 않은 제품을 반환하는 문제를 수정합니다.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - REST API를 통해 동일한 주문에 대한 부분 송장을 동시에 생성할 수 없는 문제를 수정합니다.
* **MDVA-40101** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.2 &lt;2.4.0*) - 성공적인 주문 배치 후 미니 카트에서 품목이 제거되지 않는 문제를 수정했습니다. [!DNL PayPal Express] 체크아웃.
* **MDVA-40401** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2의 경우 || >=2.4.1 &lt;2.4.4*) - 주문이 실패하는 경우에도 쿠폰 사용 값이 변경되는 문제를 수정합니다.
* **MDVA-40537** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.4.0-p1의 경우*) - 동일한 URL 키를 가진 여러 CMS 페이지가 있는 경우 스토어 보기를 만들 때 사용자가 오류가 발생하는 문제를 수정합니다.
* **MDVA-37725** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.4.3-p1의 경우*) - 기본이 아닌 웹 사이트에서 보낸 비동기 주문 이메일에 기본 웹 사이트의 로고 URL이 포함되는 문제를 수정합니다.
* **MDVA-39482** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2의 경우 || >=2.4.1 &lt;2.4.4*) - 미납주문을 활성화한 경우 수량을 &quot;0&quot;으로 하여 제품을 가져올 경우 재고가 소진되는 문제를 수정합니다.
* **MDVA-40435** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.4 &lt;2.4.4*) - GraphQL을 통해 적용할 때 동적 가격이 적용된 번들 제품에 대한 잘못된 할인이 적용되는 문제를 수정합니다.
* **MC-42528** (*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;=2.4.3-p1의 경우*) - 다음과 같은 문제가 해결되었습니다. `categoryList` GraphQL 쿼리는 할당된 범주와 할당되지 않은 범주를 모두 반환합니다.
* **MDVA-29400** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.7-p1의 경우 || >=2.4.0 &lt;=2.4.0-p1*) - 중복 주문의 문제가 해결되었습니다. [!DNL PayPal Express Checkout].
* **MDVA-26005** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2의 경우*) - 장바구니 가격 규칙 조건에 대한 범주 트리에서 범주를 선택할 수 없는 문제를 수정합니다.
* **MDVA-25631** (*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;=2.3.5-p2의 경우*) - 다수의 고객이 포함된 고객 세그먼트를 편집하고 저장할 수 있도록 성능이 향상됩니다.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - GraphQL 검색 쿼리가 관리자의 인기 검색어에 표시되지 않는 문제를 수정합니다.
* **MDVA-40601** (*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;=2.4.2-p2의 경우*) - 사용자가 GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 정보를 가져오려고 할 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-37234** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - 동일한 SKU에 대해 장바구니에 항목을 여러 번 추가(병렬 요청)하면 동일한 장바구니 ID에 대해 중복 라인 항목이 생성되는 문제를 수정합니다.
* **MDVA-33606** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;=2.4.2-p2의 경우*) - 사용자가 *고유 제한 사항 위반* 계층에 할당된 CMS 페이지를 저장할 때 오류가 발생했습니다.
* **MDVA-31590** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.1-p1의 경우*) - 사용자가 MySQL 비동기 큐를 사용하여 속성을 일괄적으로 업데이트할 수 없는 문제를 수정합니다.
* **MDVA-36309** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2의 경우*) - 관리 그리드에서 특성별 제품 검색이 느려지는 문제를 해결했습니다.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 주문이 스토어 크레딧에서 지급될 때 FPT가 있는 송장에 잘못된 총계가 표시되는 문제를 수정합니다.
* **MDVA-37364** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.3의 경우*) - 날짜 유형의 사용자 지정 고객 속성이 고객의 그리드 UI를 손상하는 문제를 수정합니다.
* **MDVA-39195** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2의 경우*) - 다음의 문제를 수정합니다. *장바구니에 추가* 장바구니로 리디렉션이 활성화될 때 카테고리 페이지에서 버튼이 비활성화되었습니다.
* **MDVA-37115** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2의 경우*) - 가 불필요한 문제를 해결합니다. *0개만 남음* 알림은 구성 가능한 제품 페이지에 표시됩니다.
* **MDVA-39521** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4의 경우*) - 사용자가 GraphQL을 통해 빈 전화 번호로 장바구니에 배송 주소를 설정할 수 없는 문제를 해결합니다.
* **MDVA-39384** (*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;=2.3.6의 경우 || >=2.4.1 &lt;=2.4.3*) - 회사 사용자에 대한 사용자 지정 고객 속성이 저장되지 않는 문제를 수정합니다.
* **MDVA-39043** (*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.4.3의 경우*) - 액세스를 제한한 관리자 사용자가 을(를) 추가하려고 할 때 오류가 발생하는 문제를 수정합니다. *제품* 위젯을 CMS 페이지에 추가합니다.
* **MDVA-39966** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.5-p2의 경우 || >=2.4.0 &lt;=2.4.0-p1*) - 잘못된 로케일 배포 문제를 수정합니다.
* **MDVA-38852** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.5-p2의 경우*) - 여러 병렬 주문의 경우 성능을 크게 저하시키는 업데이트에 대해 디자인별 카탈로그 인벤토리가 테이블을 잠그는 문제를 수정합니다.
* **MDVA-39986** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - 사용자가 Safari 브라우저를 사용하여 MacOS의 관리자에서 주문을 할 수 없는 문제를 수정합니다.
* **MDVA-38447** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 다음의 두 가지 문제를 해결했습니다. *개별적으로 표시되지 않음* 구성 가능한 하위 제품이 GraphQL 응답에서 반환되고 카테고리 필터를 사용하여 GraphQL 제품에 대한 MySQL 쿼리를 최적화합니다.
* **MDVA-40134** (*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 공유 카탈로그가 활성화되면 GraphQL에서 관련 제품을 반환하지 않는 문제를 수정합니다.
* **MDVA-39935** (*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - GraphQL에서 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 수정합니다.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4의 경우*) - 다음과 같은 문제가 해결되었습니다. *멤버 함수 getId() 호출* 관리자의 주문 세부 사항 페이지에 오류가 표시됩니다.
* **MDVA-34948** (*Adobe Commerce 및 Magento Open Source의 경우 >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - 다음과 같이 오래 실행되는 쿼리의 문제를 수정합니다. `GET_LOCK`.
* **MDVA-39305** (*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.2-p1의 경우*) - 등록된 고객이 활성화된 Google ReCaptcha로 로그인할 수 없는 문제가 수정되었습니다.
* **MDVA-37897** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4의 경우*) - 고객이 최근에 본 위젯의 옵션을 사용하여 제품을 추가하려고 할 때 잘못된 리디렉션 문제가 수정됩니다.

## v1.1.0 {#v1-1-0}

* 고객이 사용자 경험을 개선하고 필요한 패치를 쉽게 검색할 수 있도록 패치 카테고리가 도입됐다.
* 다음 `patches.json` 파일 이름이 (으)로 변경되었습니다. `support-patches.json`.
* **MDVA-38799** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않은 문제를 해결했습니다.
* **MDVA-37592** (*Adobe Commerce의 경우 >=2.3.6 &lt;=2.4.2-p1*) - 가격이 0인 제품이 공유 카탈로그에 할당된 경우 가격별 정렬이 제대로 작동하지 않는 문제를 수정합니다.
* **MDVA-38827** (*Adobe Commerce의 경우 >=2.3.3-p1 &lt;2.4.4*) - 고객이 오류 메시지가 포함된 주문 배송 이메일을 받는 문제를 수정합니다.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*Adobe Commerce의 경우 >=2.3.2 &lt;=2.3.5-p2*) - CMS 페이지를 저장할 때 발생하는 오류를 수정합니다. *PAGE_ID ID가 동일한 항목이 이미 있습니다.*.
* **MDVA-34680** (*Adobe Commerce의 경우 >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - 고객 계정 생성 시간이 고객 그리드에서 올바르게 필터링되지 않는 문제를 수정합니다.
* **MDVA-37068** (*Adobe Commerce의 경우 >=2.3.1 &lt;2.4.4*) - 장바구니에 가상 제품만 있을 때 잘못된 세율이 표시되는 문제를 수정합니다.
* **MDVA-38608** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 색인 재지정이 성공적으로 완료되지 않은 경우 임시 테이블이 삭제되지 않는 문제를 수정합니다.
* **MDVA-38308** (*Adobe Commerce의 경우 >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - 추가와 관련된 문제를 수정합니다. [!DNL Vimeo] 비디오에서 제품까지.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*Adobe Commerce의 경우 >=2.3.6 &lt;2.4.3*) - 를 사용할 때 고객이 결제 확인 페이지로 이동하지 않는 문제를 수정합니다. [!DNL Paypal Payment Advanced] 메서드를 사용합니다.
* **MDVA-37082** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 그룹화된 제품의 사용자 정의 스톡을 저장할 때 제품이 프론트엔드에 품절되는 문제를 수정합니다.
* **MDVA-36572** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.4.3*) - 대변 메모 업데이트로 인해 더 이상 데이터베이스에서 중복 제품 예약 업데이트가 발생하지 않는 문제를 수정합니다.
* **MDVA-38132** (*Adobe Commerce >=2.3.3 &lt;2.4.3*) - 다음 이유로 인해 관리자 패널에 연결할 수 없는 문제를 수정합니다. *리디렉션이 너무 많음* 오류.
* **MDVA-38270** (*Adobe Commerce의 경우 >=2.4.1 &lt;2.4.3*) - GraphQL의 주문 합계에서 기프트 카드 정보가 누락되는 문제를 수정합니다.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*Adobe Commerce의 경우 >=2.4.2 &lt;=2.4.4*) - 웹 사이트 ID가 스토어 ID와 일치하지 않을 때 GraphQL을 통해 구성 가능한 제품을 장바구니에 추가하는 문제를 해결합니다.
* **MDVA-36832** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.4.2-p1*) - 보기 너비가 768px일 때 페이지에서 이미지가 중복되는 문제를 수정합니다.
* **MDVA-37874** (*Adobe Commerce의 경우 >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - 다음의 문제를 수정합니다. *전체 장바구니에 대한 고정 할인 금액* 둘 이상의 옵션이 포함된 번들 제품에 가 잘못 적용됩니다.
* **MDVA-37913** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.4.0-p1*) - 다운로드 가능한 제품이 API를 통해 업데이트되는 경우 다운로드 가능한 링크가 사라지는 문제를 수정합니다.
* **MDVA-34330** (*Adobe Commerce의 경우 >=2.3.1 &lt;=2.4.2-p1*) - 주문 그리드의 주문이 관리 시간대에 따라 필터링되지 않는 문제를 수정합니다.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.3.7*) - Adobe Commerce에서 로 주문된 주문에 대한 부분 송장을 만들 때 오류가 발생하는 문제를 수정합니다. *계정입금* rest API를 통한 결제 방법.
* **MDVA-37362** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.4.2-p1*) - GraphQL 응답에서 구성 가능한 제품 옵션 값과 변형 속성 값이 비어 있는 문제를 수정합니다.
* **MDVA-37288** (*Adobe Commerce 2.4.2용*) - GraphQL 요청 후 잘못된 계층 가격이 반환되던 문제를 수정합니다.
* **MDVA-37225** (*Adobe Commerce의 경우 >=2.4.1 &lt;=2.4.2-p1*) - 가져온 SKU에 정수 값이 있을 때 빠른 주문 생성 중에 업로드 프로세스가 중단되는 문제를 수정합니다.
* **MDVA-37224** (*Adobe Commerce의 경우 >=2.3.3 &lt;=2.4.2-p1*) - 고객이 협상 가능 견적에 대해 지불할 수 없는 문제를 수정합니다. [!DNL PayFlow Pro] 장바구니에 다른 제품이 있는 경우.
* **MDVA-36286** (*Adobe Commerce의 경우 >=2.3.6 &lt;=2.4.2-p1*) - 동일한 SKU에 하위 범주의 다른 위치가 있는 경우 페이지 빌더 제품 위젯 미리 보기가 중단되는 문제를 수정합니다.
* **MDVA-30186** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - GraphQL 응답에서 속성 항목 수 대신 옵션 값별로 속성 옵션이 정렬되는 문제를 수정합니다.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.4.2*) - API를 통해 변경된 후 이전 사용자 지정 옵션이 남아 있는 문제를 수정합니다.
* **MDVA-35773** (*Adobe Commerce의 경우 >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - 100% 할인이 적용된 주문에 대한 송장에서 총계가 0으로 표시되지 않는 문제를 수정합니다.
* **MDVA-36833** (*Adobe Commerce 2.4.2용*) - 공유 카탈로그에서 일부 제품을 제외한 후 페이지당 제품 수를 임의로 표시하는 검색 결과 관련 문제를 수정합니다.
* **MDVA-37182** (*Adobe Commerce의 경우 >=2.4.1 &lt;=2.4.2*) - 둘 다에서 잘못된 검색 결과를 가져오는 문제를 수정합니다 [!DNL Elasticsearch] 버전 6 및 버전 7.
* **MDVA-36253** (*Adobe Commerce의 경우 >=2.4.0 &lt;=2.4.1-p1*) - 항목 삭제 후 미니 장바구니에 잘못된 부분합이 표시되는 문제를 수정합니다.
* **MDVA-36853** (*Adobe Commerce 2.4.2용*) - 대형 미디어 갤러리를 로드할 때 이미지가 표시되지 않는 문제가 해결되었습니다.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.3.4-p2*) - 범주 페이지에 번들 제품이 없는 문제가 해결되었습니다.
* **MDVA-36615** (*Adobe Commerce 2.4.2용*) - 관리 제품 그리드에서 잘못된 제품 카운트가 발생하는 문제를 수정합니다.
* **MDVA-36464** (*Adobe Commerce의 경우 >=2.4.0 &lt;=2.4.2*) - 이메일 알림 구성이 저장소 보기 수준에서 작동하지 않는 문제를 수정합니다.
* **MDVA-36138** (*Adobe Commerce ^2.3.2용*) - 장바구니에 있는 모든 품목이 무료 배송 카트 규칙에 해당되지 않는 경우 배송 가격이 조정되지 않고 전체 배송 가격이 고객에게 표시되는 문제를 수정합니다.
* **MDVA-36424** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - 백엔드 기본 URL이 상점 기본 URL과 다른 경우, 콘텐츠가 반복적으로 편집될 때 페이지 빌더 요소에 첨부된 미디어 이미지가 사라지는 문제가 수정되었습니다.
* **MDVA-35984** (*Adobe Commerce ^2.4.0용*) - 동일한 제품에 대해 여러 개의 동시 납품을 생성한 후 잘못된 제품 수량 및 판매 가능 수량이 있는 문제를 수정합니다.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - 카테고리 캐시 태그를 사용하여 GraphQL 쿼리가 캐싱하지 않는 문제를 수정합니다.
* **MDVA-33168** (*Adobe Commerce >=2.3.3 &lt;2.4.2*) - API를 통해 제품 속성을 업데이트할 때 다른 모든 속성이 빈 값으로 변경되는 문제를 수정합니다.
* **MDVA-19640** (*Adobe Commerce의 경우 >=2.3.0*) - 다음의 문제를 수정합니다. [!DNL Advanced Reporting] 은(는) 데이터를 표시하지 않습니다.
* **MDVA-11189** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.5*) - CSV 파일을 가져와서 제품 재고, 의 행을 업데이트할 때 발생하는 문제를 수정합니다. `cataloginventory_stock` 테이블이 삭제됩니다.
* **MDVA-26639** (*Adobe Commerce의 경우 >=2.3.3-p1 &lt;2.3.6*) - 새 주문 확인 이메일 템플릿이 만들어지면 주문 메일에 주문 항목이 누락되는 문제를 수정합니다.
* **MDVA-15546** (*Adobe Commerce의 경우 >=2.3.0*) - 주문을 만든 후 의 문제를 해결합니다. *열 entity_id where 절이 모호합니다.* 예외 로그에 오류가 표시됩니다.
* **MDVA-21095** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.5*) - 쿼리할 때 문제를 수정합니다 `INSERT INTO search_tmp` 대량 속성 값을 업데이트한 후에는 종료되지 않습니다.
* **MDVA-23845** (*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - JavaScript 축소가 활성화된 후 이메일 템플릿을 미리 볼 수 없는 문제를 수정합니다.
* **MDVA-22026** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.4*) - 외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 가져오지 못하는 문제를 해결합니다.
* **MDVA-22383** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.4*) - 제품 저장에 시간이 오래 걸리고 페이지가 중단되는 문제를 해결합니다.
* **MC-41359** (*Adobe Commerce의 경우 >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - 잘못된 SameSite 쿠키 매개 변수 설정의 문제를 수정합니다.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*Adobe Commerce 2.4.1용*) - 페이지 빌더에서 다음 오류가 발생하는 문제를 수정합니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 담당자에게 문의하십시오.*
* **MDVA-35356** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 송장이 부분적으로 발행된 주문 취소 후 잘못된 스토어 크레딧 반환 문제를 해결합니다.
* **MDVA-33289** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.3*) - 다음과 같은 경우 체크아웃 중에 원시 JavaScript 코드가 청구 주소 UI에 표시되는 문제를 수정합니다. [!DNL Google Tag Manager] 이(가) 활성화되었습니다.
* **MDVA-35982** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 특정 웹 사이트로 제한된 관리자가 동일한 웹 사이트에 배치된 주문에 대한 납품을 생성할 수 없는 문제를 수정합니다.
* **MDVA-35155** (*Adobe Commerce >=2.3.0 &lt;2.3.6*) - 옵션 제목을 변경한 경우 번들 제품을 구입할 수 없는 문제를 해결했습니다.
* **MDVA-35910** (*Adobe Commerce의 경우 >=2.4.1 &lt;2.4.3*) - 고객으로 로그인 기능을 사용하지 않도록 설정한 후 새 고객 계정을 만들 수 없는 문제를 수정합니다.
* **MDVA-34474** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - API를 사용하여 구매요청 목록에 제품을 추가할 때 발생하는 문제를 수정합니다.
* **MDVA-34591** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 장바구니 규칙 할인 계산이 잘못되어 문제가 해결되었습니다. *최대 수량 할인이 다음에 적용됩니다.* 및 *할인 수량 단계(구매 X)*.
* **MDVA-33704** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.3*) - 다음과 같은 문제가 해결되었습니다. *매장 픽업* 배송 옵션을 사용할 수 있도록 구성했지만 배송 옵션이 표시되지 않습니다.
* **MDVA-34928** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.3.5-p2*) - 스토어 크레딧이 지급에서 제거된 후 페이지 로더가 무기한으로 표시되는 문제를 수정합니다.
* **MDVA-35254** (*Adobe Commerce >=2.3.1 &lt;2.4.3*) - 체크아웃 중에 CAPTCHA 문제를 해결합니다.
* **MDVA-35569** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - 다음과 같은 문제가 해결되었습니다. *고정 제품 세금* 상태가 지정되면 GraphQL 응답에서 필드가 채워지지 않습니다.
* **MDVA-35847** (*Adobe Commerce의 경우 >=2.4.1 &lt;2.4.3*) - 사용자 지정 고객 속성을 사용하는 경우 회사 사용자 양식이 중단되는 B2B 문제를 수정합니다.
* **MDVA-31307** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.2*) - 다음 위치의 문제를 수정합니다. *메모리 부족* 캐시된 블록에 대한 동적 CSP 허용 목록 문제로 인해 특정 범주에 오류가 발생합니다.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 잘못된 수정 *진행 중* 올바른 메시지 상태 *완료* 소비자를 위한 메시지 `quoteItemCleaner` 여러 제품을 삭제한 후
* **MDVA-34102** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 제품 그리드 및 관리 영역의 제품 편집 페이지에서 비활성화된 제품에 대해 기본 재고 수량이 0으로 수정되었습니다.
* **MDVA-35286** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.2*) - 고객이 장바구니에 제품을 번들로 제공하고 여러 주소 체크아웃에서 온라인 체크아웃으로 전환하는 경우 오류가 발생하는 문제를 해결합니다.
* **MDVA-35312** (*Adobe Commerce의 경우 >=2.4.1-p1 &lt;2.4.2*) - 빈 GraphQL 요청일 때 응답 코드 500을 수정합니다.
* **MDVA-34189** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.3*) - 수정 사항 503 첫 번째 바이트 시간 초과 [!DNL Visual Merchandiser] 관리자 범주 페이지를 로드할 때 쿼리합니다.
* **MDVA-34695** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.1*) - 수정 사항 음수 `children_count` 카테고리를 삭제한 후

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*Adobe Commerce >=2.3.1 &lt;2.4.3*) - 다음과 같은 문제가 해결되었습니다. *기본값 사용* 예약된 변경 사항이 적용되면 확인란이 지워집니다. 예약된 변경 사항이 더 이상 적용되지 않으면 문제가 표시됩니다.
* **MDVA-35064** (*Adobe Commerce >=2.3.3 &lt;2.4.3*) - API를 통해 만든 구성 가능한 제품에 대해 URL 재작이 생성되지 않는 문제가 수정되었습니다.
* **MDVA-34943** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 빠른 주문이 이전에 입력한 SKU를 캐시하는 문제를 수정합니다.
* **MDVA-35197** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.4.0*) - 이전에 추가한 제품의 재고가 부족한 경우 GraphQL을 사용하여 장바구니에 추가할 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-34850** (*Adobe Commerce의 경우 >=2.3.1 &lt;2.4.0*) - 구성 가능한 제품의 품절 옵션이 취소선으로 표시되지 않고 표시되지 않는 문제를 수정합니다.
* **MDVA-34867** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 예정된 업데이트에 대해 설정된 조건 필드의 값이 저장되지 않는 문제를 해결합니다.
* **MDVA-35092** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.4.3*) - 사용자가 추가할 수 없는 문제 해결 [!DNL Vimeo] 더 이상 사용되지 않는 비디오로 인해 [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*Adobe Commerce의 경우 >=2.3.6 &lt;2.4.3*) - 일치하는 제품에 각 웹 사이트의 가격이 다른 경우 페이지 빌더 제품 콘텐츠 유형 미리 보기가 중단되는 문제를 수정합니다.
* **MDVA-32634** (*Adobe Commerce ^2.3.1용*) - 다음과 같은 문제가 해결되었습니다. `url_path` 계층 구조에서 범주를 이동한 후에도 모든 저장소에 할당된 범주의 범주는 변경되지 않습니다.
* **MDVA-33344** (*Adobe Commerce ^2.3.0용*) - 하드 코딩되는 문제를 수정합니다 `rma_item` 데이터베이스의 값 대신 엔티티 기본 속성 집합 ID가 사용됩니다.
* **MDVA-34192** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.3*) - dd/mm/yyyy 형식을 사용하여 고객 생년월일을 수정/지정할 수 없는 문제를 수정합니다.
* **MDVA-34847** (*Adobe Commerce ^2.3.0용*) - 사용자 지정 권한이 있는 관리자 사용자에 대한 관리 컬렉션의 저장소 ID 유형을 SQL 조건에 대한 정수로 변환하는 수정 사항입니다.
* **MDVA-34886** (*Adobe Commerce ^2.3.2용*) - 다음 경우에 검색 결과가 반환되지 않는 문제를 수정합니다. *두께* 제품 속성이 검색 가능한 것으로 구성되어 있습니다.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 의 문제를 수정합니다. [!DNL PayPal Payflow Pro] 리디렉션 매개 변수 목록 형식 오류로 인해 결제가 실패했습니다.
* **MDVA-34023** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.3*) - 오류가 발생하는 문제를 수정합니다 *addressId를 가진 엔티티 없음* 방문자의 브라우저에 임의로 표시됩니다.
* **MDVA-32759** (*Adobe Commerce의 경우 >=2.3.1 &lt;2.4.3, B2B 확장 포함*) - 공유 카탈로그가 기존 계층 가격을 삭제하는 문제를 해결합니다.
* **MDVA-33482** (*Adobe Commerce ^2.3.5용*) - 부분 송장에 대해 대변 메모를 생성하면 해당 부분 송장에 대한 세금 대신 총 주문에 대한 세금이 발생하는 문제를 수정합니다.
* **MDVA-33393** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 오류를 수정합니다. *입력한 countryId가 존재하지 않습니다.*.
* **MDVA-33632** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.7*) - 예외 메시지가 표시되는 수정 사항을 제공합니다. *이 제품은 품절입니다* 품절 제품을 재주문하려고 할 때 이제 가 관리자에게 표시됩니다.
* **MDVA-34469** (*Adobe Commerce >=2.4.1 &lt;2.4.2*) - 여러 스토어 보기를 사용할 때 고객 장바구니의 GraphQL 돌연변이가 실패하는 문제를 수정합니다.
* **MDVA-33976** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.7*) - 번들 제품에서 두 번째 옵션을 제거한 후 번들 제품의 재고가 상점 앞에 품절됨이 표시되는 문제를 수정합니다.
* **MDVA-33894** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.1(B2B 확장 포함)*) - 여러 제품 및 SKU 대소문자 구분 추가 및 제거를 포함하여 빠른 주문 기능에 대한 여러 문제를 수정합니다.
* **MDVA-27664** (*Adobe Commerce >=2.3.4 &lt;2.3.6*) - 고객 등록 양식의 문제를 수정하여 다음 오류를 표시합니다. *오류 - 생년월일은 오늘보다 커서는 안 됩니다.*
* **MDVA-33970** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - 가격 속성의 범위가 웹 사이트로 설정된 경우 대변 메모에 잘못된 통화 기호가 있는 문제를 수정합니다.
* **MDVA-33992** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 체크아웃 중에 B2B 특별 가격이 잘못 표시되는 문제를 해결합니다.
* **MDVA-34100** (*Adobe Commerce >=2.3.4 &lt;2.4.2(B2B 확장 포함)*) - 회사 구조 페이지에서 회사 계정을 만들 수 없는 문제를 수정합니다.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*Adobe Commerce의 경우 >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - CSV 파일에서 제품을 가져온 후 이미지가 중복되는 문제를 해결합니다.
* **MDVA-33382** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 범주에서 제품이 제거된 후 인덱서 무효화 문제가 해결됩니다.
* **MDVA-28511** (*Adobe Commerce >=2.3.5 &lt;2.3.6*) - 완료할 수 없는 문제를 수정합니다 [!DNL PayPal] 이름 필드에 특정 문자(예: 악센트 부호 대문자)가 포함되어 있는 경우 체크아웃.
* **MDVA-31519** (*Adobe Commerce >=2.3.5 &lt;2.3.6*) - 사이트 전체 판매 규칙이 사용 중일 때 게스트 체크아웃에서 대기 시간 초과 문제를 수정합니다.
* **MDVA-33281** (*Adobe Commerce >=2.3.4 &lt;2.3.6*) - 치명적인 오류가 발생하는 문제를 해결합니다. `inventory:reservation:list-inconsistencies` 잘못된 SKU 매개 변수 유형으로 인해 발생합니다.
* **MDVA-24201** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.5*) - 수동으로 다시 색인화할 때까지 가격이 예약된 장바구니 가격 규칙을 반영하지 않는 문제를 수정합니다.
* **MDVA-32694** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - 기본 스토어가 아닌 제품과 관련된 경우 관리자가 협상 가능 견적에 제품을 추가할 수 없는 문제를 해결합니다.
* **MDVA-33516** (*Adobe Commerce >=2.3.0 &lt;2.3.6*) - 구매요청 목록에서 번들 제품을 편집하면 오류가 발생하는 문제를 수정합니다.
* **MDVA-33975** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - GraphQL 요청의 가격 계산과 관련된 여러 문제를 수정합니다.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 의 문제를 수정합니다. [!DNL PayPal] 다음에서 결제 보고서를 사용할 수 없음: **보고서** > **판매** > **[!DNL PayPal]** 예상대로 해결되었습니다.
* **MCP-** (*Adobe Commerce >=2.3.1 &lt;2.4.2*) - 카테고리 제품에 대한 색인화 시간과 대규모 프로필에 대한 주식 색인화 시간이 개선되었습니다.
* **MDVA-33106** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - cron 후에 스케줄 조정된 제품 변경 사항이 지워지는 문제를 수정합니다 `run` 명령이 실행됩니다.
* **MDVA-19391** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.5*) - 다음의 문제를 수정합니다. `analytics_collect_data` 의 NULL 설명 레코드로 인해 오류가 발생합니다. `catalog_category_entity_text` 테이블.
* **MDVA-20376** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.4*) - 의 문제를 수정합니다. *customerId = 1인 엔티티가 없음* 에 오류 발생 `exception.log` 주문 배치 후 로그인한 고객의 경우
* **MDVA-23764** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.5*) - 의 버그를 수정합니다. `JsFooterPlugin.php` 동적 블록의 표시에 영향을 줍니다.
* **MDVA-13203** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 다음과 같은 문제가 해결되었습니다. *무결성 제한 위반 search_tmp_ 테이블* 전체 색인 재지정 후 오류가 나타납니다.
* **MDVA-23426** (*Adobe Commerce의 경우 >=2.3.3 &lt;2.3.5*) - Adobe Commerce에서 보낸 알림 이메일에 첨부 파일로 추가되는 내용이 있는 빈 본문이 포함되어 있는 문제를 수정합니다.
* **MDVA-22150** (*Adobe Commerce >=2.3.1 &lt;2.3.4*) - 장바구니에 구성 가능한 제품이 있고 쿠폰이 적용된 고객이 관리에서 해당 구성 가능한 제품이 비활성화된 경우 로그인할 수 없는 문제가 해결되었습니다.
* **MDVA-32545** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 관리자로부터 주문을 생성할 때 송장이 자동으로 전송되지 않는 문제를 수정합니다.
* **MDVA-32714** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.1*) - GraphQL 제품 쿼리에서 고객 그룹 가격이 작동하지 않는 문제를 수정합니다.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.4.2*) - 를 추가합니다. *소계(포함) 세금)* 가격 규칙 조건 옵션.
* **MDVA-31236** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.2*) - 사용자 지정 리소스 액세스 권한을 가진 관리자가 2FA를 설정하거나 로그인할 수 없는 문제를 수정합니다.
* **MDVA-30845** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.3.7*) - 다음과 같은 문제가 해결되었습니다. *죄송합니다. 현재 이 주문에 사용할 수 있는 견적이 없습니다.* ups XML/USPS/DHL에 연결하지 못하면 오류가 표시되고 다른 배송 방법을 사용할 수 없습니다.
* **MDVA-32133** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.1*) - 특정 경우에 미디어 갤러리가 페이지 빌더에서 로드되지 않는 문제를 수정합니다.
* **MDVA-12304** (*Adobe Commerce의 경우 >=2.3.0*) - 최대 쿠키 수를 50개에서 200개로 늘립니다.
* **MDVA-32632** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.5*) - 주문이 결제 시스템에 표시되지만 Adobe Commerce에 표시되지 않는 문제를 수정합니다.
* **MDVA-32449** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2(B2B 확장 포함)*) - 주문 내역이 매우 느리게 로드되거나 전혀 로드되지 않는 문제를 수정합니다.
* **MDVA-32739** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 비동기 이메일 알림을 활성화하면 이전 판매 이메일이 전송되는 문제가 해결됩니다.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*Adobe Commerce 2.3.6, 2.4.1용*) - 다음과 같은 문제가 해결되었습니다. *계정 만들기* 에서 잘못된 데이터를 수정한 후에도 버튼이 비활성화됨 *새 고객 계정 만들기* 양식.
* **MDVA-31006** (*Adobe Commerce 2.3.0의 경우, 2.3.1*) - 을 사용하여 주문을 한 후 중복 주문이 표시되는 문제를 수정합니다 [!DNL Paypal Express] 결제.
* **MDVA-25602** (*Adobe Commerce 2.3.0용*) - 의 문제 수정 [!DNL PayPal Payflow Pro] 결제 방법 및 쿠키를 다음으로 처리 `SameSite=Lax` 기본적으로 Chrome 80 브라우저 및 API 응답에서 고객 로그인 페이지로 리디렉션됩니다.

## v1.0.10 {#v1-0-10}

패치 버전에 대한 사소한 수정 사항

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.4.2*) - 다음과 같은 경우 쿠폰이 포함된 장바구니 가격 규칙이 GraphQL을 통해 적용되지 않는 문제를 수정합니다. *장바구니 전체에 대한 고정 금액 할인* 작업이 사용됩니다.
* **MDVA-30889** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 가상 및 간단한 제품을 옵션으로 사용하여 번들을 호출한 후 오류가 발생하는 문제를 수정합니다.
* **MDVA-31791** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.3.5*) - 대상 규칙 또는 연결된 제품이 사용되는 경우 제품 페이지의 성능을 개선합니다.
* **MDVA-31168** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 제품 내보내기 CSV 파일이 표시되지 않고 메모리 할당 오류가 발생하는 문제를 수정합니다.
* **MDVA-32313** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.4*) - 구성 가능한 제품을 잘못된 구성 옵션으로 위시리스트에 추가할 수 있는 문제를 수정합니다.
* **MDVA-31759** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 제품이 업데이트되지 않는 문제를 해결했습니다. *드롭다운* 및 *텍스트 영역* CSV 가져오기 중 속성 값.
* **MDVA-32012** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 한국 및 아르헨티나의 우편번호를 확인할 수 없는 문제를 수정합니다.
* **MDVA-31640** (*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - REST API를 통해 특별 가격을 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-28651** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0(B2B 확장 포함)*) - REST API를 통해 협상 가능한 견적을 로드할 때 성능 문제가 발생하는 문제를 해결합니다.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*Adobe Commerce >=2.3.0 &lt;2.4.1(B2B 확장 포함)*) - 대변 메모 그리드에 잘못된 통화 기호가 표시되는 문제를 수정합니다.
* **MDVA-31295** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 부분 주문이 완료되고 품목에 세금이 부과될 때 보상 포인트가 계산되지 않는 문제를 수정합니다.
* **MDVA-30112** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - 주문 수가 을 초과하는 문제가 해결되었습니다. *뭉치 크기* value, Adobe Commerce은 다음을 통해 주문을 고려합니다. *보류 중* 상태가 일치하지 않습니다.
* **MDVA-31150** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 송장이 Rest API 호출에 의해 게시되고 주문이 상점 신용 및 기프트 카드 계정에 의해 부분적으로 지급된 경우 GET 송장 REST API 호출에서 상점 신용 및 기프트 카드 잔액이 반환되지 않는 문제를 해결합니다.
* **MDVA-30963** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.4.2*) - 제품 필터링 결과가 다음에 대해 지정된 값만 포함하도록 설정되는 문제를 수정합니다. *모든 스토어 보기* 관리자의 범위에는 스토어 보기 수준에서 재정의된 값이 있는 제품을 포함합니다.
* **MDVA-29954** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2(B2B 확장 포함)*) - 다음과 같은 문제가 해결되었습니다. *새 회사 등록 요청* 및 *회사에 연결되었습니다.* 이메일이 잘못된 주소에서 발송되었습니다.
* **MDVA-28357** (*Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - 표준 분석기를 의 SKU 필드에 대한 키워드 토큰화기로 사용자 지정 분석기로 바꿉니다. [!DNL ElasticSearch] 와일드카드 검색 쿼리를 하이픈(&quot;-&quot;)이 포함된 SKU와 함께 작동하도록 하는 색인입니다.

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 사용자 지정 순서 상태가 변경된 문제가 해결되었습니다. *처리 중* WebApi를 사용하여 부분 선적을 만든 후.
* **MDVA-30428** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.3.5*) - 이 제품이 사용자 정의 인벤토리 소스에 할당된 경우 고객이 제품을 위시리스트에 추가할 수 없는 문제를 수정합니다.
* **MDVA-30594** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - FPT가 구성된 경우 체크아웃 중에 여러 주소가 있는 주문을 저장할 수 없는 문제를 수정합니다.
* **MDVA-29148** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - API 호출을 통해 제품을 만들 때 의 제품 사용자 지정 속성인 문제를 수정합니다. `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (Multiselect와 유사) 유형은 페이로드에 값이 제공되지 않으면 기본값을 사용하지 않습니다.
* **MDVA-30837** (*Adobe Commerce의 경우 >=2.3.1 &lt;2.3.5*) - 구성 설정을 추가했습니다. *세금에 포함: 예/아니오* 무료 배송 방법 구성에서. 날짜 *금액에 세금 포함* 이(가) (으)로 설정됨 *예*&#x200B;최소 주문 금액은 소계 + 세금으로 계산됩니다. 날짜 *금액에 세금 포함* 이(가) (으)로 설정됨 *아니요*, 최소 주문 금액은 소계로 계산됩니다.
* **MDVA-25028** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - 을 사용하여 주문하는 경우 문제를 수정합니다. [!DNL PayPal Payflow Pro] 사기 필터가 트리거될 때 &quot;사기 혐의&quot; 상태로 설정되지 않습니다.
* **MDVA-31224** (*Adobe Commerce의 경우 >=2.3.3 &lt;2.3.5*) - 의 성능을 개선합니다. `catalog_product_price` 번들 제품에 대한 작업을 다시 색인화합니다.
* **MDVA-31321** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.5*) - 다음과 같은 경우 빈 페이지를 수정합니다(오류). *모두 표시* 이(가) 선택되어 있습니다. [!DNL Elasticsearch] 큰 제품 id 목록을 반환합니다. 이 시나리오에서는 order by 절이 잘못된 SQL 형식으로 변환됩니다.
* **MDVA-30815** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.4*) - 검색 결과 페이지에 표시할 검색 결과 수를 변경하면 Adobe Commerce에 빈 페이지가 표시되는 문제를 수정합니다. [!DNL Elasticsearch] 이제 페이지당 조회한 검색 결과 수를 변경할 때 카테고리 페이지의 결과가 올바르게 표시됩니다.
* **MDVA-30782** (*Adobe Commerce의 경우 >=2.3.5 &lt;2.4.2*) - 장바구니 규칙에 관계없이 동적 블록이 표시되는 문제를 수정합니다.
* **MDVA-31021** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 성능 문제가 있는 문제를 해결합니다. `module-catalog-import-export/Model/Import/Product/Option.php`. 에 ~100만 개 이상의 레코드가 있는 경우 `catalog_product_option` 표: 단일 제품이 포함된 새 CSV의 유효성을 검사하는 데 10초 미만이 소요됩니다.
* **MDVA-31007** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.1*) - 사용자 지정 주소 속성이 내 계정 영역 및 백엔드의 주문 세부 사항 페이지에 올바르게 표시되지 않는 문제를 수정합니다.
* **MDVA-29389** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 고급 보고에서 다음과 같은 문제를 수정합니다. `analytics_collect_data` cronjob은 이렇게 말합니다: *포트는 호스트 매개 변수 내에 구성해야 합니다(예: localhost:3306).*.
* **MDVA-31343** (*Adobe Commerce >=2.3.4 &lt;2.3.6*) - 제거된 본문 클래스의 문제를 수정합니다 `page-layout-category-full-width` 범주가 예약되는 경우.
* **MDVA-30945** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 카트를 업데이트할 때 치명적인 오류 메시지가 표시되는 문제를 수정합니다 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.0*) - 를 구현합니다. *최소값이 일치해야 함* 기능 및 부분 검색 [!DNL Elasticsearch] 엔진. 검색 쿼리에서 하이픈 문제를 해결합니다.
* **MDVA-30102** (*Adobe Commerce의 경우 >=2.3.2 &lt;=2.4.0*) - 레이아웃 캐시에 TTL이 없기 때문에 Redis 캐시가 빠르게 증가하는 문제를 수정합니다.
* **MDVA-30599** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.4.0*) - API를 사용하여 만든 게스트 견적이 로그인한 고객에 대한 견적으로 잘못 표시되는 문제가 수정되었습니다.
* **MDVA-29446** (*Adobe Commerce의 경우 >=2.3.3 &lt;=2.4.0*) - 체크아웃 시 해당 배송 방법이 아닌 가격이 0으로 표시되는 문제를 수정합니다.
* **MDVA-30357** (*Adobe Commerce의 경우 >=2.3.2 &lt;=2.4.0*) - cron에서 사이트 맵을 생성할 때 잘못된 이미지 URL이 생성되는 문제를 수정합니다.
* **MDVA-30565** (*Adobe Commerce의 경우 >=2.3.2 &lt;=2.3.3-p1*) - 다음의 문제를 수정합니다. *Cartid = 0인 해당 엔티티 없음* 지속적인 장바구니가 활성화된 경우 상점 전면 체크아웃 시 게스트 고객에 대한 오류가 표시됩니다.
* **MDVA-29787** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.4.0*) - 다음과 같은 경우 관련 제품에 대한 target 규칙이 작동하지 않는 문제를 해결합니다. *다음 중 하나* 조건은 표시할 제품을 정의하는 데 사용됩니다.
* **MDVA-30977** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.3.5-p2*) - 색인 재지정 후 범주에서 무작위 제품이 누락된 문제를 수정합니다.
* **MDVA-28202** (*Adobe Commerce의 경우 >=2.3.4 &lt;=2.4.2*) - MSI를 사용할 때 계층 탐색 이 구성 가능한 제품을 올바르게 필터링하지 못하는 문제를 해결했습니다.
* **MDVA-28300** (*Adobe Commerce >=2.3.0 &lt;2.3.6*) - GQL 요청이 카탈로그 가격 규칙의 가격 변경을 반영하지 않는 문제를 수정합니다.
* **MDVA-31006** (*Adobe Commerce의 경우 >=2.3.2 &lt;=2.4.2*) - 을 사용하여 주문을 한 후 중복 주문이 표시되는 문제를 수정합니다 [!DNL Paypal Express] 결제.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 계층화된 탐색과 관련된 문제가 해결되었습니다. 여기서 *아니요* 다음과 같은 경우 부울 유형 제품 속성에 대한 값이 계층 탐색에 포함되지 않았습니다. [!DNL Elasticsearch] 검색 엔진으로 사용되었습니다.
* **MDVA-28191** (*Adobe Commerce >=2.3.3 &lt;2.4.2*) - 관리자를 통해 주문을 만드는 동안 결제 방법이 로드되지 않는 문제를 수정합니다.
* **MDVA-29959** (*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1(B2B 확장 포함)*) - 제한된 관리 사용자가 *회사* 회사 계정을 삭제할 수 있는 권한이 허용되지 않습니다.
* **MDVA-30265** (*Adobe Commerce >=2.3.3 &lt;2.4.2*) - 송장 생성 후 배송 추적 링크가 작동하지 않는 문제를 수정합니다.
* **MDVA-28409** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 다음과 같은 문제가 해결되었습니다. `sales_clean_quotes` cron 작업 실패 *메모리 부족* 데이터베이스의 만료된 따옴표 수가 많은 경우 오류 발생.
* **MDVA-30593** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.3.4*) - Quote Lifetime 설정에 따라 만료된 Quote 가 정리되지 않는 문제가 해결되었습니다.
* **MDVA-30107** (*Adobe Commerce >=2.3.0 &lt;2.3.6*) - 스토어 보기에 다른 기본 URL을 사용하는 경우 스토어 전환기가 예상대로 작동하지 않는 문제를 수정합니다.
* **MDVA-28763** (*Adobe Commerce의 경우 >=2.3.2 &lt;2.3.4*) - REST API를 사용하여 제품 정보를 두 번 이상 업데이트한 후 제품 이미지가 복제되는 문제를 수정합니다.
* **MDVA-30284** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 다음 원인으로 인해 카탈로그 검색 인덱서가 실패하는 문제를 수정합니다 *[!DNL Elasticsearch]오류: 인덱스의 총 필드 제한을 초과했습니다.*
* **MDVA-29042** (*Adobe Commerce >=2.3.3 &lt;=2.3.4-p2(B2B 확장 포함)*) - 카탈로그 권한이 (으)로 변경된 문제를 수정합니다. *허용* 새 제품이 공유 카탈로그에 추가된 후 자동으로 업데이트됩니다.
* **MDVA-30428** (*Adobe Commerce >=2.3.3 &lt;2.4.2*) - 이 제품이 사용자 정의 인벤토리 소스에 할당된 경우 고객이 제품을 위시리스트에 추가할 수 없는 문제를 수정합니다.
* **MDVA-28661** (*Adobe Commerce >=2.3.0 &lt;2.4.2(B2B 확장 포함)*) - 회사 관리자가 변경된 후 회사 사용자 회사 계정 섹션에 오류가 발생하는 문제를 수정합니다.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*Adobe Commerce 2.3.1용 - 2.3.4-p2*) - 데이터베이스 이름이 너무 길어 프런트 엔드에 범주가 업데이트되지 않는 경우 cron 작업이 실패하는 문제를 수정합니다.
* **MDVA-30106** (*Adobe Commerce ^2.3.0용*) - 체크아웃 지불 중에 가 로드되지 않는 문제를 수정합니다. *null의 &#39;length&#39; 속성을 읽을 수 없음* js 콘솔에 오류가 발생했습니다.
* **MDVA-28656** (*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - 필요한 결제 정보가 없는 주문(예: 100% 할인)이 있고 주문에 대한 송장이 생성된 경우 주문 상태가 (으)로 변경되는 문제를 해결합니다. *종료됨* (완료 대신)를 참조하십시오.
* **MDVA-30209** (*Adobe Commerce 2.3.0용 - 2.3.3-p1*) - 고객이 계정 정보를 업데이트한 경우 고객 그룹이 기본값으로 변경되는 문제를 수정합니다.
* **MDVA-30123** (*Adobe Commerce의 경우 >=2.3.4 &lt;2.4.2*) - 속성 옵션 레이블이 GraphQL 쿼리에 대해 올바르게 번역되지 않는 문제를 수정합니다.
* **MDVA-29996** (*Adobe Commerce >=2.3.3 &lt;2.4.2*) - 카테고리 권한을 활성화한 후 카테고리 페이지가 전체 페이지 캐시에 의해 캐시되지 않는 문제를 수정합니다.
* **MDVA-30164** (*Adobe Commerce >=2.3.1 &lt;2.4.2*) - 사용자 지정 고객 속성이 있는 경우 고객 그리드에서 고객 레코드를 내보낼 수 없는 문제를 수정합니다.
* **MDVA-30444** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.1*) - GraphQL을 사용하여 주문한 주문에 대해 확인 이메일이 전송되지 않는 문제를 수정합니다.
* **MDVA-30490** (*Adobe Commerce 2.3.4 - 2.3.5-p2용*) - 제품 중 하나에 짧은 설명이 비어 있는 경우 제품 비교에서 500 오류 페이지가 표시되는 문제를 수정합니다.
* **MDVA-30232** (*Adobe Commerce의 경우 >=2.3.1 &lt;2.4.1*) - 원래 주문에 기프트 카드가 포함된 경우 다시 주문할 수 없는 문제를 수정합니다.
* **MDVA-29965** (*Adobe Commerce의 경우 >=2.3.3 &lt;2.4.0*) - 장바구니에 제품을 추가할 때 고객에게 잘못된 양식 키 오류가 발생하는 문제를 수정합니다.
* **MDVA-30008** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.2*) - 공개 카탈로그에 있는 제품에 대해 관리 API를 통해 주문할 수 없는 B2B 문제를 수정합니다.
* **MDVA-22469** (*Adobe Commerce 2.3.2-p2의 경우 - 2.3.3-p1*) - Adobe Commerce 2.3.3으로 업그레이드한 후 페이지 빌더가 관리 패널에서 작동하지 않고 일부 JS 및 CSS 파일이 로드되지 않는 문제를 해결했습니다.
* **MC-35984** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.1*) - RMA(Return Merchandise Authorization)에 대한 배송 레이블을 만든 후 판매자가 반환 페이지의 페이지 요소와 상호 작용할 수 없는 문제를 수정합니다.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*Adobe Commerce 2.3.0용 - 2.3.4*) - 의 문제를 수정합니다. [!DNL PayPal Payflow Pro] 결제 방법 및 쿠키를 다음으로 처리 `SameSite=Lax` 기본적으로 Chrome 80 브라우저 및 API 응답에서 고객 로그인 페이지로 리디렉션됩니다.
* **MDVA-26694** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - 다르게 만료되도록 예약되어 있지만 제품 및 카탈로그 캐시가 매일 만료되는 문제를 수정합니다.
* **MDVA-27825** (*Adobe Commerce의 경우 >=2.3.0 &lt;2.4.1*) - 메모리 누수로 인해 대량의 데이터를 내보내지 못하는 문제를 해결합니다.
* **MDVA-29085** (*Adobe Commerce의 경우 >=2.3.0 &lt;=2.3.5-p1*) - 회사가 API로 생성된 경우 필요한 새 회사 이메일이 전송되지 않는 B2B 문제를 수정합니다.
* **MDVA-29344** (*Adobe Commerce의 경우 >=2.3.5 &lt;=2.4.0-p1*) - 헤더 요소에서 텍스트 요소로 텍스트를 복사한 후 페이지 빌더가 중단되는 문제를 수정합니다.
* **MDVA-29835** (*Adobe Commerce >2.3.1 &lt;2.4.2*) - 기프트 카드 주문에 두 개의 코드가 포함되어 있는 문제를 수정합니다.
* **MDVA-30052** (*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - 개인 콘텐츠(로컬 저장소)가 제대로 채워지지 않아 성능 문제가 발생하는 문제를 해결합니다.
* **MDVA-30131** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 계층화된 탐색과 관련된 문제가 해결되었습니다. 여기서 *아니요* 다음과 같은 경우 부울 유형 제품 속성에 대한 값이 계층 탐색에 포함되지 않았습니다. [!DNL Elasticsearch] 검색 엔진으로 사용되었습니다.
* **MDVA-35514** (*Adobe Commerce의 경우 >=2.4.0 &lt;2.4.1*) - 패키지 만들기 모달 창에서 배송 레이블을 만들고 주문한 제품을 패키지에 추가하는 문제를 해결했습니다.
