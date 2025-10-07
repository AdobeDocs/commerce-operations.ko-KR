---
title: 로깅 활성화
description: Adobe Commerce에서 다양한 유형의 로깅을 활성화하고 비활성화하는 방법에 대해 알아봅니다. 로깅 구성 및 관리 기술을 살펴봅니다.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '268'
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
