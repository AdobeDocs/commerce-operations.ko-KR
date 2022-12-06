---
title: "다음 [!UICONTROL [!DNL RabbitMQ]] tab"
description: 에 대해 알아보기 [!UICONTROL [!DNL RabbitMQ]] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: e59b8db21c449fcf91466df7482849a0454bfe3e
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 다음 [!UICONTROL [!DNL RabbitMQ]] 탭

다음 **[!UICONTROL [!DNL RabbitMQ]]** 탭에는 [!DNL RabbitMQ] 신호.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 인프라 이벤트](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 프레임은 [!DNL RabbitMQ] 선택한 기간에 발생한 시간:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) `node2_timeout_exceeded`
* `%401 Unauthorized%`) `401_unauth`
* `%401 Unauthorized%`) `401_unauth`
* `%Service restarted: rabbitmq-server%`) `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 서비스 시작/중지 신호](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

이 프레임은 [!DNL RabbitMQ] 선택한 기간 동안 발생한 서비스 시작/중지 신호:

* `%RabbitMQ is asked to stop...%`) `rabbitmq_stop`
* `%Starting RabbitMQ%`) `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 오류](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

이 프레임은 [!DNL RabbitMQ] 선택한 일정 동안 발생한 오류:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` 로서의 `exit_timeout`
* `%client unexpectedly closed TCP connection%`) `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) `undef_exit`
* `%Connection attempt from disallowed node%`) `disallowed_node`
* `%closing AMQP connection%`) `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 노드 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 대기열별 메시지 개요 상태](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 그래프에는 [!DNL RabbitMQ] 선택한 일정의 큐입니다.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 메시지 세부 정보 요약](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) `queue_err`
* `%authenticated and granted access to vhost%`) `auth`
* `%closing AMQP connection%`) `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 큐 사용량 MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 그래프는 각 사용자가 사용한 바이트 수를 보여줍니다. [!DNL RabbitMQ] 선택한 일정 동안 대기합니다.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 큐에 게시된 메시지](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 그래프는 각 사용자가 사용한 바이트 수를 보여줍니다. [!DNL RabbitMQ] 선택한 일정 동안 대기합니다.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 대기열별 게시된 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 그래프에는 게시된 메시지의 각 초당 평균 수를 보여줍니다 [!DNL RabbitMQ] 선택한 일정 동안 대기합니다.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] 대기열별 총 메시지 처리량](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 그래프는 각 초당 평균 총 메시지 수를 보여줍니다 [!DNL RabbitMQ] 선택한 일정 동안 대기합니다.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] 큐별 소비자](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

다음 **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 그래프에서는 각 소비자의 평균 총 소비자 수를 보여줍니다 [!DNL RabbitMQ] 선택한 일정 동안 대기합니다.
