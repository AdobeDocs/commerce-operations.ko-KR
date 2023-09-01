---
title: 플랫폼 개발 원칙
description: Adobe Commerce 작업 시 기본적인 플랫폼 개발 원칙을 이해합니다.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 3c1a49c2dc3dc0d3d47e16c724d4099b6a456c77
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 플랫폼 개발 원칙

이 항목에서는 다음을 포함하여 Adobe Commerce 개발의 몇 가지 주요 표준에 대해 자세히 설명합니다.

- 개발 프로세스에 따른 기능 및 기술 범위 지정
- MVC 아키텍처에 맞는 개발 모범 사례
- GRA를 포함한 아키텍처 고려 사항
- 스크립팅 및 악용에 대한 보안 표준
- 확장 개발 우수 사례
- REST, SOAP 및 GraphQL과 웹 API 통합
- 코딩 및 인프라 성능 향상
- 테스트 도구, 전략 및 방법론

일부 솔루션 구현자는 방법론, 프로세스 및 도구에서 고유한 환경 설정을 가질 수 있지만, 이 플레이북은 대부분의 구현에서 공유할 수 있는 허용되는 모범 사례 및 방법론에 중점을 둡니다.

모든 대형 IT 프로젝트와 마찬가지로 Adobe Commerce은 모범 사례 및 표준화를 사용하는 코딩 표준 및 Adobe Commerce 내에 제정된 표준을 기반으로 구축됩니다 [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/). 이러한 표준을 따르는 것은 버그를 제거하고 사용자 지정 코드 품질 및 유지 관리를 개선하는 데 중요합니다.

## 클라우드 인프라의 Adobe Commerce

Adobe Commerce on cloud infrastructure는 Adobe Commerce 소프트웨어를 위한 관리되고 자동화된 호스팅 플랫폼입니다. Adobe Commerce on cloud infrastructure에는 온-프레미스 Adobe Commerce 및 Magento Open Source 구현과 구별되는 다양한 기능이 포함되어 있습니다. 다음을 참조하십시오. [Cloud 안내서](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html).
