---
title: 클라우드 인프라 개요
description: 클라우드 인프라의 Adobe Commerce에 대해 알아봅니다.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 개요

AWS에서 Adobe Commerce에 대해 가장 인기 있는 관리 호스팅 옵션 중 하나는 Adobe Commerce 자체에서 제공합니다. Adobe Commerce on cloud infrastructure는 Adobe Commerce 소프트웨어를 위한 완전히 관리되는 자동화된 호스팅 플랫폼입니다.

Adobe Commerce on cloud infrastructure는 선도적인 호스팅 및 관리 서비스 인프라와 결합하여 완전히 맞춤화되고 안전하며 확장 가능한 웹 스토어를 신속하게 배포할 수 있도록 해주는 PaaS(platform-as-a-service) 서비스입니다. 인프라가 다른 두 가지 플랜을 제공합니다. Adobe Commerce Starter는 복잡성이 적고 카탈로그가 더 작은 소규모 스토어에 가장 적합합니다. Adobe Commerce Pro는 복잡성, 제품 카탈로그 또는 트래픽이 많은 대형 스토어를 위해 구축됩니다. Adobe Commerce은 파트너의 입력을 통해 적절한 아키텍처를 결정합니다.

Adobe Commerce은 최적화된 성능, 복원력 및 탄력적인 확장성을 제공하는 완전 이중화 멀티 클라우드 호스팅 인프라를 통해 클라우드에 대비됩니다. Fastly의 CDN(콘텐츠 전송 네트워크)에서 상거래 플랫폼을 효율적으로 실행할 수 있으며, 모니터링 및 관리를 위한 New Relic을 사용하면 스토어 환경을 원활하게 실행할 수 있습니다.

Adobe Commerce은 탄력적인 확장성, 높은 복원력 및 가용성, PCI 규정 준수, 글로벌 가용성 및 자동 패치 등 SaaS 솔루션과 가장 일반적으로 관련된 최신 클라우드 컴퓨팅의 모든 이점을 제공하면서도 판매자가 필요로 하는 소프트웨어 사용자 지정에 있어 여전히 유연성을 유지합니다.

![클라우드 인프라에서 Adobe Commerce의 아키텍처 요소를 보여주는 다이어그램](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 이점

Adobe Commerce의 다른 이점은 다음과 같습니다.

- **Adobe Commerce에 최적화**. Adobe Commerce에서 개발한 빌드 스크립트 및 서비스 구성을 통해 모든 인스턴스를 최적의 판매자 성능을 위해 올바르게 튜닝하고 구성할 수 있습니다.

- **일관되고 안전한 릴리스**. 모든 코드 배포는 일관성 및 반복성을 위한 Git 기반이며, 보안 강화를 위해 읽기 전용 프로덕션 환경이 제공됩니다.

- **파트너를 위한 유연성**. 전체 REST API 및 스크립팅 가능한 명령줄 인터페이스를 통해 외부 시스템과의 편리한 통합 및 기존 코드 관리 워크플로우와의 호환성을 보장합니다.

- **유연한 배포 도구 집합**. 개발 작업, QA 테스트 또는 운영 문제 진단을 위해 필요에 따라 환경을 신속하게 회전, 병합, 복제 및 분류할 수 있습니다.

- **지속적인 클라우드 게재**. 코드 분기 및 개발 팀 간에 지속적인 방식으로 개발에서 UAT로, 프로덕션으로 자신 있게 이동합니다.

## 타사 서비스

Adobe Commerce의 이점을 현실로 만드는 소프트웨어도 살펴보겠습니다.

![클라우드 인프라 기술 스택에 대한 Adobe Commerce을 보여 주는 다이어그램](../../../assets/playbooks/cloud-tech-stack.svg)

- Fastly CDN: 고객이 사이트에 액세스하고 저장할 때 요청이 Fastly에 도달하여 캐시된 페이지를 더 빨리 로드합니다. Fastly WAF는 DDoS 보호 서비스를 제공합니다.

- New Relic에서는 애플리케이션 및 운영 환경을 전체적으로 볼 수 있습니다. 모바일 및 브라우저 애플리케이션의 주요 지표를 지원 서비스, 데이터 저장소 및 호스트와 결합하여 전체적으로 성능을 최적화하고 모든 이니셔티브의 성공을 보장할 수 있습니다.

- Composer는 Adobe Commerce에서 종속성 및 업그레이드를 관리하고 포함된 패키지, 패키지의 기능 및 패키지 결합 방법에 대한 컨텍스트를 제공합니다.

- Git은 저장소의 코드입니다. 로컬 분기, 편리한 스테이징 영역 및 자동 빌드 및 배포로 여러 워크플로우를 통해 효율적인 신속한 개발과 지속적인 배포를 가능하게 합니다.

- PaaS(Platform-as-a-Service)는 PHP, MySQL, Redis, [!DNL RabbitMQ], 및 OpenSearch 또는 Elasticsearch 기술

- AWS 또는 Azure의 클라우드 호스팅은 온라인 판매 및 소매에 확장 가능하고 안전한 환경을 제공하는 기본 IaaS(Infrastructure-as-a-Service)를 지원합니다.
