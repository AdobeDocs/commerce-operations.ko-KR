---
title: 제품 가용성
description: 현재 지원되는 Adobe Commerce 기능에 대해 알아보고 특정 Adobe Commerce 릴리스와의 호환성을 확인합니다.
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: 846d20fb0c973e4e7eccc41cfe26f877fffc561b
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 15%

---

# 제품 가용성

다음 표에서는 Adobe Commerce 소프트웨어 가용성의 상태와 이를 얻을 수 있는 위치, 특히 기존 Adobe Commerce Composer 패키지 외부에서 사용할 수 있는 소프트웨어에 대해 설명합니다.

서비스 및 확장은 제품 릴리스 당시 Commerce의 최신 릴리스 버전에서 테스트되었습니다.

지원되는 버전은 Adobe에서 완전히 테스트되었습니다. 고객 지원 센터를 통해 지원되는 버전을 사용할 수 있습니다. 이전 버전은 제대로 작동할 수 있지만 공식적으로 지원되지 않습니다.

## Adobe 작성 확장

이러한 Adobe Commerce 확장은 핵심 Adobe Commerce 코드베이스에서 분리되었습니다. 이를 통해 Adobe은 새 기능에 대한 이전 액세스와 비교하여 약간의 위험을 기꺼이 수락하는 판매자에게 이러한 확장의 반복을 더 빨리 릴리스할 수 있습니다.

다음 표는 Adobe Commerce 버전을 기준으로 각 확장에 대한 버전 지원을 보여 줍니다.

| **Adobe Commerce 버전** | 2.4.7-베타1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                          |
|----------------------------------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Adobe Commerce에 대한 이벤트 Adobe I/O_ | 1.2.2 | 1.2.2 | 1.2.2 | 1.2.2 | - | [작성기](https://developer.adobe.com/commerce/events/get-started/installation/) <br/>[릴리스 정보](https://developer.adobe.com/commerce/events/get-started/release-notes/) |
| _B2B_ | 1.4.0+ | 1.3.5+ | 1.3.4 | 1.3.3 | 1.3.2 | [작성기](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _채널 관리자_ | - | 2.0.0 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [마켓플레이스](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _Amazon Sales Channel_ | - | 4.1.0+ | 4.3.0+ | 4.3.0+ | 4.3.0+ | [마켓플레이스](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _Experience Platform 커넥터_ | 3.0.0-Beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | 1.0.0+ | [마켓플레이스](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _페이지 빌더_ | - | - | 1.7.2 | 1.7.1 | - | [사용 안내서](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |              |
| _Adobe Commerce용 스토어 이행_ | - | 1.5.0 | 1.2.0+ | 1.2.0+ | 1.2.0+ | [마켓플레이스](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |

## 상거래 서비스

[상거래 서비스](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) 는 상거래 인스턴스와 함께 강력한 기능과 빠른 응답 시간을 제공하는 Adobe 호스팅 기능 세트입니다.

상인은 가장 최신 버전의 서비스를 사용하여 가장 높은 안정성과 기능을 보장하는 것이 좋습니다. 이 설명서에서는 현재 릴리스된 버전에 대해 설명합니다.

* Adobe Commerce 서비스는 현재 Commerce 2.4.4 이상과 호환됩니다. 가맹점은 최신 버전의 서비스를 사용하는 것이 좋다.
* 서비스는 이전 버전의 Commerce 2.4.x와 호환되는 것으로 간주되지만 공식적으로 지원되지 않습니다.
* 서비스는 제품 Recommendations 3.3.7 및 이전 버전을 제외하고 Commerce 2.3.x와 호환되지 않습니다.

다음 표는 Adobe Commerce 버전을 기준으로 각 서비스에 대한 버전 지원을 보여 줍니다.

| **Adobe Commerce 버전** | 2.4.7-베타1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                                |
|--------------------------------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Adobe Commerce용 카탈로그 서비스_ | 1.1.2 | 1.1.2 | 1.1.2 | 1.1.2 | - | [개요](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _라이브 검색_ | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | - | [마켓플레이스](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _결제 서비스_ | 2.1.1 | 2.1.1 | 2.1.1 | 2.1.1 | - | [마켓플레이스](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/release-notes.html) |
| _제품 Recommendations_ | 5.0 | 5.0 | 5.0 | 5.0 | - | [마켓플레이스](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _빠른 체크아웃_ | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | 1.2.0+ | [마켓플레이스](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [릴리스 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
