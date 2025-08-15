---
title: 'ACSD-55610: 부분적으로 취소된 주문의 할인 금액이 잘못됨'
description: ACSD-55610 패치를 적용하여 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 Adobe Commerce 문제를 해결합니다.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55610: 부분적으로 취소된 주문의 할인 금액이 잘못됨

ACSD-55610 패치는 부분적으로 취소된 주문에 잘못된 할인 금액이 있는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55610입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

일부 취소된 주문의 할인 금액이 잘못되었습니다.

<u>재현 단계</u>:

1. 장바구니 가격 규칙을 만듭니다.

   * *[!UICONTROL Rule Name]*: *겨울 판매*
   * *[!UICONTROL Active]* = *예*
   * *[!UICONTROL Websites]* = *기본 웹 사이트*
   * 모든 고객 그룹을 선택합니다.
   * 특정 쿠폰을 선택합니다.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *소계(제외) 세금)이 75*&#x200B;보다 크거나 같음
   * *[!UICONTROL Percent of product price discount]*&#x200B;을(를) 적용합니다.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *예*

1. 가격이 100으로 설정된 제품 3개를 만듭니다.
1. 세 제품을 장바구니에 추가합니다.
1. 쿠폰을 적용하세요.
1. 주문하십시오.
1. 주문의 한 품목에 대한 송장을 발행하여 발송합니다.
1. 나머지 두 항목은 취소해 주십시오.
1. `base_discount_canceled` 열을 확인합니다.

<u>예상 결과</u>:

`base_discount_cancelled`의 할인 금액이 올바르게 반영되었습니다.

<u>실제 결과</u>:

`base_discount_cancelled`이(가) 올바르지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
