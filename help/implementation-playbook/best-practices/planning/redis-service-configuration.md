---
title: Redis 서비스 구성에 대한 우수 사례
description: Adobe Commerce용 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법에 대해 알아봅니다.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 9dc17a7ec44d9c146fdc2ec48e128beacc298299
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Redis 서비스 구성에 대한 우수 사례

- Redis L2 캐시 구성
- Redis 슬레이브 연결 활성화
- 미리 로드 키
- 부실 캐시 활성화
- Redis 캐시와 Redis 세션 분리
- Redis 캐시를 압축하고 더 높은 압축을 위해 `gzip`을(를) 사용합니다.

## Redis L2 캐시 구성

`REDIS_BACKEND` 구성 파일에서 `.magento.env.yaml` 배포 변수를 설정하여 Redis L2 캐시를 구성합니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

클라우드 인프라의 환경 구성에 대해서는 [`REDIS_BACKEND`Commerce on Cloud Infrastructure Guide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_backend)의 __&#x200B;을(를) 참조하십시오.

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)에서 _Redis 페이지 캐싱 구성_&#x200B;을 참조하십시오.

>[!NOTE]
>
>최신 버전의 `ece-tools` 패키지를 사용 중인지 확인하십시오. 그렇지 않으면 [최신 버전으로 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=ko)하십시오. `composer show magento/ece-tools` CLI 명령을 사용하여 로컬 환경에 설치된 버전을 확인할 수 있습니다.


### L2 캐시 메모리 크기 조정(Adobe Commerce Cloud)

L2 캐시는 [임시 파일 시스템](https://en.wikipedia.org/wiki/Tmpfs)을(를) 저장소 메커니즘으로 사용합니다. 특수 키 값 데이터베이스 시스템과 비교하면 임시 파일 시스템에는 메모리 사용을 제어하는 키 제거 정책이 없습니다.

메모리 사용 제어 부족으로 인해 오래된 캐시를 누적하여 L2 캐시 메모리 사용량이 늘어날 수 있습니다.

L2 캐시 구현의 메모리 소진을 방지하기 위해 Adobe Commerce은 특정 임계값에 도달하면 저장소를 지웁니다. 기본 임계값은 95%입니다.

캐시 저장을 위한 프로젝트 요구 사항에 따라 L2 캐시 메모리 최대 사용량을 조정하는 것이 중요합니다. 다음 방법 중 하나를 사용하여 메모리 캐시 크기 조정을 구성합니다.

- `/dev/shm` 마운트의 크기 변경을 요청하려면 지원 티켓을 만드십시오.
- 저장소의 최대 채움 비율을 제한하려면 응용 프로그램 수준에서 `cleanup_percentage` 속성을 조정하십시오. 나머지 여유 메모리는 다른 서비스에서 사용할 수 있습니다.
캐시 구성 그룹 `cache/frontend/default/backend_options/cleanup_percentage` 아래의 배포 구성에서 구성을 조정할 수 있습니다.

>[!NOTE]
>
>구성 가능한 `cleanup_percentage` 옵션이 Adobe Commerce 2.4.4에 도입되었습니다.

다음 코드는 `.magento.env.yaml` 파일의 예제 구성을 보여 줍니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

캐시 요구 사항은 프로젝트 구성 및 사용자 지정 타사 코드에 따라 다를 수 있습니다. L2 캐시 메모리 크기 조정 범위를 사용하면 L2 캐시가 너무 많은 임계값 히트 없이 작동할 수 있습니다.
이상적으로 L2 캐시 메모리 사용은 빈번한 스토리지 지우기를 방지하기 위해 임계값 아래의 특정 수준에서 안정되어야 합니다.

다음 CLI 명령을 사용하여 클러스터의 각 노드에서 L2 캐시 저장소 메모리 사용을 확인하고 `/dev/shm` 줄을 찾을 수 있습니다.
사용은 서로 다른 노드에 걸쳐 다를 수 있지만 동일한 값으로 수렴해야 합니다.

```bash
df -h
```

## Redis 슬레이브 연결 활성화

`.magento.env.yaml` 구성 파일에서 Redis 슬레이브 연결을 활성화하여 한 노드만 읽기-쓰기 트래픽을 처리하고 다른 노드는 읽기 전용 트래픽을 처리하도록 합니다.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

[Cloud Infrastructure의 Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_use_slave_connection)에서 _REDIS_USE_SLAVE_CONNECTION_&#x200B;을(를) 참조하십시오.

Adobe Commerce 온-프레미스 설치의 경우 `bin/magento:setup` 명령을 사용하여 새 Redis 캐시 구현을 구성합니다. [구성 가이드](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)에서 _기본 캐시에 Redis 사용_&#x200B;을 참조하십시오.

>[!WARNING]
>
>_크기 조정/분할 아키텍처를 사용하여 클라우드 인프라 프로젝트에 대한 Redis 슬레이브 연결을 구성하지_&#x200B;마십시오[.](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=ko) 이로 인해 Redis 연결 오류가 발생합니다. [클라우드 인프라의 Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_use_slave_connection) 안내서에서 _Redis 구성 지침_&#x200B;을 참조하십시오.

## 미리 로드 키

페이지 간에 데이터를 다시 사용하려면 미리 로드할 키를 `.magento.env.yaml` 구성 파일에 나열합니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)에서 _Redis 미리 로드 기능_&#x200B;을 참조하세요.

