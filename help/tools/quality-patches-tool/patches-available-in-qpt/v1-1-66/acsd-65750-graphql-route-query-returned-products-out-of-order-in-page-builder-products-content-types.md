---
title: 'ACSD-65750: [!DNL GraphQL] "route" 쿼리가  [!DNL Page Builder] Products 콘텐츠 형식에서 잘못된 제품을 반환합니다.'
description: ACSD-65750 패치를 적용하여 GraphQL "route" 쿼리가  [!DNL Page Builder] Products 콘텐츠 형식에서 잘못된 제품을 반환하는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 2d6debf4d426a0473eb77919c2307afdc77bf937
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-65750: [!DNL GraphQL] &quot;route&quot; 쿼리가 [!DNL Page Builder] 제품 콘텐츠 형식에서 잘못된 제품을 반환합니다.

ACSD-65750 패치는 [!DNL GraphQL] &quot;route&quot; 쿼리가 [!DNL Page Builder] Products 콘텐츠 형식에서 잘못된 제품을 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65750입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL] 제품 콘텐츠 형식을 사용할 때 [!DNL Page Builder] &quot;route&quot; 쿼리가 올바른 정렬 순서로 제품을 반환하지 않습니다.

<u>재현 단계</u>:

1. 새 범주와 카탈로그의 일부 제품을 만들고 제품을 이 범주에 연결합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**(으)로 이동하여 만든 범주를 편집하고 **[!UICONTROL Products in Category]** 탭을 엽니다.
1. 이 범주의 각 제품에 대해 사용자 지정 **[!UICONTROL Position]**&#x200B;을(를) 설정합니다.
1. 범주를 저장하고 색인 재지정을 실행합니다.
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**(으)로 이동한 다음 **[!UICONTROL Add New Page]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Content]** 탭을 확장한 다음 **[!UICONTROL Edit with Page Builder]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Row]** 요소를 콘텐츠 영역으로 끌어 놓은 다음 **[!UICONTROL Products]** 요소를 행 내부로 끌어 놓습니다.
1. Products 요소를 다음과 같이 구성합니다.
   * **[!UICONTROL Select Products By]**: *범주*
   * **[!UICONTROL Category]**: *새로 만든 범주 선택*
   * **[!UICONTROL Sort By]**: *위치*
1. **[!UICONTROL Search Engine Optimization]** 탭으로 전환하고 **[!UICONTROL URL Key]**&#x200B;을(를) *test-widget*(으)로 설정하십시오.
1. 페이지를 저장합니다.
1. 다음 [!DNL GraphQL]개의 요청을 만듭니다.

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>예상 결과</u>:

시스템은 범주 위치에 정의된 순서대로 제품을 반환합니다.

<u>실제 결과</u>:

시스템은 GraphQL 응답에서 카테고리 위치와 일치하지 않는 순서로 제품을 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
