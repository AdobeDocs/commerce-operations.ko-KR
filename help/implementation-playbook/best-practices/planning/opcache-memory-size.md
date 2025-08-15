---
title: OPcache 메모리 크기에 대한 우수 사례
description: Adobe Commerce 프로젝트에서 특정 OPcache 메모리 사용량 설정에 의한 성능 저하를 방지하는 방법을 설명합니다.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Adobe Commerce의 OPcache 메모리 크기에 대한 우수 사례

Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.3.x의 경우 성능 저하를 방지하려면 `opcache.memory_consumption`을(를) 2GB 이상으로 설정하는 것이 좋습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure Pro 플랜 아키텍처 2.3.x
* PHP 7.0 이상

## 메모리 구성

**OPcache PHP 모듈**&#x200B;에 최소 [2GB](https://www.php.net/manual/en/book.opcache.php)의 메모리를 할당하십시오. OPcache 모듈이 `php.ini` 파일에 구성되어 있습니다. 2048MB의 메모리를 할당하려면 `opcache.memory_consumption = 2048`을(를) 설정합니다.

## 추가 정보

* [성능 모범 사례 - PHP 설정](../../../performance/software.md#php-settings)
* [PHP 옵션 구성](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](database-on-cloud.md)
* [클라우드 인프라의 Adobe Commerce에서 가장 일반적인 데이터베이스 문제](../maintenance/resolve-database-performance-issues.md)
* [인덱서 &quot;일정에 따라 업데이트&quot;는 Adobe Commerce 성능을 최적화합니다.](../maintenance/indexer-configuration.md)
