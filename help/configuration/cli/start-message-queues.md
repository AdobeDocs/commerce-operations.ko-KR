---
title: 메시지 큐 소비자 시작
description: 메시지 큐 소비자를 시작하는 방법을 알아봅니다.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 메시지 큐 소비자 시작

{{file-system-owner}}

다음을 시작해야 합니다. [메시지 큐 소비자](../queues/consumers.md) Inventory management 대량 작업, REST 벌크 및 비동기 엔드포인트와 같은 비동기 작업을 활성화합니다. B2B 기능을 활성화하려면 여러 소비자를 시작해야 합니다. 서드파티 모듈에서는 사용자 지정 소비자를 시작해야 할 수도 있습니다.

모든 소비자 목록을 보려면

```bash
bin/magento queue:consumers:list
```

메시지 대기열 소비자를 시작하려면 다음을 수행합니다.

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

사용 가능한 모든 메시지를 사용한 후 명령이 종료됩니다. 수동으로 또는 cron 작업을 사용하여 명령을 다시 실행할 수 있습니다. 의 여러 인스턴스를 실행할 수도 있습니다. `magento queue:consumers:start` 큰 메시지 대기열을 처리하는 명령입니다. 예를 들어 다음을 추가할 수 있습니다 `&` 백그라운드에서 실행할 명령에 따라 프롬프트로 돌아가서 명령을 계속 실행합니다.

```bash
bin/magento queue:consumers:start <consumer_name> &
```

다음을 참조하십시오 [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) 의 Commerce 섹션에서 다음을 수행합니다 _명령줄 도구 참조_ 명령 옵션, 매개 변수 및 값에 대한 자세한 내용을 보려면 여기를 클릭하십시오.

>[!INFO]
>
>다음 `--multi-process` 옵션이에 있음 `queue:consumers:start` 명령을 실행하되, 병렬 프로세스로 소비자를 실행하려면 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 의 옵션 `/app/etc/env.php`. 그렇지 않은 경우 `queue:consumers:start` 을(를) 사용하여 호출합니다. `--multi-process` 옵션을 선택하면 단일 스레드에서만 작동합니다.
