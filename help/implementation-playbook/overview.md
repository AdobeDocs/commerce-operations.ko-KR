---
title: 구현 플레이북
description: 상거래 구현 Playbook의 목표
exl-id: 2f82c68c-60c7-4a62-837b-492afc06e0db
source-git-commit: 7bad54402e4698545f3436d4195170adb7b48c15
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# 구현 Playbook

이 Playbook의 목적은 일반적인 Adobe Commerce 구현의 가장 전체적인 개요를 제공하는 것입니다.

개발, 통합 및 배포에서 지속적인 지원에 이르기까지 프로젝트 초기 단계부터 Adobe Commerce 프로젝트를 성공적으로 실행하기 위해 고려해야 하는 다양한 방법론과 모범 사례가 있습니다.

또한 이러한 프로세스 및 고려 사항은 모든 종류의 Adobe Commerce 프로젝트에 적용됩니다.

- 소규모, 중간 또는 대규모 구현
- B2C, B2B 및 B2B2C 비즈니스 모델
- 단일 또는 헤드리스 아키텍처
- 단일 시장 또는 다중 시장 출시
- 미들웨어를 사용하거나 사용하지 않는 광범위한 통합

이 Playbook에서 다음과 같은 전자 상거래 프로젝트 이니셔티브에 일반적으로 참여할 수 있는 다양한 이해 당사자에게 통찰력과 지침을 제공하기를 바랍니다.

- CEO와 일반 경영자들은 전자 상거래 출시가 무엇을 수반하는지 확고한 생각을 가져야 한다
- 플랫폼 자체에서 비즈니스 사용자와 작업할 CMO 및 디지털 관리자
- 기술 프로젝트 구현의 모든 단계에서 중요한 역할을 할 CTO 및 기술 관리자
- 상거래 프로젝트 프로젝트를 주도하고 관련 정보를 모두 가지고 있어야 하는 프로젝트 관리자 및 프로젝트 챔피언

IT 프로젝트의 성공은 코드를 개발, 사용자 지정, 통합 및 유지 관리하는 팀(일반적으로 솔루션 파트너)의 경험과 전문 지식에 매우 의존하지만, Adobe는 모든 이해 관계자가 Adobe Commerce 구현의 우수 사례를 숙지하는 것이 적절하다고 생각합니다.

## 이 플레이북 정보

이 Playbook의 구조는 Adobe Commerce 구현 프로젝트의 일반적인 라이프사이클을 따릅니다. 독자가 모든 관련 정보에 대해 프로젝트의 관련 섹션으로 즉시 건너뛸 수 있으므로 이 문서 전체의 탐색을 간소화할 수 있습니다.

- **프로젝트 범위 지정**—기업이 성공적인 구현을 위해 이해하고 완료하는 데 중요한 주요 의사 결정권자, 프로세스, 일정 및 요구 사항을 분류합니다.

- **개발 및 품질 관리**—다양한 Adobe Commerce 구현에 대해 테스트 및 철저한 테스트를 거친 툴, 솔루션, 프로세스, 방법론 및 특정 비즈니스 요구 사항과 목표에 가장 적합한 솔루션을 추천합니다.

- **계획 및 거버넌스**—예산에 맞춰 솔루션을 제공하기 위한 계획을 만드는 것이 여러분의 요구를 충족하는 것이 성공에 도움이 됩니다.

- **아키텍처 및 통합**—Adobe Commerce을 시장에서 가장 신뢰할 수 있고 안정적인 전자 상거래 플랫폼 중 하나로 만드는 기능, 아키텍처 및 통합입니다.

- **인프라 및 배포**—실제 플랫폼 자체에 더 나아가 Adobe Commerce을 지원하는 인프라 및 환경과 강력한 플랫폼을 제공하는 소프트웨어 솔루션을 중점적으로 살펴봅니다.

- **실행 및 잘라내기 프로세스**- 사이트를 라이브로 전환하고 그 효능을 하루 이후부터 유지시키기 위해 수행해야 하는 사전 출시 이후 출시 전략 및 작업

- **지속적인 지원 및 유지 관리**—출시 후에도 브랜드를 계속 이동할 수 있도록 전환 단계와 지속적인 지원 계획에 따른 모델 및 SLA 유형에 대한 세부 정보를 제공합니다.
