---
title: 백엔드 성능 최적화
description: Adobe Commerce 사이트의 백엔드 성능을 최적화하는 방법에 대해 알아봅니다.
badge: label="Objectsource에 의해 기여됨" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
source-git-commit: 2416357d8cacb5627fd24f92b16c2d9839f91082
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# 백엔드 성능 최적화에 대한 우수 사례

이 항목에서는 데이터베이스 최적화 및 테스트에 중점을 두고 Adobe Commerce 사이트의 백엔드 성능을 조사 및 최적화하는 모범 사례에 대해 설명합니다. 개발자는 이 정보를 사용하여 각 Commerce 프로젝트의 고유한 컨텍스트를 조사하고 사이트 성능을 개선하기 위해 백엔드 구성 및 작업을 최적화하는 기회를 식별할 수 있습니다.

>[!NOTE]
>
>Recommendations과 예제는 objectsource가 실제 클라이언트 참여에서 따라야 하는 프로세스에 영감을 받아 대규모로 고성능 Adobe Commerce 사이트를 제공합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 성능 향상을 위해 데이터베이스 최적화

데이터베이스 최적화는 사용자 경험을 향상시키고 매출을 증대시키는 확실한 방법입니다. 상거래 사이트의 중추인 데이터베이스를 최적화할 때 웹 사이트 성능 저하를 방지하고 고객의 마찰을 유발하는 긴 로드 시간을 제거할 수 있습니다.

### 스트레스 테스트

블랙 프라이데이와 같이 트래픽이 많이 발생하는 시기에는 상거래 사이트가 대규모 트래픽을 처리해야 합니다. 이러한 사건에 대비하여, 지수 부하 증가 하에서 사이트가 어떻게 작동하는지를 이해하기 위해 스트레스 테스트는 필수적이다.

스트레스 테스트에 사용할 수 있는 한 가지 도구는 GTmetrix 입니다. 일반적인 방문자 행동 및 작업을 복제하고 곱하도록 GTmetrix를 구성하여 로드에 대한 사이트 준비 상태를 측정합니다. 그런 다음 테스트를 실행하여 주요 쇼핑 이벤트 동안 성능 및 사이트 가용성에 영향을 줄 수 있는 문제를 식별하고 해결합니다.

트래픽이 많은 기간에 대한 Commerce 프로젝트 준비에 대해 자세히 알아보십시오.

