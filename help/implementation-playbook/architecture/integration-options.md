---
title: Adobe 상거래 통합 옵션
description: Explore your options for integrating other systems with your Adobe Commerce implementation.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# 일반적인 통합 지점 및 데이터 흐름

통합과 데이터 흐름에 대한 두 가지 주요 접근 방법이 있는데, 이 접근 방식은 매우 유사하지만 한 가지 주요 차이점이 있습니다.

## 모놀리식

The following diagram describes a monolithic approach that uses Adobe Commerce as both the backend system and storefront application:

![Adobe 상거래 모노리스 다이어그램](../../assets/playbooks/integration-monolith.svg)

## Headless

The following diagram describes a headless approach that uses Adobe Commerce as the backend systenm integrated with a DXP/CMS/custom application as the storefront application:

![Adobe Commerce headless diagram](../../assets/playbooks/integration-headless.svg)

The only difference between the monolithic and headless approach is storefront integration, which impacts the user experience for customers. 모놀리시는 Adobe 상거래 상점 프론트를 직접 사용하여 서드파티 서비스와 통합하지만, 헤드리스는 자체 상점 전방에 의존하여 동일한 서비스와 사용자 지정 및 통합합니다. 결제 및 SSO(Single Sign-On)와 같은 일부 서비스에는 통합 흐름을 완료하려면 storefront 및 Adobe Commerce 사용자 지정이 모두 필요합니다.

## 타사 시스템

Some popular services already have great extensions to support Adobe Commerce or popular storefront solutions, such as PWA Studio, Adobe Experience Manager, and Vue Storefront, which can be found from their extension marketplace or from related third-party websites. Even if there is no existing extension, the effort to implement the integration between Adobe Commerce and other headless storefronts are similar. All third-party services usually have documents to explain how to integrate with them. Those service are just some examples; various countries and markets may have different choices.

## Enterprise integrations

For enterprise systems integrations, which are also usually called backend integrations, there is an impact on the business data flow. 다양한 비즈니스 유형과 요구 사항에 따라 이미 소개된 세 가지 서로 다른 통합 옵션을 사용할 수 있습니다.

Product-mandatory data like SKUs, inventory, and base prices usually come from ERPs, while sales prices are usually managed by each sales channel (for example, Adobe Commerce) or CPQ (B2B or private sales). Because product-mandatory data (except inventory) does not change very often, best practice is to use scheduled batch updates through the REST API or bulk-file import. Inventory의 경우, Best Practice는 Over-Sales를 방지하기 위해 다른 판매 채널과 공유되는 제품 인벤토리에 대해 일별로 전체 업데이트를 수행하는 것입니다. Additionally, have incremental changes from your ERP scheduled within 24 hours.

제품 카탈로그, 메타데이터 및 마케팅 콘텐츠는 각 판매 채널(예: Adobe 상거래)이나 중앙 PIM에서 별도로 관리할 수 있습니다. As metadata is also not changed frequently, best practice is to use scheduled batch updates through the REST API or bulk-file import.

주문 데이터에는 일반적으로 중앙 집중식 OMS 및 WMS 시스템에서 관리되는 주문, 견적(B2B), 배송, 반품 및 교환 데이터가 포함됩니다. Order data should be synchronized as soon as possible, so REST API is usually the best option. For better performance, consider reducing the number of API calls. 주문 상태, 선적, 반품 및 교환 데이터의 경우 REST 배치 업데이트 API 예약을 시간 또는 분 단위로 고려하십시오.

B2B data is usually managed from a centralized CRM. A real-time API is used to verify existing customers and create new customers. For B2B, it might require introducing more APIs to synchronize different company employee, group, and price list between Adobe Commerce and your CRM or CPQ.

전자 메일 마케팅 및 비즈니스 데이터 분석을 위한 비즈니스 인텔리전스를 위한 eDM과 같은 다른 시스템 통합도 있습니다. 이러한 통합은 일반적으로 REST API 또는 파일 내보내기/가져오기를 통해 수행되며, 일반적으로 기존 확장에서 지원합니다.
