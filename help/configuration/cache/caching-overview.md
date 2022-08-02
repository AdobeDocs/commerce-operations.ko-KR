---
title: 캐싱 구성
description: Adobe Commerce 및 Magento Open Source 애플리케이션의 캐시 메커니즘 캐싱 및 구성 방법에 대해 알아봅니다.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 캐싱 구성

[!DNL Commerce] 기본 파일 시스템 캐싱에 대한 대체 요소를 구성할 수 있습니다. 이 안내서에서는 이러한 대체 요소 중 일부를 설명합니다. 즉,

- 다음을 설정합니다 [캐시](https://glossary.magento.com/cache) 의 메커니즘 [!DNL Commerce] 구성:

   - [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [레디스](config-redis.md)
   - 파일 시스템(기본값): 기본 파일 시스템 캐싱을 사용하려면 구성이 필요하지 않습니다.

- 설정 [바니쉬](config-varnish.md) 수정하지 않고 [!DNL Commerce] 구성.

## 캐싱 용어

[!DNL Commerce] 에서는 다음 캐싱 용어를 사용합니다.

- **프론트엔드**—에 의해 구현된 캐시 스토리지에 대한 인터페이스 또는 게이트웨이와 유사합니다. [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **캐시 유형**- 와 함께 제공되는 유형 중 하나일 수 있습니다. [!DNL Commerce] 또는 [직접 만들기](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **백엔드**- 세부 정보를 지정합니다 [캐시 저장소](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), 구현됨 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **2수준 백엔드**—캐시 레코드를 두 개의 백엔드에 저장합니다. 더 빠른 것과 더 느린 것.

   >[!INFO]
   >
   >두 수준의 백엔드 캐시 구성이 이 안내서의 범위를 벗어납니다.

## 구성 옵션

- 제공된 수정 `default` 캐시 프론트엔드—

   만 수정합니다 `<magento_root>/app/etc/di.xml` 파일, 상거래 애플리케이션의 전역 [종속성 주입](https://glossary.magento.com/dependency-injection) 구성.

- 고유한 사용자 지정 캐시 프론트엔드 구성 -

   만 수정합니다 `<magento_root>/app/etc/env.php` 파일에서 해당 구성을 재정의하므로 `di.xml` 파일.

>[!TIP]
>
>Varnish는 [!DNL Commerce] 구성. 자세한 내용은 [Varnish 구성 및 사용](config-varnish.md).
