---
title: 메시지 브로커(ActiveMQ Artemis)
description: Adobe Commerce의 온-프레미스 설치를 위한 Apache ActiveMQ Artemis 메시지 브로커를 설치하고 구성하려면 다음 단계를 따르십시오.
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# 메시지 브로커(ActiveMQ Artemis)

Adobe Commerce은 STOMP(Simple Text Oriented Messaging Protocol)를 통해 ActiveMQ Artemis 오픈 소스 메시지 브로커도 지원합니다. 안정적이고 확장 가능한 메시징 시스템을 제공하여 STOMP 기반 통합을 위한 유연성을 제공합니다.


>[!NOTE]
>
>ActiveMQ Artemis는 Adobe Commerce 2.4.5 이상 버전에서 도입되었습니다. 클라우드 인프라 프로젝트의 Adobe Commerce에 ActiveMQ Artemis를 설치하는 방법에 대한 자세한 내용은 [Cloud의 Commerce 안내서](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/service/activemq)에서 *ActiveMQ 서비스 설정*&#x200B;을 참조하십시오.

메시지 큐는 메시지의 발신자와 수신자가 서로 접촉하지 않는 비동기 통신 메커니즘을 제공한다. 메시지 대기열과 동시에 통신할 필요도 없습니다. 보낸 사람이 메시지를 대기열에 넣으면 받는 사람이 메시지를 받을 때까지 저장됩니다.

Adobe Commerce을 설치하기 전에 메시지 큐 시스템을 설정해야 합니다. 기본 시퀀스는 다음과 같습니다.

1. Apache ActiveMQ Artemis 및 사전 요구 사항을 설치합니다.
1. ActiveMQ를 Adobe Commerce에 연결합니다.

