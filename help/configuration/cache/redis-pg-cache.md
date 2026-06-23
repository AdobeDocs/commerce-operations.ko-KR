---
title: 기본 및 페이지 캐시에 대한 Redis 구성
description: Adobe Commerce용 기본 및 페이지 캐시 백엔드로 Redis를 구성하는 방법에 대해 알아봅니다. CLI 명령, env.php 설정 및 연결 확인을 살펴보십시오.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1485
ht-degree: 0%

---

# 기본 및 페이지 캐시에 대한 Redis 구성

{{cloud-cache-config}}

Commerce은 Redis 페이지 및 기본 캐싱을 구성하는 명령줄 옵션을 제공합니다. `<Commerce-install-dir>app/etc/env.php` 파일을 편집하여 캐싱을 구성할 수 있지만 특히 초기 구성의 경우 명령줄을 사용하는 것이 좋습니다. 명령줄에서 유효성 검사를 제공하여 구성이 문법적으로 정확한지 확인합니다.

**필수 구성 요소:**

계속하기 전에 [Redis 설치](config-redis.md#install-redis).

>[!NOTE]
>
>EC2에서 호스팅되는 Commerce 인스턴스의 경우 로컬 Redis 인스턴스 대신 AWS ElastiCache를 사용할 수 있습니다. [EC2 인스턴스에 대한 Elasticache 구성](redis-elasticache-for-ec2.md)을 참조하십시오.

## 지원되는 프레임워크

>[!BEGINTABS]

>[!TAB Zend 캐시(2.4.8 및 이전 버전)]

- **Zend 캐시(2.4.8 및 이전 버전)** — Commerce 2.4.8 및 이전 버전용 레거시 Redis 백엔드:
   - **기존 Redis 백엔드** — 전체 클래스 경로(`Magento\Framework\Cache\Backend\Redis`)를 사용합니다.
   - **미리 로드 키** — 자주 사용하는 캐시 키를 미리 로드할 수 있습니다.
   - **Lua 스크립트** — 가비지 수집용 Lua
   - **압축** — 데이터 압축을 지원합니다.

>[!TAB Symfony 캐시(2.4.9+)]

- **Symfony 캐시(2.4.9+)** — Commerce 2.4.9부터 Symfony 캐시는 Redis에 대한 최신 PSR-6 호환 캐싱 구현을 제공하며 성능이 크게 향상되었습니다.
   - **자동 Redis 파이프라인** — 여러 작업을 단일 요청으로 일괄 처리하여 지연을 줄입니다.
   - **PSR-6 TagAwareAdapter** - 작은 단위의 작업으로 효율적인 태그 기반 캐시 무효화
   - **Igbinary serialization** — 이진 serialization은 캐시 항목 크기를 45% 줄이고 속도를 5-10% 향상시킵니다.
   - **향상된 영구 연결** - 포크된 프로세스를 더 잘 처리하여 보다 안정적인 연결 풀링
   - **최적화된 Lua 스크립트** — 최대 효율성을 위해 파이프라인과 결합된 서버측 실행

>[!ENDTABS]


## Redis 기본 캐싱 구성

`setup:config:set` 명령을 실행하고 Redis 기본 캐싱과 관련된 매개 변수를 지정합니다.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--cache-backend=redis`은(는) Redis 기본 캐싱을 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--cache-backend-redis-<parameter>=<value>`은(는) 기본 캐싱을 구성하는 키-값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본 값 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값 127.0.0.1은(는) Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `cache-backend-redis-port` | 포트 | Redis 서버 수신 포트 | `6379` |
| `cache-backend-redis-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정하십시오. 다른 캐시는 기본적으로 0을 사용합니다.<br><br>**중요**: 둘 이상의 캐싱 유형에 대해 Redis를 사용하는 경우 데이터베이스 번호는 달라야 합니다. 기본 캐싱 데이터베이스 번호는 0으로, 페이지 캐싱 데이터베이스 번호는 1로, 세션 저장소 데이터베이스 번호는 2로 지정하는 것이 좋습니다. | `0` |
| `cache-backend-redis-password` | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 경우 데이터베이스에 액세스하려면 클라이언트가 인증해야 합니다. Redis의 구성 파일에 암호가 직접 구성되었습니다. `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | 모든 Redis 작업에 대해 Lua 스크립트를 활성화하거나 비활성화합니다. <br><br>**기본값: `0`에서 유지.** Lua가 활성화되면 번들 Redis 라이브러리(1.17.x)에서 발생하는 알려진 성능 후퇴와 GraphQL 캐시 누락 문제를 방지하기 위해 Lua 모드가 기본적으로 비활성화됩니다. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | 가비지 수집(`backend_clean_cache` cron 작업)에 대한 Lua 스크립트를 활성화하거나 비활성화합니다. <br><br>**기본값: `1`에서 유지.** GC 중에 원자 태그 세트 정리를 보장하기 위해 의도적으로 활성화되었습니다. 이 조건이 없으면 캐시 저장 작업과 동시에 `backend_clean_cache` cron이 실행되어 캐시 항목이 캐시 태그 인덱스에 해당 레코드 없이 남아 있을 때 경합 조건이 발생할 수 있습니다. 이로 인해 태그 기반 무효화는 자동으로 실패합니다. 예를 들어 제품 가격을 업데이트하면 제품 캐시가 무효화되지 않고 대신 전체 캐시 플러시가 필요할 수 있습니다. | `1` |

### Lua 모드

Lua 모드가 활성화되면 `EVALSHA`을(를) 통해 서버측에서 실행되는 단일 원자 스크립트로 여러 Redis 작업(캐시 쓰기, 태그 업데이트, 가비지 수집)을 번들로 묶습니다. 이렇게 하면 동시 요청의 인터리빙이 방지됩니다. 예를 들어 캐시 항목과 해당 태그 멤버십이 함께 기록되도록 할 수 있습니다.

>[!WARNING]
>
>Adobe Commerce 버전에 대한 영향을 이해하지 못한 채 `use_lua` 및 `use_lua_on_gc`의 기본값을 변경하지 마십시오.
>
>- **`use_lua`**: Adobe Commerce 2.4.7 또는 2.4.8(라이브러리 `colinmollenhour/cache-backend-redis` 1.17.1)에서 이 기능을 사용하면 캐시 손상 및 GraphQL 캐시 누락 문제가 발생할 수 있습니다.
>- **`use_lua_on_gc`**: Adobe Commerce 2.4.8에서 이 기능을 사용하지 않도록 설정하면 가비지 수집 중에 원자 보호가 제거되며 태그 기반 캐시 무효화가 자동으로 실패하여 복구할 전체 캐시 플러시가 필요할 수 있습니다.

## 예제 명령(기본 캐시)

다음 예제에서는 Redis 기본 캐싱을 사용하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 0으로 할당합니다. Redis는 다른 모든 매개 변수에 기본값을 사용합니다.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis 페이지 캐싱 구성

Commerce에서 Redis 페이지 캐싱을 구성하려면 추가 매개 변수와 함께 `setup:config:set` 명령을 실행합니다.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

다음 매개 변수 사용:

- `--page-cache=redis`에서 Redis 페이지 캐싱을 사용할 수 있습니다. 이 기능을 이미 활성화한 경우에는 이 매개변수를 생략합니다.

- `--page-cache-redis-<parameter>=<value>`은(는) 페이지 캐싱을 구성하는 키 및 값 쌍의 목록입니다.

| 명령줄 매개 변수 | 값 | 의미 | 기본 값 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | 정규화된 호스트 이름, IP 주소 또는 UNIX 소켓에 대한 절대 경로입니다. 기본값 127.0.0.1은(는) Redis가 Commerce 서버에 설치되어 있음을 나타냅니다. | `127.0.0.1` |
| `page-cache-redis-port` | 포트 | Redis 서버 수신 포트 | `6379` |
| `page-cache-redis-db` | 데이터베이스 | 기본 및 전체 페이지 캐시 모두에 Redis를 사용하는 경우 필수입니다. 캐시 중 하나의 데이터베이스 번호를 지정하십시오. 다른 캐시는 기본적으로 0을 사용합니다.<br/>**중요**: 둘 이상의 캐싱 유형에 대해 Redis를 사용하는 경우 데이터베이스 번호는 달라야 합니다. 기본 캐싱 데이터베이스 번호는 0으로, 페이지 캐싱 데이터베이스 번호는 1로, 세션 저장소 데이터베이스 번호는 2로 지정하는 것이 좋습니다. | `0` |
| `page-cache-redis-password` | 암호 | Redis 암호를 구성하면 기본 제공 보안 기능 중 하나인 `auth` 명령을 사용할 수 있습니다. 이 경우 데이터베이스에 액세스하려면 클라이언트가 인증해야 합니다. Redis 구성 파일 `/etc/redis/redis.conf` 내에서 암호를 구성하십시오. | |

다음 예제에서는 Redis 페이지 캐싱을 활성화하고 호스트를 `127.0.0.1`(으)로 설정하고 데이터베이스 번호를 `1`(으)로 할당합니다. 다른 모든 매개변수는 기본값으로 설정됩니다.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Commerce 환경 구성 검토

Redis 캐싱을 구성하는 명령을 실행하면 Commerce 환경 구성(`<Commerce-install-dir>app/etc/env.php`)이 업데이트됩니다.

>[!BEGINTABS]

>[!TAB Zend 캐시(2.4.8 및 이전 버전)]

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

>[!TAB Symfony 캐시(2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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
>Commerce 2.4.9부터 전체 클래스 경로 대신 간소화된 백엔드 유형 `'backend' => 'redis'`을(를) 사용합니다. 간소화된 이름을 지정하면 Sympony Cache가 자동으로 사용됩니다.

>[!ENDTABS]

## 추가 캐싱 옵션 구성

### Redis 미리 로드 기능

Commerce은 구성 데이터를 Redis 캐시에 저장하기 때문에 페이지 간에 재사용되는 데이터를 미리 로드할 수 있습니다. 미리 로드해야 하는 키를 찾으려면 Redis에서 Commerce으로 전송되는 데이터를 분석하십시오. Adobe에서는 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` 및 `DB_IS_UP_TO_DATE`과(와) 같이 모든 페이지에 로드되는 데이터를 미리 로드할 것을 제안합니다.

Redis는 `pipeline`을(를) 사용하여 로드 요청을 합성합니다. 키에는 데이터베이스 접두사가 포함되어야 합니다. 예를 들어 데이터베이스 접두사가 `061_`이면 미리 로드 키는 `061_SYSTEM_DEFAULT`과(와) 같습니다.

>[!BEGINTABS]

>[!TAB Zend 캐시]

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

>[!TAB 교감 캐시]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'redis',
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

>[!TAB 교감 캐시]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
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
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
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
| 캐시 가져오기 | 1-5ms | 0.5-2ms | 2~3배 더 빠름 |
| 캐시 집합 | 2-6ms | 0.8-2.5ms | 2~3배 더 빠름 |
| 태그 작업 | 10-30ms | 3-10ms | 3~4배 빠름 |

### 영구 연결

영구 연결은 요청 간 기존 Redis 연결을 재사용하여 5~15% 더 빠른 캐시 작업을 제공합니다. `app/etc/env.php`에서 구성:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
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
                'server' => 'redis',
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

다음은 모든 성능 최적화를 결합한 프로덕션 준비 Symfony 구성입니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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

## Redis 연결 확인

Redis와 Commerce이 제대로 작동하는지 확인하려면 다음을 수행하십시오.

1. Redis 및 Commerce을 실행하는 서버에 로그인합니다.
1. 터미널을 엽니다.
1. `redis-cli monitor` 명령 또는 `redis-cli ping` 명령을 사용하여 연결을 확인하십시오.

명령이 성공하면 Redis가 실행 중이고 Commerce 애플리케이션과 통신할 수 있습니다. 오류가 발생하면 Redis와 Commerce 간 연결 문제를 해결해야 합니다.

### Redis 모니터 명령

```shell
redis-cli monitor
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
...
```

두 명령이 모두 성공하면 Redis가 제대로 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터와 페이지 캐시를 검사하려면 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) 도구를 사용하십시오. Commerce 2 세션 및 페이지 캐시 데이터의 자동 압축 해제를 지원하며 사람이 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.
