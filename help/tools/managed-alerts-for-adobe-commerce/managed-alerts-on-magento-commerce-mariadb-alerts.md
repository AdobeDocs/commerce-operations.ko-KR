---
title: 'Adobe Commerce에 대한 관리 경고: MariaDB 경고'
description: 이 문서에서는  [!DNL New Relic]에서 Adobe Commerce에 대한 MariaDB 알림을 받을 때의 문제 해결 단계를 제공합니다. MariaDB 경고는 높은 쿼리 로드와 과도한 DML(데이터 조작어) 쿼리를 모니터링합니다. 둘 다 사용자 경험 저하 또는 다운타임으로 이어질 수 있습니다. 두 종류의 경고를 받을 수 있습니다.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: ccf8b7c5ad1fbef2cfba05f65f05ab8af0375b4c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Adobe Commerce에 대한 관리 경고: MariaDB 경고

이 문서에서는 [!DNL New Relic]에서 Adobe Commerce에 대한 MariaDB 알림을 받을 때의 문제 해결 단계를 제공합니다. MariaDB 경고는 높은 쿼리 로드와 과도한 DML(데이터 조작어) 쿼리를 모니터링합니다. 둘 다 사용자 경험 저하 또는 다운타임으로 이어질 수 있습니다. 두 종류의 경고를 받을 수 있습니다.

* DML 쿼리 경고
* DML 쿼리 위험

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure Pro 계획 아키텍처

## 문제

[Adobe Commerce에 대한 관리 경고](managed-alerts-for-magento-commerce.md)에 등록했으며 경고 임계값 중 하나 이상을 초과한 경우 [!DNL New Relic]에서 관리 경고를 받게 됩니다. 이러한 경고는 지원 및 엔지니어링의 인사이트를 사용하여 고객에게 표준 세트를 제공하기 위해 Adobe에서 개발했습니다.

**실행!**

* 이 경고가 지워질 때까지 예약된 배포를 중단합니다.
* 사이트가 응답하지 않거나 완전히 응답하지 않는 경우 즉시 사이트를 유지 관리 모드로 전환합니다. 단계는 Commerce 설치 가이드의 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)를 참조하십시오. 문제 해결을 위해 사이트에 계속 액세스할 수 있도록 제외 IP 주소 목록에 IP를 추가해야 합니다. 단계는 [제외 IP 주소 목록 유지](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)를 참조하세요.
* 사이트 성능에 영향을 주는 경우 경고의 원인이 될 수 있는 가져오기 등의 스크립트를 종료합니다.

**안 함!**

* MariaDB에 추가 스트레스를 유발할 수 있는 인덱서 또는 추가 크론을 실행합니다.
* 주요 관리 작업(예: Commerce 관리, 데이터 가져오기/내보내기)을 수행합니다.
* 캐시를 지웁니다.

## 솔루션

**DML 쿼리(UPDATE, INSERT 및 DELETE을 사용하여 데이터베이스를 수정하는 쿼리)**

DML 질의 위기 경보를 수신할 경우 1단계에서 시작합니다. DML 질의 경고 경보를 수신할 경우 2단계에서 시작합니다.

1. Adobe Commerce 지원 티켓이 있는지 확인합니다. 단계는 기술 자료 [지원 티켓을 추적](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case)을 참조하세요. 지원이 [!DNL New Relic] 임계값 경고를 받고 티켓을 만들었으며 문제 해결을 시작했을 수 있습니다. 티켓이 없으면 만듭니다. 티켓에는 다음 정보가 있어야 합니다.
   * 연락처 이유: **[!UICONTROL New Relic MariaDB alert received]**&#x200B;을(를) 선택하십시오.
   * 경고에 대한 설명.
   * [[!DNL New Relic] 문제 링크](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). [Adobe Commerce에 대한 관리 경고](managed-alerts-for-magento-commerce.md)에 포함되어 있습니다.
1. 문제의 출처를 식별하려면 DML 쿼리를 식별하십시오.
   1. New Relic [데이터베이스 페이지](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)의 단계를 사용하여 데이터베이스 작업을 검토하십시오.
   1. **[!UICONTROL CALL COUNT]**&#x200B;을(를) 기준으로 정렬한 다음 **[!UICONTROL OPERATION]**&#x200B;을(를) 기준으로 정렬합니다. `INSERT`, `DELETE` 및 `UPDATE` 작업을 검토합니다.
   1. 높은 평균 검색
   1. 데이터베이스 작업 호출자를 찾으려면 클릭스루를 클릭합니다. 이렇게 하면 시간별로 해당 쿼리를 사용하는 트랜잭션이 식별됩니다.
   1. 코드 최적화 또는 운영 최적화를 찾습니다.
      * 코드 최적화: 대량 삽입/업데이트, 색인 사용 최소화 또는 코드 조절 기능을 사용하여 쿼리를 최적화합니다.
      * 운영 최적화: 리소스 집약적인 데이터 수정을 오프로드하여 트래픽 시간을 단축합니다.
      * 추가 최적화: 최신 버전의 ECE-Tools를 사용하고 있는지 확인하십시오. 단계는 Commerce on Cloud 안내서의 [ece-tools 버전 업데이트](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)를 참조하십시오.
