---
title: Redis 및 Valkey 서비스 구성에 대한 우수 사례
description: Adobe Commerce용 Redis 및 Valkey 서비스를 구성하는 방법에 대해 알아봅니다. L2 캐시, 슬레이브 연결, 오래된 캐시 및 세션 분리를 통해 캐싱 성능을 개선합니다.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Redis 및 Valkey 서비스 구성에 대한 우수 사례

이러한 권장 사항을 사용하여 Adobe Commerce 캐싱 및 세션에 대한 Redis 또는 Valkey를 구성합니다.

- L2 캐시 구성
- 슬레이브 연결 활성화
- 미리 로드 키
- 부실 캐시 활성화
- 별도의 캐시 및 세션
- 캐시 압축
- 구성 예

>[!NOTE]
>
>클라우드 인프라 환경의 Commerce에 대해 최신 버전의 `ece-tools` 패키지를 사용 중인지 확인하십시오. 그렇지 않으면 [최신 버전으로 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=ko)하십시오. `composer show magento/ece-tools` CLI 명령을 사용하여 로컬 환경에 설치된 버전을 확인할 수 있습니다.

## L2 캐시 구성

`REDIS_BACKEND` 구성 파일에서 `VALKEY_BACKEND` 또는 `.magento.env.yaml` 배포 변수를 설정하여 L2 캐시를 구성합니다.

>[!BEGINTABS]

>[!TAB Redis 구성]

Redis의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

클라우드 인프라의 환경 구성에 대해서는 [`REDIS_BACKEND`Commerce on Cloud Infrastructure 안내서](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_backend)의 __ 구성 참조를 참조하십시오.

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)에서 _Redis 페이지 캐싱 구성_&#x200B;을 참조하십시오.

>[!TAB Valkey 구성]

Valkey의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

클라우드 인프라의 환경 구성에 대해서는 [`VALKEY_BACKEND`Commerce on Cloud Infrastructure 안내서](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)의 __ 구성 참조를 참조하십시오.

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/config-valkey.md)에서 _Valkey 구성_&#x200B;을(를) 참조하십시오.

>[!ENDTABS]


### Adobe Commerce Cloud용 L2 캐시 메모리 크기 조정

