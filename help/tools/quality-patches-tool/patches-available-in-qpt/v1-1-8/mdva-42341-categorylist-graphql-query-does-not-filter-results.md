---
title: 'MDVA-42341: "categoryList" GraphQL 쿼리가 결과를 필터링하지 않습니다.'
description: MDVA-42341 패치는 요청에 스토어 헤더가 있는 경우 "categoryList" GraphQL 쿼리가 결과를 필터링하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42341입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341: &quot;categoryList&quot; GraphQL 쿼리가 결과를 필터링하지 않습니다.

MDVA-42341 패치는 요청에 스토어 헤더가 있는 경우 &quot;categoryList&quot; GraphQL 쿼리가 결과를 필터링하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42341입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

요청에 스토어 헤더가 있는 경우 &quot;categoryList&quot; GraphQL 쿼리가 결과를 필터링하지 않습니다.

<u>재현 단계</u>:

1. 새 루트 범주를 만들고 이름을 **root2**&#x200B;로 지정합니다.
1. 두 번째 웹 사이트/스토어/스토어를 만들고 **root2**&#x200B;을(를) 새 스토어에 할당합니다.
1. 기본 루트 범주 = category1에서 새 범주를 만듭니다.
1. GraphQL 요청을 사용하여 두 번째 웹 사이트에 대한 카테고리 목록을 가져옵니다(헤더 저장소 = new 사용).

<pre>
<code class="language-graphql">
&lbrace;
  categoryList(filters: {name: {match: "category1"}}) &lbrace;
    uid
    level
    name
    breadcrumbs &lbrace;
      category_uid
      category_name
      category_level
      category_url_key
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>예상 결과</u>:

&quot;새&quot; 저장소 헤더를 사용하고 있으므로 기본 루트 범주의 범주가 응답에 나열되지 않습니다.

<u>실제 결과</u>:

기본 루트 범주의 범주는 결과에서 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
