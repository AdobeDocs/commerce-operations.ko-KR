---
title: 로깅 활성화
description: 로깅 유형을 활성화하고 비활성화하는 방법에 대해 알아봅니다.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 로깅 활성화

{{file-system-owner}}

## 디버그 로깅

기본적으로 Commerce는 디버그 로그에 씁니다(`<install_directory>/var/log/debug.log`)가 기본 모드나 개발 모드일 때는 표시되고 프로덕션 모드일 때는 표시되지 않습니다. 사용 `bin/magento setup:config:set --enable-debug-logging` 기본값을 변경하는 명령입니다.

>[!INFO]
>
>Commerce 2.3.1부터는 를 더 이상 사용할 수 없습니다. `bin/magento config:set dev/debug/debug_logging` 현재 모드에 대한 디버그 로깅을 활성화하거나 비활성화하는 명령입니다.

### 디버그 로깅을 활성화하려면

1. 사용 `setup:config:set` 현재 모드에 대한 디버그 로깅을 활성화하는 명령입니다.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### 디버그 로깅을 비활성화하려면

1. 사용 `setup:config:set` 현재 모드에 대한 디버그 로깅을 비활성화하는 명령입니다.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

## 데이터베이스 로깅

기본적으로 Commerce는 데이터베이스 작업 로그를 `<install-dir>/var/debug/db.log` 파일.

### 데이터베이스 로깅을 사용하려면

1. 사용 `dev:query-log` 데이터베이스 로깅을 활성화하거나 비활성화하는 명령입니다.

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

## Cron 로깅

버전 2.3.1이 출시되면서 Commerce는 이제 별도의 버전을 만듭니다 `cron` 로그합니다. \
최근 Commerce에서는 크론 로깅이 더 자세한 정보를 제공하면서도 시간을 늘렸습니다. `system.log` 상당히.
이동 `cron` 전용 로그에 대한 정보를 사용하면 두 로그를 보다 쉽게 읽을 수 있습니다.

기본적으로 Commerce 는 `cron` 에 대한 정보 `<install-directory>/var/log/cron.log` 파일.

## Syslog 로깅

기본적으로 Commerce 는 _syslog_ 운영 체제에 대한 로그 `syslog` 파일.
Commerce 2.3.1부터는 `magento` syslog를 활성화 또는 비활성화하는 명령입니다.
관리자의 설정이 제거되었습니다.

### syslog 로깅을 활성화하려면

에 로깅 `syslog` 은 기본적으로 비활성화되어 있습니다.

1. 사용 `setup:config:set` 를 변경하는 명령 `dev/syslog/syslog_logging` 데이터베이스 값: 까지 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```

### syslog 로깅을 비활성화하려면

1. 사용 `setup:config:set` 를 변경하는 명령 `dev/syslog/syslog_logging` 데이터베이스 값: 까지 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 캐시를 플러시합니다.

   ```bash
   bin/magento cache:flush
   ```
