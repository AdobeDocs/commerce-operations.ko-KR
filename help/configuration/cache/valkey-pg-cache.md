---
title: 기본 및 페이지 캐시에 대한 값 구성
description: Adobe Commerce용 기본 및 페이지 캐시 백엔드로 Valkey를 구성하는 방법에 대해 알아봅니다. CLI 명령, env.php 설정 및 연결 확인을 살펴보십시오.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---


# 기본 및 페이지 캐시에 대한 값 구성

Commerce은 Valkey 기본 및 페이지 캐싱을 구성하는 명령줄 옵션을 제공합니다. `<Commerce-install-dir>app/etc/env.php` 파일을 편집하여 캐싱을 구성할 수 있지만 특히 초기 구성의 경우 명령줄을 사용하는 것이 좋습니다. 명령줄에서 유효성 검사를 제공하여 구성이 문법적으로 정확한지 확인합니다.

**필수 구성 요소:**

계속하기 전에 [Valkey](config-valkey.md#install-valkey)을(를) 설치하십시오.

## 지원되는 프레임워크


>[!BEGINTABS]

>[!TAB Zend 캐시(2.4.8 및 이전 버전)]

- **Zend 캐시(2.4.8 및 이전 버전)** — Commerce 2.4.8 및 이전 버전용 기존 Valkey 백엔드:
   - **기존 Valkey 백 엔드** — 전체 클래스 경로(`Magento\Framework\Cache\Backend\Valkey`)를 사용합니다.
   - **미리 로드 키** — 자주 사용하는 캐시 키를 미리 로드할 수 있습니다.
   - **Lua 스크립트** — 가비지 수집용 Lua
   - **압축** — 데이터 압축을 지원합니다.

>[!TAB Symfony 캐시(2.4.9+)]

- **Symfony 캐시(2.4.9+)** — Commerce 2.4.9부터 Symfony 캐시는 Valkey에 대한 최신 PSR-6 호환 캐싱 구현을 제공하며 성능이 크게 향상되었습니다.
   - **자동 유효성 검사 파이프라인** — 여러 작업을 단일 요청으로 일괄 처리하여 지연을 줄입니다.
   - **PSR-6 TagAwareAdapter** - 작은 단위의 작업으로 효율적인 태그 기반 캐시 무효화
   - **Igbinary serialization** — 이진 serialization은 캐시 항목 크기를 45% 줄이고 속도를 5-10% 향상시킵니다.
   - **향상된 영구 연결** - 포크된 프로세스를 더 잘 처리하여 보다 안정적인 연결 풀링
   - **최적화된 Lua 스크립트** — 최대 효율성을 위해 파이프라인과 결합된 서버측 실행

>[!ENDTABS]

## 유효한 기본 캐싱 구성

`setup:config:set` 명령을 실행하고 Valkey 기본 캐싱에 대한 매개 변수를 지정하십시오.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`은(는) Valkey 기본 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--cache-backend-valkey-<parameter>=<value>`은(는) 기본 캐싱을 구성하는 키-값 쌍의 목록입니다.

{{valkey-redis-cli-note}}

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값인 `127.0.0.1`은(는) Valkey가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `cache-backend-valkey-port` | 포트 | Valkey 서버 수신 포트 | `6379` |
| `cache-backend-valkey-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Valkey를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정하십시오. 다른 캐시는 기본적으로 `0`을(를) 사용합니다.<br><br>**중요**: 둘 이상의 캐싱 유형에 Valkey를 사용하는 경우 데이터베이스 번호는 서로 달라야 합니다. Adobe에서는 기본 캐싱 데이터베이스 번호를 `0`에, 페이지 캐싱 데이터베이스 번호를 `1`에, 세션 저장소 데이터베이스 번호를 `2`에 할당할 것을 권장합니다. | `0` |
| `cache-backend-valkey-password` | 암호 | Valkey 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 기능을 사용하려면 클라이언트가 데이터베이스에 액세스하기 위해 인증해야 합니다. 암호가 Valkey의 구성 파일에 직접 구성되어 있습니다. `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | LUA를 활성화하거나 비활성화합니다. <br><br>**LUA**: Lua를 사용하면 Valkey 내에서 응용 프로그램 논리의 일부를 실행할 수 있으므로 성능이 향상되고 작은 단위의 실행을 통해 데이터 일관성이 보장됩니다. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | 가비지 수집에 LUA를 활성화하거나 비활성화합니다. <br><br>**LUA**: Lua를 사용하면 Valkey 내에서 응용 프로그램 논리의 일부를 실행할 수 있으므로 성능이 향상되고 작은 단위의 실행을 통해 데이터 일관성이 보장됩니다. | `1` |

## 예제 명령(기본 캐시)

다음 예제에서는 Valkey 기본 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 `0`(으)로 할당합니다. Valkey는 다른 모든 매개 변수에 기본값을 사용합니다.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## 유효한 페이지 캐싱 구성

Commerce에서 Valkey 페이지 캐싱을 구성하려면 추가 매개 변수와 함께 `setup:config:set` 명령을 실행합니다.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--page-cache=valkey`이(가) 올바른 페이지 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--page-cache-valkey-<parameter>=<value>`은(는) 페이지 캐싱을 구성하는 키 및 값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본값 |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값인 `127.0.0.1`은(는) Valkey가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `page-cache-valkey-port` | 포트 | 유효한 서버 수신 포트입니다. | `6379` |
| `page-cache-valkey-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Valkey를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정하십시오. 다른 캐시는 기본적으로 `0`을(를) 사용합니다.<br/>**중요**: 둘 이상의 캐싱 유형에 Valkey를 사용하는 경우 데이터베이스 번호는 서로 달라야 합니다. 기본 캐싱 데이터베이스 번호를 `0`에, 페이지 캐싱 데이터베이스 번호를 `1`에, 세션 저장소 데이터베이스 번호를 `2`에 할당하는 것이 좋습니다. | `0` |
| `page-cache-valkey-password` | 암호 | Valkey 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 기능을 사용하려면 클라이언트가 데이터베이스에 액세스하기 위해 인증해야 합니다. Valkey 구성 파일 `/etc/valkey/valkey.conf` 내에서 암호를 구성하십시오. | |

### 예제 명령(페이지 캐시)

다음 예제에서는 Valkey 페이지 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 `1`(으)로 할당합니다. 다른 모든 매개변수는 기본값으로 설정됩니다.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Commerce 환경 구성 검토

Valkey 캐싱을 구성하는 명령을 실행하면 Commerce 환경 구성(`<Commerce-install-dir>app/etc/env.php`)이 업데이트됩니다.

>[!BEGINTABS]

>[!TAB Zend 캐시(2.4.8 및 이전 버전)]

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

>[!TAB Symfony 캐시(2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>Commerce 2.4.9부터 전체 클래스 경로 대신 간소화된 백엔드 유형 `'backend' => 'valkey'`을(를) 사용합니다. 간소화된 이름을 지정하면 Sympony Cache가 자동으로 사용됩니다.

>[!ENDTABS]

## 추가 캐싱 옵션 구성

### 키 미리 로드 기능 확인

Commerce은 구성 데이터를 Valkey 캐시에 저장하므로 페이지 간에 재사용되는 데이터를 미리 로드할 수 있습니다. 미리 로드해야 하는 키를 찾으려면 Valkey에서 Commerce으로 전송되는 데이터를 분석하십시오. Adobe에서는 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` 및 `DB_IS_UP_TO_DATE`과(와) 같이 모든 페이지에 로드되는 데이터를 미리 로드할 것을 제안합니다.

Valkey는 `pipeline`을(를) 사용하여 로드 요청을 합성합니다. 키에는 데이터베이스 접두사가 포함되어야 합니다. 예를 들어 데이터베이스 접두사가 `061_`이면 미리 로드 키는 `061_SYSTEM_DEFAULT`과(와) 같습니다.

>[!BEGINTABS]

>[!TAB Zend 캐시]

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

>[!TAB 교감 캐시]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
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

>[!ENDTABS]

L2 캐시에서 미리 로드 기능을 사용하는 경우 키에 `:hash` 접미사를 추가해야 합니다. L2 캐시는 실제 데이터가 아닌 데이터의 해시만 전송합니다.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 병렬 생성

Commerce 2.4.0 릴리스부터 Adobe에서는 잠금 대기를 없애려는 사용자를 위해 `allow_parallel_generation` 옵션을 도입했습니다. 이 기능은 기본적으로 비활성화되어 있으며, Adobe에서는 구성 및/또는 블록이 과도하게 설정될 때까지 비활성화하는 것이 좋습니다.

**병렬 생성을 사용하려면**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

플래그이므로 명령으로 비활성화할 수 없습니다. 수동으로 구성 값을 `false`(으)로 설정:

>[!BEGINTABS]

>[!TAB Zend 캐시]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB 교감 캐시]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Sympony 캐시 성능 최적화

