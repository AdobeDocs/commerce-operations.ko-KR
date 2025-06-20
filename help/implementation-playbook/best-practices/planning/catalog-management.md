---
title: 카탈로그 관리 우수 사례
description: 장바구니 제한 및 제품 속성 구성, 페이지 매김, 옵션, 프로모션 및 변형을 나열하는 데 대한 권장 사항에 대해 알아봅니다.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# 카탈로그 관리 우수 사례

여기에 설명된 카탈로그 관리 우수 사례는 다음을 포함하되 이에 국한되지 않는 다양한 문제를 다룹니다.

- 장바구니 한도
- 범주 제한
- 제품 속성
- 제품 목록 페이지 매김
- 제품 옵션
- 제품 변형
- 프로모션

## 장바구니 제한

최상의 성능을 얻으려면 다음 지침을 사용하여 Adobe Commerce에 대한 장바구니 제한을 관리하십시오.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 장바구니 항목 수 줄이기

장바구니 항목 수를 관리하려면 다음 전략을 사용하십시오

- [!UICONTROL Add Item by SKU] 기능을 사용하여 주문을 행 수가 적은 여러 개의 작은 주문으로 분할합니다.
- 항목 목록을 로드하는 데 필요한 사용자 지정 논리 및 장바구니 사용자 지정만 추가하십시오.

## 범주 제한

많은 범주를 구성하면 성능에 영향을 줄 수 있습니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 제품 수 감소

범주 수를 줄이려면 다음 전략을 사용하십시오.

- 속성 및 사용자 지정 옵션을 통해 고유 제품 기능 관리
- 비활성 범주 제거
- 탐색에서 카탈로그 깊이 최적화

## 제품 속성

너무 많은 제품 속성이나 제품 속성 옵션을 구성하면 성능에 영향을 줄 수 있습니다.

>[!NOTE]
>
>제품 속성은 모든 제품에 전체적으로 적용되는 기능을 지정합니다. 제품 속성 옵션은 특정 제품에 적용되는 기능을 지정하기 위한 사용자 지정입니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 속성 수 감소

관리자로부터 제품을 관리하고 상점에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 제품마다 다른 제품 템플릿(속성 집합)을 사용합니다.
- 변형 관리를 위해 사용자 정의 옵션 및 복잡한 제품 활용
- 검색 가능한 속성의 수를 최소화합니다.
- 사용되지 않는 제품 속성을 제거합니다.
- 외부 제품 관리 시스템(PMS)에 비상거래 관련 속성을 저장하고 관리합니다.

### 속성 옵션 수 줄이기

관리자로부터 제품을 관리하고 상점에서 제품 데이터를 검색할 때 최상의 성능을 얻으려면:

- 복잡한 제품, 제품 변형의 소스로 사용자 정의 옵션 등 다양한 변형 메커니즘을 사용하여 제품을 만들 수 있습니다.
- 일반화된 제품 템플릿 및 옵션 컨테이너를 피하도록 타깃팅 속성 및 옵션을 사용하여 특정 제품 템플릿을 작성합니다.
- 실제 속성 옵션 목록을 유지 관리합니다.
- 외부 제품 관리 시스템(PMS)을 통해 제품 정보를 관리합니다.

### 속성 세트 수 감소

MySQL을 사용하여 사용되지 않은 제품 속성 집합을 제거합니다.

#### 속성 집합 구성 검토

1. [사이트 데이터베이스에 연결](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database).

1. MySQL을 사용하여 속성 세트 수 찾기

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 사용하지 않는 특성 세트를 모두 제거.

### 성능에 영향을 미칠 수 있음

많은 **제품 특성**&#x200B;을 구성하면 각 제품(EAV 구조)에 대한 제품 템플릿 크기와 검색해야 하는 데이터의 양이 증가합니다. 이러한 증가는 다음과 같은 방식으로 작업에 영향을 줍니다.

