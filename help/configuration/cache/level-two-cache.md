---
title: 성능 최적화를 위한 L2 캐시 구성
description: 네트워크 트래픽을 줄이고 성능을 개선하기 위해 Adobe Commerce에서 L2 캐시를 구성하는 방법에 대해 알아봅니다. 기존 및 Symfony 구현 옵션을 살펴보십시오.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: 1166
ht-degree: 0%

---

# 성능 최적화를 위한 L2 캐시 구성

L2(2단계) 캐싱은 각 웹 노드에 로컬 캐시 계층을 추가하여 원격 캐시 스토리지(Redis 또는 Valkey)와 Commerce 애플리케이션 간의 네트워크 트래픽을 줄입니다. 표준 Commerce 인스턴스는 요청당 약 300KB를 전송하며, 트래픽은 일부 상황에서 1000개 이상의 요청으로 빠르게 증가할 수 있습니다.

L2 캐싱을 사용하면 각 웹 노드는 자주 액세스하는 데이터를 로컬에 저장하고 원격 캐시를 두 가지 용도로 사용합니다.

- 최신 캐시가 로컬에 저장되었는지 확인하기 위해 캐시 데이터 버전 확인
- 업데이트된 캐시 데이터를 원격 저장소에서 로컬 시스템으로 전송 중

Commerce은 해시된 데이터 버전을 원격 캐시에 저장하고, 일반 키에 접미사 `:hash`을(를) 추가합니다. 로컬 캐시가 오래된 경우 캐시 어댑터를 통해 원격 컴퓨터에서 데이터를 가져옵니다.

두 가지 L2 캐시 구현을 사용할 수 있습니다.

