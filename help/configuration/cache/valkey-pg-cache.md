---
title: 기본 캐시에 Valkey 사용
description: Valkey를 Adobe Commerce의 기본 캐시로 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Cache
source-git-commit: 2891c8b2ff9cfae120d01605aad6eb543f01315d
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---

# 기본 캐시에 Valkey 사용

Commerce은 Valkey 페이지 및 기본 캐싱을 구성하는 명령줄 옵션을 제공합니다. `<Commerce-install-dir>app/etc/env.php` 파일을 편집하여 캐싱을 구성할 수 있지만 특히 초기 구성의 경우 명령줄을 사용하는 것이 좋습니다. 명령줄에서 유효성 검사를 제공하여 구성이 문법적으로 정확한지 확인합니다.

계속하려면 [Valkey를 설치](config-redis.md#install-redis)해야 합니다.

## 유효한 기본 캐싱 구성

`setup:config:set` 명령을 실행하고 Valkey 기본 캐싱에 대한 매개 변수를 지정하십시오.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`은(는) 올바른 기본 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--cache-backend-valkey-<parameter>=<value>`은(는) 기본 캐싱을 구성하는 키-값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값인 `127.0.0.1`은(는) Valkey가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `cache-backend-valkey-port` | 포트 | Valkey 서버 수신 포트 | `6379` |
| `cache-backend-valkey-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Valkey를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 `0`을(를) 사용합니다.<br><br>**중요**: 두 개 이상의 캐싱 형식에 Valkey를 사용하는 경우 데이터베이스 번호가 달라야 합니다. Adobe에서는 기본 캐싱 데이터베이스 번호를 `0`에, 페이지 캐싱 데이터베이스 번호를 `1`에, 세션 저장소 데이터베이스 번호를 `2`에 할당할 것을 권장합니다. | `0` |
| `cache-backend-valkey-password` | 암호 | Valkey 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 기능을 사용하려면 클라이언트가 데이터베이스에 액세스하기 위해 인증해야 합니다. 암호가 Valkey 구성 파일에 직접 구성되어 있습니다. `/etc/valkey/valkey.conf` | |

### 예제 명령

다음 예제에서는 Valkey 기본 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 `0`(으)로 할당합니다. Valkey는 다른 모든 매개 변수에 기본값을 사용합니다.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

## 페이지 캐싱 구성

Commerce에서 Valkey 페이지 캐싱을 구성하려면 추가 매개 변수와 함께 `setup:config:set` 명령을 실행합니다.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--page-cache=valkey`이(가) 올바른 페이지 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--page-cache-valkey-<parameter>=<value>`은(는) 페이지 캐싱을 구성하는 키 및 값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값인 `127.0.0.1`은(는) Valkey가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `page-cache-valkey-port` | 포트 | 유효한 서버 수신 포트입니다. | `6379` |
| `page-cache-valkey-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Valkey를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정해야 합니다. 다른 캐시는 기본적으로 `0`을(를) 사용합니다.<br/>**중요**: 두 개 이상의 캐싱 형식에 Valkey를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호를 `0`에, 페이지 캐싱 데이터베이스 번호를 `1`에, 세션 저장소 데이터베이스 번호를 `2`에 할당하는 것이 좋습니다. | `0` |
| `page-cache-valkey-password` | 암호 | Valkey 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 기능을 사용하려면 클라이언트가 데이터베이스에 액세스하기 위해 인증해야 합니다. Valkey 구성 파일 `/etc/valkey/valkey.conf` 내에서 암호를 구성하십시오. | |

### 예제 명령

다음 예제에서는 Valkey 페이지 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 `1`(으)로 할당합니다. 다른 모든 매개변수는 기본값으로 설정됩니다.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

## 결과

두 예제 명령의 결과로 Commerce은 `<Commerce-install-dir>app/etc/env.php`에 다음과 유사한 줄을 추가합니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## 새로운 Valkey 캐시 구현

[!BADGE 2.4.9-alpha]{type=Negative tooltip="2.4.9-alpha에서만 사용할 수 있습니다."}

Adobe Commerce Adobe 2.4.9부터 Valkey 캐시 구현을 사용하는 것이 좋습니다. `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## 키 미리 로드 기능 확인

Commerce은 구성 데이터를 Valkey 캐시에 저장하므로 페이지 간에 재사용되는 데이터를 미리 로드할 수 있습니다. 미리 로드해야 하는 키를 찾으려면 Valkey에서 Commerce으로 전송되는 데이터를 분석하십시오. Adobe에서는 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` 및 `DB_IS_UP_TO_DATE`과(와) 같이 모든 페이지에 로드되는 데이터를 미리 로드할 것을 제안합니다.

Valkey는 `pipeline`을(를) 사용하여 로드 요청을 합성합니다. 키에는 데이터베이스 접두사가 포함되어야 합니다. 예를 들어 데이터베이스 접두사가 `061_`이면 미리 로드 키는 `061_SYSTEM_DEFAULT`과(와) 같습니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

L2 캐시에서 미리 로드 기능을 사용하는 경우 키에 `:hash` 접미사를 추가해야 합니다. L2 캐시는 실제 데이터가 아닌 데이터의 해시만 전송합니다.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 병렬 생성

Commerce 2.4.0 릴리스부터 Adobe에서는 잠금 대기를 제거하려는 사용자를 위해 `allow_parallel_generation` 옵션을 도입했습니다.
이 기능은 기본적으로 비활성화되어 있으며, Adobe에서는 구성 및/또는 블록이 과도하게 설정될 때까지 비활성화하는 것이 좋습니다.

**병렬 생성을 사용하려면**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

플래그이므로 명령으로 비활성화할 수 없습니다. 구성 값을 `false`(으)로 수동으로 설정해야 합니다.

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Valkey 연결 확인

Valkey와 Commerce이 제대로 작동하는지 확인하려면 Valkey를 실행하는 서버에 로그인하고 터미널을 열고 `valkey-cli monitor` 명령 또는 `redis-cli ping` 명령을 사용합니다.

### Valkey monitor 명령

```bash
valkey-cli monitor
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

### Valkey ping 명령

```bash
redis-cli ping
```

필요한 응답은 `PONG`입니다.

두 명령이 모두 성공하면 Valkey가 제대로 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터와 페이지 캐시를 검사하기 위해 [RESP.app](https://flathub.org/apps/app.resp.RESP)은(는) Commerce 2 세션 및 페이지 캐시의 자동 압축 해제를 지원하고 사람이 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.
