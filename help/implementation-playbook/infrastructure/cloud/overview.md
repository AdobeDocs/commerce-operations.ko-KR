---
title: 클라우드 인프라 개요
description: 클라우드 인프라의 Adobe Commerce에 대해 알아봅니다.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# 개요

AWS에서 Adobe Commerce에 대해 가장 인기 있는 관리 호스팅 옵션 중 하나는 Adobe Commerce 자체에서 제공합니다. Adobe Commerce on cloud infrastructure는 Adobe Commerce 소프트웨어를 위한 완전히 관리되는 자동화된 호스팅 플랫폼입니다.

Adobe Commerce on cloud infrastructure는 선도적인 호스팅 및 Managed Services 인프라와 결합하여 완전히 맞춤화되고 안전하며 확장 가능한 웹 스토어를 신속하게 배포할 수 있도록 해주는 PaaS(platform-as-a-service) 서비스입니다. 인프라가 다른 두 가지 플랜을 제공합니다. Adobe Commerce [스타터](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) 플랜은 복잡성이 적고 카탈로그가 더 작은 소규모 스토어에 가장 적합합니다. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) 플랜은 복잡성이 더 큰 대규모 매장, 대규모 제품 카탈로그 또는 최대 트래픽에 맞게 디자인되었습니다. Adobe은 파트너의 입력을 통해 적절한 아키텍처를 결정합니다.

Adobe Commerce은 최적화된 성능, 복원력 및 탄력적인 확장성을 제공하는 완전 이중화 멀티 클라우드 호스팅 인프라를 통해 클라우드에 대비됩니다. Fastly의 CDN(콘텐츠 전송 네트워크)에서 상거래 플랫폼을 효율적으로 실행할 수 있으며, 모니터링 및 관리를 위한 New Relic을 사용하면 스토어 환경을 원활하게 실행할 수 있습니다.

Adobe Commerce은 소프트웨어 맞춤화 시 유연성을 유지하면서 SaaS 솔루션과 가장 일반적으로 연결되는 최신 클라우드 컴퓨팅의 모든 이점을 제공합니다.

- 탄력적인 확장성
- 높은 복원력 및 가용성
- PCI 준수
- 글로벌 가용성 및 자동 패치

![클라우드 인프라에서 Adobe Commerce의 아키텍처 요소를 보여 주는 다이어그램](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 이점

Adobe Commerce의 다른 이점은 다음과 같습니다.

- **Adobe Commerce에 최적화**. Adobe Commerce에서 개발한 빌드 스크립트 및 서비스 구성을 통해 모든 인스턴스가 최적의 판매자 성능을 위해 올바르게 튜닝되고 구성되도록 합니다.

- **일관되고 안전한 릴리스**. 모든 코드 배포는 일관성 및 반복성을 위한 Git 기반이며, 보안 강화를 위해 읽기 전용 프로덕션 환경이 제공됩니다.

- **파트너를 위한 유연성**. 전체 REST API와 스크립트 가능한 명령줄 인터페이스를 통해 외부 시스템과의 통합이 용이하고 기존 코드 관리 워크플로우와의 호환성이 보장됩니다.

- **유연한 배포 도구 집합**. 개발 작업, QA 테스트 또는 운영 문제 진단을 위해 필요에 따라 환경을 신속하게 회전, 병합, 복제 및 분류할 수 있습니다.

- **지속적인 클라우드 게재**. 코드 분기 및 개발 팀 간에 지속적인 방식으로 개발에서 UAT로, 프로덕션으로 자신 있게 이동합니다.

## 타사 서비스

이 섹션에서는 클라우드 인프라 프로젝트에서 Adobe Commerce을 위한 주요 타사 서비스 및 도구를 요약합니다. 자세한 내용은 _Cloud Guide_&#x200B;의 [기술 스택](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html)을 참조하십시오.

- **Fastly CDN**: 고객이 사이트와 스토어에 액세스할 때 캐시된 페이지를 더 빨리 로드하기 위해 요청이 Fastly에 도달합니다. Fastly WAF는 또한 DDoS 보호 서비스를 제공합니다.

- **New Relic**: 응용 프로그램 및 운영 환경에 대한 전체 보기를 제공합니다. New Relic을 사용하면 모바일 및 브라우저 애플리케이션의 주요 지표를 지원 서비스, 데이터 저장소 및 호스트와 결합하여 전체적으로 성능을 최적화하고 모든 이니셔티브의 성공을 보장할 수 있습니다.

- **작성기**: Adobe Commerce에서 종속성 및 업그레이드를 관리하고 포함된 패키지, 패키지의 기능 및 패키지 결합 방법에 대한 컨텍스트를 제공합니다.

- **Git**: 소스 코드 관리를 제공합니다. Git을 사용하면 효율적인 신속한 개발과 지속적인 배포를 위해 로컬 분기, 편리한 스테이징 영역 및 자동 빌드 및 배포의 여러 워크플로우를 사용할 수 있습니다.

- **PaaS(Platform-as-a-Service)**: PHP, MySQL, Redis, [!DNL RabbitMQ] 및 OpenSearch 또는 Elasticsearch 기술을 포함하는 사전 제공된 인프라를 제공합니다.

- **AWS 또는 Azure의 클라우드 호스팅**: 온라인 판매 및 소매에 확장 가능하고 안전한 환경을 제공하는 기본 IaaS(Infrastructure-as-a-Service)를 지원합니다.
