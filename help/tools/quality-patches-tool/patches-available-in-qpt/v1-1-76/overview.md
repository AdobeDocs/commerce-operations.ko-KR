---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.76에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 535934d92c0bd8a0d029c2c9a6c06be161db266f
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.76

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.76에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.76에는 다음 패치가 포함됩니다.
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**: 데이터 볼륨을 기반으로 두 가지 삭제 전략을 구현하여 카탈로그 규칙 제품 인덱스를 정리할 수 있도록 최대 쓰기 집합 크기 오류를 수정합니다.
1. **ACSD-67370**: PDP/PLP의 번들 제품 및 다중 통화 매장의 장바구니 페이지에 잘못된 가격이 표시된 여러 문제를 수정합니다.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**: 협상 가능 견적을 주문하면 추가 장바구니 라인이 견적에 잘못 추가되거나 병합되는 문제가 해결되었습니다. 이제 협상 가능한 견적 체크아웃의 마지막 단계를 마친 후 제품이 장바구니에 올바르게 추가됩니다.
1. **ACSD-69086**: 크론 작업에서 변경 로그 테이블을 지우지 못해 많은 양의 데이터를 처리할 때 [!DNL Galera Cluster]개의 충돌이 발생하는 문제를 해결했습니다.
1. **ACSD-69115**: 기본이 아닌 웹 사이트에 할당된 고객의 장바구니를 관리할 때 관리 사용자에게 장바구니 오류가 표시되지 않는 문제를 해결했습니다.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: [!DNL REST] API를 통해 보조 웹 사이트의 계층 가격을 업데이트하려고 할 때 기본 기본 웹 사이트를 삭제하고 보조 웹 사이트를 기본값으로 사용하면 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-69203**: 범주 조건에 여러 범주가 나열되어 있을 때 **[!UICONTROL Products List]** 위젯에서 잘못된 결과를 반환하는 문제를 해결했습니다.
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)**: 부분 송장 및 남은 수량 취소 시나리오에서 `times_used` 특성의 잘못된 처리로 인해 고객당 한 번 사용하도록 구성된 장바구니 가격 규칙 쿠폰이 여러 번 재사용되는 문제를 해결했습니다.
1. **ACSD-69308**: `special_price`이(가) 웹 사이트 수준(**[!UICONTROL All Store Views]**&#x200B;이 아님)에서만 설정되었을 때 카탈로그 가격 규칙이 적용되지 않는 문제를 해결했습니다. 수정 후에는 먼저 웹 사이트의 기본 스토어를 확인하여 카탈로그 가격 규칙이 올바르게 적용됩니다.
1. **ACSD-69261**: 부분 송장 및 남은 수량 취소 시나리오에서 `times_used` 특성의 잘못된 처리로 인해 고객당 한 번 사용하도록 구성된 장바구니 가격 규칙 쿠폰이 여러 번 재사용되는 문제를 해결했습니다.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**: `special_price`이(가) 웹 사이트 수준(**[!UICONTROL All Store Views]**&#x200B;이 아님)에서만 설정되었을 때 카탈로그 가격 규칙이 적용되지 않는 문제를 해결했습니다.
1. **ACSD-69319**: 하위 제품에 사용자 지정 원본의 재고가 있을 때 번들 가격이 제대로 색인화되지 않은 문제를 해결했습니다.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: SKU 사례를 수정하여 제품이 상점 앞에 품절 상태로 표시되는 문제를 해결했습니다.
1. **ACSD-69331**: 미디어 갤러리의 콘텐츠 작성자가 `create_folder` 권한만 있는 폴더를 만들 수 없는 문제를 해결했습니다. 수정 후에는 예상대로 폴더를 만들 수 있습니다.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: [!UICONTROL Admin]에 있는 제품의 수량을 장바구니에 있는 이전 수량보다 작게 줄이면 GraphQL을 통해 해당 장바구니에서 제품 수량을 편집할 수 없는 문제가 해결되었습니다.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**: 활성 예약 업데이트가 있는 제품에 대해 SKU 변경이 허용되는 문제를 해결했습니다. 수정 후 활성 업데이트 중에는 SKU 변경이 금지됩니다. 명확한 오류로 저장이 실패하고 관리 SKU 필드가 비활성화됩니다. 이렇게 하면 스테이징 롤백 중에 SKU 변경으로 인해 MSI 인벤토리 불일치가 발생하지 않습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
