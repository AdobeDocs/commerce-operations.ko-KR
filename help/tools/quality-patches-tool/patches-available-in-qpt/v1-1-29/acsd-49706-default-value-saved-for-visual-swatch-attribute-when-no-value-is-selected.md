---
title: 'ACSD-49706: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 저장된 기본값'
description: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 기본값이 저장되는 Adobe Commerce 문제를 해결하려면 ACSD-49706 패치를 적용합니다.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: 값을 선택하지 않은 경우 시각적 견본 속성에 대해 저장된 기본값

ACSD-49706 패치는 값을 선택하지 않은 경우 시각적 견본 속성에 대해 기본값이 저장되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49706입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

값을 선택하지 않으면 시각적 견본 속성에 대해 기본값이 저장됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동합니다.
1. **[!UICONTROL Add New Attribute]**&#x200B;을(를) 클릭합니다.
1. 필드를 채웁니다.

   * 예를 들어 입력 형식 *[!UICONTROL Visual Swatch]*&#x200B;을(를) 선택하고 여러 옵션(예: *빨강*, *녹색*)을 추가하십시오. 이러한 옵션 중 하나를 기본값으로 선택해야 합니다.
   * **[!UICONTROL Save Attribute]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**(으)로 이동합니다.
1. *[!UICONTROL Default]* 특성 집합을 편집합니다.
1. *[!UICONTROL New Attribute]*&#x200B;을(를) *[!UICONTROL Unassigned Attributes]* 열에서 중간 열의 *[!UICONTROL Product Details]* 폴더로 이동합니다.

   * **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

1. *[!UICONTROL Default]* 특성 집합을 사용하여 새 제품을 만듭니다.

   * *[!UICONTROL New Attribute]*&#x200B;을(를) 비워 두고 저장합니다.

1. 저장되면 값이 *[!UICONTROL New Attribute]*&#x200B;에 나타납니다.

<u>예상 결과</u>:

기본적으로 *[!UICONTROL New Attribute]*&#x200B;에 값이 할당되지 않습니다.

<u>실제 결과</u>:

제품 저장 시 속성에 기본값이 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
