---
title: OPcache 메모리 크기에 대한 우수 사례
description: Adobe Commerce 프로젝트에서 특정 OPcache 메모리 사용량 설정에 의한 성능 저하를 방지하는 방법을 설명합니다.
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Adobe Commerce의 OPcache 메모리 크기에 대한 우수 사례

Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.3.x의 경우 다음을 설정하는 것이 좋습니다. `opcache.memory_consumption` 성능 저하를 방지하려면 최소 2GB를 사용해야 합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.3.x
* PHP 7.0 이상

## 메모리 구성

최소 할당 **2GB** 의 메모리 [OPcache PHP 모듈](https://www.php.net/manual/en/book.opcache.php). OPcache 모듈은 `php.ini` 파일. 2048MB의 메모리를 할당하려면 `opcache.memory_consumption = 2048`.

## 추가 정보

* [성능 모범 사례 - PHP 설정](../../../performance/software.md#php-settings)
* [PHP 옵션 구성](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](database-on-cloud.md)
* [클라우드 인프라의 Adobe Commerce에서 가장 일반적인 데이터베이스 문제](../maintenance/resolve-database-performance-issues.md)
* [인덱서 &quot;일정에 따라 업데이트&quot;는 Adobe Commerce 성능을 최적화합니다.](../maintenance/indexer-configuration.md)
