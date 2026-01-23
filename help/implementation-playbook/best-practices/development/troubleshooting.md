---
title: 문제 해결 우수 사례
description: Adobe Commerce 구현 문제를 해결하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 문제 해결 우수 사례

클라우드 인프라 문제에 대한 Adobe Commerce의 효과적인 문제 해결을 위해 다음 모범 사례를 따르십시오.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce

## 우수 사례

| 문제 유형 | 우수 사례 | 리소스 |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 배포 문제 | **배포 모범 사례를 따릅니다.** 13%의 지원 티켓에 배포 문제가 있습니다. 모범 사례는 이러한 원인 중 많은 것을 방지하는 방법을 포함하도록 업데이트되었습니다. | 개발자 설명서의 [빌드 및 배포에 대한 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices). |
| 사이트 다운 문제 | **사이트 작동 중지 문제 해결사를 사용합니다.** 크론은 실행 시간이 길어질 수 있으며 서로 오버런될 수 있습니다. 많은 중단과 성능 문제의 원인이 됩니다. | 지원 기술 자료에서 [사이트 작동 중지 문제 해결사](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=ko) 및 [cron 작업을 재설정하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=ko)을 참조하십시오. |
| 성능 문제 | **Adobe Commerce 배너를 사용하지 않는 경우 사용하지 않도록 설정하십시오.** 배너를 사용하지만 사용하지 않으면 리소스가 필요하지 않은 경우 데이터베이스에 대한 조회를 수행하는 데 사용되며 성능 문제가 발생합니다. | 지원 기술 자료에서 [성능을 향상시키려면 Adobe Commerce 배너 출력을 사용하지 않도록 설정하십시오](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=ko). |
| 문제 검색 | **MySQL 카탈로그 검색 엔진이 Adobe Commerce 2.4.0에서 제거되었습니다.** 버전 2.4.0을 설치하기 전에 Elasticsearch 호스트를 설정하고 구성해야 합니다. 개발자 설명서에서 Elasticsearch 설치 및 구성 을 참조하십시오. | 개발자 설명서에서 [Elasticsearch 서비스를 설정](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)합니다. |
| 사용자 지정 오류 | **사용량이 많은 시간에는 배포하지 마십시오.** 사용자를 추가하고 제거하면 배포가 트리거됩니다. | 개발자 설명서에서 [가동 중지 시간이 전혀 없습니다](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime). |
| 데이터베이스 오류 및 문제 | **데이터베이스 문제로 인해 배포(후크 후 문제), 성능 및 사이트 중단 상황이 발생했습니다.** 많은 항목에 오류가 있거나 데이터베이스 공간 할당이 충분하지 않습니다. | 개발자 설명서에서 [MariaDB 오류 코드](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-code-reference); [저장소 공간 관리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)&#x200B;(데이터베이스 포함). |
| 구성 문제 | **저장 시 색인 대신 예약으로 색인화** 가장 효율적인 인덱싱 구성입니다. 저장 시 인덱스로 인해 전체 리인덱싱이 발생합니다. | 개발자 설명서에서 [인덱서를 구성](../../../configuration/cli/manage-indexers.md#configure-indexers)합니다. |
| 사용자 지정 코드 문제 | **느린 쿼리 로그에서 프로세스를 식별하는 기회를 확인하고 완료하는 데 시간이 너무 오래 걸릴 수 있습니다.**&#x200B;개의 느린 쿼리로 인해 데이터베이스가 교착 상태에 빠져 사이트 다운 및 성능 문제가 발생할 수 있습니다. | [MySQL에서 느린 쿼리 및 프로세스 확인 중](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=ko) |
| 확장 문제 | **현재 Commerce Marketplace에서 확인된 확장 프로그램만 사용합니다.** | Adobe Commerce용 [확장](https://commercemarketplace.adobe.com//extensions.html) |
| 리소스 문제 | **사용 가능한 메모리 및 공간을 모니터링하고 저장소를 최적화합니다.** 상당한 리소스를 사용하는 작업(예: 배포) 전에 사용 가능한 공간이 있을 수 있습니다. 파일 스토리지의 최적화 부진(예: 너무 많은 크고 풍부한 이미지)도 공간 부족의 원인이 될 수 있습니다. 리소스가 부족하면 성능 문제, 사이트 다운, 배포 중단 및 배포 오류가 발생합니다. | 개발자 설명서에서 [디스크 공간 관리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space); 지원 기술 자료에서 [파일 저장소 부족/소진, 특정 페이지 로드 속도가 느림](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=ko). |
