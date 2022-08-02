---
title: 메시지 큐 개요
description: 메시지 큐 프레임워크 및 Adobe Commerce 및 Magento Open Source 애플리케이션에서 메시지 큐 작동 방식에 대해 읽어보십시오.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# 메시지 큐 개요

MQF(메시지 큐 프레임워크)는 [모듈](https://glossary.magento.com/module) 메시지를 큐에 게시하려면 또한 비동기식으로 메시지를 받을 소비자를 정의합니다. MQF는 [RabbitMQ](http://www.rabbitmq.com) 메시지 전송 및 수신을 위한 확장 가능한 플랫폼을 제공하는 메시징 브로커 또한, 배달되지 않은 메시지를 저장하는 메커니즘이 포함된다. RabbitMQ는 AMQP(Advanced Message Queuing Protocol) 0.9.1 사양을 기반으로 합니다.

다음 다이어그램은 메시지 큐 프레임워크를 보여 줍니다.

![메시지 큐 프레임워크](../../assets/configuration/mq-framework.png)

- A [게시자](https://glossary.magento.com/publisher-subscriber-pattern) 는 exchange에 메시지를 보내는 구성 요소입니다. 게시할 교환과 보내는 메시지의 형식을 알고 있습니다.

- Exchange는 게시자로부터 메시지를 수신하여 대기열로 보냅니다. RabbitMQ에서는 여러 유형의 교환을 지원하지만, Commerce에서는 주제 교환만 사용합니다. 항목에는 점으로 구분된 텍스트 문자열을 포함하는 라우팅 키가 포함되어 있습니다. 항목 이름의 형식은 다음과 같습니다 `string1.string2`: 예 `customer.created` 또는 `customer.sent.email`.

   브로커 에서는 메시지 전달 규칙을 설정할 때 와일드카드를 사용할 수 있습니다. 별표(`*`)을 대체합니다. _하나_ 문자열 또는 파운드 기호(`#`)을 클릭하여 0개 이상의 문자열을 바꿉니다. 예, `customer.*` 을(를) `customer.create` 및 `customer.delete`, 하지만 아님 `customer.sent.email`. 하지만 `customer.#` 을(를) `customer.create`,  `customer.delete`, 및 `customer.sent.email`.

- 큐는 메시지를 저장하는 버퍼입니다.

- 소비자가 메시지를 수신합니다. 어느 대기열을 사용해야 하는지 알고 있습니다. 메시지의 처리자를 특정 큐에 매핑할 수 있습니다.

RabbitMQ를 사용하지 않고도 기본 메시지 큐 시스템을 설정할 수도 있습니다. 이 시스템에서 MySQL [어댑터](https://glossary.magento.com/adapter) 데이터베이스에 메시지를 저장합니다. 세 개의 데이터베이스 테이블(`queue`, `queue_message`, 및 `queue_message_status`) 메시지 큐 작업 로드를 관리합니다. 클라우드 일자리로 소비자들이 메시지를 받을 수 있게 한다. 이 솔루션은 확장성이 뛰어나지 않습니다. RabbitMQ는 가능한 한 사용해야 합니다.
