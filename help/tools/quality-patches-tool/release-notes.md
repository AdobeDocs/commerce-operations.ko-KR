---
title: 릴리스 정보
description: Adobe Commerce에 사용할 수 있는 패치와 이러한 패치가 해결하는 문제에 대해 알아봅니다.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# 릴리스 정보

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)은(는) Adobe 및 Magento Open Source 커뮤니티에서 개발한 개별 패치를 제공합니다. 설치된 Adobe Commerce 버전에 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리기 및 볼 수 있습니다. 누가 패치를 개발했는지에 관계없이 Adobe Commerce 및 Magento Open Source 프로젝트에 패치를 적용할 수 있습니다. 예를 들어 커뮤니티에서 개발한 패치를 Adobe Commerce 프로젝트에 적용할 수 있습니다.

>[!INFO]
>
>Adobe Commerce 프로젝트에 패치를 적용하는 방법은 [패치 적용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches)을 참조하십시오. 릴리스된 패치의 전체 목록을 검토하려면 소프트웨어 업데이트 가이드의 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하십시오.

>[!INFO]
>
>커뮤니티에서 Magento Open Source을 위해 만든 [!DNL quality patches]에 대한 자세한 내용은 [릴리스 정보](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)를 참조하세요.

## v1.1.48 {#v1-1-48}

