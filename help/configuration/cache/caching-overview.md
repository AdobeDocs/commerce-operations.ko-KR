---
title: 캐싱 구성
description: 캐싱과 Adobe Commerce 애플리케이션에 대한 캐시 메커니즘을 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 캐싱 구성

[!DNL Commerce]을(를) 사용하면 기본 파일 시스템 캐싱에 대한 대체 요소를 구성할 수 있습니다. 이 안내서에서는 이러한 대체 요소 중 일부에 대해 설명합니다. 즉,

- [!DNL Commerce] 구성에서 다음 캐시 메커니즘을 설정합니다.

   - [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [레디스](config-redis.md)
   - 파일 시스템(기본값): 기본 파일 시스템 캐싱을 사용하기 위해 구성이 필요하지 않습니다.

- [ 구성을 수정하지 않고 ](config-varnish.md)Varnish[!DNL Commerce]을 설정합니다.

## 캐싱 용어

[!DNL Commerce]은(는) 다음 캐싱 용어를 사용합니다.

- **Frontend**—캐시 저장소에 대한 인터페이스 또는 게이트웨이와 비슷하며 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)에서 구현되었습니다.
- **캐시 형식**—[!DNL Commerce]과(와) 함께 제공된 형식 중 하나일 수도 있고 [직접 만들 수도 있습니다](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **백엔드**—[Magento\Framework\Cache\Backend](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)에서 구현한 [캐시 저장소](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)에 대한 세부 정보를 지정합니다.
- **두 수준 백엔드** - 캐시 레코드를 더 빠른 백엔드와 더 느린 백엔드의 두 백엔드에 저장합니다.

  >[!INFO]
  >
  >2수준 백엔드 캐시 구성은 이 안내서의 범위를 벗어납니다.

## 구성 옵션

- 제공된 `default` 캐시 프런트 엔드를 수정하는 중—

  Commerce 응용 프로그램의 전역 종속성 삽입 구성인 `<magento_root>/app/etc/di.xml` 파일만 수정합니다.

- 사용자 지정 캐시 프론트엔드 구성—

  `<magento_root>/app/etc/env.php` 파일의 해당 구성을 무시하므로 `di.xml` 파일만 수정합니다.

>[!TIP]
>
>[!DNL Commerce] 구성을 변경할 필요가 없습니다. [바니시 구성 및 사용](config-varnish.md)을 참조하세요.
