---
title: 제품 특성 구성 모범 사례
description: 제품 속성, 속성 옵션 및 속성 세트의 수를 제한하여 Adobe Commerce 성능을 최적화하는 방법에 대해 알아봅니다
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# 제품 속성 구성에 대한 우수 사례

- 최상의 성능을 위해 제품 속성 또는 제품 속성 옵션의 최대 권장 수보다 많은 수를 구성하지 마십시오.

- **제품 속성**—
   - Adobe Commerce 버전 2.3.x 및 2.4.0에서 2.4.1-p1까지의 경우 500개 이하의 속성을 구성합니다.
   - Adobe Commerce 버전 2.4.2 이상의 경우 최대 1500개의 제품 속성을 구성합니다
- **제품 속성 옵션**-각 속성에 대해 최대 100개의 속성 옵션 구성
- **제품 속성 집합**-최대 1000개의 속성 세트 구성 _

>[!NOTE]
>
>제품 속성은 모든 제품에 전역적으로 적용되는 기능을 지정합니다. 제품 속성 옵션은 특정 제품에 적용되는 기능을 지정하는 사용자 정의입니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 제품 속성 수 감소

관리자로부터 제품을 관리하고 상점에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 다른 제품에 대해 다른 제품 템플릿(속성 세트)을 사용합니다.
- 변형 관리를 위해 사용자 정의 옵션 및 복잡한 제품 활용
- 검색 가능한 속성의 수를 최소화합니다.
- 사용되지 않는 제품 속성을 제거합니다.
- 외부 제품 관리 시스템(PMS)에 비상거래 관련 속성을 저장하고 관리합니다.

## 제품 속성 옵션 수 감소

관리자로부터 제품을 관리하고 상점에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 복잡한 제품, 제품 변형의 소스로 사용자 정의 옵션 등 다양한 변형 메커니즘을 사용하여 제품을 만들 수 있습니다.
- 일반화된 제품 템플릿 및 옵션 컨테이너를 피하도록 타깃팅 속성 및 옵션을 사용하여 특정 제품 템플릿을 작성합니다.
- 실제 속성 옵션 목록을 유지 관리합니다.
- 외부 제품 관리 시스템(PMS)을 통해 제품 정보를 관리합니다.

## 제품 속성 세트 수 감소

MySQL을 사용하여 사용되지 않은 제품 속성 집합을 제거합니다.

### 속성 집합 구성 검토

1. [사이트 데이터베이스에 연결](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. MySQL을 사용하여 속성 세트 수 찾기

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 사용하지 않는 속성 세트를 제거합니다.

## 성능에 영향을 미칠 수 있음

여러 구성 **제품 속성** 각 제품(EAV 구조)에 대한 제품 템플릿 크기와 검색해야 하는 데이터의 양을 늘립니다. 이러한 증가는 다음과 같은 방식으로 작업에 영향을 줍니다.

- EAV 데이터 검색과 관련된 SQL 쿼리 트래픽 증가 및 처리된 데이터 양 증가로 인해 DB 처리량 감소
- Adobe Commerce 인덱스 및 전체 텍스트 검색 인덱스의 크기가 크게 증가했습니다
- 대형 제품 템플릿에 대한 FLAT 인덱스를 작성할 때 하드 MySQL 제한에 도달하고 이를 사용할 수 없음

제품 데이터 및 색인 크기의 증가는 다음과 같은 방식으로 사이트 성능에 영향을 줄 수 있습니다.

- 카탈로그 탐색, 검색(빠른 고급) 및 계층화된 탐색과 관련된 대부분의 상점 시나리오에 대한 응답 시간이 늘어났습니다.
- 관리자의 제품 관리 작업이 상당히 느려져 시간 초과가 발생할 수 있습니다.
- 제품 일괄 조치 기능을 차단할 수 있습니다.
- 중대형 카탈로그의 색인 재작성 시간은 긴 실행 시간으로 인해 일별로 수행할 수 없습니다.

여러 구성 **속성 옵션** 은 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 복잡한 제품을 포함하는 PDP(제품 세부 사항) 및 카테고리 페이지의 긴 요청 및 렌더링 시간.
- 관리 제품 저장 작업 응답 시간이 최적의 성능 목표보다 증가합니다.
- 제품 편집 양식 렌더링 시간 증가.
- 체크아웃을 느리게 합니다.

## 추가 정보

- [제품 속성 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [속성 집합](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [사용자 지정 튜토리얼 > 제품 만들기 양식 사용자 지정](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
