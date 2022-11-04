---
title: Realpath 캐시 크기
description: 권장 설정을 사용하도록 PHP readlpath 캐시 구성을 업데이트하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Realpath 캐시 구성 우수 사례

Realpath Cache는 매번 찾지 않고 참조된 파일 이름의 실제 파일 시스템 경로를 캐시합니다. 다양한 파일 기능이 수행되거나 파일이 필요하고 상대 경로를 사용할 때마다 PHP는 해당 파일이 실제로 존재하는 위치를 조회해야 합니다.

상거래 성능을 향상하려면 다음 권장 설정을 사용하여 `realpath_cache` 의 설정 `php.ini` 파일:

- 캐시 크기를 10MB( )로 설정합니다.`realpath cache_size=10M`)
- ttl(live)을 7200초( )로 설정`realpath_cache_ttl=7200`)

구성 지침은 [PHP 옵션을 설정하는 방법](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## 영향을 받는 제품 및 버전

- Adobe Commerce 온-프레미스, 모든 버전 2.3.x 이상
- 클라우드 인프라, 모든 버전 2.3.x 이상의 Adobe Commerce

## 잠재적인 성능 영향

Realpath 캐시 구성 값이 너무 낮거나 너무 높으면 캐시 생성 중에 오버헤드가 추가되어 성능이 저하됩니다.

## 추가 정보

- [온-프레미스: PHP 설정](../../../performance/software.md#php-settings)
- 클라우드 인프라:
   - [데이터베이스 우수 사례](database-on-cloud.md)
   - [Magento Commerce Cloud의 가장 일반적인 데이터베이스 문제](../maintenance/resolve-database-performance-issues.md)
- [인덱서 &quot;일정에 따라 업데이트&quot;는 Magento 성능을 최적화합니다](../maintenance/indexer-configuration.md)

