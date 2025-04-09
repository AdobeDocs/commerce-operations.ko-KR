---
title: 엔터프라이즈 참조 아키텍처
description: Adobe Systems의 최신 컴포저블 커머스 기술을 사용하여 Adobe Systems Commerce를 구현하는 방법에 대해 알아보십시오.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Systems Commerce 엔터프라이즈 참조 아키텍처

Adobe Systems Commerce는 비즈니스 결과를 드라이브 탁월한 경험을 창출하기 위해 기술적 유연성과 사용 편의성을 고유하게 결합한 경험 주도 플랫폼입니다.

상거래는 성능, 규모 및 보안에 대한 기업의 요구 사항을 충족하도록 발전해 왔습니다. Adobe Systems의 최신 컴포저블 커머스 솔루션을 사용하는 현대적인 구현 접근 방식을 채택하는 것은 엔터프라이즈 비즈니스의 성공에 중요 있습니다. 이 페이지에서는 최신 상거래 구현 접근 방식을 기술적으로 자세히 설명합니다.

다음 아키텍처 다이어그램은 Adobe Systems Commerce와 모든 Adobe Experience Cloud 솔루션 간의 데이터 흐름을 보여 줍니다.

![Adobe Systems Commerce와 Experience Cloud 솔루션의 연결 방법을 보여주는 아키텍처 다이어그램](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>다이어그램에 표시된 상위 수준 데이터 흐름은 대부분의 엔터프라이즈 구현에서 일관됩니다. 구현을 고유하게 만들 수 있는 주요 구성 요소는 카탈로그를 만드는 방법입니다(특히 B2B의 경우). 카탈로그 아키텍처를 Commerce 웹 API에 [신중하게 매핑해야 합니다](https://developer.adobe.com/commerce/webapi/get-started/).

## 클라우드 기반

[Adobe Systems Commerce on 클라우드 인프라](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) 는 Commerce 구현의 기반입니다. 클라우드 기본 환경에서 Commerce 애플리케이션을 구축, 배포, 모니터링 및 관리하기 위한 셀프 서비스 접근 방식을 갖춘 안전한](../../security-and-compliance/shared-responsibility.md) 자동 호스팅 플랫폼을 제공합니다[.

다음 클라우드 기반 기술 세부 정보를 참조하십시오.

- [**확장된 아키텍처**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) - 안정적이고 예측 가능한 성능을 유지하기 위해 자동으로 조정된 용량
- [**다중 환경**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - PHP, MySQL(MariaDB), Redis, RabbitMQ 및 지원되는 검색 엔진 기술로 사전 프로비저닝되어 사이트를 개발, 테스트 및 배포
- [**구성 관리**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) - 사용자 지정 가능한 환경 구성 파일 및 CLI(명령줄 인터페이스)를 통해 애플리케이션 설정, 경로, 빌드 및 배포 작업, 알림을 관리할 수 있습니다.
- [**Git 기반 작업 과정**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) - 신속한 개발과 지속적인 배포을 위해 코드 변경 사항을 푸시한 후 자동으로 빌드 및 배포
- [**기본 제공 관찰 가능성**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) - 여러 소스의 로그 데이터를 결합하여 사이트의 성능을 관리하고 문제를 진단하는 데 도움이 되는 도구
- [**포괄적인 API 적용 범위**](https://developer.adobe.com/commerce/webapi/get-started/)—[핵심 Commerce 애플리케이션 서드파티 시스템과 통합하고 Commerce 기능을 확장하기 위한 GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) 및 [REST](https://developer.adobe.com/commerce/webapi/rest) API

## Experience Cloud 통합

Adobe Systems Commerce는 모든 Experience Cloud 솔루션과 통합되어 개인화된 커머스 경험을 대규모](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu)로 제공합니다[.

[Data Connection](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview) 은 쇼핑객의 구매 행동에 대한 통찰력을 제공하므로 다른 Adobe Systems Digital Experience 제품을 사용하여 모든 채널에서 개인화된 쇼핑 경험을 만들 수 있습니다.

>[!NOTE]
>
>자세한 내용은 다음 보고서를 참조하십시오.
>
>- [Digital Experience 블루프린트를 참조하십시오](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) .
>- 고객 경험](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization) 개인화를 참조하십시오[.


## 서드파티 시스템과의 통합

Adobe Systems 는 핵심 상거래 기능을 확장하고 상거래를 서드파티 시스템(예: CRM, ERPS 및 PIMS)과 통합하는 애플리케이션을 빌드 할 수 있는 포괄적인 확장 지점과 도구를 개발자에게 제공합니다. 이러한 도구는 다음과 같은 방법으로 플랫폼의 총 소유 비용을 줄입니다.

- **확장성** - 애플리케이션을 핵심 소프트웨어와 별도로 확장할 수 있으므로 효율성을 높이고 업그레이드를 단순화할 수 있습니다.
- **격리** – 격리된 환경은 개발자가 핵심 릴리스에 의존하지 않고 재량에 따라 확장을 업그레이드하거나 수정할 수 있음을 의미합니다.
- **기술 독립성** – 개발자는 필요에 맞는 기술 스택과 코딩 언어를 선택할 수 있습니다.

Adobe Systems 에서는 통합 및 사용자 지정 구축을 위해 다음과 같은 개발자 도구를 제공합니다.

- [**API Mesh for Adobe Systems Developer 앱 빌더**](https://developer.adobe.com/graphql-mesh-gateway/) - 여러 API, GraphQL, REST 및 기타 소스를 쿼리 가능한 단일 GraphQL 엔드포인트로 조정하고 결합합니다.
- [**앱 Builder**](https://developer.adobe.com/app-builder/docs/overview/) - Commerce 기능을 확장하고 서드파티 솔루션을 통합 대상하는 안전하고 확장 가능한 웹 애플리케이션을 구축하고 배포.
- [**이벤트**](https://developer.adobe.com/commerce/extensibility/events/) - 사용자 지정 이벤트 트리거를 사용하여 다른 확장 가능한 개발 도구와 상호 작용합니다.
- [**웹훅**](https://developer.adobe.com/commerce/extensibility/webhooks/): 웹훅을 사용하여 커머스와 서드파티 시스템 간의 상호작용을 자동으로 트리거합니다.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - 판매자를 위한 새로운 페이지와 기능으로 Commerce Admin을 사용자 지정하고 개선합니다.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/) - 참조 통합, 온보딩 스크립트 및 표준화된 아키텍처를 통해 백오피스 통합을 가속화합니다.

>[!NOTE]
>
>최신 접근 방식: Adobe Systems Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility)의 효과적인 확장성을 참조하십시오[.

## 상점 서비스

Adobe Systems 는 주요 비즈니스 목표를 지원하는 데 도움이 되는 다양하고 지능적이고 구성 가능한 머천다이징 서비스를 제공합니다. 또한 이러한 서비스는 대규모 성능을 최적화하는 데 중요 API를 제공합니다.

- [라이브 Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview)—이 AI 기반 검색 도구 통해 쇼핑객에게 더 스마트하고 빠르며 관련성 높은 결과를 제공합니다.
- [제품 추천](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview) - 쇼핑객 행동, 인기 트렌드, 제품 유사성 등을 기반으로 AI 기반 추천을 추가합니다.
- [카탈로그 서비스](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview) - 고객에게 최적화된 제품 경험 경험을 제공하는 동시에 성능을 높이고 확장성을 개선하며 전환율을 높일 수 있습니다.
- [결제 서비스](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview) - 관심도 무료 할부, 결제 처리, 주문 및 송장에 대한 단일 보기를 포함한 다양한 결제 방법을 제공하여 고객 만족도를 높입니다.

## 헤드리스 매장

헤드리스 상거래는 API 우선 상거래입니다. Adobe Commerce은 GraphQL API 계층을 통해 모든 상거래 서비스 및 데이터를 제공하는 분리된 아키텍처를 통해 완전히 headless입니다. 이 아키텍처를 통해 팀은 핵심 애플리케이션과 독립적으로 전면을 개발할 수 있으므로 새로운 기술을 통해 새로운 접점을 신속하게 구축하고 테스트할 수 있는 민첩성을 제공합니다.

Adobe은 문서 기반 작성, 성능 우선 아키텍처 및 즉시 사용 가능한 기본 실험을 통해 [Edge Delivery Services](https://www.aem.live/home)에서 제공하는 것과 동일한 이점과 기능을 포함하는 최신 headless 상점 전면 기술을 제공합니다. 이 서비스에서는 Adobe Systems Commerce [상점 서비스의](#storefront-services) 규모와 성능, 드롭인 구성 요소의](https://experienceleague.adobe.com/developer/commerce/storefront/) 유연성과 편리[함을 활용하여 상거래 기능을 제공합니다.