## 부실 캐시 활성화

특히 오래된 캐시를 사용하여 새로운 캐시를 동시에 생성함으로써 잠금 대기 시간을 줄이고 성능을 향상시킬 수 있습니다. `config.php` 구성 파일에서 부실 캐시를 활성화하고 캐시 유형을 정의합니다(클라우드만 해당).

```php
'cache' => [
        'frontend' => [
            'stale_cache_enabled' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'remote_backend_options' => [
                        'persistent' => 0,
                        'server' => 'localhost',
                        'database' => '4',
                        'port' => '6370',
                        'password' => ''
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
    ]
```

>[!NOTE]
>
>앞의 예에서 `full_page` 캐시는 [Fastly](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly)를 사용하므로 클라우드 인프라 프로젝트의 Adobe Commerce과 관련이 없습니다.

온-프레미스 설치를 구성하려면 [구성 가이드](../../../configuration/cache/level-two-cache.md#stale-cache-options)에서 _오래된 캐시 옵션_&#x200B;을 참조하십시오.

## 별도의 Redis 캐시 및 세션 인스턴스

Redis 캐시와 Redis 세션을 분리하면 캐시와 세션을 독립적으로 관리할 수 있습니다. 이는 캐시 문제가 세션에 영향을 주지 않도록 하여 매출에 영향을 줄 수 있습니다. 각 Redis 인스턴스는 자체 코어에서 실행되므로 성능이 향상됩니다.

1. `.magento/services.yaml` 구성 파일을 업데이트합니다.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. `.magento.app.yaml` 구성 파일을 업데이트합니다.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)을 제출하여 프로덕션 및 스테이징 환경에서 세션 전용 새 Redis 인스턴스의 프로비저닝을 요청합니다. 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일을 포함합니다. 이 경우 다운타임이 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 기록합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. `.magento.env.yaml` 구성 파일에 포트 번호를 추가합니다.

   >[!IMPORTANT]
   >
   >`ece-tools`이(가) `MAGENTO_CLOUD_RELATIONSHIPS` redis 세션 서비스 정의에서 자동으로 검색할 수 없는 경우에만 redis 세션 포트를 구성하십시오.

   >[!NOTE]
   >
   >`disable_locking`을(를) `1`(으)로 설정해야 합니다.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Redis 캐시 인스턴스의 [기본 데이터베이스](../../../configuration/cache/redis-pg-cache.md)(`db 0`)에서 세션을 제거합니다.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

