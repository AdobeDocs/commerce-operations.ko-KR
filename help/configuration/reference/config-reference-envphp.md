---
title: env.php 참조
description: env.php 파일의 값 목록을 참조하십시오.
source-git-commit: 7ecd54b40690ec046e9a3d46a6ef9ad44ffaf4ab
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# env.php 참조

다음 `env.php` 파일에는 다음 섹션이 포함되어 있습니다.

| 이름 | 설명 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 관리 영역에 대한 설정 |
| `cache` | 빨간색 페이지 및 기본 캐시 구성 |
| `cache_types` | 캐시 저장소 설정 |
| `consumers_wait_for_messages` | 소비자가 메시지 큐에서 메시지를 처리하는 방법을 구성합니다 |
| `cron` | 클론 작업 활성화 또는 비활성화 |
| `crypt` | 암호화 기능에 대한 암호화 키 |
| `db` | 데이터베이스 연결 설정 |
| `default_connection` | 메시지 큐 기본 연결 |
| `directories` | 전자 상거래 디렉터리 매핑 설정 |
| `downloadable_domains` | 다운로드 가능한 도메인 목록 |
| `install` | 설치 날짜 |
| `lock` | 공급자 설정 잠금 |
| `MAGE_MODE` | 다음 [애플리케이션 모드](../bootstrap/application-modes.md) |
| `queue` | [메시지 큐](../queues/manage-message-queues.md) 설정 |
| `resource` | 연결에 리소스 이름 매핑 |
| `session` | 세션 저장소 데이터 |
| `system` | 관리자에서 편집할 필드를 비활성화합니다 |
| `x-frame-options` | 설정 대상 [x-frame-options][x-frame-options] |

## 백엔드

구성 **frontName** 를 사용하는 상거래 관리 url용 `backend` env.php의 노드.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 캐시

을 사용하여 빨간색 페이지 및 기본 캐싱 구성 `cache` 노드의 `env.php` 파일.

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

추가 정보 [Redis 구성](../cache/redis-pg-cache.md).

## cache_types

모든 캐시 유형 구성은 이 노드에서 사용할 수 있습니다.

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

다른 항목에 대해 자세히 알아보기 [캐시 유형](../cli/manage-cache.md).

## consumer_wait_for_messages

처리된 메시지 수가 `max_messages` 값. 기본값은 입니다. `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

다음 옵션을 사용할 수 있습니다.

- `1`—소비자가 메시지 큐에서 메시지를 계속 처리하여 `max_messages` 에 지정된 값 `env.php` TCP 연결을 닫고 소비자 프로세스를 종료하기 전 파일 에 도달하기 전에 큐가 비어 있는 경우 `max_messages` 값이 있어야 합니다.

   지속적인 메시지 흐름이 예상되고 처리 지연이 발생할 수 있으므로 대규모 판매자에 대해 이 설정을 사용하는 것이 좋습니다.

- `0`—소비자가 대기열에서 사용 가능한 메시지를 처리하고 TCP 연결을 닫고 종료합니다. 소비자는 처리된 메시지 수가 `max_messages` 에 지정된 값 `env.php` 파일. 이로 인해 메시지 큐 처리가 지연되어 크론 작업에 문제가 발생하지 않을 수 있습니다.

   메시지 흐름이 일정하지 않을 것으로 예상되는 소규모 판매점을 위해 이 설정을 추천합니다. 며칠동안 메시지가 없을 수 있는 경우에 약간의 처리 지연이 발생하는 대신 컴퓨팅 리소스를 보존하려는 것이 좋습니다.

## cron

상거래 응용 프로그램에 대해 크론 작업을 활성화하거나 비활성화합니다. 기본적으로 크론 작업이 활성화됩니다. 비활성화하려면 `cron` 구성 `env.php` 파일 및 값을 `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron 작업을 비활성화할 때는 주의하십시오. 비활성화되면 상거래 응용 프로그램에 필요한 필수 프로세스가 실행되지 않습니다.

추가 정보 [크론](../cli/configure-cron-jobs.md).

## 암호화

Commerce는 암호 및 기타 중요한 데이터를 보호하기 위해 암호화 키를 사용합니다. 이 키는 설치 프로세스 중에 생성됩니다.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

추가 정보 [암호화 키](https://docs.magento.com/user-guide/system/encryption-key.html) 에서 _상거래 사용 안내서_.

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

메시지 큐에 대한 기본 연결을 정의합니다. 값은 `db`, `amqp`또는 다음과 같은 사용자 지정 큐 시스템 `redismq`. 다음 이외의 값을 지정하는 경우 `db`: 먼저 메시지 큐 소프트웨어를 설치 및 구성해야 합니다. 그렇지 않으면 메시지가 올바르게 처리되지 않습니다.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

If `queue/default_connection` 시스템에 지정되어 있습니다. `env.php` 파일에서 특정 연결을 정의하지 않는 한, 이 연결은 시스템을 통한 모든 메시지 큐에 사용됩니다 `queue_topology.xml`, `queue_publisher.xml` 또는 `queue_consumer.xml` 파일.
예를 들어 `queue/default_connection` is `amqp` in `env.php` 하지만 `db` 모듈의 큐 구성 XML 파일에 연결이 지정되어 있으므로 이 모듈은 MySQL을 메시지 브로커로 사용합니다.

## 디렉토리

웹 서버가 `/pub` 디렉토리 [향상된 보안][change-docroot-to-pub].

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

이 노드에서 사용할 수 있는 다운로드 가능한 도메인 목록입니다. CLI 명령을 사용하여 추가 도메인을 추가, 제거 또는 나열할 수 있습니다.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

추가 정보 [다운로드 가능한 도메인](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## 설치

상거래 응용 프로그램의 설치 날짜입니다.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 잠금

공급자 잠금 설정은 `lock` 노드 아래에 있어야 합니다.

추가 정보 [공급자 구성 잠금][lock-provider-config].

## MAGE_MODE

이 노드에서 배포 모드를 구성할 수 있습니다.

```conf
'MAGE_MODE' => 'developer'
```

추가 정보 [애플리케이션 모드](../cli/set-mode.md).

## 큐

메시지 큐 구성은 이 노드에서 사용할 수 있습니다.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

추가 정보 [메시지 큐][message-queue].

## 리소스

리소스 구성 설정은 이 노드에서 사용할 수 있습니다.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## 세션

세션 구성은 `session` 노드 아래에 있어야 합니다.

```conf
'session' => [
  'save' => 'files'
],
```

추가 정보 [Session](../storage/sessions.md).

## x-frame-options

이 노드를 사용하여 x-frame-options 헤더를 구성할 수 있습니다.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

추가 정보 [x-frame-options](../security/xframe-options.md).

## 시스템

이 노드를 사용하면 Commerce는 `env.php` 파일을 만든 다음 관리자의 필드를 비활성화합니다.

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

추가 정보 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[change-docroot-to-pub]: https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html
[encryption-key]: https://docs.magento.com/user-guide/system/encryption-key.html
[lock-provider-config]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-lock.html
[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
