---
title: 제품 옵션 구성 모범 사례
description: 제품 옵션 수를 제한하여 Adobe Commerce 성능을 최적화합니다.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 제품 옵션 모범 사례

최상의 성능을 위해 제품당 최대 100개의 제품 옵션을 구성합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 옵션 축소

최상의 사이트 성능을 얻으려면 다음 전략을 사용하여 제품 옵션 수를 줄이십시오.

- 복잡한 제품 및 사용자 지정 옵션을 제품 변형의 소스로 구성합니다.
- 모든 제품에 적용되는 글로벌 제품 템플릿과 옵션 컨테이너를 작성하는 대신 속성 세트를 사용하여 타깃팅된 속성과 옵션을 사용하는 특정 제품 템플릿을 작성합니다.
- 외부 제품 관리 시스템(PMS)을 통해 제품 정보를 관리합니다.

## 성능에 영향을 미칠 수 있음

많은 제품 옵션을 구성하면 모든 읽기 및 쓰기 작업에서 각 제품에 대해 검색되는 데이터의 양이 증가하므로 다음과 같은 결과가 발생합니다.

- SQL 쿼리 트래픽 증가 및 속도 증가 `JOIN` 데이터베이스 처리량이 증가합니다.
- Adobe Commerce 색인 및 전체 텍스트 검색 색인의 크기가 늘어났습니다.

위에 나열된 증가는 다음과 같은 방식으로 사이트 성능에 영향을 줄 수 있습니다.

- 속성에 많은 옵션이 포함된 제품과 관련된 대부분의 상점 시나리오에 대한 응답 시간이 길어졌습니다.
- 특히, 프로모션 규칙 관리를 포함하여 속성 목록 및 트리 검색과 관련된 시나리오의 경우 시간 초과로 이어질 수 있는 Admin에서 제품 관리 작업을 완료하는 데 필요한 시간이 크게 늘어났습니다.
- 공유 카탈로그의 여러 제품에 사용자 지정 가격을 지정 및 내보내기와 같은 비동기 대량 작업을 완료하는 대량 작업을 차단할 수 있습니다.

## 추가 정보

- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [제품 속성 구성에 대한 우수 사례](product-attributes-and-options.md)
- [대량 작업 로그](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [재고 일괄 조치 API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [교육: Adobe Commerce을 사용하여 카탈로그 및 제품 관리](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
