---
title: 엔터프라이즈 참조 아키텍처
description: Adobe의 최신 컴포저블 상거래 기술을 사용하여 Adobe Commerce을 구현하는 방법에 대해 알아봅니다.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 8eab688ed98eb1b9fcf4fc25f90fe2bbf99c02d6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Adobe Commerce 엔터프라이즈 참조 아키텍처

Adobe Commerce은 기술 유연성과 사용 편의성을 고유하게 조화시킨 경험 중심의 플랫폼으로, 모든 것을 비즈니스 결과를 이끄는 탁월한 경험을 창출하기 위해 제공합니다.

Commerce는 성능, 규모 및 보안에 대한 엔터프라이즈 요구 사항을 충족하도록 발전해 왔습니다. Adobe의 최신 컴포저블 상거래 솔루션을 사용하는 최신 구현 접근 방식을 채택하는 것은 기업 비즈니스의 성공에 매우 중요합니다. 이 페이지에서는 최신 Commerce 구현 접근 방식을 기술적인 세부 사항으로 설명합니다.

다음 아키텍처 다이어그램은 Adobe Commerce과 모든 Adobe Experience Cloud 솔루션 간의 데이터 흐름을 보여 줍니다.

![Adobe Commerce이 Experience Cloud 솔루션에 연결하는 방법을 보여 주는 아키텍처 다이어그램](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>다이어그램에 표시된 높은 수준의 데이터 흐름은 대부분의 엔터프라이즈 구현에서 일관됩니다. 구현을 고유하게 만들 수 있는 주요 구성 요소는 카탈로그를 만드는 방법입니다(특히 B2B의 경우). 카탈로그 아키텍처를 [Commerce 웹 API](https://developer.adobe.com/commerce/webapi/get-started/).

## 클라우드 기반

[클라우드 인프라의 Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) 는 Commerce 구현의 기반입니다. 다음을 제공합니다. [secure](../../security-and-compliance/shared-responsibility.md) 클라우드 기반 환경에서 Commerce 애플리케이션을 구축, 배포, 모니터링 및 관리하는 셀프서비스 접근 방식을 사용하는 자동화된 호스팅 플랫폼.

다음 cloud foundation 기술 세부 사항을 참조하십시오.

- [**확장 아키텍처**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—안정적이고 예측 가능한 성능을 유지하기 위해 자동으로 용량이 조정됩니다.
- [**여러 환경**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—PHP, MySQL(MariaDB), Redis, RabbitMQ과 지원되는 검색 엔진 기술로 사전 프로비저닝되어 사이트를 개발, 테스트 및 배포합니다.
- [**구성 관리**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—애플리케이션 설정, 경로 지정, 작업 빌드 및 배포, 알림 등을 관리하는 사용자 정의 가능한 환경 구성 파일 및 CLI(명령줄 인터페이스)
- [**Git 기반 워크플로우**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow)—신속한 개발 및 지속적인 배포를 위해 코드 변경 사항을 푸시한 후 자동으로 구축 및 배포
- [**내장된 가시성**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)—여러 소스의 로그 데이터를 결합하여 사이트 성능을 관리하고 문제를 진단하는 데 도움이 되는 도구
- [**포괄적인 API 범위**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) 및 [나머지](https://developer.adobe.com/commerce/webapi/rest) 핵심 Commerce 애플리케이션을 서드파티 시스템과 통합하고 Commerce 기능을 확장하기 위한 API

## Experience Cloud과 통합

Adobe Commerce은 모든 Experience Cloud 솔루션과 통합되어 [규모에 맞게 개인화된 상거래 경험](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[데이터 연결](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) 다른 Adobe Digital Experience 제품과 함께 모든 채널에서 개인화된 쇼핑 경험을 만들 수 있도록 쇼핑객의 구매 행동에 대한 통찰력을 잠금 해제합니다.

>[!NOTE]
>
>다음을 참조하십시오 [Digital Experience 블루프린트](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) 추가 기술 세부 사항.


## 서드파티 시스템과의 통합

Adobe은 개발자에게 핵심 상거래 기능을 확장하고 Commerce를 서드파티 시스템(예: CRM, ERPS 및 PIMS)과 통합하는 애플리케이션을 빌드하는 포괄적인 확장 지점 및 도구를 제공합니다. 이러한 도구를 사용하면 다음과 같은 방법으로 플랫폼의 TCO를 절감할 수 있습니다.

- **확장성**—핵심 소프트웨어와 별도로 애플리케이션을 확장할 수 있으므로 효율성이 높아지고 업그레이드가 간단해집니다.
- **격리**-격리된 환경은 개발자가 코어 릴리스에 의존하지 않고 재량에 따라 확장을 업그레이드하거나 수정할 수 있음을 의미합니다.
- **기술적 독립성**-개발자는 자신의 요구에 맞는 기술 스택과 코딩 언어를 선택할 수 있습니다.

Adobe은 통합 및 사용자 지정을 빌드하기 위한 다음 개발자 도구를 제공합니다.

- [**Adobe Developer 앱 빌더용 API Mesh**](https://developer.adobe.com/graphql-mesh-gateway/)- 여러 API, GraphQL, REST 및 기타 소스를 하나의 쿼리 가능한 GraphQL 엔드포인트로 조정하고 결합합니다.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/)—Commerce 기능을 확장하고 타사 솔루션과 통합하는 안전하고 확장 가능한 웹 애플리케이션을 구축 및 배포합니다.
- [**이벤트**](https://developer.adobe.com/commerce/extensibility/events/)—사용자 지정 이벤트 트리거를 사용하여 확장 가능한 다른 개발 도구와 상호 작용합니다.
- [**웹훅**](https://developer.adobe.com/commerce/extensibility/webhooks/)- 웹후크를 사용하여 Commerce와 서드파티 시스템 간의 상호 작용을 자동으로 트리거합니다.
- [**관리자 UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)- 판매자를 위한 새 페이지 및 기능을 사용하여 Commerce Admin을 사용자 정의하고 향상시킬 수 있습니다.

## Storefront 서비스

Adobe은 주요 비즈니스 목표를 지원하는 데 도움이 되는 지능적이고 컴포저블 머천다이징 서비스의 풍부한 세트를 제공합니다. 또한 이러한 서비스는 규모에 맞게 성능을 최적화하는 데 중요한 API를 제공합니다.

- [라이브 검색](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)—이 AI 기반 검색 도구를 사용하여 쇼핑객을 위한 보다 스마트하고, 빠르고, 적절한 결과를 제공합니다.
- [제품 Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)—구매자 행동, 인기 트렌드, 제품 유사성 등을 기반으로 AI 기반 권장 사항을 추가합니다.
- [카탈로그 서비스](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview)—고객에게 최적화된 제품 경험을 제공하는 동시에 성능을 향상시키고, 확장성을 향상시키고, 전환을 늘립니다.
- [결제 서비스](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)—무이자 지불 할부, 결제 처리, 주문 및 청구서에 대한 단일 보기를 포함하여 다양한 결제 방법을 제공하여 고객 만족을 높입니다.

## 헤드리스 상점

Headless 거래는 API 우선 거래입니다. Adobe Commerce은 GraphQL API 계층을 통해 모든 상거래 서비스 및 데이터를 제공하는 분리된 아키텍처를 통해 완전히 headless입니다. 이 아키텍처를 통해 팀은 핵심 애플리케이션과 독립적으로 전면을 개발할 수 있으므로 새로운 기술을 통해 새로운 접점을 신속하게 구축하고 테스트할 수 있는 민첩성을 제공합니다.

Adobe은 다음과 같은 기능과 이점을 제공하는 최신 헤드리스 상점 기술을 제공합니다. [Edge Delivery Services](https://www.aem.live/home) 문서 기반 작성, 성능 우선 아키텍처, 즉시 사용 가능한 기본 실험 Adobe Commerce의 규모와 성능을 활용합니다 [상점 첫 방문 서비스](#storefront-services) 및 의 유연성과 편의성 [드롭인 구성 요소](https://experienceleague.adobe.com/developer/commerce/storefront/) 상거래 기능을 제공합니다.