>[!NOTE]
>
>메시지 큐 처리에 MySQL, ActiveMQ 또는 [!DNL RabbitMQ]을(를) 사용할 수 있습니다. 메시지 큐 시스템 설정에 대한 자세한 내용은 [메시지 큐 개요](https://developer.adobe.com/commerce/php/development/components/message-queues/)를 참조하십시오. Adobe Commerce에서 Bulk API를 사용하는 경우 메시지 큐 시스템 구성은 기본적으로 [!DNL RabbitMQ]을(를) 메시지 브로커로 사용하는 것으로 설정됩니다. 자세한 내용은 [메시지 큐 소비자 시작](../../configuration/cli/start-message-queues.md)을 참조하세요.

>[!TIP]
>
>설치하기 전에 항상 [Apache ActiveMQ Artemis 다운로드 페이지](https://activemq.apache.org/components/artemis/download/)에서 안정적인 최신 버전을 확인하십시오. 이 문서의 예제에서는 2025년 9월 현재 안정적인 최신 릴리스인 버전 2.42.0을 사용합니다.


## Apache ActiveMQ Artemis 설치

Docker(개발 권장) 또는 수동 설치(프로덕션 권장)를 사용하여 ActiveMQ Artemis를 설치할 수 있습니다.

### 옵션 1: Docker 설치(개발 권장)

#### 사전 요구 사항

Docker가 시스템에 설치되어 실행 중인지 확인합니다.

>[!TIP]
>
>공식 ActiveMQ Artemis Docker 이미지에 대한 자세한 내용은 [Apache ActiveMQ Artemis Docker Hub 페이지](https://hub.docker.com/r/apache/activemq-artemis)를 참조하십시오.

#### 설치 단계

1. 공식 도커 이미지를 사용하여 ActiveMQ Artemis를 실행합니다.

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. 사용자 지정 자격 증명으로 실행:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Docker 관리 명령

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### 서비스 액세스

Docker 컨테이너가 실행되면 다음에 액세스할 수 있습니다.

- **웹 콘솔**: http://localhost:8161/console(기본 자격 증명: artemis/artemis)
- **STOMP 포트**: localhost:61613(Adobe Commerce 연결용)

>[!NOTE]
>
>개발 및 테스트를 위해 Docker 설치가 권장됩니다. 프로덕션의 경우 적절한 보안 구성과 함께 수동 설치를 사용하는 것이 좋습니다.

### 옵션 2: Ubuntu/CentOS에 수동 설치

#### 사전 요구 사항

Java 17 이상이 설치되어 있는지 확인합니다(ActiveMQ Artemis 2.42.0+에 필요).

### 설치 단계

1. [Apache ActiveMQ Artemis 웹 사이트](https://activemq.apache.org/components/artemis/download/)에서 최신 버전을 다운로드하여 설치하십시오. 2025년 9월 현재 안정적인 최신 버전은 2.42.0입니다.

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. `artemis` 사용자를 만들고 소유권을 설정합니다.

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Broker 인스턴스 만들기:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Broker를 시작합니다.

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## ActiveMQ Artemis 구성

공식 ActiveMQ Artemis 설명서를 검토하여 브로커를 구성하고 관리합니다. 다음 항목에 주의하십시오.

- 환경 변수
- 포트 액세스(STOMP 프로토콜)
- 기본 사용자 계정 및 자격 증명
- Broker 시작 및 중지
- 시스템 제한 및 리소스 조정

### 주요 구성 파일

- `/var/lib/artemis-instance/etc/broker.xml` - 주 브로커 구성
- `/var/lib/artemis-instance/etc/artemis-users.properties` - 사용자 인증
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - 사용자 역할
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap 구성

### STOMP 프로토콜 활성화

`/var/lib/artemis-instance/etc/broker.xml`을(를) 확인하여 STOMP 수락자가 구성되었는지 확인하십시오.

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

STOMP에서 SSL을 활성화하려면 `stomp-ssl` 수락자를 명시적으로 추가해야 합니다.

## ActiveMQ Artemis로 설치 및 연결

Adobe Commerce _after_&#x200B;를 설치하고 ActiveMQ Artemis를 설치하는 경우 설치하는 동안 다음 명령줄 매개 변수를 추가하십시오.

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

위치:

| 매개 변수 | 설명 |
|--- |--- |
| `--stomp-host` | ActiveMQ가 설치된 호스트 이름입니다. |
| `--stomp-port` | ActiveMQ에 연결하는 데 사용할 포트입니다. 기본값은 `61613`입니다. |
| `--stomp-user` | ActiveMQ에 연결하기 위한 사용자 이름입니다. 기본 사용자 `artemis`을(를) 사용하지 마십시오. |
| `--stomp-password` | ActiveMQ에 연결하기 위한 암호입니다. 기본 암호 `artemis`을(를) 사용하지 마십시오. |
| `--stomp-ssl` | ActiveMQ에 연결할지 여부를 나타냅니다. 기본값은 `false`입니다. 값을 true로 설정하는 경우 자세한 내용은 SSL 구성 을 참조하십시오. |

## ActiveMQ Artemis 연결

`<install_directory>/app/etc/env.php` 파일에 AMQP(RabbitMQ) 구성이 있는 Adobe Commerce 인스턴스가 이미 있고 이를 ActiveMQ에 연결하려면 다음과 비슷하도록 `queue` 섹션을 STOMP로 바꾸십시오.

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

`bin/magento setup:config:set` 명령을 사용하여 ActiveMQ 구성 값을 설정할 수도 있습니다(`app/etc/env.php` 파일에 AMQP 구성이 있는 경우 제거).

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

명령을 실행하거나 STOMP 구성 값으로 `<install_directory>/app/etc/env.php` 파일을 업데이트한 후 `bin/magento setup:upgrade`을(를) 실행하여 변경 사항을 적용하고 ActiveMQ에서 필요한 큐를 만듭니다.

## SSL 구성

SSL 지원을 구성하려면 `ssl` 파일에서 `ssl_options` 및 `<install_directory>/app/etc/env.php` 매개 변수를 다음과 비슷하게 편집하십시오.

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL 구성 옵션

| 옵션 | 설명 | 기본값 |
|--- |--- |--- |
| `verify_peer` | 브로커의 SSL 인증서 확인 | `true` |
| `verify_peer_name` | 브로커의 호스트 이름이 인증서와 일치하는지 확인 | `true` |
| `allow_self_signed` | 자체 서명된 인증서 허용 | `false` |
| `cafile` | 브로커 확인을 위한 CA 인증서 파일 경로 | SSL에 필요 |
| `certfile` | 클라이언트 인증서 파일 경로(상호 SSL용) | 선택 사항 |
| `keyfile` | 클라이언트 개인 키 파일 경로(상호 SSL용) | 선택 사항 |
| `passphrase` | 클라이언트 개인 키의 암호 | 선택 사항 |

### 개발 SSL 구성

개발 환경의 경우 느슨한 SSL 설정을 사용할 수 있습니다.

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## 성능 조정

ActiveMQ Artemis는 몇 가지 성능 조정 옵션을 제공합니다.

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## 모니터링 및 관리

### 웹 콘솔

ActiveMQ Artemis는 다음 위치에서 액세스할 수 있는 웹 기반 관리 콘솔을 제공합니다.
- URL: `http://localhost:8161/console`
- 기본 자격 증명: `artemis/artemis`

## 문제 해결

### 일반적인 문제

1. **연결이 거부되었습니다**: ActiveMQ Artemis가 실행 중이고 STOMP 수용자가 구성되어 있는지 확인하십시오.
1. **인증 실패**: Broker 구성과 `env.php` 파일 모두에서 사용자 이름/암호를 확인하십시오.
1. **SSL 핸드셰이크가 실패했습니다**: SSL 인증서 및 구성을 확인하십시오.




### STOMP 연결 확인

텔넷을 사용하여 STOMP 연결 테스트:

```bash
telnet localhost 61613
```

연결이 설정되어 있는지 확인해야 합니다. STOMP 명령을 사용하여 테스트하려면

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

예상되는 출력은 연결 설정 및 STOMP 프로토콜 응답을 보여 줍니다.

## 메시지 대기열 소비자 시작

Adobe Commerce 및 ActiveMQ Artemis를 연결한 후 메시지 큐 소비자를 시작해야 합니다. 자세한 내용은 [메시지 큐 구성](../../configuration/cli/start-message-queues.md)을 참조하세요.

