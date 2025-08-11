---
title: 'ACSD-66072: GraphQL이 제품 세부 사항 페이지에 관련 제품을 반환하지 않음'
description: ACSD-66072 패치를 적용하여 관련 제품 규칙이 구성될 때 내부 서버 오류로 인해 제품 세부 사항 페이지에서 GraphQL을 통해 관련 제품이 반환되지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1cd5383d774ab0ed97b80a4abf7df5706706ea5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66072: GraphQL이 제품 세부 사항 페이지에 관련 제품을 반환하지 않음

ACSD-66072 패치는 **[!UICONTROL Related Products Rule]**&#x200B;을(를) 구성할 때 내부 서버 오류로 인해 제품 세부 사항 페이지에서 GraphQL을 통해 관련 제품이 반환되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66072입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Related Products Rule]**&#x200B;을(를) 구성할 때 내부 서버 오류로 인해 제품 세부 사항 페이지에서 GraphQL을 통해 관련 제품이 반환되지 않습니다.

<u>재현 단계</u>:

1. 구성 가능한 제품 만들기:
   * **제품 1**: `config1`(`option1` 포함)
   * **제품 2**: `config2`(`option2` 포함)

1. 제품을 만들고 범주에 할당
   * **새 범주**&#x200B;을 만듭니다.
   * 이 범주에 제품(`config1` 및 `config2`)을 모두 할당하십시오.

1. **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]**(으)로 이동한 후 다음 설정으로 새 규칙을 만듭니다.

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. 다음 Magento CLI 명령을 실행합니다.

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. 다음 페이로드를 사용하여 `../graphql`에게 POST 요청을 보냅니다.

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>예상 결과</u>:

쿼리가 관련 제품(`config1`)을 반환합니다.

<u>실제 결과</u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

`var/log/exception.log` 파일에는 다음이 포함되어 있습니다.

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
