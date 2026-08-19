---
title: Valkey 및 Redis 서비스 구성에 대한 우수 사례
description: 복제본 연결, L2 캐시, 부실 캐시 및 세션 저장소를 포함하여 클라우드에서 Adobe Commerce에 대한 Redis 및 Valkey 캐싱을 구성하는 방법에 대해 알아봅니다.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="클라우드의 Commerce" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="클라우드 프로젝트의 Adobe Commerce에만 적용됩니다."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 55f36b56b5d719ace064eccf42675cd8f9b7683b
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Valkey 및 Redis 서비스 구성에 대한 우수 사례

Adobe Commerce 애플리케이션 캐시, 세션 저장소 및 Adobe Commerce on Cloud 배포용 L2 캐시에 대해 Redis 또는 Valkey를 구성할 때 이러한 권장 사항을 사용하십시오.

Adobe Commerce 온-프레미스 캐시 구성에 대해서는 성능 최적화를 위한 [L2 캐시 구성](/help/configuration/cache/level-two-cache.md)을 참조하세요.

>[!NOTE]
>
>이 항목에서는 Commerce 애플리케이션 캐시 및 세션 백엔드에 대해 설명합니다. Fastly 또는 Varnish와 같은 HTTP 전체 페이지 캐싱은 별도의 캐싱 레이어이며 독립적으로 구성됩니다. 애플리케이션 캐시 백엔드에 대한 변경 사항은 HTTP 전체 페이지 캐시를 대체하거나 구성하지 않습니다.

이러한 권장 사항에서는 다음 사항을 다룹니다.

- 지원되는 캐시 서비스 선택
- 복제본 연결 사용
- 별도의 캐시 및 세션 인스턴스
- 캐시 압축 구성
- 비동기 해제 사용
- 다중 스레드 I/O 사용
- 클라이언트 시간 초과 및 재시도 증가
- 미리 로드 키, 부실 캐시 및 [!DNL Symfony] L2 캐시를 포함하여 L2 캐시 구성
- 구성 예제 검토

## 지원되는 캐시 서비스 선택

| Adobe Commerce 버전 | 권장 캐시 서비스 | L2 캐시 구현 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 이하(정확한 릴리스에서 지원되는 경우) | 레디스 또는 발키 | RemoteSynchronizedCache |
| 2.4.9 이상 | 밸키 | symfony_l2 |

Redis는 Adobe Commerce 2.4.9 및 시스템 요구 사항이 대신 Valkey를 지정하는 패치 릴리스의 캐시 구성에 대해 지원되지 않습니다. [캐시 백엔드 옵션 및 저장소 참조](/help/configuration/cache/cache-options.md) 및 [시스템 요구 사항](/help/installation/system-requirements.md)에서 항상 정확한 Commerce 버전, 패치 수준 및 서비스 버전을 확인하십시오.

>[!NOTE]
>
>최신 버전의 `ece-tools` 패키지를 사용 중인지 확인하십시오. 그렇지 않으면 [최신 버전으로 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)하십시오. `composer show magento/ece-tools` CLI 명령을 사용하여 로컬 환경에 설치된 버전을 확인할 수 있습니다.

## 복제본 연결 사용

`.magento.env.yaml` 파일에서 복제본 연결을 사용하도록 설정합니다. 이 변경 사항으로 Adobe Commerce은 쓰기에 기본 끝점을 계속 사용하는 동안 읽기에 추가 캐시 연결을 사용할 수 있습니다. 이 구성을 통해 기본 캐시 서비스의 읽기 로드를 줄이고 읽기 트래픽을 보다 효과적으로 분산할 수 있습니다.

