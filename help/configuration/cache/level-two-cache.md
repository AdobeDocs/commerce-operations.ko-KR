---
title: 성능 최적화를 위한 L2 캐시 구성
description: 네트워크 트래픽을 줄이고 성능을 개선하기 위해 Adobe Commerce 온프레미스에서 L2 캐시를 구성하는 방법에 대해 알아봅니다. 기존 RemoteSynchronizedCache 구현을 최신 Symfony L2 구현과 비교합니다.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# 성능 최적화를 위한 L2 캐시 구성

L2(2수준) 캐싱은 각 웹 노드에 로컬 캐시 계층을 추가하여 원격 캐시 서비스와 Commerce 애플리케이션 간의 네트워크 트래픽을 줄입니다. 표준 Commerce 인스턴스는 요청당 약 300KB를 전송할 수 있습니다. 요청이 많은 볼륨에서는 네트워크 트래픽이 상당할 수 있습니다.

L2 캐싱을 사용하면 각 웹 노드는 자주 액세스하는 데이터를 로컬에 저장하고 원격 캐시를 두 가지 용도로 사용합니다.

- 최신 캐시가 로컬에 저장되어 있는지 확인하기 위해 캐시 데이터 버전 확인
- 원격 캐시 서비스에서 로컬 컴퓨터로 업데이트된 캐시 데이터 전송

Commerce은 해시된 데이터 버전을 원격 캐시에 저장하고, 일반 키에 접미사 `:hash`을(를) 추가합니다. 로컬 캐시가 오래된 경우 캐시 어댑터를 통해 원격 캐시 서비스에서 데이터를 가져옵니다.

사용 가능한 L2 캐시 구현은 Commerce 버전 및 패치 수준에 따라 다릅니다.

