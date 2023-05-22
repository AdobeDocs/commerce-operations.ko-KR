---
title: L2 캐시 구성
description: L2 캐시를 구성하는 방법을 알아봅니다.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# L2 캐시 구성

캐싱을 사용하면 원격 캐시 저장소와 Commerce 애플리케이션 간의 네트워크 트래픽을 줄일 수 있습니다. 표준 Commerce 인스턴스는 요청당 약 300kb를 전송하며, 트래픽은 일부 상황에서 ~1000개 이상의 요청으로 빠르게 증가할 수 있습니다.

네트워크 대역폭을 Redis로 줄이려면 캐시 데이터를 각 웹 노드에 로컬로 저장하고 원격 캐시를 두 가지 용도로 사용합니다.

- 캐시 데이터 버전을 확인하고 최신 캐시가 로컬에 저장되어 있는지 확인하십시오
- 원격 컴퓨터에서 로컬 컴퓨터로 최신 캐시 전송

Commerce는 해시된 데이터 버전을 일반 키에 접미사 &#39;:hash&#39;가 추가된 Redis에 저장합니다. 오래된 로컬 캐시가 있으면 데이터가 캐시 어댑터를 사용하여 로컬 시스템으로 전송됩니다.

>[!INFO]
>
>클라우드 인프라의 Adobe Commerce에서 다음을 사용할 수 있습니다. [변수 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) L2 캐시 구성용

## 구성 예

다음 예를 사용하여 의 기존 캐시 섹션을 수정하거나 대체합니다. `app/etc/env.php` 파일.

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
                ],
                'use_stale_cache' => false,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

위치:

- `backend` 는 L2 캐시 구현입니다.
- `backend_options` 는 L2 캐시 구성입니다.
   - `remote_backend` 는 원격 캐시 구현입니다(Redis 또는 MySQL).
   - `remote_backend_options` 는 원격 캐시 구성입니다.
   - `local_backend` 는 로컬 캐시 구현입니다. `Cm_Cache_Backend_File`
   - `local_backend_options` 는 로컬 캐시 구성입니다.
      - `cache_dir` 는 로컬 캐시가 저장된 디렉토리에 대한 파일 캐시 관련 옵션입니다.
   - `use_stale_cache` 는 부실 캐시의 사용을 활성화하거나 비활성화하는 플래그입니다.

Adobe은 원격 캐싱에 Redis 사용을 권장합니다(`\Magento\Framework\Cache\Backend\Redis`) 및 `Cm_Cache_Backend_File` 공유 메모리에 있는 데이터의 로컬 캐싱을 위해 다음을 사용합니다. `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe은 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 그것이 Redis에 대한 압력을 급격하게 감소시킴에 따라 특징입니다. 미리 로드 키에 접미사 &#39;:hash&#39;를 추가하는 것을 잊지 마십시오.

## 부실 캐시 옵션

시작 [!DNL Commerce] 2.4, `use_stale_cache` 옵션은 일부 특정 경우에 성능을 향상시킬 수 있습니다.

일반적으로 잠금 대기가 있는 상계는 성능 측면에서 수용할 수 있지만 판매자의 블록 또는 캐시 수가 클수록 잠금 대기에 더 많은 시간이 소요됩니다. 일부 시나리오에서는 **키 수** \* **조회 시간 초과** 프로세스에 걸리는 시간입니다. 드문 경우이긴 하지만 상인이 수백 개의 키를 `Block/Config` 캐시이므로 잠금에 대한 작은 조회 시간 초과도 초 비용이 들 수 있습니다.

부실 캐시는 L2 캐시에서만 작동합니다. 오래된 캐시를 사용하면 새 캐시가 병렬 프로세스에서 생성되는 동안 오래된 캐시를 보낼 수 있습니다. 부실 캐시를 활성화하려면 다음을 추가하십시오. `'use_stale_cache' => true` L2 캐시의 최상위 구성입니다.

Adobe은 `use_stale_cache` 다음을 포함하여 가장 많은 이점을 제공하는 캐시 유형에만 해당하는 옵션입니다.

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
