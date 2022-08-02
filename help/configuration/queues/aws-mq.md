---
title: Amazon 메시지 큐 설정
description: AWS MQ 서비스를 사용하도록 Commerce를 구성하는 방법을 알아봅니다.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Amazon 메시지 큐 설정

Commerce 2.4.3부터 MQ(Amazon Message Queue)가 온-프레미스 메시지 큐 인스턴스에 대한 클라우드 지원 대체용으로 제공됩니다.

AWS에서 메시지 큐를 만들려면 다음을 참조하십시오 [Amazon MQ 설정](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 에서 _AWS 설명서_.

## AWS MQ에 대한 상거래 구성

AWS MQ 서비스에 연결하려면 다음을 구성합니다 `queue.amqp` 의 개체 `env.php` 파일.
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

- `host`- AMQP 끝점의 URL; AWS에서 broker 이름을 클릭하여 사용할 수 있습니다(제거 &quot;https://&quot; 및 후행 포트 번호).
- `user`- AWS MQ Broker를 만들 때 입력한 사용자 이름 값입니다
- `password`- AWS MQ Broker를 만들 때 입력한 암호 값입니다

>[!INFO]
>
>Amazon MQ는 TLS 연결만 지원합니다. 피어 확인이 지원되지 않습니다.

편집 후 `env.php` 파일에서 다음 명령을 실행하여 설치를 완료합니다.

```bash
bin/magento setup:upgrade
```

## Commerce에서 AWS MQ 서비스를 사용하는 방법

다음 `async.operations.all` 메시지 큐 소비자가 AMQP 연결을 사용합니다.

이 소비자는 `async` AWS MQ 연결 사용.

예, 에서 `InventoryCatalog` 다음 항목이 있습니다.

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

에 대한 기본 구성 `InventoryCatalog` rabbitMQ에 메시지를 게시하지 않습니다. 기본 동작은 동일한 사용자 스레드에서 작업을 수행하는 것입니다. 다음 `InventoryCatalog` 메시지를 게시하려면 다음을 활성화합니다 `cataloginventory/bulk_operations/async`. 관리자에서 로 이동합니다. **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 일괄 작업 및 설정  `Run asynchronously`to **예**.

## 메시지 큐 테스트

Commerce에서 RabbitMQ로 메시지 전송을 테스트하려면 다음을 수행하십시오.

1. AWS의 RabbitMQ 웹 콘솔에 로그인하여 큐를 모니터링합니다.
1. 관리자에서 제품을 만듭니다.
1. 인벤토리 소스를 만듭니다.
1. 활성화 **스토어** > 구성 > **카탈로그** > **인벤토리** > 관리 일괄 작업 > 비동기식으로 실행.
1. 이동 **카탈로그** > 제품. 그리드에서 위에서 만든 제품을 선택하고 **재고 출처 지정**.
1. 클릭 **저장 및 닫기** 프로세스를 완료합니다.

   이제 RabbitMQ 웹 콘솔에 메시지가 표시됩니다.

1. 시작 `async.operations.all` 메시지 큐 소비자.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

이제 RabbitMQ 웹 콘솔에서 큐에 있는 메시지가 처리됩니다.
관리자의 제품에서 재고 소스가 변경되었는지 확인합니다.
