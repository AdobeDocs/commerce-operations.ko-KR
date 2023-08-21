---
title: 제품 목록 페이지 매김에 대한 우수 사례
description: Storefront 카탈로그의 각 페이지에 표시되는 제품 수를 관리하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다.
role: User, Admin
feature: Best Practices, Catalog Management
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 제품 목록 페이지 매김에 대한 우수 사례

최상의 성능을 위해 페이지당 최대 48개의 제품을 표시하십시오.

쇼핑객이 단일 페이지에서 모든 카테고리 제품을 볼 수 있도록 Adobe Commerce을 구성할 수 있습니다. 카테고리 제품 수가 48개 제품을 크게 초과하는 경우 상점 페이지 매김 컨트롤에 대한 카탈로그 구성을 업데이트합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 목록 구성 업데이트

범주에 48개가 넘는 제품이 있는 경우 옵션을 비활성화하도록 상점 카탈로그 구성을 업데이트하십시오. **페이지당 모든 제품 허용**.

이 옵션을 비활성화하면 Adobe Commerce은 제품 목록 상점 페이지 매김 컨트롤을 사용하여 상점 첫 번째 구성 요소에 표시되는 제품 수를 관리합니다. 자세한 내용은 [페이지 매김 컨트롤 구성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 추가 정보

- [제품 목록 구성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
