---
title: 온프레미스 인프라
description: Adobe Commerce 온프레미스 인프라 및 서드파티 클라우드 서비스에 대해 알아봅니다.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Adobe Commerce 온-프레미스 인프라

새로운 Adobe Commerce 구현을 시작하거나 기존 온프레미스 Adobe Commerce 구현을 클라우드로 이전하는 동기는 다양하지만 가장 일반적인 전략적 요인은 자본 지출 감소, 지속적인 비용 절감, 확장성 및 탄력성 향상, 마켓 출시 시간 개선, 보안 및 규정 준수 개선 등입니다.

다음 다이어그램은 AWS 인프라에 Adobe Commerce 온프레미스를 배포하기 위한 참조 아키텍처를 보여 줍니다. Azure, Google Cloud 및 Alibaba Cloud와 같은 다른 클라우드 공급업체는 유사한 인프라 설계와 상동 서비스를 공유합니다.

![타사 클라우드 서비스에서 자체 호스팅 Adobe Commerce 인프라를 보여 주는 다이어그램](/help/assets/playbooks/on-premises-infrastructure.svg)

위에 표시된 인프라의 각 측면에 대한 역할과 기능에 대해 자세히 살펴보겠습니다.

1. Amazon Route 53는 DNS 구성을 제공합니다.

1. AWS WAF는 일반적인 웹 악용으로부터 Adobe Commerce을 보호하는 웹 애플리케이션 방화벽입니다.

1. Amazon CloudFront는 정적 및 동적 웹 콘텐츠의 배포 속도를 높이는 빠른 콘텐츠 전달 네트워크(CDN)입니다.

1. 첫 번째 Elastic Load Balancing 애플리케이션 로드 밸런서는 여러 가용 영역의 AWS Auto Scaling 그룹에 있는 바니시 인스턴스 간에 트래픽을 분산합니다.

1. Varnish Cache는 HTTP 역방향 프록시를 캐시하는 웹 응용 프로그램 가속기입니다. AWS 마켓플레이스를 통해 사용할 수 있는 엔터프라이즈 버전은 클라우드 백엔드와 동적 호스트 간의 캐시 지우기를 지원하는 기능이 더 우수하므로 권장됩니다.

1. 두 번째 Elastic Load Balancing 애플리케이션 로드 밸런서는 Varnish Cache의 트래픽을 여러 가용 영역의 Adobe Commerce 인스턴스 AWS Auto Scaling 그룹에 분산합니다.

1. Amazon EC2 인스턴스에 최신 버전의 Adobe Commerce을 설치합니다. 설치는 Adobe Commerce 응용 프로그램, Nginx 웹 서버 및 PHP로 구성됩니다. Amazon 머신 이미지(AMI)를 구축하여 Auto Scaling 그룹에서 새 인스턴스를 시작합니다.

1. Amazon Elasticsearch 서비스는 Adobe Commerce 카탈로그 검색에 대한 관리되는 Elasticsearch 서비스입니다.

1. Amazon Redis용 ElastiCache는 데이터베이스에 캐싱 레이어를 제공합니다.

1. Amazon Aurora 또는 AmazonRDS를 사용하여 데이터베이스 관리(고가용성 및 멀티 마스터 구성 포함)를 단순화합니다.

1. EFSMount Target을 사용하면 Amazon Elastic File System(AmazonEFS)을 Varnish 및 Adobe Commerce 인스턴스에 쉽게 매핑할 수 있습니다.

1. Amazon EFS를 사용하여 Adobe Commerce 인스턴스의 니스 및 공유 미디어 에셋에 대한 공유 구성에 액세스합니다.

## 클라우드 서비스

AWS은 Adobe Commerce 환경과 관련하여 AWS에서 DevOps 프로세스를 사용할 수 있도록 지원하는 기술 플랫폼을 제공하는 것 외에도 기존 SCM(소프트웨어 구성 관리) 솔루션을 제공하거나 보완할 수 있는 서비스 컬렉션을 제공합니다. 여기에는 관리 소스 제어, 빌드, CI/CD(지속적 통합/지속적 배포) 및 배포 서비스를 허용하는 AWSCodeCommit, AWSCodeBuild, AWSCodePipeline 및 AWSCodeDeploy가 포함됩니다.

## 클라우드 마이그레이션

Adobe Commerce을 AWS으로 마이그레이션하는 데 대한 가치 제안은 운영 통찰력과 민첩성을 제공하는 여러 서비스를 통해 더욱 향상됩니다. 즉, 기술적 관점(예: 시간당 요청)뿐만 아니라 비즈니스 운영 관점(예: 시간당 주문)에서도 플랫폼에 대한 운영 통찰력(예: 두 데이터 세트가 결합될 수 있는 경우)을 제공합니다. 이렇게 하면 캠페인 성과, 플랫폼 운영 비용 및 기타 지표가 거의 무한대에 가깝게 실시간으로 파악할 수 있습니다.

Adobe Commerce에서 AWS으로 설정하면 특정 애플리케이션 종속성이 클라우드에서 사용할 수 있는 완전히 관리되는 대체 요소로 대체될 수 있습니다. 예를 들어, EC2 인스턴스에서 관계형 데이터베이스를 직접 호스팅하지 않고, 여러 애플리케이션의 데이터베이스를 Amazon Relational Database Service(AmazonRDS)로 쉽게 대체할 수 있습니다. 이 전략의 이점은 핵심 애플리케이션을 크게 변경하지 않고도 미분화 구성 요소의 운영 책임을 AWS으로 오프로드할 수 있다는 것입니다.

AWS에서 Adobe Commerce을 실행하는 데 사용할 수 있는 몇 가지 배포 옵션이 있습니다. 가장 적절한 선택은 비용, 규모, 가용성 및 유연성에 대한 요구 사항과 조직의 AWS 및 Adobe Commerce 기술에 따라 다릅니다.

{{$include /help/_includes/hosting-related-links.md}}
