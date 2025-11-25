---
title: Adobe Commerce에 대한 관리 경고
description: Adobe Commerce on cloud infrastructure Pro 계획 아키텍처 고객인 경우 관리 경고를 사용하여 사이트 상태를 이해할 수 있습니다. Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 고객인 경우  [!DNL Apdex]  및 오류율 조건에 대한 경고만 받습니다.
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 4560e7d000ad8333c3089b8b5e8ffd25f5d31b67
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Adobe Commerce에 대한 관리 경고


주요 대시보드와 경고를 설정하여 사이트가 중요한 스토리지 및 [!DNL Apdex] 수준(응용 프로그램 및 서비스 응답 시간에 대한 사용자 만족도)에 도달하는 시기를 이해하는 데 도움이 됩니다. 이렇게 하면 응답 시간이 느려지거나 중단이 발생하기 전에 조치를 취하는 데 도움이 될 수 있습니다. 아래 나열된 기사로 경고 문제를 해결할 수 있습니다. 경고를 사용하려면 먼저 알림 채널을 설정하십시오. Commerce on Cloud Guide의 [[!DNL New Relic] 알림 채널 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service)을 참조하십시오.

>[!NOTE]
>
>Adobe Commerce 경고 정책에 대한 관리 경고를 사용할 수 없는 경우 이 계정이 새로 만들어졌거나 [!DNL New Relic]이(가) 최근에 구성되었기 때문일 수 있습니다. 매주 화요일에 해당 계정에 경고 정책을 추가하는 프로세스가 실행됩니다. 다음 프로세스가 실행된 다음 날에 경고 정책을 사용할 수 있습니다. 정책이 여전히 누락된 경우 [Adobe Commerce 지원 요청을 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)하고 프로젝트 ID를 포함하십시오.

이러한 경고에 대한 문제 해결 단계를 제공하는 KB 문서에 대한 링크는 아래 표의 를 참조하십시오.

* Adobe Commerce에 대한 관리 경고: CPU 경고
* Adobe Commerce에 대한 관리 경고: CPU 중요 경고
* Adobe Commerce에 대한 관리 경고: 메모리 경고 경고
* Adobe Commerce에 대한 관리 경고: 메모리 위험 경고
* Adobe Commerce에 대한 관리 경고: [!DNL Apdex] 경고
* Adobe Commerce에 대한 관리 경고: [!DNL Apdex] 중요 경고
* Adobe Commerce에 대한 관리 경고: 디스크 경고 경고
* Adobe Commerce에 대한 관리 경고: 디스크 위험 경고
* Adobe Commerce에 대한 관리 경고: MariaDB 경고
* Adobe Commerce에서 관리되는 경고: [!DNL Redis] 메모리 경고
* Adobe Commerce에서 관리되는 경고: [!DNL Redis] 메모리 위험 경고

>[!NOTE]
>
>경고 경고와 중요 경고 모두에 대한 설정된 임계값은 고객 기반 전반의 과거 성능 데이터를 사용하여 수행한 조사를 기반으로 하며 Adobe Commerce 지원 및 엔지니어링 팀의 최신 통찰력을 나타냅니다. 이러한 임계값은 최신 진행 중인 분석을 기반으로 변경될 수 있습니다. 일반적인 경보 흐름은 심각도 측면에서 경보가 더 낮거나 더 높은 경보를 받는 것이다. 따라서 위기 경보를 받기 전에 경고 경보를 받을 가능성이 높습니다. 문제 해결 단계는 문서 링크를 참조하십시오.

| 심각도 | CPU | 메모리 | 디스크 | [!DNL Apdex] | 마리아DB | [!DNL Redis] 메모리 | 문제 해결 문서 |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| 경고 | ✅ |        |      |       |         |              | [Adobe Commerce에 대한 관리 경고: CPU 경고 경고](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| 중요 | ✅ |        |      |       |         |              | [Adobe Commerce에 대한 관리 경고: CPU 중요 경고](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| 경고 |     | ✅ |      |       |         |              | [Adobe Commerce에 대한 관리 경고: 메모리 경고 경고](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| 중요 |     | ✅ |      |       |         |              | [Adobe Commerce에 대한 관리 경고: 메모리 위험 경고](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| 경고 |     |        |      | ✅ |         |              | [Adobe Commerce에 대한 관리 경고: [!DNL Apdex] 경고](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| 중요 |     |        |      | ✅ |         |              | [Adobe Commerce에 대한 관리 경고: [!DNL Apdex] 중요 경고](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| 경고 |     |        | ✅ |       |         |              | [Adobe Commerce에 대한 관리 경고: 디스크 경고 경고](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| 중요 |     |        | ✅ |       |         |              | [Adobe Commerce에 대한 관리 경고: 디스크 위험 경고](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| 경고 및 위험 |     |        |      |       | ✅ |              | [Adobe Commerce에 대한 관리 경고: MariaDB 경고](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| 경고 |     |        |      |       |         | ✅ | [Adobe Commerce에서 관리되는 경고: [!DNL Redis] 메모리 경고 경고](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| 중요 |     |        |      |       |         | ✅ | [Adobe Commerce에서 관리되는 경고: [!DNL Redis] 메모리 위험 경고](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

## 관리 경고에 대해 설정된 경고 임계값 검토

New Relic 계정의 관리 경고에 대해 구성된 경고 임계값을 검토할 수 있습니다. 지침은 [관리 경고를 사용하여 성능 모니터링](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/investigate/investigate-performance#monitor-performance-with-managed-alerts)을 참조하십시오.
