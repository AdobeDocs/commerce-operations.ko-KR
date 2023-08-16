---
title: 메시지 브로커
description: '다음 단계에 따라 필요한 메시지 브로커 소프트웨어(예: [!DNL RabbitMQ]) Adobe Commerce 및 Magento Open Source의 온-프레미스 설치용'
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 메시지 브로커

Adobe Commerce은 [!DNL RabbitMQ] 오픈 소스 메시지 브로커. 신뢰할 수 있고, 가용성이 높고, 확장 가능하고, 휴대성이 뛰어난 메시징 시스템을 제공합니다.

메시지 큐는 메시지의 발신자와 수신자가 서로 접촉하지 않는 비동기 통신 메커니즘을 제공한다. 메시지 대기열과 동시에 통신할 필요도 없습니다. 보낸 사람이 메시지를 대기열에 넣으면 받는 사람이 메시지를 받을 때까지 저장됩니다.

Adobe Commerce 또는 Magento Open Source을 설치하기 전에 메시지 대기열 시스템을 설정해야 합니다. 기본 시퀀스는 다음과 같습니다.

1. 설치 [!DNL RabbitMQ] 및 모든 사전 요구 사항
1. 연결 [!DNL RabbitMQ] Adobe Commerce 또는 Magento Open Source에 전송됩니다.

>[!NOTE]
>
>MySQL 또는 [!DNL RabbitMQ] 메시지 대기열 처리용. 메시지 대기열 시스템 설정에 대한 자세한 내용은 [메시지 대기열 개요](https://developer.adobe.com/commerce/php/development/components/message-queues/). Adobe Commerce에서 벌크 API를 사용하는 경우 메시지 대기열 시스템 구성은 기본적으로 사용으로 설정됩니다 [!DNL RabbitMQ] 메시지 브로커입니다. 다음을 참조하십시오 [메시지 큐 소비자 시작](../../configuration/cli/start-message-queues.md) 추가 정보.

## 설치 [!DNL RabbitMQ] 우분투에서

설치하려면 [!DNL RabbitMQ] ubuntu 16에서 다음 명령을 입력합니다.

```bash
sudo apt install -y rabbitmq-server
```

이 명령은 필요한 Erlang 패키지도 설치합니다.

이전 버전의 우분투가 있다면 [!DNL RabbitMQ] 는 웹 사이트에서 패키지를 설치할 것을 권장합니다.

1. .deb 패키지 다운로드 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 패키지 설치 `dpkg`.

을(를) 참조하십시오 [데비안/우분투에 설치](https://www.rabbitmq.com/install-debian.html) 추가 정보.

## 설치 [!DNL RabbitMQ] CentOS에서

### Erlang 설치

[!DNL RabbitMQ] 는 와 동일한 시스템에 설치되어야 하는 Erlang 프로그래밍 언어를 사용하여 작성되었습니다. [!DNL RabbitMQ].

다음을 참조하십시오 [수동 설치](https://www.erlang-solutions.com/downloads/) 추가 정보.

다음을 참조하십시오. [[!DNL RabbitMQ]/Erlang 버전 매트릭스](https://www.rabbitmq.com/which-erlang.html) 올바른 버전을 설치하려면 다음을 수행하십시오.

### 설치 [!DNL RabbitMQ]

다음 [!DNL RabbitMQ] 서버는 CentOS에 포함되어 있지만 버전은 오래된 경우가 많습니다. [!DNL RabbitMQ] 는 웹 사이트에서 패키지를 설치할 것을 권장합니다.

다음을 참조하십시오. [!DNL RabbitMQ] 지원되는 최신 버전을 보려면 페이지를 설치하십시오. Adobe Commerce 및 Magento Open Source 2.3 및 2.4 지원 [!DNL RabbitMQ] 3.8.x

을(를) 참조하십시오 [RPM 기반 Linux에 설치](https://www.rabbitmq.com/install-rpm.html) 추가 정보.

## Configure [!DNL RabbitMQ]

공식 검토 [!DNL RabbitMQ] 구성 및 관리 설명서 [!DNL RabbitMQ]. 다음 항목에 주의하십시오.

* 환경 변수
* 포트 액세스
* 기본 사용자 계정
* Broker 시작 및 중지
* 시스템 제한

## 다음으로 설치 [!DNL RabbitMQ] 및 연결

Adobe Commerce 또는 Magento Open Source을 설치하는 경우 _이후_ 을(를) 설치하는 중입니다. [!DNL RabbitMQ]를 클릭하고 설치하는 동안 다음 명령줄 매개 변수를 추가합니다.

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

위치:

| 매개 변수 | 설명 |
|--- |--- |
| `--amqp-host` | 호스트 이름 위치 [!DNL RabbitMQ] 이(가) 설치되었습니다. |
| `--amqp-port` | 연결에 사용할 포트 [!DNL RabbitMQ]. 기본값은 입니다 `5672`. |
| `--amqp-user` | 에 연결하기 위한 사용자 이름 [!DNL RabbitMQ]. 기본 사용자 사용 안 함 `guest`. |
| `--amqp-password` | 에 연결하기 위한 암호 [!DNL RabbitMQ]. 기본 암호 사용 안 함 `guest`. |
| `--amqp-virtualhost` | 에 연결할 가상 호스트 [!DNL RabbitMQ]. 기본값은 입니다 `/`. |
| `--amqp-ssl` | 연결 여부를 나타냅니다. [!DNL RabbitMQ]. 기본값은 입니다 `false`. 값을 true로 설정하는 경우 자세한 내용은 SSL 구성 을 참조하십시오. |

## 연결 [!DNL RabbitMQ]

이미 Adobe Commerce 또는 Magento Open Source이 설치되어 있고 이 파일을 연결하려는 경우 [!DNL RabbitMQ], 추가 `queue` 의 섹션 `<install_directory>/app/etc/env.php` 다음과 유사하도록 파일을 생성합니다.

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

다음을 설정할 수도 있습니다. [!DNL RabbitMQ] 를 사용한 구성 값 `bin/magento setup:config:set` 명령:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

를 실행하거나 를 업데이트한 후 `<install_directory>/app/etc/env.php` amqp 구성 값이 있는 파일, 실행 `bin/magento setup:upgrade` 변경 사항을 적용하고 필요한 대기열 및 교환을 만들려면 [!DNL RabbitMQ].

## SSL 구성

SSL 지원을 구성하려면 다음을 편집합니다. `ssl` 및 `ssl_options` 의 매개 변수 `<install_directory>/app/etc/env.php` 다음과 유사하도록 파일을 생성합니다.

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

Adobe Commerce을 연결한 후 [!DNL RabbitMQ], 메시지 큐 소비자를 시작해야 합니다. 다음을 참조하십시오 [메시지 큐 구성](../../configuration/cli/start-message-queues.md) 을 참조하십시오.