>[!NOTE]
>
>복제 연결을 사용할 수 있는지 여부는 프로젝트의 토폴로지(예: 단일 노드 대 분할 또는 HA 아키텍처) 및 `ece-tools` 버전에 따라 다릅니다. 이 설정을 사용하기 전에 `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp`을(를) 실행하고 `USE_SLAVE_CONNECTION` 항목을 확인하여 서비스에 대한 복제본 관계가 있는지 확인하십시오. 토폴로지에서 복제본 끝점을 프로비전하는지 확인하려면 `ece-tools`을(를) 업그레이드하고 다시 배포하거나 `USE_SLAVE_CONNECTION` 항목이 없는 경우 Adobe Commerce 지원에 문의하세요.
>
>`symfony_l2`의 경우 복제본 연결 지원은 `ece-tools` 및 클라우드 패치 업데이트를 통해 제공됩니다. `VALKEY_USE_SLAVE_CONNECTION: true`을(를) 변경하는 것 외에는 추가 캐시 구성이 필요하지 않습니다. 수정 사항을 받으려면 최신 `ece-tools` 버전으로 업데이트하십시오.

>[!BEGINTABS]

>[!TAB Valkey 구성]

Valkey의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

환경 변수 구성에 대한 자세한 내용은 _Commerce on Cloud Infrastructure Guide_&#x200B;의 [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)을(를) 참조하십시오.

>[!TAB Redis 구성]

Redis의 경우 다음을 사용합니다.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

환경 변수 구성에 대한 자세한 내용은 _Commerce on Cloud Infrastructure Guide_&#x200B;의 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)을(를) 참조하십시오.

>[!ENDTABS]

## 별도의 캐시 및 세션 인스턴스

캐시와 세션 구성은 독립적입니다. 사용하는 캐시 백 엔드 또는 L2 캐시 구현에 관계없이 `SESSION_CONFIGURATION`은(는) 캐시 동작에 영향을 주지 않습니다. 캐시와 세션을 분리하면 독립적으로 관리할 수 있습니다. 캐시와 세션 트래픽 간의 경합을 줄이고, 캐시 관련 압력이 세션에 영향을 주지 않도록 하며, 각 Redis 또는 Valkey 인스턴스의 크기를 조정하고 자체 워크로드에 맞게 조정할 수 있도록 합니다.

>[!IMPORTANT]
>
>프로덕션 및 스테이징에서 전용 세션 인스턴스를 프로비저닝하는 것은 셀프서비스가 아닙니다. 아래 3단계에 설명된 대로 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 파일과 함께 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)을 제출해야 합니다.

세션에 대한 전용 인스턴스를 프로비저닝하려면 아래 단계를 따르십시오.

>[!BEGINTABS]

>[!TAB Valkey]

1. `.magento/services.yaml` 구성 파일을 업데이트하여 `<version>`을(를) 사용 중인 서비스 버전으로 바꿉니다. 릴리스별 지원되는 서비스 버전에 대해서는 [시스템 요구 사항](/help/installation/system-requirements.md)을 참조하십시오.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)을 제출하세요. 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일을 포함합니다.

   이 업데이트로 인해 가동 중지 시간은 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 확인합니다.

   ```shell
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

1. Valkey 캐시 인스턴스의 [기본 데이터베이스](/help/configuration/cache/redis-pg-cache.md)(`db 0`)에서 세션을 제거합니다.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB 레디스]

1. `.magento/services.yaml` 구성 파일을 업데이트하여 `<version>`을(를) 사용 중인 서비스 버전으로 바꿉니다.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)을 제출하세요. 업데이트된 `.magento/services.yaml` 및 `.magento.app.yaml` 구성 파일을 포함합니다.

   이 업데이트로 인해 가동 중지 시간은 발생하지 않지만, 새 서비스를 활성화하려면 배포가 필요합니다.

1. 새 인스턴스가 실행 중인지 확인하고 포트 번호를 확인합니다.

   ```shell
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

1. Redis 캐시 인스턴스의 [기본 데이터베이스](/help/configuration/cache/redis-pg-cache.md)(`db 0`)에서 세션을 제거합니다.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 캐시 압축

