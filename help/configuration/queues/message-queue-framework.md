---
title: 메시지 대기열 개요
description: 메시지 큐 프레임워크와 Adobe Commerce 애플리케이션에서 작동하는 방식을 확인하십시오.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 메시지 대기열 개요

MQF(메시지 대기열 프레임워크)는 모듈이 메시지를 대기열에 게시할 수 있도록 하는 시스템입니다. 또한 비동기적으로 메시지를 받을 [소비자](consumers.md)도 정의합니다. MQF는 [[!DNL RabbitMQ]](https://www.rabbitmq.com)을(를) 메시지 브로커로 사용하며, 메시지 송수신에 확장 가능한 플랫폼을 제공합니다. 게재되지 않은 메시지를 저장하는 메커니즘도 포함됩니다. [!DNL RabbitMQ]은(는) AMQP(고급 메시지 대기열 프로토콜) 0.9.1 사양을 기반으로 합니다.

다음 다이어그램은 메시지 대기열 프레임워크를 보여 줍니다.

![메시지 큐 프레임워크](../../assets/configuration/mq-framework.png)

- 게시자는 교환에 메시지를 보내는 구성 요소입니다. 게시할 교환과 보내는 메시지의 형식을 알고 있습니다.

- 거래소는 게시자로부터 메시지를 수신하여 대기열로 보냅니다. [!DNL RabbitMQ]에서 여러 유형의 교환을 지원하지만 Commerce에서는 주제 교환만 사용합니다. 항목에는 점으로 구분된 텍스트 문자열이 들어 있는 라우팅 키가 포함되어 있습니다. 항목 이름의 형식은 `string1.string2`입니다(예: `customer.created` 또는 `customer.sent.email`).

  브로커를 사용하면 메시지 전달 규칙을 설정할 때 와일드카드를 사용할 수 있습니다. 별표(`*`)를 사용하여 _one_ 문자열을 바꾸거나 파운드 기호(`#`)를 사용하여 0개 이상의 문자열을 바꿀 수 있습니다. 예를 들어 `customer.*`은(는) `customer.create` 및 `customer.delete`을(를) 필터링하지만 `customer.sent.email`은(는) 필터링하지 않습니다. 그러나 `customer.#`은(는) `customer.create`, `customer.delete` 및 `customer.sent.email`을(를) 필터링합니다.

- 큐는 메시지를 저장하는 버퍼입니다.

- 소비자는 메시지를 수신합니다. 소비할 큐를 알고 있습니다. 메시지 처리자를 특정 대기열에 매핑할 수 있습니다.

[!DNL RabbitMQ]을(를) 사용하지 않고 기본 메시지 큐 시스템을 설정할 수도 있습니다. 이 시스템에서는 MySQL 어댑터가 데이터베이스에 메시지를 저장합니다. 세 개의 데이터베이스 테이블(`queue`, `queue_message` 및 `queue_message_status`)이 메시지 큐 작업을 관리합니다. 크론 작업은 소비자가 메시지를 받을 수 있도록 합니다. 이 솔루션은 확장성이 별로 없습니다. 가능하면 항상 [!DNL RabbitMQ]을(를) 사용해야 합니다.
