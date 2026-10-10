---
title: 'ACSD-51305: GraphQL 응답에서 품절 복합 하위 제품을 사용할 수 없음'
description: ACSD-51305 패치를 적용하여 Adobe Commerce 응답에서 품절 복합 하위 제품을 사용할 수 없는 GraphQL 문제를 해결합니다.
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-51305: GraphQL 응답에서 품절 복합 하위 제품을 사용할 수 없음

ACSD-51305 패치는 GraphQL 응답에서 품절 복합 하위 제품을 사용할 수 없는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51305입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 응답에서 품절 복합 하위 제품을 사용할 수 없습니다.

<u>재현 단계</u>:

1. 관리 웹 사이트에 로그인합니다.
1. 카테고리를 만듭니다(cat1, id=3).
1. *simple1* 제품을 만드십시오(재고 부족, 개별적으로 표시되지 않음, *cat1*&#x200B;에 할당됨).
1. *simple2* 제품을 만듭니다(재고 있음, 개별적으로 표시되지 않음, *cat1*&#x200B;에 할당됨).
1. *simple1* 및 *simple2* 하위 제품이 있는 *bundle1* 제품을 라디오 단추 *option1* 제품으로 만들고 *cat1* 범주에 할당합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**(으)로 이동합니다.

   * **[!UICONTROL Display Out of Stock Products]**&#x200B;을(를) *예*(으)로 설정합니다.

1. 상점 앞에서 *bundle1* 제품을 열고 *simple1* 및 *simple2* 하위 제품이 모두 표시되는지 확인하십시오.
1. 다음 GraphQL 쿼리를 실행합니다.

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>예상 결과</u>:

**[!UICONTROL Options]** 블록 내의 **[!UICONTROL Product]** 섹션이 비어 있지 않습니다.

<u>실제 결과</u>:

**[!UICONTROL Options]** 블록 내의 **[!UICONTROL Product]** 섹션이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]&#x200B;[&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
