---
title: '개요: [!DNL Quality Patches Tool](QPT) v1.1.37'
description: 이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.37에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%
---
# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.37

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.37에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.37에는 다음 패치가 포함됩니다.

1. **ACSD-52613**: rest API에서 `Inventory_source` 항목을 업데이트하지 않았더라도 캐시와 인덱스가 새로 고침되는 문제를 해결했습니다.
1. **ACSD-51884**: resize 명령을 실행한 후 제품 이미지 캐시 경로가 올바르지 않게 되는 문제를 해결했습니다.
1. **ACSD-53628**: CSV 판매 주문 보고서에 잘못된 특수 문자가 표시되는 문제를 해결했습니다.
1. **ACSD-49843**: *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* 설정이 활성화된 온라인 결제 방법으로 주문 항목에 대한 자동 청구가 발행된 후 제품 다운로드에 대한 링크를 사용할 수 없는 문제를 해결했습니다.
1. **ACSD-53148**: 구성 가능한 동일한 제품을 장바구니에 추가하기 위해 GraphQL에서 두 개의 병렬 요청이 발생하여 동일한 제품 SKU를 사용하는 장바구니에 두 개의 개별 항목이 발생하는 문제를 해결했습니다.
1. **ACSD-47054**: 미리 보기 색인 다시 지정이 모든 스토어에 대해 색인 다시 지정으로 실행되어 속도가 느려지는 문제를 해결했습니다.
1. **ACSD-52606**: 사용자가 **[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;을(를) 클릭할 때 *주문이 픽업될 준비가 되지 않았습니다*. 오류 메시지가 표시되는 문제를 해결했습니다.
1. **ACSD-51574**: 이미지를 같은 이름의 다른 이미지로 바꾼 후 프론트엔드에서 이미지가 업데이트되지 않는 문제를 해결했습니다.
1. **ACSD-53728**: 제품 EAV 인덱서를 완료하는 데 시간이 더 오래 걸리는 문제를 해결했습니다.
1. **ACSD-53979**: 시작 메시지에 작은 따옴표가 포함된 경우 홈 페이지에서 발생하는 JS 문제를 해결합니다.
1. **ACSD-52143**: 제품 가져오기 후 사용자 지정 옵션이 제거되던 문제를 해결했습니다.
1. **ACSD-53750**: 다중 스레드 `catalog_product_price` 다시 인덱싱하는 동안 *끊어진 파이프 또는 닫힌 연결을 수정*&#x200B;합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
