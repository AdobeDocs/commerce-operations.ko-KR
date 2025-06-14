---
title: '[!DNL RabbitMQ] 탭'
description: ' [!DNL Observation for Adobe Commerce]의 [!DNL RabbitMQ] 탭에 대해 알아봅니다.'
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# [!UICONTROL [!DNL RabbitMQ]] 탭

**[!UICONTROL [!DNL RabbitMQ]]** 탭에 [!DNL RabbitMQ] 신호에 초점을 맞춘 정보가 있습니다.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 인프라 이벤트](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 프레임에는 선택한 기간 동안 발생한 [!DNL RabbitMQ]과(와) 관련된 인프라 이벤트가 표시됩니다.

* `unexpected_resp_node1`(으)로 `%Response [error] for node [rabbit@host1]: unexpected http response from%`)
* `unexpected_resp_node2`(으)로 `%Response [error] for node [rabbit@host2]: unexpected http response from%`)
* `unexpected_resp_node3`(으)로 `%Response [error] for node [rabbit@host3]: unexpected http response from%`)
* `node3_timeout_exceeded`(으)로 `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`)
* `node1_timeout_exceeded`(으)로 `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`)
* `node2_timeout_exceeded`(으)로 `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`)
* `401_unauth`(으)로 `%401 Unauthorized%`)
* `401_unauth`(으)로 `%401 Unauthorized%`)
* `rmq_service_restart`(으)로 `%Service restarted: rabbitmq-server%`)
* `rmq_node1_down`(으)로 `%Response [failed] for node [rabbit@host1]: nodedown%`)
* `rmq_node2_down`(으)로 `%Response [failed] for node [rabbit@host2]: nodedown%`)
* `rmq_node2_down`(으)로 `%Response [failed] for node [rabbit@host2]: nodedown%`)
* `rmq_entity_modified`(으)로 `%Entity modified: exchange/bindings.destination%`)
* `rmq_entity_modified`(으)로 `%Entity modified: exchange/bindings.destination%`)
* `%Entity modified: queue/exclusive%`)을(를) `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`(으)로 `rmq_entity_q_delete`(으)로
* `rmq_entity_modified_q_durable`(으)로 `%Entity modified: queue/durable%`)
* `rmq_entity_modified_ver_mgt`(으)로 `%Entity modified: version/management%`)
* `rmq_entity_modified_ver_mgt`(으)로 `%Entity modified: version/management%`)

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 서비스 시작/중지 신호](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

이 프레임에는 선택한 일정 동안 발생한 [!DNL RabbitMQ]개의 서비스 시작/중지 신호가 표시됩니다.

* `rabbitmq_stop`(으)로 `%RabbitMQ is asked to stop...%`)
* `rabbitmq_start`(으)로 `%Starting RabbitMQ%`)

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ]개 오류](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

이 프레임에는 선택한 기간 동안 발생한 [!DNL RabbitMQ]개의 오류가 표시됩니다.

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}`을(를) `exit_timeout`(으)로
* `client_closed_tcp_conn`(으)로 `%client unexpectedly closed TCP connection%`)
* `undef_exit`(으)로 `%at undefined exit with reason shutdown in context shutdown_error%`)
* `disallowed_node`(으)로 `%Connection attempt from disallowed node%`)
* `rmq_err_amqp_conn`(으)로 `%closing AMQP connection%`)

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 노드 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `rmq_node1_down`(으)로 `%rabbit on node rabbit@host1 down%`)
* `rmq_node2_down`(으)로 `%rabbit on node rabbit@host2 down%`)
* `rmq_node3_down`(으)로 `%rabbit on node rabbit@host3 down%`)
* `rmq_node1_up`(으)로 `%rabbit on node rabbit@host1 up%`)
* `rmq_node2_up`(으)로 `%rabbit on node rabbit@host2 up%`)
* `rmq_node3_up`(으)로 `%rabbit on node rabbit@host3 up%`)

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

대기열별 ![[!DNL RabbitMQ] 메시지 높은 수준의 요약 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 그래프는 선택한 기간에 대해 [!DNL RabbitMQ] 큐에서 게시한 메시지 수를 보여줍니다.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 메시지 세부 정보 요약](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `queue_err`(으)로 `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)
* `queue_err`(으)로 `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)
* `auth`(으)로 `%authenticated and granted access to vhost%`)
* `close_conn`(으)로 `%closing AMQP connection%`)

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 큐 사용량 MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 그래프는 선택한 기간 동안 각 [!DNL RabbitMQ] 큐에서 사용한 바이트 수를 보여 줍니다.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

대기열별 게시된 메시지 ![[!DNL RabbitMQ]개](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 그래프는 선택한 기간 동안 각 [!DNL RabbitMQ] 큐에서 사용한 바이트 수를 보여 줍니다.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

대기열별 ![[!DNL RabbitMQ] 게시된 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 그래프는 선택한 기간 동안 각 [!DNL RabbitMQ] 큐의 초당 평균 게시된 메시지 수를 보여줍니다.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

큐별 총 ![[!DNL RabbitMQ]개 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 그래프는 선택한 기간 동안 각 [!DNL RabbitMQ] 큐의 초당 평균 총 메시지 수를 보여 줍니다.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

대기열별 소비자 ![[!DNL RabbitMQ]명](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 그래프는 선택한 기간 동안 각 [!DNL RabbitMQ] 큐의 평균 총 소비자 수를 보여줍니다.
