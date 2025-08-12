---
title: 세션 저장소에 Valkey 사용
description: 세션 저장소에 대한 Valkey를 구성하는 방법에 대해 알아봅니다.
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: bc0274074c0254f649af2f9e2b288017ac82ce9b
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---


# 세션 저장소에 Valkey 사용

>[!IMPORTANT]
>
>계속하려면 [Valkey를 설치](config-valkey.md#install-valkey)해야 합니다.

Adobe Commerce은 Valkey 세션 저장소를 구성하는 명령줄 옵션을 제공합니다.

`setup:config:set` 명령을 실행하고 Valkey 관련 매개 변수를 지정합니다.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey`이(가) Valkey 세션 저장소를 사용하도록 설정합니다. 이 기능이 이미 활성화되어 있으면 이 매개변수를 생략합니다.

- `--session-save-valkey-<parameter_name>=<parameter_value>`은(는) 세션 저장소를 구성하는 매개 변수/값 쌍의 목록입니다.

| 명령줄 매개 변수 | 매개 변수 이름 | 의미 | 기본값 |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | 호스트 | UNIX 소켓을 사용하는 경우 정규화된 호스트 이름, IP 주소 또는 절대 경로입니다. | localhost |
| session-save-valkey-port | 포트 | 유효한 서버 수신 포트입니다. | 6379 |
| session-save-valkey-password | 암호 | Valkey 서버에 인증이 필요한 경우 암호를 지정합니다. | 비어 있음 |
| session-save-valkey-timeout | timeout | 연결 시간 제한(초)입니다. | 2.5 |
| session-save-valkey-persistent-id | persistent_identifier | 영구 연결을 활성화하는 고유 문자열(예: sess-db0).<br>[phpredis 및 php-fpm과 관련된 알려진 문제](https://github.com/phpredis/phpredis/issues/70). |
| session-save-valkey-db | 데이터베이스 | 데이터 손실을 방지하는 데 권장되는 고유한 Valkey 데이터베이스 번호입니다.<br><br>**중요**: 두 개 이상의 캐싱 형식에 Valkey를 사용하는 경우 데이터베이스 번호가 달라야 합니다. 기본 캐싱 데이터베이스 번호를 `0`에, 페이지 캐싱 데이터베이스 번호를 `1`에, 세션 저장소 데이터베이스 번호를 `2`에 할당하는 것이 좋습니다. | 0 |
| session-save-valkey-compression-threshold | compression_threshold | 압축을 비활성화하려면 `0`(으)로 설정합니다(`suhosin.session.encrypt = On`일 때 권장됨). | 2048 |
| session-save-valkey-compression-lib | compression_library | 옵션: gzip, lzf, lz4 또는 snappy. | gzip |
| session-save-valkey-log-level | log_level | 세부 정보(verbose)부터 세부 정보(verbose)까지 순서대로 나열되는 다음 중 하나로 설정합니다.<ul><li>0(긴급: 가장 심각한 오류만)<li>1(경고: 즉각적인 조치 필요)<li>2 (중요: 애플리케이션 구성 요소를 사용할 수 없음)<li>3 (오류: 런타임 오류, 중요하지 않지만 모니터링해야 함)<li>4(경고: 추가 정보, 권장)<li>5(알림: 정상이지만 중대한 상태)<li>6 (정보: 정보 메시지)<li>7(디버그: 개발 또는 테스트용으로만 사용되는 가장 많은 정보)</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | 한 세션에 대한 잠금을 기다릴 수 있는 최대 프로세스 수. 대규모 생산 클러스터의 경우 이를 PHP 프로세스 수의 10% 이상으로 설정합니다. | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | 프론트엔드(즉, storefront) 세션에 대한 잠금을 해제하기 전에 대기할 시간(초)입니다. | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | adminhtml(즉, Admin) 세션의 잠금을 해제하기 전에 대기하는 시간(초)입니다. | 30 |
| session-save-valkey-first-lifetime | first_lifetime | 첫 번째 쓰기에서 봇이 아닌 세션의 수명(초)이거나 `0`을(를) 사용하여 사용하지 않도록 설정하십시오. | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | 첫 번째 쓰기 시 봇에 대한 세션 수명(초)이거나 `0`을(를) 사용하여 사용하지 않도록 설정하십시오. | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | 후속 쓰기 시 봇에 대한 세션 수명(초)이거나 `0`을(를) 사용하여 사용하지 않도록 설정하십시오. | 7200 |
| session-save-valkey-disable-locking | disable_locking | 세션 잠금을 완전히 비활성화합니다. | 0(false) |
| session-save-valkey-min-lifetime | min_lifetime | 최소 세션 수명(초)입니다. | 60 |
| session-save-valkey-max-lifetime | max_lifetime | 최대 세션 수명(초)입니다. | 2592000(720시간) |
| session-save-valkey-sentinel-master | sentinel_master | 유효성 검사 마스터 이름입니다. | 비어 있음 |
| session-save-valkey-sentinel-server | sentinel_servers | Valkey Sentinel 서버 목록(쉼표로 구분됨). | 비어 있음 |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Valkey Sentinel 마스터 상태 플래그를 확인합니다. | 0(false) |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | 센티널에 대한 연결 재시도. | 5 |

## 예

다음 예제에서는 Valkey를 세션 데이터 저장소로 설정하고 호스트를 `127.0.0.1`(으)로 설정하고 로그 수준을 `4`(으)로 설정하고 데이터베이스 번호를 `2`(으)로 설정합니다. 다른 모든 매개변수는 기본값으로 설정됩니다.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### 결과

Commerce이 `<magento_root>app/etc/env.php`에 다음과 유사한 줄을 추가합니다.

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>세션 레코드에 대한 TTL은 관리자에 구성된 쿠키 수명 값을 사용합니다. 쿠키 수명이 `0`(기본값: `3600`)로 설정된 경우 Valkey 세션은 min_lifetime에 지정된 초 수(기본값: `60`)로 만료됩니다. 이러한 불일치는 Valkey 및 세션 쿠키가 `0`의 라이프타임 값을 해석하는 방식의 차이로 인해 발생합니다. 해당 비헤이비어를 원하지 않는 경우 min_lifetime 값을 늘립니다.

## Valkey 연결 확인

Valkey와 Commerce이 제대로 작동하는지 확인하려면 Valkey가 실행 중인 서버에 로그인하고 터미널을 열고 `valkey-cli monitor` 명령 또는 `redis-cli ping` 명령을 사용합니다.

### Valkey monitor 명령

```bash
valkey-cli monitor
```

샘플 세션-스토리지 출력:

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Valkey ping 명령

```bash
valkey-cli ping
```

필요한 응답은 `PONG`입니다.

두 명령이 모두 성공하면 Valkey가 제대로 설정됩니다.

### 압축된 데이터 검사

압축된 세션 데이터와 페이지 캐시를 검사하기 위해 [RESP.app](https://flathub.org/apps/app.resp.RESP)은(는) Commerce 2 세션 및 페이지 캐시의 자동 압축 해제를 지원하고 사람이 읽을 수 있는 형식으로 PHP 세션 데이터를 표시합니다.
