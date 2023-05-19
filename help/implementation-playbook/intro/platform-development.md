---
title: 플랫폼 개발 원칙
description: Adobe Commerce 작업 시 기본적인 플랫폼 개발 원칙을 이해합니다.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 플랫폼 개발 원칙

이 플레이북에서는 다음을 포함하여 Adobe Commerce 개발의 몇 가지 주요 표준에 대해 자세히 살펴봅니다.

- 개발 프로세스에 따른 기능 및 기술 범위 지정
- MVC 아키텍처에 맞는 개발 모범 사례
- GRA를 포함한 아키텍처 고려 사항
- 스크립팅 및 악용에 대한 보안 표준
- 확장 개발 우수 사례
- REST, SOAP 및 GraphQL과 웹 API 통합
- 코딩 및 인프라 성능 향상
- 테스트 도구, 전략 및 방법론

일부 솔루션 구현자는 구현 프로젝트 전체에서 사용되는 방법론, 프로세스 및 도구에 대해 고유한 환경 설정을 가질 수 있지만, 이 플레이북은 일반적으로 받아들여지는 모범 사례 및 대다수 구현에서 공유할 수 있는 방법론에 중점을 둡니다.

모든 대형 IT 프로젝트와 마찬가지로 Adobe Commerce은 Adobe Commerce 코딩 표준 내에서 확립된 표준뿐만 아니라 기본 기술(예: PHP/Zend, Symfony, JavaScript, jQuery 및 HTML)의 모범 사례 및 표준화를 활용하는 코딩 표준을 기반으로 구축됩니다. 이러한 표준을 따르는 것은 버그를 제거하고 사용자 지정 코드 품질 및 유지 관리를 개선하기 위해 반드시 수행해야 합니다.

## 클라우드 인프라의 Adobe Commerce

Adobe Commerce on cloud infrastructure는 Adobe Commerce 소프트웨어를 위한 관리되고 자동화된 호스팅 플랫폼입니다. Adobe Commerce on cloud infrastructure에는 온-프레미스 Adobe Commerce 및 Magento Open Source 구현과 구별되는 다양한 추가 기능이 포함되어 있습니다.

![Adobe Commerce 구성 요소 인포그래픽](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on cloud infrastructure는 PHP, MySQL, Redis, [!DNL RabbitMQ], 및 Elasticsearch 기술, PaaS(Platform as a Service) 환경에서 코드 변경이 푸시될 때마다 효율적인 신속한 개발 및 지속적인 배포를 위한 자동 빌드 및 배포 작업을 포함하는 Git 기반 워크플로, 사용자 지정이 용이한 환경 구성 파일 및 도구, 온라인 판매 및 소매를 위한 확장 가능하고 안전한 환경을 제공하는 AWS 호스팅.

![Adobe Commerce 구성 요소 인포그래픽](../../assets/playbooks/cloud-tech-stack.svg)
