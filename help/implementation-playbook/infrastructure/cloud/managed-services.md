---
title: Managed Services
description: 클라우드 인프라 구현에서 Adobe Commerce를 위한 Adobe Managed Services, 고객 및 클라우드 서비스 공급자의 책임을 검토하십시오.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# 관리 서비스

클라우드 인프라 관리 서비스의 Adobe Commerce는 기본적으로 안전합니다.

![Adobe 상거래 관리 서비스를 보여주는 다이어그램](../../../assets/playbooks/managed-services.svg)

## 공유 권한

Adobe Commerce Pro는 공유 권한 보안 모델을 사용합니다. 이 모델에서는 시스템의 보안을 유지하기 위해 서로 다른 책임 영역이 있습니다. 이 접근 방식을 통해 최상의 클라우드 기술을 유연하게 사용하고 사용할 수 있습니다.

![Adobe 상거래 공유 권한 모델을 보여주는 다이어그램](../../../assets/playbooks/shared-responsibility.svg)

### Adobe 관리 서비스 책임

Adobe Managed Services는 Adobe Commerce Pro 클라우드 환경, 핵심 Adobe Commerce Pro 애플리케이션 코드 및 내부 상거래 시스템의 보안 및 가용성을 담당합니다. 여기에는 다음이 포함되지만 이에 국한되지 않습니다.

- 서버 수준 패치
- Adobe Commerce Pro 플랜을 제공하는 데 필요한 서비스 운영
- 취약성 테스트
- 보안 이벤트 로깅 및 모니터링
- 사고 관리
- 운영 모니터링
- 24/7 지원
- SLA에 따라 고객 인프라를 사용할 수 있도록 보장

Adobe Managed Services는 또한 서버 방화벽 구성(iptables) 및 주변 방화벽 구성(보안 그룹)을 관리합니다. 또한 Adobe은 코어 애플리케이션에 대한 보안 업데이트를 주기적으로 릴리스할 수 있습니다. 이러한 패치를 적용하는 것은 고객의 책임입니다. 이러한 영역은 클라우드 인프라 시스템에서 Adobe 커머스 PCI 인증을 받습니다.

### AWS 책임

Adobe Managed Services는 클라우드 서버 인프라에 Amazon 웹 서비스(AWS)를 사용합니다. AWS는 방화벽 시스템 및 침입 탐지 시스템(IDS)을 통한 라우팅, 스위칭 및 주변 네트워크 보안 등 네트워크의 보안을 담당합니다. AWS는 적절한 전력, 냉각 및 메커니즘 제어를 보장하기 위한 환경 보안뿐만 아니라 Adobe 커머스 클라우드 환경을 관리하는 데이터 센터에 대한 물리적 보안을 담당합니다.

Adobe Commerce Pro는 다음 사용 방법을 제공합니다.

- Amazon Elastic Compute Cloud(EC2)
- Amazon Simple Storage Service (S3)
- Amazon EBS(Elastic Block Store)
- Amazon VPC(Virtual Private Cloud)
- Amazon ELB(Elastic Load Balancer)
- Amazon 클라우드 추적 서비스.

Amazon에는 PCI DSS, SOC 2 및 ISO 27001 인증이 포함된 광범위한 규정 준수 프로그램이 있습니다.

### 솔루션 파트너/고객 책임

고객은 주로 Adobe Commerce Pro 계획 클라우드 환경에서 실행되는 Adobe 상거래 애플리케이션의 사용자 지정 구현 보안을 담당합니다. 여기에는 다음이 포함됩니다.

- Penetration 테스트 및 일반 취약성 검사 등 애플리케이션 및 보안 모니터링 활동을 안전하게 구성 및 코딩할 수 있도록 합니다.

- 시스템에 사용되는 모든 사용자 지정, 확장, 기타 애플리케이션 또는 통합의 보안

- 사용자의 보안 및 구성 및 애플리케이션에 대한 액세스 권한 부여

- 고객은 비프로덕션 환경에 대한 모든 코드 배포를 제어합니다. 또한 이 제어는 코어 Adobe 상거래 응용 프로그램, 확장 또는 사용자 지정 코드에 응용 프로그램 보안 패치를 적용해야 합니다.

- 고객은 맞춤형 애플리케이션에 대한 침투 테스트를 수행해야 합니다. 이러한 책임은 고객, 구현 파트너 또는 Adobe 상거래 전문 서비스가 기술 리소스를 통해 해결할 수 있습니다.

- 고객은 맞춤형 어플리케이션과 자체 프로세스의 PCI 요구 사항을 담당합니다. 고객의 PCI 규정 준수는 검토해야 하는 영역을 최소화하기 위해 AWS 및 Adobe 커머스 PCI 인증을 기반으로 구축됩니다.
