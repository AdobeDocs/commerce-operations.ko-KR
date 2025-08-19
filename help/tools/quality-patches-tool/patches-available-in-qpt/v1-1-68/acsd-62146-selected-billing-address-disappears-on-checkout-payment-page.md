---
title: 'ACSD-62146: 선택한 청구 주소가 결제 체크아웃 페이지에서 사라짐'
description: 주소 검색이 활성화되고 고객 주소 수 제한이 1로 설정된 경우 ACSD-62146 패치를 적용하여 선택한 청구 주소가 체크아웃 결제 페이지에서 사라지는 Adobe Commerce 문제를 해결하십시오.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146: 선택한 청구 주소가 결제 체크아웃 페이지에서 사라짐

ACSD-62146 패치는 주소 검색을 사용하도록 설정하고 [!UICONTROL Number of Customer Addresses Limit]을(를) 1로 설정하면 선택한 청구 주소가 체크아웃 결제 페이지에서 사라지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62146입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주소 검색을 사용하도록 설정하고 **[!UICONTROL Number of Customer Addresses Limit]**&#x200B;을(를) 1로 설정하면 선택한 청구 주소가 결제 페이지에서 사라집니다.

<u>재현 단계</u>:

1. 주소 검색을 사용하려면 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**(으)로 이동합니다.
1. **[!UICONTROL Number of Customer Addresses Limit]**&#x200B;을(를) 1로 설정합니다.
1. 고객을 만들고 두 개의 다른 주소를 추가합니다.
1. 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
1. **[!UICONTROL Change Address]**&#x200B;을(를) 클릭하고 팝업을 사용하여 주소를 변경합니다.
1. 배송 주소로 주소 2를 선택합니다.
1. 결제 단계로 진행하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭하십시오.
1. 청구 주소와 배송 주소가 동일한지 확인합니다.
1. 지불하지 않고 페이지를 새로 고칩니다.

<u>예상 결과</u>:

청구와 배송 주소가 동일한 경우 배송 주소가 표시됩니다.

<u>실제 결과</u>:

기본 청구 주소와 선택한 배송 주소가 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
