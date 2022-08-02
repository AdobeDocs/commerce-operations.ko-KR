---
title: 로깅 활성화
description: 로깅 유형을 활성화 및 비활성화하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 로깅 활성화

{{file-system-owner}}

## 디버그 로깅

기본적으로 Commerce는 디버그 로그(`<install_directory>/var/log/debug.log`) 기본 모드이거나 개발 모드일 때 사용할 수 있지만 프로덕션 모드일 때는 사용할 수 없습니다. 를 사용하십시오 `bin/magento setup:config:set --enable-debug-logging` 기본값을 변경하는 명령입니다.

>[!INFO]
>
>Commerce 2.3.1부터 이제 `bin/magento config:set dev/debug/debug_logging` 현재 모드에 대한 디버그 로깅을 활성화하거나 비활성화하는 명령입니다.

### 디버그 로깅을 사용하려면

1. 를 사용하십시오 `setup:config:set` 현재 모드에 대한 디버그 로깅을 사용하도록 설정하는 명령입니다.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### 디버그 로깅을 비활성화하려면

1. 를 사용하십시오 `setup:config:set` 현재 모드에 대한 디버그 로깅을 사용하지 않도록 설정하는 명령입니다.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

## 데이터베이스 로깅

기본적으로 Commerce는 데이터베이스에 데이터베이스 활동 로그를 기록합니다 `<install-dir>/var/debug/db.log` 파일.

### 데이터베이스 로깅을 사용하려면

1. 를 사용하십시오 `dev:query-log` 데이터베이스 로깅을 활성화하거나 비활성화하는 명령

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

## 로그온

버전 2.3.1의 릴리스를 사용하면 이제 Commerce에서 별도의 를 만듭니다 `cron` 로그. \
최근에 상거래에 더 자세한 정보를 기록하는 크론이 생성되었으며, 이에 따라 더 많은 정보가 제공되었지만 `system.log` 상당히.
이동 `cron` 전용 로그에 대한 정보를 사용하면 두 로그를 보다 쉽게 읽을 수 있습니다.

기본적으로 상거래 쓰기 `cron` 정보 `<install-directory>/var/log/cron.log` 파일.

## Syslog 로깅

기본적으로 상거래 쓰기 _syslog_ 운영 체제에 로그 `syslog` 파일.
Commerce 2.3.1부터 `magento` syslog를 활성화하거나 비활성화하는 명령
관리자의 설정이 제거되었습니다.

### syslog 로깅을 사용하려면

에 로그인하는 중 `syslog` 은 기본적으로 비활성화되어 있습니다.

1. 를 사용하십시오 `setup:config:set` 명령 변경 `dev/syslog/syslog_logging` 데이터베이스 값 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### syslog 로깅을 비활성화하려면

1. 를 사용하십시오 `setup:config:set` 명령 변경 `dev/syslog/syslog_logging` 데이터베이스 값 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```