| 구현 | Commerce 버전 | 원격 캐시 서비스 | 설명 |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | 지원되는 경우 2.4.9 이전 | 릴리스 및 패치 수준에 따라 Redis 또는 Valkey | 로컬 저장소용 `Cm_Cache_Backend_File`을(를) 사용하는 Zend 기반 두 수준 캐시 |
| [Symfony L2(`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9 이상 | 밸키 | PSR-6 규정을 준수하는 최신 Symfony 캐시 기반 L2 구현 |

## RemoteSynchronizedCache L2 캐시 구성


>[!NOTE]
>
>이 섹션에서는 2.4.9 이전의 Adobe Commerce 온-프레미스 버전에 대한 `RemoteSynchronizedCache` L2 구성을 다룹니다. 여기서 정확한 Commerce 릴리스 및 패치 수준 지원 매트릭스에서 지원합니다.
>
>Adobe Commerce 2.4.9 이상에서는 Valkey를 [Symfony L2 캐시](#symfony-l2-cache-implementation)와 함께 사용합니다.
>
>클라우드 인프라의 Adobe Commerce에 대해 `.magento.env.yaml`에서 배포 변수를 통해 L2 캐시를 구성하십시오. `app/etc/env.php`을(를) 직접 편집하지 마십시오. [L2 캐시 구성](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)을 참조하십시오.

캐시 구성 지침은 Commerce 버전에 따라 다릅니다.

Redis를 지원하는 Adobe Commerce 온-프레미스 버전의 경우 다음 예제를 사용하여 `app/etc/env.php` 파일의 기존 캐시 섹션을 수정하거나 바꾸세요.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
]
```

위치:

- `backend`은(는) L2 캐시 구현입니다.
- `backend_options`은(는) L2 캐시 구성입니다.
  - `remote_backend`은(는) 원격 캐시 구현입니다. Commerce 릴리스 및 패치 수준 지원에 따라 Redis 또는 Valkey입니다.
  - `remote_backend_options`은(는) 원격 캐시 구성입니다.
  - `local_backend`은(는) 로컬 캐시 구현입니다. `Cm_Cache_Backend_File`.
  - `local_backend_options`은(는) 로컬 캐시 구성입니다.
  - `cache_dir`은(는) 로컬 캐시가 저장되는 디렉터리를 정의하는 파일 캐시 관련 옵션입니다.

Redis 또는 Valkey를 지원하는 2.4.9 이전 Adobe Commerce 버전의 경우, Adobe에서는 정확한 릴리스에서 지원하는 원격 캐싱에 Redis 또는 Valkey를 사용하고 로컬 캐싱에 `Cm_Cache_Backend_File`을(를) 사용하는 것이 좋습니다. 로컬 캐시는 일반적으로 `/dev/shm/`과(와) 같은 임시 파일 시스템에 저장됩니다.

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobe에서는 Redis에 대한 부하를 줄이기 위해 `[cache preload](redis-pg-cache.md#redis-preload-feature)` 기능을 사용하는 것이 좋습니다. 미리 로드 키에 대해 접미사 `:hash`을(를) 추가해야 합니다.

## 부실 캐시 옵션

Commerce 2.4부터 `use_stale_cache` 옵션을 사용하면 새 캐시 데이터가 병렬 프로세스에서 생성되는 동안 이전에 캐시된 데이터를 제공함으로써 특정 경우에 대한 성능을 향상시킬 수 있습니다. 이 섹션에서 설명하는 권장 캐시 유형 및 상쇄는 `RemoteSynchronizedCache` 및 `symfony_l2` 구현 모두에 적용됩니다. `symfony_l2` 구성 예제는 [부실 캐시가 있는 Symfony L2 캐시](#symfony-l2-cache-with-stale-cache)를 참조하십시오.

일반적으로, 잠금 대기를 갖는 상계는 성능 관점에서 받아들여질 수 있다. 그러나 블록 또는 캐시 항목의 수가 증가하면 잠금 대기에 더 많은 시간이 걸립니다. 일부 시나리오에서 대기 시간은 프로세스에 대해 최대 **키 수** x **조회 시간 초과**&#x200B;일 수 있습니다. 드문 경우이지만 사용자가 `Block/Config` 캐시에 수백 개의 키를 보유할 수 있으므로 잠금에 대한 작은 조회 시간 제한도 초 단위로 소요될 수 있습니다.

>[!IMPORTANT]
>
>부실 캐시는 L2 캐시에서만 작동합니다. 활성화하려면 L2 캐시 프런트 엔드의 최상위 구성에 `'use_stale_cache' => true`을(를) 추가하십시오.

Adobe에서는 다음을 포함하여 가장 많은 혜택을 받는 캐시 유형에 대해서만 `use_stale_cache` 옵션을 사용하도록 권장합니다.

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe에서는 `default` 캐시 유형에 대해 `use_stale_cache` 옵션을 활성화하지 않는 것이 좋습니다.

다음 코드는 `RemoteSynchronizedCache` 백엔드에 대한 예제 구성을 보여 줍니다. `symfony_l2`의 예제는 [부실 캐시가 있는 Symfony L2 캐시](#symfony-l2-cache-with-stale-cache)를 참조하십시오.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Sympony L2 캐시 구현

Commerce 버전 2.4.9+에서 `RemoteSynchronizedCache` 대신 Symfony L2 캐시 구현(`symfony_l2` 백 엔드)을 사용합니다. Symfony L2 캐시는 Valkey를 사용하여 PSR-6 호환 캐싱 구현을 제공합니다.

>[!IMPORTANT]
>
>Redis는 다음 Adobe Commerce 릴리스의 캐시 구성에 대해 지원되지 않습니다.
>
>- Adobe Commerce 2.4.9 이상
>- Adobe Commerce 2.4.8-p4 이상 패치
>- Adobe Commerce 2.4.7-p9 이상 패치
>- Adobe Commerce 2.4.6-p14 이상 패치
>- Adobe Commerce 2.4.5-p16 이상 패치
>
>이러한 릴리스에 대해 Valkey를 구성합니다.
>
>Adobe Commerce 2.4.9 이상에서 L2 캐싱에 대해 `symfony_l2`을(를) 구성하는 경우 원격 캐시 서비스에 Valkey를 사용해야 합니다. [유효성 검사 설정](config-valkey.md)을 참조하세요.

### RemoteSynchronizedCache에서 Symfony L2로 마이그레이션

`RemoteSynchronizedCache` 백엔드에서 `symfony_l2`(으)로 온-프레미스 설치를 업그레이드하는 경우 `app/etc/env.php`을(를) 업데이트하기 전에 다음을 검토하세요. `backend` 값만 변경하면 안 됩니다. 구성 구조, 키 이름 및 일부 기본 동작이 다릅니다.

- **구성 구조가 변경됩니다.** `remote_backend`, `remote_backend_options` 및 `local_backend`은(는) `symfony_l2`에서 다른 값을 사용합니다. 예를 들어 `remote_backend`은(는) 정규화된 클래스 이름이 아닌 `'valkey'`이(가) 됩니다. 기존 `RemoteSynchronizedCache` 구성을 편집하지 않고 아래의 [구성 예제](#configuration-example-with-symfony-l2-cache)을(를) 시작점으로 사용하십시오.

- **`preload_keys`은(는) `symfony_l2`.**(으)로 권장되지 않습니다. `RemoteSynchronizedCache` 구성에 `preload_keys`이(가) 포함된 경우 마이그레이션의 일부로 제거하십시오. 키를 미리 로드해도 `symfony_l2`에서 성능이 향상되지 않으며, 불필요한 추가 키 조회를 트리거하여 Valkey에 대한 로드를 늘릴 수 있습니다.

- **압축에는 명시적 플래그가 필요합니다.** `compression_lib`만 설정하면 `symfony_l2`에서 압축을 사용할 수 없습니다. 필요한 `compress_data` 설정에 대해서는 [Symfony L2 캐시에 대한 백엔드 옵션](#backend-options-for-symfony-l2-cache)을 참조하십시오.

- **수동으로 구성된 온-프레미스 배포는 기본적으로 부실 캐시를 사용하도록 설정하지 않습니다.** `use_stale_cache`의 기본값은 `symfony_l2`에서 `false`입니다([백엔드 옵션 테이블](#backend-options-for-symfony-l2-cache) 참조). `RemoteSynchronizedCache` 구성에서 `stale_cache_enabled` 프런트 엔드를 사용한 경우 부실 캐시가 있는 [Symfony L2 캐시의 패턴을 사용하여 명시적으로 다시 만들어야 합니다](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>`VALKEY_BACKEND: symfony_l2` 배포 변수를 설정하는 클라우드 환경의 Adobe Commerce에는 `ece-tools`에 의해 자동으로 생성된 `stale_cache_enabled` 프론트엔드를 포함한 전체 L2 구성이 있습니다. 클라우드별 동작은 [Symfony L2 캐시 구성](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)을 참조하십시오.

- **Redis는 `symfony_l2`에 대해 지원되는 원격 백엔드가 아닙니다.** 이 변경 사항의 일부로 Valkey로 마이그레이션합니다. [유효성 검사 설정](config-valkey.md)을 참조하세요.

### Sympony L2 캐시를 사용한 구성 예

>[!IMPORTANT]
>
>이 `app/etc/env.php` 예제는 온-프레미스 설치에만 적용됩니다. 클라우드 인프라의 Adobe Commerce의 경우 `app/etc/env.php`을(를) 직접 편집하지 마십시오. `.magento.env.yaml`에서 `VALKEY_BACKEND: symfony_l2`을(를) 설정합니다. `ece-tools`은(는) 배포 중에 L2 캐시 구성을 생성하고 유지 관리합니다. [Symfony L2 캐시 구성](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)을 참조하십시오.

`app/etc/env.php` 파일에서 L2 캐시에 대해 간소화된 `symfony_l2` 백 엔드 유형을 사용합니다. 이 예제에서는 `symfony_l2`에 권장되지 않는 `preload_keys` 구성을 포함하지 않습니다. 자세한 내용은 [RemoteSynchronizedCache에서 Symfony L2로 마이그레이션](#migrating-from-remotesynchronizedcache-to-symfony-l2)을 참조하십시오.

이 예제는 `cleanup_percentage`을(를) `90`(으)로 설정합니다. 기본값은 `95`입니다. 사용 가능한 로컬 캐시 저장소 및 Commerce 배포의 요구 사항에 따라 이 값을 조정합니다.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### 부실 캐시가 있는 교감 L2 캐시

캐시 유형이 부실 캐시에서 혜택을 받는 [부실 캐시 옵션](#stale-cache-options)과(와) 그 이유를 참조하십시오.

다음 예제를 사용하여 `symfony_l2` 부실 캐시 지원에 대해 별도의 프론트엔드를 구성하십시오.

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Symfony L2 캐시를 위한 백엔드 옵션

| 옵션 | 유형 | 기본값 | 설명 |
| -------- | ------ | --------- | ----------- |
| `remote_backend` | 문자열 | `'valkey'` | 원격 캐시 백엔드. `valkey`을(를) Symfony L2와 함께 사용합니다. Redis는 공식적으로 지원되지 않습니다. |
| `remote_backend_options` | 배열 | `[]` | 원격 Valkey 백엔드 구성 |
| `local_backend` | 문자열 | `'file'` | 로컬 백 엔드 유형: `file` 또는 `apcu` |
| `local_backend_options` | 배열 | `[]` | 로컬 백엔드 구성 |
| `cleanup_percentage` | 정수 | `95` | L1 캐시 정리 임계값, 1에서 100 사이의 백분율로 표시 |
| `use_stale_cache` | 부울 | `false` | 프런트 엔드에 오래된 캐시 사용 |
| `compress_data` | 부울 | `false` | `compression_lib`과(와) 결합할 경우 압축을 활성화합니다. 원격 Valkey 백엔드 옵션에서 이 옵션을 설정합니다. |
| `persistent` | 부울 | `true` | 원격 백엔드에 대한 영구 연결을 제어합니다. Zend 캐시 동작과 일치하도록 `false`(`'0'`)(으)로 설정합니다. 이 동작은 기본적으로 비영구 연결로 설정됩니다. |

>[!NOTE]
>
>`frontend_options.write_control` 옵션은 `RemoteSynchronizedCache` 구성에 적용되며 `symfony_l2`에는 적용되지 않습니다.

### 향상된 Sympony L2 캐시 성능 및 안정성

>[!NOTE]
>
>이러한 개선 사항은 `symfony_l2`을(를) 사용하는 Adobe Commerce 2.4.9 배포에 적용되며 패치 ACP2E-5132에서 사용할 수 있습니다.
>
>Adobe Commerce 온프레미스의 경우 품질 패치 도구(QPT)를 사용하여 이 패치를 적용합니다. 클라우드 인프라의 Adobe Commerce의 경우 패치는 Commerce용 클라우드 패치 패키지에 포함되어 있으며 `ece-tools`의 종속성입니다. 배포 중에 최신 클라우드 패치를 받으려면 `ece-tools`의 최신 버전으로 업데이트하십시오.

최신 업데이트를 통해 Symfony L2 캐시 확장성이 향상되고 불필요한 파일 시스템 I/O가 줄며 캐시 일관성과 신뢰성이 향상됩니다.

#### 최적화된 Sympony L2 캐시 태그 스토리지

Valkey 지원 Symfony L2 캐시 배포의 경우 캐시 태그는 Valkey에만 저장됩니다. 이렇게 하면 중복 파일 시스템 태그 인덱스 쓰기가 제거되고 디스크 I/O가 감소하며 `var/cache/symfony/tags/` 디렉터리의 불필요한 증가를 방지할 수 있습니다.

#### 파일 기반 캐시 동작 개선

파일 기반 캐시를 사용하는(유효성 검사 없이) 배포의 경우 캐시 무효화를 지원하기 위해 로컬 태그 인덱스가 계속 유지됩니다. 이제 태그 인덱스가 이전에 하드코딩된 `var/cache` 위치 대신 구성된 `cache_dir`에 기록되어 일관된 캐시 디렉터리 사용을 보장하고 사용자 지정 캐시 구성에 대한 지원을 개선합니다.

#### 다시 태그 지정 후 오래된 태그 멤버십 수정

캐시 항목을 다시 태깅하면 캐시 항목이 더 이상 속해 있지 않은 태그와 연결된 상태로 둘 수 있습니다. 이제 다시 태그 지정 시 오래된 태그 멤버십이 지워지므로 캐시 항목은 현재 할당된 태그에 의해서만 무효화됩니다.

#### 변경되지 않은 저장을 위한 이중 원격 쓰기 수정

변경되지 않은 콘텐츠로 캐시 항목을 저장해도 원격(Valkey) 백엔드에 대한 쓰기가 트리거됩니다. 이제 콘텐츠가 변경되지 않으면 저장을 생략하여 불필요한 원격 쓰기를 줄일 수 있습니다.

#### L1 크기 기반 제거 수정(cleanup_percentage)

L1 크기 기반 제거에 사용된 `cleanup_percentage` 임계값이 정리를 일관되게 트리거하지 않았습니다. 이제 L1 캐시 제거에서 구성된 `cleanup_percentage`을(를) 올바르게 적용합니다.

#### 부실 캐시에 대한 재생성 잠금

`use_stale_cache`이(가) 활성화되어 있고 항목의 원격 복사본을 일시적으로 사용할 수 없는 경우 이제 한 프로세스만 단기 잠금을 획득하여 해당 항목을 다시 생성합니다. 동일한 항목에 대한 다른 동시 요청은 기존 로컬 값을 직접 재생성하는 대신 계속 처리되므로 재생성 스탬프와 중복 백엔드 로드가 줄어듭니다.

#### 영향

- Valkey 지원 Symfony L2 캐시 배포를 위해 중복 파일 시스템 태그 인덱스 쓰기를 제거하여 디스크 I/O를 줄이고 `var/cache/symfony/tags/` 디렉터리의 불필요한 증가를 방지합니다.
- 파일 기반 캐시 배포가 캐시 무효화 동작을 유지하면서 로컬 태그 인덱스에 대해 구성된 `cache_dir`을(를) 일관되게 사용하도록 합니다.
- 다시 태깅한 후 오래된 태그 멤버십이 남아 있어 잘못된 캐시 무효화를 방지합니다.
- 변경되지 않은 캐시 저장에 대한 불필요한 원격 쓰기를 줄여 네트워크 및 백엔드 로드 감소.
- 구성된 `cleanup_percentage` 임계값에서 L1 캐시 제거를 안정적으로 트리거합니다.
- 모든 동시 요청이 항목을 다시 빌드하도록 하는 대신 키당 단일 재생기를 선택하여 `use_stale_cache` 항목에 대한 재생성 속도를 줄입니다.

자세한 구성 옵션은 다음을 참조하십시오.

- [Symfony Cache를 사용한 Valkey 캐시 구성](valkey-pg-cache.md)