- [휴일 준비](https://experienceleague.adobe.com/docs/events/mbi-webinars-recordings/2021/holiday-readiness.html)
- [휴일 쇼핑 분석](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [서지 용량 증가](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### 로드 테스트

GTmetrix 또는 이와 유사한 도구를 사용하여 테스트 상거래 프로젝트를 로드할 수도 있습니다. 부하 테스트는 부하 테스트의 전조로서 대규모, 높은 트래픽 사이트의 필수 작업입니다. 최대 로드 상태에서 사이트 성능에 영향을 미치는 문제를 예측 및 완화하여 예기치 않은 사이트 운영 중단, 고객 불만 및 재정적 손실을 방지합니다.

GTmetrix를 사용하여 과도한 트래픽을 시뮬레이션하고 사이트 성능을 분석하여 사이트 용량에 대한 명확한 정보를 얻을 수 있습니다. 이러한 분석은 병목 현상을 식별 및 해결하고 최적화할 수 있는 기회를 식별하는 데 도움이 되며, 이를 통해 상거래 사이트가 부하 증가 시 효과적으로 작동할 수 있도록 합니다.

Adobe Commerce 프로젝트 테스트에 대해 자세히 알아보기:

- [테스트 지침](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (클라우드 인프라)
- [애플리케이션 테스트](https://developer.adobe.com/commerce/testing/guide/)

### 성능 문제 파악 및 해결

New Relic 및 Adobe Commerce용 관찰 과 같은 다양한 도구를 사용하여 병목 현상을 감지하고 상거래 사이트를 효과적으로 최적화하여 성능 문제를 해결합니다. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) 클라우드 인프라의 Adobe Commerce에 포함되어 있으며 [Adobe Commerce 관찰](/help/tools/observation-for-adobe-commerce/intro.md) 클라우드 및 온프레미스 배포에 모두 포함됩니다.

이러한 도구를 사용하여 사이트 성능을 분석하고 다음과 관련된 성능 문제를 식별합니다.

- CPU를 많이 사용하는 기능
- 쿼리 및 백엔드 작업에 대한 캐시 관리 구성
- 서드파티 API 호출
- Cron 스케줄링

예를 들어 제품 세부 사항 및 범주 페이지에 중점을 두고 거래를 면밀히 검사할 수 있습니다. 성능 향상을 위해 최적화할 수 있는 시간 소모적인 프로세스를 파악합니다. 한 고객 참여에서 objectsource는 제품 세부 사항 페이지의 성능 문제를 발견했고 이 결과 성능 시간의 3.5%가 소모되는 API 호출을 발견했습니다. 이 결과를 기반으로 코드 실행 계층 구조를 검사하여 병목 현상을 일으키는 문제를 정확히 찾아내고 해결했습니다.

사이트 성능 관리에 대해 자세히 알아보기:

- [성능 모니터링](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (클라우드 인프라)
- [성능 최적화 검토](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [구성 모범 사례](/help/performance/configuration.md)
- [Adobe Commerce 관찰](/help/tools/observation-for-adobe-commerce/intro.md)

### MySQL 성능 최적화

데이터베이스 클러스터링 및 쿼리 최적화를 구현하여 MySQL 성능 문제를 해결하는 것은 블랙 프라이데이와 같이 트래픽이 많은 시기 전후에 성능을 개선하는 효과적인 방법입니다.

#### 데이터베이스 클러스터링 구현

트래픽이 많은 웹 사이트는 주로 단일 MySQL 서버에 의존하여 데이터베이스 병목 현상을 겪습니다. 성능을 향상시키고 고가용성을 보장하는 분산 아키텍처인 데이터베이스 클러스터링을 구현하여 이러한 병목 현상을 해결할 수 있습니다.

데이터베이스 클러스터링은 여러 웹 노드가 여러 MySQL 서버에 연결할 수 있도록 함으로써 최대 트래픽 기간 동안 데이터베이스 관련 문제의 영향을 최소화합니다. Galera Cluster와 같은 도구를 사용하여 상거래 사이트에 대한 데이터베이스 클러스터링을 설정합니다. Galera Cluster는 [클라우드 인프라에 배포된 Adobe Commerce 프로젝트](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### MySQL 쿼리 최적화

일반적으로 대부분의 Adobe Commerce 사이트의 인프라는 단일 MySQL 서버에 연결된 여러 웹 노드로 구성됩니다.

이 설정에서는 각 프론트엔드 웹 노드가 여러 MySQL 서버를 허용하는 Galera Cluster에 연결됩니다. 프론트엔드 웹 노드의 수를 늘리면 애플리케이션 성능이 향상될 수 있지만, 단일 MySQL 서버는 여전히 병목 현상으로 남아 있습니다.

MySQL 서버 성능을 최적화하고 병목 현상을 최소화하려면 불필요한 쿼리를 식별하고 줄이는 것이 중요합니다. 예를 들어 초당 1,000개의 쿼리를 보내지만 200개만 필요한 경우 쿼리 수를 최적화하고 줄이면 성능이 크게 향상될 수 있습니다.

MySQL 구성 및 최적화에 대해 자세히 알아보기:

- [데이터베이스 구성 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Galera DB 복제를 위한 느린 복제](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [일반 MySQL 지침](/help/installation/prerequisites/database/mysql.md)
- [MySQL 쿼리 캐싱](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## 크론 작업을 효과적으로 관리: 성능 및 시간

Cron 작업은 보고서 생성 및 제품 색인화와 같은 사이트 백그라운드 작업을 처리하는 데 중요한 역할을 합니다. 그러나 cron 작업 최적화는 전체 성능에 미치는 영향을 신중하게 고려해야 합니다. 개발자는 일정 예약 빈도를 평가하고 특정 요구 사항에 따라 최적의 타이밍을 결정해야 합니다.

성능과 편의성의 균형을 맞추려면 트래픽이 적은 기간 동안 cron job을 예약하는 것이 좋습니다. 그러나 시간대가 다른 클라이언트를 처리하는 것은 여러 지역에서 조화로운 경험을 보장하기 위한 사려 깊은 접근 방식을 요구하면서 문제를 초래할 수 있습니다.

cron 성능 및 타이밍을 최적화할 책임이 있는 경우 Commerce 관리자의 현재 cron 구성을 검토하고 Commerce 프로젝트에 대한 cron 작업 설정 및 구성에 대해 알아보십시오.

또한 Adobe Commerce용 관찰 을 사용하여 크론 관련 성과 지표를 볼 수 있습니다. 이 도구는 여러 소스의 로그 데이터를 결합하여 Adobe Commerce 사이트 성능을 더 잘 관리하고 문제를 진단하는 데 도움이 됩니다.

Adobe Commerce cron 구현에 대해 자세히 알아보십시오.

- [크론(예약된 작업)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 다음에서 _Commerce Admin Systems 사용 안내서_
- [애플리케이션 구성 - crons 속성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (클라우드 인프라)
- [크론 구성 및 실행](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (온-프레미스)
- [Adobe Commerce 관찰](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (다음을 참조하십시오. [!UICONTROL Cron] 및 [!UICONTROL MySQL] 탭)
