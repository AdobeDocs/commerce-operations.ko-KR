---
title: 세션 저장소에 Redis 사용
description: 세션 저장소에 대한 Redis 구성 방법을 알아봅니다.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 세션 저장소에 Redis 사용

>[!IMPORTANT]
>
>다음을 수행해야 합니다. [Redis 설치](config-redis.md#install-redis) 계속하기 전에


이제 Commerce에서 Redis 세션 저장소를 구성하는 명령줄 옵션을 제공합니다. 이전 릴리스에서는 `<Commerce install dir>app/etc/env.php` 파일. 명령줄에서 유효성 검사를 제공하고 권장 구성 방법이지만 `env.php` 파일.

를 실행합니다. `setup:config:set` 명령을 실행하고 Redis 특정 매개 변수를 지정합니다.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

여기서

`--session-save=redis` Redis 세션 저장소를 사용합니다. 이 기능을 이미 활성화한 경우에는 이 매개 변수를 생략하십시오.

`--session-save-redis-<parameter_name>=<parameter_value>` 세션 저장소를 구성하는 매개 변수/값 쌍 목록입니다.

| 명령줄 매개 변수 | 매개 변수 이름 | 의미 | 기본값 |
|--- |--- |--- |--- |
| session-save-redis-host | 호스트 | UNIX 소켓을 사용하는 경우 정규화된 호스트 이름, IP 주소 또는 절대 경로입니다. | localhost |
| session-save-redis-port | 포트 | Redis 서버 수신 포트입니다. | 6379년 |
| session-save-redis-password | 암호 | Redis 서버에 인증이 필요한 경우 암호를 지정합니다. | 비어 있음 |
| session-save-redis-timeout | timeout | 연결 시간 초과(초)입니다. | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 영구 연결을 활성화하는 고유한 문자열(예: sess-db0).<br>[phpredis 및 php-fpm의 알려진 문제](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | 데이터베이스 | 고유 Redis 데이터베이스 번호입니다. 이 번호는 데이터 손실로부터 보호하는 것이 좋습니다.<br><br>**중요 사항**: 두 개 이상의 캐싱 유형에 Redis를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호를 0에, 페이지 캐싱 데이터베이스 번호는 1에, 세션 저장소 데이터베이스 번호는 2에 지정하는 것이 좋습니다. | 0 |
| session-save-redis-compression-threshold | compression_threshold | 압축을 비활성화하려면 0으로 설정합니다(권장할 경우). `suhosin.session.encrypt = On`).<br>[64KB 이상의 문자열에 대해 알려진 문제](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048년 |
| session-save-redis-compression-lib | compression_library | 옵션: gzip, lzf, lz4 또는 snappy. | gzip |
| session-save-redis-log-level | log_level | 최소 세부 정보에서 가장 자세한 정보까지 순서대로 나열된 다음 중 하나로 설정합니다.<ul><li>0(긴급: 가장 심각한 오류만)<li>1(경고: 즉각적인 조치 필요)<li>2(중요: 애플리케이션 구성 요소를 사용할 수 없음)<li>3 (오류: 런타임 오류(심각하지 않지만 모니터링해야 함)<li>4(경고: 추가 정보, 권장)<li>5(통지: 일반적이지만 중요한 조건<li>6(정보: 정보 메시지)<li>7(디버그: 개발 또는 테스트에만 가장 많은 정보)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 한 세션의 잠금을 기다릴 수 있는 최대 프로세스 수입니다. 대규모 프로덕션 클러스터의 경우 PHP 프로세스 수의 10% 이상으로 설정합니다. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | 프런트 엔드(즉, storfront) 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)입니다. | 5개 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | 관리자(즉, 관리자) 세션에 대한 잠금을 해제하기 전에 대기하는 시간(초)입니다. | 30 |
| session-save-redis-first-lifetime | first_lifetime | 첫 번째 쓰기 시 보트가 아닌 세션에 대한 라이프타임(초)이나 0을 사용하여 비활성화할 수 있습니다. | 600년 |
| session-save-redis-bot-first-lifetime | bots_first_lifetime | 첫 번째 쓰기 시 봇에 대한 세션의 라이프타임(초) 또는 0을 사용하여 을 비활성화하십시오. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 이후 쓰기 시 봇에 대한 세션의 라이프타임(초) 또는 0을 사용하여 을 비활성화하십시오. | 7200년 |
| session-save-redis-disable-locking | disable_locking | 세션 잠금을 완전히 비활성화합니다. | 0(false) |
| session-save-redis-min-lifetime | min_lifetime | 최소 세션 수명(초). | 60 |
| session-save-redis-max-lifetime | max_lifetime | 최대 세션 수명(초). | 2592000 (720시간) |
| session-save-redis-sentinel-master | sentel_master | 레디스 센티넬 마스터 이름 | 비어 있음 |
| session-save-redis-sentinel-servers | sentel_servers | Redis Sentinel 서버 목록, 쉼표로 구분됨 | 비어 있음 |
| session-save-redis-sentinel-verify-master | sentel_verify_master | Redis Sentinel 마스터 상태 플래그 확인 | 0(false) |
| session-save-redis-sentinel-connect-retries | sentel_connect_retries | 센티널에 대한 연결 다시 시도 | 5개 |

## 예

다음 예제에서는 Redis를 세션 데이터 저장소로 설정하고 호스트를 로 설정합니다. `127.0.0.1`를 사용하여 로그 레벨을 4로 설정하고 데이터베이스 번호를 2로 설정합니다. 다른 모든 매개 변수는 기본값으로 설정됩니다.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 결과

상거래에 다음과 유사한 라인이 추가됩니다. `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>세션 레코드의 TTL은 관리자에게 구성된 쿠키 라이프타임 값을 사용합니다. 쿠키 라이프타임이 0으로 설정된 경우(기본값은 3600) Redis 세션은 min_lifetime에 지정된 초 수(기본값 60)로 만료됩니다. 이러한 불일치는 Redis 및 세션 쿠키가 라이프타임 값 0을 해석하는 방식의 차이로 인한 것입니다. 해당 동작을 원하지 않는 경우 min_lifetime 값을 늘립니다.

## Redis 연결 확인

Redis와 Commerce가 함께 작동하는지 확인하려면 Redis를 실행하는 서버에 로그인하고 터미널을 열고 Redis 모니터 명령 또는 ping 명령을 사용합니다.

### Redis monitor 명령

```bash
redis-cli monitor
```

샘플 세션 저장소 출력:

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping 명령

```bash
redis-cli ping
```

`PONG` 은 응답이어야 합니다.

두 명령이 모두 성공하면 Redis가 올바르게 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터 및 페이지 캐시를 검사하려면 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) 에서는 Commerce 2 Session 및 Page 캐시의 자동 압축 해제를 지원하고 사용자가 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.

