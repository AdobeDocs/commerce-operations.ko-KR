---
title: 'ACSD-54319: *[!UICONTROL Products in Carts]* 보고서에서 제품 가격이 0으로 표시됨'
description: '*[!UICONTROL Products in Carts]* 보고서에서 제품 가격이 0으로 표시되는 Adobe Commerce 문제를 해결하려면 ACSD-54319 패치를 적용합니다'
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319: *[!UICONTROL Products in Carts]* 보고서에서 제품 가격이 0으로 표시됨

ACSD-54319 패치를 사용하면 *[!UICONTROL Products in Carts]* 보고서에서 제품 가격이 0으로 표시되는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54319입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Products in Carts]* 보고서에 제품 가격이 0으로 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Catalog Price Scope]** > **[!UICONTROL Website]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]**&#x200B;에서 **[!UICONTROL Price]**&#x200B;을(를) **[!UICONTROL Catalog Price Scope]**(으)로 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;에서 두 번째 웹 사이트를 만듭니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;에서 제품을 만듭니다.
1. 이 제품을 두 번째 웹 사이트에만 할당합니다.
1. 두 번째 웹 사이트에서 제품을 장바구니에 추가합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** 그리드로 이동합니다.
1. *[!UICONTROL Price]* 눈금의 *[!UICONTROL Products In Carts]* 열을 확인합니다.

<u>예상 결과</u>:

*[!UICONTROL Products in Carts]* 보고서 격자에서 제품 가격이 0이 아닙니다.

<u>실제 결과</u>:

*[!UICONTROL Products in Carts]* 보고서 격자에서 제품 가격이 0입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
