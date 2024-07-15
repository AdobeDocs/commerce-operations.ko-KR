---
title: Amazon 메시지 큐 설정
description: AWS MQ 서비스를 사용하도록 Commerce을 구성하는 방법에 대해 알아봅니다.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Amazon 메시지 큐 설정

Commerce 2.4.3부터 Amazon 메시지 큐(MQ)를 온-프레미스 메시지 큐 인스턴스에 대한 클라우드 기반 대체 인스턴스로 사용할 수 있습니다.

AWS에서 메시지 큐를 만들려면 _AWS 설명서_&#x200B;에서 [Amazon MQ 설정](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html)을 참조하세요.

## AWS MQ용 Commerce 구성

AWS MQ 서비스에 연결하려면 `env.php` 파일에서 `queue.amqp` 개체를 구성하십시오.
AWS 메시지 큐에는 SSL/TLS 연결이 필요합니다.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

위치:

- `host` - AMQP 끝점의 URL입니다. AWS에서 브로커 이름을 클릭하면 사용할 수 있습니다(&quot;https://&quot; 및 후행 포트 번호 제거).
- `user`—AWS MQ 브로커를 만들 때 입력한 사용자 이름 값
- `password`—AWS MQ 브로커를 만들 때 입력한 암호 값

>[!INFO]
>
>Amazon MQ는 TLS 연결만 지원합니다. 피어 확인은 지원되지 않습니다.

`env.php` 파일을 편집한 후 다음 명령을 실행하여 설치를 완료합니다.

```bash
bin/magento setup:upgrade
```

## Commerce에서 AWS MQ 서비스를 사용하는 방법

`async.operations.all` 메시지 대기열 소비자가 AMQP 연결을 사용합니다.

이 소비자는 AWS MQ 연결을 통해 `async` 접두사가 붙은 모든 항목 이름을 라우팅합니다.

예를 들어 `InventoryCatalog`에는 다음과 같은 항목이 있습니다.

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

`InventoryCatalog`에 대한 기본 구성은 [!DNL RabbitMQ]에 메시지를 게시하지 않습니다. 기본 동작은 동일한 사용자 스레드에서 작업을 수행하는 것입니다. `InventoryCatalog`에게 메시지를 게시하도록 하려면 `cataloginventory/bulk_operations/async`을(를) 사용하도록 설정하십시오. 관리자의 경우 **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 대량 작업으로 이동하여 `Run asynchronously`을(를) **예**(으)로 설정합니다.

## 메시지 큐 테스트

Commerce에서 [!DNL RabbitMQ](으)로 메시지 전송을 테스트하려면:

1. 큐를 모니터링하려면 AWS의 [!DNL RabbitMQ] 웹 콘솔에 로그인하십시오.
1. 관리자에서 제품을 만듭니다.
1. 인벤토리 소스를 만듭니다.
1. **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 일괄 작업 > 비동기적으로 실행을 사용하도록 설정합니다.
1. **카탈로그** > 제품으로 이동합니다. 그리드에서 위에서 만든 제품을 선택하고 **인벤토리 Source 할당**&#x200B;을 클릭합니다.
1. 프로세스를 완료하려면 **저장 및 닫기**&#x200B;를 클릭하십시오.

   이제 [!DNL RabbitMQ] 웹 콘솔에 메시지가 표시됩니다.

1. `async.operations.all` 메시지 큐 소비자를 시작합니다.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

이제 [!DNL RabbitMQ] 웹 콘솔에서 처리된 대기 중인 메시지가 표시됩니다.
관리자에서 제품에 대한 인벤토리 소스가 변경되었는지 확인합니다.