L2 캐시는 저장소 메커니즘으로 [임시 파일 시스템](https://en.wikipedia.org/wiki/Tmpfs)&#x200B;(`/dev/shm`)을(를) 사용합니다. MPFS는 전문 키-밸류 저장소와 달리 키 제거 정책이 없으므로 메모리 사용량이 무제한 증가할 수 있습니다. 소진을 방지하기 위해 Adobe Commerce은 사용량이 구성 가능한 임계값(기본적으로 95%)에 도달하면 L2 저장소를 자동으로 지웁니다. 더 큰 `/dev/shm` 마운트를 요청하거나 정리 임계값을 낮추어 메모리 사용을 제어할 수 있습니다.

프로젝트 요구 사항에 따라 최대 L2 캐시 메모리 사용량을 조정합니다. 다음 방법 중 하나를 사용하십시오.

- `/dev/shm` 탑재 크기를 조정하려면 지원 티켓을 만드십시오. 이 시나리오에서는 `/dev/shm` 마운트 크기를 15GB로 설정하는 것이 좋습니다.
- 응용 프로그램 수준에서 `cleanup_percentage` 속성을 조정하여 다른 서비스에 사용할 수 있는 저장소 사용 및 사용 가능한 메모리를 제한합니다.
캐시 구성 그룹 `cache/frontend/default/backend_options/cleanup_percentage` 아래의 배포 구성에서 구성을 조정할 수 있습니다.

>[!NOTE]
>
>구성 가능한 `cleanup_percentage` 옵션이 Adobe Commerce 2.4.4에 도입되었습니다.

다음 예제는 `.magento.env.yaml` 파일의 구성 코드를 보여 줍니다.

>[!BEGINTABS]

>[!TAB Redis 구성]

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

>[!TAB Valkey 구성]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

캐시 요구 사항은 프로젝트 구성 및 사용자 지정 타사 코드에 따라 다릅니다. 캐시가 빈번한 임계값 히트 없이 작동할 수 있도록 L2 캐시 메모리의 크기를 지정합니다.

이상적으로 L2 캐시 메모리 사용은 빈번한 스토리지 지우기를 피하기 위해 임계값 아래에서 안정됩니다.

다음 CLI 명령을 실행하고 `/dev/shm` 줄을 검토하여 클러스터의 각 노드에서 L2 캐시 저장소 메모리 사용을 확인할 수 있습니다.

```bash
df -h /dev/shm
```

사용법은 노드에 따라 다를 수 있지만 비슷한 값으로 수렴해야 합니다.

## L2 캐시에 대한 사용자 지정 디렉터리 구성

L2 캐시 성능을 최적화할 때 RAM 디스크(`/dev/shm/`)와 같은 사용자 지정 고성능 디렉터리에 로컬 캐시 파일을 저장하도록 선택할 수 있습니다.

응용 프로그램 전체의 일관성을 보장하고 캐시 저장소가 조각화되지 않도록 하려면 특정 L2 백 엔드 옵션과 `app/etc/env.php` 파일 내의 전역 디렉터리 레지스트리를 모두 구성하십시오.

**모범 사례:** `local_backend_options['cache_dir']`과(와) 전역 `directories['cache']['path']`을(를) 모두 정의합니다.

- **`local_backend_options['cache_dir']`**: 백 엔드 캐시 어댑터(예: `Cm_Cache_Backend_File`)가 동기화된 L2 캐시 파일을 지정된 위치에 저장하도록 지시합니다.
- **`directories['cache']['path']`**: Adobe Commerce `DirectoryList` 레지스트리를 업데이트하여 사용자 지정 경로를 전체 응용 프로그램에 대한 최종 시스템 캐시 디렉터리로 설정합니다.

### 분할 캐시 디렉터리 및 GlusterFS 세그멘테이션 오류 방지

`local_backend_options`에서만 사용자 지정 경로를 정의하면 L2 캐시 엔진이 올바르게 작동하지만 전역 응용 프로그램 레지스트리는 `var/cache`을(를) 기본 캐시 위치로 계속 인식합니다.

이 구성이 일치하지 않으면 서드파티 확장 또는 핵심 대체 프로세스가 임시 파일을 기본 `var/cache` 디렉터리에 쓰는 &quot;브레인 분할&quot; 시나리오가 발생합니다.

**Adobe Commerce Cloud에 미치는 중요한 영향:** Pro 아키텍처에서 `var/` 디렉터리가 공유 분산 파일 시스템에 탑재되었습니다. 이 네트워크 마운트를 통해 고속 캐시 I/O를 강제로 수행하면 클라이언트가 압도되며 **GlusterFS 세그멘테이션 오류 및 클러스터 전체 정전**&#x200B;의 주요 트리거입니다. 두 설정을 모두 구성하면 모든 캐시 입출력이 로컬 고성능 디스크에 엄격하게 유지됩니다.

### 구성 예

단일 통합 캐시 디렉터리를 적용하려면 두 구성을 모두 포함하도록 `env.php` 파일을 업데이트하십시오.

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## 슬레이브 연결 활성화

`.magento.env.yaml` 파일에서 슬레이브 연결을 활성화하여 Adobe Commerce이 쓰기에 기본 끝점을 계속 사용하는 동안 읽기에 추가 읽기 전용 캐시 연결을 사용할 수 있도록 합니다. 이 구성을 통해 기본 캐시 서비스의 읽기 로드를 줄이고 읽기 트래픽을 보다 효과적으로 분산할 수 있습니다.

>[!BEGINTABS]

>[!TAB Redis 구성]

Redis의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Commerce Cloud 인프라의 환경 구성에 대해서는 [Commerce on Cloud Infrastructure Guide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#redis_use_slave_connection)의 _REDIS_USE_SLAVE_CONNECTION_&#x200B;을(를) 참조하십시오.

Adobe Commerce 온-프레미스 설치의 경우 `bin/magento setup` 명령을 사용하여 새 Redis 캐시 구현을 구성합니다. [구성 가이드](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)에서 _기본 캐시에 Redis 사용_&#x200B;을 참조하십시오.

>[!TAB Valkey 구성]

Valkey의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Commerce Cloud 인프라의 환경 구성에 대해서는 [Commerce on Cloud Infrastructure Guide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ko#valkey_use_slave_connection)의 _VALKEY_USE_SLAVE_CONNECTION_&#x200B;을(를) 참조하십시오.

Adobe Commerce 온-프레미스 설치의 경우 `bin/magento setup` 명령을 사용하여 새 Valkey 캐시 구현을 구성합니다. [구성 가이드](../../../configuration/cache/config-valkey.md)에서 _Valkey 구성_&#x200B;을(를) 참조하십시오.

>[!ENDTABS]

## 미리 로드 키

Magento은 일반적으로 Redis 또는 Valkey에서 캐시 항목을 한 번에 하나씩 로드합니다. 미리 로드 기능을 사용하면 Magento이 요청 중에 처음 액세스할 때 단일 파이프라인에서 가져오는 자주 사용하는 키 목록을 제공할 수 있습니다. 그런 다음 Magento은 가져온 값을 나머지 해당 요청에 대해 PHP 메모리에 유지하므로 Redis 또는 Valkey로의 반복된 라운드 트립이 줄어들고 해당 키에 대한 요청 부트스트랩 성능을 향상시킬 수 있습니다.

Redis 또는 Valkey에서 활성 명령을 모니터링하여 자주 사용되는 키를 식별할 수 있습니다.

>[!BEGINTABS]

>[!TAB 미리 로드 키 구성]

미리 로드 키가 `.magento.env.yaml` 구성 파일에 구성되어 있습니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

키를 나열하려면 다음 명령을 실행합니다.

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10초 후 **[!UICONTROL Ctrl+C]**&#x200B;을 누릅니다. 그런 다음 다음 다음 명령을 실행합니다.

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

이 로그에는 미리 로드할 수 있는 키가 나열됩니다. 키의 내용을 보려면 다음 명령을 실행합니다.

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)에서 _Redis 미리 로드 기능_&#x200B;을 참조하세요.

>[!TAB 키 미리 로드 키 구성]

미리 로드 키가 `.magento.env.yaml` 구성 파일에 구성되어 있습니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

키를 나열하려면 다음 명령을 실행합니다.

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10초 후 **[!UICONTROL Ctrl+C]**&#x200B;을 누릅니다. 그런 다음 다음 다음 명령을 실행합니다.

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

이 로그에는 미리 로드할 수 있는 키가 나열됩니다. 키의 내용을 보려면 다음 명령을 실행합니다.

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature)에서 _Valkey 미리 로드 기능_&#x200B;을(를) 참조하십시오.

>[!ENDTABS]

## 부실 캐시 활성화

부실 캐시는 `RemoteSynchronizedCache`의 L2 캐시 기능입니다. 활성화하면 모든 동시 요청을 대기시키는 대신 다른 요청이 이미 동일한 항목을 다시 생성하는 동안 Adobe Commerce은 `/dev/shm`에서 기존 로컬 캐시 값을 제공할 수 있습니다. 이렇게 하면 값비싼 캐시 항목을 재생성하는 동안 캐시 스템피드 및 잠금 경합이 줄어듭니다.

### 작동 방식

`RemoteSynchronizedCache`을(를) 사용하면 Magento은 각 캐시 항목의 복사본 두 개를 유지 관리합니다. 하나는 `/dev/shm`에 로컬 복사본이고 다른 하나는 Redis 또는 Valkey에 원격 복사본입니다. 원격 복사본을 사용할 수 없고 해당 키에 대한 재생성 잠금이 이미 있는 경우, 동시 요청은 새 값이 기록될 때까지 기다리지 않고 이전 로컬 값을 수신할 수 있습니다.

부실 캐시를 활성화하려면 `.magento.env.yaml` 파일에서 구성하십시오.

>[!BEGINTABS]

>[!TAB Redis에 대한 부실 캐시 구성]

레디스의 경우:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Valkey에 대한 부실 캐시 구성]

