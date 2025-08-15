---
title: ' [!DNL Cron] 탭'
description: ' [!DNL Cron] 의  [!DNL Observation for Adobe Commerce]탭에 대해 알아봅니다.'
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# [!DNL Cron] 탭

이 탭은 문제 및 [!DNL cron] 문제의 원인을 신속하게 파악하기 위한 것입니다.

## [!UICONTROL Cron transaction duration in seconds]

![크론 트랜잭션 기간(초)](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]** 프레임에 [!DNL crons] 트랜잭션 기간이 초 단위로 표시됩니다. 런타임이 긴 트랜잭션을 표시합니다. APM에 대해 자세히 알아보면 트랜잭션/작업이 실행 중일 수 있는 쿼리에 대한 자세한 정보를 알 수 있습니다.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads by Node](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

**[!UICONTROL MySQL Non-Sleeping Threads by Node]** 프레임은 선택한 기간 동안 노드별로 MySQL 비절전 모드 스레드를 표시합니다.

## [!UICONTROL SQL Trace count by path]

경로별 ![SQL 추적 수](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

**[!UICONTROL SQL Trace count by path]** 프레임은 경로별로 MySQL 추적 수를 살펴봅니다. 이렇게 하면 선택한 기간 동안 SQL 문을 추적하는 데 도움이 될 수 있습니다.

## [!UICONTROL Cron database call]

![크론 데이터베이스 호출](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

**[!UICONTROL Cron database call]** 프레임은 선택한 기간 동안 데이터베이스에 대해 호출하는 [!DNL crons]의 수를 봅니다.

## [!UICONTROL Cron schedule table locks]

![크론 일정 테이블 잠금](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

**[!UICONTROL Cron schedule table locks]** 프레임은 선택한 기간 동안 [!DNL cron] 일정 테이블 잠금을 봅니다.

## [!UICONTROL Cron schedule clean cron fired]

![크론 일정 테이블 잠금](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

**[!UICONTROL Cron schedule clean cron fired]** 프레임은 선택한 기간 동안 정리된 [!DNL crons]의 수를 봅니다. 이 프레임에 데이터가 표시되지 않으면 [!DNL crons]이(가) 올바르게 실행되는 데 문제가 있을 수 있습니다. [!DNL cron] 작업 일정이 정리되지 않으면 [!DNL crons]이(가) 최적으로 실행되지 않으며 실행하는 데 더 오래 걸릴 수 있습니다.

## [!UICONTROL Cron schedule clean records details table]

![크론 일정 정리 레코드 세부 정보 테이블](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

**[!UICONTROL Cron schedule clean records details table]** 테이블은 선택한 일정 동안 `cron_schedule` 테이블에서 레코드를 정리하는 작업에 대한 세부 정보를 제공합니다.

## [!UICONTROL cron_schedule table updates]

![cron_schedule 테이블 업데이트](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

**[!UICONTROL cron_schedule table updates]** 프레임은 선택한 기간 동안 [!DNL cron]개의 예약된 테이블 업데이트 횟수를 봅니다. 이 테이블의 삭제 또는 업데이트에 대한 활동이 높으면 [!DNL crons]에 문제가 있을 수 있습니다. 또한 [!DNL crons]은(는) 실행 및 완료 시 이 테이블을 업데이트하므로 이 테이블에 활동이 없고 구성된 [!DNL crons]이(가) 있으면 [!DNL crons]에 문제가 있을 수 있습니다.

## [!UICONTROL Datastore Operations Tables]

![데이터 저장소 작업 테이블](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]**&#x200B;이(가) 선택한 기간에 대해 `SELECT`, `DELETE` 및 `UPDATE`을(를) 포함한 데이터베이스 테이블 작업을 봅니다. 이 프레임에서는 데이터베이스 테이블에 대한 작업 빈도가 가장 높은 데이터베이스 테이블을 보여 줍니다.
