---
title: 'MDVA-41305: 구성 가능한 제품에 대한 GraphQL 쿼리 addProductsToWishlist 오류'
description: MDVA-41305 패치는 구성 가능한 제품에 대한 GraphQL 쿼리 'addProductsToWishlist'에서 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41305입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: 985c3c46-d2c8-4479-b9e4-e5f9504ab03b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305: 구성 가능한 제품에 대한 GraphQL 쿼리 addProductsToWishlist 오류

MDVA-41305 패치를 사용하면 구성 가능한 제품에 대한 GraphQL 쿼리 `addProductsToWishlist`에서 오류가 발생하는 문제를 해결할 수 있습니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41305입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL에서 구성 가능한 제품(구성 포함/제외)을 위시리스트에 추가하면 구성 가능한 SKU 및 응답으로 구성 가능한 옵션을 가져올 수 없습니다.

<u>재현 단계</u>:

1. 구성 가능한 제품을 만듭니다(파란색, 회색 및 하나의 사용자 지정 옵션 사용).
1. 프론트엔드를 엽니다. 고객으로 로그인하고 위시리스트를 만듭니다(wishlist_id 확인).
1. Postman을 열고 고객 토큰을 만듭니다.

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(email: "", password: "") {
        token
      }
     }
     </code>
     </pre>

1. 전달자 인증을 위해 이 토큰을 설정합니다.
1. 다음 지침을 사용하여 구성 가능한 제품 *파란색*&#x200B;을(를) 위시리스트에 추가해 보십시오.

<pre>
<code class="language-graphql">
mutation {
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: [
     {
       sku: "conf2"
       selected_options: [
            "Y29uZmlndXJhYmxlLzkzLzUw"
       ]
       quantity: 1
       entered_options: [
         {
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         }
       ]
     }
    ]
  ) {
    wishlist {
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) {
        items {
         id
         quantity
         ... on ConfigurableWishlistItem  {
           child_sku
           customizable_options {
             customizable_option_uid
           }
         }
         product {
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface {
             options {
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption {
                value {
                  uid
                  sku
                  price
                  price_type
                  max_characters
                }
              }
            }
          }
          price_range {
            minimum_price {
              regular_price {
                currency
                value
              }
            }
            maximum_price {
               regular_price {
                 currency
                 value
               }
             }
           }
         }
       }
     }
   }
  user_errors {
    code
    message
   }
 }
}
</code>
</pre>

<u>예상 결과</u>:

사용자는 페이로드에 지정되고 위시리스트에 추가된 응답에서 구성된 제품 옵션 세트를 볼 수 있습니다.

<u>실제 결과</u>:

응답에서 *내부 서버 오류*&#x200B;이(가) 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
