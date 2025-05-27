---
title: Valkey 서비스 구성에 대한 우수 사례
description: Adobe Commerce용 확장된 Valkey 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법을 알아봅니다.
role: Developer, Admin
feature: Best Practices, Cache
source-git-commit: 107b5bb19c3375be64c216bd89feb8410e2fc2bd
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Valkey 서비스 구성에 대한 우수 사례

Adobe은 Valkey 서비스를 구성할 때 다음 모범 사례를 권장합니다.

## Valkey L2 캐시 구성

`.magento.env.yaml` 구성 파일에서 `VALKEY_BACKEND` 배포 변수를 설정하여 Valkey L2 캐시를 구성합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

클라우드 인프라의 환경 구성에 대해서는 _Commerce on Cloud Infrastructure Guide_&#x200B;의 [`VALKEY_BACKEND`](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)을(를) 참조하십시오.

온-프레미스 설치의 경우 _구성 가이드_&#x200B;에서 [Valkey 페이지 캐싱 구성](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)을 참조하십시오.

>[!NOTE]
>
>최신 버전의 `ece-tools` 패키지를 사용 중인지 확인하십시오. 그렇지 않으면 [최신 버전으로 업그레이드](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)하십시오. `composer show magento/ece-tools` CLI 명령을 사용하여 로컬 환경에 설치된 버전을 확인할 수 있습니다.

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
>`cleanup_percentage` 구성 옵션이 Adobe Commerce 2.4.4에 도입되었습니다.

다음 예제에서는 `.magento.env.yaml` 파일의 `CACHE_CONFIGURATION`을(를) 보여 줍니다.

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

캐시 요구 사항은 프로젝트 구성 및 사용자 지정 타사 코드에 따라 다를 수 있습니다. L2 캐시 메모리 크기 조정 범위를 사용하면 L2 캐시가 불필요한 임계값 히트 없이 작동할 수 있습니다.
이상적으로 L2 캐시 메모리 사용은 빈번한 스토리지 지우기를 방지하기 위해 임계값 아래의 특정 수준에서 안정되어야 합니다.

다음 CLI 명령을 사용하여 클러스터의 각 노드에서 L2 캐시 저장소 메모리 사용을 확인한 다음 `/dev/shm` 줄을 검색할 수 있습니다.
사용은 서로 다른 노드에 걸쳐 다를 수 있지만 동일한 값으로 수렴해야 합니다.

```bash
df -h
```

## Valkey 슬레이브 연결 활성화

`.magento.env.yaml` 구성 파일에서 Valkey 슬레이브 연결을 활성화하여 한 노드만 읽기-쓰기 트래픽을 처리하고 다른 노드는 읽기 전용 트래픽을 처리하도록 합니다.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

자세한 내용은 _Commerce on Cloud Infrastructure Guide_&#x200B;의 [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection)을(를) 참조하십시오.

Adobe Commerce 온-프레미스 설치의 경우 `bin/magento:setup` 명령을 사용하여 새 Valkey 캐시 구현을 구성합니다. 자세한 내용은 _구성 가이드_&#x200B;에서 [기본 캐시에 대한 Valkey 사용](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)을 참조하십시오.

>[!WARNING]
>
>[크기 조정/분할 아키텍처](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture)를 사용하여 클라우드 인프라 프로젝트에 대한 올바른 슬레이브 연결을 구성하지 _마십시오_. 이로 인해 Redis 연결 오류가 발생합니다. 자세한 내용은 _클라우드 인프라의 Commerce_ 안내서의 [Redis 구성 지침](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection)을 참조하십시오.

## 미리 로드 키

페이지 간에 데이터를 다시 사용하려면 미리 로드할 키를 `.magento.env.yaml` 구성 파일에 나열합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

온-프레미스 설치의 경우 _구성 가이드_&#x200B;에서 [Valkey 미리 로드 기능](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)을(를) 참조하십시오.

## 부실 캐시 활성화

특히 오래된 캐시를 사용하여 새로운 캐시를 동시에 생성함으로써 잠금 대기 시간을 줄이고 성능을 향상시킵니다. 부실 캐시를 사용하도록 설정하고 `.magento.env.yaml` 구성 파일에서 캐시 형식을 정의합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>앞의 예에서 `full_page` 캐시는 [Fastly](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/cdn/fastly)를 사용하므로 클라우드 인프라 프로젝트의 Adobe Commerce과 관련이 없습니다.

온-프레미스 설치를 구성하려면 _구성 가이드_&#x200B;에서 [오래된 캐시 옵션](../../../configuration/cache/level-two-cache.md#stale-cache-options)을 참조하십시오.

배포 중에 [빌드 및 배포 로그](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations.html#build-and-deploy-logs)에 다음 줄이 표시됩니다.

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## 캐시 압축

6GB가 넘는 Valkey `maxmemory`을(를) 사용하는 경우 캐시 압축을 사용하여 키에서 사용하는 공간을 줄일 수 있습니다. 클라이언트측 성능이 저하됩니다. 예비 CPU가 있는 경우 Adobe에서 이를 활성화하도록 권장합니다. _구성 가이드_&#x200B;에서 [세션 저장소에 Redis 사용](../../../configuration/cache/redis-session.md)을 참조하십시오.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```

## 추가 정보

- [Redis 페이지 캐시](../../../configuration/cache/redis-pg-cache.md)
- [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md)
