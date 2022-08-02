---
title: L2 캐시 구성
description: L2 캐시를 구성하는 방법을 알아봅니다.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# L2 캐시 구성

캐싱은 원격 캐시 저장소와 상거래 응용 프로그램 간의 네트워크 트래픽을 줄일 수 있도록 합니다. 표준 Commerce 인스턴스는 요청당 약 300kb를 전송하며, 일부 경우에는 트래픽이 약 1,000개 이상의 요청으로 빠르게 증가할 수 있습니다.

네트워크 대역폭을 Redis로 줄이려면 각 웹 노드에 캐시 데이터를 로컬로 저장하고 원격 캐시를 두 가지 용도로 사용합니다.

- 캐시 데이터 버전을 확인하고 최신 캐시가 로컬로 저장되었는지 확인합니다
- 원격 컴퓨터에서 로컬 시스템으로 최신 캐시를 전송합니다

Commerce는 해시된 데이터 버전을 Redis에 저장하며 접미사 &#39;:hash&#39;가 일반 키에 추가됩니다. 오래된 로컬 캐시가 있는 경우 데이터가 캐시 어댑터를 사용하여 로컬 시스템으로 전송됩니다.

>[!INFO]
>
>클라우드 인프라 기반의 Adobe Commerce의 경우, [확장된 Redis 캐시 구현](https://support.magento.com/hc/en-us/articles/360049292532) 지원 문서.

## 구성 예

다음 예제를 사용하여 의 기존 캐시 섹션을 수정하거나 바꿉니다 `app/etc/env.php` 파일.

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
   - `remote_backend` 원격 캐시 구현: Redis 또는 MySQL입니다.
   - `remote_backend_options` 원격 캐시 구성입니다.
   - `local_backend` 은 로컬 캐시 구현입니다. `Cm_Cache_Backend_File`
   - `local_backend_options` 은 로컬 캐시 구성입니다.
      - `cache_dir` 은 로컬 캐시가 저장된 디렉토리에 대한 파일 캐시 특정 옵션입니다.
   - `use_stale_cache` 는 오래된 캐시를 사용하거나 사용하지 않도록 설정하는 플래그입니다.

원격 캐싱에는 Redis를 사용하는 것이 좋습니다(`\Magento\Framework\Cache\Backend\Redis`) 및 `Cm_Cache_Backend_File` 공유 메모리의 데이터를 로컬 캐싱하는 경우 다음을 사용합니다. `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe은 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 이 기능은 레디스의 압력을 크게 감소시켜 줍니다. 사전 로드 키에 접미사 &#39;:hash&#39;를 추가하는 것을 잊지 마십시오.

## 오래된 캐시 옵션

시작 [!DNL Commerce] 2.4, `stale_cache` 옵션을 사용하면 일부 특정 경우에 성능이 향상됩니다.

일반적으로, 잠금 대기 시 상쇄 해제를 성능 측면에서는 사용할 수 있지만, 머천트가 가지고 있는 블록 또는 캐시 수가 클수록 잠금 대기 시간이 늘어납니다. 일부 시나리오에서는 **키 수** \* **조회 시간 초과** 프로세스의 시간입니다. 드문 경우이긴 하지만, 상인은 `Block/Config` 캐시되므로 잠금에 대한 작은 조회 시간 제한도 몇 초 정도 걸릴 수 있습니다.

오래된 캐시는 L2 캐시에서만 작동합니다. 오래된 캐시가 있으면 오래된 캐시를 보낼 수 있지만 새 캐시가 병렬 프로세스에서 생성됩니다. 오래된 캐시를 활성화하려면 `'use_stale_cache' => true` L2 캐시의 최상위 구성
