---
title: 다음 [!UICONTROL [!DNL RabbitMQ]] 탭
description: 에 대해 알아보기 [!UICONTROL [!DNL RabbitMQ]] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 다음 [!UICONTROL [!DNL RabbitMQ]] 탭

다음 **[!UICONTROL [!DNL RabbitMQ]]** 탭에는 다음과 같은 중요 정보가 있습니다. [!DNL RabbitMQ] 신호.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 인프라 이벤트](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 이 프레임에는 [!DNL RabbitMQ] 이(가) 선택한 기간에 발생했습니다.

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) as `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) as `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) as `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) as `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) as `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) as `node2_timeout_exceeded`
* `%401 Unauthorized%`) as `401_unauth`
* `%401 Unauthorized%`) as `401_unauth`
* `%Service restarted: rabbitmq-server%`) as `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) as `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) as `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) as `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) as `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 서비스 시작/중지 신호](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

이 프레임은 다음을 표시합니다. [!DNL RabbitMQ] 선택한 일정 동안 발생한 서비스 시작/중지 신호:

* `%RabbitMQ is asked to stop...%`) as `rabbitmq_stop`
* `%Starting RabbitMQ%`) as `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 오류](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

이 프레임은 다음을 표시합니다. [!DNL RabbitMQ] 선택한 일정 동안 발생한 오류:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` 다음으로: `exit_timeout`
* `%client unexpectedly closed TCP connection%`) as `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) as `undef_exit`
* `%Connection attempt from disallowed node%`) as `disallowed_node`
* `%closing AMQP connection%`) as `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 노드 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) as `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) as `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) as `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) as `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) as `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) as `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 대기열별 메시지 상위 수준 요약 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 그래프는 게시한 메시지의 수를 [!DNL RabbitMQ] 선택한 일정에 대한 큐에 추가합니다.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 메시지 세부 사항 요약](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%authenticated and granted access to vhost%`) as `auth`
* `%closing AMQP connection%`) as `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 대기열 사용량(MB)](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 그래프는 각 사용자가 사용한 바이트 수를 보여 줍니다 [!DNL RabbitMQ] 선택한 기간 동안 큐에 추가합니다.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 대기열별 게시된 메시지](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 그래프는 각 사용자가 사용한 바이트 수를 보여 줍니다 [!DNL RabbitMQ] 선택한 기간 동안 큐에 추가합니다.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 대기열별 게시된 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 그래프는 초당 평균 게시된 메시지 수를 보여줍니다. [!DNL RabbitMQ] 선택한 기간 동안 큐에 추가합니다.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] 대기열별 총 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 그래프는 초당 평균 총 메시지 수를 보여줍니다. [!DNL RabbitMQ] 선택한 기간 동안 큐에 추가합니다.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] 대기열별 소비자](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 그래프는 각 소비자에 대한 평균 총 소비자 수를 보여줍니다 [!DNL RabbitMQ] 선택한 기간 동안 큐에 추가합니다.