* **ACSD-55566**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 동일한 번들 항목이 있는 소스 및 대상 카트를 병합할 때 [!DNL GraphQL] 응답에서 &quot;*내부 서버 오류*&quot;로 `mergeCart` 돌연변이가 실패하는 문제를 해결했습니다.
* **ACSD-56546**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - **제품 구성 중 표시**&#x200B;가 *사용 안 함*&#x200B;일 때 구성 가능 및 번들 제품이 상점 앞에 **재고 부족**&#x200B;으로 표시되는 문제를 해결했습니다.
* **ACSD-56635**(Adobe Commerce >=2.4.6 &lt;2.4.7) - 가져오기를 **계정 공유**&#x200B;와 함께 사용하여 *Global*&#x200B;로 설정한 경우 가져온 고객이 동일한 전자 메일 주소로 복제되는 문제를 수정합니다.
* **ACSD-56741**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 데이터베이스에 색인 지정 메커니즘 및 [!DNL MView]과(와) 관련이 없는 사용자 지정 [!DNL MySQL] 트리거가 포함된 경우 `setup:upgrade` 동안 표시되는 &quot;*null 형식의 값에 대한 배열 오프셋에 액세스하려고 합니다*&quot; 오류 메시지를 수정합니다.
* **ACSD-57315**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 관리자의 **[!UICONTROL View transaction]** 화면에서 [!UICONTROL Fetch] 단추를 클릭할 때마다 [!DNL PayPal Payflow Pro]에서 새 트랜잭션이 만들어지는 문제를 수정합니다.
* **ACSD-57337**(Adobe Commerce >=2.4.4 &lt;2.4.6) - 특정 웹 사이트에 대한 액세스 제한이 있는 관리자 사용자가 **[!UICONTROL Companies]** 그리드에 있는 모든 웹 사이트에서 회사를 볼 수 있는 문제를 해결했습니다.
* **ACSD-57394**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - [!DNL GraphQL]의 여러 정렬 필드를 기준으로 잘못된 제품 정렬 문제를 해결합니다.
* **ACSD-57565**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 기간이 업데이트될 때까지 **[!UICONTROL Order]** 대시보드에 잘못된 주문 정보가 표시되는 문제를 해결합니다. 이제 대시보드에 첫 번째 로드 시 올바른 주문 통계가 표시됩니다.
* **ACSD-57854**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 제품 [!DNL GraphQL] 요청이 범주 집계에서 비활성화된 범주를 반환한 경우 문제를 해결합니다.
* **ACSD-58008**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 종료 날짜가 지정되지 않은 경우 예약된 업데이트를 업데이트하여 이전 버전의 준비된 항목을 제거하던 문제를 수정합니다.
* 업데이트된 패치: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 여러 주소로 체크아웃하는 동안 *[!UICONTROL Used]* 및 *[!UICONTROL Times Used]* 특성에 생성된 쿠폰에 대한 잘못된 값이 표시되는 문제를 해결했습니다.
* **ACSD-56760**(Adobe Commerce >=2.4.6 &lt;2.4.7) - 웹 스토어에 자체 루트 범주가 있는 경우 특정 웹 사이트로 제한된 관리 사용자가 범주 내에서 새 제품을 정렬하거나 추가할 수 없는 문제를 해결했습니다.
* **ACSD-56858**(Adobe Commerce >=2.4.2 &lt;2.4.7) - B2B 회사 역할 권한이 제한된 회사 관리자에 대해 잘못 표시되는 문제를 해결했습니다.
* **ACSD-57074**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - `price_`로 시작하는 `attrbute_code`이(가) 있는 *Yes/No* 사용자 지정 특성이 인덱싱에서 제대로 작동하지 않고 이러한 특성이 있는 제품을 프런트 엔드에서 사용할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 제품이 아직 재고가 있는 경우에도 재고 수량이 변경되면 카테고리 페이지가 캐시되는 문제가 해결됩니다.
* **ACSD-54656**(Adobe Commerce >=2.4.5 &lt;2.4.6) - 체크아웃 중에 보이지 않는 Recaptcha가 실패하여 주문이 이루어지지 않는 문제를 해결합니다.
* **ACSD-55100**(Adobe Commerce >=2.4.6 &lt;2.4.7) - GraphQL에서 검색 결과에 1만개 이상의 제품을 반환하지 않는 문제를 해결했습니다.
* **ACSD-56621**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 회사 관리자의 인사말 헤더 섹션에 업데이트된 이름과 성이 반영되지 않는 문제를 수정합니다.
* **ACSD-56842**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - `setup:di:compile`을(를) 실행한 후 지연된 프록시 및 지연된 프록시 팩토리가 없는 문제를 수정합니다.
* **ACSD-57003**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 주문이 부분적으로 환불 및 부분적으로 배송될 때 주문 상태가 *[!UICONTROL Processing]*(으)로 변경되는 대신 *[!UICONTROL Complete]*(으)로 변경되는 문제를 해결했습니다.
* 업데이트된 패치: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 예약된 업데이트로 인해 두 개의 하위 제품 중 하나가 비활성화될 때 구성 가능한 제품이 품절되는 문제를 해결했습니다.
* **ACSD-56616**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 간단한 제품의 재고가 없을 때 번들 제품이 상점 앞에 재고로 표시되는 문제를 해결했습니다.
* **ACSD-56515**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 웹 사이트 수준 권한이 있는 관리자가 동적 블록을 추가하거나 편집할 수 없는 문제가 해결되었습니다.
* **ACSD-56447**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 병렬 REST 웹 API 요청을 통해 동일한 제품을 장바구니에 추가하면 장바구니에 두 개의 개별 항목이 표시되는 문제를 해결합니다.
* **ACSD-56415**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 데이터베이스에 인덱싱할 부분 가격 데이터가 많을 때 `DELETE` 쿼리로 인해 부분 가격 인덱싱의 성능이 느려지는 문제를 해결했습니다.
* **ACSD-54965**(Adobe Commerce >=2.4.5 &lt;2.4.6) - 제품이 사용자 지정 주식에만 할당된 경우 시각적 머천다이징 그리드에 올바른 재고가 표시되지 않는 문제를 해결했습니다.
* **ACSD-52824**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 회사 설정에서 해당 결제 방법을 사용하지 않도록 설정한 경우 회사 고객에 대해 PayPal Express, Google Pay 및 Apple Pay 단추가 표시되는 문제를 해결합니다.
* 업데이트된 패치: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - **재고 부족 상태에서 하단으로 이동** 옵션을 사용하여 범주 제품을 정렬할 때 사용자가 관리 대시보드로 리디렉션되고 `Invalid security or form key. Please refresh the page` 오류가 화면 위에 표시되는 문제를 해결합니다.
* **ACSD-56280**(Adobe Commerce >=2.4.4 &lt;2.4.7) - 선물 레지스트리에서 항목 순서를 지정하면 예외가 발생하는 문제를 수정합니다.
* **ACSD-56246**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 제품에 대해 예약된 업데이트가 활성화될 때 사용자 지정 다중 선택 특성에서 데이터가 제거되는 문제를 해결합니다.
* **ACSD-56193**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4)의 경우) - 예약된 블록이 페이지 빌더를 사용하여 범주 설명에 사용될 때 바니시/Fastly 캐시가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-56158**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - &quot;장바구니&quot; 쿼리가 각 세금 규칙에 대한 총 세금 값을 반환하는 문제를 수정합니다.
* **ACSD-56023**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 캐시가 활성화되면 CMS 페이지에서 위젯 콘텐츠가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-55427**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 관리자가 관리자의 제품 페이지에서 공유 카탈로그의 제품 할당을 취소할 수 없는 문제를 해결했습니다.
* **ACSD-55352**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 고객 보상 포인트가 포함된 부분 대변 메모를 만든 후 주문 상태가 [닫힘]으로 변경되고 [관리 주문] 페이지에서 대변 메모 옵션이 사라지는 문제가 수정되었습니다.
* **ACSD-55231**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 빠른 주문 기능을 사용하여 장바구니에 제품을 추가할 수 없는 문제를 해결했습니다.
* **ACSD-54283**(Adobe Commerce >=2.4.3 &lt;2.4.4) - 기본(일반 그룹)에 대해 공유 카탈로그에 할당되지 않은 제품/범주가 여전히 XML 사이트 맵에 포함된 문제를 해결했습니다.
* 업데이트된 패치: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않는 문제를 해결합니다.
* **ACSD-53636**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5) - 특별 가격이 있는 하위 제품이 구성 가능한 제품의 제품 목록 페이지에 일반 가격이 표시되지 않는 문제를 해결했습니다.
* **ACSD-54885**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 관리 사용자가 *고객으로 로그인* 기능을 사용할 때 다중 주소 체크아웃 문제를 해결합니다.
* **ACSD-55610**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 문제를 해결합니다.
* **ACSD-55334**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - GraphQL 응답의 번역 사전을 통해 레이블에 대한 번역을 수정합니다.
* **ACSD-54739**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 제품 재고 상태 조건이 관련 제품 규칙에 적용되지 않는 문제를 수정합니다.
* **ACSD-53925**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - `catalog_product_price` 차원 모드가 *웹 사이트*&#x200B;로 설정된 경우 관리자가 제품 캐러셀에 CMS 블록을 저장할 수 없는 문제를 해결했습니다.
* **ACSD-52714**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 날짜 형식이 *Y-m-d*(으)로 설정된 경우 날짜 필터가 관리 그리드에서 작동하지 않는 문제를 해결했습니다.
* **ACSD-55055**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 장바구니에서 장바구니 가격 규칙에 제품 특성을 로드하는 성능을 개선합니다.
* **ACSD-53790**(Adobe Commerce >=2.4.6 &lt;2.4.7) - REST API를 통해 단일 제품에 대한 여러 RMA를 만들 수 있는 문제를 해결했습니다.
* **ACSD-56090**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5) - GraphQL 요청이 특별히 요청된 저장소 데이터가 아닌 모든 저장소의 데이터로 응답하는 문제를 해결했습니다.
* **ACSD-54983**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 사용자 상태가 *[!UICONTROL Inactive]*(으)로 설정된 경우 GraphQL 요청으로 회사 사용자 UID를 가져올 수 없는 문제를 해결했습니다.
* **ACSD-53309**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 사용자 지정 가능 옵션을 선택할 때 *[!UICONTROL Regular Price]* 레이블에서 세금이 완전히 적용되지 않는 문제를 해결했습니다.
* **ACSD-55305**(Adobe Commerce >=2.4.4 &lt;2.4.7) - **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** 페이지의 *[!UICONTROL Edit Company User]* 팝업이 화면에서 로더로 중지되는 문제를 수정합니다.
* 업데이트된 패치: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - *[!UICONTROL Recently Viewed]* 제품 데이터가 스토어 보기에서 제대로 업데이트되지 않는 문제를 해결했습니다.
* **ACSD-54626**(Adobe Commerce >=2.4.6 &lt;2.4.7) - [!DNL GraphQL]을(를) 통해 `NUMBER_OF_SKUS` 특성이 있는 새 구매 주문 규칙(`createPurchaseOrderApprovalRule`)을 만들 수 없는 문제를 해결했습니다.
* **ACSD-53845**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - `consumer max_messages` = 0일 때 [!DNL MySQL] 연결 시간 초과 문제를 해결합니다.
* **ACSD-54890**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - `/tmp` 디스크의 공간이 부족하여 `aggregate_sales_report_bestsellers_data`에서 [!DNL MySQL] 오류가 발생하는 문제를 해결합니다.
* **ACSD-55112**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - [!DNL Google reCAPTCHA v3] 유효성 검사 없이 *[!UICONTROL Submit review]* 단추를 여러 번 클릭할 수 있는 문제를 해결했습니다.
* **ACSD-54264**(Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - 오류 메시지 *&quot;요청한 특성을 업데이트할 수 없는 문제가 수정되었습니다. 행 ID: store_id&quot;*&#x200B;은(는) 고객이 다른 스토어 보기에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.
* **ACSD-54418**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 고정 할인 금액이 동적으로 가격이 책정된 번들의 각 하위 제품에 잘못 적용되는 문제를 해결했습니다.
* **ACSD-55238**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 빈 제품 *[!UICONTROL Meta Description]*&#x200B;을(를) 저장하는 동안 수정되었습니다.
* **ACSD-54966**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 이전 주문이 실패한 경우 고객당 사용이 제한된 쿠폰 코드를 다시 사용할 수 없는 문제를 해결했습니다.
* **ACSD-54060**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 제한된 관리자가 다른 범위에 할당된 다른 제품의 하위 항목인 경우 제품을 저장할 수 없는 문제를 해결했습니다.
* **ACSD-48910**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 주문이 청구되어 배송된 후 여러 소스에 할당된 번들 제품의 수량이 0이 아닌 경우에도 재고가 부족한 문제가 해결되었습니다.
* **ACSD-55381**(Adobe Commerce >=2.4.2 &lt;2.4.7) - [!DNL GraphQL]을(를) 통해 [!DNL B2B] *[!UICONTROL Requisition list]*&#x200B;에서 `configurable_product_option_uid` 및 `configurable_product_option_value_uid` 필드를 쿼리할 때 내부 서버 오류가 수정되었습니다.
* **ACSD-55628**(Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 바꾸는 수정 사항이 있습니다.
* 업데이트된 패치: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 제품이 장바구니에 이미 추가된 후 공유 카탈로그에서 제거될 때 장바구니에서 발생하는 문제를 수정합니다.
* **ACSD-53722**(Adobe Commerce >=2.4.4 &lt;2.4.7) - 다른 범위에 대한 예약된 업데이트가 활성화될 때 번들 제품 옵션의 가격이 $0로 변경되는 문제를 해결합니다.
* **ACSD-53643**(Adobe Commerce >=2.4.3 &lt;2.4.7) - 사용 안 함 또는 재고 부족 제품이 있는 구매 주문을 할 때 주문 합계가 잘못된 문제를 수정합니다. 이러한 구매 주문의 *[!UICONTROL Place Order]* 단추를 숨김으로써 해결되었습니다.
* **ACSD-54067**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 제품 비디오가 모바일 장치에서 재생되지 않는 문제를 해결합니다.
* **ACSD-55414**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - MariaDB가 EAV entity_id를 문자열에서 정수로 캐스팅하려고 할 때 성능이 향상됩니다.
* **ACSD-51819**(Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - 동일한 견적 ID로 여러 주문을 할 수 있는 문제를 수정합니다.
* **ACSD-53118**(Adobe Commerce >=2.4.0 &lt;2.4.7) - 제품에 빈 특성이 있는 동안 쿠폰 코드를 사용하여 *[!UICONTROL Cart Price Rule]*&#x200B;이(가) 적용되는 문제를 수정합니다.
* **ACSD-54324**(Adobe Commerce >=2.4.5 &lt;2.4.7) - GraphQL requisition_lists 요청에서 페이지 매김 설정을 고려하지 않고 모든 결과를 반환하는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680**(Adobe Commerce >=2.4.0 &lt;2.4.6) - 여러 개의 할당된 원본이 있는 제품에 대해 제출된 B2B 견적을 처리할 수 없는 문제를 해결했습니다.
* **ACSD-54040**(Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - B2B 모듈이 활성화되면 *[!UICONTROL Created]* 필드가 비어 있는 주문 세부 사항 문제를 수정합니다.
* **ACSD-54319**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - *[!UICONTROL Product in Cart]* 보고서에서 제품 가격이 0으로 표시되는 문제를 해결했습니다.
* **ACSD-53378**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 주소록이 큰 고객의 체크아웃 페이지 로드 시간을 개선합니다.
* **ACSD-52657**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 미니카트가 하위 도메인을 사용하는 보조 저장소 보기에서 업데이트되지 않는 문제를 해결했습니다.
* **ACSD-53414**(Adobe Commerce >=2.4.6 &lt;2.4.7) - 제한된 관리자가 권한 범위 외부에서 CMS 페이지를 볼 수 있는 문제를 해결했습니다.
* **ACSD-54472**(Adobe Commerce >=2.4.6 &lt;2.4.7) - 거부된 회사의 고객이 계속 인증할 수 있고, 차단되거나 거부된 회사의 고객이 여전히 주문을 할 수 있는 문제를 수정합니다. 이 패치는 GraphQL 종단점에 대한 추가 유효성 검사를 추가합니다.
* **ACSD-52801**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - GraphQL에서 제품을 검색할 때 부분 일치를 수행하는 옵션을 추가합니다.
* **ACSD-55004**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - `php.ini`에 구성된 값보다 큰 가져오기 파일을 업로드하는 동안 유효성 검사기가 충돌하는 문제를 해결했습니다.
* **ACSD-54989**(Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - *[!UICONTROL Enable Purchase Orders]*&#x200B;이(가) *[!UICONTROL Yes]*(으)로 설정되고 *[!UICONTROL Purchase Order]*&#x200B;이(가) *[!UICONTROL No]*(으)로 설정된 경우 회사 관리자가 주문할 수 없는 문제를 해결했습니다.
* **ACSD-54007**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 고객 데이터를 가져올 때 정의되지 않은 배열 키 &quot;_scope&quot;*오류가 수정되었습니다.*
* **ACSD-55031**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 컴파일 중에 *Type &quot;mixed&quot;를 null을 허용할 수 없습니다* 오류가 수정되었습니다.
* **ACSD-54961**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 제한된 관리자가 *제품 검토* 상태를 일괄 업데이트할 수 없는 문제를 해결했습니다.
* **ACSD-55256**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 첫 번째 이미지만 이미지 슬라이더에 표시되는 문제를 해결했습니다.
* 업데이트된 패치: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704**(Adobe Commerce >=2.4.0 &lt;2.4.7) - 보상 포인트가 만료된 후 보상 포인트 잔고 내역이 잘못 계산되는 문제를 수정합니다.
* **ACSD-53583**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - *카테고리 제품* 및 *제품 카테고리* 인덱서의 부분 색인 재지정 성능을 개선합니다.
* **ACSD-54026**(Adobe Commerce >=2.4.6 &lt;2.4.7) - 권한이 없는 사용자에 대한 `updateCompanyRole` GraphQL 요청에 대해 잘못된 오류 메시지를 수정합니다.
* **ACSD-54106**(Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5) - 터키어 악센트 부호가 있는 문자의 이름별 범주 제품 정렬이 올바르지 않은 문제를 해결했습니다.
* **ACSD-52219**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 책갈피 보기 사이를 자주 전환할 때 관리 그리드 저장 필터가 예상대로 작동하지 않는 문제를 해결했습니다.
* **ACSD-54342**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 잘못된 오류 메시지가 수정됩니다. *데이터 구조에 오류: 유효한 데이터가 없는 CSV 파일을 가져올 때 값이 혼합됨*.
* **ACSD-54660**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 새 입력 특성 *sort*&#x200B;을(를) 추가하여 GraphQL에서 고객 주문을 `sort_field` 및 `sort_direction`(으)로 정렬했습니다.
* **ACSD-54776**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 선택하지 않은 *[!UICONTROL Use Default Value]* 및 기본이 아닌 제품 필드 값이 두 번째 웹 사이트, 스토어 및 스토어 보기에 저장되지 않는 문제를 해결했습니다.
* **ACSD-53998**(Adobe Commerce 및 Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) - 고객 계정에서 로그아웃한 후 **[!UICONTROL Customer Segment]**&#x200B;을(를) 기반으로 하는 **[!UICONTROL Dynamic Block]**&#x200B;이(가) 제대로 작동하지 않는 문제를 해결했습니다.
* **ACSD-53204**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 수정 사항 *제품을 저장할 수 없습니다.`rest/V1/products/<sku>/media` 끝점을 사용하여 제품 갤러리에 이미지를 추가하도록 동시에 요청할 때* 오류가 발생했습니다.
* **ACSD-47657**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - AWS 자격 증명에 대한 캐싱 메커니즘을 추가했습니다. 이제 자격 증명 공급자는 Magento 캐시를 사용하여 EC2 구성을 위해 AWS에서 검색한 자격 증명을 캐시합니다.
* 업데이트된 패치: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4) - 부분 인덱스가 실행될 때 공유 카탈로그에 할당된 제품이 상점 앞에 표시되지 않는 문제를 해결했습니다.
* **ACSD-54018**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 위젯 조건에서 비전역 특성을 사용하는 [!UICONTROL Product List] 위젯의 성능 문제를 수정합니다.
* **ACSD-54111**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 워터마크 이미지의 종횡비가 제품 이미지와 일치하지 않을 때 제품 썸네일 이미지가 상점 앞에 표시되지 않는 문제를 해결했습니다.
* **ACSD-47669**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 수정 *무결성 제약 조건 위반: 1452 하위 행을 추가하거나 업데이트할 수 없음: 외래 키 제약 조건이 실패합니다* 제품 CSV를 가져올 때 오류가 발생합니다.
* **ACSD-53347**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 가격 인덱서를 실행하는 데 시간이 너무 오래 걸리는 문제를 해결했습니다.
* **ACSD-52287**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 비동기 그리드 인덱싱이 활성화된 경우 보관된 주문 그리드에서 잘못된 주문 상태가 발생하는 문제를 해결합니다.
* **ACSD-52929**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 인벤토리 인덱서가 비동기 모드로 구성된 경우 기본 소스 항목을 다시 인덱싱하도록 중복 요청으로 문제를 해결합니다.
* **ACSD-53824**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - `setup:upgrade` 동안 `UpdateMultiselectAttributesBackendTypes` 마이그레이션 데이터 패치가 데이터베이스 트랜잭션 크기 제한을 초과하는 문제를 해결합니다.

## v1.1.37 {#v1-1-37}

* **ACSD-52613**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - REST API에서 `Inventory_source` 항목을 업데이트하지 않았더라도 캐시와 색인을 새로 고치는 문제가 수정되었습니다.
* **ACSD-51884**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - resize 명령을 실행한 후 제품 이미지 캐시 경로가 올바르지 않게 되는 문제를 해결합니다.
* **ACSD-53628**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - CSV 판매 주문 보고서에 잘못된 특수 문자가 표시되는 문제가 수정되었습니다.
* **ACSD-53148**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 구성 가능한 동일한 제품을 장바구니에 추가하기 위해 GraphQL에서 두 개의 병렬 요청이 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목을 가져오는 문제를 해결했습니다.
* **ACSD-52606**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 사용자가 **[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;을(를) 클릭하면 *주문이 픽업될 준비가 되지 않았습니다*. 오류 메시지가 표시되는 문제를 수정합니다.
* **ACSD-51574**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 이미지를 같은 이름의 다른 이미지로 바꾼 후 프론트엔드에서 이미지가 업데이트되지 않는 문제를 해결했습니다.
* **ACSD-53728**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제품 EAV 인덱서를 완료하는 데 시간이 더 오래 걸리는 문제를 해결했습니다.
* **ACSD-53979**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 시작 메시지에 작은 따옴표가 포함된 경우 홈페이지에서 발생하는 JS 문제를 수정합니다.
* **ACSD-52085**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 특별 가격이 있는 구성 가능한 제품이 제품 회전판에 표시되지 않는 문제를 해결했습니다.
* **ACSD-53795**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - `indexer_update_all_views` cron 작업에서 데이터 형식이 잘못된 문제를 해결합니다.
* **ACSD-52143**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 제품 가져오기 후 사용자 지정 옵션이 제거되는 문제를 해결했습니다.
* **ACSD-53750**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 다중 스레드 `catalog_product_price` 다시 인덱싱 중 *끊어진 파이프 또는 닫힌 연결* 오류를 수정합니다.
* **ACSD-49843**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) - **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** 설정이 활성화된 상태에서 온라인 결제 방법으로 주문 항목에 자동 송장이 발행된 후 제품 다운로드에서 링크를 사용할 수 없는 문제를 해결합니다.
* **ACSD-47054**(Adobe Commerce >=2.4.2 &lt;2.4.6) - 미리보기 색인 재지정이 모든 스토어에 대해 색인 재지정을 실행하여 속도가 느려지는 문제를 해결했습니다.
* ACSD-46541, ACSD-47079용 새 버전이 추가되었습니다.
* ACSD-49970-v3이 ACSD-54095으로 대체되었습니다.

## v1.1.36 {#v1-1-36}

* **ACSD-53239**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt; 2.4.6의 경우) - 인벤토리 인덱서가 업데이트 시 예약 모드에서 모든 캐시를 정리하는 문제를 해결합니다.
* **ACSD-50887**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - *[!UICONTROL Use in search]* 옵션을 *예*(으)로 설정하지 않고 제품 특성 속성 *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;을(를) *예*(으)로 설정할 수 있는 문제를 해결했습니다.
* **ACSD-51846**(Adobe Commerce 및 Magento Open Source >=2.4.3-p2 &lt;2.4.6) - 모든 수준의 REST API 페이로드의 유효성을 검사하지 않아 발생하는 *내부 오류* 문제를 수정합니다.
* **ACSD-52906**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 동일한 고객 세그먼트에 속하는 로그인한 고객에 대해 X-Pages-Vary 쿠키가 잘못 설정되어 일부 Magento에 대해 부적절한 캐싱을 유발하는 문제를 해결했습니다.
* **ACSD-52736**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 구성 가능한 제품 수량에 대한 요구 사항이 포함된 *장바구니 가격 규칙*&#x200B;이(가) 예상대로 작동하지 않는 문제를 해결했습니다.
* **ACSD-47875**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 재고 관리를 사용하는 특정 스토어 보기 범위에 대해 관리자가 관리에서 고객 장바구니에 제품을 추가할 수 없는 문제를 해결했습니다.
* **ACSD-53176**(Adobe Commerce >=2.3.7 &lt;2.4.5) - *을(를) 가진*&#x200B;관련 제품 규칙&#x200B;*이(가)* 조건 중 하나와 일치하지 않는 문제를 해결했습니다.
* **ACSD-51666**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 오류 수정 *세션이 만료되었습니다. 다시 로그인하십시오.*: 고객이 로그인을 시도한 후에 발생합니다.
* MDVA-39305-v2에 대한 새 버전이 추가되었습니다.
* ACSD-19640에 대한 요구 사항이 업데이트되었습니다.

## v1.1.35 {#v1-1-35}

* **ACSD-51899**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 체크아웃 배송 단계의 기본 배송 주소가 이전에 선택한 매장 픽업 주소로 자동 채워지는 문제를 해결합니다.
* **ACSD-52041**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 오류 메시지: *[오류] [!DNL Page Builder]이(가) 잠금을 해제하지 않고 5초 동안 렌더링되는 문제를 해결했습니다.[!DNL Page Builder](으)로 편집한 콘텐츠를 저장할 때*&#x200B;이(가) Chrome 브라우저에 표시됩니다.
* **ACSD-52095**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 제품 내보내기 후 CSV 파일에서 `manage_stock` 값이 0으로 잘못 설정되는 문제가 해결되었습니다.
* **ACSD-51358**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 종료 날짜 없이 예약된 업데이트를 제거하면 동일한 엔터티에 대해 다른 예약된 업데이트가 제거되는 문제가 해결됩니다.
* **ACSD-48070**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 예약된 업데이트를 편집하면 예외가 트리거되는 문제가 해결됩니다.
* **ACSD-51890**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - [!DNL Google reCAPTCHA] v3 유효성 검사 없이 [!UICONTROL Submit review] 단추를 여러 번 클릭할 수 있는 문제를 해결했습니다.
* **ACSD-51984**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 선택하지 않은 *[!UICONTROL Use Default Value]* 및 *[!UICONTROL non-default product field]* 값이 두 번째 웹 사이트, 스토어 및 스토어 보기에 저장되지 않는 문제를 해결했습니다.
* **ACSD-52398**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류 수정 *요청된 수량을 사용할 수 없습니다*. 이 오류는 상점 앞의 장바구니에 있는 번들 제품의 수량을 업데이트하려고 할 때 발생합니다.
* **ACSD-52786**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 카탈로그 규칙 조건 *SKU is*&#x200B;이(가) 지정된 SKU로 시작하는 모든 제품에 적용되는 문제를 수정합니다.
* **ACSD-52921**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 장바구니에 품절 구성 가능한 제품이 있을 때 GraphQL에서 장바구니 세부 정보를 요청할 때 내부 오류가 발생하는 문제를 수정합니다.
* **ACSD-51683**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 사용자 지정 가능한 옵션을 GraphQL을 사용하여 장바구니에 추가할 수 없는 문제를 해결했습니다.
* **ACSD-52133**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 업그레이드 후 고객 계정을 저장할 수 없는 문제를 해결했습니다.
* **ACSD-52202**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 주문 처리 시 기본값이 아닌 재고가 0으로 변경되면 기본 재고의 판매 가능 수량이 0으로 잘못 변경되는 문제가 해결됩니다.
* **ACSD-51265**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 시스템에 번들 제품이 너무 많을 때 `catalog_product_price` 리인덱싱 성능 문제를 수정합니다.
* **ACSD-52831**(Adobe Commerce >=2.3.7 &lt;2.4.7) - [!DNL Google reCAPTCHA v3 Invisible]이(가) 활성화된 경우 고객이 협상 가능한 견적 주문을 할 수 없는 문제를 수정합니다.
* **ACSD-51845**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 계층 가격과 다른 특성 집합이 있는 후속 제품을 비동기 대량 REST API를 통해 업데이트할 수 없는 문제를 해결했습니다.
* **ACSD-52815**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 기본 재고의 경우 8과 달리, 기본값이 아닌 출처의 수량 필드에 대한 입력이 최대 6자리를 지원하는 문제를 해결했습니다.
* **ACSD-51149**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 카탈로그 권한이 활성화된 예약된 ImportExport가 인덱서를 무효화한 다음 cron의 캐시 플러시를 무효화하는 문제를 해결했습니다.
* **ACSD-50815**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 단순 제품의 10진수를 새 번들 제품 옵션에 사용할 수 없는 문제를 해결했습니다.
* ACSD-47803용 버전이 업데이트되었습니다.
* ACSD-51892의 제목을 업데이트했습니다.
* ACSD-51379이 업데이트되었습니다.
* ACSD-49970-v2를 업데이트했습니다.

## v1.1.34 {#v1-1-34}

* **ACSD-52277**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - Admin에서 새 주문을 만들 때 저장소 보기를 선택한 후 관리자 사용자가 제대로 리디렉션되지 않는 문제를 해결했습니다.
* **ACSD-50813**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 관리자가 SKU에서 [!UICONTROL Add Products by SKU] 기능이 있는 슬래시가 포함된 번들 제품을 관리자 주문에 추가할 수 없는 문제를 해결했습니다.
* **ACSD-51630**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 대량의 시스템 메시지가 관리 페이지 다운로드를 지연시키는 문제를 해결했습니다.
* **ACSD-51853**(Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.7) - [!UICONTROL Page Builder]을(를) 사용할 때 복사된 텍스트 스타일이 적용되지 않는 문제를 해결합니다.
* **ACSD-52160**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - &#39;항목이 발견되거나 이러한 모든 조건 중 하나가 참인 장바구니에서 찾을 수 없는 경우&#39;라는 규칙 조건을 기반으로 장바구니 가격 규칙에 대한 제품 유효성 검사 결과가 제대로 평가되지 않는 문제를 해결했습니다.
* **ACSD-51636**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 필요한 모든 역할과 권한이 있음에도 불구하고 회사 관리자가 고객 계정 섹션에서 새 사용자를 추가할 수 없는 문제를 해결했습니다.
* **ACSD-51739**(Adobe Commerce >=2.4.6 &lt;2.4.7) - CompanyTeam GraphQL 요청에서 `structure_id`이(가) 요청될 때 오류가 반환되는 문제를 수정합니다.
* **ACSD-51857**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 큰 sales_order 및 `sales_order_item` 데이터베이스 테이블에 대한 `aggregate_sales_report_bestsellers_data` cron 보고서의 성능이 느린 이유는 기본 데이터 쿼리가 작성된 방법 때문이었습니다.
* **ACSD-48448**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 주문 취소 중에 경합 조건 문제가 발생하여 `inventory_reservation` 표에 항목이 중복되는 문제를 해결합니다.
* **ACSD-52689**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.6) - REST API를 사용하여 이미지를 Amazon S3 저장소에 업로드할 수 없는 문제를 해결했습니다.
* **B2B-2674**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 1customAttributeMetadata1 GraphQL 쿼리에 캐싱 기능을 추가합니다.
* ACSD-44938용 새 버전이 추가되었습니다.
* ACSD-46988에 대한 요구 사항이 추가되었습니다.

## v1.1.33 {#v1-1-33}

* **ACSD-50478**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5) - DB 덤프에 트리거와 *구분 기호* SQL 명령이 포함된 경우에 대한 데이터베이스 롤백 명령을 수정합니다.
* **ACSD-50512**(Adobe Commerce >=2.4.5 &lt;2.4.7) - 수정 *오류: 다운로드 가능한 링크가 제품과 관련이 없습니다. 링크를 확인하고 다시 시도하십시오.다운로드 가능한 제품 스테이징 업데이트의 시작 날짜를 업데이트할 때 발생하는* 오류입니다.
* **ACSD-50949**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 고급 검색의 가격 필터가 SKU 필터와 함께 사용될 때 적절한 결과를 반환하지 않는 문제를 수정합니다.
* **ACSD-51645**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 확장 `Magento_OfflineShipping`이(가) 비활성화된 경우 새 장바구니 가격 규칙을 저장할 때 발생하는 오류를 수정합니다.
* **ACSD-50895**(Adobe Commerce >=2.4.5 &lt;2.4.7) - [!DNL Google Analytics] 4 GTM이 구성되지 않은 경우 [!DNL Google Analytics] 3 GTM 태그가 실행되지 않는 문제가 해결되었습니다.
* **ACSD-51102**(Adobe Commerce >=2.4.2 &lt;2.4.7) - 예약된 업데이트로 인해 규칙이 활성화될 때 많은 수의 제품에 적용되는 카탈로그 규칙이 올바르게 인덱싱되지 않는 문제를 해결했습니다.
* **ACSD-50368**(Adobe Commerce 및 Magento Open Source >= 2.4.3 &lt;2.4.5) - 비동기 REST API 또는 비동기 벌크 REST API를 통해 고객을 만들 때 고객의 `group_id`이(가) 무시되는 문제를 해결했습니다.
* **ACSD-51497**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - 고객이 드롭다운 유형의 사용자 지정 속성으로 카탈로그 페이지를 정렬할 수 없는 문제를 수정합니다.
* **ACSD-51408**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt; 2.4.7의 경우) - 주문 항목 상태가 *[!UICONTROL Backordered]*(으)로 잘못 설정되는 문제를 해결했습니다.
* **ACSD-51735**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 제품 재고가 *0*&#x200B;일 때 주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정되는 문제가 수정되었습니다.
* **ACSD-51792**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - [!DNL Google Tag Manager] 4를 사용하도록 설정한 경우 페이지에 노출 이벤트가 없는 문제가 해결되었습니다.
* **ACSD-51471**(Adobe Commerce >=2.4.3 &lt;2.4.7) - 관리자가 자체적으로 예약된 업데이트가 있는 간단한 제품을 사용하는 번들 제품에 대해 예약된 업데이트를 저장할 수 없는 문제를 수정합니다.
* **ACSD-51700**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 발생하는 오류를 수정합니다.
* **ACSD-51120**(Adobe Commerce >=2.3.7 &lt;2.4.3) - 스테이징 업데이트를 통해 업데이트된 CMS 블록이 포함된 CMS 페이지에 대해 GraphQL GET 요청 캐시가 지워지지 않는 문제를 해결했습니다.
* **ACSD-51240**(Adobe Commerce >=2.4.4 &lt;2.4.6) - 회사 등록 양식을 통해 등록한 경우 업로드된 파일이 없는 문제를 수정합니다.
* **ACSD-51907**(Adobe Commerce >=2.4.2 &lt;2.4.3) - 제한된 관리자가 오프라인 환급으로 대변 메모를 만들 수 없는 문제를 해결했습니다.
* **ACSD-52148**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4) - [!DNL Google V3 reCAPTCHA] 관리자 로그인이 가끔 실패하는 문제를 해결합니다.
* **ACSD-51431**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 변경 로그에 새 항목이 없어도 인덱서 상태가 *작업*&#x200B;인 문제를 해결합니다.
* **ACSD-51892**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 구성 파일이 여러 번 로드되는 성능 문제를 해결했습니다.
* 사용되지 않는 ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - [!UICONTROL Page Builder's] 오류가 여러 개 발생하여 관리자가 콘텐츠 권한 없이 제품을 저장할 수 없는 문제를 해결했습니다.
* **ACSD-51305**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - GraphQL 응답에서 품절 구성 가능한 하위 제품을 사용할 수 없는 문제를 해결했습니다.
* **ACSD-50621**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 다중 웹 사이트 환경에서 편집하려고 할 때 공유 카탈로그의 다른 웹 사이트에 대한 [!UICONTROL Tier Prices]이(가) 표시되지 않는 문제를 해결했습니다.
* **ACSD-51041**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) - 가격 인덱서의 성능이 향상됩니다.
* **ACSD-51379**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - [!UICONTROL Page Builder]을(를) 통해 페이지 텍스트 콘텐츠에 대한 변경 사항이 저장되지 않는 문제를 해결했습니다.
* **ACSD-49480**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 장바구니에 하나의 장바구니 가격 규칙만 적용되는 문제가 해결되었습니다.
* **ACSD-51230**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 주문에서 간단한 제품의 일부 환불이 처리되는 경우 기프트 카드 계정이 삭제되는 문제를 해결했습니다.
* **ACSD-51238**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 구성 가능한 제품을 업데이트하고 가격을 편집할 때 인벤토리 소스가 제거되는 문제를 해결합니다.
* **ACSD-50794**(Adobe Commerce >=2.4.1 &lt;2.4.7) - GraphQL을 통해 제거할 때 선물 메시지 또는 선물 포장 세부 사항이 데이터베이스에서 업데이트되지 않는 문제를 해결했습니다.
* **ACSD-51528**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - *sales_order* 테이블에서 *x_forwarded_for* 열에 null 값이 있는 문제를 해결했습니다.
* **ACSD-50849**(Adobe Commerce >=2.4.4 &lt;2.4.6) - 캐시를 지운 후 새 제품을 범주에 추가하면 기존 제품의 위치와 선택이 일치하지 않는 문제가 해결됩니다.
* **ACSD-51294**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - GTM/GA 가격, 수량, 세금, 배송 및 수익이 문자열로 [!DNL Google Analytics] 및 GTM에 전송되는 문제를 해결합니다.
* **ACSD-51204**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 대변 메모를 만든 후 완전히 판매된 제품이 재고로 반환되지 않는 문제를 해결했습니다.
* **ACSD-51291**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.4-p4) || >=2.4.5 &lt;2.4.5-p3) - 한 웹 사이트에 대한 액세스 권한이 있는 제한된 관리자가 여러 웹 사이트에 할당된 제품에 이미지/비디오를 추가할 수 있는 문제를 해결했습니다.
* ACSD-50336용 새 버전이 추가되었습니다.
* ACSD-49970 패치를 교체했습니다.

