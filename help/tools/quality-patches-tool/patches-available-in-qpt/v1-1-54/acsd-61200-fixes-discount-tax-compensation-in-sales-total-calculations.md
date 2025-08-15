---
title: 'ACSD-61200: 판매 합계 계산에서 할인 세금 보상을 수정합니다.'
description: ACSD-61200 패치를 적용하여 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]*이(가) 판매 총계 계산에서 누락되어 판매 주문 데이터와 쿠폰 보고서 데이터가 일치하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: 판매 합계 계산에서 할인 세금 보상을 수정합니다.

ACSD-61200 패치는 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]* 계산에서 *[!UICONTROL Total Amount]* 및 *[!UICONTROL Total Amount Actual]*&#x200B;이(가) 누락되어 판매 주문 데이터와 쿠폰 보고서 데이터가 일치하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61200입니다. 이 문제는 Adobe Commerce 버전 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

- Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

- Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

판매 총계 계산에서 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;이(가) 누락되어 판매 주문 및 쿠폰 보고서 데이터가 정확하지 않습니다.

<u>재현 단계</u>:

1. [!UICONTROL Tax Zone] 및 [!UICONTROL Tax Rule]을(를) 만듭니다.
1. 다음 세금 구성을 설정합니다.
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. 주문, 송장 및 대변 메모에 대해 다음 표시 설정을 갱신합니다.
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. 10% 할인에 대한 쿠폰이 포함된 [!UICONTROL Cart Price Rule]을(를) 만듭니다.
1. 쿠폰을 사용하여 주문을 완료하고 송장 및 선적을 생성합니다.
1. **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]**(으)로 이동하여 보고서를 생성합니다.
1. 주문 요약의 데이터를 보고서의 데이터와 비교합니다.

<u>예상 결과</u>:

*[!UICONTROL Total Amount]* 및 *[!UICONTROL Total Amount Actual]* 계산에는 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;이(가) 모두 포함되어 있으며, 주문 요약을 보고서 데이터와 일치시킵니다.

<u>실제 결과</u>:

계산에서 *[!UICONTROL Discount Tax Compensation Amount]* 및 *[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;이(가) 누락되었기 때문에 판매 주문 데이터와 쿠폰 보고서 데이터가 일치하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

- Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
- 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool] 릴리스됨: 도구 가이드의 품질 패치를 자체 제공하는 새 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
