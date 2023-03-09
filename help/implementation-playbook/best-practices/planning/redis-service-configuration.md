---
title: Redis 서비스 구성에 대한 우수 사례
description: Adobe Commerce용 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법에 대해 알아봅니다.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: e7888688803d86ec342b156da77adc663475fe20
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Redis 서비스 구성에 대한 우수 사례

- Adobe Commerce의 각 요청에 대해 수행되는 Redis 쿼리 수를 최소화하기 위한 다음 최적화가 포함된 확장된 Redis 캐시 구현을 사용하십시오.
   - Redis와 Adobe Commerce 간의 네트워크 데이터 전송 크기 감소
   - 어댑터에서 무엇을 로드해야 하는지 자동으로 판별하는 기능을 향상시켜 CPU 사이클의 Redis 사용량 감소
   - Redis 쓰기 작업에 대한 경합 조건 감소
- Redis 캐시와 Redis 세션 분리
- Redis 캐시 압축 및 사용 `gzip` 성능 향상

## 확장된 Redis 캐시 구현

확장된 Redis 캐시 구현을 사용하도록 구성 업데이트 `\Magento\Framework\Cache\Backend\Redis`.

### 클라우드 배포 구성

다음을 설정하여 향상된 Redis 캐시 구성 `REDIS_BACKEND` 의 배포 변수 `.magento.env.yaml` 구성 파일입니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

자세한 내용은 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 의 변수 설명 _클라우드 인프라의 Commerce 안내서_.

>[!NOTE]
>
> 다음 확인: `ece-tools` 를 사용하여 명령줄에서 로컬 환경에 설치된 버전 `composer show magento/ece-tools` 명령입니다. 필요한 경우 [최신 버전으로 업데이트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>실행 _아님_ 를 사용하여 클라우드 인프라 프로젝트에 대한 Redis 슬레이브 연결 구성 [확장 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 이로 인해 Redis 연결 오류가 발생합니다. 다음을 참조하십시오 [redis 구성 지침](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 다음에서 _클라우드 인프라의 상거래_ 가이드.

### 온-프레미스 배포 구성

Adobe Commerce 온-프레미스 배포의 경우 다음을 사용하여 새 Redis 캐시 구현을 구성합니다. `bin/magento:setup` 명령입니다. 자세한 내용은 [기본 캐시에 Redis 사용](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 별도의 캐시 및 세션 인스턴스

Redis 캐시와 Redis 세션을 분리하면 캐시 문제가 세션에 영향을 주지 않도록 캐시와 세션을 독립적으로 관리할 수 있습니다.

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

1. 제출 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) Pro 프로덕션 및 스테이징 환경에서 Redis 서비스 구성을 변경합니다. 업데이트된 항목 포함 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일입니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 기록합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 포트 번호를 `.magento.env.yaml` 구성 파일입니다.

   >[!NOTE]
   >`disable_locking` 은(는) 로 설정되어야 합니다. `1`.

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

캐시 압축을 사용하지만 클라이언트측 성능이 저하됩니다. 예비 CPU가 있는 경우 활성화합니다. 다음을 참조하십시오 [세션 스토리지에 Redis 사용](../../../configuration/cache/redis-session.md).

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
