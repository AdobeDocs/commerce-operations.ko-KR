---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.61에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.61

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.61에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.61에는 다음 패치가 포함됩니다.

1. **ACP2E-3689**: 더 심층적인 수준에 카테고리 트리가 표시되고 앵커/비앵커 관계가 반영된 여러 문제가 수정되었습니다.
1. **ACP2E-3705**: `indexer_update_all_views`을(를) 설정할 때 `MAGE_INDEXER_THREADS_COUNT` cron 실행이 실패하는 문제를 해결했습니다.
1. **ACSD-63883**: [!UICONTROL Requisition List]이(가) `items_count` 응답에서 잘못된 [!DNL GraphQL]을(를) 반환하는 문제를 해결했습니다.
1. **ACSD-63974**: 한 번에 모든 레코드 대신 페이지당 레코드 수로 제한된 레코드의 일부만 표시하는 상점 앞 [!UICONTROL Requisition List] 그리드에 페이지 매김 기능을 추가하여 항목이 너무 많을 때 [!UICONTROL Requisition List] 페이지를 로드하는 데 시간이 너무 오래 걸리는 문제를 해결했습니다.
1. **ACSD-64178**: 제품 특성이 수천 개일 경우 [!UICONTROL Attribute Set] 편집 페이지가 느리게 로드되는 문제를 해결했습니다.
1. **ACSD-64209**: cron 스케줄러가 상태가 **[!UICONTROL ordered]**&#x200B;인 견적을 제외하지 않고 모든 협상 가능한 견적을 검색하여 전자 메일 또는 전자 메일이 트리거되는 문제를 해결했습니다.
1. **ACSD-64431**: 요청에 쿠폰 코드 정보가 포함된 `placeOrder` 돌연변이로 인해 더 이상 내부 오류가 발생하지 않고 대신 주문이 성공적으로 수행되었음을 알 수 있습니다.
1. **ACSD-64467**: 스토어 보기 수준에서 범주 설명을 저장한 후 WYSIWYG 편집기가 비어 있는 문제가 해결되었습니다.
1. **ACSD-64546**: UPS 배송 레이블을 만드는 동안 UI에 일반 오류 메시지가 발생하고 *문자열 변환에 대한 배열* 예외가 로그에 저장되는 문제를 해결하여 실제 오류가 UI에 표시되고 올바른 오류 메시지가 로그에 저장되도록 합니다.
1. **ACSD-64684**: *천(1,000)*&#x200B;의 쉼표(천 구분 기호)로 인해 값이 *999*&#x200B;보다 큰 기프트 카드를 편집하고 저장할 때 유효성 검사 오류가 발생하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
