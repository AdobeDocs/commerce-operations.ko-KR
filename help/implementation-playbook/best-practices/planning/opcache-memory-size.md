---
title: OPcache 메모리 크기에 대한 우수 사례
description: Adobe Commerce 프로젝트에서 OPcache 메모리 사용량에 대한 특정 설정으로 성능 저하를 방지하는 방법에 대해 설명합니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Adobe Commerce의 OPcache 메모리 크기에 대한 우수 사례

클라우드 인프라 Pro 계획 아키텍처 2.3.x의 경우 다음을 설정하는 것이 좋습니다 `opcache.memory_consumption` 최소 2GB로 설정하면 성능이 저하되지 않습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure pro plan architecture 2.3.x
* PHP 7.0 이상

## 메모리 구성

적어도 할당 **2GB** 메모리 [OPcache PHP 모듈](https://www.php.net/manual/en/book.opcache.php). OPcache 모듈은 `php.ini` 파일. 2048MB의 메모리를 할당하려면 을 설정합니다. `opcache.memory_consumption = 2048`.

## 추가 정보

* [성능 우수 사례 - PHP 설정](../../../performance/software.md#php-settings)
* [PHP 옵션 구성](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [클라우드 인프라 기반의 Adobe Commerce을 위한 데이터베이스 우수 사례](database-on-cloud.md)
* [클라우드 인프라에서 Adobe Commerce의 가장 일반적인 데이터베이스 문제](../maintenance/resolve-database-performance-issues.md)
* [인덱서 &quot;일정에 따라 업데이트&quot;는 Adobe Commerce 성능을 최적화합니다](../maintenance/indexer-configuration.md)
