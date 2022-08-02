---
title: 지원 유틸리티 실행
description: 기본 제공 지원 유틸리티를 사용하여 상거래 프로젝트 문제를 해결하십시오.
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# 지원 유틸리티 실행

{{ee-only}}

{{file-system-owner}}

Adobe Commerce 지원 유틸리티 - [데이터 수집기](https://docs.magento.com/user-guide/system/support-data-collector.html)—사용자가 지원 팀에서 사용할 수 있는 시스템에 대한 문제 해결 정보를 수집할 수 있습니다.

Adobe Commerce은 이러한 백업을 사용함(예: _덤프_&#x200B;를 사용하여 코드에 액세스해야 하는 문제를 분석할 수 있습니다. 일반적인 시나리오는 다음과 같습니다.

1. Commerce Store에 문제가 발생하여 Adobe Commerce 지원 센터에 문의하십시오.
1. 지원에서 문제를 재현하기 위해 코드 또는 데이터베이스를 봐야 한다고 판단합니다.
1. 코드를 `.tar.gz` 파일.

   이 백업은 미디어 파일을 제외하여 처리 속도를 높이고 파일 크기가 훨씬 작아집니다(_F).

1. 데이터베이스를 `.tar.gz` 파일.

   기본적으로 중요한 데이터는 백업을 만들 때 해시됩니다.

1. 파일 공유 서비스에 백업을 업로드합니다.
1. 지원 기능은 개발 또는 프로덕션 환경에 영향을 주지 않고 문제를 분석합니다.

유틸리티를 완료하는 데 몇 분이 걸릴 수 있습니다.

## 코드 백업 만들기

이 명령은 코드를 백업하고 압축합니다 `tar.gz` 형식 지정

{{tip-backup-command}}

명령 옵션:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

위치:

- **`--name`** 덤프 파일 이름을 지정합니다(선택 사항). 이 매개 변수를 생략하면 덤프 파일은 시간과 날짜 스탬프가 지정됩니다.
- **`-o|--output=<path>`** 은 백업을 저장할 절대 파일 시스템 경로입니다(필수).
- **`-l|--logs`** 로그 파일을 포함합니다(선택 사항).

예를 들어 이름이 인 코드 백업을 만들려면 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

명령이 완료되면 Adobe Commerce 지원에 코드 백업을 제공합니다.

## 데이터베이스 백업 만들기

이 명령은 상거래 데이터베이스를 백업하고 압축합니다 `tar.gz` 형식 지정

{{tip-backup-command}}

명령 옵션:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

위치:

- **`--name`** 덤프 파일 이름을 지정합니다(선택 사항). 이 매개 변수를 생략하면 덤프 파일은 시간과 날짜 스탬프가 지정됩니다.
- **`-o|--output=<path>` 은 백업을 저장할 절대 파일 시스템 경로입니다(필수).
- **`-l|--logs`** 로그 파일을 포함합니다(선택 사항).
- **`-i|--ignore-sanitize`** 는 데이터가 보존됨을 의미합니다. 백업을 만들 때 데이터베이스에 저장된 중요한 데이터를 해시하려면 플래그를 생략합니다(선택 사항).

중요한 데이터에는 다음 데이터베이스 테이블의 고객 정보가 포함됩니다.

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

명령이 완료되면 Adobe Commerce 지원에 데이터베이스 백업을 제공합니다.

## 문제 해결: 유틸리티 및 경로 표시

데이터 수집기 및 명령줄에 필요한 유틸리티로 경로를 표시하는 명령을 제공합니다. 예를 들어 관리자 또는 명령줄에서 다음과 같은 오류가 표시되는 경우 이러한 명령을 사용할 수 있습니다.

```terminal
Utility lsof not found
```

다음 명령을 표시된 순서대로 실행하여 지원 유틸리티 및 데이터 수집기에서 사용하는 응용 프로그램의 경로를 표시합니다.

1. 상거래 설치 디렉토리로 변경합니다.

   For example, `cd /var/www/magento2`

   >[!INFO]
   >
   >명령이 올바르게 실행됩니다 _전용_ 설치 디렉토리에서 다음을 수행합니다.

1. `bin/magento support:utility:paths` 만들기 `<magento_root>/var/support/Paths.php`: 유틸리티에서 사용하는 모든 애플리케이션에 대한 경로를 나열합니다.
1. `bin/magento support:utility:check` 파일 시스템 경로를 표시합니다.

샘플은

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

도구 실행 문제를 해결하려면 이러한 응용 프로그램이 설치되어 있고 웹 서버 사용자의 `$PATH` 환경 변수 입니다.
