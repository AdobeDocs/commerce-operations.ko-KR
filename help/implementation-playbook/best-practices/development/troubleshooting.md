---
title: 문제 해결 우수 사례
description: Adobe Commerce 구현 문제를 해결하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 문제 해결 우수 사례

클라우드 인프라 문제에 대한 Adobe Commerce의 효과적인 문제 해결을 위해 다음 모범 사례를 따르십시오.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce

## 우수 사례

| 문제 유형 | 우수 사례 | 리소스 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 배포 문제 | **배포 모범 사례를 따르십시오.** 13%의 지원 티켓에 배포 문제가 포함되어 있습니다. 모범 사례는 이러한 원인 중 많은 것을 방지하는 방법을 포함하도록 업데이트되었습니다. | [빌드 및 배포에 대한 우수 사례](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 개발자 설명서에서 확인할 수 있습니다. |
| 사이트 다운 문제 | **사이트 작동 중지 문제 해결사를 사용합니다.** 크롱은 오래 달릴 수 있고 서로 오버런할 수 있습니다. 많은 중단과 성능 문제의 원인이 됩니다. | [사이트 작동 중지 문제 해결사](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) 및 [cron 작업을 재설정하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 을 참조하십시오. |
| 성능 문제 | **Adobe Commerce 배너를 사용하지 않는 경우 비활성화합니다.** 배너가 활성화되었지만 사용되지 않는 경우 리소스가 필요하지 않은 경우 데이터베이스에 대한 조회를 수행하는 데 사용되며 성능 문제가 발생합니다. | [Adobe Commerce 배너 출력을 비활성화하여 성능 향상](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) 을 참조하십시오. |
| 문제 검색 | **MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거되었습니다.** 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 를 구성해야 합니다. 개발자 설명서에서 설치 및 구성 Elasticsearch 를 참조하십시오. | [Elasticsearch 서비스 설정](https://devdocs.magento.com/cloud/project/services-elastic.html) 개발자 설명서에서 확인할 수 있습니다. |
| 사용자 지정 오류 | **피크 타임에는 배포하지 마십시오.** 사용자를 추가하고 제거하면 배포가 트리거됩니다. | [다운타임 없는 배포](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 개발자 설명서에서 확인할 수 있습니다. |
| 데이터베이스 오류 및 문제 | **데이터베이스 문제로 인해 배포(후크 후 문제), 성능 및 사이트 다운 상황이 발생합니다.** 많은 경우 오류가 발생하거나 데이터베이스 공간 할당이 충분하지 않습니다. | [MariaDB 오류 코드](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [저장소 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (데이터베이스 포함) 을 참조하십시오. |
| 구성 문제 | **저장 시 인덱스 대신 스케줄로 인덱스를 작성합니다.** 이는 가장 효율적인 인덱싱 구성입니다. 저장 시 인덱스로 인해 전체 리인덱싱이 발생합니다. | [인덱서 구성](../../../configuration/cli/manage-indexers.md#configure-indexers) 개발자 설명서에서 확인할 수 있습니다. |
| 사용자 지정 코드 문제 | **느린 쿼리 로그에서 프로세스를 식별하고 완료하는 데 시간이 너무 오래 걸릴 수 있는 기회를 확인하십시오.** 느린 쿼리로 인해 데이터베이스가 교착 상태에 빠지면 사이트 다운 및 성능 문제가 발생할 수 있습니다. | [MySQL에서 느린 쿼리 및 프로세스 확인 시간이 너무 오래 걸림](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 확장 문제 | **현재 Commerce Marketplace에 있는 확인된 확장만 사용합니다.** | [Adobe Commerce용 확장](https://marketplace.magento.com/extensions.html) |
| 리소스 문제 | **사용 가능한 메모리 및 공간을 모니터링하고 스토리지를 최적화합니다.** 중요한 리소스(예: 배포)를 사용하는 작업 전에 사용 가능한 공간이 있을 수 있습니다. 파일 스토리지의 최적화 부진(예: 너무 많은 크고 풍부한 이미지)도 공간 부족의 원인이 될 수 있습니다. 리소스가 부족하면 성능 문제, 사이트 다운, 배포 중단 및 배포 오류가 발생합니다. | [디스크 공간 관리](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 개발자 설명서에서 [파일 스토리지 부족/소진, 특정 페이지 로드 속도가 느림](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) 을 참조하십시오. |
