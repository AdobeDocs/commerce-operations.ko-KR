---
title: 지원 유틸리티 실행
description: 지원 유틸리티를 실행하여 Adobe Commerce 프로젝트 문제를 해결하는 방법을 알아봅니다. 내장된 진단 및 지원 도구를 살펴보십시오.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# 지원 유틸리티 실행

{{ee-only}}

{{file-system-owner}}

Adobe Commerce 지원 유틸리티([데이터 수집기](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/support#data-collector))를 사용하면 사용자가 지원 팀에서 사용할 수 있는 시스템에 대한 문제 해결 정보를 수집할 수 있습니다.

Adobe Commerce은 이러한 백업을 사용하여 코드에 액세스해야 하는 문제를 분석합니다. _덤프_&#x200B;라고도 합니다. 일반적인 시나리오는 다음과 같습니다.

1. Commerce 스토어에 문제가 있으므로 Adobe Commerce 지원 센터에 문의하십시오.
1. 지원 팀은 문제를 재현하기 위해 코드 또는 데이터베이스를 확인해야 한다고 판단합니다.
1. `.tar.gz` 파일에 코드를 백업합니다.

   이 백업은 프로세스 속도를 높이고 파일이 훨씬 작아지도록 미디어 파일을 제외합니다(_R).

1. 데이터베이스를 `.tar.gz` 파일로 백업합니다.

   기본적으로 중요한 데이터는 백업을 만들 때 해시됩니다.

1. 백업을 파일 공유 서비스에 업로드합니다.
1. 지원은 개발 또는 프로덕션 환경에 영향을 주지 않고 문제를 분석합니다.

유틸리티가 완료되는 데 몇 분 정도 걸릴 수 있습니다.

## 코드 백업 만들기

이 명령은 코드를 백업하고 `tar.gz` 형식으로 압축합니다.

{{tip-backup-command}}

명령 옵션:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

위치:

- **`--name`**&#x200B;이(가) 덤프 파일 이름을 지정합니다(선택 사항). 이 매개 변수를 생략하면 덤프 파일에 타임스탬프가 지정됩니다.
- **`-o|--output=<path>`**&#x200B;은(는) 백업을 저장할 절대 파일 시스템 경로입니다(필수).
- **`-l|--logs`**&#x200B;에 로그 파일이 포함되어 있습니다(선택 사항).

예를 들어, 이름이 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`인 코드 백업을 만들려면 다음을 수행하십시오.

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

명령이 완료되면 Adobe Commerce 지원에 코드 백업을 제공합니다.

## 데이터베이스 백업 만들기

이 명령은 Commerce 데이터베이스를 백업하고 `tar.gz` 형식으로 압축합니다.

{{tip-backup-command}}

명령 옵션:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

위치:

- **`--name`**&#x200B;이(가) 덤프 파일 이름을 지정합니다(선택 사항). 이 매개 변수를 생략하면 덤프 파일에 타임스탬프가 지정됩니다.
- **`-o|--output=<path>`은(는) 백업을 저장할 절대 파일 시스템 경로입니다(필수).
- **`-l|--logs`**&#x200B;에 로그 파일이 포함되어 있습니다(선택 사항).
- **`-i|--ignore-sanitize`**&#x200B;은(는) 데이터가 보존됨을 의미합니다. 백업을 만들 때 데이터베이스에 저장된 중요한 데이터를 해시하려면 플래그를 생략하십시오(선택 사항).

중요한 데이터에는 다음 데이터베이스 테이블의 고객 정보가 포함됩니다.

```
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

## 문제 해결: 디스플레이 유틸리티 및 경로

데이터 수집기와 명령줄에 필요한 유틸리티의 경로를 표시하는 명령을 제공합니다. 예를 들어 다음과 같은 오류가 관리자 또는 명령줄에 표시되는 경우 이러한 명령을 사용할 수 있습니다.

```
Utility lsof not found
```

다음 명령을 표시된 순서대로 실행하여 지원 유틸리티 및 데이터 수집기에서 사용하는 응용 프로그램에 대한 경로를 표시합니다.

1. Commerce 설치 디렉토리로 변경합니다.

   For example, `cd /var/www/magento2`

   >[!INFO]
   >
   >명령은 설치 디렉터리에서 _only_ 올바르게 실행됩니다.

1. `bin/magento support:utility:paths`은(는) 유틸리티에서 사용하는 모든 응용 프로그램의 경로를 나열하는 `<magento_root>/var/support/Paths.php`을(를) 만듭니다.
1. `bin/magento support:utility:check`에 파일 시스템 경로가 표시됩니다.

샘플은 다음과 같습니다.

```
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

도구 실행 문제를 해결하려면 이러한 응용 프로그램이 설치되어 있고 웹 서버 사용자의 `$PATH` 환경 변수에 있는지 확인하십시오.
