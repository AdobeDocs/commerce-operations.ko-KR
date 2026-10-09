---
title: 'ACSD-66084: ''row_total_incl_tax''는 주문 API에서 완전히 할인된 항목에 대해 0.00이 아닌 거의 0을 반환합니다.'
description: ACSD-66084 패치를 적용하여 주문 API 응답에서 완전히 할인된 항목에 대해 'row_total_incl_tax'가 0.00 대신 거의 0에 가까운 잔차 값으로 반환되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '473'
ht-degree: 0%
---
# ACSD-66084: 주문 API에서 완전히 할인된 항목에 대해 `row_total_incl_tax`이(가) 0.00 대신 0에 가까운 값을 반환합니다.

ACSD-66084 패치는 완전 할인 항목에 대해 0.00 대신 주문 API 응답에서 `row_total_incl_tax`이(가) 0에 가까운 잔차 값으로 반환되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66084입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`row_total_incl_tax`은(는) 완전 할인된 항목의 경우 0.00 대신 주문 API 응답에서 거의 0에 가까운 나머지 값으로 반환됩니다.

<u>재현 단계</u>:

1. 가격과 특별 가격으로 제품을 만듭니다. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** 클릭 > **[!UICONTROL Price]**&#x200B;을(를) $25로 설정하고 **[!UICONTROL Special Price]**&#x200B;을(를) **[!UICONTROL Advanced Pricing]**&#x200B;에서 $16.99로 설정합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]**(으)로 이동하여 20%의 비율을 추가합니다. 그런 다음 **[!UICONTROL Tax Rules]**(으)로 이동하여 규칙을 만들고 할당합니다.
   **[!UICONTROL Taxable Goods]**&#x200B;을(를) 제품 세금 등급으로 지정합니다.
1. 100% 할인과 쿠폰이 포함된 판매 규칙을 만듭니다. **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**(으)로 이동하여 100% 할인이 적용되는 규칙을 추가한 다음 **[!UICONTROL Specific Coupon]**&#x200B;을(를) 사용하고 코드를 입력하세요.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** >(으)로 이동하여 세금 설정을 구성합니다.
1. 무료 배송을 활성화하십시오. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**(으)로 이동합니다. **[!UICONTROL Enabled]**&#x200B;을(를) **[!UICONTROL Yes]**(으)로 설정하고 설정을 조정합니다.
1. 제품 페이지로 이동하여 **[!UICONTROL Add to Cart]**&#x200B;을(를) 선택합니다. 장바구니에 가서 쿠폰 코드를 적용하세요.
1. 해당 세금 구역에 주문을 합니다.
1. REST API를 통해 관리 토큰(API)을 생성합니다.
1. REST API를 통해 주문 세부 사항을 검색합니다.
1. 응답에서 `row_total_incl_tax`을(를) 확인합니다.

<u>예상 결과</u>:

`row_total_incl_tax`은(는) 항목이 완전히 할인된 경우 `0.00`과(와) 같이 통화에 적합한 값을 반환해야 합니다.

<u>실제 결과</u>:

`row_total_incl_tax`은(는) `3.5527136788005e-15`과(와) 같이 0에 가까운 부동 소수점 값을 반환하며, 이는 통화 표시에 적합하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
