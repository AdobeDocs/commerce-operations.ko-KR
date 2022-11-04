---
title: 문제 해결 우수 사례
description: Adobe Commerce 구현 문제를 해결하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 754051c98d2c5265398f1f0806cb34128fe03c36
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# 문제 해결 우수 사례

클라우드 인프라 문제에 대한 Adobe Commerce의 효과적인 문제 해결을 위해 다음 우수 사례를 따르십시오.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud 인프라

## 우수 사례

| 문제 유형 | 우수 사례 | 리소스 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 배포 문제 | **배포 우수 사례를 따릅니다.** 지원 티켓 중 13%는 배포 문제를 포함합니다. 이러한 원인 중 많은 것을 방지하는 방법을 포함하도록 모범 사례가 업데이트되었습니다. | [빌드 및 배포에 대한 우수 사례](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 개발자 설명서에서 를 참조하십시오. |
| 사이트 다운 문제 | **사이트 다운 문제 해결사를 사용합니다.** 크론은 오래 실행될 수 있고 서로 오버런할 수 있습니다. 많은 운영 중단과 성능 문제의 원인입니다. | [사이트 아래로 문제 해결사](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 및 [충돌 작업을 재설정하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 지원 기술 자료에서 |
| 성능 문제 | **Adobe Commerce 배너를 사용하지 않는 경우 비활성화하십시오.** 배너를 활성화했지만 사용하지 않으면 리소스가 필요하지 않으면 데이터베이스를 조회하는 데 사용되며 성능 문제가 발생합니다. | [성능을 향상시키기 위해 Adobe Commerce 배너 출력을 비활성화합니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 지원 기술 자료에서 |
| 검색 문제 | **MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거되었습니다.** 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트 설정과 구성이 있어야 합니다. 개발자 설명서에서 Elasticsearch 설치 및 구성 을 참조하십시오. | [Elasticsearch 서비스 설정](https://devdocs.magento.com/cloud/project/services-elastic.html) 개발자 설명서에서 를 참조하십시오. |
| 사용자 지정 오류 | **피크 시간 동안 배포하지 마십시오.** 사용자를 추가하고 제거하면 배포가 트리거됩니다. | [다운타임 없이 구축](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 개발자 설명서에서 를 참조하십시오. |
| 데이터베이스 오류 및 문제 | **데이터베이스 문제로 인해 배포(후크 후 문제), 성능 및 사이트 다운 상황이 발생합니다.** 많은 경우 오류 또는 데이터베이스 공간 할당이 부족합니다. | [MariaDB 오류 코드](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [저장소 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (데이터베이스 포함)을 개발자 설명서에서 확인할 수 있습니다. |
| 구성 문제 | **저장 시 인덱스 대신 예약별 색인입니다.** 가장 효율적인 인덱싱 구성입니다. 저장 시 색인으로 인해 전체 재색인화가 발생합니다. | [인덱서 구성](../../../configuration/cli/manage-indexers.md#configure-indexers) 개발자 설명서에서 를 참조하십시오. |
| 사용자 지정 코드 문제 | **완료하는 데 시간이 너무 오래 걸리는 프로세스를 식별하고 종료할 수 있는 기회를 보려면 느린 쿼리 로그를 확인하십시오.** 느린 쿼리로 인해 데이터베이스 교착 상태가 발생하여 사이트 다운과 성능 문제가 발생할 수 있습니다. | [MySQL에서 느린 쿼리 및 프로세스를 확인하는 동안 시간이 너무 오래 걸립니다](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 확장 문제 | **현재 Commerce Marketplace에서 확인된 확장만 사용합니다.** | [Adobe Commerce용 확장](https://marketplace.magento.com/extensions.html) |
| 리소스 문제 | **사용 가능한 메모리 및 공간을 모니터링하고 스토리지를 최적화합니다.** 중요한 리소스(예: 배포)를 사용하는 작업 전에 사용 가능한 공간이 있을 수 있습니다. 파일 저장 공간 최적화(예: 너무 많은 대용량, 풍부한 이미지)가 제대로 최적화되지 않아 공간이 부족해질 수 있습니다. 낮은 리소스로 인해 성능 문제, 사이트 작동 중지, 구축 중단 및 배포 오류가 발생합니다. | [디스크 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 개발자 설명서에서 다음을 참조하십시오. [파일 저장 공간 부족/소진, 특정 페이지 로드 속도가 느림](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 지원 기술 자료에서 |
