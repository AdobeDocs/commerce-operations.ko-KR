---
title: ' [!DNL Observation for Adobe Commerce] nerdlet을 사용하는 방법'
description: ' [!DNL Observation for Adobe Commerce] nerdlet을 사용하는 방법을 알아봅니다.'
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# [!DNL Observation for Adobe Commerce] Nerdlet을 사용하는 방법

## 일반적인 문제 확인 방법

환경 리소스 상태 확인:

* **[!UICONTROL Storage Free and MySQL % free storage by node]**&#x200B;개 프레임의 비율을 검사합니다.

   * 저장 공간이 부족하면 프레임 헤더에 있는 링크를 따르십시오.

* **[!UICONTROL free system memory and Swap memory free in bytes]**&#x200B;개 프레임의 비율을 검사합니다.

   * 이러한 메모리 상태가 매우 낮으면 문제의 원인이 될 수 있습니다.

* **[!UICONTROL Alerts during the timeframe]** 프레임을 검사합니다.

   * 클라우드 인프라의 Adobe Commerce에서 [!DNL Managed alerts]을(를) 제공합니다. 헤더의 링크를 클릭하면 특정 경고에 대한 작업을 결정하는 데 도움이 되는 [!DNL Support Knowledge Base]개의 문서를 볼 수 있습니다.

* **[!UICONTROL CPU % by host]** 프레임을 검사합니다. CPU 사용률이 높은 경우 헤더의 [!DNL Support Knowledge Base] 문서에서 프레임을 확인하십시오. 또한 트래픽 피크 기간 동안 데이터베이스 가져오기/내보내기 또는 백업이 수행되지 않는지 확인하십시오.

* **[!UICONTROL Web Traffic volume compared to one week ago]** 프레임 확인: 같은 기간 동안 이전 주보다 트래픽이 훨씬 높은 경우 이에 대해 설명할 수 있습니까(예: 판매 캠페인 또는 마케팅된 새 제품)?
   * 트래픽 증가를 설명할 수 없는 경우 프로덕션 환경의 평균 응답 시간(밀리초)을 확인합니다. 응답 시간에 기여하는 트래픽이 높을수록 일반적인 트래픽과 다릅니까? 시간대를 확장하여 예외 항목인지 확인합니다.
   * 트래픽 증가가 웹 트랜잭션에 영향을 줍니까? **[!UICONTROL Response Code]** 프레임에서 오류를 확인합니다. 사이트가 다운된 경우 프레임 헤더의 `Site Down?` 링크를 클릭할 수 있습니다. 프레임은 발생하는 모든 오류와 그 빈도를 식별합니다.
   * 누군가가 귀하의 웹 사이트에 변경 사항을 배포했습니까? **[!UICONTROL Deployment Log Entries]** 프레임은 문제 일정 동안 배포가 수행되었는지 여부를 나타냅니다. 배포 직후에 문제가 발생하면 배포 활동이 사이트에 추가 로드(캐시 지우기, 서비스 다시 시작 등)를 추가하고 있을 수 있습니다.
   * 업사이징이나 다운사이징이 발생했습니까? 사이트가 일시적으로 업사이징된 경우 원래 클러스터 크기로 반환되었을 수 있습니다. 사이트 용량을 늘려야 한다는 요청이 있으면 업사이징이 발생할 수 있습니다. **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 프레임을 확인하십시오. 이 프레임은 때로 하나의 특정 노드에서 중단을 감지합니다. 크기가 감소하면 하나 이상의 노드에 문제가 있을 수 있습니다.

* **[!UICONTROL IP Frequency]** 탭은 원본 서버에 대해 수행된 IP 주소에서 요청 빈도를 식별합니다(즉, [!DNL Fastly]에서 캐시되지 않은 요청이 74로 제공될 수 없음).

   * [!DNL Fastly] 관련 문제에 대해 **[!UICONTROL Fastly Cache]** 프레임을 확인하고 오류 패싯을 선택하여 오류인 요청의 비율을 확인합니다. 비웹 로드와 일치하는 경우 백엔드 문제를 나타낼 수 있습니다.
   * 웹 트래픽으로 인해 로드가 발생하지 않는 경우 느린 쿼리 또는 [!DNL crons]과 같은 비웹 요청의 빌드업이나 오류가 발생할 수 있습니다.

* 문제/문제 타임라인과 일치할 수 있는 오류에 대해서는 **[!UICONTROL Database Errors]** 프레임을 확인하십시오.
* 발생하는 SQL 문을 식별하려면 **[!UICONTROL Database mysql-slow.log]** 프레임을 확인하십시오. 쿼리가 최적화되지 않은 경우 `INSERT`, `UPDATE` 및 `DELETE` 명령에 시간이 걸릴 수 있습니다. 큰 테이블에 대해 `SELECT` 문을 수행하면 매우 비효율적일 수 있습니다.
* **[!UICONTROL PHP States]** 및 **[!UICONTROL PHP Errors]** 프레임에 PHP에 문제가 있을 수 있습니다. **[!UICONTROL PHP States]** 프레임에는 PHP 프로세스가 종료되고 시작되며 서비스가 노드별로 준비 상태에 도달하면 표시됩니다. **[!UICONTROL PHP Errors]** 프레임을 사용하면 메모리 크기, 작업자 또는 서버 수와 같은 PHP에서 문제가 발생하는 위치를 파악할 수 있습니다.
* 트랜잭션 지연을 보려면, 가장 오래 실행되는 트랜잭션 기간을 표시하기 위해 Transactions - Avg, Max, Min 테이블을 열별로 정렬할 수 있습니다. 오버로드된 클러스터에는 트랜잭션에 지연 기간이 있지만 메서드나 [!DNL cron]에 문제가 있는 것을 찾아낼 수 있는 예외 항목도 표시됩니다.
* **[!UICONTROL Cron error]** 프레임에는 [!DNL cron]개의 잠금, [!DNL cron]개의 로그와 관련된 SQL 오류 및 전용 스테이징 환경이 있을 때 프로덕션 환경에서 실행 중일 수 있는 공유 스테이징 [!DNL crons]이(가) 표시됩니다.
* [!UICONTROL ElasticSearch Errors] 프레임에 [!DNL Elasticsearch] 쿼리, 데이터 또는 인덱스와 관련된 주요 문제를 나타낼 수 있는 오류가 표시됩니다.
