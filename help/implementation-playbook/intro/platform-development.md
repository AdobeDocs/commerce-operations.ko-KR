---
title: 플랫폼 개발 원칙
description: Adobe 상거래 작업 시 기본 플랫폼 개발 원칙을 이해합니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# 플랫폼 개발 원칙

이 Playbook에서는 다음을 포함한 Adobe 상거래 개발의 몇 가지 주요 표준에 대해 자세히 설명합니다.

- 개발 프로세스에 따라 기능 및 기술 범위 지정
- MVC 아키텍처에 정렬하는 개발 우수 사례
- GRA를 포함한 아키텍처 고려 사항
- 스크립팅 및 취약점에 대한 보안 표준
- 확장 개발 모범 사례
- REST, SOAP 및 GraphQL과 웹 API 통합
- 코딩 및 인프라를 위한 성능 향상
- 테스트 툴, 전략 및 방법론

일부 솔루션 구현자는 구현 프로젝트 전체에서 사용되는 방법론, 프로세스 및 도구에 대해 자체 환경 설정을 사용할 수 있지만, 이 Playbook은 대부분의 구현에서 공유할 수 있는 일반적으로 받아들여지는 우수 사례와 방법론에 중점을 둡니다.

모든 대규모 IT 프로젝트와 마찬가지로 Adobe Commerce는 Adobe Commerce Coding Standard 내에 구축된 표준뿐만 아니라 기본 기술(예: PHP/Zend, Symfony, JavaScript, jQuery 및 HTML)의 우수 사례 및 표준화를 활용하는 코딩 표준을 기반으로 구축되었습니다. 이러한 표준을 따르는 것은 버그를 제거하고 사용자 지정 코드의 품질 및 유지 관리를 개선하기 위해 절대적이어야 합니다.

## 클라우드 인프라에서 커머스 Adobe

Adobe Commerce on cloud infrastructure는 Adobe 상거래 소프트웨어를 위한 관리 및 자동화된 호스팅 플랫폼입니다. 클라우드 기반의 Adobe 상거래 인프라에는 온프레미스 Adobe 상거래 및 Magento Open Source 구현과 별도로 설정하는 다양한 추가 기능이 포함되어 있습니다.

![Adobe 상거래 구성 요소 인프라 그래픽](../../assets/playbooks/commerce-cloud.svg)

클라우드 인프라에서 Adobe 커머스 는 PHP, MySQL, Redis, RabbitMQ 및 Elasticsearch 기술을 포함하는 사전 프로비저닝 인프라를 제공합니다. PaaS(Platform as a Service) 환경에서 코드 변경 사항이 푸시될 때마다 효율적인 개발 및 지속적인 배포를 위한 자동 빌드 및 배포 작업을 수행하는 Git 기반 워크플로우입니다. 사용자 정의 가능한 환경 구성 파일 및 도구 온라인 판매 및 리테일을 위한 확장 가능하고 안전한 환경을 제공하는 AWS 호스팅

![Adobe 상거래 구성 요소 인프라 그래픽](../../assets/playbooks/cloud-tech-stack.svg)