## v1.1.31 {#v1-1-31}

* **ACSD-50345**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - 실패한 지급을 제출한 후 Recaptcha v2가 다시 로드되지 않는 문제를 수정합니다.
* **ACSD-50817**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - Cron 작업 `sales_clean_quotes`을(를) 최적화하여 더 빠르게 실행합니다.
* **ACSD-49392**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - 번들 제품에 대한 부분 환불 후 주문 상태가 마감으로 변경되는 문제를 수정합니다.
* **ACSD-51036**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 동시 REST API 호출 중 경합 조건으로 인해 [!UICONTROL Items Ordered] 테이블의 배송 상태 정보가 덮어쓰기되는 문제가 수정되었습니다.
* **ACSD-50858**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - 배너 콘텐츠 로드 성능을 개선합니다.
* MDVA-39305-v2, ACSD-45169용 새 버전이 추가되었습니다.
* 패치 ACSD-50260-v2를 업데이트했습니다.

## v1.1.30 {#v1-1-30}

* **ACSD-50336**(Adobe Commerce 및 Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - 제품이 재입고되거나 가격이 변경될 때 제품 경고 이메일이 전송되지 않는 문제를 수정합니다.
* **ACSD-50367**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 값이 없는 다중 선택 고객 주소 특성을 만들 때 고객 주소 내보내기가 작동하지 않는 문제를 수정합니다.
* **ACSD-49877**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 비디오가 스트리밍 서비스가 아닌 원격 비디오 파일에 직접 연결된 경우 모바일 [!DNL Safari]에서 비디오 자동 재생이 작동하지 않는 문제를 해결했습니다.
* **ACSD-50165**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 오류 *파일을 삭제할 수 없습니다. 경고!unlink: 관리자에서 JS/CSS 캐시를 플러시할 때 해당 파일 또는 디렉터리*&#x200B;이(가) 없습니다.
* **ACSD-49737**(Adobe Commerce 및 Magento Open Source >=2.4.1-p1 &lt;2.4.7) - 카드 결제가 실패한 후 쿠폰이 사용된 것으로 잘못 표시되는 문제를 해결했습니다.
* **ACSD-50814**(Adobe Commerce 및 Magento Open Source >=2.4.6 &lt;2.4.7) - 관리 사용자가 대변 메모를 만들 수 없는 문제를 해결했습니다.
* **ACSD-50116**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 관리 사용자가 하위 범주 레벨 3 이하에 대해 URL 다시 쓰기를 만들 수 없는 문제를 해결합니다.
* **ACSD-49513**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5) - 0바이트 파일로 인해 원격 저장소 동기화가 실패하는 문제를 해결했습니다.
* **ACSD-46683**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 배송 가격에 *아직 계산되지 않음*&#x200B;이 표시되는 문제를 해결했습니다.
* **ACSD-49129**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - `rest/V1/products/sku/media` 제품 미디어 API 응답에서 *[!UICONTROL content]* 특성(base64 이미지 코드)이 반환되지 않는 문제를 수정합니다.
* **ACSD-50276**(Adobe Commerce >=2.4.0 &lt;2.4.7) - 다중 선택 고객 특성이 만들어지는 경우 고객 등록 양식이 상점 앞에서 작동하지 않는 문제를 수정합니다.
* **ACSD-50527**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 빈 동적 블록으로 페이지를 저장할 때 발생하는 오류를 수정합니다.
* **ACSD-49973**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - GraphQL을 통해 번들 제품을 가져오는 성능을 개선합니다.
* **ACSD-51114**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 비동기 인덱싱이 활성화되면 무작위 제품이 큰 카탈로그에서 사라지는 문제를 해결합니다. 대규모 카탈로그에 대한 비동기 리인덱싱의 성능을 향상시킵니다.
* **B2B-2598**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.7) - [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] 및 [!UICONTROL storeConfig] GraphQL 쿼리에 캐싱 기능을 추가합니다.
* MDVA-42806, ACSD-48627, ACSD-46815에 대한 새 버전이 추가되었습니다.
* ACSD-49773, ACSD-47179, ACSD-48300에 대한 패치 메타데이터가 업데이트되었습니다.

## v1.1.29 {#v1-1-29}

* **ACSD-49389**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.7) - 주문이 픽업될 준비가 되지 않은 경우 API에서 픽업 준비 이메일을 보내는 문제를 수정합니다.
* **ACSD-49822**(Adobe Commerce >=2.3.7 &lt;2.4.7) - [!UICONTROL Requisition List] 페이지의 업데이트가 [!UICONTROL Print Requisition List]에 반영되지 않는 문제를 해결했습니다.
* **ACSD-48771**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 이전 [!DNL Page Builder] 버전에서 열 차단 콘텐츠 형식을 업그레이드할 때 발생하는 문제를 해결합니다.
* **ACSD-49464**(Adobe Commerce >=2.3.7 &lt;2.4.7) - orderId가 다른 경우 송장, 선적 및 대변 메모가 보관 위치에서 다시 이동되지 않는 문제를 수정합니다.
* **ACSD-49773**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - AWS S3을 원격 저장소로 사용할 때 제품 내보내기가 실패하는 문제를 수정합니다.
* **ACSD-49748**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 초대를 보낼 수 없는 문제를 해결했습니다.
* **ACSD-49502**(Adobe Commerce >=2.4.3 &lt;2.4.7) - 스테이징 업데이트가 다운로드 가능한 제품에 적용된 후 다운로드 가능한 링크가 제대로 업데이트되지 않는 문제를 해결합니다.
* **ACSD-49527**(Adobe Commerce >=2.4.2 &lt;2.4.7) - GraphQL 회사 역할이 페이지 매김을 올바르게 표시하지 않는 문제를 해결했습니다.
* **ACSD-49706**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 값을 선택하지 않으면 시각적 견본 특성에 대해 기본값이 저장되는 문제가 해결됩니다.
* **ACSD-49835**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 다중 선택 특성에 대한 저장소 수준에서 기본값 사용 확인란이 올바르게 저장되지 않는 문제를 해결했습니다.
* **ACSD-49898**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 번들 제품에 1,000을 초과하는 특별 가격이 있을 때 제품 그리드에서 예외가 발생하는 문제를 해결합니다.
* **ACSD-50234**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.5) - [!DNL PayPal]에 주문을 하면 확인 이메일에서 잘못된 고객 이름 문제를 수정합니다.
* **ACSD-49960**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 고객 주문 그리드에 대해 날짜별 필터링이 작동하지 않는 문제를 수정합니다.
* **ACSD-49849**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - GraphQL을 통해 [!DNL PayPal Express]을(를) 주문할 때 고객 이메일이 [!DNL PayPal] 이메일로 대체되는 문제를 해결했습니다.
* **ACSD-49839**(Adobe Commerce >=2.3.7 &lt;2.4.7) - SKU에서 제품에 작은따옴표나 큰따옴표가 있을 때 공유 카탈로그 가격 및 구조에서 관리자에게 오류가 발생하는 문제를 수정합니다.
* **ACSD-49970**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - [!DNL New Relic] 보고가 켜져 있을 때 GraphQL 오류에 대한 잘못된 처리가 수정되었습니다.
* **ACSD-50260**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - GraphQL 제품 검색 결과가 10,000개의 결과로만 제한되는 문제를 해결했습니다.
* **ACSD-48813**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 검색 시 특성의 검색 가중치에 따라 관련 결과가 표시되지 않는 문제를 수정합니다.

## v1.1.28 {#v1-1-28}

* **ACSD-48204**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.3) - 예/아니요 특성을 기반으로 만들어진 카탈로그 가격 규칙이 선택한 범위를 고려하지 않는 문제를 해결했습니다.
* **ACSD-47704**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 번들 제품에 재고 제품의 가격만 표시되는 문제가 해결되었습니다.
* **ACSD-49370**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - *날짜 시간* 제품 특성에 GraphQL 스키마의 *FilterMatchTypeInput* 유형이 있는 문제를 해결했습니다.
* **ACSD-48807**(Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.7) - 고객 제품 검토가 GraphQL을 통해 스토어뷰로 필터링되지 않는 문제를 해결했습니다.
* **ACSD-49433**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 금액이 미결인 기프트 카드용 장바구니에서 기본 금액이 소계로 표시되는 문제를 해결했습니다.
* **ACSD-48866**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 범주에 대한 RSS 피드를 요청할 때 오류가 발생하는 문제를 해결합니다.
* **ACSD-48784**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시되는 문제를 수정합니다.
* **ACSD-48857**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - Page Builder로 편집한 후 사용자가 변경 사항을 저장할 수 없는 문제를 해결합니다.
* **ACSD-49065**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 사용자 지정 주식에만 할당된 경우 관리자에 견적 항목이 표시되지 않는 문제를 해결했습니다.
* **ACSD-49179**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 서로 다른 스토어에 대해 통화가 다를 경우 주문 보고서에 잘못된 금액이 표시되는 문제를 해결했습니다.
* **ACSD-49286**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 페이지에 여러 제품 위젯이 있을 때 제품이 장바구니에 두 번 추가되는 문제를 수정합니다.
* **ACSD-49574**(Adobe Commerce >=2.4.4 &lt;2.4.7) - GraphQL을 통해 장바구니에서 기프트 카드 제품 업데이트를 지원하는 기능을 추가합니다.
* 업데이트된 패치: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362**(Adobe Commerce >=2.4.1 &lt;2.4.7) - 협상 가능 견적을 사용하여 주문할 때 새 주소 대신 기본 배송 주소가 사용되는 문제를 해결했습니다.
* **ACSD-48059**(Adobe Commerce >=2.3.7 &lt;2.4.7) - 판매자가 범주의 &quot;[!UICONTROL Match product by rule]&quot;을(를) 저장할 수 없는 문제를 해결했습니다.
* **ACSD-48216**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - [!UICONTROL UPDATE] 작업에서 [!UICONTROL inventory_source_item] 테이블의 [!UICONTROL AUTO_INCREMENT]이(가) 증가하는 문제를 해결했습니다.
* **ACSD-47908**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - 체크아웃 중에 배송 단계에서 소스 및 수량을 선택할 때 &quot;0보다 작거나 같은 값이 예상됩니다.&quot; 오류가 수정되었습니다.
* **ACSD-49497**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 주문이 선적 후 처리 상태에 남아 있고 부분 환불이 적용되는 문제를 해결합니다.
* **ACSD-48694**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) - &quot;잘못된 상태 변경 요청됨&quot; 오류로 인해 고객이 주문을 할 수 없는 문제가 해결되었습니다.
* **ACSD-49013**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.7) - 벌크 API를 사용하여 고객을 만들 때 전자 메일 확인이 웹 사이트 로케일로 번역되지 않는 문제를 해결했습니다.
* **ACSD-48164**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제한된 관리자가 웹 사이트 수준 값을 저장할 수 없는 문제를 해결했습니다.
* **ACSD-48404**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4의 경우) - &quot;범주 페이지 매김 저장 = 예&quot;가 브라우저의 뒤로 단추를 누를 때 오류가 발생하는 문제를 해결했습니다.
* **ACSD-48634**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - &quot;[!UICONTROL Google Analytics Content Experiments]&quot;이(가) 활성화되면 스테이징 업데이트 페이지에서 JS 오류가 수정됩니다.
* **ACSD-49042**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - 하위 순서가 무한한 제품을 상점 앞에서 주문할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937**(Adobe Commerce 및 Magento Open Source 2.4.4용) || >=2.4.5 &lt;2.4.6) - 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 항상 전송되지 않는 문제를 해결합니다.
* **ACSD-48661**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 회사의 크레딧 제한이 999보다 큰 경우 쉼표 구분 기호로 인해 유효성 검사 오류로 인해 회사가 저장되지 않는 문제를 해결합니다.
* **ACSD-48773**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.7) - 보상 포인트 전자 메일 템플릿을 잘못된 저장소에서 가져오는 문제를 수정합니다.
* **ACSD-48587**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.7) - 제품 위젯 일치 규칙의 HTML 특수 문자가 일치하는 제품을 표시하지 못하는 문제를 해결합니다.
* **ACSD-48212**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 제품 가져오기에서 제품을 잘못된 소스에 할당하는 문제를 해결합니다.
* **ACSD-47988**(Adobe Commerce 및 Magento Open Source >=2.3.7 &lt;2.4.6) - 제품 내보내기가 페이지 빌더 제품 설명의 HTML 태그를 트리밍하는 문제를 수정합니다.
* **ACSD-48366**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 제품 이미지가 주식형 전자 메일 서식 파일에 표시되지 않는 문제를 해결했습니다.
* **ACSD-48417**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.7) - 제품에 대한 일정 변경을 만들고 다른 제품을 저장한 후 SQL 오류가 표시되는 문제를 해결합니다.

