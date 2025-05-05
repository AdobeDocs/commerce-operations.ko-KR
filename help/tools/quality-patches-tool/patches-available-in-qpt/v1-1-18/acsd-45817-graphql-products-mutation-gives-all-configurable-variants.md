---
title: 'ACSD-45817: GraphQL 제품 돌연변이는 구성 가능한 모든 변형을 제공합니다.'
description: ACSD-45817 패치는 특정 스토어에 대한 GraphQL 'products' 돌연변이가 요청된 스토어에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45817입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817: GraphQL 제품 돌연변이는 구성 가능한 모든 변형을 제공합니다.

ACSD-45817 패치는 특정 저장소에 대한 GraphQL `products` 돌연변이가 요청된 저장소에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45817입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 저장소에 대한 GraphQL `products` 돌연변이는 요청된 저장소에 할당되지 않은 변형을 포함하여 구성 가능한 모든 변형을 반환합니다.

<u>필수 구성 요소</u>:

두 번째 웹 사이트, 두 번째 스토어 및 두 번째 스토어 보기를 만듭니다.

<u>재현 단계</u>:

1. 두 개의 하위 제품인 &quot;configurable-a&quot; 및 &quot;configurable-b&quot;로 구성 가능한 제품을 만듭니다.
1. 구성 가능한 제품을 두 웹 사이트에 할당합니다.
1. 두 번째 웹 사이트에 &quot;configurable-a&quot; 변형을 하나만 할당합니다.
1. **Storefront**(으)로 이동하여 두 번째 웹 사이트로 전환하고 구성 가능한 제품을 엽니다.
1. 하나의 하위 옵션인 &quot;configurable-a&quot;만 표시되는지 확인합니다.
1. `POST: /graphql` 끝점 및 `Headers: "store" = "new"`을(를) 사용하여 GraphQL 쿼리 실행

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>예상 결과</u>:

&quot;configurable-b&quot; 변형은 두 번째 웹 사이트에 할당되지 않았으며 응답에 표시되어서는 안 됩니다.

<u>실제 결과</u>:

&quot;configurable-b&quot; 변형이 응답에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
