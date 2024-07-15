---
title: 캐시 옵션
description: 낮은 수준의 캐시 스토리지에 대한 액세스를 구성합니다.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# 낮은 수준의 캐시 옵션

Commerce 애플리케이션은 낮은 수준의 캐시 프론트엔드 및 백엔드를 사용하여 캐시 스토리지에 대한 액세스를 제공합니다.

## 낮은 수준의 프론트엔드 캐시

Commerce은 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 프런트 엔드 캐시를 구현하여 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)을(를) 확장합니다.

## 낮은 수준 백엔드 캐시

일반적으로 Commerce 애플리케이션은 [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)이(가) 지원하는 모든 백엔드 캐시에서 작동합니다. 그러나 이 안내서에서는 다음 낮은 수준 백엔드 캐시만 다룹니다.

- [레디스](config-redis.md)
- [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 파일 시스템(기본값): 파일 시스템 캐싱을 사용하는 데 필요한 구성이 없습니다.

[바니시](config-varnish.md)에서는 낮은 수준의 캐시 백엔드를 설정할 필요가 없습니다.