6GB 이상의 Redis 또는 Valkey `maxmemory`을(를) 사용하는 경우 캐시 압축을 사용하여 키에 사용되는 공간을 줄일 수 있습니다. 이 설정은 메모리 절감을 위해 클라이언트측 성능을 처리합니다. 여유 CPU 용량이 있는 경우 활성화해 보십시오. _구성 가이드_&#x200B;에서 [세션 저장소에 Redis 사용](/help/configuration/cache/redis-session.md) 또는 [세션 저장소에 Valkey 사용](/help/configuration/cache/valkey-session.md)을 참조하십시오.

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

Adobe Commerce 클라우드 인프라에서 `lazyfree`을(를) 사용하려면 다음 Redis 또는 Valkey 구성을 환경에 적용할 것을 요청하는 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)합니다.

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

Adobe Commerce 클라우드 인프라에서 Redis I/O 스레딩을 사용하려면 아래의 I/O 스레딩 구성을 요청하는 [Adobe Commerce 지원 티켓](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)을 제출하십시오. 이 구성은 더 높은 CPU 사용 비용으로 소켓 읽기, 쓰기 및 명령 구문 분석을 기본 스레드에서 오프로드하여 처리량을 향상시킬 수 있습니다. 로드 중 유효성 검사 및 호스트 모니터링

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

## L2 캐시 구성

`.magento.env.yaml` 구성 파일에서 `VALKEY_BACKEND` 또는 `REDIS_BACKEND` 배포 변수를 설정하여 L2 캐시를 구성합니다.

클라우드 인프라의 Adobe Commerce에 두 가지 L2 캐시 구현을 사용할 수 있습니다.

- 레거시 구현에서는 로컬 저장소에 `Cm_Cache_Backend_File`과(와) 함께 `RemoteSynchronizedCache`을(를) 사용합니다.
- 최신 구현에서는 PSR-6 준수 및 향상된 성능을 통해 `symfony_l2`을(를) 사용합니다. 최신 구현은 Valkey만 지원합니다.

| Commerce 버전 | Valkey가 있는 RemoteSynchronizedCache | 권장 구성 |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 및 이전 <br>(Valkey가 지원되는 경우) | 지원되는 기존 L2 경로 | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 이상 | 지원되지 않음 | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>Redis 캐시는 Adobe Commerce 2.4.9 또는 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 및 2.4.8-p4 이상의 패치 릴리스에서는 지원되지 않습니다. Redis가 지원되지 않는 캐시 구성에 Valkey를 사용합니다. 릴리스별로 지원되는 캐시 서비스에 대해서는 [시스템 요구 사항](/help/installation/system-requirements.md)을 참조하십시오.

>[!BEGINTABS]

>[!TAB Valkey 구성]

Valkey를 지원하는 Commerce 2.4.8 및 이전 버전에서 다음 구성을 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Commerce 2.4.9 이상에서는 [!DNL Symfony] L2 구현과 함께 다음 구성을 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Redis 구성]

Redis를 지원하는 버전 2.4.8 및 이전 Commerce 버전에서는 다음을 사용합니다.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

환경 구성에 대한 자세한 내용은 _Commerce on Cloud Infrastructure Guide_&#x200B;의 [`REDIS_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)을(를) 참조하십시오.

>[!ENDTABS]

### [!DNL Symfony] L2 캐시가 있는 Valkey로 마이그레이션

기존 클라우드 기반 Adobe Commerce 프로젝트를 `RemoteSynchronizedCache`(Redis 또는 Valkey)에서 `symfony_l2`(으)로 마이그레이션하는 경우 `.magento.env.yaml`을(를) 업데이트하기 전에 다음을 검토하십시오.

