---
title: Realpath 캐시 크기
description: 권장 설정을 사용하도록 PHP readlpath 캐시 구성을 업데이트하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Realpath 캐시 구성 모범 사례

Realpath 캐시는 매번 조회하는 대신 참조된 파일 이름의 실제 파일 시스템 경로를 캐시합니다. 다양한 파일 함수가 수행되거나 파일이 필요하고 상대 경로를 사용할 때마다 PHP는 해당 파일이 실제로 존재하는 위치를 조회해야 합니다.

Commerce 성능을 향상시키려면 다음 권장 설정을 사용하여 `php.ini` 파일에서 `realpath_cache` 설정을 구성하십시오.

- 캐시 크기를 10MB(`realpath_cache_size=10M`)로 설정합니다.
- TTL(Time to Live)을 7,200초(`realpath_cache_ttl=7200`)로 설정합니다.

구성 지침은 [PHP 옵션을 설정하는 방법](../../../installation/prerequisites/php-settings.md#how-to-set-php-options)을 참조하십시오.

## 영향을 받는 제품 및 버전

- Adobe Commerce 온-프레미스, 모든 버전 2.3.x 이상
- 클라우드 인프라의 Adobe Commerce, 모든 버전 2.3.x 이상

## 성능에 영향을 미칠 수 있음

Realpath 캐시 구성 값이 너무 낮거나 너무 높으면 캐시 생성 중에 추가 오버헤드가 추가되어 성능이 저하됩니다.

## 추가 정보

- [온-프레미스: PHP 설정](../../../performance/software.md#php-settings)
- 클라우드 인프라의 경우:
  - [데이터베이스 모범 사례](database-on-cloud.md)
  - [Magento Commerce Cloud의 가장 일반적인 데이터베이스 문제](../maintenance/resolve-database-performance-issues.md)
- [인덱서 &quot;일정에 따라 업데이트&quot;는 Magento 성능을 최적화합니다.](../maintenance/indexer-configuration.md)
