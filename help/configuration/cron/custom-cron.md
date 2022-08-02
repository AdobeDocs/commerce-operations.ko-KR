---
title: 크론 작업
description: 크론 그룹 및 사용자 지정 크론 작업 만들기에 대해 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# 크론 작업

이러한 항목에서는 사용자 지정 크론 작업을 설정하는 방법과 선택적으로 사용자 지정 크론 그룹을 설정하는 방법에 대해 설명합니다. 상거래 확장을 위해 예약된 작업을 주기적으로 실행해야 하는 경우 이러한 주제를 사용하여 기준을 설정할 수 있습니다 _작업_ (예약된 작업) 및 원할 경우 _그룹_- 사용자 지정 작업을 동시에 실행합니다.

상거래 제공 크론 그룹을 사용하는 경우 사용자 지정 크론 그룹을 정의할 필요가 없습니다. 그러나 cron 작업을 다른 일정에 따라 실행하려면 해당 작업을 모두 함께 실행하려면 콘 그룹을 정의해야 합니다

상거래 애플리케이션은 다음 콘 그룹을 제공합니다.

- `default`- 대부분의 cra 작업을 포함합니다
- `index`, 새로 고침 [인덱서](../cli/manage-indexers.md)
- `consumers`: 메시지 큐를 실행합니다 [소비자](../cli/start-message-queues.md)
- 이러한 항목은 Adobe Commerce에서만 사용할 수 있습니다
   - `staging`를 실행하는 [스테이징 관련](https://docs.magento.com/user-guide/cms/content-staging.html) 작업
   - `catalog_event`target 및 장바구니 규칙에 대한 작업을 실행하는 중
