---
title: 클라우드 인프라 환경
description: 적합한 사용 사례에 적합한 환경을 사용하십시오.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 환경

Adobe Commerce on cloud infrastructure Pro 아키텍처는 스토어를 개발, 테스트 및 시작하는 데 사용할 수 있는 환경을 지원합니다. 각 환경에는 데이터베이스와 웹 서버가 있습니다. Adobe Commerce에서 활용하는 네 가지 환경은 다음과 같습니다.

- **통합**- 단일 환경 분기를 제공하며 최대 4개의 추가 환경 분기를 생성할 수 있습니다. 이를 통해 PaaS(Platform-as-a-Service) 컨테이너에 최대 5개의 활성 분기를 배포할 수 있습니다.

- **스테이징**—전용 IaaS(Infrastructure-as-a-Service) 컨테이너에 구축되는 단일 환경 분기 제공

- **프로덕션**—전용 IaaS(Infrastructure-as-a-Service) 컨테이너에 구축되는 단일 환경 분기 제공

- **글로벌 기본**- PaaS(Platform-as-a-Service) 컨테이너에 배포되는 마스터 분기를 제공합니다.

![Adobe Commerce 클라우드 환경 간의 관계를 보여 주는 다이어그램](../../../assets/playbooks/environment-diagram.svg)

## Git 분기

통합 환경은 PaaS(Platform-as-a-Service) 컨테이너에 배포된 Adobe Commerce 코드가 포함된 단일 기본 통합 분기를 제공합니다.

클라우드 인프라 환경의 Adobe Commerce은 유연하고 지속적인 통합 프로세스를 지원합니다. 로컬 프로젝트 폴더에 통합 분기를 복제하는 것부터 시작합니다. 새 분기 또는 여러 분기를 만들어 새 기능을 개발하고 변경 사항을 구성하고 확장을 추가합니다. 개발된 코드 분기 및 해당 구성 파일을 사용하면 코드 변경 사항을 통합 분기에 병합하여 보다 포괄적인 테스트를 수행할 수 있습니다.

![Adobe Commerce 클라우드 환경에 대한 git 기반 분기 전략을 보여 주는 다이어그램](../../../assets/playbooks/branching-diagram.svg)
