---
title: 구현 계획 단계
description: Adobe Commerce 프로젝트의 계획 단계에 대한 구현 모범 사례에 대해 알아봅니다.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 계획 단계

계획 단계에는 다음 활동이 포함됩니다.

- 요구 사항 수집
- 건축 디자인
- 카탈로그 디자인
- 프로젝트 범위 지정
- 계정 프로비저닝
- 사용자 액세스
- 확장 구매

다음 섹션에는 계획 단계에 대한 모범 사례 정보가 포함되어 있습니다.

## 요구 사항 수집

- **애플리케이션 구성**
   - [사이트, 스토어 및 스토어 조회수 구성 모범 사례(클라우드 인프라)](sites-stores-store-views.md)
   - [Adobe Commerce 사이트에 발생하는 5가지 가장 일반적인 구성 문제를 방지 및 해결하는 방법](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [캐싱 우수 사례](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [전체 페이지 캐싱](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache 메모리 크기](opcache-memory-size.md)
   - [보고 구성](reporting-configuration.md)

- **데이터베이스 구성**
   - [클라우드 배포를 위한 데이터베이스 구성 모범 &#x200B; 사례](database-on-cloud.md)
   - [MySQL &#x200B; 구성](mysql-configuration.md)

- **서비스 구성**
   - [Fastly 설정](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - 알림 채널 구성](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis 서비스 구성에 대한 우수 사례&#x200B;](redis-service-configuration.md)
   - [Realpath 캐시 크기 모범 사례](realpath-cache-size.md)

## **건축 디자인**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [글로벌 참조 아키텍처 이해](../../../implementation-playbook/architecture/global-reference/overview.md)

## **카탈로그 디자인**

다음 항목에서는 카테고리 수에 대한 권장 최대 수, 제품 유효 SKU, 제품 변형, 제품 속성 및 옵션 등을 포함하여 Adobe Commerce 카탈로그를 구성하기 위한 성능 최적화 모범 사례에 대해 설명합니다.

- [범주 구성](catalog-management.md#category-limits)
- [제품 &#x200B; 구성](catalog-management.md#product-sku-limits)
- [제품 변형 구성](catalog-management.md#product-variations)
- [제품 옵션 구성](catalog-management.md#product-options)
- [제품 속성 &#x200B; 구성](catalog-management.md#product-attributes)
- [제품 목록의 페이지 매김 구성](catalog-management.md#product-listing-pagination)

## **영업 및 마케팅**

- [제품 장바구니 제한에 대한 우수 사례](catalog-management.md#cart-limits)
- [프로모션 구성에 대한 우수 사례](catalog-management.md#promotions)

## **프로젝트 범위 지정**

- [파트너 에스컬레이션](partner-escalation.md)
- [결제 저장 처리](payment-processing-storage.md)

## **확장 구매**

- [Adobe Commerce에서 타사 확장을 사용하기 위한 우수 사례](extensions.md)
