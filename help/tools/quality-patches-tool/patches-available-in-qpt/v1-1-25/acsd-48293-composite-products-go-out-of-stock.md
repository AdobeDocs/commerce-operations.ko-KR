---
title: 'ACSD-48293: 재입고된 어린이 제품이 품절되었을 때 재고 부족 복합 제품'
description: ACSD-48293 패치를 적용하여 품절된 하위 제품이 재고로 반환될 때 합성 제품이 품절되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: 재입고된 어린이 제품이 품절되었을 때 재고 부족 복합 제품

ACSD-48293 패치는 품절된 하위 제품이 재고로 반환될 때 복합 제품이 품절되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-48293입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다 팔린 아동용품을 재고로 반품하면 복합제품은 품절됩니다.

<u>재현 단계</u>:

1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 두 개의 소스와 재고를 만들어 각 웹 사이트에 할당합니다.
1. **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*&#x200B;에서 품절 제품 표시 옵션을 활성화합니다.
1. 기본 웹 사이트의 재고 출처(수량 = 1 설정)를 사용하여 하나의 연관된 제품으로 구성 가능한 제품을 생성합니다.
1. 구성 가능한 제품을 주문합니다.
1. 크론을 작동시키세요
1. 상점에서 구성 가능한 제품을 열고 재고가 없는지 확인합니다.
1. [!UICONTROL Admin]에서 구성 가능한 제품을 열고 **[!UICONTROL Manage Stock Option]**&#x200B;을(를) *[!UICONTROL No]*(으)로 설정합니다.
1. 크론을 작동시키세요
1. 주문을 출하하고 수량을 간단한 제품에 추가하여 재고를 만듭니다.
1. 크론을 작동시키세요
1. 상점에서 제품 사용 가능 여부를 확인합니다.

<u>예상 결과</u>:

구성 가능한 제품이 재고에 있습니다.

<u>실제 결과</u>:

구성 가능한 제품의 재고가 부족합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
