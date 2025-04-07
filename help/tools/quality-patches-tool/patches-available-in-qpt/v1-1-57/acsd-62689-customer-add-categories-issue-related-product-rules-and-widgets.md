---
title: 'ACSD-62689: [!UICONTROL Related Product Rules]의 범주 및 깊이 4 이후의 위젯을 추가할 수 없습니다.'
description: 고객이 깊이 4 중첩 후 [!UICONTROL Related Product Rules]과(와) 위젯에 범주를 추가할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-62689 패치를 적용하십시오.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
source-git-commit: 7aefd4f20580529a9da14776368bf2c3bbb3ff3c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: *[!UICONTROL Related Product Rules]*&#x200B;의 범주 및 깊이 4 이후의 위젯을 추가할 수 없습니다.

>[!NOTE]
>
>이 패치는 [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md)(으)로 대체되었습니다.

ACSD-62689 패치는 고객이 깊이 4 중첩 후에 *[!UICONTROL Related Product Rules]*&#x200B;과(와) 위젯에 범주를 추가할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62689입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객은 깊이 4 중첩 후에는 *[!UICONTROL Related Product Rules]*&#x200B;에 범주와 위젯을 추가할 수 없습니다.

<u>재현 단계</u>:

1. 기본 루트 범주 아래에 *[!UICONTROL Anchor]* 및 *[!UICONTROL Non-Anchor]*(이)라는 두 개의 범주를 만듭니다.
   * *[!UICONTROL Non-Anchor]* 범주에 대해 *[!UICONTROL Is Anchor]* 플래그가 비활성화되어 있는지 확인하십시오.
1. **[!UICONTROL Content]** > **[!UICONTROL Widgets]**(으)로 이동하여 위젯을 만듭니다.
1. *[!UICONTROL Layout Updates]*&#x200B;에서 *[!UICONTROL Display on]* 필드의 **[!UICONTROL Non-Anchor Categories]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Specific Categories]**&#x200B;을(를) 클릭합니다.
1. 카테고리 선택 아이콘을 클릭합니다.
1. 루트 범주를 확장합니다.
1. 범주를 확인합니다. 둘 다 비활성화되고 선택할 수 없습니다.
1. *[!UICONTROL Layout Updates]*&#x200B;에서 *[!UICONTROL Display on]* 필드의 **[!UICONTROL Anchor Categories]**&#x200B;을(를) 선택합니다. 그런 다음 5단계와 6단계를 수행합니다.
1. 범주를 확인합니다. 둘 다 활성화되고 선택할 수 있어야 합니다.

<u>예상 결과</u>:

7단계에서는 *[!UICONTROL Non-Anchor]* 범주만 선택할 수 있습니다. 9단계에서는 *[!UICONTROL Anchor]* 범주를 선택해야 합니다.

<u>실제 결과</u>:

단계 7에서, 두 범주는 선택가능하지 않다. 단계 9에서는 두 범주가 모두 선택 가능합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).

