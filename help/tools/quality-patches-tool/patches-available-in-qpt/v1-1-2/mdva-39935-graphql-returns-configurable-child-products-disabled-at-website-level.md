---
title: 'MDVA-39935: GraphQL은 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환합니다.'''
description: MDVA-39935 Adobe Commerce 패치는 GraphQL이 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39935입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-39935: GraphQL은 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환합니다.

MDVA-39935 Adobe Commerce 패치는 GraphQL이 웹 사이트 수준에서 비활성화된 구성 가능한 하위 제품을 반환하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39935입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL은 구성 가능한 하위 제품이 웹 사이트 수준에서 비활성화된 후에도 이를 반환합니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **카탈로그** > **인벤토리** > **재고 옵션** > **재고 부족 제품 표시** > **예**&#x200B;에서 재고 부족 제품 표시 옵션을 활성화합니다.
1. 두 개 이상의 **단순 제품**&#x200B;이 있는 **구성 가능한 제품**&#x200B;을 선택하십시오.
1. **간단한 제품**&#x200B;을 사용하지 않도록 설정하고 **구성 가능한 제품**&#x200B;을 저장하세요.
1. GraphQL을 사용하여 **구성 가능한 제품** 데이터를 가져옵니다.

<pre>
  <code class="language-graphql">
&lbrace;
  products(filter: { sku: { eq: "cp1" } }) &lbrace;
    items &lbrace;
      __typename
      name
      sku
      ... on ConfigurableProduct &lbrace;
        variants &lbrace;
          product &lbrace;
            __typename
            name
            sku
            color
            stock_status
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>예상 결과</u>:

비활성화된 제품은 변형 결과에 표시되지 않습니다.

<u>실제 결과</u>:

비활성화된 제품 데이터를 변형 결과로 가져옵니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko) 섹션을 참조하십시오.
