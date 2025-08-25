---
title: 'ACSD-66963: ''estimateTotals'' 돌연변이가 가상 제품 할인에 대해 null을 반환합니다.'
description: ACSD-66963 패치를 적용하여 가상 제품만 있는 장바구니에 할인 코드가 적용되면 'estimateTotals'가 할인에 대해 *null*을 반환하는 Adobe Commerce 문제를 수정합니다.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963: `estimateTotals` 돌연변이가 가상 제품 할인에 대해 null을 반환합니다.

ACSD-66963 패치는 가상 제품만 있는 장바구니에 할인 코드가 적용될 때 `estimateTotals`이(가) 할인용으로 *null*&#x200B;을(를) 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66963입니다. 이 문제는 Adobe Commerce 2.4.8에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가상 제품만 포함된 장바구니에 할인 코드가 적용되면 `estimateTotals` 돌연변이는 할인에 대해 *null*&#x200B;을 반환합니다.

<u>재현 단계</u>:

1. 가상 제품만 포함하는 장바구니를 만듭니다.
1. 할인 코드 적용:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>예상 결과</u>:

가상 제품만 들어 있는 카트에 대한 할인 정보가 포함되어 있습니다.

    &quot;
    &lbrace;
    &quot;data&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;prices&quot;: &lbrace;
    &quot;discounts&quot;: &lbrack;
    &lbrace;
    &quot;amount&quot;: &lbrace;
    &quot;value&quot;: 100.5,
    &quot;currency&quot;: &quot;USD&quot;
    &rbrace;,
    &quot;label&quot;: &quot;테스트용 두 번째 할인 코드&quot;,
    &quot;coupon&quot;: &lbrace;
    &quot;code&quot;: &quot;z3r0c00l&quot;
    ,
    &quot;apply_to&quot;: &quot;ITEM&quot;,
    &quot;type&quot;: null
    
    &rbrack;
    &rbrace;
    &rbrace;
    &rbrace;
    ,
    &quot;확장&quot;: {}
    &rbrace;
    &quot;

<u>실제 결과</u>:

가상 제품만 있는 장바구니의 경우 할인 정보가 *null*(으)로 반환됩니다.

    &quot;
    &lbrace;
    &quot;data&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;prices&quot;: &lbrace;
    &quot;discounts&quot;: null
    &rbrace;
    &rbrace;
    
    ,
    &quot;extensions&quot;: {}
    &rbrace;
    &quot;

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
