---
title: 메시지 대기열 관리
description: Adobe Commerce의 명령줄에서 메시지 대기열을 관리하는 방법을 알아봅니다.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: caca8df48c498977f830082ef27d9afb6220ae92
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 메시지 대기열 관리

소비자가 메시지를 검색하도록 크론 작업 또는 외부 프로세스 관리자를 사용하여 명령줄에서 메시지 대기열을 관리할 수 있습니다.

## 프로세스 관리

크론 작업은 소비자를 다시 시작하는 기본 메커니즘입니다. 다음에 의해 시작된 프로세스 `cron` 지정된 수의 메시지를 사용한 다음 종료합니다. 재실행 중 `cron` 소비자를 다시 시작합니다.

다음 예제는 `crontab` 실행 중인 소비자에 대한 구성:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>메시지 대기열을 확인하는 빈도는 비즈니스 논리와 사용 가능한 시스템 리소스에 따라 달라질 수 있습니다. 일반적으로 카탈로그 업데이트와 같은 리소스 집약적인 프로세스보다 새로운 고객을 확인하고 환영 이메일을 더 자주 보낼 수 있습니다. 다음을 정의해야 합니다 `cron` 비즈니스 요구에 따라 일정을 예약합니다.
>
>관리 저장소 > 설정 > 구성 > 고급 > 시스템 > Cron 그룹 구성 옵션: 소비자에서 구성할 수 있습니다.
>
>다음을 참조하십시오 [cron 구성 및 실행](../cli/configure-cron-jobs.md) 사용에 대한 자세한 내용 `cron` Commerce와 함께 사용됩니다.

다음과 같은 프로세스 관리자를 사용할 수도 있습니다. [감독자](http://supervisord.org/index.html) 프로세스 상태를 모니터링합니다. 관리자는 명령줄을 사용하여 필요에 따라 프로세스를 재시작할 수 있습니다.

## 구성

### 기본적으로 동작

- 크론 작업 `consumers_runner` 활성화됨
- 크론 작업 `consumers_runner` 정의된 모든 소비자 실행
- 각 소비자는 10000 메시지를 처리한 다음 종료합니다

>[!INFO]
>
>Adobe Commerce 스토어가 Cloud 플랫폼에서 호스팅되는 경우 [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 을(를) 구성하려면 `consumers_runner` cron job.

### 특정 구성

편집 `/app/etc/env.php` cron 작업을 구성하는 파일 `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - 를 활성화하거나 비활성화하는 부울 값 `consumers_runner` cron 작업(기본값 = `true`).
- `max_messages` - 종료하기 전에 각 소비자가 처리해야 하는 최대 메시지 수(기본값 = `10000`). 권장하지는 않지만 0을 사용하여 소비자가 종료하지 않도록 할 수 있습니다. 다음을 참조하십시오 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 소비자가 메시지 큐의 메시지를 처리하는 방법을 구성합니다.
- `consumers` - 실행할 소비자를 지정하는 문자열 배열. 빈 배열이 실행됩니다. *모두* 소비자.
- `multiple_processes` - 몇 개의 프로세스에서 실행할 소비자를 지정하는 키-값 쌍의 배열입니다. Commerce 2.4.4 이상에서 지원됩니다.

   >[!INFO]
   >
   >MySQL 작업 큐에서 여러 소비자를 실행하는 것은 권장되지 않습니다. 다음을 참조하십시오 [메시지 대기열을 MySQL에서 AMQP로 변경](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) 추가 정보.

   >[!INFO]
   >
   >Adobe Commerce 스토어가 Cloud 플랫폼에서 호스팅되는 경우 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) 소비자가 메시지 큐의 메시지를 처리하는 방법을 구성합니다.

다음을 참조하십시오 [메시지 큐 소비자 시작](../cli/start-message-queues.md).