## v1.1.25 {#v1-1-25}

* **ACSD-48058**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 번들 제품이 웹 사이트에 할당되지 않은 경우 제품 가격 리색인이 작동하지 않는 문제를 수정합니다.
* **ACSD-48262**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - &quot;Allow All Products Per Page&quot; 설정이 Yes로 설정되어 있을 때 프론트엔드에 제품이 표시되지 않는 문제를 해결했습니다.
* **ACSD-48293**(Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4)의 경우) - 품절된 하위 제품이 재고로 반환될 때 복합 제품이 품절되는 문제를 수정합니다.
* **ACSD-47520**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 대변 메모가 생성될 때 고객이 보상 포인트를 잃는 문제를 해결했습니다.
* **ACSD-48044**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4)의 경우) - 여러 상품권을 다중 배송을 통해 단일 주문에 적용하면 주문이 이루어지지 않는 문제를 해결합니다.
* **ACSD-48300**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 구성 가능한 제품이 제거될 경우 반환을 만들 수 없는 문제를 해결했습니다.
* **ACSD-47910**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 각 엔터티 그리드에서 주문, 송장, 배송 및 대변 메모가 누락되는 문제를 수정합니다.
* **ACSD-47292**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - &quot;재고 부족 제품 표시&quot;가 [예]로 설정된 경우 GraphQL 응답에서 재고 부족 번들 제품을 사용할 수 없는 문제를 수정합니다.
* **ACSD-48234**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - &quot;재고 부족&quot; 옵션이 활성화된 경우 카탈로그 검색 결과에 잘못된 범주 항목 수가 표시되는 문제를 해결합니다.
* **ACSD-48313**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5) - 특성 값에 쉼표가 포함되어 있으면 &quot;configurable_variations&quot; 열이 구문 분석되지 않는 문제를 해결합니다. &quot;additional_attributes&quot;에도 동일한 구문 분석 알고리즘이 사용됩니다.
* **ACSD-48627**(Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6) - 장바구니 세부 정보를 가져오기 위해 GraphQL 요청을 보낼 때 품절 구성 가능한 제품으로 인해 오류가 발생하는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 스토어-뷰 수준에서 *url_key* 특성이 재정의된 제품에 대해 SEO용 URL이 생성되지 않는 문제가 수정되었습니다.
* **ACSD-46865**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 비동기 인덱싱이 활성화된 경우 배달 및 대변 메모 그리드가 채워지지 않는 문제가 해결되었습니다.
* **ACSD-47004**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - VAT ID가 없는 청구 주소에 VAT가 적용되지 않는 문제를 해결했습니다.
* **ACSD-47803**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 품절 구성 가능한 제품 견본이 사용 가능한 것으로 표시되는 문제를 수정합니다.
* **ACSD-47137**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - pub/media 폴더가 매우 클 때 이미지 갤러리의 로드 속도를 개선합니다.
* **ACSD-46770**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - *전자 메일 주문 확인*&#x200B;을 선택하지 않아도 관리자 주문 전자 메일이 전송되는 문제가 해결되었습니다.
* **ACSD-47955**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - GraphQL에서 장바구니 할인을 올바르게 표시하지 않는 문제를 해결했습니다.
* **ACSD-46617**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 소계가 구성된 *최소 주문 양*&#x200B;보다 크더라도 *체크아웃 계속* 단추가 회색으로 표시되는 문제를 해결했습니다.
* **ACSD-47079**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5) - REST API POST /rest/V1/inventory/source-items를 통해 하위 제품 재고 상태가 변경되면 복합 제품(번들, 그룹화 및 구성 가능) 재고 상태가 업데이트되지 않는 문제를 수정합니다.
* **ACSD-47336**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 수정 *문제가 발생했습니다.Commerce 관리자의 알림을 해제할 때* 오류가 발생했습니다.
* **ACSD-47559**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 미리 보기 전자 메일 템플릿 영역이 완전히 표시되지 않는 문제를 해결했습니다.
* **ACSD-47920**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - *게스트 체크아웃 허용*&#x200B;이 꺼져 있더라도 Rest API를 통해 게스트 사용자로 주문을 할 수 있는 문제를 해결했습니다.
* 교체된 패치: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 특정 범위에 대한 액세스 권한이 제한된 관리자가 제품 검토를 삭제할 수 없는 문제를 해결했습니다.
* **ACSD-47107**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5) - 카탈로그 가격 규칙 할인이 사용자 지정 제품 옵션에 적용되는 문제를 해결했습니다.
* **ACSD-47232**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 총 가중치 조건이 있는 쿠폰을 관리자에서 적용할 수 없는 문제를 해결했습니다.
* **ACSD-46519**(Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.6) - GraphQL categoryList 요청이 앵커 범주에 대해 잘못된 product_count를 반환하는 문제를 수정합니다.
* **ACSD-47027**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 느린 updateCompanyRole GraphQL 요청을 수정합니다.
* **ACSD-47666**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 관리자 > 시스템 > 권한 > 사용자 역할 > 역할 > 역할 사용자 그리드에서 필터 기능이 작동하지 않는 문제를 수정합니다.
* **ACSD-47497**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 관리 아래의 구성에 서비스 탭이 표시되지 않는 문제를 해결합니다.
* 업데이트된 패치: ACSD-47743.
* 교체된 패치: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.3) - PHP 7.4의 알려진 제품에 대한 일부 존재하지 않는 범주 경로에 액세스할 때 _유형 부울 값에 대한 배열 오프셋에 액세스하려고 시도_ 오류가 수정되었습니다.
* **ACSD-47332**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 00:00과 00:59 UTC 사이에서 실행할 때만 보고되는 오류와 함께 cron이 실패하는 문제를 수정합니다.
* **ACSD-47280**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 특정 범위에서 공유 카탈로그 기능을 사용하지 않도록 설정할 수 없는 문제가 해결되었습니다.
* **ACSD-47106**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - 회사 만들기 페이지의 새 사용자 지정 특성에 값을 저장할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6) - 많은 수의 제품 소스를 할당할 때 사용자에게 오류가 발생하는 문제를 수정합니다.
* **ACSD-46856**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 시스템 > 구성 > 가져오기 > 고급 가격을 통해 계층 가격 업데이트 성능을 개선합니다.
* **ACSD-46541**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4)의 경우) - 주문 항목이 삭제될 경우 관리자가 대변 메모를 만들 수 없는 문제를 해결했습니다.
* **ACSD-46581**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 장바구니에서 국가를 선택한 후 예상 총 세액이 업데이트되지 않는 문제를 수정합니다.
* **ACSD-46618**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 제품 목록 위젯에서 로그인한 고객에 대해 잘못된 캐시 가격이 표시되는 문제를 수정합니다.
* **ACSD-46674**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - 고객 이메일에서 이미지 유형의 사용자 지정 옵션이 HTML으로 표시되는 문제를 해결했습니다.
* **ACSD-46988**(Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6) - GraphQL &#39;currency&#39; API 요청이 사용자 지정 통화에 대해 NULL 값을 반환하는 문제를 수정합니다.
* **ACSD-47076**(Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5) - 상점 전면에서 Vimeo 비디오를 재생할 수 없는 문제를 해결했습니다.
* **ACSD-45071**(Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4) - 가져오는 동안 기본 소스가 제품에 추가되는 문제를 수정합니다.
* **AC-3023**(Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6) - DHL 구성표를 최신 버전 10.0으로 업데이트합니다.
* 업데이트된 패치: MDVA-42584.
* 교체된 패치: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5*) - 스토어 크레딧을 사용하여 환불할 때 사용자가 잘못된 주문 상태를 받는 문제를 수정합니다.
* **ACSD-46703**(*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6*) - 제품 편집 페이지에서 사용자 지정 옵션을 끌어서 놓을 수 없는 문제를 해결했습니다.
* **ACSD-44851**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6*) - 하위 범주가 있는 범주를 열거나 확장할 수 없는 문제를 해결했습니다.
* **ACSD-46815**(*Adobe Commerce 및 Magento Open Source >=2.4.5 &lt;2.4.6*) - 범주 트리 요청이 20개 범주로 제한되는 문제를 해결했습니다.
* **ACSD-45675**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.6*) - 제품 내보내기에서 *기본 스토어 보기* 범위의 카테고리 이름을 사용하는 문제를 해결했습니다.
* **ACSD-46869**(*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.6*) - 제품 수량을 변경하지 않고 장바구니에서 구성 가능한 제품이 *REST API PUT* 요청을 통해 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-42768-V2**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - *Display Out-of-Stock*&#x200B;이(가) *Yes*&#x200B;일 때 구성 가능한 제품에 *0*(으)로 정가가 표시되는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* 사용되지 않는 패치: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 범주 트리 요청이 20개의 범주로 제한되는 문제를 해결했습니다.
* **ACSD-45781**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.2*) - 스토어 전면 검색 필드가 모바일에 표시되지 않는 문제를 수정합니다.
* **ACSD-46192**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;2.4.5*) - `async/bulk/V1/configurable-products/bySku/options` 끝점 사용 관련 문제를 수정합니다.
* **ACSD-46404**(*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5*) - 2.4.4로 업그레이드한 후 관리자 사용자가 로그인할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 특정 저장소에 대한 GraphQL 제품 변형이 요청된 저장소에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환하는 문제를 해결합니다.
* **ACSD-46146**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.6*) - 관리자의 주문을 받은 후 두 개의 주문 확인 전자 메일이 전송되는 문제가 해결되었습니다.
* **ACSD-45255**(*Adobe Commerce >=2.4.3 &lt;2.4.6*) - 제한된 관리자의 낮은 재고 보고서 페이지에서 예외를 수정합니다.
* **ACSD-45488**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.6*) - 여러 소스를 사용하는 구성 가능한 제품이 자동으로 In Stock에 반환되지 않는 문제를 해결했습니다.
* **ACSD-45754**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.6*) - 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 해결했습니다.
* **ACSD-45849**(*Adobe Commerce >=2.4.3 &lt;2.4.4*&#x200B;의 경우) - 스테이징 업데이트가 적용된 후 비디오 메타데이터가 손실되는 문제를 해결했습니다.
* **ACSD-45257**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.4*) - GraphQL에서 장바구니 할인을 올바르게 표시하지 않는 문제를 해결했습니다.
* **ACSD-44938**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4*) - 게스트 사용자에 대한 GraphQL 요청에서 `VAT_ID`을(를) 적용할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.4.4*) - 대변 메모를 만든 후 가상 제품에 대한 재고 수량이 잘못 계산되는 문제를 해결했습니다.
* **ACSD-43887**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - 회사 구매 발주가 활성화되면 체크아웃 결제 페이지에 잘못된 세부 정보가 표시되는 문제를 수정합니다.
* **ACSD-45143**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5*) - `setShippingAddressesOnCart` 돌연변이로 인해 숫자 영역 코드를 *region*(으)로 설정할 수 없는 문제가 해결되었습니다.
* **ACSD-44591**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.6*) - CAPTCHA 확인 없이 주문을 할 때 발생하는 오류를 수정합니다.
* **ACSD-45520**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.6*) - 사용자가 장바구니에서 구성 가능한 제품을 편집할 때 제품 세부 사항 페이지에서 견본 옵션이 미리 선택되지 않는 문제를 수정합니다.
* **ACSD-45169**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.6*) - 스테이징 업데이트가 적용된 후 [!DNL Visual Merchandiser]에 구성 가능한 제품에 대한 올바른 주식과 가격이 표시되지 않는 문제가 해결되었습니다.
* **ACSD-45424**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.6*) - 부분 환불 후 잘못된 예약 보상이 만들어지는 문제를 해결했습니다(대변 메모).
* **MDVA-42807**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.6*) - 사용자 지정 통화 기호가 상점 앞에 표시되지 않는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 제한된 관리자에 대해 주문 보고서의 주문 합계가 잘못 계산되는 문제를 해결했습니다.
* **MDVA-44940**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*&#x200B;의 경우) - 관리자의 범주를 저장하는 동안 발생하는 SQL 오류를 수정합니다.
* **MDVA-44562**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - 비기본 스토어 보기에서 시작된 GraphQL 요청에도 불구하고 견적 항목에 대한 비기본 스토어 id가 기본 스토어 id로 재정의되는 문제를 해결합니다.
* **MDVA-43167**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 관리자가 모든 주문을 선택할 때 관리자 주문 그리드 일괄 작업이 다중 페이지에 적용되지 않는 문제를 해결했습니다.
* **MDVA-44044**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 해결했습니다.
* **MDVA-42509**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.4*) - 빠른 주문에 대해 CSV를 업로드할 수 없어 *쿠키를 보낼 수 없음* 오류가 발생하는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-41061, MDVA-42584.
* 내부 프로세스 변경으로 인해 새 [!DNL Quality Patches Tool] 패치의 접두사가 *MDVA*&#x200B;에서 *ACSD*(으)로 변경됩니다.

## v1.1.15 {#v1-1-15}

