---
title: env.php 참조
description: env.php 파일의 값 목록을 참조하십시오.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# env.php 참조

`env.php` 파일에는 다음 섹션이 포함되어 있습니다.

| 이름 | 설명 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 관리 영역에 대한 설정 |
| `cache` | Redis 페이지 및 기본 캐시 구성 |
| `cache_types` | 캐시 저장소 설정 |
| `consumers_wait_for_messages` | 소비자가 메시지 큐의 메시지를 처리하는 방법 구성 |
| `cron` | cron 작업 활성화 또는 비활성화 |
| `crypt` | 암호화 기능의 암호화 키 |
| `db` | 데이터베이스 연결 설정 |
| `default_connection` | 메시지 대기열 기본 연결 |
| `directories` | Commerce 디렉터리 매핑 설정 |
| `downloadable_domains` | 다운로드 가능한 도메인 목록 |
| `install` | 설치 날짜 |
| `lock` | 공급자 설정 잠금 |
| `MAGE_MODE` | [응용 프로그램 모드](../bootstrap/application-modes.md) |
| `queue` | [메시지 큐](../queues/manage-message-queues.md) 설정 |
| `resource` | 연결에 리소스 이름 매핑 |
| `session` | 세션 저장소 데이터 |
| `system` | 관리자의 편집 필드 비활성화 |
| `x-frame-options` | [x-frame-options][x-frame-options]에 대한 설정 |

## 백엔드

env.php의 `backend` 노드를 사용하여 Commerce 관리 URL에 대한 **frontName**&#x200B;을(를) 구성합니다.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 캐시

`env.php` 파일에서 `cache` 노드를 사용하여 redis 페이지 및 기본 캐싱을 구성합니다.

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

[Redis 구성](../cache/redis-pg-cache.md)에서 자세히 알아보세요.

## cache_type

이 노드에서 모든 캐시 유형 구성을 사용할 수 있습니다.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

다른 [캐시 형식](../cli/manage-cache.md)에 대해 자세히 알아보세요.

## consumer_wait_for_messages

처리된 메시지 수가 `max_messages` 값보다 작은 경우 소비자가 메시지를 계속 폴링할지 여부를 지정합니다. 기본값은 `1`입니다.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

다음 옵션을 사용할 수 있습니다.

- `1`—TCP 연결을 닫고 소비자 프로세스를 종료하기 전에 소비자가 `env.php` 파일에 지정된 `max_messages` 값에 도달할 때까지 메시지 큐에서 메시지를 계속 처리합니다. `max_messages` 값에 도달하기 전에 큐를 비우면 소비자는 더 많은 메시지가 도착할 때까지 기다립니다.

  지속적인 메시지 흐름이 예상되고 처리 지연이 바람직하지 않으므로 대규모 판매자에 대해 이 설정을 권장합니다.

- `0` - 소비자가 큐에서 사용 가능한 메시지를 처리하고 TCP 연결을 닫고 종료합니다. 소비자는 처리된 메시지 수가 `env.php` 파일에 지정된 `max_messages` 값보다 적더라도 추가 메시지가 대기열에 들어갈 때까지 기다리지 않습니다. 이렇게 하면 메시지 큐 처리의 오랜 지연으로 인한 cron 작업 문제를 방지하는 데 도움이 될 수 있습니다.

  메시지 흐름이 일정하지 않고 며칠 동안 메시지가 없을 때 약간의 처리 지연에 대한 교환 조건으로 컴퓨팅 리소스를 보존하려는 소규모 가맹점에 이 설정을 권장합니다.

## cron

Commerce 애플리케이션에 대한 cron 작업을 활성화하거나 비활성화합니다. 기본적으로 cron job이 활성화되어 있습니다. 비활성화하려면 `cron` 구성을 `env.php` 파일에 추가하고 값을 `0`(으)로 설정하십시오.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron 작업을 비활성화할 때는 주의하십시오. 비활성화된 경우 Commerce 애플리케이션에 필요한 필수 프로세스는 실행되지 않습니다.

[크론](../cli/configure-cron-jobs.md)에 대해 자세히 알아보세요.

## 암호

Commerce은 암호 및 기타 중요한 데이터를 보호하기 위해 암호화 키를 사용합니다. 이 키는 설치 프로세스 중에 생성됩니다.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

_Commerce 사용 안내서_&#x200B;에서 [암호화 키](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/encryption-key)에 대해 자세히 알아보세요.

## db

모든 데이터베이스 구성은 이 노드에서 사용할 수 있습니다.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

메시지 대기열에 대한 기본 연결을 정의합니다. 값은 `db`, `amqp` 또는 `redismq`과(와) 같은 사용자 지정 큐 시스템일 수 있습니다. `db` 이외의 값을 지정하는 경우 먼저 메시지 큐 소프트웨어를 설치 및 구성해야 합니다. 그렇지 않으면 메시지가 올바르게 처리되지 않습니다.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

`queue/default_connection`이(가) 시스템 `env.php` 파일에 지정된 경우, 특정 연결이 `queue_topology.xml`, `queue_publisher.xml` 또는 `queue_consumer.xml` 파일에 정의되어 있지 않은 한 이 연결은 시스템을 통한 모든 메시지 큐에 사용됩니다.
예를 들어 `env.php`에서 `queue/default_connection`이(가) `amqp`이지만 모듈의 큐 구성 XML 파일에 `db` 연결이 지정된 경우 모듈은 MySQL을 메시지 브로커로 사용합니다.

## 디렉터리

웹 서버가 [향상된 보안](../../installation/tutorials/docroot.md)을 위해 `/pub` 디렉터리에서 Commerce 앱을 제공하도록 구성된 경우 설정해야 하는 선택적 디렉터리 매핑 옵션입니다.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

이 노드에서 사용할 수 있는 다운로드 가능한 도메인 목록입니다. 추가 도메인은 CLI 명령을 사용하여 추가, 제거 또는 나열할 수 있습니다.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

[다운로드 가능한 도메인](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd)에 대해 자세히 알아보세요.

## 설치

Commerce 애플리케이션 설치 날짜입니다.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 잠금

잠금 공급자 설정이 `lock` 노드를 사용하여 구성되었습니다.

[공급자 구성 잠금](../../installation/tutorials/lock-provider.md)에 대해 자세히 알아보세요.

## MAGE_모드

이 노드에서 배포 모드를 구성할 수 있습니다.

```conf
'MAGE_MODE' => 'developer'
```

[응용 프로그램 모드](../cli/set-mode.md)에 대해 자세히 알아보세요.

## 큐

이 노드에서 메시지 큐 구성을 사용할 수 있습니다.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

[메시지 큐][message-queue]에 대해 자세히 알아보세요.

## 리소스

이 노드에서 리소스 구성 설정을 사용할 수 있습니다.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

세션 구성은 `session` 노드에 저장됩니다.

```conf
'session' => [
  'save' => 'files'
],
```

[세션](../storage/sessions.md)에 대해 자세히 알아보세요.

## x-frame-options

이 노드를 사용하여 x-frame-options 헤더를 구성할 수 있습니다.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

[x-frame-options](../security/xframe-options.md)에 대해 자세히 알아보세요.

## 시스템

이 노드를 사용하면 Commerce은 `env.php` 파일의 구성 값을 잠근 다음 관리자의 필드를 비활성화합니다.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

자세한 내용은 [env-php-config-set](../cli/set-configuration-values.md)을 참조하세요.

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
