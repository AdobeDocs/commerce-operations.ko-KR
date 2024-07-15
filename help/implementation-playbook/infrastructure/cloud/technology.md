---
title: 클라우드 인프라 기술
description: 클라우드 인프라의 Adobe Commerce에 대한 기술 Adobe 사용 컬렉션을 자세히 살펴보십시오.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# 기술

Adobe Commerce on cloud infrastructure는 여러 소프트웨어 솔루션을 사용하여 플랫폼을 지원합니다. 자세한 내용은 _Cloud Guide_&#x200B;에서 다음 항목을 참조하십시오.

- [Pro 환경 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [Starter 환경 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## 기능 및 이점

- Virtual Private Cloud(VPC)에 있는 3개의 전용 인스턴스는 3개의 별도 가용 영역 또는 데이터 센터에 걸쳐 탄력적인 로드 밸런서가 있습니다.
- 단일 인스턴스 실패를 초래할 수 있는 이벤트에 대한 복원성이 높습니다. 예를 들어 전체 AWS 가용 영역 또는 데이터 센터의 중단이 있을 수 있습니다.
- 웹, 캐싱, 검색 및 데이터베이스를 포함한 전체 스택에 걸쳐 가동 중지 시간이 전혀 없습니다.
