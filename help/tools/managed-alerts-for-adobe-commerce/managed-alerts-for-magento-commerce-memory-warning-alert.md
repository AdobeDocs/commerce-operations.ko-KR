---
title: 'Adobe Commerce에 대한 관리 경고: 메모리 경고 경고'
description: 이 문서에서는  [!DNL New Relic]에서 Adobe Commerce에 대한 메모리 경고 알림을 받는 경우의 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 54cb28acd9e930cc915f2ab1bf04cfc61d08663c
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Adobe Commerce에 대한 관리 경고: 메모리 경고 경고

이 문서에서는 [!DNL New Relic]에서 Adobe Commerce에 대한 메모리 경고 알림을 받는 경우에 대한 문제 해결 단계를 제공합니다. 문제를 해결하기 위해 즉각적인 조치가 필요합니다. 선택한 경고 알림 채널에 따라 경고는 다음과 같이 표시됩니다.

![메모리 경고](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처

## 문제

[Adobe Commerce에 대한 관리 경고](managed-alerts-for-magento-commerce.md)에 등록했으며 경고 임계값 중 하나 이상을 초과한 경우 [!DNL New Relic]에서 경고를 받게 됩니다. 이러한 경고는 지원 및 엔지니어링의 인사이트를 사용하여 고객에게 표준 세트를 제공하기 위해 Adobe Commerce에서 개발했습니다.

<u>**실행!**</u>:

* 이 경고가 지워질 때까지 예약된 배포를 중단하는 것이 좋습니다.
* 사이트가 응답하지 않거나 완전히 응답하지 않는 경우 즉시 사이트를 유지 관리 모드로 전환합니다. 단계는 Commerce 설치 가이드의 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)를 참조하십시오. 문제 해결을 위해 사이트에 계속 액세스할 수 있도록 제외 IP 주소 목록에 IP를 추가해야 합니다. 단계는 Commerce 설치 가이드의 [제외 IP 주소 목록 유지](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)를 참조하십시오.

<u>**안 함!**</u>:

* 사이트에 추가 페이지 보기를 가져올 수 있는 추가 마케팅 캠페인을 시작합니다.
* 인덱서 또는 추가 크론을 실행하여 CPU 또는 디스크에 추가 스트레스를 발생시킬 수 있습니다.
* 주요 관리 작업(예: 관리자, 데이터 가져오기/내보내기)을 수행합니다.
* 캐시를 지웁니다.

## 솔루션

다음 단계에 따라 원인을 식별하고 해결하십시오.

1. [[!DNL New Relic] APM의 인프라 페이지](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)를 사용하여 메모리 사용량이 가장 많은 프로세스를 식별합니다. 단계는 [[!DNL New Relic] [인프라 모니터링 호스트 페이지: [!UICONTROL Processes] 탭]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)을 참조하십시오. [!DNL Redis] 또는 MySQL과 같은 서비스가 메모리 사용의 최상위 소스인 경우 다음을 시도하십시오.

   * 최신 버전을 사용하고 있는지 확인하십시오. 최신 버전은 경우에 따라 메모리 누수를 해결할 수 있습니다. 최신 버전을 사용하고 있지 않다면 업그레이드를 고려해 보십시오. 단계는 Commerce on Cloud Guide의 [서비스 변경](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하세요.
   * 증가된 메모리 사용량의 원인을 여전히 식별할 수 없는 경우 오래 실행되는 쿼리, 기본 키가 정의되지 않음 및 중복 인덱스와 같은 MySQL 문제를 확인하십시오. 단계는 Commerce 구현 플레이북의 [클라우드 인프라에서 Adobe Commerce의 가장 일반적인 데이터베이스 문제](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)를 참조하십시오.
   * MySQL 문제가 없으면 PHP 문제를 확인합니다. CLI/터미널에서 `ps aufx`을(를) 실행하여 실행 중인 프로세스를 검토하십시오. 터미널 출력에는 현재 실행 중인 cron job 및 process가 표시됩니다. 프로세스의 실행 시간에 대한 출력을 확인합니다. 실행 시간이 긴 크론이 있는 경우 크론이 걸려있을 수 있습니다. 문제 해결 단계는 Commerce 지원 기술 자료에서 [성능이 느리고 실행 중인 크론](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) 및 [실행 중인 크론 작업이 중단 상태](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status)를 참조하십시오.

1. 여전히 문제의 원인을 식별하기가 어려운 경우 [[!DNL New Relic] APM의 트랜잭션 페이지](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)를 사용하여 성능 문제가 있는 트랜잭션을 식별하십시오.

   * 오름차순 [!DNL Apdex] 점수로 트랜잭션을 정렬합니다. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)은(는) 웹 응용 프로그램 및 서비스의 응답 시간에 대한 사용자 만족도를 나타냅니다. [낮음 [!DNL Apdex] 점수](managed-alerts-for-magento-commerce-apdex-warning-alert.md)는 병목 현상(응답 시간이 더 긴 트랜잭션)을 나타낼 수 있습니다. 일반적으로 데이터베이스, [!DNL Redis] 또는 PHP입니다. 단계는 New Relic [가장 높은 트랜잭션 보기 [!DNL Apdex] 불만](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)를 참조하세요.
   * 가장 높은 처리량, 가장 느린 평균 응답 시간, 가장 많은 시간이 소요되는 임계값 및 기타 임계값별로 트랜잭션을 정렬합니다. 단계는 [[!DNL New Relic] 특정 성능 문제 찾기](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)를 참조하세요. 여전히 문제를 확인하기 어려운 경우 [[!DNL New Relic] APM의 인프라 페이지](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)를 사용하십시오.

1. 메모리 사용량 증가의 원인을 파악할 수 없는 경우 최근 트렌드를 검토하여 최근 코드 배포 또는 구성 변경과 관련된 문제(예: 새로운 고객 그룹 및 카탈로그에 대한 대규모 변경)를 파악하십시오. 코드 배포 또는 변경 시 상관 관계에 대한 지난 7일간의 활동을 검토하는 것이 좋습니다.

1. 위의 방법이 적절한 시간 내에 원인 및/또는 해결책을 찾는 데 도움이 되지 않는 경우 업사이징을 요청하거나 아직 이 사이트를 유지 관리 모드로 전환하십시오. 단계는 Commerce 지원 기술 자료에서 [임시 크기 조정 요청 방법](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) 및 Commerce 설치 안내서에서 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)를 참조하십시오.

1. 업사이징이 사이트를 정상 작업으로 반환하는 경우 영구 업사이징을 요청하거나(Adobe 계정 팀에 문의), 로드 테스트를 실행하고 쿼리 또는 서비스 압력을 줄이는 코드를 최적화하여 전용 스테이징에서 문제를 재현해 보십시오. Commerce on Cloud Guide의 [부하 및 부하 테스트](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)를 참조하십시오.
