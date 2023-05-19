---
title: 크론 작업
description: 크론 그룹 및 사용자 지정 크론 작업 만들기에 대해 알아봅니다.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# 크론 작업

이 항목에서는 사용자 정의 cron 작업 및 선택적으로 사용자 정의 cron 그룹을 설정하는 방법에 대해 설명합니다. Commerce 확장을 정기적으로 실행해야 하는 경우 이러한 항목을 사용하여 cron을 설정할 수 있습니다 _작업_ (예약된 작업) 및 cron(옵션) _그룹_- 사용자 지정 작업을 동시에 실행합니다.

Commerce에서 제공한 cron 그룹을 사용하는 경우 사용자 정의 cron 그룹을 정의할 필요가 없습니다. 그러나 cron 작업을 다른 일정으로 실행하거나 모두 함께 실행하려면 cron 그룹을 정의해야 합니다

Commerce 응용 프로그램은 다음 cron 그룹을 제공합니다.

- `default`: 대부분의 cron 작업이 포함되어 있습니다
- `index`, 새로 고침 [인덱서](../cli/manage-indexers.md)
- `consumers`: 메시지 큐를 실행합니다. [소비자](../cli/start-message-queues.md)
- 이 주제들은 Adobe Commerce에서만 사용할 수 있습니다
   - `staging`, 실행 [스테이징 관련](https://docs.magento.com/user-guide/cms/content-staging.html) 작업
   - `catalog_event`타겟 및 장바구니 규칙에 대한 작업을 실행하는
