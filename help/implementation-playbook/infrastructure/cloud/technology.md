---
title: 클라우드 인프라 기술
description: 클라우드 인프라에서 Adobe Commerce에 사용하는 기술 컬렉션을 자세히 살펴봅니다.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 기술

앞서 언급했듯이 Adobe Commerce은 많은 소프트웨어 솔루션을 활용하여 플랫폼을 지원합니다. 특히, 프로덕션에 관련되어 있어, Adobe에서는 프로덕션 환경을 최대한 활용하는 데 도움이 되는 클라우드 인프라의 Adobe Commerce에 포함된 일부 기술 솔루션과 기능을 분류했습니다.

![클라우드 인프라 기술에 대한 Adobe Commerce을 보여주는 다이어그램](../../../assets/playbooks/infrastructure-technology.svg)

## 소프트웨어 솔루션

- **Nginx**—PHP-FPM을 사용하는 웹 서버입니다. 여러 작업자가 있는 인스턴스가 한 개 있습니다.

- **GlusterFS**—4개의 디렉토리 마운트를 사용하여 모든 정적 파일 배포를 관리하고 동기화할 수 있는 파일 서버:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **레디스**—VM당 하나의 서버당 하나의 서버로서 하나의 서버만 활성화되고 다른 두 서버는 복제본으로 사용됩니다.

- **Elasticsearch**- Adobe Commerce 버전 2.2.x 이상을 검색합니다.

- **갈레라**—모든 데이터베이스의 고유 ID에 대해 자동 증분 설정이 3인 노드당 하나의 MariaDB MySQL 데이터베이스를 사용하는 데이터베이스 클러스터.

## 기능 및 이점

- VPC에 세 개의 전용 인스턴스가 있으면 세 개의 분리된 가용 영역 또는 데이터 센터에 탄력적인 로드 밸런서가 있습니다.

- 단일 인스턴스가 실패할 수 있는 이벤트에 대해 높은 복원력이 제공됩니다. 예를 들어 전체 AWS 가용성 영역 또는 데이터 센터의 중단이 있습니다.

- 웹, 캐싱, 검색 및 데이터베이스를 포함하여 전체 스택에서 다운타임이 15분 이내에 전혀 발생하지 않습니다.