Symfony Cache를 사용하는 경우 Igbinary 직렬 변환기를 구성하고, igbinary PHP 확장과 phpredis 확장을 설치하고 영구 연결을 활성화하여 성능을 더욱 최적화할 수 있습니다.

### Igbinary 직렬 변환기

Igbinary 직렬 변환기는 PHP의 기본 직렬화에 비해 상당한 성능 향상을 제공합니다. `app/etc/env.php`에서 수동으로 구성해야 합니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### PHP Igbinary 확장 설치

igbinary serialization을 사용하려면 PHP Igbinary 확장을 설치해야 합니다.

**apt 사용(Debian/Ubuntu 권장)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**pecl(대체 메서드) 사용**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis 확장: phpredis vs Predis

Commerce 2.4.9+에는 phpredis(기본 C 확장) 및 Predis(순수 PHP 라이브러리) 간 자동 대체 기능이 포함되어 있습니다. 최적의 성능을 위해 phpredis 설치:

**apt 사용(Debian/Ubuntu 권장)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**pecl(대체 메서드) 사용**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**성능 비교**:

| 작업 | 프레디스 | 프프레디스 | 개선 사항 |
|-----------|--------|----------|-------------|
| 캐시 GET | 1-5ms | 0.5-2ms | 2~3배 더 빠름 |
| 캐시 집합 | 2-6ms | 0.8-2.5ms | 2~3배 더 빠름 |
| 태그 작업 | 10-30ms | 3-10ms | 3~4배 빠름 |

