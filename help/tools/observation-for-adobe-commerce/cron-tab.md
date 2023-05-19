---
title: 다음 [!DNL Cron] 탭
description: 에 대해 알아보기 [!DNL Cron] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 다음 [!DNL Cron] 탭

이 탭은 의 문제 및 원인을 신속하게 격리하기 위한 시도입니다. [!DNL cron] 문제.

## [!UICONTROL Cron transaction duration in seconds]

![Cron 트랜잭션 기간(초)](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

다음 **[!UICONTROL Cron transaction duration in seconds]** 프레임 표시 [!DNL crons] 트랜잭션 기간(초). 런타임이 긴 트랜잭션을 표시합니다. APM에 대해 자세히 알아보면 트랜잭션/작업이 실행 중일 수 있는 쿼리에 대한 자세한 정보를 알 수 있습니다.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![노드별 MySQL 비휴지 스레드](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

다음 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame은 선택한 기간에 대해 노드별로 MySQL 비휴지 스레드를 보여 줍니다.

## [!UICONTROL SQL Trace count by path]

![경로별 SQL 추적 수](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

다음 **[!UICONTROL SQL Trace count by path]** frame은 MySQL 추적 수를 경로별로 살펴봅니다. 이렇게 하면 선택한 기간 동안 SQL 문을 추적하는 데 도움이 됩니다.

## [!UICONTROL Cron database call]

![Cron 데이터베이스 호출](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

다음 **[!UICONTROL Cron database call]** frame은 [!DNL crons] 선택한 기간 동안 데이터베이스에 대한 호출.

## [!UICONTROL Cron schedule table locks]

![Cron 일정 테이블 잠금](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

다음 **[!UICONTROL Cron schedule table locks]** 프레임 살펴보기 [!DNL cron] 선택한 기간에 대해 일정 테이블 잠금.

## [!UICONTROL Cron schedule clean cron fired]

![Cron 일정 테이블 잠금](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

다음 **[!UICONTROL Cron schedule clean cron fired]** frame은 [!DNL crons] 선택한 기간에 걸쳐 정리되었습니다. 이 프레임에 데이터가 표시되지 않으면 다음과 같은 문제가 발생할 수 있습니다. [!DNL crons] 올바르게 실행 중입니다. 다음과 같은 경우 [!DNL cron] 작업 일정이 정리되지 않았습니다. [!DNL crons] 은 최적으로 실행되지 않으며 실행하는 데 더 오래 걸릴 수 있습니다.

## [!UICONTROL Cron schedule clean records details table]

![Cron 일정 클린 레코드 세부 정보 테이블](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

다음 **[!UICONTROL Cron schedule clean records details table]** 다음은에서 레코드를 정리하는 작업에 대한 세부 정보를 제공합니다. `cron_schedule` 선택한 기간에 걸친 테이블입니다.

## [!UICONTROL cron_schedule table updates]

![cron_schedule 테이블 업데이트](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

다음 **[!UICONTROL cron_schedule table updates]** frame은 [!DNL cron] 예약된 테이블이 선택한 기간에 걸쳐 업데이트됩니다. 이 테이블의 삭제 또는 업데이트에 대한 활동이 높으면 다음 문제가 발생할 수 있습니다. [!DNL crons]. 또한, [!DNL crons] 이 테이블이 실행되고 완료될 때 업데이트되므로 이 테이블에 활동이 없고 [!DNL crons] 구성되었습니다. 문제가 발생할 수 있습니다. [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![데이터 저장소 작업 테이블](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

다음 **[!UICONTROL Datastore Operations Tables]** 다음을 포함한 데이터베이스 테이블 작업을 살펴봅니다. `SELECT`, `DELETE`, 및 `UPDATE` 을(를) 선택해 주십시오. 이 프레임에서는 데이터베이스 테이블에 대한 작업 빈도가 가장 높은 데이터베이스 테이블을 보여 줍니다.
