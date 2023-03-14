---
title: 클라우드 인프라 기술
description: 클라우드 인프라에서 Adobe Commerce에 사용되는 기술 컬렉션을 자세히 살펴보십시오.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 기술

앞에서 언급했듯이 Adobe Commerce은 다양한 소프트웨어 솔루션을 활용하여 플랫폼을 지원합니다. 특히 프로덕션과 관련하여 프로덕션 환경을 최대한 활용하는 데 도움이 되는 Adobe Commerce on cloud infrastructure에 포함된 몇 가지 기술 솔루션과 기능을 분류했습니다.

![클라우드 인프라 기술에 대한 Adobe Commerce을 보여 주는 다이어그램](../../../assets/playbooks/infrastructure-technology.svg)

## 소프트웨어 솔루션

- **Ngix**- PHP-FPM을 사용하는 웹 서버입니다. 여러 작업자가 있는 인스턴스가 한 개 있습니다.

- **글로스터**—4개의 디렉토리 마운트를 사용하여 모든 정적 파일 배포 및 동기화를 관리하는 파일 서버:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **레디스**—VM당 하나의 서버만 활성 상태이고 나머지 두 서버는 복제본입니다.

- **Elasticsearch**- Adobe Commerce 버전 2.2.x 이상을 검색합니다.

- **OpenSearch**- Adobe Commerce 버전 2.4.6 이상을 검색합니다.

- **갈레라**—노드당 하나의 MariaDB MySQL 데이터베이스가 있는 데이터베이스 클러스터로, 모든 데이터베이스의 고유 ID에 대해 3의 자동 증가 설정을 사용합니다.

## 기능 및 이점

- VPC에 3개의 전용 인스턴스가 있는 경우, 3개의 개별 가용 영역 또는 데이터 센터에 탄력적인 로드 밸런서가 있습니다.

- 단일 인스턴스 실패를 초래할 수 있는 이벤트에 대해 더 높은 복원성이 제공됩니다. 예를 들어 전체 AWS 가용 영역 또는 데이터 센터의 가동 중단이 이에 해당합니다.

- 웹, 캐싱, 검색 및 데이터베이스를 포함한 전체 스택에 대해 15분 이내에 다운타임 없이 확장할 수 있습니다.
