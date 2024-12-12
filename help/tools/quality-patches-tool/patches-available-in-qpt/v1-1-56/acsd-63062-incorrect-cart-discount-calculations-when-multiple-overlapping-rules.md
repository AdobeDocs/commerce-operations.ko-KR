---
title: 'ACSD-63062: 겹치는 규칙이 여러 개 있는 잘못된 장바구니 할인 계산'
description: ACSD-63062 패치를 적용하여 여러 겹침 규칙이 적용될 때 잘못된 장바구니 할인 계산이 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: 겹치는 규칙이 여러 개 있는 잘못된 장바구니 할인 계산

ACSD-63062 패치는 여러 겹침 규칙이 적용될 때 잘못된 장바구니 할인 계산이 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63062입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 겹치는 규칙이 적용되면 잘못된 장바구니 할인 계산이 발생합니다.

<u>재현 단계</u>:

1. 샘플 데이터를 사용하여 새 인스턴스를 설치합니다.
1. 다음과 같은 세 가지 간단한 제품을 만듭니다.

   * simple1: $1080
   * simple2: $260
   * simple3: $280

1. 다음과 같이 4개의 *[!UICONTROL Cart Price Rules]*&#x200B;을(를) 만듭니다.

   * 규칙 1:

      * *[!UICONTROL Priority]*: 100
      * *[!UICONTROL Conditions]* 탭: 총 수량이 3보다 크거나 같은 경우 simple2($280) 제품을 사용합니다.
      * *[!UICONTROL Actions]* 탭: SKU는 단순2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * 규칙 2:

      * *[!UICONTROL Priority]*: 200
      * *[!UICONTROL Actions]* 탭: SKU는 단순2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * 규칙 3:

      * *[!UICONTROL Priority]*: 300
      * *[!UICONTROL Conditions]* 탭: 소계가 $1000보다 크거나 같음
      * 전체 장바구니에 대한 *[!UICONTROL Fixed Amount Discount]*: $100

   * 규칙 4:

      * *[!UICONTROL Priority]*: 400
      * *[!UICONTROL Conditions]* 탭: 총 수량이 2보다 크거나 같은 경우 simple1($1080) 제품을 사용합니다.
      * *[!UICONTROL Actions]* 탭: SKU는 simple1입니다.
      * 전체 장바구니에 대한 *[!UICONTROL Fixed Amount Discount]*: $960

1. 상점으로 이동하여 주어진 수량의 다음 제품을 장바구니에 추가합니다.

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. 장바구니를 확인하십시오.

<u>예상 결과</u>:

할인은 $1352입니다.

<u>실제 결과</u>:

적용되는 할인은 $1525.33입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
