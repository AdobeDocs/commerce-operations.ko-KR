---
title: 헤드리스 상거래
description: Headless Commerce의 의미와 Adobe Commerce이 Headless 아키텍처를 지원하는 방법에 대해 알아봅니다.
exl-id: acf66714-c10e-4c8b-b7ca-04cb2ca2fcf9
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 헤드리스 상거래

## Headless 이유

우선, 레거시 엔터프라이즈 커머스는 비용이 많이 들고 사일로 인해 확장이 어렵고, 플랫폼 제한을 통해 레거시 구조가 강화되며, 혁신이 어려워집니다.

고객은 기업이 모든 채널에서 고객과 상호 작용하고 참여하기를 기대합니다. 고객 중심의 조직은 변화하는 고객 기대에 부응할 수 있는 미래 지향적 플랫폼 구축을 모색하고 있습니다.

Headless 거래는 API 기반 거래입니다. 비즈니스 논리는 물론 상업의 트랜잭션 및 데이터 측면을 프레젠테이션에서 분리합니다. Headless는 플랫폼 자체와 분리된 프론트엔드 경험 레이어와 함께 모든 채널 및 터치포인트에 대한 완전한 유연성을 제공하는 통합 프레임워크입니다. 이를 통해 브랜드는 민첩성을 사용하여 제품, 데이터 및 주문과 같은 콘텐츠를 현재와 미래의 모든 접점에 전달하는 동시에 원하는 방식으로 표시할 수 있습니다.

Headless 아키텍처는 상업용 애플리케이션의 나머지 부분에서 헤드를 기술적으로 분리하는 것입니다. Adobe Commerce은 GraphQL API 계층을 통해 모든 상거래 서비스 및 데이터를 제공하는 분리된 아키텍처를 통해 완전히 headless입니다. 이 아키텍처를 통해 프론트엔드 팀은 Adobe Commerce과 독립적으로 프론트엔드를 개발하여 새로운 기술을 통해 새로운 접점을 신속하게 구축하고 테스트할 수 있습니다.

Adobe Commerce GraphQL API는 Adobe의 I/O Runtime에 배포되는 마이크로서비스를 통해 확장할 수도 있습니다. 백엔드에 대한 코드 사용자 지정 없이 옴니채널 비즈니스 프로세스를 통합, 확장 및 사용자 지정할 수 있는 탁월한 민첩성을 제공하므로 프론트엔드 접점에 영향을 주지 않고 핵심 플랫폼을 쉽게 업그레이드할 수 있습니다. Adobe Commerce GraphQL API는 오픈 소스이며 개발자 커뮤니티에서 제공하는 상당한 기여와 감독으로 커뮤니티 엔지니어링 프로그램의 일부입니다.

![헤드리스 상거래 아키텍처 다이어그램](../../../assets/playbooks/headless-diagram.svg)

![헤드리스 상거래 아키텍처 다이어그램의 이점](../../../assets/playbooks/headless-benefits.svg)
