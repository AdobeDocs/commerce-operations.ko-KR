---
title: 캐싱 구성
description: 캐싱과 Adobe Commerce 및 Magento Open Source 애플리케이션에 대한 캐시 메커니즘을 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 캐싱 구성

[!DNL Commerce] 기본 파일 시스템 캐싱에 대한 대체 요소를 구성할 수 있습니다. 이 안내서에서는 이러한 대체 요소 중 일부에 대해 설명합니다. 즉,

- 에서 다음 캐시 메커니즘을 설정합니다. [!DNL Commerce] 구성:

   - [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [레디스](config-redis.md)
   - 파일 시스템(기본값): 기본 파일 시스템 캐싱을 사용하기 위해 구성이 필요하지 않습니다.

- 다음을 설정합니다. [니스](config-varnish.md) 을 수정하지 않고 [!DNL Commerce] 구성.

## 캐싱 용어

[!DNL Commerce] 는 다음 캐싱 용어를 사용합니다.

- **프론트엔드**—다음을 통해 구현된 캐시 스토리지에 대한 인터페이스 또는 게이트웨이와 유사 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **캐시 유형**- 와 함께 제공되는 유형 중 하나일 수 있습니다. [!DNL Commerce] 또는 다음을 수행할 수 있습니다 [자신만의 고유한 만들기](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **백엔드**- 다음에 대한 세부 사항을 지정합니다. [캐시 스토리지](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), 구현 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **2단계 백엔드**- 캐시 레코드를 더 빠른 레코드와 더 느린 백엔드, 이렇게 두 개의 백엔드에 저장합니다.

  >[!INFO]
  >
  >2수준 백엔드 캐시 구성은 이 안내서의 범위를 벗어납니다.

## 구성 옵션

- 제공된 항목 수정 `default` 캐시 프론트엔드—

  다음 항목만 수정합니다. `<magento_root>/app/etc/di.xml` 상거래 애플리케이션의 전역 종속성 삽입 구성입니다.

- 사용자 지정 캐시 프론트엔드 구성—

  다음 항목만 수정합니다. `<magento_root>/app/etc/env.php` 이 파일은 의 동일한 구성을 무시하므로 `di.xml` 파일.

>[!TIP]
>
>바니시는 다음을 변경할 필요가 없습니다. [!DNL Commerce] 구성. 다음을 참조하십시오 [바니시 구성 및 사용](config-varnish.md).
