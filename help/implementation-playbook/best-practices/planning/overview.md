---
title: 구현 계획 단계
description: Adobe Commerce 프로젝트의 계획 단계에 대한 구현 모범 사례에 대해 알아봅니다.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# 계획 단계

계획 단계에는 다음 활동이 포함됩니다.

- 건축 디자인
- 카탈로그 디자인
- 확장 구매
- 프로젝트 범위 지정
- 요구 사항 수집
- 영업 및 마케팅

다음 섹션에는 계획 단계에 대한 모범 사례 정보가 포함되어 있습니다.

## 요구 사항 수집

<table>
<thead>
  <tr>
    <th>모범 사례</th>
    <th>설명</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>애플리케이션 구성</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">사이트, 스토어 및 스토어 조회수 구성</a></td>
    <td>사이트, 스토어 및 스토어 보기를 구성하여 사이트 성능을 극대화합니다.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">일반적인 구성 문제</a></td>
    <td>Adobe Commerce 사이트에 대한 5가지 가장 일반적인 구성 문제를 수정하고 방지합니다.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html?lang=ko">캐싱</a></td>
    <td>캐시 관리 도구를 사용하여 사이트의 성능을 향상시킵니다.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">전체 페이지 캐싱</a></td>
    <td>Adobe Commerce 확장에서 캐싱을 구현할 때 공용 데이터로 작업하는 방법을 알아봅니다.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache 메모리 크기</a></td>
    <td>OPcache 메모리 사용량의 특정 설정으로 성능 저하를 방지하십시오.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">보고 구성</a></td>
    <td>보고 모듈을 사용하지 않는 경우 보고서 모듈을 제거하여 사이트 성능을 최적화합니다.</td>
  </tr>
  <tr>
    <td colspan="2"><em>데이터베이스 구성</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">클라우드 배포를 위한 데이터베이스 구성</a></td>
    <td>클라우드 인프라 프로젝트에 Adobe Commerce을 배포할 때 성능을 개선하도록 데이터베이스 및 애플리케이션 설정을 구성합니다.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQL 구성</a></td>
    <td>MySQL 트리거 및 슬레이브 연결이 사이트 성능에 어떻게 영향을 주는지 그리고 이를 효과적으로 사용하는 방법에 대해 알아봅니다.</td>
  </tr>
  <tr>
    <td colspan="2"><em>서비스 구성</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko">Fastly 설정</a></td>
    <td>클라우드 인프라 프로젝트에서 Adobe Commerce에 대한 Fastly 서비스를 구성합니다.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html?lang=ko">New Relic에 대한 알림 채널 구성</a></td>
    <td>New Relic 대시보드에 액세스하고 Adobe Commerce on cloud infrastructure 프로젝트에서 데이터를 분석합니다.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Redis 구성</a></td>
    <td>Adobe Commerce용 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 개선합니다.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath 캐시 크기</a></td>
    <td>권장 설정을 사용하도록 PHP 'readlpath' 캐시 구성을 업데이트하여 성능을 최적화합니다.</td>
  </tr>
</tbody>
</table>

## 카탈로그 디자인

| 모범 사례 | 설명 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [범주 구성](catalog-management.md#category-limits) | 최적의 성능을 위해 제품 카테고리를 구성합니다. |
| [제품 &#x200B; 구성](catalog-management.md#product-sku-limits) | 최적의 성능을 위해 제품 SKU를 구성합니다. |
| [제품 변형 구성](catalog-management.md#product-variations) | 최적의 성능을 위해 제품 변형을 구성합니다. |
| [제품 옵션 구성](catalog-management.md#product-options) | 최적의 성능을 위해 제품 옵션을 구성합니다. |
| [제품 특성 &#x200B; 구성](catalog-management.md#product-attributes) | 최적의 성능을 위해 제품 속성을 구성합니다. |
| [제품 목록에 대한 페이지 매김 구성](catalog-management.md#product-listing-pagination) | 최적의 성능을 위한 제품 목록 페이지 매김 구성 |

## 확장

| 모범 사례 | 설명 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Adobe Commerce에서 타사 확장 사용](extensions.md) | 타사 Adobe Commerce 확장으로 인한 성능 문제를 방지하는 방법을 알아봅니다. |

## 프로젝트 범위 지정

| 모범 사례 | 설명 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [파트너 에스컬레이션](partner-escalation.md) | Adobe 계정 팀과 파트너 문제를 에스컬레이션할 준비를 하거나 에스컬레이션을 방지하는 방법을 알아봅니다. |
| [결제 저장소 처리](payment-processing-storage.md) | 결제 세부 정보를 안전하게 처리하고 저장합니다. |

## 영업 및 마케팅

| 모범 사례 | 설명 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [제품 장바구니 제한](catalog-management.md#cart-limits) | 최적의 성능을 위해 장바구니 제한을 관리합니다. |
| [프로모션 구성](catalog-management.md#promotions) | 장바구니에 있는 항목에 대한 판매 및 판촉을 구성합니다. |