* **MDVA-40961**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 항목의 최소 수량이 장바구니에 이미 있는 경우 장바구니에 추가 항목을 추가할 수 없는 문제를 해결했습니다.
* **MDVA-44887**(*Adobe Commerce 및 Magento Open Source >=2.4.4 &lt;2.4.5*&#x200B;의 경우) - *발견되지 않은 구문 오류를 수정합니다.오류: 관리 패널에서 예기치 않은 토큰 &#39;const&#39;* 오류가 발생했습니다.
* **MDVA-43718**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 수정 사항 *소비자가 %resources에 액세스할 수 있는 권한이 없습니다.사용자 지정 통합에서 공유 카탈로그에 액세스할 때 표시되는* 오류입니다.
* **MDVA-44660**(*Adobe Commerce 및 Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - 고객의 이름과 성에 그레이브 악센트 문자 ``` ` ```을(를) 사용할 수 없는 문제를 해결했습니다.
* **MDVA-40896**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*&#x200B;의 경우) - 비동기 제품 벌크 API에서 *오류: TypeError: 인수 3이 Magento에 전달됨* 오류가 수정되었습니다.
* **MDVA-38559**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.3*) - 둘 이상의 구독을 가진 고객의 */V1/customers/search API* 오류를 수정합니다.
* **MDVA-44533**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.4*) - 번들 하위 제품에 할인이 잘못 적용되는 문제가 수정되었습니다.
* 업데이트된 패치: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - 제품 *개별적으로 표시되지 않음*&#x200B;이 여전히 카탈로그 고급 검색 결과에 표시되는 문제를 해결했습니다.
* **MDVA-44100**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 모든 FPT가 장바구니의 마지막 제품에 할당되고 다른 제품에 대해 재설정되는 문제를 해결했습니다.
* **MDVA-43605**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.5*) - Rest API를 사용할 때 주문 데이터가 행 합계에 대해 음수 값을 반환하는 문제를 해결했습니다.
* **MDVA-43102**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;2.4.5*) - REST API를 통해 환불을 수행하면 판매 가능 수량이 올바르게 업데이트되지 않는 문제가 수정되었습니다.
* **MDVA-43178**(*Adobe Commerce 및 Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - 사용자 지정 저장소에 대한 고객 토큰을 GraphQL에서 검색할 수 없는 문제를 해결했습니다.
* **MDVA-43859**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 삭제된 고객이 로그인을 시도할 때 *customerId =*&#x200B;인 해당 엔터티가 기록되지 않는 문제를 해결했습니다.
* **MDVA-44147**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - GraphQL 요청이 구매요청 목록을 반환하지 않는 문제를 해결했습니다.
* **MDVA-44505**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - GraphQL 적용 보상 포인트가 총계를 업데이트하지 않고 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - 고객 세그먼트가 *모두*(으)로 설정된 경우에만 관련 제품 규칙이 작동하는 문제가 해결되었습니다.
* **MDVA-39605**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.5*) - Redis 캐시 TTL(만료 날짜)에 잘못된 값이 있는 문제를 해결했습니다.
* **MDVA-43862**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.5*) - GraphQL *UpdateCartItems 돌연변이* 오류로 인해 고객이 장바구니 항목을 업데이트할 수 없는 문제를 해결했습니다.
* **MDVA-43824**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p3) || >=2.4.1 &lt;2.4.5*) - 할인을 적용한 주문 취소 시 오류가 발생하는 문제를 수정합니다.
* **MDVA-43451**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 오류 *요청한 스토어를 찾을 수 없는 문제를 해결했습니다. 스토어를 확인하고 다시 시도하십시오.특정 웹 사이트에 대한 공유 카탈로그를 구성하는 동안*&#x200B;이(가) 나타납니다.
* **MDVA-43491**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.4.5*) - 다중 스토어 웹 사이트에 대한 제품을 가져올 때 기본 이미지 레이블이 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-43601**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 전체 다시 인덱싱 후 트리거가 누락된 문제를 해결합니다.
* **MDVA-42046**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - 제품을 업데이트하는 동안 날짜 입력 필드가 있는 제품 특성에 잘못된 값이 지정되는 문제를 수정합니다.
* **MDVA-43935**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 업셀 제품이 두 번 표시되는 문제를 해결했습니다.
* **MDVA-44188**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 주소에 `.-`이(가) 있는 시스템에서 발급한 전자 메일이 전송되지 않는 문제를 해결했습니다.
* **MDVA-42283**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 프랑스어 로케일에 대한 관리 순서 그리드의 날짜-시간 형식이 잘못된 문제를 수정합니다.
* 업데이트된 패치: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* [!DNL Site-Wide Analysis Tool]에 대한 패치 메타데이터를 추가했습니다.

## v1.1.12 {#v1-1-12}

* **MDVA-39713**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.3.6*) - 사용자가 활성 예약 업데이트의 시작 시간을 편집할 수 있는 문제를 해결했습니다.
* **MDVA-42410**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 쿠폰 보고서에 기본 통화만 표시되는 문제를 해결했습니다.
* **MDVA-41136**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - `mage-cache-sessid`의 만료 날짜가 연장되지 않아 고객 데이터가 정리되는 문제를 해결했습니다.
* **MDVA-39993**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - API를 통해 수행된 인벤토리 변경이 프론트엔드의 제품 페이지에 반영되지 않는 문제를 수정합니다.
* **MDVA-42855**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 체크아웃 중에 새 고객 주소가 주소록에 저장되지 않는 문제를 해결했습니다.
* **MDVA-42645**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 저장소 크레딧 기능을 사용하지 않도록 설정한 경우 관리자가 보상 포인트를 환불할 수 없는 문제를 해결했습니다.
* **MDVA-43414**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2*&#x200B;의 경우) - 숫자 SKU에서 `inventory.reservations.updateSalabilityStatus` 큐 소비자를 실행할 때 발생하는 PHP 치명적인 오류를 수정합니다.
* **MDVA-41628**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.5*) - 새 모듈을 추가할 때 기존의 제한된 관리 사용자가 새 리소스에 액세스할 수 있는 문제를 해결했습니다.
* **MDVA-43348**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - `gift_card_options`에 *uid*&#x200B;이(가) 포함된 경우 기프트 카드 GraphQL 요청에 오류가 표시되는 문제를 해결했습니다.
* **MDVA-39546**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 스테이징 업데이트 시작 날짜를 편집하는 동안 현재 날짜보다 이전 날짜로 설정할 수 있는 문제를 해결했습니다.
* **MDVA-42950**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 제품 페이지에서 비디오가 재생되지 않는 문제를 해결했습니다.
* **MDVA-42689**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 가져오는 동안 제품 범주를 업데이트하는 동안 Adobe Commerce에서 *무결성 제약 조건 위반* 오류가 발생하는 문제를 해결했습니다.
* **MDVA-41229**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 구성 가능한 제품을 가져온 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않는 문제를 해결했습니다.
* **MDVA-43731**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - *일치하는 최소 용어*&#x200B;에 값을 추가할 때 *동의어 검색*&#x200B;이(가) 더 이상 작동하지 않는 문제를 해결했습니다.
* **MDVA-43232**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.5*) - [!DNL Visual Merchandiser]의 제품을 하위/최상위 가격으로 정렬하면 범주를 저장하는 동안 오류가 발생하는 문제를 해결했습니다.
* **MDVA-43726**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.3*) - 부분 색인 재지정 후 저장소 수준 특성 일치를 기반으로 하는 카탈로그 가격 규칙이 적용되지 않는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-36464, MDVA-37478, MDVA-38608.
* [!DNL Site-Wide Analysis Tool]에 대한 패치 메타데이터를 추가했습니다.

## v1.1.11 {#v1-1-11}

* **MDVA-42790**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - REST API를 통해 특정 웹 사이트에 대해 제품 가격 특성을 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-41350**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 제한된 액세스 권한을 가진 관리자가 SKU로 역할 범위를 벗어난 제품을 순서대로 추가할 때 예외가 발생하는 문제를 해결했습니다.
* **MDVA-42269**(*Adobe Commerce 및 Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - *TypeError: strtotime() 매개 변수 1이 문자열이어야 하는데 null이 주어지면* 오류가 발생하여 관리자가 관리자에 로그인할 수 없는 문제가 해결되었습니다.
* **MDVA-40830**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 스토어 크레딧이 주문 배치 중에 여러 번 적용되는 문제를 해결했습니다.
* **MDVA-42237**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - 하위 제품 가격이 변경된 후 구성 가능한 제품 특별 가격이 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-42520**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - *국경 간 거래 사용*&#x200B;을(를) 사용하는 경우 세율이 두 번 적용되는 문제를 수정합니다.
* 업데이트된 패치: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* 사용되지 않는 패치: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728**(*Adobe Commerce 및 Magento Open Source >=2.3.2 &lt;2.4.5*) - *제품 가시성*&#x200B;을 변경한 후에만 대량 특성 업데이트로 기본 저장소에 대한 URL 다시 쓰기가 만들어지는 문제를 해결했습니다.
* **MDVA-43091**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 백엔드에서 관리자가 번들 제품을 주문하면 오류 *이 제품에 대한 소수점 이하 자릿수를 사용할 수 없음*&#x200B;이 발생하는 문제를 해결했습니다.
* **MDVA-40816**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - 관련 제품 규칙이 규칙 조건에 정의되지 않은 범주의 제품을 표시하는 문제를 해결했습니다.
* **MDVA-41305**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.5*) - GraphQL 돌연변이가 구성 가능한 제품 옵션을 위시리스트에 추가한 후 반환하지 않는 문제를 해결했습니다.
* **MDVA-39181**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 관련 제품 규칙에 규칙 조건에 정의되지 않은 범주의 제품이 표시되는 문제를 해결했습니다.
* **MDVA-42584**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - Import 또는 API를 통해 수량 및 재고 상태를 변경한 후 백엔드에서 구성 가능한 재고 상태가 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-40175**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.3*) - *배송 방법을 변경하려면 클릭*&#x200B;을(를) 수행하면 순서 조정 중에 관리자의 배송 방법을 선택할 수 있는 라디오 단추가 표시되지 않는 문제가 해결되었습니다.
* **MDVA-42768**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.5*) - *품절 표시*&#x200B;가 예인 경우 구성 가능한 제품에 일반 가격이 0으로 표시되는 문제를 해결했습니다.
* **MDVA-43201**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 특정 로케일에 DOB 특성을 사용할 때 고객 로그인에 오류가 발생하는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.5*) - Adobe Commerce 시간대가 로컬 환경 시간대와 다를 때 날짜 필터가 제대로 작동하지 않는 문제를 해결했습니다.
* **MDVA-42657**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - 관리 사용자가 고객 세그먼트 조건에서 범주를 선택할 수 없는 문제를 해결했습니다.
* **MDVA-42806**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 기존 회사가 REST API를 통해 업데이트될 때마다 *새 회사 등록* 전자 메일이 전송되는 문제를 해결했습니다.
* **MDVA-37984**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.5*) - [!DNL Visual Merchandiser] *규칙별로 제품 일치* 기능이 스테이징 업데이트로 제품을 제대로 필터링하지 못하는 문제를 해결했습니다.
* **MDVA-40488**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 품절 하위 제품이 있는 구성 가능한 제품이 올바른 가격 범위에 표시되지 않는 문제를 해결했습니다.
* **MDVA-42507**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.5*) - 장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되는 문제를 해결했습니다.
* **MDVA-39163**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.4.5*) - 새 사용자가 등록되고 장바구니의 제품이 게스트 세션에서 제공된 경우 배송 방법을 사용할 수 없는 문제를 해결했습니다.
* **MDVA-38626**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.5*) - 관리자가 [!DNL PayPal Payflow Pro] 결제를 사용하여 백엔드에 주문할 수 없는 문제를 해결했습니다.
* **MDVA-38666**(*Adobe Commerce 및 Magento Open Source >=2.3.2 &lt;2.3.6*) - 관리 사용자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결했습니다.
* **MDVA-38526**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 관리 사용자가 [!DNL Site-Wide Analysis tool]에 액세스할 수 없는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - *mage-messages* 쿠키가 이미 있지만 새 메시지가 없는 경우 이를 설정한 후 사용자가 500 오류를 가져오는 문제를 해결했습니다.
* **MDVA-41139**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;2.4.4*) - 구성 가능한 제품의 원본 중 하나에 대해 단순 제품의 qty=0일 때 제품을 가져온 후 해당 제품이 품절되는 문제를 해결했습니다.
* **MDVA-42326**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 영구적 장바구니가 활성화된 경우에도 세션 시간 제한 후 고객이 체크아웃 시 오류가 발생하는 문제를 수정합니다.
* **MDVA-42341**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*&#x200B;의 경우) - 요청에 스토어 헤더가 있는 경우 `categoryList` GraphQL 쿼리가 결과를 필터링하지 않는 문제를 해결했습니다.
* **MDVA-38393**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*&#x200B;의 경우) - 간단한 제품 이름을 변경할 경우 구성 가능한 제품에 대해 카탈로그 규칙이 작동하지 않는 문제를 해결했습니다.
* **MDVA-39153**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 관리자의 순서 변경 중에 할인 금액이 잘못 계산되는 문제가 수정되었습니다.
* 업데이트된 패치: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.3*) - 관리 사용자가 웹 사이트를 삭제한 후 고객의 그리드에 액세스할 수 없는 문제를 해결했습니다.
* **MDVA-40311**(*Adobe Commerce 및 Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - 관리 사용자가 오류 메시지 *잘못된 보안 또는 양식 키를 받는 문제를 해결했습니다. 사용자 지정 관리자 경로가 구성되어 있고 비밀 키가 활성화된 경우 관리자에 로그인한 후* 페이지를 새로 고치십시오.
* **MDVA-41631**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 사용자가 GraphQL을 통해 선택적 *전화* 값 없이 주문 정보를 검색하려고 할 때 오류가 발생하는 문제를 해결했습니다.
* **MDVA-27239**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.3.6*) - 크로스셀 제품이 표시되지 않는 문제를 해결했습니다.
* 업데이트된 패치: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.4.4*) - 리인덱싱하는 동안 프런트 엔드에 제품이 누락된 문제를 해결했습니다.
* **MDVA-40120**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - DESC/ASC별로 GraphQL 정렬이 동일한 관련성 또는 가격을 갖는 제품에서 작동하지 않는 문제를 해결했습니다.
* **MDVA-41399**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;2.4.2*) - 고객이 위시리스트에 제품을 추가할 경우 관리 사용자가 *장바구니 관리* 페이지에 액세스할 수 없는 문제를 해결했습니다.
* **MDVA-40609**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*&#x200B;의 경우) - 비활성화된 제품 데이터가 `cataloginventory_stock_status` 인덱스 테이블에 없어 비활성화된 제품 수량이 잘못 표시되는 문제를 해결했습니다.
* **MDVA-39031**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - 대상 웹 사이트에 할당되지 않았더라도 GraphQL을 통해 장바구니에 제품을 추가할 수 있는 문제를 해결했습니다.
* **MDVA-41597**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - GraphQL을 사용하여 구성 가능한 제품을 장바구니에 둘 이상 추가할 때 사용자에게 오류가 발생하는 문제를 해결했습니다.
* **MDVA-27456**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.3.7*) - 사용자가 [!DNL Swagger]을(를) 로드하려고 할 때 오류가 발생하는 문제를 해결했습니다.
* **MDVA-32776**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.2*) - 주문이 되었으나 배송되지 않은 경우 재고 상태가 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-30862**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.0*) - 인쇄된 PDF 송장의 주문 날짜가 잘못된 문제를 해결했습니다.
* [!DNL Quality Patch Tool]에 대한 인덱스 페이지를 개선했습니다. 최신 버전의 도구에서 [!DNL quality patches]에 대한 편리한 검색 및 필터링을 추가했습니다.
* 업데이트된 패치: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 종료 날짜가 이전에 제거된 경우 새 업데이트를 만들거나 기존 예약된 제품 업데이트를 편집할 수 없는 문제가 해결되었습니다.
* **MDVA-41046**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 사용자 지정 옵션이 있는 간단한 제품을 구성 가능한/그룹화된 제품에 할당할 수 있는 문제를 해결했습니다.
* **MDVA-40545**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 동일한 페이지에 대한 노드가 두 개 이상 있더라도 페이지의 첫 번째 노드만 검색되던 문제를 해결했습니다.
* **MDVA-41164**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - 관리자가 파일 또는 이미지 유형 사용자 지정 고객 특성이 있는 회사를 저장하거나 편집할 수 없는 문제를 해결했습니다.
* **MDVA-39229**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 카탈로그 규칙 준비 업데이트 시작 시간을 업데이트한 후 다음 오류가 표시되는 문제를 해결했습니다. *Cron 작업 staging_synchronize_entities_period에 오류가 있습니다. 활성 업데이트를 삭제할 수 없습니다.*
* **MDVA-40619**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - CMS 페이지에서 인라인 편집을 시도할 때 CMS 페이지 계층 구조를 변경하면 500 오류가 발생하는 문제를 해결했습니다.
* **MDVA-41061**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 관리자로부터 제품을 저장할 때 재고 상태가 저장 가능으로 재설정되는 문제를 해결합니다.
* **MDVA-31763**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 수동으로 다시 색인화할 때까지 카탈로그 가격 규칙이 되돌아가거나 적용되지 않는 문제를 해결했습니다.
* **MDVA-37748**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - GraphQL 쿼리가 공유 카탈로그에 할당되지 않은 제품을 반환하는 문제를 해결합니다.

## v1.1.4 {#v1-1-4}

* **MDVA-40399**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - REST API를 통해 동일한 주문에 대한 부분 송장을 동시에 만들 수 없는 문제를 해결했습니다.
* **MDVA-40101**(*Adobe Commerce 및 Magento Open Source >=2.3.2 &lt;2.4.0*) - [!DNL PayPal Express] 체크아웃을 사용하여 성공적으로 주문을 배치한 후 미니 장바구니에서 항목이 제거되지 않는 문제를 해결했습니다.
* **MDVA-40401**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 주문이 실패하더라도 쿠폰 사용 값이 변경되는 문제를 수정합니다.
* **MDVA-40537**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.4.0-p1*&#x200B;의 경우) - 동일한 URL 키를 사용하는 여러 CMS 페이지가 있는 경우 스토어 보기를 만들 때 사용자에게 오류가 발생하는 문제를 해결했습니다.
* **MDVA-37725**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.4.3-p1*&#x200B;의 경우) - 기본이 아닌 웹 사이트에서 보낸 비동기 주문 전자 메일에 기본 웹 사이트의 로고 URL이 포함되는 문제를 해결했습니다.
* **MDVA-39482**(*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - 미납주문을 사용할 때 수량을 &quot;0&quot;과 함께 가져올 경우 제품이 품절되는 문제를 수정합니다.
* **MDVA-40435**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;2.4.4*) - GraphQL을 통해 적용할 때 동적 가격이 적용된 번들 제품에 대한 할인이 잘못되어 발생하는 문제를 해결했습니다.
* **MC-42528**(*Adobe Commerce 및 Magento Open Source >=2.4.3 &lt;=2.4.3-p1*&#x200B;의 경우) - `categoryList` GraphQL 쿼리가 할당된 범주와 할당되지 않은 범주를 모두 반환하는 문제를 해결했습니다.
* **MDVA-29400** (*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - [!DNL PayPal Express Checkout]에서 수행한 중복 주문의 문제를 수정합니다.
* **MDVA-26005**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.3.5-p2*&#x200B;의 경우) - 장바구니 가격 규칙 조건에 대한 범주 트리에서 범주를 선택할 수 없는 문제를 해결했습니다.
* **MDVA-25631**(*Adobe Commerce 및 Magento Open Source >=2.3.3 &lt;=2.3.5-p2*&#x200B;의 경우) - 많은 수의 고객이 포함된 고객 세그먼트를 편집하고 저장하는 성능이 향상됩니다.

## v1.1.3 {#v1-1-3}

* **MDVA-40262**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - GraphQL 검색 쿼리가 관리자의 인기 검색어에 표시되지 않는 문제를 해결했습니다.
* **MDVA-40601**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;=2.4.2-p2*&#x200B;의 경우) - GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 정보를 가져오려고 할 때 사용자에게 오류가 발생하는 문제가 해결되었습니다.
* **MDVA-37234**(*Adobe Commerce 및 Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - 동일한 SKU에 대해 장바구니에 항목을 여러 번 추가(병렬 요청)하면 동일한 장바구니 ID에 대해 중복 라인 항목이 생성되는 문제가 해결되었습니다.
* **MDVA-33606**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;=2.4.2-p2*&#x200B;의 경우) - 계층에 할당된 CMS 페이지를 저장할 때 사용자에게 *고유 제한 위반* 오류가 발생하는 문제를 해결했습니다.
* **MDVA-31590**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.1-p1*&#x200B;의 경우) - 사용자가 MySQL 비동기 큐를 사용하여 특성을 일괄적으로 업데이트할 수 없는 문제를 해결했습니다.
* **MDVA-36309**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*&#x200B;의 경우) - 특성별 제품 검색이 관리자 그리드에서 느려지는 문제를 해결했습니다.

## v1.1.2 {#v1-1-2}

* **MDVA-38929**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 스토어 크레딧에서 주문을 결제할 때 FPT가 있는 송장에 잘못된 총계가 표시되는 문제를 해결했습니다.
* **MDVA-37364**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.3*&#x200B;의 경우) - 날짜 유형의 사용자 지정 고객 특성이 고객의 그리드 UI를 손상하는 문제를 해결했습니다.
* **MDVA-39195**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*&#x200B;의 경우) - 장바구니로 리디렉션이 활성화될 때 범주 페이지에서 *장바구니에 추가* 단추가 비활성화되는 문제를 해결했습니다.
* **MDVA-37115**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;=2.4.2-p2*&#x200B;의 경우) - 구성 가능한 제품 페이지에 불필요한 *0개의 왼쪽* 알림만 표시되는 문제를 해결했습니다.
* **MDVA-39521**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4*) - 사용자가 GraphQL을 통해 빈 전화 번호로 장바구니의 배송 주소를 설정할 수 없는 문제를 해결했습니다.
* **MDVA-39384**(*Adobe Commerce 및 Magento Open Source >=2.3.1 &lt;=2.3.6) || >=2.4.1 &lt;=2.4.3*) - 회사 사용자에 대한 사용자 지정 고객 특성이 저장되지 않는 문제를 수정합니다.
* **MDVA-39043**(*Adobe Commerce 및 Magento Open Source >=2.3.4 &lt;=2.4.3*&#x200B;의 경우) - 액세스 권한이 제한된 관리자가 *제품* 위젯을 CMS 페이지에 추가하려고 할 때 오류가 발생하는 문제를 해결했습니다.
* **MDVA-39966**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - 잘못된 로케일 배포 문제를 해결했습니다.
* **MDVA-38852**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;=2.3.5-p2*&#x200B;의 경우) - 디자인을 통한 카탈로그 인벤토리가 여러 병렬 주문의 경우 성능을 크게 저하시키는 업데이트에 대해 테이블을 잠그는 문제를 해결합니다.
* **MDVA-39986**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.3*) - 사용자가 Safari 브라우저를 사용하여 MacOS의 관리자에 순서를 지정할 수 없는 문제를 해결했습니다.
* **MDVA-38447**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.4*) - 두 가지 문제가 해결되었습니다. *개별적으로 표시되지 않음* 구성 가능한 하위 제품이 GraphQL 응답에 반환되고 범주 필터를 사용하여 GraphQL 제품 쿼리에 대해 MySQL 쿼리가 최적화됩니다.
* **MDVA-40134**(*Adobe Commerce 및 Magento Open Source >=2.4.2 &lt;2.4.3*) - 공유 카탈로그가 활성화되면 GraphQL에서 관련 제품을 반환하지 않는 문제를 해결했습니다.
* **MDVA-39935**(*Adobe Commerce 및 Magento Open Source >=2.4.1 &lt;2.4.4*) - GraphQL에서 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 해결했습니다.

## v1.1.1 {#v1-1-1}

* **MDVA-36021**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;2.4.4*) - 관리자의 주문 세부 사항 페이지에 *멤버 함수 getId()* 호출이 표시되는 문제를 해결했습니다.
* **MDVA-34948** (*Adobe Commerce 및 Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - `GET_LOCK`과(와) 같이 오래 실행되는 쿼리와 관련된 문제를 수정합니다.
* **MDVA-39305**(*Adobe Commerce 및 Magento Open Source >=2.4.0 &lt;=2.4.2-p1*&#x200B;의 경우) - 등록된 고객이 활성화된 Google ReCaptcha로 로그인할 수 없는 문제를 해결합니다.
* **MDVA-37897**(*Adobe Commerce 및 Magento Open Source >=2.3.0 &lt;2.4.4*) - 고객이 최근에 본 위젯의 옵션이 있는 제품을 추가하려고 할 때 잘못된 리디렉션으로 문제를 수정합니다.

## v1.1.0 {#v1-1-0}

* 고객이 사용자 경험을 개선하고 필요한 패치를 쉽게 검색할 수 있도록 패치 카테고리가 도입됐다.
* `patches.json` 파일의 이름이 `support-patches.json`(으)로 바뀌었습니다.
* **MDVA-38799**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 스테이징 업데이트를 만든 후 다운로드 가능한 제품이 저장되지 않은 문제를 해결했습니다.
* **MDVA-37592**(*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*&#x200B;의 경우) - 공유 카탈로그에 가격이 0으로 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 해결했습니다.
* **MDVA-38827**(*Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - 고객이 오류 메시지가 포함된 주문 배송 이메일을 받는 문제를 해결합니다.

## v1.0.26 {#v1-0-26}

* **MDVA-38468**(*Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*&#x200B;의 경우) - CMS 페이지를 저장할 때 오류를 수정합니다. *ID PAGE_ID가 같은 항목이 이미 있습니다*.
* **MDVA-34680**(*Adobe Commerce >=2.3.6 &lt;=2.3.7) || >=2.4.1 &lt;2.4.3*) - 고객 계정의 생성 시간이 고객 그리드에서 올바르게 필터링되지 않는 문제를 해결했습니다.
* **MDVA-37068**(*Adobe Commerce >=2.3.1 &lt;2.4.4*&#x200B;의 경우) - 장바구니에 가상 제품만 있을 때 잘못된 세율이 표시되는 문제를 수정합니다.
* **MDVA-38608**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 색인 재지정이 완료되지 않은 경우 임시 테이블이 삭제되지 않는 문제를 해결했습니다.
* **MDVA-38308** (*Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - 제품에 [!DNL Vimeo] 비디오를 추가하는 것과 관련된 문제를 수정합니다.

## v1.0.25 {#v1-0-25}

* **MDVA-37916**(*Adobe Commerce >=2.3.6 &lt;2.4.3*) - [!DNL Paypal Payment Advanced] 메서드를 사용할 때 고객이 결제 확인 페이지로 이동하지 않는 문제를 해결했습니다.
* **MDVA-37082**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 그룹화된 제품의 사용자 지정 재고를 저장할 때 프론트엔드에 제품이 품절 상태로 표시되는 문제를 해결합니다.
* **MDVA-36572**(*Adobe Commerce >=2.3.5 &lt;2.4.3*) - 대변 메모 업데이트로 인해 더 이상 데이터베이스에 중복 제품 예약 업데이트가 발생하지 않는 문제를 해결했습니다.
* **MDVA-38132**(*Adobe Commerce >=2.3.3 &lt;2.4.3*) - *리디렉션이 너무 많음* 오류로 인해 관리 패널에 연결할 수 없는 문제를 수정합니다.
* **MDVA-38270**(*Adobe Commerce >=2.4.1 &lt;2.4.3*) - GraphQL의 총 주문에서 기프트 카드 정보가 누락되는 문제를 해결했습니다.

## v1.0.24 {#v1-0-24}

* **MDVA-37779**(*Adobe Commerce >=2.4.2 &lt;=2.4.4*&#x200B;의 경우) - 웹 사이트 ID가 스토어 ID와 일치하지 않을 때 GraphQL을 통해 구성 가능한 제품을 장바구니에 추가하는 문제를 해결했습니다.
* **MDVA-36832**(*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*&#x200B;의 경우) - 보기 너비가 768px일 때 페이지에서 이미지가 중복되는 문제를 해결했습니다.
* **MDVA-37874**(*Adobe Commerce >=2.3.6 &lt;=2.3.7) || >=2.4.1 &lt;=2.4.2-p1*) - 두 개 이상의 옵션이 포함된 번들 제품에 *전체 장바구니에 대한 고정 할인 금액*&#x200B;이 잘못 적용되는 문제가 수정되었습니다.
* **MDVA-37913**(*Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*&#x200B;의 경우) - 다운로드 가능한 제품이 API를 통해 업데이트되는 경우 다운로드 가능한 링크가 사라지는 문제를 해결했습니다.
* **MDVA-34330**(*Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*&#x200B;의 경우) - Orders 그리드의 주문이 관리 시간대에 따라 필터링되지 않는 문제를 해결했습니다.

## v1.0.23 {#v1-0-23}

* **MDVA-37478**(*Adobe Commerce >=2.3.0 &lt;=2.3.7*&#x200B;의 경우) - REST API를 통해 *계정에서 결제* 결제 방법으로 주문된 주문에 대한 부분 송장을 만들 때 Adobe Commerce에서 오류가 발생하는 문제를 해결했습니다.
* **MDVA-37362**(*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*&#x200B;의 경우) - 구성 가능한 제품 옵션 값과 변형 특성 값이 GraphQL 응답에서 비어 있는 문제를 해결했습니다.
* **MDVA-37288**(*Adobe Commerce 2.4.2*&#x200B;의 경우) - GraphQL 요청 후 잘못된 계층 가격이 반환되던 문제를 해결했습니다.
* **MDVA-37225**(*Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*&#x200B;의 경우) - 가져온 SKU에 정수 값이 있는 경우 빠른 주문 생성 중에 업로드 프로세스가 중단되는 문제를 수정합니다.
* **MDVA-37224**(*Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*&#x200B;의 경우) - 고객이 장바구니에 있는 다른 제품으로 [!DNL PayFlow Pro]과(와) 협상 가능한 견적에 대해 결제할 수 없는 문제를 해결했습니다.
* **MDVA-36286**(*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*&#x200B;의 경우) - 동일한 SKU에 하위 범주의 다른 위치가 있는 경우 Page Builder 제품 위젯 미리 보기가 중단되는 문제를 해결했습니다.
* **MDVA-30186** (*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - GraphQL 응답에서 특성 항목 수 대신 옵션 값별로 특성 옵션이 정렬되는 문제가 해결되었습니다.

## v1.0.22 {#v1-0-22}

* **MDVA-36718**(*Adobe Commerce >=2.3.0 &lt;=2.4.2*&#x200B;의 경우) - API를 통해 변경된 후 이전 사용자 지정 옵션이 남아 있는 문제를 해결했습니다.
* **MDVA-35773** (*Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - 100% 할인된 주문에 대한 송장에서 총계가 0으로 표시되지 않는 문제를 해결했습니다.
* **MDVA-36833**(*Adobe Commerce 2.4.2*&#x200B;의 경우) - 공유 카탈로그에서 일부 제품을 제외한 후 페이지당 임의의 제품 수를 표시하는 검색 결과와 관련된 문제를 해결했습니다.
* **MDVA-37182**(*Adobe Commerce >=2.4.1 &lt;=2.4.2*&#x200B;의 경우) - [!DNL Elasticsearch] 버전 6 및 버전 7 모두에서 잘못된 검색 결과를 가져오는 문제를 해결했습니다.
* **MDVA-36253**(*Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*&#x200B;의 경우) - 항목 삭제 후 미니 장바구니에 잘못된 소계가 표시되는 문제를 해결했습니다.
* **MDVA-36853**(*Adobe Commerce 2.4.2*&#x200B;의 경우) - 대형 미디어 갤러리를 로드할 때 이미지가 표시되지 않는 문제를 해결했습니다.

## v1.0.21 {#v1-0-21}

* **MDVA-34665**(*Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*&#x200B;의 경우) - 범주 페이지에 번들 제품이 없는 문제를 해결했습니다.
* **MDVA-36615**(*Adobe Commerce 2.4.2*&#x200B;의 경우) - 관리 제품 표에서 잘못된 제품 수로 인한 문제를 해결했습니다.
* **MDVA-36464**(*Adobe Commerce >=2.4.0 &lt;=2.4.2*&#x200B;의 경우) - 전자 메일 알림 구성이 저장소 보기 수준에서 작동하지 않는 문제를 해결했습니다.
* **MDVA-36138**(*Adobe Commerce ^2.3.2*&#x200B;의 경우) - 장바구니에 있는 모든 항목이 무료 배송 장바구니 규칙에 적합하지 않을 경우 배송 가격이 조정되지 않고 전체 배송 가격이 고객에게 표시되는 문제를 해결했습니다.
* **MDVA-36424** (*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - 백엔드 기본 URL이 상점 기본 URL과 다른 경우 콘텐츠가 반복적으로 편집될 때 페이지 빌더 요소에 첨부된 미디어 이미지가 사라지는 문제가 수정되었습니다.
* **MDVA-35984**(*Adobe Commerce ^2.4.0*&#x200B;의 경우) - 동일한 제품에 대해 여러 개의 동시 출하를 만든 후 제품 수량과 판매 가능 수량이 잘못된 문제를 수정합니다.

## v1.0.20 {#v1-0-20}

* **MDVA-36170**(*Adobe Commerce >=2.3.4 &lt;2.4.2*&#x200B;의 경우) - 이렇게 하면 GraphQL 쿼리가 범주 캐시 태그를 사용하여 캐싱하지 않는 문제가 해결됩니다.
* **MDVA-33168**(*Adobe Commerce >=2.3.3 &lt;2.4.2*&#x200B;의 경우) - API를 통해 제품 특성을 업데이트할 때 발생하는 문제를 해결했습니다. 다른 모든 특성은 빈 값으로 변경됩니다.
* **MDVA-19640**(*Adobe Commerce >=2.3.0*&#x200B;의 경우) - [!DNL Advanced Reporting]에 데이터가 표시되지 않는 문제가 해결되었습니다.
* **MDVA-11189**(*Adobe Commerce >=2.3.0 &lt;2.3.5*) - 제품 재고를 업데이트하기 위해 CSV 파일을 가져온 후 `cataloginventory_stock` 테이블의 행이 삭제될 때 문제를 수정합니다.
* **MDVA-26639**(*Adobe Commerce >=2.3.3-p1 &lt;2.3.6*&#x200B;의 경우) - 새 주문 확인 전자 메일 템플릿을 만들 경우 주문 항목이 주문 메일에 누락되는 문제를 해결했습니다.
* **MDVA-15546**(*Adobe Commerce >=2.3.0*&#x200B;의 경우) - 주문을 만든 후 *Column entity_id where 절이 모호합니다* 오류가 예외 로그에 표시되는 문제를 해결했습니다.
* **MDVA-21095**(*Adobe Commerce >=2.3.0 &lt;2.3.5*&#x200B;의 경우) - 대량 특성 값을 업데이트한 후 쿼리 `INSERT INTO search_tmp`이(가) 종료되지 않을 때 문제를 해결합니다.
* **MDVA-23845**(*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*&#x200B;의 경우) - JavaScript 축소가 활성화된 후 전자 메일 템플릿을 미리 볼 수 없는 문제를 해결했습니다.
* **MDVA-22026**(*Adobe Commerce >=2.3.2 &lt;2.3.4*&#x200B;의 경우) - 외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 가져오지 못하는 문제를 해결했습니다.
* **MDVA-22383**(*Adobe Commerce >=2.3.0 &lt;2.3.4*&#x200B;의 경우) - 제품 저장에 시간이 오래 걸리고 페이지가 중단되는 문제를 해결했습니다.
* **MC-41359**(*Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - 잘못된 SameSite 쿠키 매개 변수 설정의 문제를 해결합니다.

## v1.0.19 {#v1-0-19}

* **MDVA-33614**(*Adobe Commerce 2.4.1*&#x200B;의 경우 ) - 페이지 빌더에서 다음 오류가 발생하는 문제를 해결했습니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 담당자에게 문의하십시오.*
* **MDVA-35356**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 부분 송장 주문 취소 후 잘못된 스토어 크레딧 반환 문제를 해결했습니다.
* **MDVA-33289**(*Adobe Commerce >=2.4.0 &lt;2.4.3*) - [!DNL Google Tag Manager]이(가) 활성화된 경우 체크아웃 중에 원시 JavaScript 코드가 청구 주소 UI에 표시되는 문제를 수정합니다.
* **MDVA-35982**(*Adobe Commerce >=2.3.0 &lt;2.4.3*&#x200B;의 경우) - 특정 웹 사이트로 제한된 관리자 사용자가 동일한 웹 사이트에 배치된 주문에 대한 납품을 만들 수 없는 문제를 해결했습니다.
* **MDVA-35155**(*Adobe Commerce >=2.3.0 &lt;2.3.6*) - 옵션 제목을 변경한 경우 번들 제품을 구입할 수 없는 문제를 해결했습니다.
* **MDVA-35910**(*Adobe Commerce >=2.4.1 &lt;2.4.3*) - 고객으로 로그인 기능을 사용하지 않도록 설정한 후 새 고객 계정을 만들 수 없는 문제를 해결했습니다.
* **MDVA-34474**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - API를 사용하여 구매요청 목록에 제품을 추가할 때 발생하는 문제를 수정합니다.
* **MDVA-34591**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - *최대 할인 수량이 적용된 대상* 및 *할인 수량 단계(구매 X)*&#x200B;에 대한 잘못된 장바구니 규칙 할인 계산과 관련된 문제를 해결했습니다.
* **MDVA-33704**(*Adobe Commerce >=2.4.0 &lt;2.4.3*) - 사용할 수 있도록 구성되었지만 *스토어 픽업에서* 배송 옵션이 표시되지 않는 문제를 해결했습니다.
* **MDVA-34928**(*Adobe Commerce >=2.3.5 &lt;2.3.5-p2*&#x200B;의 경우) - 스토어 크레딧이 지불에서 제거된 후 페이지 로더가 무기한 표시되는 문제를 해결했습니다.
* **MDVA-35254**(*Adobe Commerce >=2.3.1 &lt;2.4.3*) - 체크아웃 중에 CAPTCHA 문제를 해결했습니다.
* **MDVA-35569**(*Adobe Commerce >=2.3.4 &lt;2.4.2*) - 상태가 지정된 경우 *고정 제품 세금* 필드가 GraphQL 응답에서 채워지지 않는 문제를 해결했습니다.
* **MDVA-35847**(*Adobe Commerce >=2.4.1 &lt;2.4.3*) - 사용자 지정 고객 특성을 사용하는 경우 회사 사용자 양식이 중단되는 B2B 문제를 수정합니다.
* **MDVA-31307**(*Adobe Commerce >=2.4.0 &lt;2.4.2*) - 캐시된 블록에 대한 동적 CSP 허용 목록 문제로 인해 특정 범주에 *메모리 부족* 오류가 있는 문제를 해결합니다.

## v1.0.18 {#v1-0-18}

* **MDVA-32655**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 여러 제품을 삭제한 후 소비자 `quoteItemCleaner`에 대해 잘못된 *진행 중* 메시지 상태를 올바른 *완료* 메시지로 수정합니다.
* **MDVA-34102**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 제품 그리드에서 비활성화된 제품에 대해 기본 재고 수량이 영(0)으로 수정되고 관리 영역에서 제품 페이지가 편집됩니다.
* **MDVA-35286**(*Adobe Commerce >=2.4.0 &lt;2.4.2*) - 고객이 장바구니에 제품을 번들로 제공하고 여러 주소 체크아웃에서 Onepage 체크아웃으로 전환하는 경우 오류가 발생하는 문제를 해결했습니다.
* **MDVA-35312**(*Adobe Commerce >=2.4.1-p1 &lt;2.4.2*&#x200B;의 경우) - 빈 GraphQL 요청일 때 응답 코드 500을 수정합니다.
* **MDVA-34189**(*Adobe Commerce >=2.3.4 &lt;2.4.3*) - 관리 범주 페이지를 로드할 때 [!DNL Visual Merchandiser] 쿼리에서 503개의 첫 번째 바이트 시간 제한이 수정되었습니다.
* **MDVA-34695**(*Adobe Commerce >=2.3.0 &lt;2.4.1*&#x200B;의 경우) - 범주를 삭제한 후 음수 `children_count`이(가) 수정되었습니다.

## v1.0.17 {#v1-0-17}

* **MDVA-34012**(*Adobe Commerce >=2.3.1 &lt;2.4.3*) - 예약된 변경 내용이 적용된 후 *기본값 사용* 확인란이 지워지는 문제를 해결했습니다. 예약된 변경 사항이 더 이상 적용되지 않으면 문제가 표시됩니다.
* **MDVA-35064**(*Adobe Commerce >=2.3.3 &lt;2.4.3*) - API를 통해 만든 구성 가능한 제품에 대해 URL 다시 쓰기가 생성되지 않는 문제가 수정되었습니다.
* **MDVA-34943**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 빠른 주문이 이전에 입력한 SKU를 캐시하는 문제를 수정합니다.
* **MDVA-35197**(*Adobe Commerce >=2.3.5 &lt;2.4.0*) - 이전에 추가한 제품의 재고가 부족한 경우 GraphQL을 사용하여 장바구니에 추가할 때 오류가 발생하는 문제를 수정합니다.
* **MDVA-34850**(*Adobe Commerce >=2.3.1 &lt;2.4.0*) - 구성 가능한 제품의 품절 옵션이 취소선으로 표시되지 않고 표시되지 않는 문제를 해결했습니다.
* **MDVA-34867**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - 예약된 업데이트에 대해 설정된 조건 필드의 값이 저장되지 않는 문제를 해결했습니다.
* **MDVA-35092**(*Adobe Commerce >=2.3.5 &lt;2.4.3*) - 더 이상 사용되지 않는 [!DNL Vimeo] API로 인해 사용자가 [!DNL Vimeo] 비디오를 추가할 수 없는 문제를 해결했습니다.

## v1.0.16 {#v1-0-16}

* **MDVA-33453**(*Adobe Commerce >=2.3.6 &lt;2.4.3*) - 일치하는 제품에 각 웹 사이트의 가격이 다른 경우 Page Builder 제품 콘텐츠 형식 미리 보기가 중단되는 문제를 해결했습니다.
* **MDVA-32634**(*Adobe Commerce ^2.3.1*&#x200B;의 경우) - 계층에서 범주를 이동한 후 모든 저장소에 할당된 범주의 `url_path`이(가) 변경되지 않은 상태로 유지되는 문제를 해결했습니다.
* **MDVA-33344**(*Adobe Commerce ^2.3.0*&#x200B;의 경우) - 하드 코딩된 `rma_item` 엔터티 기본 특성 집합 ID가 데이터베이스의 값 대신 사용되는 문제를 해결했습니다.
* **MDVA-34192**(*Adobe Commerce >=2.3.4 &lt;2.4.3*) - dd/mm/yyyy 형식을 사용하여 고객 생년월일을 수정/지정할 수 없는 문제를 해결했습니다.
* **MDVA-34847**(*Adobe Commerce ^2.3.0*&#x200B;의 경우) - 사용자 지정 권한이 있는 관리자의 관리 컬렉션에 있는 SQL 조건에 대한 저장소 ID 형식이 정수로 변환되는 수정 사항입니다.
* **MDVA-34886**(*Adobe Commerce ^2.3.2*&#x200B;의 경우) - *가중치* 제품 특성이 검색 가능한 것으로 구성된 경우 검색 결과가 반환되지 않는 문제를 해결했습니다.

## v1.0.15 {#v1-0-15}

* **MDVA-33559**(*Adobe Commerce >=2.3.0 &lt;2.4.3*&#x200B;의 경우) - 리디렉션 매개 변수 목록 형식 오류로 인해 [!DNL PayPal Payflow Pro] 결제가 실패하는 문제를 해결했습니다.
* **MDVA-34023**(*Adobe Commerce >=2.3.0 &lt;2.4.3*) - *addressId를 가진 해당 엔터티가 방문자의 브라우저에 임의로 표시되지 않는 문제를 해결했습니다.*
* **MDVA-32759**(*Adobe Commerce >=2.3.1 &lt;2.4.3, B2B 확장 포함*) - 공유 카탈로그가 기존 계층 가격을 삭제하는 문제를 해결했습니다.
* **MDVA-33482**(*Adobe Commerce ^2.3.5*&#x200B;의 경우 ) - 부분 송장에 대해 대변 메모를 생성하면 해당 부분 송장에 대한 세금 대신 총 주문에 대해 세금이 부과되는 문제를 해결했습니다.
* **MDVA-33393**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 오류 *제공된 countryId가 존재하지 않습니다*.
* **MDVA-33632**(*Adobe Commerce >=2.3.0 &lt;2.3.7*) - 품절 제품을 다시 주문하려고 할 때 *이 제품의 품절* 예외 메시지가 관리자에게 표시되는 문제를 해결합니다.
* **MDVA-34469**(*Adobe Commerce >=2.4.1 &lt;2.4.2*) - 여러 스토어 보기를 사용할 때 고객 장바구니에 있는 GraphQL 돌연변이가 실패하는 문제를 해결했습니다.
* **MDVA-33976**(*Adobe Commerce >=2.3.0 &lt;2.3.7*) - 번들 제품에서 두 번째 옵션을 제거한 후 번들 제품이 상점 앞에 품절되어 표시되는 문제를 해결했습니다.
* **MDVA-33894**(*Adobe Commerce >=2.4.0 &lt;2.4.1, B2B 확장 포함*) - 여러 제품 추가 및 제거, SKU 대소문자 구분 등 빠른 주문 기능에 대한 여러 문제가 수정되었습니다.
* **MDVA-27664**(*Adobe Commerce >=2.3.4 &lt;2.3.6*) - 고객 등록 양식에서 표시되는 오류의 원인이 되는 문제를 해결했습니다. *오류 - 생년월일은 오늘보다 커서는 안 됩니다.*
* **MDVA-33970**(*Adobe Commerce >=2.3.4 &lt;2.4.2*) - 가격 특성의 범위가 웹 사이트로 설정되어 있을 때 대변 메모에 잘못된 통화 기호가 있는 문제가 수정되었습니다.
* **MDVA-33992**(*Adobe Commerce >=2.3.0 &lt;2.4.2*&#x200B;의 경우) - 체크아웃 중에 잘못 표시되는 B2B 특별 가격 문제를 해결했습니다.
* **MDVA-34100**(*Adobe Commerce >=2.3.4 &lt;2.4.2, B2B 확장 포함*) - 회사 구조 페이지에서 회사 계정을 만들 수 없는 문제를 해결했습니다.

## v1.0.14 {#v1-0-14}

* **MDVA-31969**(*Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - CSV 파일에서 제품을 가져온 후 이미지가 중복되는 문제를 해결합니다.
* **MDVA-33382**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 범주에서 제품을 제거한 후 인덱서 무효화 문제를 해결했습니다.
* **MDVA-28511**(*Adobe Commerce >=2.3.5 &lt;2.3.6*) - 이름 필드에 특정 문자(예: 악센트 부호 대문자)가 포함된 경우 [!DNL PayPal] 체크아웃을 완료할 수 없는 문제를 해결했습니다.
* **MDVA-31519**(*Adobe Commerce >=2.3.5 &lt;2.3.6*&#x200B;의 경우) - 사이트 전체 판매 규칙이 사용 중일 때 게스트 체크아웃에서 대기 시간 초과 문제를 해결합니다.
* **MDVA-33281**(*Adobe Commerce >=2.3.4 &lt;2.3.6*) - 잘못된 SKU 매개 변수 유형으로 인해 `inventory:reservation:list-inconsistencies`에 치명적인 오류가 발생하는 문제를 해결했습니다.
* **MDVA-24201**(*Adobe Commerce >=2.3.0 &lt;2.3.5*) - 수동으로 다시 인덱싱할 때까지 가격이 예약된 장바구니 가격 규칙을 반영하지 않는 문제를 해결했습니다.
* **MDVA-32694** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - 기본 스토어가 아닌 제품과 관련된 경우 관리자가 협상 가능한 견적에 제품을 추가할 수 없는 문제를 해결했습니다.
* **MDVA-33516**(*Adobe Commerce >=2.3.0 &lt;2.3.6*) - 구매요청 목록에서 번들 제품을 편집하면 오류가 발생하는 문제를 해결했습니다.
* **MDVA-33975**(*Adobe Commerce >=2.3.4 &lt;2.4.2*) - GraphQL 요청의 가격 계산과 관련된 여러 문제가 수정되었습니다.

## v1.0.13 {#v1-0-13}

* **MDVA-30858**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - **보고서** > **판매** > **[!DNL PayPal]** 결산에서 [!DNL PayPal] 결제 보고서를 사용할 수 없는 문제를 해결했습니다.
* **MCP-87**(*Adobe Commerce >=2.3.1 &lt;2.4.2*) - 큰 프로필의 카테고리 제품 및 주식 인덱서의 색인화 시간이 개선되었습니다.
* **MDVA-33106**(*Adobe Commerce >=2.3.0 &lt;2.4.2*&#x200B;의 경우) - cron `run` 명령을 실행한 후 다시 예약된 제품 변경 사항이 지워지는 문제를 해결했습니다.
* **MDVA-19391**(*Adobe Commerce >=2.3.0 &lt;2.3.5*) - `catalog_category_entity_text` 테이블의 NULL 설명 레코드로 인해 `analytics_collect_data`에서 오류가 발생하는 문제를 해결했습니다.
* **MDVA-20376**(*Adobe Commerce >=2.3.2 &lt;2.3.4*) - 주문 배치 후 로그인한 고객의 경우 `exception.log`에 *customerId = 1*&#x200B;인 엔터티가 없는 문제 해결
* **MDVA-23764**(*Adobe Commerce >=2.3.2 &lt;2.3.5*&#x200B;의 경우) - 동적 블록의 표시에 영향을 주는 `JsFooterPlugin.php`의 버그를 수정합니다.
* **MDVA-13203**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 전체 색인 재지정 후 *무결성 제한 위반 search_tmp_ table* 오류가 표시되는 문제를 해결했습니다.
* **MDVA-23426**(*Adobe Commerce >=2.3.3 &lt;2.3.5*&#x200B;의 경우) - Adobe Commerce에서 보낸 알림 전자 메일에 첨부 파일로 추가되는 내용이 포함된 빈 본문이 있는 문제를 해결했습니다.
* **MDVA-22150**(*Adobe Commerce >=2.3.1 &lt;2.3.4*&#x200B;의 경우) - 장바구니에 구성 가능한 제품이 있고 쿠폰이 적용된 고객이 관리자에서 해당 구성 가능한 제품을 사용하지 않도록 설정한 경우 로그인할 수 없는 문제를 해결했습니다.
* **MDVA-32545**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 관리자로부터 주문을 만들 때 송장이 자동으로 전송되지 않는 문제를 해결했습니다.
* **MDVA-32714**(*Adobe Commerce >=2.3.4 &lt;2.4.1*&#x200B;의 경우) - GraphQL 제품 쿼리에서 고객 그룹 가격이 작동하지 않는 문제를 해결했습니다.

## v1.0.12 {#v1-0-12}

* **MDVA-31399**(*Adobe Commerce >=2.3.2 &lt;2.4.2*&#x200B;의 경우) - *소계를 추가합니다(포함). 가격 규칙 조건에 대한* 옵션입니다.
* **MDVA-31236**(*Adobe Commerce >=2.4.0 &lt;2.4.2*) - 사용자 지정 리소스 액세스 권한이 있는 관리자가 2FA를 설정하거나 로그인할 수 없는 문제를 해결했습니다.
* **MDVA-30845**(*Adobe Commerce >=2.3.5 &lt;2.3.7*) - *죄송합니다. 현재 이 주문에 대해 사용 가능한 견적이 없습니다* 오류가 표시되고 UPS XML/USPS/DHL에 연결하지 못할 때 다른 배송 방법을 사용할 수 없는 문제가 해결되었습니다.
* **MDVA-32133**(*Adobe Commerce >=2.4.0 &lt;2.4.1*) - 특정 경우에 미디어 갤러리가 페이지 빌더에서 로드되지 않는 문제를 해결했습니다.
* **MDVA-12304**(*Adobe Commerce >=2.3.0*&#x200B;의 경우) - 최대 쿠키 수를 50개에서 200개로 늘립니다.
* **MDVA-32632**(*Adobe Commerce >=2.3.2 &lt;2.3.5*) - 주문이 결제 시스템에 표시되지만 Adobe Commerce에 표시되지 않는 문제가 수정되었습니다.
* **MDVA-32449** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2(B2B 확장 포함*) - 주문 내역이 매우 느리게 로드되거나 전혀 로드되지 않는 문제가 해결되었습니다.
* **MDVA-32739**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 비동기 전자 메일 알림을 사용하도록 설정하면 이전 판매 전자 메일이 전송되는 문제가 해결됩니다.

## v1.0.11 {#v1-0-11}

* **MC-38509**(*Adobe Commerce 2.3.6, 2.4.1*&#x200B;의 경우) - *새 고객 계정 만들기* 양식에서 잘못된 데이터를 수정한 후 *계정 만들기* 단추가 비활성화되는 문제를 해결했습니다.
* **MDVA-31006**(*Adobe Commerce 2.3.0, 2.3.1*&#x200B;의 경우) - [!DNL Paypal Express] 결제를 사용하여 주문한 후 중복 주문이 표시되는 문제를 해결했습니다.
* **MDVA-25602**(*Adobe Commerce 2.3.0*&#x200B;의 경우) - Chrome 80 브라우저 및 API 응답을 고객 로그인 페이지로 리디렉션하면 [!DNL PayPal Payflow Pro] 결제 방법 및 기본적으로 쿠키를 `SameSite=Lax`(으)로 처리하는 문제가 수정됩니다.

## v1.0.10 {#v1-0-10}

패치 버전에 대한 사소한 수정 사항

## v1.0.9 {#v1-0-9}

* **MDVA-31363**(*Adobe Commerce >=2.3.2 &lt;2.4.2*) - *전체 장바구니에 대한 고정 금액 할인* 작업이 사용되는 경우 쿠폰이 포함된 장바구니 가격 규칙이 GraphQL을 통해 적용되지 않는 문제를 해결했습니다.
* **MDVA-30889**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 가상 및 단순 제품을 옵션으로 사용하여 번들을 호출한 후 오류가 발생하는 문제를 해결합니다.
* **MDVA-31791**(*Adobe Commerce >=2.3.4 &lt;2.3.5*) - 대상 규칙 또는 연결된 제품이 사용되는 경우 제품 페이지의 성능이 향상됩니다.
* **MDVA-31168**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 제품 내보내기 CSV 파일이 표시되지 않고 메모리 할당 오류가 있는 문제를 해결했습니다.
* **MDVA-32313**(*Adobe Commerce >=2.3.0 &lt;2.3.4*&#x200B;의 경우) - 구성 가능한 제품을 잘못된 구성 옵션으로 위시리스트에 추가할 수 있는 문제를 해결했습니다.
* **MDVA-31759**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - CSV 가져오기 중에 제품이 *dropdown* 및 *textarea* 특성 값으로 업데이트되지 않는 문제를 해결했습니다.
* **MDVA-32012**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 한국 및 아르헨티나의 우편번호를 확인할 수 없는 문제를 수정합니다.
* **MDVA-31640** (*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - REST API를 통해 특별 가격을 업데이트할 수 없는 문제를 수정했습니다.
* **MDVA-28651** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || B2B 확장이 있는 >2.4.0(*) - REST API를 통해 협상 가능한 견적을 로드할 때 성능 문제가 발생하는 문제를 해결합니다.

## v1.0.8 {#v1-0-8}

* **MDVA-31242**(*Adobe Commerce >=2.3.0 &lt;2.4.1, B2B 확장 포함*) - 대변 메모 표에 잘못된 통화 기호가 표시되는 문제를 해결했습니다.
* **MDVA-31295**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 부분 주문이 완료되고 항목이 과세될 때 보상 포인트가 계산되지 않는 문제를 수정합니다.
* **MDVA-30112**(*Adobe Commerce >=2.3.4 &lt;2.4.2*) - 주문 수가 *bunch-size* 값을 초과할 경우 Adobe Commerce에서 *보류 중* 상태의 주문이 일치하지 않는 것으로 간주하는 문제를 해결했습니다.
* **MDVA-31150**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - Rest API 호출에서 청구서를 게시하고 스토어 신용 카드 및 기프트 카드 계정에서 주문을 부분적으로 결제했을 때 GET Invoice Rest API 호출에서 스토어 신용 카드 및 기프트 카드 잔액이 반환되지 않는 문제를 해결했습니다.
* **MDVA-30963**(*Adobe Commerce >=2.3.2 &lt;2.4.2*&#x200B;의 경우) - 제품 필터링 결과가 관리자의 *모든 저장소 보기* 범위에 지정된 값만 포함하도록 설정되는 경우 저장소 보기 수준에서 재정의된 값이 있는 제품을 포함하는 문제를 해결했습니다.
* **MDVA-29954** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || B2B 확장이 있는 2.4.2*) - *새 회사 등록 요청* 및 *회사에 연결됨* 전자 메일이 잘못된 주소에서 전송되는 문제를 해결합니다.
* **MDVA-28357** (*Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - 표준 분석기를 사용자 지정 분석기로 바꾸고 [!DNL ElasticSearch] 인덱스의 SKU 필드에 대한 키워드 토큰화기로 바꾸어 와일드카드 검색 쿼리가 하이픈(&quot;-&quot;)이 포함된 SKU에서 작동하도록 합니다.

## v1.0.7 {#v1-0-7}

* **MDVA-30972**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - WebApi를 사용하여 부분 선적을 만든 후 사용자 지정 주문 상태가 *처리*(으)로 변경된 문제를 해결했습니다.
* **MDVA-30428**(*Adobe Commerce >=2.3.4 &lt;2.3.5*) - 이 제품이 사용자 지정 인벤토리 소스에 할당된 경우 고객이 제품을 위시리스트에 추가할 수 없는 문제를 해결했습니다.
* **MDVA-30594**(*Adobe Commerce >=2.3.0 &lt;2.4.2*&#x200B;의 경우) - FPT가 구성된 경우 체크아웃 중에 여러 주소가 있는 주문을 저장할 수 없는 문제를 해결했습니다.
* **MDVA-29148**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - API 호출을 통해 제품을 만들 때 문제를 해결했습니다. `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`(Multiselect와 같은) 유형의 제품 사용자 지정 특성은 페이로드에 값이 제공되지 않은 경우 기본값을 사용하지 않습니다.
* **MDVA-30837**(*Adobe Commerce >=2.3.1 &lt;2.3.5*) - 무료 배송 방법 구성에 구성 설정 *세금에 포함: 예/아니요*&#x200B;를 추가했습니다. *세금에 포함*&#x200B;이 *예*(으)로 설정되면 최소 주문 금액은 소계 + 세금으로 계산됩니다. *세금에 포함*&#x200B;이 *아니요*(으)로 설정되면 최소 주문 금액이 소계로 계산됩니다
* **MDVA-25028** (*Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - 사기 필터가 트리거될 때 [!DNL PayPal Payflow Pro]을(를) 사용하여 수행한 주문이 [사기 혐의] 상태로 설정되지 않은 경우 문제를 수정합니다.
* **MDVA-31224**(*Adobe Commerce >=2.3.3 &lt;2.3.5*) - 번들 제품에 대한 `catalog_product_price` 다시 인덱싱 작업의 성능을 개선합니다.
* **MDVA-31321**(*Adobe Commerce >=2.3.2 &lt;2.3.5*) - *모두 표시*&#x200B;를 선택하면 빈 페이지가 수정됩니다(오류). [!DNL Elasticsearch]이(가) 제품 id의 큰 목록을 반환합니다. 이 시나리오에서는 order by 절이 잘못된 SQL 형식으로 변환됩니다.
* **MDVA-30815**(*Adobe Commerce >=2.3.2 &lt;2.3.4*&#x200B;의 경우) - 검색 결과 페이지에 표시할 검색 결과 수를 변경하면 Adobe Commerce에 빈 페이지가 표시되는 문제를 해결합니다. [!DNL Elasticsearch]은(는) 이제 페이지당 표시되는 검색 결과의 수를 변경할 때 범주 페이지의 결과를 올바르게 표시합니다.
* **MDVA-30782**(*Adobe Commerce >=2.3.5 &lt;2.4.2*&#x200B;의 경우) - 장바구니 규칙과 관계없이 동적 블록이 표시되는 문제를 해결했습니다.
* **MDVA-31021**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - `module-catalog-import-export/Model/Import/Product/Option.php`에서 성능 문제가 있는 문제를 해결했습니다. `catalog_product_option` 테이블에 ~100k개 이상의 레코드가 있는 경우 단일 제품을 사용하는 새 CSV의 유효성을 검사하는 데 10초 미만이 소요됩니다.
* **MDVA-31007**(*Adobe Commerce >=2.4.0 &lt;2.4.1*) - 사용자 지정 주소 특성이 내 계정 영역 및 백엔드의 주문 세부 사항 페이지에 올바르게 표시되지 않는 문제가 수정되었습니다.
* **MDVA-29389**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - `analytics_collect_data` cronjob이 *호스트 매개 변수(예: localhost:3306)* 내에서 포트를 구성해야 한다고 하는 고급 보고 문제를 해결했습니다.
* **MDVA-31343**(*Adobe Commerce >=2.3.4 &lt;2.3.6*&#x200B;의 경우) - 범주가 예약되어 있을 때 제거된 본문 클래스 `page-layout-category-full-width`의 문제를 해결합니다.
* **MDVA-30945**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 장바구니 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`을(를) 업데이트할 때 치명적인 오류 메시지가 표시되는 문제를 해결했습니다.

## v1.0.6 {#v1-0-6}

* **MDVA-28993**(*Adobe Commerce >=2.3.4 &lt;2.4.0*&#x200B;의 경우) - *Minimum이 [!DNL Elasticsearch] 엔진에 대해* 기능과 부분 검색을 일치해야 합니다. 검색 쿼리에서 하이픈 문제를 해결합니다.
* **MDVA-30102**(*Adobe Commerce >=2.3.2 &lt;=2.4.0*&#x200B;의 경우) - 레이아웃 캐시에 TTL이 없으므로 Redis 캐시가 빠르게 증가하는 문제를 해결했습니다.
* **MDVA-30599**(*Adobe Commerce >=2.3.4 &lt;=2.4.0*&#x200B;의 경우) - API를 사용하여 만든 게스트 견적이 로그인한 고객의 견적으로 잘못 표시되는 문제를 해결했습니다.
* **MDVA-29446**(*Adobe Commerce >=2.3.3 &lt;=2.4.0*&#x200B;의 경우) - 체크아웃 중에 해당 배송 방법 가격이 0으로 표시되는 문제를 해결했습니다.
* **MDVA-30357**(*Adobe Commerce >=2.3.2 &lt;=2.4.0*&#x200B;의 경우) - cron에서 사이트 맵을 생성할 때 잘못된 이미지 URL이 생성되는 문제를 수정합니다.
* **MDVA-30565**(*Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*&#x200B;의 경우) - 영구 장바구니가 활성화된 경우 *상점 체크아웃에서 게스트 고객에 대해 cartid = 0* 오류가 표시되지 않는 문제를 해결했습니다.
* **MDVA-29787**(*Adobe Commerce >=2.3.0 &lt;=2.4.0*&#x200B;의 경우) - *이(가)* 조건 중 하나이면 표시할 제품을 정의하는 데 사용되는 경우 관련 제품에 대한 대상 규칙이 작동하지 않는 문제를 해결했습니다.
* **MDVA-30977**(*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*&#x200B;의 경우) - 다시 인덱싱한 후 범주에서 임의의 제품이 누락된 문제를 해결했습니다.
* **MDVA-28202**(*Adobe Commerce >=2.3.4 &lt;=2.4.2*&#x200B;의 경우) - MSI를 사용할 때 계층 탐색 기능이 구성 가능한 제품을 올바르게 필터링하지 못하는 문제를 해결했습니다.
* **MDVA-28300**(*Adobe Commerce >=2.3.0 &lt;2.3.6*) - GQL 요청이 카탈로그 가격 규칙의 가격 변경을 반영하지 않는 문제를 해결했습니다.
* **MDVA-31006**(*Adobe Commerce >=2.3.2 &lt;=2.4.2*&#x200B;의 경우) - [!DNL Paypal Express] 결제를 사용하여 주문한 후 중복 주문이 표시되는 문제를 해결했습니다.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 검색 엔진으로 [!DNL Elasticsearch]을(를) 사용한 경우 부울 유형 제품 특성에 대한 *No* 값이 계층 탐색에 포함되지 않은 계층 탐색 문제를 해결했습니다.
* **MDVA-28191**(*Adobe Commerce >=2.3.3 &lt;2.4.2*&#x200B;의 경우) - 관리자를 통해 주문을 만드는 동안 결제 방법이 로드되지 않는 문제를 해결했습니다.
* **MDVA-29959**(*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1, B2B 확장 포함*) - *회사* 권한을 가진 제한된 관리자 사용자가 회사 계정을 삭제할 수 없는 문제를 해결했습니다.
* **MDVA-30265**(*Adobe Commerce >=2.3.3 &lt;2.4.2*&#x200B;의 경우) - 송장 생성 후 배송 추적 링크가 작동하지 않는 문제를 수정합니다.
* **MDVA-28409** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 데이터베이스의 만료된 따옴표 수가 많을 때 `sales_clean_quotes` cron 작업이 *메모리 부족* 오류와 함께 실패하는 문제를 수정합니다.
* **MDVA-30593**(*Adobe Commerce >=2.3.0 &lt;2.3.4*&#x200B;의 경우) - Quote Lifetime 설정에 따라 만료된 Quote가 정리되지 않는 문제를 수정합니다.
* **MDVA-30107**(*Adobe Commerce >=2.3.0 &lt;2.3.6*&#x200B;의 경우) - 저장소 보기에 다른 기본 URL을 사용하는 경우 저장소 전환기가 예상대로 작동하지 않는 문제를 해결했습니다.
* **MDVA-28763**(*Adobe Commerce >=2.3.2 &lt;2.3.4*&#x200B;의 경우) - REST API를 사용하여 제품 정보를 두 번 이상 업데이트한 후 제품 이미지가 복제되는 문제를 해결했습니다.
* **MDVA-30284**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 다음 *[!DNL Elasticsearch]오류로 인해 카탈로그 검색 인덱서가 실패하는 문제를 해결했습니다. 인덱스의 총 필드 제한을 초과했습니다.*
* **MDVA-29042**(*Adobe Commerce >=2.3.3 &lt;=2.3.4-p2, B2B 확장 포함*) - 새 제품이 공유 카탈로그에 추가된 후 카탈로그 권한이 *허용*(으)로 자동 변경되는 문제를 해결했습니다.
* **MDVA-30428**(*Adobe Commerce >=2.3.3 &lt;2.4.2*&#x200B;의 경우) - 이 제품이 사용자 지정 인벤토리 소스에 할당된 경우 고객이 제품을 위시리스트에 추가할 수 없는 문제를 해결했습니다.
* **MDVA-28661**(*Adobe Commerce >=2.3.0 &lt;2.4.2, B2B 확장 포함*) - 회사 관리자가 변경된 후 회사 사용자 회사 계정 섹션에 오류가 발생하는 문제를 해결했습니다.

## v1.0.4 {#v1-0-4}

* **MDVA-30195**(*Adobe Commerce 2.3.1 - 2.3.4-p2*&#x200B;의 경우) - 데이터베이스 이름이 너무 길어 프런트 엔드에서 범주가 업데이트되지 않는 경우 cron 작업이 실패하는 문제를 해결했습니다.
* **MDVA-30106**(*Adobe Commerce ^2.3.0*&#x200B;의 경우) - 체크아웃 결제 중에 *null인 속성 &#39;길이&#39;를 읽을 수 없음* 오류가 JS 콘솔에서 로드되지 않는 문제를 해결했습니다.
* **MDVA-28656** (*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - 필요한 결제 정보가 없는 주문(예: 100% 할인)이 발생하고 주문에 대한 송장이 만들어진 경우 주문 상태가 완료 대신 *마감됨*(으)로 변경되는 문제를 해결합니다.
* **MDVA-30209**(*Adobe Commerce 2.3.0 - 2.3.3-p1*&#x200B;의 경우) - 고객이 계정 정보를 업데이트한 경우 고객 그룹이 기본값으로 변경된 문제를 수정합니다.
* **MDVA-30123**(*Adobe Commerce >=2.3.4 &lt;2.4.2*&#x200B;의 경우) - 특성 옵션 레이블이 GraphQL 쿼리에 대해 올바르게 변환되지 않는 문제를 수정합니다.
* **MDVA-29996**(*Adobe Commerce >=2.3.3 &lt;2.4.2*&#x200B;의 경우) - 범주 권한을 사용하도록 설정한 후 범주 페이지가 전체 페이지 캐시에 의해 캐시되지 않는 문제를 해결합니다.
* **MDVA-30164**(*Adobe Commerce >=2.3.1 &lt;2.4.2*&#x200B;의 경우) - 사용자 지정 고객 특성이 있는 경우 고객 그리드에서 고객 레코드를 내보낼 수 없는 문제를 해결했습니다.
* **MDVA-30444**(*Adobe Commerce >=2.3.0 &lt;2.4.1*) - GraphQL을 사용하여 주문한 주문에 대해 확인 이메일이 전송되지 않는 문제를 해결했습니다.
* **MDVA-30490**(*Adobe Commerce 2.3.4 - 2.3.5-p2*&#x200B;의 경우) - 제품 중 하나에 짧은 설명이 비어 있는 경우 제품 비교에서 500 오류 페이지가 표시되는 문제를 해결했습니다.
* **MDVA-30232**(*Adobe Commerce >=2.3.1 &lt;2.4.1*) - 원래 주문에 기프트 카드가 포함된 경우 순서를 변경할 수 없는 문제를 해결했습니다.
* **MDVA-29965**(*Adobe Commerce >=2.3.3 &lt;2.4.0*&#x200B;의 경우) - 장바구니에 제품을 추가할 때 고객에게 잘못된 양식 키 오류가 발생하는 문제를 해결했습니다.
* **MDVA-30008**(*Adobe Commerce >=2.3.0 &lt;2.4.2*) - 공개 카탈로그에 있는 제품에 대해 관리 API를 통해 주문할 수 없는 B2B 문제를 해결했습니다.
* **MDVA-22469**(*Adobe Commerce 2.3.2-p2 - 2.3.3-p1*&#x200B;의 경우) - Adobe Commerce 2.3.3으로 업그레이드한 후 페이지 빌더가 관리 패널에서 작동하지 않고 일부 JS 및 CSS 파일이 로드되지 않는 문제를 해결했습니다.
* **MC-35984**(*Adobe Commerce >=2.4.0 &lt;2.4.1*) - 반품 승인(RMA)에 대한 배송 레이블을 만든 후 판매자가 반품 페이지의 페이지 요소와 상호 작용할 수 없는 문제를 해결했습니다.

## v1.0.3 {#v1-0-3}

* **MDVA-25602**(*Adobe Commerce 2.3.0 - 2.3.4*&#x200B;의 경우) - Chrome 80 브라우저 및 API 응답을 고객 로그인 페이지로 리디렉션하면 기본적으로 [!DNL PayPal Payflow Pro] 결제 방법 및 `SameSite=Lax`(으)로 쿠키를 처리하는 문제가 해결됩니다.
* **MDVA-26694** (*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - 다르게 만료되도록 예약되어 있지만 제품 및 카탈로그 캐시가 매일 만료되는 문제를 수정합니다.
* **MDVA-27825**(*Adobe Commerce >=2.3.0 &lt;2.4.1*&#x200B;의 경우) - 메모리 누출로 인해 대용량 데이터 내보내기가 실패하는 문제를 해결했습니다.
* **MDVA-29085**(*Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*&#x200B;의 경우) - 회사가 API로 만들어진 경우 필요한 새 회사 이메일이 전송되지 않는 B2B 문제를 수정합니다.
* **MDVA-29344**(*Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*&#x200B;의 경우) - 헤더 요소에서 텍스트 요소로 텍스트를 복사한 후 Page Builder가 중단되는 문제를 해결합니다.
* **MDVA-29835**(*Adobe Commerce >2.3.1 &lt;2.4.2*&#x200B;의 경우) - 기프트 카드 주문에 두 개의 코드가 대신 포함된 문제가 해결되었습니다.
* **MDVA-30052**(*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - 개인 콘텐츠(로컬 저장소)가 제대로 채워지지 않아 성능 문제가 발생하는 문제를 해결했습니다.
* **MDVA-30131** (*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - 검색 엔진으로 [!DNL Elasticsearch]을(를) 사용한 경우 부울 유형 제품 특성에 대한 *No* 값이 계층 탐색에 포함되지 않은 계층 탐색 문제를 해결했습니다.
* **MDVA-35514**(*Adobe Commerce >=2.4.0 &lt;2.4.1*) - 패키지 만들기 모달 창에서 배송 레이블을 만들고 주문한 제품을 패키지에 추가하는 문제를 해결했습니다.
