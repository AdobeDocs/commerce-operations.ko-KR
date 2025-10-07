---
title: L2 캐시 구성
description: Adobe Commerce 성능 최적화를 위한 L2 캐시를 구성하는 방법을 알아봅니다. 설정 단계 및 네트워크 트래픽 감소 기술을 살펴봅니다.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# L2 캐시 구성

캐싱을 사용하면 원격 캐시 스토리지와 Commerce 애플리케이션 간의 네트워크 트래픽을 줄일 수 있습니다. 표준 Commerce 인스턴스는 요청당 약 300kb를 전송하며, 트래픽은 일부 상황에서 ~1000개 이상의 요청으로 빠르게 증가할 수 있습니다.

네트워크 대역폭을 Redis로 줄이려면 캐시 데이터를 각 웹 노드에 로컬로 저장하고 원격 캐시를 두 가지 용도로 사용합니다.

- 캐시 데이터 버전을 확인하고 최신 캐시가 로컬에 저장되어 있는지 확인하십시오
- 원격 컴퓨터에서 로컬 컴퓨터로 최신 캐시 전송

Commerce은 해시된 데이터 버전을 일반 키에 접미사 &#39;:hash&#39;이(가) 추가된 Redis에 저장합니다. 오래된 로컬 캐시가 있으면 데이터가 캐시 어댑터를 사용하여 로컬 시스템으로 전송됩니다.

>[!INFO]
>
>클라우드 인프라의 Adobe Commerce의 경우 L2 캐시 구성에 [변수 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)를 사용할 수 있습니다.

## 구성 예

다음 예제를 사용하여 `app/etc/env.php` 파일의 기존 캐시 섹션을 수정하거나 바꾸십시오.

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
],
```

위치:

- `backend`은(는) L2 캐시 구현입니다.
- `backend_options`은(는) L2 캐시 구성입니다.
   - `remote_backend`은(는) 원격 캐시 구현인 Redis 또는 MySQL입니다.
   - `remote_backend_options`은(는) 원격 캐시 구성입니다.
   - `local_backend`은(는) 로컬 캐시 구현입니다. `Cm_Cache_Backend_File`
   - `local_backend_options`은(는) 로컬 캐시 구성입니다.
   - `cache_dir`은(는) 로컬 캐시가 저장된 디렉터리에 대한 파일 캐시 관련 옵션입니다.

Adobe에서는 다음을 사용하여 원격 캐싱(`\Magento\Framework\Cache\Backend\Redis`)에 Redis를 사용하고 공유 메모리에 있는 데이터의 로컬 캐싱에 `Cm_Cache_Backend_File`을(를) 사용하는 것이 좋습니다. `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe은 Redis에 대한 압력을 크게 낮추기 때문에 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 기능을 사용할 것을 권장합니다. 미리 로드 키에 접미사 &#39;:hash&#39;을(를) 추가하는 것을 잊지 마십시오.

## 부실 캐시 옵션

[!DNL Commerce] 2.4부터 `use_stale_cache` 옵션을 사용하면 일부 특정 경우에 성능이 향상될 수 있습니다.

일반적으로 잠금 대기가 있는 상계는 성능 측면에서 수용할 수 있지만 판매자의 블록 또는 캐시 수가 클수록 잠금 대기에 더 많은 시간이 소요됩니다. 일부 시나리오에서는 프로세스에 대해 **키 개수** \* **조회 시간 초과**&#x200B;를 대기할 수 있습니다. 드문 경우이지만 판매자는 `Block/Config` 캐시에 수백 개의 키를 보유할 수 있으므로 잠금에 대한 작은 조회 시간 제한도 초 단위로 소요될 수 있습니다.

부실 캐시는 L2 캐시에서만 작동합니다. 오래된 캐시를 사용하면 새 캐시가 병렬 프로세스에서 생성되는 동안 오래된 캐시를 보낼 수 있습니다. 부실 캐시를 활성화하려면 L2 캐시의 최상위 구성에 `'use_stale_cache' => true`을(를) 추가하십시오.

Adobe에서는 다음을 포함하여 가장 많은 혜택을 받는 캐시 유형에 대해서만 `use_stale_cache` 옵션을 사용하도록 권장합니다.

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe에서는 `use_stale_cache` 캐시 유형에 대해 `default` 옵션을 활성화하지 않는 것이 좋습니다.

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
