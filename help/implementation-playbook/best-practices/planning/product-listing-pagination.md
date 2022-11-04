---
title: 제품 목록 페이지 매김 우수 사례
description: 상점 카탈로그의 각 페이지에 표시되는 제품 수를 관리하여 Adobe Commerce 성능을 최적화하는 방법을 배웁니다.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# 제품 목록 페이지 매김 우수 사례

최상의 성능을 얻으려면 페이지당 최대 48개의 제품을 표시하십시오.

쇼핑객이 단일 페이지에서 모든 카테고리 제품을 볼 수 있도록 Adobe Commerce을 구성할 수 있습니다. 카테고리 제품 수가 48개 제품을 크게 초과하는 경우 상점 전면 페이지 매김 컨트롤에 대한 카탈로그 구성을 업데이트합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 목록 구성 업데이트

어떤 카테고리에 48개 이상의 제품이 있는 경우 storefront 카탈로그 구성을 업데이트하여 옵션을 사용하지 않도록 설정합니다. **페이지당 모든 제품 허용**.

이 옵션을 비활성화하면 Adobe Commerce에서는 제품 목록 Storefront 페이지 매김 컨트롤을 사용하여 storefront 구성 요소에 표시되는 제품 수를 관리합니다. 자세한 내용은 [페이지 매김 컨트롤 구성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 추가 정보

- [제품 목록 구성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
