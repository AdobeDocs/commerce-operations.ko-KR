---
title: Amazon 메시지 큐 설정
description: AWS MQ 서비스를 사용하도록 Commerce를 구성하는 방법에 대해 알아봅니다.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Amazon 메시지 큐 설정

Commerce 2.4.3부터 Amazon 메시지 큐(MQ)를 온-프레미스 메시지 큐 인스턴스에 대한 클라우드 기반 대체 인스턴스로 사용할 수 있습니다.

AWS에서 메시지 큐를 만들려면 다음을 참조하십시오. [Amazon MQ 설정](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 다음에서 _AWS 설명서_.

## AWS MQ용 Commerce 구성

AWS MQ 서비스에 연결하려면 `queue.amqp` 의 오브젝트 `env.php` 파일.
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

- `host`—AMQP 끝점의 URL입니다. AWS에서 브로커 이름을 클릭하면 사용할 수 있습니다(&quot;https://&quot; 및 후행 포트 번호 제거).
- `user`—AWS MQ 브로커를 만들 때 입력한 사용자 이름 값입니다
- `password`—AWS MQ Broker를 만들 때 입력한 암호 값

>[!INFO]
>
>Amazon MQ는 TLS 연결만 지원합니다. 피어 확인은 지원되지 않습니다.

편집 후 `env.php` 다음 명령을 실행하여 설치를 완료합니다.

```bash
bin/magento setup:upgrade
```

## Commerce에서 AWS MQ 서비스를 사용하는 방법

다음 `async.operations.all` 메시지 대기열 소비자는 AMQP 연결을 사용합니다.

이 소비자는 접두사가 있는 모든 주제 이름을 라우팅합니다. `async` AWS MQ 연결을 통해.

예를 들어, `InventoryCatalog` 다음이 있습니다.

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

의 기본 구성 `InventoryCatalog` 에 메시지를 게시하지 않음 [!DNL RabbitMQ]; 기본 동작은 동일한 사용자 스레드에서 작업을 수행하는 것입니다. 알리기 `InventoryCatalog` 메시지를 게시하려면 다음을 활성화합니다. `cataloginventory/bulk_operations/async`. 관리자로부터 다음 위치로 이동합니다. **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 벌크 작업 및 설정  `Run asynchronously`끝 **예**.

## 메시지 큐 테스트

Commerce에서 (으)로 메시지 전송을 테스트하려면 [!DNL RabbitMQ]:

1. 에 로그인합니다 [!DNL RabbitMQ] AWS의 웹 콘솔로 큐를 모니터링합니다.
1. 관리자에서 제품을 만듭니다.
1. 인벤토리 소스를 만듭니다.
1. 사용 **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 일괄 작업 > 비동기적으로 실행.
1. 다음으로 이동 **카탈로그** > 제품. 그리드에서 위에서 만든 제품을 선택하고 **재고 출처 지정**.
1. 클릭 **저장 및 닫기** 을 클릭하여 프로세스를 완료합니다.

   이제에 메시지가 표시되는 것이 좋습니다. [!DNL RabbitMQ] 웹 콘솔.

1. 시작 `async.operations.all` 메시지 큐 소비자.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

이제 대기 중인 메시지가 [!DNL RabbitMQ] 웹 콘솔.
관리자에서 제품에 대한 인벤토리 소스가 변경되었는지 확인합니다.
