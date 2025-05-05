---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.58에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f8473bbdedef26b291547d828e47a9ba08a5d142
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool] (QPT) v1.1.58

이 하위 섹션에서는 [!DNL Quality Patches Tool] (QPT) v1.1.58에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.58에는 다음 패치가 포함됩니다.

1. **ACSD-48570**: **URL에 스토어 코드 추가**&#x200B;가 *활성화됨*&#x200B;일 때 [!UICONTROL Admin] 암호 재설정 링크를 클릭하여 암호 재설정 페이지에 연결할 수 없는 문제를 해결했습니다. 이전에는 로그인 페이지 또는 404 페이지가 표시되었습니다.
1. **ACSD-62118**: 구매 주문 방법을 사용하여 [!DNL B2B]개의 주문을 했을 때 `sales_order_tax_item` 테이블이 완전히 업데이트되지 않는 문제를 해결했습니다.
1. **ACSD-63067**: 모든 제품 수량이 잘못 강조 표시되고 한 수량만 잘못된 경우 그룹화된 제품의 모든 제품에 대해 *[!DNL Please specify the quantity of product(s).]* 메시지가 표시되는 문제를 해결했습니다.
1. **ACSD-63090**: 장바구니에 추가된 후 제품이 삭제되면 장바구니 항목이 제거되는 문제를 해결합니다.
1. **ACSD-63182**: **[!DNL MSI]** *enabled*(으)로 중복 번들 제품을 저장할 때 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-63283**: 선물 레지스트리에서 항목을 주문하면 예외가 발생하고 선물 레지스트리 업데이트에 레지스트리에 속하지 않는 항목이 포함된 문제가 해결되었습니다.
1. **ACSD-63299**: 구성 가능한 제품에 대한 특별 가격이 상점 앞에 표시되지 않는 문제를 해결했습니다.
1. **ACSD-63325**: 빈 [!DNL GraphQL] 요청을 제출할 때 `Syntax Error: Unexpected <EOF>` 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-63329**: [!DNL REST API]을(를) 통해 제품을 만들 때 **[!UICONTROL Date]** 또는 **[!UICONTROL Date and Time]** 입력 형식의 특성에 대한 기본값이 설정되지 않는 문제를 해결했습니다.
1. **ACSD-63572**: 인덱서 프로세스가 종료된 경우 `CatalogRule` 인덱서 임시 테이블이 정리되지 않는 문제를 해결했습니다.
1. **ACSD-63578**: [!UICONTROL Admin]에서 **[!UICONTROL Add to Order by SKU]**&#x200B;의 **[!UICONTROL Delete]** 단추를 클릭해도 [!DNL SKU]이(가) 제거되지 않는 문제가 해결되었습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.

