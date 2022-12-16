---
title: 메시지 큐 소비자 시작
description: 메시지 큐 소비자를 시작하는 방법을 알아봅니다.
source-git-commit: 3e3dac0c75622b210cf1168639b8804003f3c538
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# 메시지 큐 소비자 시작

{{file-system-owner}}

을(를) 시작해야 합니다 [메시지 큐 소비자](../queues/consumers.md) Inventory management 대량 작업 및 REST 대량 및 비동기 끝점과 같은 비동기 작업을 사용하도록 설정하려면 다음을 수행하십시오. B2B 기능을 활성화하려면 여러 소비자를 시작해야 합니다. 타사 모듈을 사용하려면 사용자 지정 소비자를 시작해야 할 수도 있습니다.

모든 소비자 목록을 보려면

```bash
bin/magento queue:consumers:list
```

메시지 대기열 소비자를 시작하려면 다음을 수행합니다.

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

사용 가능한 모든 메시지를 사용한 후 명령이 종료됩니다. 수동으로 또는 크론 작업으로 명령을 다시 실행할 수 있습니다. 의 여러 인스턴스를 실행할 수도 있습니다 `magento queue:consumers:start` 큰 메시지 큐를 처리하는 명령입니다. 예를 들어 를 추가할 수 있습니다 `&` 명령에서 백그라운드에서 실행한 다음 프롬프트로 돌아가서 명령을 계속 실행합니다.

```bash
bin/magento queue:consumers:start <consumer_name> &
```

자세한 내용은 [큐:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) 의 상거래 섹션에서 _명령줄 도구 참조_ 명령 옵션, 매개 변수 및 값에 대한 자세한 내용을 참조하십시오.

>[!INFO]
>
>다음 `--multi-process` 옵션이 `queue:consumers:start` 명령을 따르지만 병렬 프로세스를 사용하여 소비자를 실행하려면 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 옵션 `/app/etc/env.php`. 그렇지 않으면 `queue:consumers:start` 를 사용하여 를 호출합니다 `--multi-process` 옵션, 단일 스레드에서만 작동합니다.