Valkey의 경우:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>`full_page` 캐시 형식은 [Fastly](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly)을(를) 사용하므로 Cloud 인프라 프로젝트의 Adobe Commerce과 관련이 없습니다.

온-프레미스 설치의 경우 [구성 가이드](../../../configuration/cache/level-two-cache.md#stale-cache-options)에서 _오래된 캐시 옵션_&#x200B;을 참조하세요.

>[!WARNING]
>
>위의 구성은 `default` 캐시 프런트 엔드에서 오래된 캐시를 활성화하며, 이로 인해 해당 프런트 엔드를 사용하는 모든 캐시 항목에 오래된 캐시 동작이 적용됩니다. Magento 코어 캐시 유형은 일반적으로 이 설정에서 예상대로 작동합니다. 그러나 프로젝트에 전용 캐시 프론트엔드 없이 일반 `\Magento\Framework\App\Cache` API(예: `$this->cache->save()`)를 통해 캐시에 쓰는 사용자 지정 코드 또는 확장이 포함되어 있는 경우 이러한 항목은 재생성 중에도 부실 값을 제공할 수 있습니다.
>
>
>이로 인해 사용자 지정에 예기치 않은 동작이 발생하는 경우 `default` 프런트 엔드에 오래된 캐시를 사용하지 않도록 설정한 후 일반적으로 [완료 온-프레미스](../../../configuration/cache/level-two-cache.md#stale-cache-options)와 같이 선택한 캐시 유형에 대해서만 사용하도록 설정하십시오.

### 캐시 유형당 부실 캐시를 개별적으로 활성화

`.magento.env.yaml`에서 전용 캐시 프런트 엔드를 정의하고 선택한 캐시 유형을 매핑하여 선택한 캐시 유형에 대해서만 오래된 캐시를 활성화할 수 있습니다.

올바르게 작동하려면 사용자 지정 프론트엔드를 `CACHE_CONFIGURATION.frontend`에서 전체 프론트엔드로 정의해야 합니다. 새 프론트엔드 이름에 대해 `use_stale_cache: true`만 정의하면 충분하지 않습니다.

**예제 구성**

>[!BEGINTABS]

>[!TAB Redis에 대한 부실 캐시 구성]

레디스의 경우:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Valkey에 대한 부실 캐시 구성]

Valkey의 경우:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>소스 프론트엔드가 압축, 다시 시도, 미리 로드 키 또는 기타 조정 값과 같은 추가 백엔드 옵션으로 구성된 경우, 새 프론트엔드가 동일한 동작을 유지하도록 해당 옵션을 `stale_cache_enabled`에 복사합니다.


## 별도의 캐시 및 세션 인스턴스

캐시와 세션을 분리하면 독립적으로 관리할 수 있습니다. 캐시와 세션 트래픽 간의 경합을 줄이고, 캐시 관련 압력이 세션에 영향을 주지 않도록 하며, 각 Redis 또는 Valkey 인스턴스의 크기를 조정하고 자체 워크로드에 맞게 조정할 수 있도록 합니다.

세션에 대한 전용 인스턴스를 프로비저닝하려면 아래 단계를 따르십시오.

>[!BEGINTABS]

>[!TAB 레디스]

1. `.magento/services.yaml` 구성 파일을 업데이트합니다.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. 프로덕션 및 스테이징 환경에서 세션 전용 새 Redis 인스턴스를 요청합니다.

   [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)을 제출하세요. 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일을 포함합니다.

   이 업데이트로 인해 가동 중지 시간은 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 확인합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. `.magento.env.yaml` 구성 파일에 포트 번호를 추가합니다.

   >[!IMPORTANT]
   >
   >`ece-tools`이(가) `MAGENTO_CLOUD_RELATIONSHIPS` Redis 세션 서비스 정의에서 자동으로 검색할 수 없는 경우에만 Redis 세션 포트를 구성하십시오.

   >[!NOTE]
   >
   >최상의 성능을 위해 `disable_locking`을(를) `1`(으)로 설정하십시오. 드문 경우지만 동시 세션 활동이 많기 때문에 경합 상태가 발생하는 경우 잠금을 활성화하려면 `0`(으)로 설정하십시오.

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

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. `.magento/services.yaml` 구성 파일을 업데이트합니다.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 프로덕션 및 스테이징 환경에서 세션 전용 새 Valkey 인스턴스를 요청합니다.

   [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)을 제출하세요. 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일을 포함합니다.

   이 업데이트로 인해 가동 중지 시간은 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 확인합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. `.magento.env.yaml` 구성 파일에 포트 번호를 추가합니다.

   >[!IMPORTANT]
   >
   >`ece-tools`이(가) `MAGENTO_CLOUD_RELATIONSHIPS` Valkey 세션 서비스 정의에서 Valkey 세션 포트를 자동으로 검색할 수 없는 경우에만 Valkey 세션 포트를 구성하십시오.

   >[!NOTE]
   >
   >최상의 성능을 위해 `disable_locking`을(를) `1`(으)로 설정하십시오. 드문 경우지만 동시 세션 활동이 많기 때문에 경합 상태가 발생하는 경우 잠금을 활성화하려면 `0`(으)로 설정하십시오.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Valkey 캐시 인스턴스의 [기본 데이터베이스](../../../configuration/cache/redis-pg-cache.md)(`db 0`)에서 세션을 제거합니다.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 캐시 압축

6GB 이상의 Redis 또는 Valkey `maxmemory`을(를) 사용하는 경우 캐시 압축을 사용하여 키에 사용되는 공간을 줄일 수 있습니다. 이 설정은 메모리 절감을 위해 클라이언트측 성능을 처리합니다. 여유 CPU 용량이 있는 경우 활성화해 보십시오. [구성 가이드](../../../configuration/cache/redis-session.md)에서 [세션 저장소에 Redis 사용](../../../configuration/cache/valkey-session.md) 또는 _세션 저장소에 Valkey 사용_&#x200B;을 참조하십시오.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 비동기 해제 사용

클라우드 인프라의 Adobe Commerce에서 `lazyfree`을(를) 사용하려면 다음 Redis 또는 Valkey 구성을 환경에 적용할 것을 요청하는 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)합니다.

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

