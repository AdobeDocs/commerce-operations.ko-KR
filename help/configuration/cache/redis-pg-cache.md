---
title: 기본 캐시에 Redis 사용
description: Redis를 Adobe Commerce 및 Magento Open Source의 기본 캐시로 구성하는 방법을 배웁니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# 기본 캐시에 Redis 사용

Commerce에서는 Redis 페이지와 기본 캐싱을 구성하는 명령줄 옵션을 제공합니다. 을 편집하여 캐싱을 구성할 수 있지만 `<Commerce install dir>app/etc/env.php` 특히 초기 구성에 대해서는 명령줄에서 을(를) 사용하는 것이 좋습니다. 명령줄에서 유효성 검사를 제공하여 구성이 문법적으로 정확한지 확인합니다.

다음을 수행해야 합니다. [Redis 설치](config-redis.md#install-redis) 계속하기 전에

## Redis 기본 캐싱 구성

를 실행합니다. `setup:config:set` Redis 기본 캐싱에 해당하는 매개 변수를 명령 및 지정합니다.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter_name>=<parameter_value>...
```

여기서

`--cache-backend=redis` Redis 기본 캐싱을 활성화합니다. 이 기능을 이미 활성화한 경우에는 이 매개 변수를 생략하십시오.

`--cache-backend-redis-<parameter_name>=<parameter_value>` 는 기본 캐싱을 구성하는 키 및 값 쌍 목록입니다.

| 명령줄 매개 변수 | 매개 변수 | 의미 | 기본값 |
|--- |--- |--- |--- |
| cache-backend-redis-server | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓의 절대 경로. 기본값 127.0.0.1은 Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | 127.0.0.1 |
| cache-backend-redis-port | 포트 | Redis 서버 수신 포트 | 6379년 |
| cache-backend-redis-db | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필요합니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 0을 사용합니다.<br><br>중요 사항: 두 개 이상의 캐싱 유형에 Redis를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호를 0에, 페이지 캐싱 데이터베이스 번호는 1에, 세션 저장소 데이터베이스 번호는 2에 지정하는 것이 좋습니다. | 0 |
| cache-backend-redis-password | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나가 활성화됩니다. a `auth` 명령: 클라이언트가 데이터베이스에 액세스할 수 있도록 인증해야 합니다. 암호는 Redis 구성 파일에 직접 구성됩니다. `/etc/redis/redis.conf`. |  |

### 예제 명령

다음 예에서는 Redis 기본 캐싱을 활성화하고 호스트를 로 설정합니다. `127.0.0.1` 데이터베이스 번호를 0에 할당합니다. Redis에서는 다른 모든 매개 변수에 기본값을 사용합니다.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis 페이지 캐싱 구성

상거래 시 Redis 페이지 캐싱을 구성하려면 `setup:config:set` 추가 매개 변수를 사용하는 명령

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter_name>=<parameter_value>...
```

여기서

`--page-cache=redis` 빨간색 페이지 캐싱을 활성화합니다. 이 기능을 이미 활성화한 경우에는 이 매개 변수를 생략하십시오.

`--page-cache-redis-<parameter_name>=<parameter_value>` 페이지 캐싱을 구성하는 매개 변수/값 쌍 목록입니다.

| 명령줄 매개 변수 | 매개 변수 | 의미 | 기본값 |
|--- |--- |--- |--- |
| page-cache-redis-server | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓의 절대 경로. 기본값 127.0.0.1은 Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | 127.0.0.1 |
| page-cache-redis-port | 포트 | Redis 서버 수신 포트 | 6379년 |
| page-cache-redis-db | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필요합니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 0을 사용합니다.<br/>중요 사항: 두 개 이상의 캐싱 유형에 Redis를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호를 0에, 페이지 캐싱 데이터베이스 번호는 1에, 세션 저장소 데이터베이스 번호는 2에 지정하는 것이 좋습니다. | 0 |
| page-cache-redis-password | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나가 활성화됩니다. a `auth` 명령: 클라이언트가 데이터베이스에 액세스할 수 있도록 인증해야 합니다. Redis 구성 파일 /etc/redis/redis.conf에서 암호를 구성합니다. |  |

### 예제 명령

다음 예에서는 Redis 페이지 캐싱을 활성화하고 호스트를 로 설정합니다. `127.0.0.1` 데이터베이스 번호를 1에 할당합니다. 다른 모든 매개 변수는 기본값으로 설정됩니다.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 결과

두 가지 예제 명령의 결과로 Commerce는 다음과 유사한 라인을 `<Commerce install dir>app/etc/env.php`:

```php
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
],
```

## EC2 인스턴스에서 AWS ElastiCache 사용

Commerce 2.4.3부터 Amazon EC2에서 호스팅되는 인스턴스는 로컬 Redis 인스턴스 대신 AWS ElastiCache를 사용할 수 있습니다.

>[!WARNING]
>
>이 섹션은 Amazon EC2 VPC에서 실행되는 상거래 인스턴스에만 작동합니다. 온-프레미스 설치에서는 작동하지 않습니다.

### Redis 클러스터 구성

후 [AWS에서 Redis 클러스터 설정](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)를 사용하여 ElastiCache를 사용하도록 EC2 인스턴스를 구성합니다.

1. [ElastiCache 클러스터 만들기](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) 동일한 리전 및 EC2 인스턴스의 VPC에 있는 경우
1. 연결을 확인합니다.

   - EC2 인스턴스에 대한 SSH 연결 열기
   - EC2 인스턴스에서 Redis 클라이언트를 설치합니다.

      ```bash
      sudo apt-get install redis
      ```

   - EC2 보안 그룹에 인바운드 규칙 추가: 유형 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache 클러스터 보안 그룹에 인바운드 규칙 추가: 유형 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLI에 접속:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### 클러스터를 사용하도록 상거래 구성

Commerce에서는 여러 유형의 캐싱 구성을 지원합니다. 일반적으로 캐싱 구성은 프런트 엔드 및 백엔드 간에 분할됩니다. 프런트 엔드 캐싱은 모든 캐시 유형에 사용되는 &#39;기본값&#39;으로 분류됩니다. 하위 수준 캐시를 사용자 지정하거나 분할하여 더 나은 성능을 얻을 수 있습니다. 일반적인 Redis 구성은 기본 캐시 및 페이지 캐시를 고유한 RDB(Redis Database)로 분리하는 것입니다.

실행 `setup` 교정 끝점을 지정하는 명령

Redis에 대한 상거래를 기본 캐싱으로 구성:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Redis 페이지 캐싱에 대한 상거래 구성:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

세션 저장소에 Redis를 사용하도록 상거래 구성:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 연결 확인

Commerce가 ElasiCache와 통신하는지 확인하려면:

1. 상거래 EC2 인스턴스에 SSH 연결을 엽니다.
1. Redis 모니터를 시작합니다.

   ```bash
   redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port> monitor
   ```

1. 상거래 UI에서 페이지를 엽니다.
1. 확인 [캐시 출력](#verify-redis-connection) 터미널.

## 새로운 Redis 캐시 구현

Commerce 2.3.5부터는 확장된 Redis 캐시 구현을 사용하는 것이 좋습니다. `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Redis 사전 로드 기능

Commerce는 Redis 캐시에 많은 구성 데이터를 저장하므로 페이지 간에 다시 사용되는 데이터를 미리 로드할 수 있습니다.
미리 로드해야 하는 키를 찾으려면 Redis에서 Commerce로 전송되는 데이터를 분석해야 합니다. 모든 페이지에 로드되는 데이터를 미리 로드하는 것이 좋습니다. 일반적인 예는 다음과 같습니다 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.
레디스는 `pipeline` 로드 요청을 종합하려면
예를들어 데이터베이스 접두사가 다음과 같은 경우 키는 데이터베이스 접두사를 포함해야 합니다 `061_`, 사전 로드 키의 모습은 다음과 같습니다. `061_SYSTEM_DEFAULT`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

L2 캐시와 함께 사전 로드 기능을 사용하는 경우 L2 캐시는 데이터 자체가 아닌 데이터의 해시만 전송하므로 키에 &#39;:hash&#39; 접미사를 추가하는 것을 잊지 마십시오.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 병렬 생성

2.4.0 릴리스부터 `allow_parallel_generation` 잠금 대기 시간을 제거하려는 사용자에 대한 옵션입니다.
기본적으로 비활성화되어 있으며, 구성 및/또는 블록이 너무 많을 때까지 비활성화하는 것이 좋습니다.

**병렬 생성을 사용하려면**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

플래그이므로 명령으로 비활성화할 수 없습니다. 구성 값을 수동으로 로 설정해야 합니다. `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Redis 연결 확인

Redis와 Commerce가 함께 작동하는지 확인하려면 Redis를 실행하는 서버에 로그인하고 터미널을 열고 Redis 모니터 명령 또는 ping 명령을 사용합니다.

### Redis monitor 명령

```bash
redis-cli monitor
```

샘플 페이지 캐싱 출력:

```terminal
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Redis ping 명령

```bash
redis-cli ping
```

`PONG` 은 응답이어야 합니다.

두 명령이 모두 성공하면 Redis가 올바르게 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터 및 페이지 캐시를 검사하려면 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) 에서는 Commerce 2 Session 및 Page 캐시의 자동 압축 해제를 지원하고 사용자가 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.
