---
title: 제품 제한 우수 사례
description: 사이트 성능을 극대화하도록 제품 SKU(Stock Keeping Unit)를 구성하는 모범 사례에 대해 배웁니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e259f9b999566447469200c93db3bc4ba06434c0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# 제품 SKU 구성에 대한 우수 사례

성능을 극대화하기 위해 효과적인 제품 재고 관리 단위(SKU)에 권장되는 최대 값은 2억 4200만 개입니다. 이 유효 제품 SKU 최대값은 다음과 같이 계산됩니다.

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

위치:

- N은 해당 카테고리의 항목 수를 나타냅니다
- 고객 그룹은 공유 카탈로그를 추가하여 추가 고객 그룹을 생성합니다.

최대 유효 SKU 수 이상을 갖는 경우 제품 데이터 검색이 느려지고 관리 패널 작업 또는 색인을 완료하는 시간이 늘어납니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 수 감소

제품(SKU)을 줄이려면 다음 전략을 사용하십시오.

- 다중 범위 최소화—
   - 웹 사이트를 통합하면 승수가 줄어듭니다. 50,000개의 SKU, 10개의 웹 사이트 및 10개의 고객 그룹이 있는 경우 유효 SKU 수는 500만 개입니다. 5개의 고객 그룹을 제거하면 유효 SKU가 250만 개로 줄어듭니다.
   - 공유 카탈로그 및 고객 그룹 승수를 대체하려면 사용자 지정 가격책정에 대체 제품 기능을 사용하십시오.
   - 스토어의 유효한 SKU 수에 대한 고객 그룹과 공유 카탈로그 기능은 모두 승수로 작동합니다.
- 카탈로그 재구성—
   - 카테고리에 할당된 제품 수를 줄입니다.
   - 웹 사이트, 고객 그룹, 공유 카탈로그, 제품 수 또는 구성 가능한 제품 옵션 수를 줄여 SKU 수를 줄입니다
- 별도의 제품을 만드는 대신 사용자 지정 옵션을 사용하여 더 많은 제품 변형을 제공합니다.
- 비용 은 각 스토어 또는 고객 그룹에 따라 다르게 지정할 수 있으므로 유효 SKU에 잠재적인 가격 변동이 포함될 수 있다는 점을 고려합니다.
- 모듈과 같은 사용되지 않는 시스템 구성 요소를 비활성화하거나 제거합니다. (자세한 내용은  [모듈 제거](../../../installation/tutorials/uninstall-modules.md))
- 외부 PMS(플랫폼 관리 시스템)에서 제품을 관리합니다.

## 추가 정보

- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [제품 지정](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [공유 카탈로그 작업](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- 클라우드 인프라: [여러 웹 사이트 및 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 온-프레미스: [여러 웹 사이트 또는 저장소](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce on cloud 인프라: 저장소 구성 우수 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
