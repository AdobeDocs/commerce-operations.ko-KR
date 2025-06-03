---
title: 'ACSD-65223: B2B 구매 발주에 대해 수동으로 선택한 약관 및 계약으로 인해 오류가 발생합니다'
description: ACSD-65223 패치를 적용하여 결제 시 약관이 필요할 때 [!UICONTROL Purchase Orders]을(를) 사용하여 만든 주문을 신용 카드와 같은 온라인 결제 방법으로 완료할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 57c0cb63f1e2c7b12d11b759eddf0d21b5db78b2
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ACSD-65223: B2B 구매 발주에 대해 수동으로 선택한 약관 및 계약으로 인해 오류가 발생합니다

ACSD-65223 패치를 사용하면 결제 시 약관이 필요할 때 **[!UICONTROL Purchase Orders]**&#x200B;을(를) 사용하여 만든 주문을 신용 카드와 같은 온라인 결제 방법으로 완료할 수 없는 문제를 해결할 수 있습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65223입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) B2B 1.5.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) B2B 1.5.1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문하기 위해 약관이 필요한 경우 [!UICONTROL Purchase Orders]을(를) 사용하여 만든 주문을 완료하려고 하면 신용 카드와 같은 온라인 결제 방법을 사용하여 주문할 수 없습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**(으)로 이동한 다음 **[!UICONTROL B2B Features]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Enable Company]** 및 **[!UICONTROL Enable Purchase Orders]**&#x200B;을(를) *예*(으)로 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]**(으)로 이동하여 새 조건을 만듭니다. **[!UICONTROL Applied]**&#x200B;을(를) *[!UICONTROL Manually]*(으)로 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]**(으)로 이동한 다음 **[!UICONTROL Enable Terms and Conditions]**&#x200B;을(를) *예*(으)로 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]**(으)로 이동하여 [!DNL Braintree]을(를) 구성합니다.
1. 상점 첫 화면에서 회사를 만듭니다.
1. 관리자의 **[!UICONTROL Customers]** > **[!UICONTROL Companies]**(으)로 이동합니다.
1. 회사를 승인하고 **[!UICONTROL Purchase Orders]**&#x200B;을(를) 허용합니다.
1. 프론트엔드에서 계정에 로그인합니다.
1. 장바구니에 항목을 추가합니다.
1. **[!UICONTROL Purchase Order]**&#x200B;을(를) 사용하여 주문합니다.
1. 고객 대시보드에서 **[!UICONTROL Purchase Orders]** 탭을 클릭합니다.
1. 새 구매 발주에서 주문을 생성합니다. 그런 다음 결제 방법으로 신용 카드를 선택합니다.
1. 약관에 동의합니다.
1. 주문하십시오.

<u>예상 결과</u>:

체크아웃을 위해 약관이 필요한 경우 승인된 구매 발주에 대해 온라인 결제 방법을 사용하여 주문할 수 있습니다.

<u>실제 결과</u>:

체크아웃을 위해 약관이 필요한 경우 승인된 구매 발주에 온라인 결제 방법을 사용하여 주문할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
