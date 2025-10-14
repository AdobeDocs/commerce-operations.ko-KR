---
title: 'ACSD-58566: 구매 주문 설명에 대한 GraphQL 내부 서버 오류'
description: ACSD-58566 패치를 적용하여 GraphQL이 'addPurchaseOrderComment' 돌연변이의 'created_at' 필드를 쿼리할 때 내부 서버 오류를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: 구매 주문 설명에 대한 GraphQL 내부 서버 오류

ACSD-58566 패치는 `created_at` 돌연변이의 `addPurchaseOrderComment` 필드 쿼리가 예상 날짜/시간 대신 null 값을 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58566입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL이 `created_at` 돌연변이의 `addPurchaseOrderComment` 필드를 쿼리할 때 내부 서버 오류를 반환합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되고 회사 및 구매 발주가 활성화됩니다.

<u>재현 단계</u>:

1. 회사 사용자에 대한 고객 토큰을 생성합니다.
1. 다음 GraphQL 요청 시퀀스를 수행합니다.
   1. *을(를) 사용하여*&#x200B;장바구니`customerCart`을(를) 만듭니다.
   1. *을(를) 사용하여*&#x200B;장바구니`addProductsToCart`에 제품을 추가합니다.
   1. `placePurchaseOrder`을(를) 사용하여 주문합니다.
   1. `addPurchaseOrderComment`을(를) 사용하여 구매 주문에 댓글을 추가합니다.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>예상 결과</u>:

`created_at` 필드는 구매 주문 설명의 날짜/시간을 반환합니다.

<u>실제 결과</u>:

`created_at` 날짜 대신 null을 표시합니다.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