### 영구 연결

영구 연결은 요청 간에 기존 Valkey 연결을 재사용하여 5~15% 더 빠른 캐시 작업을 제공합니다. `app/etc/env.php`에서 구성:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>각 캐시 유형에 대해 고유한 `persistent_id`을(를) 사용하여 연결 충돌을 방지하십시오.

### 최적화된 전체 구성

모든 성능 최적화를 결합한 프로덕션 준비 구성은 다음과 같습니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Valkey 연결 확인

Valkey와 Commerce이 제대로 작동하는지 확인하려면 다음을 수행하십시오.

1. Valkey 및 Commerce을 실행하는 서버에 로그인합니다.
1. 터미널을 엽니다.
1. `valkey-cli monitor` 명령 또는 `valkey-cli ping` 명령을 사용하여 연결을 확인하십시오.

명령이 성공하면 Valkey 가 실행 중이고 Commerce 애플리케이션과 통신할 수 있습니다. 실패할 경우 Valkey와 Commerce 간 연결 문제를 해결해야 합니다.

### Valkey monitor 명령

```shell
valkey-cli monitor
```

샘플 페이지 캐싱 출력:

```text
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

```shell
valkey-cli ping
```

필요한 응답은 `PONG`입니다.

두 명령이 모두 성공하면 Valkey가 제대로 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터와 페이지 캐시를 검사하려면 [RESP.app](https://flathub.org/apps/app.resp.RESP) 도구를 사용하십시오. Commerce 2 세션 및 페이지 캐시 데이터의 자동 압축 해제를 지원하며 사람이 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.

