---
title: Adobe Commerce 글로벌 참조 아키텍처
description: 글로벌 참조 아키텍처를 활용하여 Adobe Commerce 구현을 최대한 활용하십시오.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: f713e07b57705e8720c773f9f762a357c173e29d
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 글로벌 참조 아키텍처(GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

지역화된 통화, 언어, 미디어, 공유 카탈로그 및 고유 장바구니와 함께 여러 로컬 시장에서 여러 브랜드를 위한 여러 사이트를 운영하고 동일한 기능 및 통합을 구현하기 위한 불필요한 비용을 방지하려는 비즈니스를 운영하는 경우, 글로벌 참조 아키텍처(GRA)는 항상 좋은 옵션입니다.

![건축에서 발산의 비용을 설명하는 표](../../assets/playbooks/divergent-architecture.svg)

![아키텍처 통합 비용을 설명하는 표](../../assets/playbooks/consolidated-architecture.svg)

GRA:

- 구현 접근 방식
- 배포 전략
- 프로세스 거버넌스 모델

GRA는 다음과 같지 않습니다.

- 제품 &quot;기능&quot;
- 모든 상거래 플랫폼에 고유
- 글로벌 비즈니스 사용 사례에만 해당

GRA의 영향:

- 코드 전달 방법

   - 다양한 경험을 제공하는 용도별 코드 저장소를 중심으로 구축됩니다.

- 비즈니스 시스템 통합 방법

   - 브랜드 및/또는 지역별로 비즈니스 시스템에 대한 연결 통합

- 맞춤화 개발 및 유지 관리 방법

   - 맞춤화는 중앙 집중화되고 도메인별로 수행되므로 비즈니스에 대한 전체적인 관점에서 모든 맞춤화 작업이 수행됩니다.

- 새로운 시장을 활성화하는 방법

   - 여러 채널 및 시장의 출시를 간소화하므로 시간과 비용이 상당히 많이 듭니다.
