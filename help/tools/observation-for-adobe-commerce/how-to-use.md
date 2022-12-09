---
title: "사용 방법 [!DNL Observation for Adobe Commerce] nerlet"
description: 사용 방법을 알아봅니다 [!DNL Observation for Adobe Commerce] 너들릿.
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 사용 방법 [!DNL Observation for Adobe Commerce] 너릿

## 문제 보기에 대한 일반적인 접근 방식

환경 리소스 상태 확인:

* %(%)를 검사합니다. **[!UICONTROL Storage Free and MySQL % free storage by node]** 프레임.

   * 낮은 저장소가 표시되면 프레임 헤더에 있는 링크를 따르십시오.

* %(%)를 검사합니다. **[!UICONTROL free system memory and Swap memory free in bytes]** 프레임.

   * 메모리 상태가 매우 낮은 경우 문제에 기여할 수 있습니다.

* 를 검사합니다. **[!UICONTROL Alerts during the timeframe]** 프레임.

   * Adobe Commerce on cloud infrastructure는 다음을 제공합니다 [!DNL Managed alerts]. 헤더에서 링크를 클릭하여 를 볼 수 있습니다 [!DNL Support Knowledge Base] 특정 경고에 대한 부품 작업을 결정하는 데 도움이 되는 문서.

* 를 검사합니다. **[!UICONTROL CPU % by host]** 프레임: CPU 사용률이 높은 경우 [!DNL Support Knowledge Base] 프레임의 헤더에 있는 문서 또한 최대 트래픽 기간 동안 데이터베이스 가져오기/내보내기 또는 백업이 수행되지 않는지 확인하십시오.

* 을(를) 확인합니다. **[!UICONTROL Web Traffic volume compared to one week ago]** 프레임: 트래픽이 동일한 기간 동안 이전 주보다 훨씬 더 높은 경우, 이것을 설명(예를 들어, 마케팅된 판매 캠페인 또는 새로운 제품)할 수 있습니까?
   * 트래픽 증가를 설명할 수 없는 경우 프로덕션 환경에 대한 평균 응답 시간(밀리초)을 확인하십시오. 응답 시간에 기여하는 높은 트래픽이 정상과는 다른 가요? 시간대를 확장하여 예외 항목인지 확인합니다.
   * 트래픽 증가가 웹 트랜잭션에 영향을 줍니까? 을(를) 확인합니다. **[!UICONTROL Response Code]** 프레임 을 참조하십시오. 사이트가 다운된 경우 `Site Down?` 를 프레임 헤더에 연결합니다. 프레임은 발생하는 모든 오류와 해당 빈도를 식별합니다.
   * 다른 사용자가 웹 사이트에 변경 내용을 배포했습니까? 다음 **[!UICONTROL Deployment Log Entries]** 프레임은 문제 기간 동안 모든 배포가 수행되었는지 여부를 나타냅니다. 배포 후 문제가 바로 발생하면 배포 활동이 사이트에 추가 로드를 추가하고 있는 것(캐시 지움, 서비스 다시 시작 등)일 수 있습니다.
   * 업사이즈나 다운사이즈가 발생했습니까? 사이트 크기가 일시적으로 업사이징된 경우 원래 클러스터 크기로 반환되었을 수 있습니다. 사이트 용량을 늘리기 위해 요청이 수행된 경우 크기가 커질 수 있습니다. 을(를) 확인합니다. **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** 프레임. 이 프레임은 때로 특정 노드에서 중단이 감지됩니다. 크기가 줄어든 경우 하나 이상의 노드에 문제가 발생할 수 있습니다.

* 다음 **[!UICONTROL IP Frequency]** 탭에서 은(는) 원본 서버에 대해 수행된 IP 주소에서 요청 빈도를 식별합니다(즉, 이 요청을 처리할 수 없음을 의미합니다 [!DNL Fastly] 74는 캐시되지 않았습니다.)

   * 기타 [!DNL Fastly] 관련 문제, **[!UICONTROL Fastly Cache]** 프레임에서 오류 패싯을 선택하여 오류인 요청의 비율을 확인합니다. 비웹 로드와 일치하는 경우 백엔드 문제를 나타낼 수 있습니다.
   * 로드가 웹 트래픽으로 인해 표시되지 않는 경우 느린 쿼리 또는 와 같은 웹이 아닌 요청의 빌드 또는 오류가 있을 수 있습니다 [!DNL crons].

* 을(를) 확인합니다. **[!UICONTROL Database Errors]** 문제/문제 타임라인과 일치할 수 있는 오류에 대한 프레임.
* 을(를) 확인합니다. **[!UICONTROL Database mysql-slow.log]** 프레임을 사용하여 발생하는 SQL 문을 식별합니다. `INSERT`, `UPDATE`, 및 `DELETE` 쿼리가 최적화되지 않은 경우 명령이 시간이 걸릴 수 있습니다. 짝수 `SELECT` 큰 테이블에 대해 행해지는 경우 진술은 매우 비효율적일 수 있다.
* **[!UICONTROL PHP States]** 및 **[!UICONTROL PHP Errors]** 프레임에 PHP에 발생할 수 있는 문제가 표시됩니다. 다음 **[!UICONTROL PHP States]** 프레임은 PHP 프로세스 종료, 시작 및 서비스가 노드별로 준비 상태에 도달하면 표시됩니다. 다음 **[!UICONTROL PHP Errors]** 프레임은 메모리 크기, 작업자 또는 서버 수와 같이 PHP에서 문제가 발생하는 위치를 격리하는 데 도움이 될 수 있습니다.
* 트랜잭션에서 지연을 보려면 트랜잭션 - 평균, 최대, 최소 테이블을 열별로 정렬하여 가장 오래 실행되는 트랜잭션 기간을 표시할 수 있습니다. 오버로드된 클러스터는 트랜잭션의 지속 시간이 지연되지만, 메서드 또는 [!DNL cron].
* 다음 **[!UICONTROL Cron error]** 프레임이 표시됩니다. [!DNL cron] 잠금, 연결된 SQL 오류 [!DNL cron] 로그 및 공유 스테이징 [!DNL crons] 전용 스테이징 환경이 있는 경우 프로덕션 환경에서 실행될 수 있습니다.
* 다음 [!UICONTROL ElasticSearch Errors] 프레임에는 [!DNL Elasticsearch] 쿼리, 데이터 또는 색인을 참조하십시오.
