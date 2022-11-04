---
title: 제품 옵션 구성 우수 사례
description: 제품 옵션 수를 제한하여 Adobe Commerce 성능을 최적화합니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# 제품 옵션 우수 사례

최상의 성능을 위해 제품당 최대 100개의 제품 옵션을 구성합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 옵션 감소

최상의 사이트 성능을 위해 다음 전략을 사용하여 제품 옵션 수를 줄입니다.

- 복잡한 제품 및 사용자 지정 옵션을 제품 변형의 소스로 구성합니다.
- 모든 제품에 적용되는 글로벌 제품 템플릿 및 옵션 컨테이너를 만드는 대신 속성 세트를 사용하여 타깃팅된 속성 및 옵션으로 특정 제품 템플릿을 만듭니다.
- 외부 PMS(제품 관리 시스템)를 통해 제품 정보를 관리합니다.

## 잠재적인 성능 영향

여러 제품 옵션을 구성하면 모든 읽기 및 쓰기 작업에서 각 제품에 대해 검색된 데이터의 양이 증가하므로 다음과 같은 문제가 발생합니다.

- SQL 쿼리 트래픽 증가 및 초과 `JOIN` 작업이 데이터베이스 처리량을 증가시킵니다.
- Adobe Commerce 인덱스 및 전체 텍스트 검색 색인의 크기가 늘어났습니다.

위에 나열된 증가는 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 속성에 많은 옵션이 포함된 제품과 관련된 대부분의 상점 시나리오의 응답 시간이 길어졌습니다.
- 특히 프로모션 규칙 관리를 포함한 속성 목록 및 트리 검색과 관련된 시나리오의 경우 시간 초과를 초래할 수 있는 관리에서 제품 관리 작업을 완료하는 데 필요한 시간이 크게 증가합니다.
- 가져오기 및 내보내기, 공유 카탈로그의 여러 제품에 사용자 지정 가격 할당과 같은 비동기 일괄 작업을 완료하는 대량 작업을 차단할 수 있습니다.

## 추가 정보

- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [제품 속성 구성에 대한 우수 사례](product-attributes-and-options.md)
- [대량 작업 로그](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [재고 일괄 작업 API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [교육: Adobe Commerce을 사용하여 카탈로그 및 제품 관리](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

