---
title: 메시지 브로커
description: 'Adobe Commerce의 온-프레미스 설치에 필요한 메시지 브로커 소프트웨어(예:  [!DNL RabbitMQ])를 설치하고 구성하려면 다음 단계를 따르십시오.'
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 메시지 브로커

Adobe Commerce은 [!DNL RabbitMQ] 오픈 소스 메시지 브로커를 사용합니다. 신뢰할 수 있고, 가용성이 높고, 확장 가능하고, 휴대성이 뛰어난 메시징 시스템을 제공합니다.

메시지 큐는 메시지의 발신자와 수신자가 서로 접촉하지 않는 비동기 통신 메커니즘을 제공한다. 메시지 대기열과 동시에 통신할 필요도 없습니다. 보낸 사람이 메시지를 대기열에 넣으면 받는 사람이 메시지를 받을 때까지 저장됩니다.

Adobe Commerce을 설치하기 전에 메시지 큐 시스템을 설정해야 합니다. 기본 시퀀스는 다음과 같습니다.

1. [!DNL RabbitMQ] 및 필수 구성 요소를 설치합니다.
1. [!DNL RabbitMQ]을(를) Adobe Commerce에 연결합니다.

>[!NOTE]
>
>메시지 큐 처리에 MySQL 또는 [!DNL RabbitMQ]을(를) 사용할 수 있습니다. 메시지 큐 시스템 설정에 대한 자세한 내용은 [메시지 큐 개요](https://developer.adobe.com/commerce/php/development/components/message-queues/)를 참조하십시오. Adobe Commerce에서 Bulk API를 사용하는 경우 메시지 큐 시스템 구성은 기본적으로 [!DNL RabbitMQ]을(를) 메시지 브로커로 사용하는 것으로 설정됩니다. 자세한 내용은 [메시지 큐 소비자 시작](../../configuration/cli/start-message-queues.md)을 참조하세요.

## Ubuntu에 [!DNL RabbitMQ] 설치

Ubuntu 16에 [!DNL RabbitMQ]을(를) 설치하려면 다음 명령을 입력하십시오.

```bash
sudo apt install -y rabbitmq-server
```

이 명령은 필요한 Erlang 패키지도 설치합니다.

이전 버전의 Ubuntu가 있는 경우 [!DNL RabbitMQ]에서 해당 웹 사이트에서 패키지를 설치하는 것이 좋습니다.

1. [rabbitmq-server](https://www.rabbitmq.com/download.html)에서 .deb 패키지를 다운로드합니다.
1. `dpkg`(으)로 패키지를 설치합니다.

자세한 내용은 [Debian/Ubuntu에 설치](https://www.rabbitmq.com/install-debian.html)를 참조하세요.

## CentOS에 [!DNL RabbitMQ] 설치

### Erlang 설치

[!DNL RabbitMQ]은(는) Erlang 프로그래밍 언어를 사용하여 작성되었으며, [!DNL RabbitMQ]과(와) 동일한 시스템에 설치해야 합니다.

자세한 내용은 [수동 설치](https://www.erlang-solutions.com/downloads/)를 참조하십시오.

올바른 버전을 설치하려면 [[!DNL RabbitMQ]/Erlang 버전 매트릭스](https://www.rabbitmq.com/which-erlang.html)를 참조하세요.

### [!DNL RabbitMQ] 설치

[!DNL RabbitMQ] 서버가 CentOS에 포함되어 있지만 버전이 오래된 경우가 많습니다. [!DNL RabbitMQ]님은 웹 사이트에서 패키지를 설치할 것을 권장합니다.

지원되는 최신 버전을 얻으려면 [!DNL RabbitMQ] 설치 페이지를 참조하세요. Adobe Commerce 2.3 및 2.4는 [!DNL RabbitMQ] 3.8.x를 지원합니다.

자세한 내용은 [RPM 기반 Linux에 설치](https://www.rabbitmq.com/install-rpm.html)를 참조하십시오.

## [!DNL RabbitMQ] 구성

공식 [!DNL RabbitMQ] 설명서를 검토하여 [!DNL RabbitMQ]을(를) 구성하고 관리하십시오. 다음 항목에 주의하십시오.

* 환경 변수
* 포트 액세스
* 기본 사용자 계정
* Broker 시작 및 중지
* 시스템 제한

## [!DNL RabbitMQ](으)로 설치 및 연결

Adobe Commerce _after_&#x200B;를 설치하는 경우 [!DNL RabbitMQ]을(를) 설치하는 동안 다음 명령줄 매개 변수를 추가하십시오.

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

위치:

| 매개 변수 | 설명 |
|--- |--- |
| `--amqp-host` | [!DNL RabbitMQ]이(가) 설치된 호스트 이름입니다. |
| `--amqp-port` | [!DNL RabbitMQ]에 연결하는 데 사용할 포트입니다. 기본값은 `5672`입니다. |
| `--amqp-user` | [!DNL RabbitMQ]에 연결하기 위한 사용자 이름입니다. 기본 사용자 `guest`을(를) 사용하지 마십시오. |
| `--amqp-password` | [!DNL RabbitMQ]에 연결하기 위한 암호입니다. 기본 암호 `guest`을(를) 사용하지 마십시오. |
| `--amqp-virtualhost` | [!DNL RabbitMQ]에 연결하기 위한 가상 호스트입니다. 기본값은 `/`입니다. |
| `--amqp-ssl` | [!DNL RabbitMQ]에 연결할지 여부를 나타냅니다. 기본값은 `false`입니다. 값을 true로 설정하는 경우 자세한 내용은 SSL 구성 을 참조하십시오. |

## [!DNL RabbitMQ] 연결

Adobe Commerce이 이미 설치되어 있고 이를 [!DNL RabbitMQ]에 연결하려는 경우 `<install_directory>/app/etc/env.php` 파일에 다음과 비슷하게 `queue` 섹션을 추가하십시오.

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

`bin/magento setup:config:set` 명령을 사용하여 [!DNL RabbitMQ] 구성 값을 설정할 수도 있습니다.

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

명령을 실행하거나 AMQP 구성 값으로 `<install_directory>/app/etc/env.php` 파일을 업데이트한 후 `bin/magento setup:upgrade`을(를) 실행하여 변경 사항을 적용하고 [!DNL RabbitMQ]에서 필요한 큐 및 교환을 만듭니다.

## SSL 구성

SSL 지원을 구성하려면 `<install_directory>/app/etc/env.php` 파일에서 `ssl` 및 `ssl_options` 매개 변수를 다음과 비슷하게 편집하십시오.

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## 메시지 대기열 소비자 시작

Adobe Commerce 및 [!DNL RabbitMQ]에 연결한 후에는 메시지 큐 소비자를 시작해야 합니다. 자세한 내용은 [메시지 큐 구성](../../configuration/cli/start-message-queues.md)을 참조하세요.
