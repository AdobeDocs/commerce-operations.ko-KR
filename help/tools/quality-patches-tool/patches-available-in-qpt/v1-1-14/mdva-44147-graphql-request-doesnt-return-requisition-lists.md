---
title: 'MDVA-44147: [!DNL GraphQL] 요청이 [!UICONTROL Requisition Lists]을(를) 반환하지 않습니다.'
description: MDVA-44147 패치는  [!DNL GraphQL] 요청이 [!UICONTROL Requisition Lists]을(를) 반환하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44147입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# MDVA-44147: [!DNL GraphQL] 요청이 [!UICONTROL Requisition Lists]을(를) 반환하지 않습니다.

MDVA-44147 패치는 [!DNL GraphQL] 요청이 [!UICONTROL Requisition Lists]을(를) 반환하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44147입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL] 요청이 [!UICONTROL Requisition Lists]을(를) 반환하지 않습니다.

<u>재현 단계</u>:

1. **스토어** > **설정** > **구성** > **일반** > **B2B 기능**(으)로 이동하여 **[!UICONTROL Requisition List]**&#x200B;을(를) 사용하도록 설정합니다.
1. 고객으로 로그인하고 [[!UICONTROL Requisition List]](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists)에 제품을 추가합니다.
1. [[!UICONTROL Customer Token]](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/) 만들기

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) &lbrace;
          token
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. 다음 쿼리를 사용하여 고객으로부터 모든 [!UICONTROL Requisition Lists]을(를) 검색합니다. 값이 `Bearer <customer_token>`인 **Authorization** 헤더를 사용합니다. 자세한 내용은 개발자 설명서에서 [고객 쿼리](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) 문서를 참조하십시오.

   요청:

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   응답:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "customer": &lbrace;
          "requisition_lists": &lbrace;
            "items": &lbrack;
            &lbrace;
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": &lbrace;
                "items": &lbrack;
                &lbrace;
                  "uid": "MQ==",
                  "product": &lbrace;
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    &rbrace;,
                    "quantity": 1
                  &rbrace;
                  &rbrack;,
                  "total_pages": 1
                &rbrace;
              &rbrace;
              &rbrack;,
              "total_count": 1
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. 반환된 목록(MQ==)에서 항목의 UID을 복사하고 다음 쿼리를 사용하여 UID으로 필터링된 목록을 가져옵니다.

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20,
          filter: &lbrace;
            uids: &lbrace;
              eq: "MQ=="
            &rbrace;
          &rbrace;
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

<u>예상 결과</u>:

하나의 결과가 반환됩니다.

<u>실제 결과</u>:

결과가 0으로 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [[!DNL Quality Patches Tool] 안내서의  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.

[!DNL QPT]에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