- EAV 데이터 검색과 관련된 SQL 쿼리 트래픽 증가 및 처리된 데이터 양 증가로 인해 DB 처리량 감소
- Adobe Commerce 인덱스 및 전체 텍스트 검색 인덱스의 크기가 크게 증가했습니다
- 크기가 큰 제품 템플릿에 대한 FLAT 인덱스를 작성할 때 엄격한 MySQL 제한에 도달하고 사용할 수 없음

제품 데이터 및 인덱스 크기가 증가하면 다음과 같은 방식으로 사이트 성과에 영향을 줄 수 있습니다.

- 카탈로그 검색, 검색(빠른 및 고급) 및 계층화된 탐색과 관련된 대부분의 상점 시나리오에 대한 응답 시간이 증가했습니다.
- 관리자의 제품 관리 작업이 상당히 느려져 시간 초과가 리드 수 있습니다.
- 제품 대량 작업 기능을 차단할 수 있습니다.
- 중간 규모 및 대형 카탈로그에 대한 Index 다시 빌드 시간은 실행 시간이 길기 때문에 매일 수행할 수 없습니다.

다음과 같은 방법으로 많은 **특성 옵션**&#x200B;을 구성하면 사이트 성능에 영향을 줄 수 있습니다.

- 복잡한 제품을 포함하는 PDP(제품 세부 사항) 및 카테고리 페이지의 긴 요청 및 렌더링 시간.
- 관리 제품 저장 작업 응답 시간이 최적의 성능 목표보다 증가합니다.
- 제품 편집 양식 렌더링 시간 증가.
- 체크아웃을 느리게 합니다.

## 제품 옵션

제품당 너무 많은 제품 옵션을 구성하면 성능에 영향을 줄 수 있습니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 옵션 수 감소

제품당 제품 옵션 수를 줄이려면 다음 전략을 사용하십시오.

- 복잡한 제품 및 사용자 지정 옵션을 제품 변형의 소스로 구성합니다.
- 모든 제품에 적용되는 글로벌 제품 템플릿과 옵션 컨테이너를 작성하는 대신 속성 세트를 사용하여 타깃팅된 속성과 옵션을 사용하는 특정 제품 템플릿을 작성합니다.
- 외부 제품 관리 시스템(PMS)을 통해 제품 정보를 관리합니다.

### 성능에 영향을 미칠 수 있음

많은 제품 옵션을 구성하면 모든 읽기 및 쓰기 작업에서 각 제품에 대해 검색되는 데이터의 양이 증가하므로 다음과 같은 결과가 발생합니다.

- SQL 쿼리 트래픽이 증가하고 `JOIN` 작업이 많으면 데이터베이스 처리량이 증가합니다.
- Adobe Commerce 색인 및 전체 텍스트 검색 색인의 크기가 늘어났습니다.

위에 나열된 증가는 다음과 같은 방식으로 사이트 성능에 영향을 줄 수 있습니다.

- 속성에 많은 옵션이 포함된 제품과 관련된 대부분의 상점 시나리오에 대한 응답 시간이 길어졌습니다.
- 특히, 프로모션 규칙 관리를 포함하여 속성 목록 및 트리 검색과 관련된 시나리오의 경우 시간 초과로 이어질 수 있는 Admin에서 제품 관리 작업을 완료하는 데 필요한 시간이 크게 늘어났습니다.
- 공유 카탈로그의 여러 제품에 사용자 지정 가격을 지정 및 내보내기와 같은 비동기 대량 작업을 완료하는 대량 작업을 차단할 수 있습니다.

## 제품 목록 페이지 매김

페이지 당 너무 많은 제품을 표시하면 성능에 영향을 줄 수 있습니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 제품 목록 구성 업데이트

범주에 제품이 너무 많으면 상점 카탈로그 구성을 업데이트하여 **페이지당 모든 제품 허용** 옵션을 비활성화하십시오.

