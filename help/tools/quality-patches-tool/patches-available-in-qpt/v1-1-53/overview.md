---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.53에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.53

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.53에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.53에는 다음 패치가 포함됩니다.

1. **ACSD-48318**: 환경 에뮬레이션 중첩이 허용되지 않는 문제를 해결했습니다. 이제 `getInfoBlockHtml()` 호출 동안 에뮬레이션이 중지되면 `send()` 호출 동안 에뮬레이션이 시작됩니다.
1. **ACSD-59930**: 회사 *[!UICONTROL Create]*, *[!UICONTROL Save]* 및 *[!UICONTROL Delete]* 흐름의 성능을 개선합니다.
1. **ACSD-60584**: 한 웹 사이트에서 사용자에 대해 만든 액세스 토큰이 다른 웹 사이트의 고객 정보에 액세스하거나 변경할 수 있는 문제를 해결했습니다.
1. **ACSD-60804**: 삭제된 회사에 연결된 고객을 편집하면 *null에서 멤버 함수 `getSuperUserId()`에 대한 호출 오류*&#x200B;이(가) 발생하는 문제를 해결했습니다.
1. **ACSD-61133**: `sales_clean_quotes` 크론이 승인되지 않은 구매 주문에서 견적을 삭제하는 문제를 해결했습니다.
1. **ACSD-61528**: GraphQL을 사용하여 [!UICONTROL Admin]에서 역할을 검색해도 결과가 반환되지 않는 문제를 해결했습니다.
1. **ACSD-61553**: 우선 순위가 다른 여러 할인 및 *[!UICONTROL Maximum Qty Discount is Applied To]*&#x200B;이(가) 제품에 적용될 때 *[!UICONTROL Cart Price Rule]* 할인이 잘못 계산되는 문제를 해결했습니다.
1. **ACSD-61667**: *매장 내 픽업*&#x200B;이 있는 원본이 많은 경우 배송을 만들기 위한 인벤토리 성능을 향상시킵니다.
1. **ACSD-61969**: 사용자가 구성된 쿠폰 코드와 정확히 일치하는 대/소문자 구분 쿠폰 코드를 입력해야 하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
