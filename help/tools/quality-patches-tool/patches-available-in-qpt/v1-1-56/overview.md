---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.56에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.56

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.56에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.56에는 다음 패치가 포함됩니다.

1. **ACSD-63244**: JavaScript 오류로 인해 [!DNL Google Maps]이(가) 올바르게 렌더링되지 않는 문제와 *확인할 수 없는 TypeError가 많은 문제가 해결되었습니다._each는 [!UICONTROL Admin] 패널의 콘솔에* 함수가 아닙니다.
1. **ACSD-63242**: 항목이 10,000개가 넘는 카탈로그 제품을 추가할 때 가져오기 속도가 느려지는 문제를 해결했습니다.
1. **ACSD-63062**: 여러 겹치는 규칙이 적용될 때 잘못된 장바구니 할인 계산이 발생하는 문제를 해결했습니다.
1. **ACSD-62979**: GraphQL 헤더에서 잘못된 [!UICONTROL Store ID]을(를) 사용하면 치명적인 메모리 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-62971**: *[!UICONTROL Quantity]* 열에 숫자가 아닌 값이 있는 재고 소스를 가져오면 *수량*&#x200B;이(가) *0*(으)로 설정되는 문제가 해결되었습니다.
1. **ACSD-62872**: 일정 업데이트의 유효성이 잘못 검사되는 고유한 특성 유효성 검사 문제를 해결했습니다.
1. **ACSD-62755**: [!DNL TinyMCE] 7에서 글꼴 크기와 글꼴을 편집기 초기화 설정 내에 구체적으로 추가해야 하는 문제를 해결했습니다.
1. **ACSD-62670**: [!UICONTROL Products Ordered] 보고서를 CSV 및 XML로 내보내면 오류가 반환되는 문제를 해결했습니다.
1. **ACSD-62577**: 쿼리 및 테이블 인덱스를 최적화하여 상점 검색 쿼리의 성능이 저하되는 문제를 해결했습니다.
1. **ACSD-62475**: [!UICONTROL Gift Card] 제품이 장바구니에서 잘못 병합되는 문제를 해결했습니다.
1. **ACSD-62428**: [!DNL SKU]이(가) 검색 가능한 특성으로 설정되지 않은 경우 카탈로그 검색 색인에서 `is_out_of_stock`이(가) 잘못된 값으로 설정되는 문제를 해결합니다.
1. **ACSD-62355**: 구성 가능한 제품이 많은 값이 있는 많은 특성을 기반으로 할 때 구성 가능한 제품 편집 페이지의 로드 시간을 개선합니다.
1. **ACSD-61805**: [!DNL REST API]을(를) 통해 미납 주문 상태를 업데이트한 후 상점 첫 화면에서 제품이 품절되는 문제를 해결했습니다.
1. **ACSD-60811**: 현재 상태가 *[!UICONTROL Processing]* 또는 *[!UICONTROL Fraud]*&#x200B;인 경우에만 사용자 지정 값 또는 댓글로 주문 상태를 업데이트할 수 있는 문제를 해결했습니다.
1. **ACSD-62952**: [!UICONTROL Gift Registry] 날짜가 상점 앞에 잘못 표시되는 문제를 해결했습니다.
1. **ACSD-55339**: *0*(영)으로 시작하는 제품 [!DNL SKU]이(가) *0*&#x200B;을(를) 제거하여 견적이 업데이트되지 않도록 하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
