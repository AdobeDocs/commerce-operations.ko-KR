---
title: 엔터프라이즈 참조 아키텍처
description: Adobe의 최신 컴포저블 상거래 기술을 사용하여 Adobe Commerce을 구현하는 방법에 대해 알아봅니다.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 581a7dbcc19c31df80e03cb9f321a6adb5fa1a73
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce 엔터프라이즈 참조 아키텍처

Adobe Commerce은 기술 유연성과 사용 편의성을 고유하게 조화시킨 경험 중심의 플랫폼으로, 모든 것을 비즈니스 결과를 이끄는 탁월한 경험을 창출하기 위해 제공합니다.

Commerce은 성능, 규모 및 보안에 대한 엔터프라이즈 요구 사항을 충족하도록 발전해 왔습니다. Adobe의 최신 컴포저블 상거래 솔루션을 사용하는 최신 구현 접근 방식을 채택하는 것은 기업 비즈니스의 성공에 매우 중요합니다. 이 페이지에서는 최신 Commerce 구현 접근 방식에 대해 기술적인 세부 정보를 제공합니다.

다음 아키텍처 다이어그램은 Adobe Commerce과 모든 Adobe Experience Cloud 솔루션 간의 데이터 흐름을 보여 줍니다.

![Adobe Commerce이 Experience Cloud 솔루션에 연결하는 방법을 보여 주는 아키텍처 다이어그램](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>다이어그램에 표시된 높은 수준의 데이터 흐름은 대부분의 엔터프라이즈 구현에서 일관됩니다. 구현을 고유하게 만들 수 있는 주요 구성 요소는 카탈로그를 만드는 방법입니다(특히 B2B의 경우). 카탈로그 아키텍처를 [Commerce 웹 API](https://developer.adobe.com/commerce/webapi/get-started/)에 매핑해야 합니다.

## 클라우드 기반

[클라우드 인프라의 Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)은(는) Commerce 구현의 기반입니다. 클라우드 기반 환경에서 Commerce 애플리케이션을 구축, 배포, 모니터링 및 관리하는 셀프서비스 접근 방식을 통해 [보안](../../security-and-compliance/shared-responsibility.md) 자동 호스팅 플랫폼을 제공합니다.

다음 cloud foundation 기술 세부 사항을 참조하십시오.

- [**확장 아키텍처**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—안정적이고 예측 가능한 성능을 유지하기 위해 자동으로 용량이 조정되었습니다.
- [**여러 환경**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—PHP, MySQL(MariaDB), Redis, RabbitMQ 및 지원되는 검색 엔진 기술로 사전 프로비저닝되어 사이트를 개발, 테스트 및 배포합니다.
- [**구성 관리**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—응용 프로그램 설정, 경로, 빌드 및 배포 작업, 알림을 관리할 수 있도록 사용자 지정 가능한 환경 구성 파일 및 CLI(명령줄 인터페이스)입니다.
- [**Git 기반 워크플로**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) - 신속한 개발 및 지속적인 배포를 위해 코드 변경 사항을 푸시한 후 자동으로 빌드하고 배포합니다.
- [**기본 제공 가시성**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)—여러 소스의 로그 데이터를 결합하여 사이트 성능을 관리하고 문제를 진단하는 데 도움이 되는 도구입니다.
- 핵심 Commerce 애플리케이션을 타사 시스템과 통합하고 Commerce 기능을 확장하기 위한 [**포괄적인 API 적용 범위**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) 및 [REST](https://developer.adobe.com/commerce/webapi/rest) API

## Experience Cloud과 통합

Adobe Commerce은 모든 Experience Cloud 솔루션과 통합되어 [규모에 맞는 개인화된 상거래 경험을](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu)제공합니다.

[데이터 연결](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview)은(는) 다른 Adobe Digital Experience 제품과 함께 모든 채널에서 개인화된 쇼핑 경험을 만들 수 있도록 쇼핑객의 구매 행동에 대한 통찰력을 잠금 해제합니다.

>[!NOTE]
>
>자세한 내용은 다음 리소스를 참조하십시오.
>
>- 자세한 내용은 [Digital Experience 블루프린트](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview)를 참조하십시오.
>- [고객 경험 개인화](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization)를 참조하십시오.


## 서드파티 시스템과의 통합

Adobe은 개발자에게 핵심 Commerce 기능을 확장하고 Commerce을 타사 시스템(예: CRM, ERPS 및 PIMS)과 통합하는 애플리케이션을 빌드하는 포괄적인 확장 지점 및 도구를 제공합니다. 이러한 도구를 사용하면 다음과 같은 방법으로 플랫폼의 TCO를 절감할 수 있습니다.

- **확장성**—핵심 소프트웨어와 별도로 응용 프로그램을 확장할 수 있으므로 효율성이 향상되고 업그레이드가 간단해집니다.
- **격리**-격리된 환경은 개발자가 코어 릴리스에 의존하지 않고 임의로 확장을 업그레이드하거나 수정할 수 있음을 의미합니다.
- **기술 독립성**-개발자는 필요에 맞는 기술 스택과 코딩 언어를 선택할 수 있습니다.

Adobe은 통합 및 사용자 지정을 빌드하기 위한 다음 개발자 도구를 제공합니다.

- [**Adobe Developer App Builder용 API Mesh**](https://developer.adobe.com/graphql-mesh-gateway/) - 여러 API, GraphQL, REST 및 기타 소스를 하나의 쿼리 가능한 GraphQL 엔드포인트로 조정하고 결합합니다.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) - Commerce 기능을 확장하고 서드파티 솔루션과 통합하는 안전하고 확장 가능한 웹 애플리케이션을 빌드하고 배포합니다.
- [**이벤트**](https://developer.adobe.com/commerce/extensibility/events/)—사용자 지정 이벤트 트리거를 사용하여 다른 확장 가능한 개발 도구와 상호 작용합니다.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) - 웹후크를 사용하여 Commerce과 서드파티 시스템 간의 상호 작용을 자동으로 트리거합니다.
- [**관리자 UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)—판매자를 위한 새 페이지 및 기능을 사용하여 Commerce 관리자를 사용자 지정하고 개선합니다.
- [**통합 시작 키트**](https://developer.adobe.com/commerce/extensibility/starter-kit/) - 참조 통합, 온보딩 스크립트 및 표준화된 아키텍처를 통해 백오피스 통합을 가속화합니다.

>[!NOTE]
>
>[최신 접근 방식: Adobe Commerce의 효과적인 확장성](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility)을 참조하십시오.

## Storefront 서비스

Adobe은 주요 비즈니스 목표를 지원하는 데 도움이 되는 지능적이고 컴포저블 머천다이징 서비스의 풍부한 세트를 제공합니다. 또한 이러한 서비스는 규모에 맞게 성능을 최적화하는 데 중요한 API를 제공합니다.

- [실시간 검색](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview) - 이 AI 기반 검색 도구를 사용하여 쇼핑객에게 보다 스마트하고 빠르며 적절한 결과를 제공합니다.
- [제품 Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) - 구매자 행동, 인기 트렌드, 제품 유사성 등을 기반으로 AI 기반 권장 사항을 추가합니다.
- [카탈로그 서비스](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview) - 성능을 향상시키고, 확장성을 개선하고, 전환을 늘리는 동시에 고객에게 최적화된 제품 경험을 제공합니다.
- [결제 서비스](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)—무이자 결제 할부, 결제 처리, 주문 및 청구서에 대한 단일 보기를 포함한 다양한 결제 방법을 제공하여 고객 만족도를 높입니다.

## 헤드리스 상점

Headless 거래는 API 우선 거래입니다. Adobe Commerce은 GraphQL API 계층을 통해 모든 상거래 서비스 및 데이터를 제공하는 분리된 아키텍처를 통해 완전히 headless입니다. 이 아키텍처를 통해 팀은 핵심 애플리케이션과 독립적으로 전면을 개발할 수 있으므로 새로운 기술을 통해 새로운 접점을 신속하게 구축하고 테스트할 수 있는 민첩성을 제공합니다.

Adobe은 문서 기반 작성, 성능 우선 아키텍처 및 즉시 사용 가능한 기본 실험을 통해 [Edge Delivery Services](https://www.aem.live/home)이(가) 제공하는 것과 동일한 이점 및 기능을 포함하는 최신 headless 상점 전면 기술을 제공합니다. Adobe Commerce [상점 서비스](#storefront-services)의 규모와 성능, [수신 구성 요소](https://experienceleague.adobe.com/developer/commerce/storefront/)의 유연성과 편리성을 활용하여 상거래 기능을 제공합니다.

