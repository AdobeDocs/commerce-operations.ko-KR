---
title: 로깅 활성화
description: Adobe Commerce에서 다양한 유형의 로깅을 활성화하고 비활성화하는 방법에 대해 알아봅니다. 로깅 구성 및 관리 기술을 살펴봅니다.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 로깅 활성화

{{file-system-owner}}

## 디버그 로깅

기본적으로 Commerce은 디버그 로그(`<install_directory>/var/log/debug.log`)가 기본 모드이거나 개발 모드일 때는 기록하지만 프로덕션 모드일 때는 기록하지 않습니다. `bin/magento setup:config:set --enable-debug-logging` 명령을 사용하여 기본값을 변경합니다.

>[!INFO]
>
>Commerce 2.3.1부터는 `bin/magento config:set dev/debug/debug_logging` 명령을 사용하여 현재 모드에 대한 디버그 로깅을 활성화하거나 비활성화할 수 없습니다.

### 디버그 로깅을 활성화하려면

1. `setup:config:set` 명령을 사용하여 현재 모드에 대한 디버그 로깅을 사용하도록 설정합니다.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### 디버그 로깅을 비활성화하려면

1. 현재 모드에 대한 디버그 로깅을 비활성화하려면 `setup:config:set` 명령을 사용하십시오.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

## 데이터베이스 로깅

기본적으로 Commerce은 `<install-dir>/var/debug/db.log` 파일에 데이터베이스 활동 로그를 기록합니다.

### 쿼리 로깅 저장소 위치

데이터베이스 로깅이 활성화되면 Commerce은 다음 위치에 쿼리 로그를 저장합니다.

- **쿼리 로그 파일**: `<install-directory>/var/debug/db.log`
- **로그 디렉터리**: `<install-directory>/var/debug/`

쿼리 로그에는 다음이 포함됩니다.
- 응용 프로그램에서 실행되는 SQL 쿼리
- 쿼리 실행 시간
- 쿼리 매개 변수 및 바인딩
- 데이터베이스 연결 정보

>[!NOTE]
>
>쿼리 로그 파일은 트래픽이 많은 환경에서 빠르게 커질 수 있습니다. 디스크 공간을 모니터링하고 로그 순환 또는 쿼리 로그 파일의 주기적 정리를 구현하는 것이 좋습니다.

### 데이터베이스 로깅을 사용하려면

1. `dev:query-log` 명령을 사용하여 데이터베이스 로깅을 활성화하거나 비활성화합니다.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### 쿼리 로그를 보려면

표준 파일 보기 명령을 사용하여 쿼리 로그를 볼 수 있습니다.

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Cron 로깅

버전 2.3.1이 출시되면서 Commerce은 이제 별도의 `cron` 로그를 만듭니다. \
Commerce은 최근 크론 로깅을 더 자세히 만들어 더 많은 정보를 제공했지만 `system.log`이(가) 상당히 길어졌습니다.
`cron` 정보를 전용 로그로 이동하면 두 로그를 더 쉽게 읽을 수 있습니다.

기본적으로 Commerce은 `cron` 파일에 `<install-directory>/var/log/cron.log` 정보를 기록합니다.

## Syslog 로깅

기본적으로 Commerce은 운영 체제 _파일에_ syslog`syslog` 로그를 기록합니다.
Commerce 2.3.1부터는 `magento` 명령을 사용하여 syslog를 활성화하거나 비활성화해야 합니다.
관리자의 설정이 제거되었습니다.

### syslog 로깅을 활성화하려면

기본적으로 `syslog`에 로그인할 수 없습니다.

1. `setup:config:set` 명령을 사용하여 `dev/syslog/syslog_logging` 데이터베이스 값을 `true`(으)로 변경합니다.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### syslog 로깅을 비활성화하려면

1. `setup:config:set` 명령을 사용하여 `dev/syslog/syslog_logging` 데이터베이스 값을 `false`(으)로 변경합니다.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```
