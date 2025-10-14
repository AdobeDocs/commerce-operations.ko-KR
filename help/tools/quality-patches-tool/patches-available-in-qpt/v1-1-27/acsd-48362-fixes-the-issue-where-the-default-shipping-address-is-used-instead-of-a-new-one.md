---
title: 'ACSD-48362: 새 주소 대신 기본 배송 주소가 사용됩니다.'
description: ACSD-48362 패치를 적용하여 협상 가능 견적을 사용하여 주문을 할 때 새 주소 대신 기본 배송 주소가 사용되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362: 새 주소 대신 기본 배송 주소가 사용됩니다

ACSD-48362 패치는 협상 가능 견적을 사용하여 주문을 할 때 새로 추가된 주소 대신 기본 배송 주소가 사용되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48362입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

협상 가능 견적을 사용하여 주문을 할 때 새로 추가된 배송 주소 대신 기본 배송 주소가 사용됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**(으)로 이동하여 B2B 견적을 사용하도록 설정합니다.
1. 회사 사용자로 로그인
1. 장바구니에 제품을 추가합니다.
1. 장바구니 페이지로 이동하여 견적을 요청합니다.
1. 고객의 **[!UICONTROL My Quotes]** 페이지로 이동하여 방금 만든 견적을 선택하십시오.
1. 고객 견적 페이지의 **[!UICONTROL Shipping Information]** 섹션으로 이동합니다.
   * **[!UICONTROL Add New Address]**&#x200B;을(를) 클릭하고 양식을 작성한 다음 주소를 저장합니다(**[!UICONTROL Use as my default billing address]** 또는 **[!UICONTROL Use as my default shipping address]**&#x200B;을(를) 선택하지 마십시오).
1. 고객의 견적 페이지에서 **[!UICONTROL Send for Review]**&#x200B;을(를) 클릭합니다.
1. Adobe Commerce 관리자로 이동하여 방금 만든 견적을 열고 **[!UICONTROL Send]**&#x200B;을(를) 클릭합니다.
1. 이제 고객의 견적 페이지로 이동하여 페이지를 새로 고치고 **[!UICONTROL Proceed to Checkout]**&#x200B;을(를) 클릭합니다.
1. 체크아웃 페이지에서 데이터는 새 배송 주소를 선택한 경우에도 기본 배송 주소를 표시합니다.
1. **[!UICONTROL Continue]**&#x200B;을(를) 클릭하고 주문합니다.

<u>예상 결과</u>:

주문은 체크아웃 페이지에서 기본 배송 주소를 다시 선택하지 않고 새 주소를 사용해야 합니다.

<u>실제 결과</u>:

기본 배송 주소로 주문이 처리됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko). 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
