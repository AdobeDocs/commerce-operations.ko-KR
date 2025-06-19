---
title: 'ACP2E-3841: 하위 선택 조건이 사용되고 무료 배송이 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않습니다'
description: ACP2E-3841 패치를 적용하여 하위 선택 조건이 사용되고 무료 배송이 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않는 Adobe Commerce 문제를 수정합니다.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACP2E-3841: 하위 선택 조건이 사용되고 무료 배송이 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않습니다

ACP2E-3841 패치는 하위 선택 조건이 사용되고 무료 배송이 활성화될 때 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACP2E-3841입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p9

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 선택 조건이 사용되고 무료 배송이 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않습니다.

<u>필수 구성 요소</u>:

**설정:**
1. **[!UICONTROL Free Shipping]** = *활성화됨*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**필요한 범주:**
1. 범주 테스트 1
1. 범주 테스트 2

**필요한 제품:**
1. 제품 테스트 1:
   1. 카테고리: 카테고리 테스트 1
   1. 가격: $ 45
1. 제품 테스트 2:
   1. 카테고리: 카테고리 테스트 2
   1. 가격: $ 56.25 

      **(테스트가 올바르게 작동하려면 가격이 여기에 표시된 것과 같아야 합니다.)**

**장바구니 가격 규칙:**

관리자로 로그인하고 **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**(으)로 이동합니다. 다음 값을 사용합니다.

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: 무료 배송 테스트
1. **[!UICONTROL Active]**: *예*
1. **[!UICONTROL Websites]**: *기본 웹 사이트*
1. **[!UICONTROL Customer Groups]**: *로그인되지 않음, 일반, 도매, Retailer*
1. **[!UICONTROL Coupon]**: *쿠폰 없음*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

작업:

**[!UICONTROL Percent of product price discount]** = *10*

<u>재현 단계</u>:

1. 매장 앞에 로그인합니다.
2. 제품 테스트 1 추가.
3. Product Test 2를 두 개 추가합니다.
4. 장바구니를 방문합니다.
5. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

오류 없음.

<u>실제 결과</u>:

*500 오류*

*메시지: 사용되지 않는 기능: float 112.5에서 int로의 암시적 변환은 /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php의 214행에서 정밀도를 잃음*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
