---
title: 'ACSD-56158: 장바구니에 여러 세금 규칙이 적용될 때 GraphQL 응답에 잘못된 세금 값이 표시됨'
description: ACSD-56158 패치를 적용하여 여러 세금 규칙이 장바구니에 적용될 때 GraphQL 응답의 세금 값 렌더링이 잘못된 Adobe Commerce 문제를 수정합니다.
feature: GraphQL, Taxes
role: Admin, Developer
exl-id: dc22861c-cd41-402f-be37-d02c02b59433
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-56158: 장바구니에 여러 세금 규칙이 적용될 때 GraphQL 응답에 잘못된 세금 값이 표시됨

ACSD-56158 패치는 여러 세금 규칙이 장바구니에 적용될 때 GraphQL 응답의 세금 값 렌더링이 올바르지 않은 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56158입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 세금 규칙이 장바구니에 적용되면 GraphQL 응답의 세금 값 렌더링이 올바르지 않습니다.

<u>재현 단계</u>:

1. 미국 주소로 고객을 만듭니다.
1. 관리 패널로 이동합니다.
1. 가격이 $100인 제품을 만듭니다.
1. 미국 주소에 대해 두 개의 세율을 생성합니다. 하나는 10%에 대한 세율이고 다른 하나는 5%에 대한 세율입니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Rule]**&#x200B;에서 미국에 대한 두 개의 세금 규칙을 구성합니다.
1. 하나의 세율을 하나의 규칙에 지정합니다.
1. 프론트엔드에서 미국 주소로 고객으로 로그인하고 제품을 장바구니에 추가합니다.
1. GraphQL을 통해 고객 토큰을 생성합니다.
1. GraphQL을 통해 장바구니 ID를 생성합니다.
1. GraphQL을 통해 고객의 장바구니를 가져와 적용된 세금이 올바른지 확인하십시오.

   ```GraphQL
   {
       cart(cart_id: "o3Yqt6zkn8ncOzFxGnR1IWdT..") {
           id
           email
           billing_address {
               city
               country {
                   code
                   label
               }
               firstname
               lastname
               company
               postcode
               vat_id
               region {
                   code
                   label
               }
               street
               telephone
           }
           shipping_addresses {
               firstname
               lastname
               company
               street
               city
               postcode
               vat_id
               region {
                   code
                   label
               }
               country {
                   code
                   label
               }
               telephone
               available_shipping_methods {
                   amount {
                       currency
                       value
                   }
                   available
                   carrier_code
                   carrier_title
                   error_message
                   method_code
                   method_title
                   price_excl_tax {
                       value
                       currency
                   }
                   price_incl_tax {
                       value
                       currency
                   }
               }
               selected_shipping_method {
                   amount {
                       value
                       currency
                   }
                   carrier_code
                   carrier_title
                   method_code
                   method_title
               }
           }
           available_payment_methods {
               code
               title
           }
           selected_payment_method {
               code
               title
           }
           applied_coupons {
               code
           }
           prices {
               grand_total {
                   value
                   currency
               }
               subtotal_excluding_tax {
                   value
                   currency
               }
               subtotal_including_tax {
                   value
                   currency
               }
               applied_taxes {
                   label
                   amount {
                       currency
                       value
                   }
               }
           }
       }
   }    
   ```

<u>예상 결과</u>:

각 세율에는 자체 세액이 표시됩니다.

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 10
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 5
        }
    }
]
```

<u>실제 결과</u>:

각 규칙에 대해 반환된 총 세액:

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    }
]
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
