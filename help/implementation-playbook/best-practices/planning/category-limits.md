---
title: 카테고리 구성 우수 사례
description: 카탈로그의 카테고리 수를 제한하여 사이트 성능을 극대화하는 모범 사례를 알아봅니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# 카테고리 구성에 대한 우수 사례

최상의 성능을 위해 Adobe Commerce 사이트에 대한 최대 권장 카테고리 수를 초과하여 구성하지 마십시오.

- Adobe Commerce 버전 2.4.2 이상의 경우 최대 6000개의 카테고리를 구성합니다
- Adobe Commerce 버전 2.3.x 및 2.4.0~2.4.1-p1의 경우, 최대 3000개의 카테고리를 구성합니다

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 수 감소

다음 전략을 사용하여 카테고리 수를 줄입니다.

- 속성 및 사용자 지정 옵션을 통해 고유한 제품 기능 관리
- 비활성 범주 제거
- 탐색에서 카탈로그 깊이 최적화

## 성능에 영향을 줄 수 있음

권장되는 최대 카테고리 수를 초과하는 카테고리는 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 캐싱되지 않은 카탈로그 페이지에 대한 응답 시간의 실질적인 증가
- 관리자에서 카테고리를 관리하는 동안 긴 실행 및 시간 초과가 발생합니다
- 해당 데이터베이스 테이블의 크기 증가
- 인덱스 테이블이 크면 색인 작업을 완료하는 데 필요한 시간이 늘어납니다. `[category/product relation index\]`
- 범주 트리 작성, 메뉴 검색 및 범주 규칙 관리 작업을 완료하기 위한 처리 시간이 늘어났습니다

## 추가 정보

- [카테고리 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [탐색 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [제품 지정](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce on cloud 인프라: 저장소 구성 우수 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