`lazyfree`이(가) 활성화되면 Redis 또는 Valkey는 제거, 만료, 서버에서 시작된 삭제, 사용자 삭제 및 복제본 데이터 세트 플러시를 위해 백그라운드 스레드로 메모리 재확보를 오프로드합니다. 이렇게 하면 기본 스레드 차단이 줄어들고 요청 지연이 감소할 수 있습니다.

>[!NOTE]
>
>`lazyfree-lazy-user-del yes` 옵션을 사용하면 `DEL` 명령이 `UNLINK`과(와) 같이 동작하여 키의 연결이 즉시 해제되고 비동기적으로 메모리를 확보할 수 있습니다.

>[!WARNING]
>
>백그라운드에서 자유롭게 작업하기 때문에 백그라운드 스레드에서 작업을 완료할 때까지 삭제되거나 만료되거나 제거된 키에서 사용하는 메모리가 할당된 상태로 유지됩니다. Redis 또는 Valkey 인스턴스에 이미 메모리가 부족할 경우 신중하게 테스트하고 먼저 메모리 압력을 줄이는 것이 좋습니다. 예를 들어, 특정 경우에 대해 블록 캐시를 비활성화하고 위에 설명된 대로 캐시 및 세션 Redis 인스턴스를 구분합니다.

## 다중 스레드 I/O 사용

