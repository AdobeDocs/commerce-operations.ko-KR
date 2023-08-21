---
title: 제품 변형 구성 모범 사례
description: 구성된 제품 변형의 수를 제한하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다.
role: Admin
feature: Best Practices, Catalog Management
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 제품 변형 구성을 위한 우수 사례

최상의 성능을 위해 제품당 최대 50개의 변형을 구성합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 변형 수 감소

최상의 사이트 성능을 얻으려면 다음 전략을 사용하여 제품 변형의 수를 줄이십시오.

- 다양한 제품에 변형 수를 분산하여 카탈로그를 재구성합니다.
- 재고가 없는 구성 가능한 속성 옵션을 제거합니다.
- 사용자 지정 옵션, 카테고리, 관련 항목, 그룹화 및 번들 제품과 같은 대체 기능을 통해 변형을 관리합니다.

## 성능에 영향을 미칠 수 있음

제품 변형의 권장 수를 초과하면 다음 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 복잡한 제품을 포함하는 제품 세부 사항 및 카테고리 페이지의 긴 요청 및 렌더링 시간.
- 관리자의 저장 작업을 완료하는 데 걸리는 응답 시간이 늘어났습니다.
- 제품 편집 양식을 렌더링하는 데 시간이 늘어났습니다.
- 체크아웃을 느리게 합니다.

## 추가 정보

- [구성 가능한 제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 교육—[Adobe Commerce을 사용하여 카탈로그 및 제품 관리](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
