---
title: RabbitMQ에서 ActiveMQ로 마이그레이션
description: Adobe Commerce의 온-프레미스 설치에 사용되는 메시지 큐 브로커를 바꾸는 방법에 대해 알아봅니다.
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# ActiveMQ로 마이그레이션

ActiveMQ(Apache ActiveMQ Artemis)는 Adobe Commerce에서 메시지 큐를 처리하기 위해 RabbitMQ에 대한 대안을 제공하는 고성능, 다중 프로토콜 메시지 브로커입니다.

2.4.8-p3, 2.4.7-p8, 2.4.6-p13 및 2.4.5-p16부터 Adobe Commerce은 메시지 큐 브로커로 ActiveMQ를 지원합니다. 이렇게 하면 온프레미스 설치에서 인프라 요구 사항과 전문 지식을 기반으로 RabbitMQ와 ActiveMQ 중에서 선택할 수 있는 유연성을 추가로 제공합니다.

## 시작하기 전에

마이그레이션을 시작하기 전에 다음을 확인하십시오.

1. `app/etc/env.php`에서 현재 RabbitMQ 구성을 검토하십시오.
1. 데이터베이스와 코드베이스를 완전히 백업합니다.
1. 설치가 ActiveMQ에 대한 시스템 요구 사항을 충족하는지 확인합니다.
1. 마이그레이션을 완료할 유지 관리 기간을 계획합니다.

## 마이그레이션 경로

ActiveMQ로 마이그레이션하는 것은 간단한 프로세스이지만 브로커를 전환하기 전에 모든 보류 중인 메시지가 처리되도록 하는 것이 중요합니다.

이러한 마이그레이션 지침은 Adobe Commerce이 메시지 대기열 브로커를 사용하는 유일한 애플리케이션이라고 가정합니다.

### 1단계: 사이트를 유지 관리 모드로 설정

1. 사이트를 [유지 관리 모드](../../installation/tutorials/maintenance-mode.md)로 설정:

   ```bash
   bin/magento maintenance:enable
   ```

1. 유지 관리 모드가 활성화되어 있는지 확인합니다.

   ```bash
   bin/magento maintenance:status
   ```

### 2단계: RabbitMQ 메시지 카운트 확인

계속하기 전에 RabbitMQ의 모든 메시지가 처리되었는지 확인하십시오. 다음 방법 중 하나를 사용하십시오.

#### 방법 A: RabbitMQ 관리 대시보드 사용

1. `http://<host>:15672`에서 RabbitMQ 관리 UI에 액세스
1. 기본 자격 증명: `guest/guest`
1. **큐** 탭으로 이동
1. 모든 대기열에 **개의 메시지 표시** 확인

   ![RabbitMQ 관리 대시보드](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### 방법 B: rabbitmqctl 명령줄 사용

1. 모든 대기열과 메시지 카운트 확인:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="RabbitMQ CLI 출력" width="500" />

1. 자세한 대기열 정보 확인:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="RabbitMQ CLI 상세 출력" width="500" />

### 3단계: 보류 중인 메시지 처리

메시지가 대기열에 보류 중인 경우 계속 진행하기 전에 처리하십시오.

1. 사용 가능한 소비자 목록 가져오기:

   ```bash
   bin/magento queue:consumers:list
   ```

1. 소비자를 그룹으로 처리하거나 개별 메시지 대기열로 처리합니다.

   - **소비자를 그룹으로 처리**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >시스템에서 cron이 이미 실행 중인 경우 `bin/magento cron:run --group=consumers`을(를) 수동으로 실행할 필요가 없습니다. 대신 2단계의 명령을 사용하여 메시지 수를 확인하여 메시지가 처리되고 있는지 확인합니다.

   - **특정 메시지 큐 처리**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     예를 들어 비동기 작업을 처리하려면 다음을 수행합니다.

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >`--max-messages` 매개 변수는 소비자가 중지하기 전에 처리할 메시지 수를 제한합니다. 대기열 크기를 기준으로 이 값을 조정합니다.

   - **메시지 처리 모니터링**

     모든 대기열이 비어 있을 때까지 메시지 수를 계속 확인합니다.

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### 4단계: 모든 메시지가 처리되는지 확인

다음 단계로 진행하기 전에 **모든 대기열에 0개의 메시지가 표시되는지**&#x200B;확인하십시오. 2단계의 확인 명령을 다시 실행합니다.

>[!WARNING]
>
>처리되지 않은 메시지가 남아 있는 경우 다음 단계로 진행하지 마십시오. 메시지가 아직 보류 중일 때 브로커를 전환하면 데이터 손실이 발생할 수 있습니다.

### 5단계: 소비자 및 cron 작업 중단

1. 실행 중인 모든 메시지 큐 소비자 중지:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. cron 작업 비활성화:

   ```bash
   bin/magento cron:remove
   ```

1. cron 작업이 제거되었는지 확인합니다.

   ```bash
   crontab -l
   ```

### 6단계: 현재 구성 백업

현재 구성의 백업을 만듭니다.

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### 7단계: 선택적으로 RabbitMQ를 제거

RabbitMQ가 더 이상 필요하지 않으면 제거할 수 있습니다.

### 8단계: Adobe Commerce에서 ActiveMQ 설치 및 구성

STOMP 프로토콜 구성 및 연결 확인과 같은 ActiveMQ 설치 및 구성 작업을 완료하려면 [설치 및 구성 안내서](../../installation/prerequisites/activemq.md)를 참조하십시오.

### 9단계: cron 작업 재설치

1. 테스트가 성공적으로 완료되면 cron 작업을 다시 설치합니다.

   ```bash
   bin/magento cron:install
   ```

1. cron 작업이 예약되어 있는지 확인합니다.

   ```bash
   crontab -l
   ```

### 10단계: 유지 관리 모드 비활성화

1. 모든 것이 올바르게 작동하는지 확인한 후 유지 관리 모드를 비활성화합니다.

   ```bash
   bin/magento maintenance:disable
   ```

1. 유지 관리 모드가 비활성화되어 있는지 확인합니다.

   ```bash
   bin/magento maintenance:status
   ```

### 11단계: 시스템 모니터링

마이그레이션 후 24-48시간 동안 시스템을 모니터링하여 모든 큐 작업이 올바르게 작동하는지 확인합니다.

- ActiveMQ 웹 콘솔에서 메시지 처리량을 정기적으로 확인하십시오.
- 응용 프로그램 로그에서 큐 관련 오류 모니터링
- 비동기 작업(구성 저장, 내보내기 등)이 작동하는지 확인합니다.
- cron 로그를 확인하여 소비자가 실행 중인지 확인하십시오

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## 롤백

마이그레이션 도중 또는 후에 문제가 발생하는 경우 RabbitMQ로 롤백할 수 있습니다.

1. 유지 관리 모드 활성화:

   ```bash
   bin/magento maintenance:enable
   ```

1. 모든 소비자를 중지하고 cron 을 비활성화하십시오.

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. 이전 구성을 복원합니다.

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. RabbitMQ 시작(중지된 경우):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. 캐시 지우기:

   ```bash
   bin/magento cache:flush
   ```

1. cron을 다시 설치합니다.

   ```bash
   bin/magento cron:install
   ```

1. 유지 관리 모드 비활성화:

   ```bash
   bin/magento maintenance:disable
   ```

마이그레이션을 완료한 후에는 더 이상 구성 값을 변경할 필요가 없습니다.

