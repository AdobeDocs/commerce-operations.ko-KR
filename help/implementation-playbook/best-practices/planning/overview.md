---
title: 구현 계획 단계
description: Adobe Commerce 프로젝트의 계획 단계에 대한 구현 모범 사례에 대해 알아봅니다.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# 계획 단계

계획 단계에는 다음 활동이 포함됩니다.

- 요구 사항 수집
- 건축설계
- 카탈로그 디자인
- 프로젝트 범위 지정
- 계정 프로비저닝
- 사용자 액세스
- 확장 구매

다음 섹션에는 계획 단계에 대한 모범 사례 정보가 포함됩니다.

## 요구 사항 수집

- **애플리케이션 구성**
   - [사이트 구성, 저장소 및 저장소 보기 모범 사례(클라우드 인프라)](sites-stores-store-views.md)
   - [Adobe Commerce 사이트에 대한 5가지 가장 일반적인 구성 문제를 예방 및 해결하는 방법](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [캐싱 우수 사례](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [전체 페이지 캐싱](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache 메모리 크기](opcache-memory-size.md)
   - [보고 구성](reporting-configuration.md)

- **데이터베이스 구성**
   - [클라우드 배포를 위한 데이터베이스 구성 &#x200B; 모범 사례](database-on-cloud.md)
   - [MySQL 슬레이브 연결 &#x200B; 구성](configure-mysql-slave-connection-on-cloud.md)
   - [MySQL 트리거 사용](mysql-triggers-usage.md)

- **서비스 구성**
   - [기본 설정](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - 알림 채널 구성](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis 서비스 구성에 대한 &#x200B; 우수 사례](redis-service-configuration.md)
   - [Realpath 캐시 크기 모범 사례](realpath-cache-size.md)

## **건축설계**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [글로벌 참조 아키텍처 이해](../../../implementation-playbook/architecture/global-reference.md)

## **카탈로그 디자인**

다음 항목에서는 카테고리 수, 제품 유효 SKU, 제품 변형, 제품 속성 및 옵션 등에 대한 권장 최대값을 포함하여 Adobe Commerce 카탈로그를 구성하기 위한 성능 최적화 모범 사례를 설명합니다.

- [카테고리 구성](category-limits.md)
- [제품 &#x200B; 구성](product-sku-limits.md)
- [제품 변형 구성](product-variations.md)
- [제품 옵션 구성](product-options.md)
- [제품 특성 &#x200B; 구성](product-attributes-and-options.md)
- [제품 목록에 대한 페이지 매김 구성](product-listing-pagination.md)

## **판매 및 마케팅**

- [제품 장바구니 제한에 대한 &#x200B; 우수 사례](product-cart.md)
- [프로모션 구성 우수 사례](product-cart-promotions.md)

## **프로젝트 범위 지정**

- [파트너 문제 제기](partner-escalation.md)

## **구매 확장**

- [Adobe Commerce에서 타사 확장을 사용하는 &#x200B; 우수 사례](extensions.md)
