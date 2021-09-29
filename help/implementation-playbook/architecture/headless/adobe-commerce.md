---
title: 헤드리스 Adobe 상거래 아키텍처
description: Adobe Commerce의 헤드리스 아키텍처가 고유하게 어떻게 접근하는지 알아봅니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Headless Adobe Commerce Architecture

The benefit of Adobe Commerce’s architecture is that it’s not an all-or-nothing proposition and a merchant can find the right mix of solutions for their business. They can build a PWA Studio-powered PWA for their primary site experience or use Adobe Experience Manaager as the layer in complex customer journeys, all while building out a custom frontend to experiment with new touchpoints. Commerce에서 헤드리스 아키텍처로 제공하는 유연성과 시장 출시 기간 동안 어떤 플랫폼도 충족할 수 없습니다.

![헤드리스 Adobe Commerce storfront 아키텍처를 보여주는 다이어그램](../../../assets/playbooks/headless-storefront-architecture.svg)

각각의 접근 방식은 상호 배타적이 아니다. 고객은 프런트 엔드(헤드)를 빌드하거나, 웹/모바일 경험에 PWA Studio을 사용하거나, 유리에 Adobe Experience Manager을 사용할 수 있습니다(전체 배포 또는 하이브리드 배포).

Adobe 상거래는 항상 REST API를 사용하는 헤드리스 배포에 대해 허용했습니다. REST는 강력하지만 특히 대량 처리에서 헤드리스 측면에서 볼 때 GraphQL API는 직관적인 개발자 경험을 통해 더 빠른 개발을 가능하게 하고, 기존 API에 영향을 주지 않는 변경 사항을 허용하여 유연성이 높으며, 필요한 데이터만 정확히 집계하여 데이터 양을 최소화하여 성능이 향상됩니다.

GraphQL은 많은 상위 전자 상거래 플랫폼에서 사용되는 성능 API에 대한 업계 표준입니다. 이것은 그것이 시장에서 검증된 솔루션과 전문 지식이 존재한다는 것을 의미하기 때문에 그것은 좋은 것입니다.

Adobe Commerce에는 옵션으로 연결된 상점 전면이 있지만, 상인이 Adobe Commerce 레거시 프론트런트런드를 사용할 필요는 없습니다. 상인은 Adobe 상거래 최고의 상거래 서비스를 이용하여 백엔드 비즈니스 프로세스를 처리하고, Adobe의 storefront API를 사용하여 분리된 자체 스토어를 통합하여 프런트 엔드 환경을 구축할 수 있습니다.

이제, 헤드리스 선택 사항들을 살펴봅시다.

## PWA Studio

The first is a progressive web application built with PWA Studio. 이 과정의 일부는 PWA이 상거래 백엔드에서 분리되는 헤드리스 스토어프런트런트입니다. 상인들은 PWA Studio을 통해 Adobe 상거래 위에 고성능, 신뢰성 및 비용 효율적인 PWA을 구축하여 모바일 및 데스크탑에서 동급 최강의 웹 경험을 제공할 수 있습니다. 시간이 갈수록 이 옵션은 기본 옵션으로 연결된 스토어를 앞지릅니다.

대부분의 상인들은 PWA에 대해 산업이 향하여 가고 있는 방향을 이해하며 많은 잠재적인 차단장치들이 빠르게 제거되고 있다.

매주 PWA Studio에 대한 전문 지식을 구축하는 파트너 수가 늘어나고 고객 출시가 가속화되고 있습니다. PWA Studio에 대한 최신 업데이트에는 Adobe Commerce Marketplace 확장과의 호환성을 크게 향상하는 데 도움이 되는 확장성이 포함되어 있습니다.

많은 상인들은 개발자를 많이 의존해야 하기 때문에 헤드리스 및 PWA을 할 준비가 되지 않았다고 생각할 수도 있습니다. 상거래 애플리케이션과 Adobe Commerce에서 개발한 HEAD를 모두 사용할 경우 상거래 기능 전반에서 호환성을 보장할 수 있다는 이점이 있습니다.

Adobe에서는 PWA을 보다 쉽게 액세스할 수 있고 판매자를 위해 관리할 수 있도록 비즈니스 사용자가 Page Builder를 사용하여 일상적인 컨텐츠 변경 사항을 관리하고 새 랜딩 페이지를 만드는 등의 작업을 수행할 수 있도록 합니다. 이 두 가지 강력한 기능을 함께 사용하면 모든 장치와 경험을 빠르게 마케팅할 수 있습니다.

## Adobe Experience Manager

콘텐츠 및 디지털 자산 관리 요구 사항을 위한 강력한 조합인 Adobe Experience Manager를 통해 판매자는 개인화된 콘텐츠 중심의 경험을 더 빨리 시장에 출시하고 디지털 자산 관리를 머신 러닝, Adobe Sensei 기반의 콘텐츠 및 고객 여정 관리의 힘과 결합할 수 있습니다.

Adobe Commerce plus Adobe Exeprience Manager is a powerful story in that the commerce engine allows businesses to enable commerce though customer interfaces that are powered by Adobe Experience Manager.

## Custom Heads

여기서 논의할 마지막 옵션은 사용자 정의 프런트 엔드 구축 옵션입니다. 이 옵션은 React와 같은 특정 프런트 엔드 스택에 숙련된 기존 전문 지식과 사내 개발자를 위한 것입니다. 만약 그들이 Adobe 상거래의 전통적인 프론트엔드 개발에서 기술을 가지고 있지 않다면, 그들은 그들 자신의 사용자 지정 React 프론트엔드 구축을 위해 더 비용 효과적이라고 결정할 수 있습니다.

기본적으로 이 모델은 강력한 고객 또는 시스템 통합을 통해 개발 기술과 리소스를 개발하고, PWA Studio과 함께 제공되는 Page Builder와 같은 과의 네이티브 호환성을 얻을 수 없습니다. 상인이 완전히 맞춤 제품을 만들 때 언제든지 시장 출시 시간을 잃을 수 있습니다.

사용자 정의 프런트엔드는 혁신 및 실험을 가능하게 합니다. AR/VR이나 음성 상거래에 대한 많은 이야기가 있습니다. 그리고 Adobe 커머스 같은 아키텍처는 상인들이 기존의 웹 스토어에 영향을 주지 않고 이러한 옵션을 탐색할 수 있도록 해줍니다.
