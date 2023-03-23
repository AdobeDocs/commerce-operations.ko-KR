---
title: Redis 서비스 구성에 대한 우수 사례
description: Adobe Commerce에 대한 확장된 Redis 캐시 구현을 사용하여 캐싱 성능을 향상시키는 방법을 알아봅니다.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 92faa85b51a1fd5314a5906e8650b03723118ce1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Redis 서비스 구성에 대한 우수 사례

- Adobe Commerce의 각 요청에 대해 수행되는 Redis 쿼리 수를 최소화하기 위해 다음 최적화를 포함하는 확장된 Redis 캐시 구현을 사용하십시오.
   - Redis와 Adobe Commerce 간의 네트워크 데이터 전송 크기 감소
   - 로드해야 하는 사항을 자동으로 결정할 수 있는 어댑터의 기능을 개선하여 CPU 사이클의 Redis를 줄입니다.
   - Redis 쓰기 작업에 대한 경합 조건 감소
- Redis 캐시에서 Redis 세션을 분리하십시오
- Redis 캐시 압축 및 사용 `gzip` 성능을 향상시키다

## 확장된 Redis 캐시 구현

확장된 Redis 캐시 구현을 사용하도록 구성을 업데이트합니다 `\Magento\Framework\Cache\Backend\Redis`.

### 클라우드 배포 구성

를 설정하여 향상된 Redis 캐시를 구성합니다. `REDIS_BACKEND` 의 배포 변수 `.magento.env.yaml` 구성 파일.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

자세한 내용은 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 변수 설명 _Commerce on Cloud Infrastructure 안내서_.

>[!NOTE]
>
> 을(를) 확인합니다. `ece-tools` 를 사용하여 명령줄에서 로컬 환경에 설치된 버전 `composer show magento/ece-tools` 명령. 필요한 경우 [최신 버전으로 업데이트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>작업 _not_ 클라우드 인프라 프로젝트에 대한 Redis 슬레이브 연결 구성 [스케일 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 이로 인해 Redis 연결 오류가 발생합니다. 자세한 내용은 [Redis 구성 지침](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 에서 _클라우드 기반의 상거래_ 안내서.

### 온-프레미스 배포 구성

Adobe Commerce 온-프레미스 배포의 경우, `bin/magento:setup` 명령. 자세한 내용은 [기본 캐시에 Redis 사용](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 별도의 캐시 및 세션 인스턴스

Redis 세션에서 Redis 캐시를 분리하면 캐시 문제가 세션에 영향을 주지 않도록 캐시 및 세션을 독립적으로 관리할 수 있습니다.

1. 업데이트 `.magento/services.yaml` 구성 파일.

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

1. 업데이트 `.magento.app.yaml` 구성 파일.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 제출 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pro 프로덕션 및 스테이징 환경에서 Redis 서비스 구성을 변경하려면 다음을 수행하십시오. 업데이트된 내용을 포함합니다 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 기록합니다.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 포트 번호를 `.magento.env.yaml` 구성 파일.

   >[!NOTE]
   >`disable_locking` 를 로 설정해야 합니다. `1`.

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

1. 에서 세션 제거 [기본 데이터베이스](../../../configuration/cache/redis-pg-cache.md) (`db 0`)을 클릭하여 Redis 캐시 인스턴스에 배치합니다.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

배포 중에 [로그 작성 및 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

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

캐시 압축을 사용하지만 클라이언트측 성능과 교환이 있다는 것을 인식하십시오. 예비 CPU가 있는 경우 활성화합니다. 자세한 내용은 [세션 저장소에 Redis 사용](../../../configuration/cache/redis-session.md).

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
- [세션 저장소에 Redis 사용](../../../configuration/cache/redis-session.md)
