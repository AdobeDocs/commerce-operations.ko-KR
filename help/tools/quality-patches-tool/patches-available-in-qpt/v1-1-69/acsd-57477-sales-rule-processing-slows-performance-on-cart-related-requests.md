---
title: 'ACSD-57477: 판매 규칙 처리를 통해 장바구니 관련 요청의 성능이 저하됩니다.'
description: 'ACSD-57477 패치를 적용하여 사용 가능한 제품 특성이 많은 프로젝트에서(예: 1000 특성) AddProductsToCart Adobe Commerce 작업이 변수로 실행될 때 Commerce에서 이러한 모든 제품 특성을 로드하려고 시도하여 AddProductsToCart GraphQL 작업에서 성능 문제가 느려지는 GraphQL 문제를 해결합니다.'
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: 판매 규칙 처리를 통해 장바구니 관련 요청의 성능이 저하됩니다.

ACSD-57477 패치는 판매 규칙 처리가 장바구니 관련 요청에서 성능 저하를 초래하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57477입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

매개 변수를 GraphQL 변수로 보낼 경우 판매 규칙을 처리하면 장바구니 관련 요청에 대한 성능이 느려집니다.

<u>재현 단계</u>:

1. 1000개의 제품 속성을 추가합니다.
1. GraphQL 쿼리 아래에서 장바구니를 만듭니다.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. GraphQL 쿼리 아래에서 장바구니에 제품을 추가합니다.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. 이러한 변수를 설정합니다.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. 이 문제는 매개 변수를 GraphQL 변수로 보낼 때만 발생합니다. GraphQL 쿼리 자체에 매개 변수를 포함하면 이 문제는 발생하지 않습니다.
1. GraphQL 쿼리 자체에 매개 변수를 추가한 후 동일한 **장바구니에 추가** 요청을 보냅니다.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>예상 결과</u>:

`AddProductsToCart` GraphQL 작업 성능을 저하해서는 안 됩니다.

<u>실제 결과</u>:

`AddProductsToCart` GraphQL 작업 성능이 저하됩니다. 매개 변수를 변수로 보낼 때 모든 제품 특성이 로드되기 때문입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
