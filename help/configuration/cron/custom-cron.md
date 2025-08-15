---
title: 크론 작업
description: 크론 그룹 및 사용자 지정 크론 작업 만들기에 대해 알아봅니다.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 크론 작업

이 항목에서는 사용자 정의 cron 작업 및 선택적으로 사용자 정의 cron 그룹을 설정하는 방법에 대해 설명합니다. Commerce 확장을 정기적으로 실행해야 하는 경우 이러한 항목을 사용하여 cron _job_(예약된 작업)과 cron _group_(선택 사항)을 설정할 수 있습니다. 이 작업은 동시에 사용자 지정 작업을 실행합니다.

Commerce에서 제공하는 cron 그룹을 사용하는 경우에는 사용자 정의 cron 그룹을 정의할 필요가 없습니다. 하지만 cron 작업을 다른 일정으로 실행하거나 모두 함께 실행하려면 cron 그룹을 정의해야 합니다

Commerce 애플리케이션은 다음과 같은 cron 그룹을 제공합니다.

- 대부분의 cron 작업이 포함된 `default`
- `index`: [인덱서](../cli/manage-indexers.md)를 새로 고칩니다.
- `consumers`, 메시지 큐 [소비자](../cli/start-message-queues.md)를 실행하는 경우
- 이 주제들은 Adobe Commerce에서만 사용할 수 있습니다
   - `staging`, [스테이징 관련](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging) 작업 실행
   - `catalog_event`, 대상 및 장바구니 규칙에 대한 작업을 실행하는 경우