- **배포 변수를 변경하면 `symfony_l2`을(를) 사용할 수 있습니다.** `VALKEY_BACKEND: symfony_l2`만 설정하면 전체 L2 캐시 구성이 자동으로 빌드됩니다. 사용된 이전 `RemoteSynchronizedCache` 구성에 사용된 `backend_options` 구조를 수동으로 다시 만들 필요가 없습니다. [구성 [!DNL Symfony] L2 캐시](#configure-symfony-l2-cache)를 참조하십시오.

- **기존 구성에서 `preload_keys`을(를) 제거합니다.** `RemoteSynchronizedCache` 구성에 `CACHE_CONFIGURATION` 아래의 `preload_keys`이(가) 포함된 경우 마이그레이션의 일부로 제거하십시오. 자세한 내용은 [키 미리 로드](#preload-keys)를 참조하십시오.

- **오래된 캐시 동작이 자동으로 변경됩니다.** `symfony_l2`에서 `ece-tools`은(는) `RemoteSynchronizedCache`에 필요한 수동 프론트엔드 구성 없이 일반 캐시 형식(예: `layout`, `block_html`, `full_page` 및 `translate`)에 대해 오래된 캐시를 자동으로 활성화합니다. 이전에 부실 캐시를 수동으로 구성했으며 정확한 이전 동작을 유지하려면 마이그레이션하기 전에 [부실 캐시 활성화](#enable-stale-cache)를 검토하십시오.

- **압축에는 명시적 플래그가 필요합니다.** `CACHE_CONFIGURATION`을(를) 통해 `symfony_l2` 압축을 사용자 지정하는 경우 `compression_lib`만 설정하면 압축이 활성화되지 않습니다. `compress_data`도 설정해야 합니다. [캐시 압축](#cache-compression)을 참조하세요.

- **Redis는 `symfony_l2`에 대해 지원되는 원격 백엔드가 아닙니다.** 이 변경 사항의 일부로 Valkey로 마이그레이션합니다. [Valkey 서비스 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)을(를) 참조하십시오.

- **세션 구성은 이 마이그레이션의 영향을 받지 않습니다.** `SESSION_CONFIGURATION`은(는) 캐시 백엔드와 독립적이므로 `symfony_l2`(으)로 이동할 때 변경할 필요가 없습니다. [캐시와 세션 인스턴스 구분](#separate-cache-and-session-instances)을 참조하십시오.

>[!IMPORTANT]
>
>`app/etc/env.php`에서 `symfony_l2`을(를) 수동으로 구성하지 마십시오. 배포 중에 `ece-tools`이(가) 설정을 적용하고 유지할 수 있도록 `.magento.env.yaml`을(를) 통해 구성하십시오. [구성 [!DNL Symfony] L2 캐시](#configure-symfony-l2-cache)를 참조하십시오.

### 미리 로드 키

올바른 위치(`backend_options` 또는 `remote_backend_options` 아래)를 사용하는 경우 미리 로드 키를 `symfony_l2` 구성에 적용할 수 있습니다. 하지만 Adobe에서는 `symfony_l2`에 미리 로드 키를 사용하지 않는 것이 좋습니다. `symfony_l2` 미리 로드 구현은 키를 한 번에 하나씩 가져오므로 `RemoteSynchronizedCache`의 경우처럼 라운드 트립이 줄어들지 않으며 성능상의 이점 없이 Valkey의 로드를 늘릴 수 있습니다.

미리 로드 기능을 사용하면 Magento이 요청 중에 처음 액세스할 때 단일 파이프라인에서 가져오는 자주 사용하는 키 목록을 제공할 수 있습니다. 그런 다음 Magento은 가져온 값을 나머지 해당 요청에 대해 PHP 메모리에 유지하므로 Redis 또는 Valkey로의 반복된 라운드 트립이 줄어들고 해당 키에 대한 요청 부트스트랩 성능을 향상시킬 수 있습니다.

Redis 또는 Valkey에서 활성 명령을 모니터링하여 자주 사용되는 키를 식별할 수 있습니다.

미리 로드 키가 `.magento.env.yaml` 구성 파일에 구성되어 있습니다. 이 예는 `RemoteSynchronizedCache`을(를) 지원하는 Adobe Commerce 2.4.8 및 이전 버전에 대한 구성을 보여줍니다.

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

10초 후 **Ctrl+C**&#x200B;를 누릅니다. 그런 다음 다음 다음 명령을 실행합니다.

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

이 로그에는 미리 로드할 수 있는 키가 나열됩니다. 키의 내용을 보려면 다음 명령을 실행합니다.

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### 부실 캐시 활성화

부실 캐시는 다른 요청이 이미 동일한 항목을 다시 만드는 동안 Adobe Commerce에서 `/dev/shm`의 기존 로컬 캐시 값을 제공할 수 있는 L2 캐시 기능입니다. 이렇게 하면 동시 요청이 대기하지 않습니다. 이렇게 하면 값비싼 캐시 항목을 재생성하는 동안 캐시 스템피드 및 잠금 경합이 줄어듭니다.

Adobe Commerce 2.4.9 이상의 경우 `.magento.env.yaml` 파일에서 `VALKEY_BACKEND: symfony_l2`을(를) 설정합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools`은(는) `default` 프론트엔드와 `stale_cache_enabled` 프론트엔드를 모두 자동으로 생성하고, `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` 및 `translate` 캐시 형식을 부실 사용 프론트엔드에 매핑합니다. 이러한 형식에는 수동 `use_stale_cache` 또는 프론트엔드 구성이 필요하지 않습니다. 이러한 자동 매핑은 그 자체로 선택적 부실 캐시 활성화의 한 예입니다. 특정 캐시 유형만 부실 사용 프론트엔드를 사용하며 그 전부는 아닙니다. `stale_cache_enabled`에 매핑되는 형식을 사용자 지정하거나 기본값 이외의 형식을 추가하려면 [L2 캐시 구성 사용자 지정](#customize-the-symfony-l2-cache-configuration)을 참조하십시오. [!DNL Symfony] 

>[!NOTE]
>
>`full_page` 캐시 유형은 전체 페이지 캐싱에 Fastly를 사용하므로 클라우드 인프라 프로젝트의 Adobe Commerce과 관련이 없습니다. `ece-tools`에서 기본 `symfony_l2` 매핑에 수동 구성 예제에 `full_page`이(가) 포함되어 있어도 이 섹션의 수동 구성 예제에서는 이 때문에 이 예제를 생략합니다.

다음 레거시 구성은 `RemoteSynchronizedCache`을(를) 사용하고 수동 부실 캐시 및 프론트엔드 구성이 필요한 Adobe Commerce 2.4.8 이하에 적용됩니다. 여기에도 동일한 전역 중복 권장 사항이 적용됩니다.

#### 레거시 RemoteSynchronizedCache 백엔드의 작동 방식

`RemoteSynchronizedCache`을(를) 사용하면 Magento은 각 캐시 항목의 복사본 두 개를 유지 관리합니다. 하나는 `/dev/shm`에 로컬 복사본이고 다른 하나는 Redis 또는 Valkey에 원격 복사본입니다. 원격 복사본을 사용할 수 없고 해당 키에 대한 재생성 잠금이 이미 있는 경우, 동시 요청은 새 값이 기록될 때까지 기다리지 않고 이전 로컬 값을 수신할 수 있습니다.

2.4.8 및 이전 버전에 대해 오래된 캐시를 활성화하려면 `.magento.env.yaml` 파일에서 구성합니다.

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

>[!WARNING]
>
>위의 구성은 `default` 캐시 프런트 엔드에서 오래된 캐시를 활성화하며, 이로 인해 해당 프런트 엔드를 사용하는 모든 캐시 항목에 오래된 캐시 동작이 적용됩니다. Magento 코어 캐시 유형은 이 설정에서 예상대로 작동합니다. 그러나 프로젝트에 전용 캐시 프론트엔드 없이 일반 `\Magento\Framework\App\Cache` API(예: `$this->cache->save()`)를 통해 캐시에 쓰는 사용자 지정 코드 또는 확장이 포함되어 있는 경우 이러한 항목은 재생성 중에도 부실 값을 제공할 수 있습니다.
>
>
>이렇게 하면 사용자 지정에 예기치 않은 동작이 발생하는 경우 `default` 프런트 엔드에 오래된 캐시를 사용하지 않도록 설정한 후 아래 표시된 것처럼 선택한 캐시 유형에 대해서만 사용하도록 설정하십시오.

#### 캐시 유형별로 오래된 캐시 활성화(이전)

`.magento.env.yaml`에서 전용 캐시 프런트 엔드를 정의하고 선택한 캐시 유형을 매핑하여 선택한 캐시 유형에 대해서만 오래된 캐시를 활성화할 수 있습니다. 이 수동 접근 방식은 레거시 `RemoteSynchronizedCache` 백엔드에 적용됩니다. `symfony_l2`은(는) 위에서 설명한 대로 이 매핑을 자동으로 수행합니다.

올바르게 작동하려면 사용자 지정 프론트엔드를 `CACHE_CONFIGURATION.frontend`에서 전체 프론트엔드로 정의해야 합니다. 새 프론트엔드 이름에 대해 `use_stale_cache: true`만 정의하면 충분하지 않습니다.

**예제 구성**

버전 2.4.8 및 이전 버전의 Redis의 경우, 다음 구성은 `layout`, `reflection`, `config_integration`, `config_integration_api` 및 `translate` 캐시 유형에 대해 오래된 캐시를 활성화하고 다른 구성은 오래된 캐시가 비활성화된 기본 프런트 엔드를 사용합니다.

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

>[!NOTE]
>
>소스 프론트엔드가 추가 백엔드 옵션으로 구성된 경우, 새 프론트엔드가 동일한 동작을 유지하도록 해당 옵션을 `stale_cache_enabled`에 복사합니다.

### [!DNL Symfony] L2 캐시 구성

Adobe Commerce 2.4.9 이상 버전은 `symfony_l2` 캐시 백엔드를 지원합니다. `symfony_l2` 백엔드는 Adobe Commerce에서 L1 및 L2 캐시 동작을 관리하는 데 사용하는 캐시 구현입니다. **원격 캐시 서비스로 Redis 또는 Valkey를 대체하지 않습니다.**

>[!IMPORTANT]
>
>`ece-tools`이(가) 배포 중에 설정을 적용하고 유지 관리하도록 `.magento.env.yaml` 배포 변수를 통해 `symfony_l2`을(를) 구성하십시오. 배포가 수동 `env.php` 변경 내용을 덮어쓸 수 있으므로 `app/etc/env.php`에서 `symfony_l2`을(를) 수동으로 구성하지 마십시오. `ece-tools`이(가) `symfony_l2`을(를) 적용하지 않으면 Commerce이 파일 기반 캐시로 대체되어 디스크 I/O가 증가하고, 다중 노드 환경에서 파일 시스템 복제 오버헤드가 추가되며 성능이 저하될 수 있습니다.

Adobe Commerce 2.4.9용 `symfony_l2` 캐시를 사용하려면 다음 단계를 완료하십시오.

- 클라우드 프로젝트에서 [`ece-tools` 패키지 v2002.2.12](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) 이상을 사용하고 있는지 확인하십시오.

- `.magento.env.yaml` 파일에서 배포 변수를 설정합니다. `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

`VALKEY_BACKEND` 배포 변수를 `symfony_l2`(으)로 설정하면 `default` 및 `stale_cache_enabled` 프런트 엔드를 포함한 Valkey 서비스 연결 세부 정보에서 일반 캐시 형식이 이미 매핑된 전체 L2 캐시 구성이 자동으로 빌드됩니다. `CACHE_CONFIGURATION` 정의는 선택 사항이며 특정 백엔드 옵션을 사용자 지정하려는 경우에만 필요합니다.

>[!NOTE]
>
>Adobe Commerce 2.4.9용 패치 ACP2E-5132는 태그 저장소를 최적화하고 오래된 캐시 재생성 잠금을 추가하며 오래된 태그 멤버십, 중복 원격 쓰기 및 L1 크기 기반 제거(`cleanup_percentage`) 문제를 해결하여 [!DNL Symfony] L2 캐시 성능과 안정성을 개선합니다. 이를 통해 디스크 I/O 및 백엔드 로드를 줄이는 동시에 캐시 일관성을 향상시킬 수 있습니다. _Adobe Commerce 구성 가이드_&#x200B;에서 [향상된 Symfony L2 캐시 성능 및 안정성](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability)을(를) 참조하십시오.
>
>이 패치는 [Commerce용 클라우드 패치](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)&#x200B;(종속성: `ece-tools`)에 포함되어 있으며 최신 `ece-tools` 버전으로 업데이트할 때 배포 중에 자동으로 적용됩니다. 패치를 받으려면 `ece-tools`의 최신 버전으로 업데이트하십시오.

#### [!DNL Symfony] L2 캐시 구성 사용자 지정

`ece-tools`은(는) `default` 및 `stale_cache_enabled` 프런트 엔드에 대한 Valkey 연결 세부 정보(`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`)를 자동으로 파생합니다. 로컬 캐시 디렉터리와 같은 다른 백엔드 옵션을 사용자 지정하려면 `VALKEY_BACKEND: symfony_l2`과(와) 함께 `_merge: true`을(를) 사용하여 `CACHE_CONFIGURATION`을(를) 정의합니다. 여기서 정의하는 값은 자동 생성된 해당 기본값을 재정의합니다. 생략하는 모든 옵션은 `ece-tools`에서 자동으로 파생되는 값을 계속 사용합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>`symfony_l2`에 대해 `CACHE_CONFIGURATION`을(를) 정의할 때 프로젝트의 Valkey 서비스 이외의 캐시 끝점을 의도적으로 가리키고 있는 경우에만 `server` 또는 `port`을(를) 재정의하십시오. `ece-tools` 패키지는 Valkey 서비스 관계에서 이러한 값을 자동으로 파생합니다.
>
>`server`을(를) 재정의하는 경우 프로젝트의 Valkey 서비스에 연결할 때 해당 값은 `localhost`이어야 합니다. 잘못된 `server` 또는 `port` 값을 제공하면 캐시 연결 오류가 발생하여 배포가 실패합니다.

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

>[!TAB Valkey 구성]

Commerce 2.4.9 이상의 경우 다음 구성을 사용하여 정리 임계값을 90%로 설정합니다.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Redis 구성]

Commerce 2.4.8 및 이전 버전의 경우 다음 구성을 사용하여 정리 임계값을 90%로 설정합니다.

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

>[!ENDTABS]

캐시 요구 사항은 프로젝트 구성 및 사용자 지정 타사 코드에 따라 다릅니다. 캐시가 빈번한 임계값 히트 없이 작동할 수 있도록 L2 캐시 메모리의 크기를 지정합니다.

이상적으로 L2 캐시 메모리 사용은 빈번한 스토리지 지우기를 피하기 위해 임계값 아래에서 안정됩니다.

다음 CLI 명령을 실행하고 `/dev/shm` 줄을 검토하여 클러스터의 각 노드에서 L2 캐시 저장소 메모리 사용을 확인할 수 있습니다.

```shell
df -h /dev/shm
```

사용법은 노드에 따라 다르지만 비슷한 값으로 수렴합니다.

## 구성 예

다음 예를 Redis 또는 Valkey 서비스 구성의 시작점으로 사용하십시오.


### 모든 모범 사례 권장 사항 적용

>[!BEGINTABS]

>[!TAB Valkey 구성 예]

`VALKEY_BACKEND: symfony_l2`의 경우 `ece-tools`이(가) `default` 및 `stale_cache_enabled` 프런트 엔드와 해당 캐시 유형 매핑을 생성하게 합니다. 광범위한 `default` 프런트 엔드에서 `use_stale_cache`을(를) 설정하지 마십시오. 아래의 `CACHE_CONFIGURATION` 블록에는 명시적 백엔드 옵션 무시만 포함되어 있습니다.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB Redis 구성 예제]

Adobe Commerce 2.4.8 및 이전 버전의 Redis에 대해 다음 구성을 사용하십시오.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!ENDTABS]

### 캐시 유형별로 부실 캐시 구분

>[!BEGINTABS]

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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

>[!TAB 레디스]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
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

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [Valkey 서비스 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Redis 서비스 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [변수 배포](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
