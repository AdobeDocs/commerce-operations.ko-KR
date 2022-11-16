---
title: 제품 속성 구성 우수 사례
description: 제품 특성, 특성 옵션 및 속성 세트의 수를 제한하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# 제품 속성 구성에 대한 우수 사례

- 최상의 성능을 위해 제품 속성 또는 제품 속성 옵션의 최대 권장 수를 초과하지 않도록 하십시오.

- **제품 속성**—
   - Adobe Commerce 버전 2.3.x 및 2.4.0~2.4.1-p1의 경우 500개 이하의 속성을 구성합니다
   - Adobe Commerce 버전 2.4.2 이상의 경우 최대 1500개의 제품 속성을 구성합니다
- **제품 속성 옵션**-각 속성에 대해 최대 100개의 속성 옵션을 구성합니다
- **제품 속성 세트**-최대 1000개의 특성 집합 구성

>[!NOTE]
>
>제품 속성은 모든 제품에 전역적으로 적용되는 기능을 지정합니다. 제품 속성 옵션은 특정 제품에 적용되는 기능을 지정하기 위한 사용자 지정 항목입니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 제품 속성 수 감소

관리자로부터 제품을 관리하고 저장소에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 다른 제품에 대해 다른 제품 템플릿(속성 세트)을 사용합니다.
- 변형 관리를 위한 사용자 정의 옵션 및 복잡한 제품 활용
- 검색 가능한 속성의 수를 최소화합니다.
- 사용되지 않는 제품 속성을 제거합니다.
- 외부 제품 관리 시스템(PMS)에서 비전자 상거래 관련 특성을 저장하고 관리합니다.

## 제품 속성 옵션 수 감소

관리자로부터 제품을 관리하고 저장소에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 다양한 변형 메커니즘을 사용하여 제품을 만들 수 있습니다. 복잡한 제품, 제품 변형의 소스로서의 사용자 지정 옵션.
- 일반화된 제품 템플릿 및 옵션 컨테이너를 방지하기 위해 타깃팅 속성 및 옵션을 사용하여 특정 제품 템플릿을 작성합니다.
- 실제 속성 옵션 목록을 유지합니다.
- 외부 PMS(제품 관리 시스템)를 통해 제품 정보를 관리합니다.

## 제품 특성 집합 수 감소

MySQL을 사용하여 사용되지 않은 제품 속성 세트를 제거합니다.

### 특성 집합 구성 검토

1. [사이트 데이터베이스에 연결](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. MySQL을 사용하여 속성 집합 수를 찾습니다.

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 사용하지 않은 속성 세트를 모두 제거합니다.

## 성능에 영향을 줄 수 있음

많은 구성 **제품 속성** 는 각 제품(EAV 구조)의 제품 템플릿 크기와 검색해야 하는 데이터 양을 늘립니다. 이러한 증가는 다음과 같은 방법으로 작업에 영향을 줍니다.

- EAV 데이터 검색과 관련된 SQL 쿼리 트래픽 및 처리된 데이터 양이 증가하여 DB 처리량이 감소함
- Adobe Commerce 인덱스 및 전체 텍스트 검색 색인의 크기가 크게 증가합니다
- 큰 제품 템플릿에 대한 평면 인덱스를 만들고 사용할 수 없을 때 하드 MySQL에 도달하면 제한이 발생합니다

제품 데이터 및 인덱스 크기가 증가하면 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 카탈로그 탐색, 검색(빠른 및 고급) 및 계층화된 탐색과 관련된 대부분의 상점 시나리오에 대한 응답 시간이 늘어났습니다.
- 관리자의 제품 관리 작업이 매우 느리게 진행되므로 시간 초과가 발생할 수 있습니다.
- 제품 일괄 작업 기능을 차단할 수 있습니다.
- 긴 실행 시간으로 인해 중간 크기 및 대형 카탈로그에 대한 색인 재작성 시간은 매일 수행할 수 없습니다.

많은 구성 **속성 옵션** 은 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 복잡한 제품이 포함된 제품 세부 사항(PDP) 및 카테고리 페이지의 긴 요청 및 렌더링 시간.
- 관리 제품 저장 작업 응답 시간이 최적의 성능 목표보다 증가합니다.
- 제품 편집 양식 렌더링 시간이 늘어납니다.
- 체크아웃을 느리게 합니다.

## 추가 정보

- [제품 속성 개요](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [속성 세트](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [제품 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Customization tutorials > 제품 만들기 양식 사용자 지정](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
