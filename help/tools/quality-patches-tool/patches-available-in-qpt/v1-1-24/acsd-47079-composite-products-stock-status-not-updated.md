---
title: 'ACSD-47079: 하위 제품 재고 상태가 변경될 때 복합 제품의 재고 상태가 업데이트되지 않음'
description: ACSD-47079 패치를 적용하여 REST API POST /rest/V1/inventory/source-items를 통해 하위 제품 재고 상태가 변경될 때 합성 제품(번들, 그룹화 및 구성 가능) 재고 상태가 업데이트되지 않는 Adobe Commerce 문제를 수정합니다.
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%
---
# ACSD-47079: 하위 제품 재고 상태가 변경될 때 복합 제품의 재고 상태가 업데이트되지 않음

ACSD-47079 패치는 하위 제품 재고 상태가 REST API POST `/rest/V1/inventory/source-items`을(를) 통해 변경되면 복합 제품(번들, 그룹화 및 구성 가능)의 재고 상태가 업데이트되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47079입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 제품 재고 상태가 REST API POST `/rest/V1/inventory/source-items`을(를) 통해 변경되면 복합 제품(번들, 그룹화 및 구성 가능)의 재고 상태가 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 각 구성 가능하고 번들로 묶인 그룹화된 제품을 간단한 하위 제품 하나로 만듭니다.
1. `source-items` API 호출을 사용하여 각 단순 하위 제품 상태를 **[!UICONTROL Out of Stock]**(으)로 설정합니다.
1. 이제 상위 제품의 재고 상태를 확인합니다.

<u>예상 결과</u>:

상위 제품의 상태는 [!UICONTROL Out of Stock]입니다.

<u>실제 결과</u>:

상위 제품의 상태는 [!UICONTROL In Stock]입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]&#x200B;[&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
