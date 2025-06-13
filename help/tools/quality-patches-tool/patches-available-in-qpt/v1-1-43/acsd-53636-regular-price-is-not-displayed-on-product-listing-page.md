---
title: 'ACSD-53636: [!UICONTROL Product Listing] 페이지에 일반 가격이 표시되지 않습니다.'
description: ACSD-53636 패치를 적용하여 특별 가격이 적용된 하위 제품이 있는 구성 가능한 제품의 경우 *[!UICONTROL Product Listing]* 페이지에 일반 가격이 표시되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636: *[!UICONTROL Product Listing]* 페이지에 일반 가격이 표시되지 않습니다.

ACSD-53636 패치는 특별 가격이 있는 하위 제품이 구성 가능한 제품에 대해 *[!UICONTROL Product Listing]* 페이지에 일반 가격이 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53636입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특별 가격이 적용된 하위 제품이 있는 구성 가능한 제품의 경우 *[!UICONTROL Product Listing]* 페이지에 일반 가격이 표시되지 않습니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**(으)로 이동하여 구성 가능한 제품을 만들거나 엽니다.
2. 하위 제품을 열고 하위 제품 전체 또는 중 하나에 특별 가격을 추가하고 제품을 저장합니다.
3. 프론트엔드로 이동하여 구성 가능한 제품의 **[!UICONTROL Product Detail]** 페이지를 여십시오. 특별 가격이 적용된 하위 제품 견본에는 *[!UICONTROL Regular price]*&#x200B;이(가) 취소되어 표시됩니다(예상됨).
4. 프론트엔드로 이동하여 특별 가격으로 구성 가능한 제품에 대한 **[!UICONTROL Product Listing]** 페이지를 엽니다. 구성 가능한 제품 견본 변경 사항은 *[!UICONTROL Product Detail Page]* 및 기타 간단한 제품과 달리 일반 가격을 표시하지 않습니다.

<u>예상 결과</u>:

*[!UICONTROL Product Listing]* 페이지에서 구성 가능한 제품은 하위 제품에 대한 일반 가격을 표시합니다.

<u>실제 결과</u>:

*[!UICONTROL Product Listing]* 페이지에서 구성 가능한 제품에 하위 제품에 대한 일반 가격이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
