---
title: 'MDVA-39031: GraphQL을 통해 장바구니에 할당 해제된 제품 추가 가능'
description: MDVA-39031 패치는 대상 웹 사이트에 할당되지 않았더라도 GraphQL을 통해 장바구니에 제품을 추가할 수 있는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39031입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 6250c6f6-b74b-4713-a704-d252270693d4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-39031: GraphQL을 통해 장바구니에 할당 해제된 제품 추가 가능

MDVA-39031 패치는 대상 웹 사이트에 할당되지 않았더라도 GraphQL을 통해 장바구니에 제품을 추가할 수 있는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39031입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

대상 웹 사이트에 할당되지 않은 경우에도 GraphQL을 통해 장바구니에 제품을 추가할 수 있습니다.

<u>재현 단계</u>:

1. 보조 웹 사이트를 만듭니다.
1. 제품을 만들고 기본 웹 사이트에 할당합니다.
1. GraphQL을 사용하여 보조 웹 사이트에 대한 빈 장바구니를 만듭니다.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

   다음과 같은 헤더 포함:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

1. 기본 웹 사이트에 할당된 제품을 보조 웹 사이트의 장바구니에 추가합니다.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: &lbrack;
            &lbrace;
              quantity: 1
              sku: "p1"
            &rbrace;
          &rbrack;
        ) &lbrace;
          cart &lbrace;
           items &lbrace;
            product &lbrace;
              name
              sku
            &rbrace;
            quantity
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

   헤더

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

<u>예상 결과</u>:

제품이 헤더에 정의된 스토어에 할당되지 않았기 때문에 장바구니에 추가되지 않습니다.

<u>실제 결과</u>:

제품이 장바구니에 추가되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
