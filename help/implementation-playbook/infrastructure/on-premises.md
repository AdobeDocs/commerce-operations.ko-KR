---
title: 온프레미스 인프라
description: Adobe Commerce 온프레미스 인프라 및 타사 클라우드 서비스에 대해 알아봅니다.
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce 온-프레미스 인프라

새로운 Adobe Commerce 구현을 시작하거나 기존 온프레미스 Adobe Commerce 구현을 클라우드로 전환하는 이유는 많지만, 가장 일반적인 전략적 요인 중 하나는 자본 지출을 줄이고, 지속적인 비용을 절감하고, 확장성과 탄력성을 향상시키며, 시장 출시 시간을 향상시키고, 보안 및 규정 준수를 향상시키는 것입니다.

다음 다이어그램은 AWS 인프라에서 Adobe Commerce 온프레미스 배포를 위한 참조 아키텍처를 보여 줍니다. Azure, Google Cloud 및 Alibaba Cloud와 같은 다른 클라우드 공급업체는 유사한 인프라 디자인과 동종 서비스를 공유합니다.

![타사 클라우드 서비스에서 자체 호스팅된 Adobe Commerce 인프라를 보여주는 다이어그램](../../assets/playbooks/on-premises-infrastructure.svg)

위에 표시된 인프라의 각 측면에 대한 역할과 기능에 대해 자세히 살펴보겠습니다.

1. Amazon Route 53는 DNS 구성을 제공합니다.

1. AWS WAF는 일반적인 웹 취약점 등으로부터 Adobe Commerce을 보호하는 웹 애플리케이션 방화벽입니다.

1. Amazon CloudFront는 정적 및 동적 웹 컨텐츠 배포를 가속화하는 CDN(Fast Content Delivery Network)입니다.

1. 첫 번째 Elastic Load Balancing 애플리케이션 로드 밸런서는 여러 가용 영역의 AWS 자동 크기 조정 그룹의 Varnish 인스턴스에 걸쳐 트래픽을 분산합니다.

1. Varnish Cache는 HTTP 역방향 프록시를 캐싱하는 웹 응용 프로그램 가속기입니다. AWS marketplace를 통해 제공되는 엔터프라이즈 버전은 동적 호스트 간에 클라우드 백엔드와 캐시 지우기를 지원하는 기능이 더 우수하므로 권장됩니다.

1. 두 번째 Elastic Load Balancing 애플리케이션 로드 밸런서는 여러 가용 영역에서 Adobe Commerce 인스턴스의 AWS Auto Scaling 그룹에 있는 Varnish Cache의 트래픽을 배포합니다.

1. Amazon EC2 인스턴스에 최신 버전의 Magento Open Source 또는 Adobe Commerce을 설치합니다. 설치는 Adobe Commerce 애플리케이션, Nginx 웹 서버 및 PHP로 구성됩니다. AMI(Amazon Machine Image)를 작성하여 자동 크기 조정 그룹에서 새 인스턴스를 시작합니다.

1. Amazon Elasticsearch 서비스는 Adobe Commerce 카탈로그 검색을 위한 관리 Elasticsearch 서비스입니다.

1. Redis용 Amazon ElastiCache는 데이터베이스용 캐싱 계층을 제공합니다.

1. Amazon Aurora 또는 AmazonRDS를 사용하여 데이터베이스 관리를 단순화합니다(고가용성 및 다중 마스터 구성 포함).

1. EFSMount Target을 사용하면 Amazon Elastic File System(AmazonEFS)을 Varnish 및 Adobe Commerce 인스턴스에 쉽게 매핑할 수 있습니다.

1. Amazon EFS를 사용하여 Adobe Commerce 인스턴스 간에 Varnish 및 공유 미디어 자산 간의 공유 구성에 액세스합니다.

## 클라우드 서비스

AWS은 Adobe Commerce 환경 주변에서 AWS에서 DevOps 프로세스를 활성화하기 위한 지원 기술 플랫폼을 제공할 뿐만 아니라, 기존 소프트웨어 구성 관리(SCM) 솔루션을 제공하거나 늘릴 수 있는 서비스 컬렉션을 제공합니다. 여기에는 관리되는 소스 제어, 빌드, CI/CD(Continuous Integration/Continuous Deployment) 및 배포 서비스를 허용하는 AWSCodeCommit, AWSCodeBuild, AWSCodePipeline 및 AWSCodeDeploy가 포함됩니다.

## 클라우드 마이그레이션

Adobe Commerce을 AWS으로 마이그레이션하기 위한 가치 제안은 운영 통찰력과 민첩성을 제공하는 몇 가지 서비스를 사용함으로써 더욱 향상되었습니다. 즉, 기술적 관점(예: 시간당 요청 수)뿐만 아니라 비즈니스 운영 관점(예: 시간당 주문 수)에서 플랫폼에 대한 운영 통찰력, 특히 두 세트의 데이터가 결합될 수 있는 경우를 의미합니다. 이를 통해 캠페인 성과, 플랫폼 운영 비용 및 기타 지표의 수를 거의 실시간으로 파악할 수 있습니다.

AWS에 대한 Adobe Commerce 설정은 특정 애플리케이션 종속성을 클라우드에서 사용할 수 있는 완전히 관리되는 대체 요소로 바꿀 수 있습니다. 예를 들어, EC2 인스턴스에서 관계형 데이터베이스를 직접 호스팅하지 않고 많은 애플리케이션의 데이터베이스를 Amazon Relational Database Service(AmazonRDS)로 쉽게 대체할 수 있습니다. 이 전략의 이점은 핵심 애플리케이션을 크게 변경하지 않고도 미분화 구성 요소의 운영 책임을 AWS에 제공할 수 있다는 것입니다.

AWS에서 Adobe Commerce(Magento Open Source 및 Adobe Commerce 버전 모두)를 실행하는 데 사용할 수 있는 몇 가지 배포 옵션이 있습니다. 가장 적합한 선택은 조직의 AWS 및 Adobe Commerce 기술뿐만 아니라 비용, 규모, 가용성, 유연성에 대한 요구 사항에 따라 달라집니다.
