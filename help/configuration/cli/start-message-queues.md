---
title: 메시지 큐 소비자 시작
description: Adobe Commerce 비동기 작업을 위한 메시지 큐 소비자를 시작하는 방법을 알아봅니다. 소비자 관리 및 B2B 기능 설정을 살펴보십시오.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 메시지 큐 소비자 시작

{{file-system-owner}}

Inventory management 대량 작업 및 REST 대량/비동기 끝점과 같은 비동기 작업을 사용하려면 [메시지 큐 소비자](../queues/consumers.md)를 시작해야 합니다. B2B 기능을 활성화하려면 여러 소비자를 시작해야 합니다. 서드파티 모듈에서는 사용자 지정 소비자를 시작해야 할 수도 있습니다.

모든 소비자 목록을 보려면

```bash
bin/magento queue:consumers:list
```

메시지 대기열 소비자를 시작하려면 다음을 수행합니다.

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

사용 가능한 모든 메시지를 사용한 후 명령이 종료됩니다. 수동으로 또는 cron 작업을 사용하여 명령을 다시 실행할 수 있습니다. `magento queue:consumers:start` 명령의 여러 인스턴스를 실행하여 큰 메시지 큐를 처리할 수도 있습니다. 예를 들어 `&`을(를) 명령에 추가하여 백그라운드에서 실행하고 프롬프트로 돌아가서 명령을 계속 실행할 수 있습니다.

```bash
bin/magento queue:consumers:start <consumer_name> &
```

명령 옵션, 매개 변수 및 값에 대한 자세한 내용은 [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart)명령줄 도구 참조&#x200B;_의 Commerce 섹션에서_&#x200B;을(를) 참조하십시오.

>[!INFO]
>
>`--multi-process` 옵션이 `queue:consumers:start` 명령에 있지만 병렬 프로세스로 소비자를 실행하려면 [`multiple_processes`](../queues/manage-message-queues.md#configuration)에서 `/app/etc/env.php` 옵션을 구성하십시오. 그렇지 않으면 `queue:consumers:start` 옵션을 사용하여 `--multi-process`을(를) 호출하는 경우 단일 스레드에서만 작동합니다.