이 옵션을 비활성화하면 Adobe Commerce은 제품 목록 상점 페이지 매김 컨트롤을 사용하여 상점 첫 번째 구성 요소에 표시되는 제품 수를 관리합니다. 자세한 내용은 [페이지 매김 컨트롤 구성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html?lang=ko#configure-the-pagination-controls)을 참조하십시오.

## 제품 SKU 제한

너무 많은 제품 SKU를 구성하면 제품 데이터 검색 속도가 느려지고 관리 작업이나 색인을 완료하는 시간이 증가하여 성능에 영향을 줄 수 있습니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 제품 수 감소

제품 수(SKU)를 줄이려면 다음 전략을 사용하십시오.

- 승수 최소화—
   - 웹 사이트를 통합하면 승수가 줄어듭니다.
   - 사용자 지정 가격에 대해 대체 제품 기능을 사용하여 공유 카탈로그 및 고객 그룹 승수를 바꿉니다.
   - 고객 그룹과 공유 카탈로그 모두 스토어에 있는 유효한 SKU 수에 대한 승수로 작동합니다.
- 카탈로그 재구성—
   - 범주에 할당된 제품 수를 줄입니다.
   - 웹 사이트, 고객 그룹, 공유 카탈로그, 제품 수 또는 구성 가능한 제품 옵션 수를 줄여 SKU 수를 줄입니다.
- 별도의 제품을 만들지 않고 사용자 지정 옵션을 사용하여 더 많은 제품 변형을 제공합니다.
- 계정 경우 유효 SKU에는 가격이 각 스토어 또는 고객 그룹에 따라 다르게 지정될 수 있기 때문에 가격의 여러 잠재적 순열이 포함될 수 있습니다.
- 사용하지 않는 시스템 구성 요소 좋아요 모듈을 비활성화하거나 제거합니다. [모듈 제거](../../../installation/tutorials/uninstall-modules.md)를 참조하십시오.
- 외부 플랫폼 관리 시스템(PMS)에서 제품을 관리합니다.

## 제품 변형

제품당 너무 많은 변형을 구성하면 성능에 영향을 줄 수 있습니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) :

- 클라우드 인프라 기반 Adobe Systems Commerce
- Adobe Systems Commerce 온-프레미스

### 변형 수 줄이기

최상의 사이트 성능을 얻으려면 다음 전략을 사용하여 제품 변형의 수를 줄이십시오.

- 다양한 제품에 변형 수를 분산하여 카탈로그를 재구성합니다.
- 재고가 없는 구성 가능한 속성 옵션을 제거합니다.
- 사용자 지정 옵션, 카테고리, 관련 항목, 그룹화 및 번들 제품과 같은 대체 기능을 통해 변형을 관리합니다.

### 성능에 영향을 미칠 수 있음

제품 변형의 권장 수를 초과하면 다음 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 복잡한 제품을 포함하는 제품 세부 사항 및 카테고리 페이지의 긴 요청 및 렌더링 시간.
- 관리자의 저장 작업을 완료하는 데 걸리는 응답 시간이 늘어났습니다.
- 제품 편집 양식을 렌더링하는 데 시간이 늘어났습니다.
- 체크아웃을 느리게 합니다.

## 프로모션

다음 모범 사례에 따라 장바구니에 있는 항목에 대한 판매 및 판촉을 구성하십시오.

- **판매 규칙(장바구니 가격 규칙)**
   - 사용하지 않는 규칙을 관리하고 제거합니다.
   - 가장 효율적인 일치를 위해 엄격한 규칙 조건(예: 속성 또는 범주 필터)을 추가합니다.
- **쿠폰**
   - 사용하지 않거나 만료된 쿠폰을 제거합니다.
   - 캠페인 요구 사항을 충족하는 데 필요한 쿠폰 수만 생성합니다.

### 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

### 성능에 영향을 미칠 수 있음

장바구니 가격 규칙 또는 쿠폰이 권장되는 최대 수보다 많으면 다음 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 장바구니에 제품이 추가될 때 응답 시간이 늘어났습니다.
- 미니 마트를 로드하고 렌더링하는 데 시간이 늘어났습니다.
- 장바구니 페이지를 렌더링하는 데 시간이 늘어났습니다.
- 체크아웃 페이지에서 **합계** 블록을 렌더링하는 시간이 늘어났습니다.
