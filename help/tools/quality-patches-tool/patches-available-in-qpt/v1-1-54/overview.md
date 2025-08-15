---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.54에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.54

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.54에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.54에는 다음 패치가 포함됩니다.

1. **ACSD-60267**: 구성 가능한 제품 옵션을 통해 FPT가 포함된 간단한 제품을 장바구니에 직접 추가할 때는 고정 제품 세금(FPT)이 올바르게 적용되지만 이러한 제품을 선택할 때는 실패하는 문제를 해결했습니다.
1. **ACSD-61103**: 고객이 API 끝점을 통해 성공적으로 로그인한 후 `customer_entity` 테이블의 오류 수가 0으로 재설정되지 않는 문제를 해결했습니다.
1. **ACSD-61134**: 쇼핑객이 [!DNL Braintree Vault] 확인란을 선택 취소하여 청구 주소를 업데이트할 때 체크아웃 워크플로에서 *[!UICONTROL My billing and shipping address are the same]* 결제 방법이 자동으로 선택 취소되는 문제를 해결했습니다.
1. **ACSD-61199**: 기존 계층이 있는 CMS 페이지를 편집할 때 CMS 페이지 계층 구조 탭에 적절한 트리 구조가 표시되지 않는 문제를 해결했습니다.
1. **ACSD-61200**: 매출의 *[!UICONTROL Total Amount]* 및 *[!UICONTROL Total Amount Actual]*&#x200B;에 대한 계산에 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;이(가) 누락되어 판매 주문 데이터가 일치하지 않는 문제를 해결했습니다.
1. **ACSD-61522**: 게스트 고객의 *[!UICONTROL First Name]* 및 *[!UICONTROL Last Name]* 필드에 전자 메일 주소를 입력하고 잘못된 주문 확인 전자 메일을 보낼 수 있는 문제를 해결했습니다.
1. **ACSD-61756**: `AdvancedSalesRule`개 필터의 성능을 개선합니다.
1. **ACSD-61799**: 고정 할인이 적용된 여러 장바구니 규칙이 견적에 적용되면 총 할인이 잘못 계산되는 문제가 수정되었습니다.
1. **ACSD-61845**: *text/html* accept 헤더만 사용하여 요청을 보낼 때 발생하는 오류를 수정합니다.
1. **ACSD-62056**: MSI가 설치된 경우 구성 가능한 제품에 대한 이미지 업로드가 실패하는 문제를 해결했습니다.
1. **ACSD-62485**: 회사가 만들어질 때 `async.operations.all` 소비자가 작동하지 않는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
