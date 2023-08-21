---
title: 제품 제한 우수 사례
description: 사이트 성능을 최대화하기 위해 제품 SKU(Stock Keeping Unit)를 구성하는 모범 사례에 대해 알아봅니다.
role: Admin
feature: Best Practices, Catalog Management
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 제품 SKU 구성에 대한 우수 사례

성능을 극대화하기 위해 효과적인 제품 SKU(Stocking Keeping Units)의 권장 최대값은 2억 4,200만입니다. 이 유효 제품 SKU 최대값은 다음과 같이 계산됩니다.

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

위치:

- N은 해당 카테고리의 항목 수로 표시됩니다
- 추가 고객 그룹을 만들기 때문에 고객 그룹에는 공유 카탈로그가 포함됩니다.

유효한 SKU의 최대 수보다 많으면 제품 데이터 검색 속도가 느려지고 관리 패널 작업 또는 색인화를 완료하는 시간이 늘어납니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 수 감소

제품 수(SKU)를 줄이려면 다음 전략을 사용하십시오.

- 승수 최소화—
   - 웹 사이트를 통합하면 승수가 줄어듭니다. 50,000개의 SKU, 10개의 웹 사이트 및 10개의 고객 그룹이 있는 경우 유효한 SKU 수는 500만 개입니다. 5개의 고객 그룹을 제거하면 유효 SKU가 250만 개로 줄어듭니다.
   - 사용자 지정 가격에 대해 대체 제품 기능을 사용하여 공유 카탈로그 및 고객 그룹 승수를 바꿉니다.
   - 고객 그룹과 공유 카탈로그 모두 스토어에 있는 유효한 SKU 수에 대한 승수로 작동합니다.
- 카탈로그 재구성—
   - 범주에 할당된 제품 수를 줄입니다.
   - 웹 사이트, 고객 그룹, 공유 카탈로그, 제품 수 또는 구성 가능한 제품 옵션 수를 줄여 SKU 수를 줄입니다.
- 별도의 제품을 만들지 않고 사용자 지정 옵션을 사용하여 더 많은 제품 변형을 제공합니다.
- 각 스토어 또는 고객 그룹별로 가격을 다르게 지정할 수 있으므로 유효 SKU에 여러 잠재적 가격 순열이 포함될 수 있다는 점을 고려합니다.
- 모듈과 같이 사용하지 않는 시스템 구성 요소를 비활성화하거나 제거합니다. (참조:  [모듈 제거](../../../installation/tutorials/uninstall-modules.md).)
- 외부 플랫폼 관리 시스템(PMS)에서 제품을 관리합니다.

## 추가 정보

- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [제품 할당](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [공유 카탈로그 작업](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- 클라우드 인프라: [여러 웹 사이트 및 스토어 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 온-프레미스: [여러 웹 사이트 또는 스토어](../../../configuration/multi-sites/ms-overview.md)
- [클라우드 인프라의 Adobe Commerce: 스토어 구성 모범 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
