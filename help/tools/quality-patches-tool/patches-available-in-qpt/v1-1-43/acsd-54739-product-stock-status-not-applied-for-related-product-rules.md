---
title: 'ACSD-54739: *[!UICONTROL Related Product Rules]*에 대해 *[!UICONTROL Product Stock]* 상태가 적용되지 않음'
description: ACSD-54739 패치를 적용하여 *[!UICONTROL Related Product Rules]*에 대해 *[!UICONTROL Product Stock]* 상태가 적용되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '355'
ht-degree: 0%
---
# ACSD-54739: *[!UICONTROL Related Product Rules]*&#x200B;에 대해 *[!UICONTROL Product stock]* 상태가 적용되지 않음

ACSD-54739 패치는 *[!UICONTROL Related Product Rules]*&#x200B;에 대해 *[!UICONTROL Product stock]* 상태가 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54739입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Related Product Rules]*&#x200B;에 대해 *[!UICONTROL Product stock]* 상태가 적용되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Display Out of Stock Products]** 구성을 *예*(으)로 설정합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]**(으)로 이동하여 프로모션 규칙 조건으로 *예*&#x200B;를 설정합니다.
1. 관련 제품 규칙을 만듭니다. **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > 특성 수량이 있는 조건 추가(재고/재고 부족 선택)로 이동합니다.
1. 프론트엔드에 있는 제품들을 확인하세요

<u>예상 결과</u>:

재고/재고 부족 제품이 *[!UICONTROL Related Product Rules]*&#x200B;까지 일치합니다.

<u>실제 결과</u>:

재고/재고 부족 제품이 *[!UICONTROL Related Product Rules]*&#x200B;에서 일치하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]&#x200B;[&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
