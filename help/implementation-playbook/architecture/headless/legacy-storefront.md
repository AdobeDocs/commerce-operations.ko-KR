---
title: Storefront 아키텍처 결합
description: Headless Adobe Commerce 아키텍처의 컨텍스트 내에서 결합된 상점 광고가 무엇을 의미하는지 알아봅니다.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# (레거시) Adobe Commerce 상점 첫 화면 아키텍처 결합

대부분의 상용 고객을 위한 현재 기본 배포 옵션은 다음과 같습니다.

- B2B 및 B2C에서 100% 기능 지원
- 빠르게 배포/맞춤화할 수 있는 성숙 참조 테마(Luma)
- 성숙한 SI 파트너 구현 전문 지식
- 페이지 빌더 또는 스테이징 및 미리보기와 같은 상거래 기능과 완벽하게 호환
- Adobe Commerce Marketplace의 확장과 광범위한 호환성

![결합된 Adobe Commerce 상점 첫 화면 아키텍처를 보여 주는 다이어그램](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 기존 상점 단점

- **헤드리스 아님**- 모놀리식 Adobe Commerce 애플리케이션의 모든 부분. 프론트엔드와 백엔드 간에 비즈니스 논리와 프로세스가 분리되지 않습니다.

- **PWA 아님**—테마가 반응적이지만 사이트 성능이 동급 최고의 PWA에 비해 훨씬 뒤쳐집니다.

- **프론트엔드 아키텍처(Adobe Commerce UI 구성 요소)**—Adobe Commerce/PHP 전문가가 기존 상점을 기반으로 구축합니다.

Headless 옵션에 들어가기 전에 보다 친숙한 상점 아키텍처로 시작하겠습니다. Headless가 분리되면 이는 Luma 데모에서 가장 일반적으로 볼 수 있는 결합된 상점 아키텍처가 됩니다.

이 단계에서 상점 기능은 해당 GraphQL API 계층으로 분리되지 않고 핵심 상거래 서비스와 긴밀하게 통합됩니다. 그래서, 그 주제에 결합된 많은 사업 논리가 있습니다. 이 방법은 헤드리스가 아니며 PWA이 아닙니다.

이는 B2B와 B2C 상거래 기능을 모두 갖춘 100% 기능 지원을 보유하고 있기 때문에 현재 가맹점이 가장 많이 사용하는 옵션이다. 커뮤니티는 친숙하고, 관련 전문 지식의 성숙한 생태계가 있으며, Adobe Commerce Marketplace 확장 프로그램과의 광범위한 호환성을 가지고 있습니다.

하지만 우리가 앞서 이야기한 이점은 부족한 것 같습니다. 레이어를 분리하지 않으면 변경 시 많은 종속성과 잠재적인 실패 지점이 있습니다. 이는 잘 구현된 PWA 만큼 성능이 뛰어나지 않으며 판매자가 Adobe Commerce 또는 PHP 개발에 대한 전문 지식이 없다면 그러한 리소스를 찾아야 합니다.
