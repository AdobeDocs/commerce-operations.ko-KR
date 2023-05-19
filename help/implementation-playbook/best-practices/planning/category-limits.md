---
title: 범주 구성 모범 사례
description: 카탈로그의 카테고리 수를 제한하여 사이트 성능을 극대화하는 모범 사례에 대해 알아봅니다.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 카테고리 구성에 대한 우수 사례

최상의 성능을 위해 Adobe Commerce 사이트에 대해 권장되는 최대 범주 수를 초과하여 구성하지 마십시오.

- Adobe Commerce 버전 2.4.2 이상의 경우 최대 6000개의 범주를 구성합니다
- Adobe Commerce 버전 2.3.x 및 2.4.0에서 2.4.1-p1까지의 경우 최대 3000개의 범주를 구성합니다

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 수 감소

범주 수를 줄이려면 다음 전략을 사용하십시오.

- 속성 및 사용자 지정 옵션을 통해 고유 제품 기능 관리
- 비활성 범주 제거
- 탐색에서 카탈로그 깊이 최적화

## 성능에 영향을 미칠 수 있음

권장되는 최대 카테고리 수를 초과하면 다음과 같은 방식으로 사이트 성능에 영향을 줄 수 있습니다.

- 캐시되지 않은 카탈로그 페이지에 대한 응답 시간이 눈에 띄게 늘어남
- 관리자로부터 범주를 관리하는 동안 장기 실행 및 시간 초과
- 해당 데이터베이스 테이블의 크기 증가
- 색인 테이블이 클수록 색인 작업을 완료하는 데 필요한 시간이 늘어납니다. `[category/product relation index\]`
- 카테고리 트리 작성, 메뉴 검색 및 카테고리 규칙 관리 작업을 완료하는 데 걸리는 처리 시간 증가

## 추가 정보

- [카테고리 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [탐색 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [제품 할당](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [클라우드 인프라의 Adobe Commerce: 스토어 구성 모범 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
