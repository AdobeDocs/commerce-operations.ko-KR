---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: 이 하위 섹션에서는 [!DNL Quality Patches Tool] (QPT) v1.1.86에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9e453ce98ac552d883469e20e65516be8ef02b4f
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%
---
# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.86

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.86에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.86에는 다음 패치가 포함됩니다.


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**: 관리자에서 주문을 만드는 동안 페이지를 새로 고치면 동일한 SKU가 여러 번 추가되는 문제가 해결되었습니다.
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**: 많은 권한이 있는 범주에 대한 **[!UICONTROL Category Permissions]**&#x200B;을(를) 보거나 편집하면 브라우저가 응답하지 않는 문제를 해결했습니다.
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**: 관리자에서 RMA를 보거나 저장하는 경우 **[!UICONTROL Action Logs]** 보고서에 RMA 번호가 표시되지 않는 문제가 해결되었습니다.
1. **ACP2E-5057**: **[!UICONTROL Catalog Price Scope]**&#x200B;이(가) **[!UICONTROL Website]**(으)로 설정된 경우 번들 제품에 대한 [!DNL GraphQL] 쿼리가 웹 사이트별 가격 대신 전역 번들 옵션 가격을 반환하는 문제를 해결했습니다.
1. **ACP2E-5061**: 범주 머천다이징 규칙이 `AND` 조건을 여러 값과 일치하는 조건과 결합할 수 없는 문제를 해결했습니다.
1. **[ACP2E-5071](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5071.md)**: 장바구니에 이미 사용 가능한 전체 수량이 포함되어 있을 때 재고 비가용성 메시지가 제품 페이지에 항상 표시되지 않는 문제를 해결했습니다.
1. **[ACP2E-5061](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5061.md)**: 카테고리 머천다이징 규칙이 AND 조건을 여러 값 중 하나와 일치하는 조건과 결합할 수 없는 문제를 해결했습니다.
1. **ACP2E-5071**: 장바구니에 이미 사용 가능한 전체 수량이 포함되어 있을 때 재고 비가용성 메시지가 제품 페이지에 항상 표시되지 않는 문제를 해결했습니다.
1. **ACP2E-5094**: `MAGENTO_DC_*` 환경 변수가 설정되어 있을 때 페이지 로드 속도가 현저히 느려지는 문제를 해결했습니다.
1. **[ACP2E-5134](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5134.md)**: 회사 공유 카탈로그에서 번들에 포함된 제품을 제거하면 번들 제품이 장바구니에 남으며 장바구니와 체크아웃 중에 오류가 발생하는 문제를 해결했습니다.
1. **[ACP2E-5118](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5118.md)**: **[!UICONTROL Translations]** 캐시를 사용하지 않도록 설정할 때 [!DNL Page Builder] 미리 보기가 렌더링되지 않는 문제를 해결했습니다.
1. **ACP2E-5146**: 다른 웹 사이트의 고객이 관리자 사용자와 동일한 ID를 가지고 있을 때 특정 웹 사이트로 제한된 관리자 사용자가 고객을 삭제할 수 없는 문제를 해결했습니다.
1. **[ACP2E-5176](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5176.md)**: Google Tag Manager를 통해 Google Analytics 4로 전송된 전자 상거래 이벤트가 Universal Analytics 형식을 사용하고 여러 체크아웃 이벤트를 생략하는 문제를 해결했습니다.
1. **ACP2E-5185**: 범주 트리에서 범주를 이동하면 오류 `There was a category move error`이 표시되거나 저장소에 많은 URL 재쓰기가 있을 때 완료되는 데 몇 분이 걸리는 문제를 해결했습니다.
1. **[ACP2E-4191](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-4191.md)**: EAV 유형 및 특성 캐시가 비활성화될 때 특정 REST API 요청이 무한 루프를 입력하는 문제를 해결했습니다.
1. **ACP2E-4973**: **[!UICONTROL In-Store Delivery]**&#x200B;에서 다른 게재 메서드로 전환해도 장바구니에서 연결된 저장소 주소가 지워지지 않는 문제가 해결되었습니다.
1. **ACP2E-4191**: **[!UICONTROL EAV types and attributes]** 캐시가 비활성화될 때 특정 REST API 요청이 무한 루프를 입력하는 문제를 해결했습니다.
1. **[ACP2E-4973](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-4973.md)**: 매장 배달에서 다른 배달 방법으로 전환해도 장바구니에서 연결된 매장 주소가 지워지지 않는 문제를 해결했습니다.
1. **ACP2E-5221**: 저장소 및 고객 그룹이 많은 설치에서 **[!UICONTROL Quick Order]**&#x200B;을(를) 사용하도록 설정할 때 **[!UICONTROL Catalog Product Permissions]** 인덱서가 훨씬 더 오래 걸리는 문제를 해결했습니다.
1. **[ACP2E-5245](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5245.md)**: 첫 번째 주문에서 배송 및 청구에 동일한 주소를 사용하는 새로 등록한 고객이 다음 체크아웃 중에 해당 주소가 두 번 표시되는 문제를 해결했습니다.
1. **ACP2E-5248**: [!DNL PHP] 8.5에서 **[!UICONTROL Add Product]** 페이지를 열 때 **[!UICONTROL Edit Product Status]** 권한이 없는 관리자 사용자에게 `null as array offset` 사용 중단 오류가 표시되는 문제를 해결했습니다.
1. **ACP2E-5254**: 고객이 캐시를 지울 때까지 목록을 열 때 구매요청 목록에 추가된 제품이 표시되지 않는 문제를 해결했습니다.
1. **ACP2E-5268**: **[!UICONTROL Enable Frontend Resize]**&#x200B;이(가) **[!UICONTROL No]**(으)로 설정되어 있을 때 구성 가능한 제품을 만들지 못하는 문제가 해결되었습니다.
1. **[ACP2E-3752](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3752.md)**: 제품 가져오기 처리에서 오류가 발생하는 문제를 해결했습니다. *경고: 제품 가져오기 작업이 많이 생성될 때 정의되지 않은 배열 키 &quot;apply_to&quot;*&#x200B;입니다.
1. **ACP2E-5280**: **[!UICONTROL Category Permissions]**&#x200B;이(가) 활성화된 동안 로그인할 때 고객이 오류가 발생하는 문제를 해결합니다.
1. **ACP2E-5295**: 동일한 프로세스에서 **[!UICONTROL Inventory]** 인덱서 이후에 실행할 때 `Fail in child process` 오류와 함께 병렬 제품 가격 리인덱싱이 실패하는 문제를 해결했습니다.
1. **ACP2E-5298**: 장바구니 가격 규칙에 대한 보기 전용 액세스 권한이 있는 관리자가 쿠폰 코드를 생성하거나 삭제할 수 있는 문제를 해결했습니다.
1. **ACP2E-5333**: **[!UICONTROL is not]** 연산자를 사용하는 **[!UICONTROL Total Number of Orders]** 조건으로 고객 세그먼트를 새로 고치지 못하고 하나 이상의 값이 `Unknown operator specified` 오류로 인해 실패하는 문제를 해결했습니다.
1. **[ACP2E-5425](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5425.md)**: 고객이 동일한 주문에 대해 중복 주문 확인 이메일을 받는 문제를 해결합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