| 구현 | 버전 | 설명 |
| -------------- | ------- | ----------- |
| [레거시(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | 로컬 저장소용 `Cm_Cache_Backend_File`을(를) 사용하는 Zend 기반 두 수준 캐시 |
| [최신(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | PSR-6 규정 준수 및 향상된 성능을 갖춘 Symfony 캐시 기반 L2. Valkey만 지원합니다. |

## 기존 L2 캐시 구성(RemoteSynchronizedCache)

>[!NOTE]
>
>기존 L2 캐시 구성 지침은 이전 버전의 Adobe Commerce에 적용됩니다. Adobe Commerce 버전 2.4.9 이상을 사용하는 경우 Valkey를 [L2 캐시용 Symfony 2와 함께 사용](#modern-symfony-l2-cache-implementation)하십시오.

캐시 구성 지침은 배포 유형에 따라 다릅니다.

- **Cloud의 Adobe Commerce에 대해**&#x200B;에서 `.magento.env.yaml`의 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_backend) 또는 [`VALKEY_BACKEND`](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) 배포 변수를 설정하여 L2 캐시를 구성하십시오. 구성 예제는 [L2 캐시 구성](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)을 참조하십시오.

- **Redis를 지원하는 Adobe Commerce 온-프레미스 버전의 경우**&#x200B;에서 다음 예제를 사용하여 `app/etc/env.php` 파일의 기존 캐시 섹션을 수정하거나 바꾸세요.

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
  - `remote_backend`은(는) 원격 캐시 구현인 Redis 또는 MySQL입니다.
  - `remote_backend_options`은(는) 원격 캐시 구성입니다.
  - `local_backend`은(는) 로컬 캐시 구현입니다. `Cm_Cache_Backend_File`
  - `local_backend_options`은(는) 로컬 캐시 구성입니다.
  - `cache_dir`은(는) 로컬 캐시가 저장된 디렉터리에 대한 파일 캐시 관련 옵션입니다.

Adobe Commerce의 경우 Adobe에서는 다음을 사용하여 원격 캐싱(`\Magento\Framework\Cache\Backend\Redis`)에 Redis를 사용하고 공유 메모리에 있는 데이터의 로컬 캐싱에 `Cm_Cache_Backend_File`을(를) 사용합니다. `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe은 Redis에 대한 압력을 크게 낮추기 때문에 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 기능을 사용할 것을 권장합니다. 미리 로드 키에 접미사 &#39;:hash&#39;을(를) 추가하는 것을 잊지 마십시오.

## 부실 캐시 옵션

Commerce 2.4부터 `use_stale_cache` 옵션을 사용하면 새 캐시 데이터가 병렬 프로세스에서 생성되는 동안 이전에 캐시된 데이터를 제공함으로써 특정 경우에 대한 성능을 향상시킬 수 있습니다.

일반적으로, 잠금 대기를 갖는 상계는 성능 관점에서 받아들여질 수 있다. 그러나 블록 또는 캐시 항목의 수가 증가하면 잠금 대기에 더 많은 시간이 걸립니다. 일부 시나리오에서 대기 시간은 프로세스에 대해 최대 **키 수** x **조회 시간 초과**&#x200B;일 수 있습니다. 드문 경우이지만 판매자는 `Block/Config` 캐시에 수백 개의 키를 보유할 수 있으므로 잠금에 대한 작은 조회 시간 제한도 초 단위로 소요될 수 있습니다.

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

다음 코드는 구성의 예를 보여 줍니다.

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

## 최신 Sympony L2 캐시 구현

Commerce 버전 2.4.9+에서 기존 L2 캐시 대신 Sympony 캐시 기반 L2 캐시 구현(`symfony_l2` 백엔드)을 사용합니다. Symfony L2 캐시는 최신 PSR-6 호환 캐싱 구현을 제공하며 기존 `RemoteSynchronizedCache`에 비해 성능이 크게 개선되었습니다.

>[!NOTE]
>
>Cloud의 Adobe Commerce에 대해 ECE 도구 패키지(`ece-tools`)는 이 구성을 자동으로 관리합니다. `app/etc/env.php`을(를) 직접 편집하지 마십시오. 배포는 수동 변경 내용을 덮어씁니다. 클라우드 구성의 경우 대신 [Symfony L2 캐시 구성](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)을 참조하십시오.

>[!IMPORTANT]
>
>{{redis-cache-support}}
>
>`symfony_l2`은(는) Adobe Commerce 2.4.9 이상에서만 사용할 수 있으므로 Valkey를 원격 백엔드로 사용하여 구성하십시오. Redis는 `symfony_l2`에 대해 공식적으로 지원되는 원격 백엔드가 아닙니다. 릴리스별로 지원되는 캐시 서비스에 대해서는 [시스템 요구 사항](../../installation/system-requirements.md)을 참조하십시오.

### Symfony L2 캐시의 이점

- **최신 아키텍처**: Symfony 캐시 구성 요소를 기반으로 구축(PSR-6 준수)
- **향상된 성능**: Igbinary serialization, gzip 압축 및 Lua 스크립트에 대한 기본 지원
- **영구 연결**: 연결 풀링으로 유효성 검사 연결 오버헤드를 줄입니다.
- **키 미리 로드**: 중요한 데이터에 대한 캐시 키 미리 로드를 지원합니다.
- **오래된 캐시 지원**: `use_stale_cache` 옵션과의 완전한 호환성
- **간소화된 구성**: 클리너 백 엔드 형식 이름(`valkey`, `file`)

### Sympony L2 캐시를 사용한 구성 예

L2 캐시에 대해 간소화된 `symfony_l2` 백 엔드 유형 사용:

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
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
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

오래된 캐시 지원을 위한 별도의 프론트엔드를 구성합니다.

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
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | 문자열 | `'valkey'` | 원격 백 엔드 유형: `valkey` 또는 `file`. L2 캐시에 `valkey`을(를) 사용합니다. |
| `remote_backend_options` | 배열 | `[]` | 원격 백엔드 구성(Valkey 설명서 참조) |
| `local_backend` | 문자열 | `'file'` | 로컬 백 엔드 유형: `file` 또는 `apcu` |
| `local_backend_options` | 배열 | `[]` | 로컬 백엔드 구성 |
| `cleanup_percentage` | 정수 | `95` | L1 캐시 정리 임계값(1-100) |
| `use_stale_cache` | 부울 | `false` | 고가용성을 위해 오래된 캐시 활성화 |

>[!NOTE]
>
>`remote_backend` 옵션도 `redis` 값을 허용합니다. 그러나 Redis는 Adobe Commerce 2.4.9 이상에서 공식적으로 지원되는 캐시 서비스가 아닙니다. Adobe에서는 `valkey`(으)로만 `symfony_l2`을(를) 구성하는 것이 좋습니다. 릴리스별로 지원되는 캐시 서비스에 대해서는 [시스템 요구 사항](../../installation/system-requirements.md)을 참조하십시오.

### 향상된 Sympony L2 캐시 성능 및 안정성

>[!NOTE]
>
>이러한 개선 사항은 `symfony_l2`을(를) 사용하는 Adobe Commerce 2.4.9 배포에 적용되며 패치 ACP2E-5132에서 사용할 수 있습니다. 최신 패치 릴리스 정보는 [Commerce용 클라우드 패치](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)를 참조하십시오.

#### 최적화된 Sympony L2 캐시 태그 스토리지

중복 파일 시스템 태그 인덱스 쓰기를 제거하여 Valkey 지원 배포를 위해 최적화된 Sympony L2 캐시 비헤이비어 이제 캐시 태그는 Valkey에만 저장되며, Sympony L2 캐시 동작을 레거시 캐시 구현에 맞춥니다. 이렇게 하면 불필요한 디스크 I/O가 줄어들고 캐시 쓰기 성능이 향상되며 `var/cache/symfony/tags/` 디렉터리의 증가를 방지할 수 있습니다.

#### 파일 기반 캐시 동작 개선

파일 기반 캐시를 사용하는(유효성 검사 없이) 배포의 경우 캐시 무효화를 지원하기 위해 로컬 태그 인덱스가 계속 유지됩니다. 이제 태그 인덱스가 이전에 하드코딩된 `var/cache` 위치 대신 구성된 `cache_dir`에 기록되어 일관된 캐시 디렉터리 사용을 보장하고 사용자 지정 캐시 구성에 대한 지원을 개선합니다.

#### 향상된 캐시 무효화

이제 캐시 무효화는 적절한 L1 태그 정리와 함께 TTL 기반 재생성 잠금을 사용하여 태그 무효화 후에 이전에 지속될 수 있는 오래된 캐시 항목을 제거합니다.

#### 기본적으로 압축 사용

Redis/Valkey 압축(`compress_data`)이 이제 Symfony L2 캐시에 대해 기본적으로 활성화되어 메모리 사용량과 네트워크 트래픽을 줄이고 레거시 캐시 구현의 기본 동작에 맞게 조정됩니다.

#### 영향

- Valkey 지원 Symfony L2 캐시 구축을 위해 중복 파일 시스템 태그 인덱스 쓰기를 제거합니다.
- 디스크 I/O를 줄이고 캐시 쓰기 성능을 향상시킵니다.
- `var/cache/symfony/tags/` 디렉터리의 불필요한 증가를 방지합니다.
- 파일 기반 캐시 배포가 캐시 무효화 동작을 유지하면서 구성된 `cache_dir`을(를) 일관되게 사용하도록 합니다.
- TTL 기반 재생성 잠금 및 적절한 L1 태그 정리를 통해 오래된 캐시 항목을 제거합니다.
- 기본적으로 `compress_data`을(를) 사용하도록 설정하여 메모리 사용량 및 네트워크 트래픽을 줄입니다.

자세한 구성 옵션은 다음을 참조하십시오.
- [Symfony Cache를 사용한 Valkey 캐시 구성](valkey-pg-cache.md)

