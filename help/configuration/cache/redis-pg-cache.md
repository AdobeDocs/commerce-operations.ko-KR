---
title: 기본 캐시에 Redis 사용
description: Redis를 Adobe Commerce의 기본 캐시로 구성하는 방법에 대해 알아봅니다. 명령줄 설정, 구성 옵션 및 유효성 검사 기술을 살펴봅니다.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: ee4a873a73e8fd747e7d4c8e157327fab1074cc9
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# 기본 캐시에 Redis 사용

Commerce은 Redis 페이지 및 기본 캐싱을 구성하는 명령줄 옵션을 제공합니다. `<Commerce-install-dir>app/etc/env.php` 파일을 편집하여 캐싱을 구성할 수 있지만 특히 초기 구성의 경우 명령줄을 사용하는 것이 좋습니다. 명령줄에서 유효성 검사를 제공하여 구성이 문법적으로 정확한지 확인합니다.

계속하려면 [Redis를 설치](config-redis.md#install-redis)해야 합니다.

>[!NOTE]
>
>EC2에서 호스팅되는 Commerce 인스턴스의 경우 로컬 Redis 인스턴스 대신 AWS ElastiCache를 사용할 수 있습니다. [EC2 인스턴스에 대한 Elasticache 구성](redis-elasticache-for-ec2.md)을 참조하십시오.

## Redis 기본 캐싱 구성

`setup:config:set` 명령을 실행하고 Redis 기본 캐싱과 관련된 매개 변수를 지정합니다.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--cache-backend=redis`은(는) Redis 기본 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--cache-backend-redis-<parameter>=<value>`은(는) 기본 캐싱을 구성하는 키-값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값 127.0.0.1은(는) Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `cache-backend-redis-port` | 포트 | Redis 서버 수신 포트 | `6379` |
| `cache-backend-redis-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 0을 사용합니다.<br><br>**중요**: 둘 이상의 캐싱 형식에 대해 Redis를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호는 0으로, 페이지 캐싱 데이터베이스 번호는 1로, 세션 저장소 데이터베이스 번호는 2로 지정하는 것이 좋습니다. | `0` |
| `cache-backend-redis-password` | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 경우 데이터베이스에 액세스하려면 클라이언트가 인증해야 합니다. Redis의 구성 파일에 암호가 직접 구성되었습니다. `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | LUA를 활성화하거나 비활성화합니다. <br><br>**LUA**: Lua를 사용하면 Redis 내에서 응용 프로그램 논리의 일부를 실행할 수 있으므로 성능이 향상되고 작은 단위의 실행을 통해 데이터 일관성이 보장됩니다. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | 가비지 수집에 LUA를 활성화하거나 비활성화합니다. <br><br>**LUA**: Lua를 사용하면 Redis 내에서 응용 프로그램 논리의 일부를 실행할 수 있으므로 성능이 향상되고 작은 단위의 실행을 통해 데이터 일관성이 보장됩니다. | `1` |

### 예제 명령

다음 예제에서는 Redis 기본 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 0으로 할당합니다. Redis는 다른 모든 매개 변수에 기본값을 사용합니다.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis 페이지 캐싱 구성

Commerce에서 Redis 페이지 캐싱을 구성하려면 추가 매개 변수와 함께 `setup:config:set` 명령을 실행합니다.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--page-cache=redis`에서 Redis 페이지 캐싱을 사용할 수 있습니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--page-cache-redis-<parameter>=<value>`은(는) 페이지 캐싱을 구성하는 키 및 값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값 127.0.0.1은(는) Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `page-cache-redis-port` | 포트 | Redis 서버 수신 포트 | `6379` |
| `page-cache-redis-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 0을 사용합니다.<br/>**중요**: 둘 이상의 캐싱 형식에 대해 Redis를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호는 0으로, 페이지 캐싱 데이터베이스 번호는 1로, 세션 저장소 데이터베이스 번호는 2로 지정하는 것이 좋습니다. | `0` |
| `page-cache-redis-password` | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 경우 데이터베이스에 액세스하려면 클라이언트가 인증해야 합니다. Redis 구성 파일 `/etc/redis/redis.conf` 내에서 암호를 구성하십시오. | |

### 예제 명령

다음 예제에서는 Redis 페이지 캐싱을 활성화하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 1로 할당합니다. 다른 모든 매개변수는 기본값으로 설정됩니다.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Commerce 환경 구성 검토

Redis 캐싱을 구성하는 명령을 실행하면 Commerce 환경 구성(`<Commerce-install-dir>app/etc/env.php`)이 업데이트됩니다.

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

## 추가 캐싱 옵션 구성

이 섹션에서는 기본적으로 비활성화된 선택적 구성 설정을 활성화하는 방법에 대해 설명합니다.

### Redis 미리 로드 기능

Commerce은 구성 데이터를 Redis 캐시에 저장하기 때문에 페이지 간에 재사용되는 데이터를 미리 로드할 수 있습니다. 미리 로드해야 하는 키를 찾으려면 Redis에서 Commerce으로 전송되는 데이터를 분석하십시오. `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`과(와) 같이 모든 페이지에 로드되는 데이터를 미리 로드하는 것이 좋습니다.

Redis는 부하 요청을 합성하기 위해 `pipeline`을(를) 사용합니다. 키에는 데이터베이스 접두사가 포함되어야 합니다. 예를 들어 데이터베이스 접두사가 `061_`이면 미리 로드 키는 `061_SYSTEM_DEFAULT`과(와) 같습니다.

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

L2 캐시와 함께 미리 로드 기능을 사용하는 경우 L2 캐시는 데이터 자체가 아니라 데이터의 해시만 전송하므로 키에 `:hash` 접미사를 추가하는 것을 잊지 마십시오.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 병렬 생성

`allow_parallel_generation` 옵션을 활성화하여 잠금 대기를 제거하십시오.

이 옵션은 기본적으로 비활성화되어 있으며, Adobe에서는 구성 또는 블록이 많을 때까지 비활성화하는 것이 좋습니다.

**병렬 생성을 사용하려면**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

이 옵션은 플래그이므로 명령으로 비활성화할 수 없습니다. 구성 값을 `false`(으)로 수동으로 설정해야 합니다.

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

Redis와 Commerce이 함께 작동하는지 확인하려면 Redis를 실행하는 서버에 로그인하고 터미널을 열고 Redis 모니터 명령 또는 ping 명령을 사용합니다.

### Redis 모니터 명령

```bash
redis-cli monitor
```

샘플 페이지 캐싱 출력:

```
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

필요한 응답은 `PONG`입니다.

두 명령이 모두 성공하면 Redis가 제대로 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터와 페이지 캐시를 검사하기 위해 [RESP.app](https://flathub.org/apps/details/app.resp.RESP)은(는) Commerce 2 세션 및 페이지 캐시의 자동 압축 해제를 지원하고 사람이 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.
