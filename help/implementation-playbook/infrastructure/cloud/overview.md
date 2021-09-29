---
title: 클라우드 인프라 개요
description: 클라우드 인프라에서 Adobe 상거래에 대해 알아봅니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# 개요

AWS에서 Adobe 상거래를 위한 가장 인기 있는 관리 호스팅 옵션 중 하나는 Adobe 상거래 자체에서 제공합니다. Adobe Commerce on cloud infrastructure는 Adobe 상거래 소프트웨어를 위한 완전히 관리되는 자동화된 호스팅 플랫폼입니다.

Adobe Commerce on cloud infrastructure is a platform-as-a-service (PaaS) offering that enables rapid deployment of fully customizable, secure, and scalable web storefronts combined with a leading hosting and managed services infrastructure. 다양한 인프라와 함께 두 가지 계획을 제공합니다. Adobe Commerce Starter는 복잡성이 적고 카탈로그가 작은 소규모 저장소에 가장 적합합니다. Adobe Commerce Pro는 더욱 복잡해진 대형 상점, 더 큰 제품 카탈로그 또는 트래픽이 가장 많이 발생하는 경우를 위해 설계되었습니다. Adobe Commerce will determine the appropriate architecture with input from partners.

Adobe Commerce는 최적화된 성능, 탄력성 및 탄력적인 확장성을 제공하는 완전 중복 멀티 클라우드 호스팅 인프라를 갖춘 클라우드 솔루션입니다. You can efficiently run your commerce platform on Fastly’s content delivery network (CDN), and with New Relic for monitoring and management you can keep your store environment running smoothly.

Adobe Commerce offers all the benefits of modern cloud computing that are most commonly associated with SaaS solutions: elastic scalability, high resilience and availability, PCI compliance, and global availability and automated patching, while still maintaining flexibility in software customization that our merchants require.

![클라우드 인프라에서 Adobe 상거래의 아키텍처 요소를 보여주는 다이어그램](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 이점

Adobe 상거래의 기타 이점은 다음과 같습니다.

- **Adobe 상거래에 최적화되었습니다**. Adobe Commerce에서 개발한 빌드 스크립트 및 서비스 구성을 통해 최적의 머천트 성능을 위해 모든 인스턴스를 올바르게 튜닝하고 구성할 수 있습니다.

- **일관된 보안 릴리스**. 모든 코드 배포는 보안 강화를 위한 읽기 전용 프로덕션 환경을 갖춘 일관성 및 반복 기능을 위한 Git 기반입니다.

- **파트너를 위한 유연성**. 전체 REST API 및 스크립트 가능한 명령줄 인터페이스를 사용하면 외부 시스템과 쉽게 통합하고 기존 코드 관리 워크플로우와 호환됩니다.

- **유연한 배포 도구 세트**. 개발 작업, QA 테스트 또는 프로덕션 문제 진단에 대해 원하는 대로 신속하게 환경을 스핀업, 병합, 복제 및 축소합니다.

- **Continuous cloud delivery**. 코드 분기 및 개발 팀에서 지속적으로 개발에서 UAT로 바로 전환하고 있습니다.

## Third-party services

Let’s also take a look at the software that makes Adobe Commerce’s benefits a reality.

![클라우드 인프라 기술 스택에서 Adobe 상거래를 보여주는 다이어그램](../../../assets/playbooks/cloud-tech-stack.svg)

- 강력한 CDN: 고객이 사이트에 액세스하고 저장소에 액세스하면 요청이 Faste에 도달하여 캐시된 페이지를 더 빨리 로드합니다. WAF는 또한 디도스 보호 서비스를 제공합니다.

- New Relic을 통해 애플리케이션 및 운영 환경을 완벽하게 파악할 수 있습니다. 이 기능을 사용하면 모바일 및 브라우저 애플리케이션의 주요 지표와 지원 서비스, 데이터 저장소 및 호스트를 결합할 수 있으므로 전체 성능으로 최적화하고 모든 이니셔티브의 성공을 보장할 수 있습니다.

- 작성기는 Adobe Commerce에서 종속성 및 업그레이드를 관리하고, 포함된 패키지, 패키지 작업 및 해당 방식에 대한 컨텍스트를 제공합니다.

- Git is your code in repositories. 자동 빌드 및 배포를 통해 로컬 분기, 편리한 스테이징 영역 및 여러 워크플로우를 통해 효율적인 개발 및 지속적인 배포를 수행할 수 있습니다.

- Platform-as-a-Service(PaaS)는 PHP, MySQL, Redis, RabbitMQ 및 Elasticsearch 기술을 포함하는 미리 제공된 인프라를 제공합니다.

- AWS 또는 Azure의 클라우드 호스팅은 온라인 판매 및 소매업을 위한 확장 가능하고 안전한 환경을 제공하는 기본 IaaS(Infrastructure-as-a-Service)를 지원합니다.