배포 중에 [빌드 및 배포 로그](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=ko#build-and-deploy-logs)에 다음 줄이 표시됩니다.

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## 캐시 압축

6GB가 넘는 Redis `maxmemory`을(를) 사용하는 경우 캐시 압축을 사용하여 키에서 사용하는 공간을 줄일 수 있습니다. 클라이언트측 성능이 저하됩니다. 예비 CPU가 있는 경우 활성화합니다. [구성 가이드](../../../configuration/cache/redis-session.md)에서 _세션 저장소에 Redis 사용_&#x200B;을 참조하십시오.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Redis 비동기 해제 사용(lazyfree)

클라우드 인프라의 Adobe Commerce에서 `lazyfree`을(를) 사용하려면 다음 Redis 구성을 환경에 적용하도록 요청하는 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)하십시오.

```
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Lazyfree가 활성화되면 Redis는 제거, 만료, 서버에서 시작된 삭제, 사용자 삭제 및 복제본 데이터 세트 플러시를 위해 백그라운드 스레드로 메모리 재확보를 오프로드합니다. 이렇게 하면 기본 스레드 차단이 줄어들고 요청 지연이 감소할 수 있습니다.

>[!NOTE]
>
>`lazyfree-lazy-user-del yes` 옵션을 사용하면 `DEL` 명령이 `UNLINK`과(와) 같이 동작하여 키의 연결이 즉시 해제되고 비동기적으로 메모리를 확보할 수 있습니다.

>[!WARNING]
>
>백그라운드에서 자유롭게 작업하기 때문에 삭제/만료/축출된 키에 사용되는 메모리는 백그라운드 스레드에서 작업을 완료할 때까지 할당된 상태로 유지됩니다. Redis가 이미 메모리가 부족한 경우 신중하게 테스트하고 먼저 메모리 압력을 줄이는 것을 고려하십시오(예: 특정 경우에 대해 블록 캐시를 비활성화하고 위에서 설명한 대로 캐시와 세션 Redis 인스턴스를 구분).

## Redis 다중 스레드 I/O 활성화

클라우드 인프라의 Adobe Commerce에서 Redis I/O 스레딩을 사용하려면 아래 구성을 요청하는 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)을 제출하세요. 이렇게 하면 더 높은 CPU 사용률을 감수하면서 주 스레드에서 소켓 읽기/쓰기 및 명령 구문 분석을 오프로드하여 처리량을 향상시킬 수 있습니다. 로드 중 유효성 검사 및 호스트 모니터링

```
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
```

>[!NOTE]
>
>I/O 스레드는 클라이언트 I/O를 병렬화하고 구문 분석만 수행합니다. Redis 명령 실행은 단일 스레드로 유지됩니다.

>[!WARNING]
>
>I/O 스레드를 활성화하면 CPU 사용량이 늘어날 수 있으며 모든 워크로드에는 도움이 되지 않습니다. 보수적인 가치와 벤치마크로 시작하십시오. 지연이 증가하거나 CPU이 포화되면 `io-threads`을(를) 줄이거나 I/O 스레드에서 읽기를 사용하지 않도록 설정하십시오.

## Redis 클라이언트 시간 초과 및 다시 시도 횟수 증가

`.magento.env.yaml`에서 백 엔드 옵션을 조정하여 캐시 클라이언트의 허용 한도를 임시 포화도로 높입니다.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            read_timeout: 10
            connect_retries: 5
```

이러한 설정은 응답 대기 창을 확장하고 연결 설정을 다시 시도하여 Redis의 일시적인 정체를 방지하기 위해 클라이언트 허용 한도를 높입니다. 이렇게 하면 짧은 스파이크 동안 간헐적인 `cannot connect to localhost:6370` 및 읽기 시간 제한 오류를 줄일 수 있습니다.

>[!NOTE]
>
>지속적인 오버로드에 대한 수정 사항이 아닙니다.

## 추가 정보

- [Redis 페이지 캐시](../../../configuration/cache/redis-pg-cache.md)
- [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md)
