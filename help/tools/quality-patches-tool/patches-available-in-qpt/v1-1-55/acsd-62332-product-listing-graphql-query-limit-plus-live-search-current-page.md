---
title: 'ACSD-62332: 제품 목록 GraphQL 쿼리가 10,000개의 제품으로 제한되고 [!DNL Live Search] 현재 페이지를 1로 설정합니다.'
description: ACSD-62332 패치를 적용하여 Adobe Commerce을 통해 쿼리할 때 제품 목록 GraphQL 쿼리가 10,000개 제품의 total_count로 제한되고  [!DNL Live Search] 현재 페이지를 검색 기준에서 *2* 페이지 대신 *1* 로 설정하는 GraphQL 문제를 해결합니다.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: GraphQL 쿼리를 10,000개의 제품으로 제한한 제품 목록 [!DNL Live Search]에서 현재 페이지를 1로 설정합니다.

>[!NOTE]
>
>이 패치는 업데이트된 [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) 버전이며 2.4.6 - 2.4.6-p8 버전에서 [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md)을(를) 대체합니다. 자세한 내용은 해당 문서를 참조하십시오.

ACSD-62332 패치는 GraphQL 쿼리를 나열하는 제품이 10,000개 제품 중 `total_count`개로 제한되고, GraphQL을 통해 쿼리할 때 [!DNL Live Search]이(가) 검색 기준에서 현재 페이지를 *2* 페이지 대신 *1*(으)로 설정하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-62332입니다. Adobe Commerce 2.4.7에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 목록 GraphQL 쿼리는 총 10,000개의 제품으로 제한되며, 여기서 [!DNL Live Search]은(는) GraphQL을 통해 쿼리할 때 검색 기준에서 현재 페이지를 *2* 페이지 대신 *1*(으)로 설정합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
