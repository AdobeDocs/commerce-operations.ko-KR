---
title: 'ACSD-58566: 구매 주문 설명에 대한 GraphQL 내부 서버 오류'
description: ACSD-58566 패치를 적용하여 GraphQL이 'addPurchaseOrderComment' 돌연변이의 'created_at' 필드를 쿼리할 때 내부 서버 오류를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%
---
# ACSD-58566: 구매 주문 설명에 대한 GraphQL 내부 서버 오류

ACSD-58566 패치는 `addPurchaseOrderComment` 돌연변이의 `created_at` 필드 쿼리가 예상 날짜/시간 대신 null 값을 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58566입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL이 `addPurchaseOrderComment` 돌연변이의 `created_at` 필드를 쿼리할 때 내부 서버 오류를 반환합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되고 회사 및 구매 발주가 활성화됩니다.

<u>재현 단계</u>:

1. 회사 사용자에 대한 고객 토큰을 생성합니다.
1. 다음 GraphQL 요청 시퀀스를 수행합니다.
   1. `customerCart`을(를) 사용하여 *장바구니*&#x200B;을(를) 만듭니다.
   1. `addProductsToCart`을(를) 사용하여 *장바구니*&#x200B;에 제품을 추가합니다.
   1. `placePurchaseOrder`을(를) 사용하여 주문합니다.
   1. `addPurchaseOrderComment`을(를) 사용하여 구매 주문에 댓글을 추가합니다.

   ```graphql
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

```json
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

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
