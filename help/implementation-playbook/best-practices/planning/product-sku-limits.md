---
title: 제품 제한 우수 사례
description: 사이트 성능을 극대화하도록 제품 SKU(Stock Keeping Unit)를 구성하는 모범 사례에 대해 배웁니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# 제품 SKU 구성에 대한 우수 사례

성능을 극대화하기 위해 효과적인 제품 재고 관리 단위(SKU)에 권장되는 최대 값은 1천만 개입니다. 이 유효 제품 최대값은 다음과 같이 계산됩니다.

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

최대 유효 SKU 수 이상을 보유하면 제품 데이터 검색이 느려지고 관리 작업을 완료하는 시간이 늘어납니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 수 감소

제품(SKU)을 줄이려면 다음 전략을 사용하십시오.

- 다중 범위 최소화—
   - 스토어 또는 웹 사이트를 이동하면 승수가 줄어듭니다. 50,000개의 SKU, 10개의 웹 사이트 및 10개의 고객 그룹이 있는 경우 유효 SKU 수는 500만 개입니다. 5개의 고객 그룹을 제거하면 유효 SKU가 250만 개로 줄어듭니다.
   - 공유 카탈로그 및 고객 그룹 승수를 대체하려면 사용자 지정 가격책정에 대체 제품 기능을 사용하십시오.
- 카탈로그 재구성—
   - 카테고리에 할당된 제품 수를 줄입니다.
   - 저장소, 웹 사이트, 고객 그룹 또는 제품 수를 줄여 SKU 수를 줄입니다.
- 별도의 제품을 만드는 대신 사용자 지정 옵션을 사용하여 더 많은 제품 변형을 제공합니다.
- 모듈과 같은 사용되지 않는 시스템 구성 요소를 비활성화하거나 제거합니다. (자세한 내용은  [모듈 제거](../../../installation/tutorials/uninstall-modules.md))
- 외부 PMS(플랫폼 관리 시스템)에서 제품을 관리합니다.

## 추가 정보

- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [제품 지정](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- 클라우드 인프라: [여러 웹 사이트 및 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 온-프레미스: [여러 웹 사이트 또는 저장소](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce on cloud 인프라: 저장소 구성 우수 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
