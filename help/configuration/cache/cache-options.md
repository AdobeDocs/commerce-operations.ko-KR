---
title: 캐시 옵션
description: 낮은 수준의 캐시 스토리지에 대한 액세스를 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 낮은 수준의 캐시 옵션

상거래 응용 프로그램은 낮은 수준의 캐시 프론트엔드 및 백엔드를 사용하여 캐시 저장소에 대한 액세스를 제공합니다.

## 낮은 수준의 프런트 엔드 캐시

상거래 확장 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 구현으로 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 프런트 엔드 캐시

## 낮은 수준의 백엔드 캐시

일반적으로 상거래 애플리케이션은 [Zend_Cache 뒷면](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 을 지원합니다. 그러나 이 안내서에서는 다음의 낮은 수준의 백엔드 캐시만 다룹니다.

- [레디스](config-redis.md)
- [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 파일 시스템(기본값): 파일 시스템 캐싱을 사용하는 경우에는 구성이 필요하지 않습니다.

[바니쉬](config-varnish.md) 은 낮은 수준의 캐시 백엔드를 설정할 필요가 없습니다.
