---
title: 'ACSD-66139: 비활성 장바구니에 대해 정의되지 않은 오류로 인해 GraphQL 주문이 실패합니다'
description: ACSD-66139 패치를 적용하여 존재하지 않거나 비활성 장바구니에 대한 주문을 할 때 GraphQL이 오류 메시지가 번역될 때 특정 오류 코드 대신 정의되지 않은 오류 코드를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139: 비활성 장바구니에 대해 &#39;정의되지 않음&#39; 오류로 GraphQL 주문 실패

ACSD-66139 패치는 존재하지 않거나 비활성 장바구니를 주문할 때 GraphQL이 오류 메시지가 번역될 때 특정 오류 코드 대신 *정의되지 않음* 오류 코드를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66139입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL은 존재하지 않거나 비활성 장바구니를 주문할 때 오류 메시지가 번역되면 특정 오류 코드 대신 *정의되지 않음* 오류 코드를 반환합니다.

<u>재현 단계</u>:

1. `app/i18n/Magento/de_DE/de_DE.csv`을(를) 추가하고 다음 오류 문자열 번역을 포함하십시오.

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. 관리 패널에서 스토어 보기를 만듭니다. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**(으)로 이동합니다. **[!UICONTROL Create Store View]**&#x200B;을(를) 클릭하고 **[!UICONTROL Code]**&#x200B;에 대해 코드 `test`을(를) 입력하십시오.
1. `german` 언어를 새로 만든 스토어 보기에 할당하십시오.
1. `setup:upgrade` 및 `setup:static-content:deploy -f` 실행
1. 헤더 &#39;Store:test&#39;을(를) 사용하여 다음 GraphQL 쿼리를 실행합니다.

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>예상 결과</u>:

올바른 오류 응답:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>실제 결과</u>:

반환된 `error_code`은(는) *정의되지 않음*&#x200B;입니다.

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
