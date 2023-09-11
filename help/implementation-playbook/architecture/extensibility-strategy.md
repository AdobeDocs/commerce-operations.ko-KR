---
title: Adobe Commerce 확장성 전략
description: Adobe Commerce의 확장성 모델을 통해 구현을 사용자 정의할 수 있는 방법을 알아봅니다.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 확장성 전략

Adobe Commerce의 확장성 플랫폼을 사용하면 업그레이드 능력을 유지하면서 프로세스를 효율적으로 사용자 정의하고, 시스템을 통합하고, 새로운 기능을 배포할 수 있습니다.

## 상거래 확장 전략 개요

Commerce 플랫폼의 기능을 확장하려면 다음과 같은 높은 수준의 접근 방식이 필요합니다.

* Commerce 플랫폼의 기본 기능을 확장합니다. 예를 들어, 판매자는 플랫폼의 기본 기능을 확장하고 구체화하는 Marketplace 애플리케이션(종종 서드파티가 빌드함)을 설치할 수 있습니다(예: 체크아웃 중에 배송 주소를 확인하고 UPS 통신사 주소 API와의 빠른 통합을 용이하게 하는 확장).

* Commerce 플랫폼과 타사 앱/확장 통합. 개발자는 Commerce의 기존 포괄적인 REST 및 GraphQL API를 사용하여 Commerce를 서드파티 솔루션과 직접 통합할 수 있습니다.

그러나 플랫폼 아키텍처는 플랫폼 확장을 위한 최상의 전략을 결정합니다. Commerce는 Headless 배포를 위해 다양한 GQL 및 REST API 범위를 제공합니다. 핵심 Commerce 코드 베이스는 더욱 모듈식 아키텍처와 향상된 새로운 사용자 정의 도구를 제공하는 단일 통합 계층으로 계속 발전하고 있습니다.

* [Adobe Commerce용 App Builder](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) 는 Adobe 인프라를 기반으로 구축된 개발 프레임워크 및 도구 세트입니다. 개발자는 이 도구를 사용하여 사용자 경험/상점 맞춤화부터 미들웨어 및 비즈니스 논리 확장에 이르기까지 다양한 Commerce 확장을 만들 수 있습니다.

* [Adobe Developer 앱 빌더용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/) 개발자가 여러 데이터 소스를 단일 API 엔드포인트로 결합할 수 있습니다. Adobe I/O을 사용하는 Adobe Commerce API 및 기타 Adobe 제품과 개인 및 서드파티 API 및 기타 소프트웨어 인터페이스의 API 오케스트레이션 또는 통합을 지원합니다.

* [Adobe Commerce에 대한 이벤트 Adobe I/O](https://developer.adobe.com/commerce/events/get-started/) 은 App Builder 및 타사 웹 후크를 사용하여 개발된 애플리케이션에서 트랜잭션 데이터를 사용할 수 있도록 하여 이벤트 기반 애플리케이션 생성을 지원합니다.

이러한 도구는 API를 만들고 사용자 정의 플러그인 및 통합을 통합하기 위해 Adobe Developer 콘솔 및 Adobe 개발자 도구에 대한 액세스를 제공합니다.

다음 다이어그램은 Commerce 확장성 전략의 주요 구성 요소를 강조 표시합니다.

![Adobe Commerce 확장성 전략 다이어그램](../../assets/playbooks/extensibility-strategy-overview.png)
