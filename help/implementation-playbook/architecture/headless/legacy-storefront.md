---
title: 결합된 상점 건축
description: 헤드리스 Adobe Commerce 아키텍처의 컨텍스트 내에서 결합된 storfront가 의미하는 바에 대해 알아봅니다.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 결합된(레거시) Adobe Commerce 상점 아키텍처

대부분의 커머셜 고객을 위한 현재 기본 배포 옵션은 다음과 같습니다.

- B2B 및 B2C에서 100% 기능 지원
- 빠르게 배포/사용자 지정할 수 있는 Luma(성숙한 참조 테마)
- 성숙한 SI 파트너 구축 전문 지식
- Page Builder 또는 Staging &amp; Preview와 같은 상거래 기능과 완벽하게 호환
- Adobe Commerce Marketplace의 확장과의 광범위한 호환성

![결합된 Adobe Commerce 상점 전면 아키텍처를 보여주는 다이어그램](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 기존 상점 단점

- **헤드리스 아님**—모놀리식 Adobe Commerce 애플리케이션의 모든 부분입니다. 프런트 엔드 및 백엔드 간에 비즈니스 로직과 프로세스를 분리하지 않습니다.

- **PWA 아님**—테마가 응답형이지만 사이트 성능은 동급 최고의 PWA에 비해 훨씬 낮습니다.

- **프런트 엔드 아키텍처(Adobe Commerce UI 구성 요소)**—기존 저장소에 구축할 Adobe Commerce/PHP 전문가

헤드리스 옵션을 사용하기 전에 보다 익숙한 상점 아키텍처 로 시작하십시오. 헤드리스가 분리되면, 이것은 Luma 데모에서 가장 일반적으로 보이는 연결된 상점 전면 아키텍처가 됩니다.

여기서 상점 기능이 해당 GraphQL API 레이어로 분리되지 않고 핵심 상거래 서비스와 긴밀하게 통합됩니다. 그래서, 그 주제에 결합된 많은 비즈니스 논리가 있습니다. 이 접근법은 헤드리스가 아니라 PWA이 아닙니다.

이 옵션은 B2B 및 B2C Commerce 기능을 모두 사용하여 100% 기능 지원을 제공하므로 현재 판매자가 사용하는 가장 일반적인 옵션입니다. 커뮤니티는 잘 알고 있으며, 그에 대한 전문 지식이 풍부한 성숙된 에코시스템이 있으며, Adobe Commerce Marketplace 확장 프로그램과의 광범위한 호환성을 갖추고 있습니다.

그러나, 그것은 우리가 일찍이 말했던 이점들이 부족하다. 레이어를 분리하지 않으면 변경 시 많은 종속성이 있고 잠재적인 실패 지점이 있습니다. 잘 구현된 PWA만큼 성능이 좋지 않으며 상인이 Adobe Commerce나 PHP 개발에 전문성을 가지고 있지 않다면 해당 리소스를 찾아야 합니다.
