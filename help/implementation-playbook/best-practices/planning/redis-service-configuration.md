---
title: Redis 서비스 구성에 대한 우수 사례
description: Adobe Commerce용 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법에 대해 알아봅니다.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 156e6412b9f94b74bad040b698f466808b0360e3
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Redis 서비스 구성에 대한 우수 사례

- Redis L2 캐시 구성
- Redis 슬레이브 연결 활성화
- 미리 로드 키
- 부실 캐시 활성화
- Redis 캐시와 Redis 세션 분리
- Redis 캐시 압축 및 사용 `gzip` 높은 압축률을 위해

## Redis L2 캐시 구성

다음을 설정하여 Redis L2 캐시 구성 `REDIS_BACKEND` 의 배포 변수 `.magento.env.yaml` 구성 파일입니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

클라우드 인프라의 환경 구성에 대해서는 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 다음에서 _클라우드 인프라의 Commerce 안내서_.

온-프레미스 설치의 경우 [Redis 페이지 캐싱 구성](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) 다음에서 _구성 안내서_.

>[!NOTE]
>
>최신 버전의 를 사용 중인지 확인합니다. `ece-tools` 패키지. 그렇지 않은 경우, [최신 버전으로 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). 를 사용하여 로컬 환경에 설치된 버전을 확인할 수 있습니다. `composer show magento/ece-tools` CLI 명령입니다.

## Redis 슬레이브 연결 활성화

에서 Redis 슬레이브 연결 활성화 `.magento.env.yaml` 한 노드만 읽기-쓰기 트래픽을 처리하고 다른 노드는 읽기 전용 트래픽을 처리하도록 구성 파일입니다.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

다음을 참조하십시오 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 다음에서 _클라우드 인프라의 Commerce 안내서_.

Adobe Commerce 온-프레미스 설치의 경우 `bin/magento:setup` 명령입니다. 다음을 참조하십시오 [기본 캐시에 Redis 사용](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) 다음에서 _구성 안내서_.

>[!WARNING]
>
>실행 _아님_ 를 사용하여 클라우드 인프라 프로젝트에 대한 Redis 슬레이브 연결 구성 [크기 조정/분할 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 이로 인해 Redis 연결 오류가 발생합니다. 다음을 참조하십시오 [Redis 구성 지침](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 다음에서 _클라우드 인프라의 상거래_ 가이드.

## 미리 로드 키

페이지 간에 데이터를 재사용하려면 `.magento.env.yaml` 구성 파일입니다.

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

온-프레미스 설치의 경우 [Redis 미리 로드 기능](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) 다음에서 _구성 안내서_.

## 부실 캐시 활성화

특히 오래된 캐시를 사용하여 새로운 캐시를 동시에 생성함으로써 잠금 대기 시간을 줄이고 성능을 향상시킬 수 있습니다. 부실 캐시를 활성화하고 `.magento.env.yaml` 구성 파일:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

온-프레미스 설치 구성에 대해서는 [부실 캐시 옵션](../../../configuration/cache/level-two-cache.md#stale-cache-options) 다음에서 _구성 안내서_.

## 별도의 Redis 캐시 및 세션 인스턴스

Redis 캐시와 Redis 세션을 분리하면 캐시와 세션을 독립적으로 관리할 수 있습니다. 이는 캐시 문제가 세션에 영향을 주지 않도록 하여 매출에 영향을 줄 수 있습니다. 각 Redis 인스턴스는 자체 코어에서 실행되므로 성능이 향상됩니다.

1. 업데이트 `.magento/services.yaml` 구성 파일입니다.

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

1. 업데이트 `.magento.app.yaml` 구성 파일입니다.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 제출 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 운영 및 스테이징 환경에서 세션 전용 새 Redis 인스턴스의 프로비저닝을 요청합니다. 업데이트된 항목 포함 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일입니다. 이 경우 다운타임이 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 기록합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 포트 번호를 `.magento.env.yaml` 구성 파일입니다.

   >[!NOTE]
   >`disable_locking` 은(는) 로 설정되어야 합니다. `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 에서 세션 제거 [기본 데이터베이스](../../../configuration/cache/redis-pg-cache.md) (`db 0`)을 클릭하여 Redis Cache 인스턴스를 검색합니다.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

배포하는 동안 [로그 작성 및 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
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

6GB 이상의 Redis를 사용하는 경우 `maxmemory`, 캐시 압축을 사용하여 키에서 사용하는 공간을 줄일 수 있습니다. 클라이언트측 성능이 저하됩니다. 예비 CPU가 있는 경우 활성화합니다. 다음을 참조하십시오 [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md) 다음에서 _구성 안내서_.

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

## 추가 정보

- [Redis 페이지 캐시](../../../configuration/cache/redis-pg-cache.md)
- [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md)