클라우드 인프라의 Adobe Commerce에서 Redis I/O 스레딩을 사용하려면 아래의 I/O 스레딩 구성을 요청하는 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ko#submit-ticket)을 제출하십시오. 이 구성은 더 높은 CPU 사용량을 희생하여 주 스레드에서 소켓 읽기 및 쓰기, 명령 구문 분석을 오프로드하여 처리량을 향상시킬 수 있습니다. 로드 중 유효성 검사 및 호스트 모니터링

>[!BEGINTABS]

>[!TAB Redis에 대한 I/O 스레드 구성]

레디스의 경우:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Valkey에 대한 I/O 스레드 구성]

Valkey의 경우:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I/O 스레드는 클라이언트 I/O를 병렬화하고 구문 분석만 수행합니다. Redis 명령 실행은 단일 스레드로 유지됩니다.

>[!WARNING]
>
>I/O 스레드를 활성화하면 CPU 사용량이 늘어날 수 있으며 모든 워크로드에는 도움이 되지 않습니다. 보수적인 가치와 벤치마크로 시작하십시오. 지연이 증가하거나 CPU이 포화되면 `io-threads`을(를) 줄이거나 I/O 스레드에서 읽기를 사용하지 않도록 설정하십시오.


## 클라이언트 시간 초과 및 재시도 증가

`.magento.env.yaml`에서 백엔드 옵션을 조정하여 Redis 또는 Valkey 캐시 클라이언트의 허용 한도를 짧은 채도 기간으로 늘립니다.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

이러한 설정은 연결 설정을 다시 시도하고 Redis 또는 Valkey에서 답글 작성 시간을 더 많이 허용하여 짧은 스파이크 동안 간헐적인 연결 및 읽기 시간 초과 오류를 줄일 수 있습니다.

>[!NOTE]
>
>이러한 설정은 일시적인 정체에 도움이 될 수 있지만 지속적인 과부하를 해결하지는 못합니다.

## 구성 예

다음 예를 Redis 또는 Valkey 서비스 구성의 시작점으로 사용하십시오.


### 모든 모범 사례 권장 사항 적용

>[!BEGINTABS]

>[!TAB 레디스]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey 구성 예]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### 모든 모범 사례 권장 사항을 적용하고 캐시 유형별로 오래된 캐시를 구분합니다.

>[!BEGINTABS]

>[!TAB 레디스]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## 추가 정보

다음 관련 항목을 참조하십시오.

- [Redis 페이지 캐시](../../../configuration/cache/redis-pg-cache.md)
- [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md)
- [기본 캐시에 Valkey 사용](../../../configuration/cache/valkey-pg-cache.md)
- [세션 저장소에 Valkey 사용](../../../configuration/cache/valkey-session.md)
