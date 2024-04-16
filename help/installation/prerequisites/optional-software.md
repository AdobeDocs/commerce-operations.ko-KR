---
title: 옵션 소프트웨어
description: Adobe Commerce의 온프레미스 설치를 지원하기 위해 설치할 수 있는 선택적 소프트웨어에 대해 자세히 알아봅니다.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# 옵션 소프트웨어

cron 관련 작업이 제대로 수행되도록 NTP를 설치하는 것이 좋습니다. (예를 들어 서버 날짜는 과거 또는 미래일 수 있습니다.)

이 항목에서 설명하는 다른 선택적 유틸리티는 설치에 도움이 될 수 있지만 Adobe Commerce 또는 Magento Open Source을 설치하거나 사용할 필요는 없습니다.

## NTP(Network Time Protocol) 설치 및 구성

[NTP](https://www.ntp.org/) 를 사용하여 서버가 시스템 시계를 동기화할 수 있습니다. [전체적으로 사용 가능한 풀 서버](https://www.ntppool.org/en/). 신뢰할 수 있는 NTP 서버는 내부 네트워크나 외부 공용 서버에 대한 전용 하드웨어 솔루션이든 관계없이 사용하는 것이 좋습니다.

여러 호스트에 Adobe Commerce 또는 Magento Open Source을 배포하는 경우 NTP를 사용하면 서버가 있는 시간대에 관계 없이 시계가 모두 동기화됩니다. 또한 서버 시계가 정확하기 때문에 cron 관련 작업(예: 인덱싱 및 트랜잭션 이메일)이 정확합니다.

### Ubuntu에서 NTP 설치 및 구성

NTP를 설치하려면 다음 명령을 입력합니다.

```bash
apt-get install ntp
```

계속 [NTP 풀 서버 사용](#use-ntp-pool-servers).

### CentOS에서 NTP 설치 및 구성

NTP를 설치하고 구성하려면 다음을 수행하십시오.

1. 다음 명령을 입력하여 적절한 NTP 소프트웨어를 찾습니다.

   ```bash
   yum search ntp
   ```

1. 설치할 패키지를 선택하십시오. 예를 들어, `ntp.x86_64`.

1. 패키지를 설치합니다.

   ```bash
   yum -y install ntp.x86_64
   ```

1. 서버가 시작될 때 NTP가 시작되도록 다음 명령을 입력합니다.

   ```bash
   chkconfig ntpd on
   ```

1. 다음 섹션을 계속합니다.

### NTP 풀 서버 사용

풀 서버 선택은 사용자가 결정합니다. NTP 풀 서버를 사용하는 경우 ntp.org 를 사용하는 것이 좋습니다. [풀 서버](https://www.ntppool.org/en/) 에 설명된 대로 서버의 시간대에 가깝습니다. [NTP 풀 프로젝트 페이지](https://www.ntppool.org/en/use.html). 배포의 모든 호스트에서 사용할 수 있는 개인 NTP 서버가 있는 경우 해당 서버를 대신 사용할 수 있습니다.

1. 열기 `/etc/ntp.conf` 텍스트 편집기에서.

1. 다음과 유사한 행을 찾습니다.

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 해당 줄을 교체하거나 NTP 풀 서버 또는 다른 NTP 서버를 지정하는 줄을 추가합니다. 두 개 이상을 지정하는 것이 좋습니다.

1. 미국 내 3개의 NTP 서버를 사용하는 예는 다음과 같습니다.

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 변경 내용 저장 `/etc/ntp.conf` 텍스트 편집기를 종료합니다.

1. 서비스를 다시 시작합니다.

   * 우분투: `service ntp restart`

   * CentOS: `service ntpd restart`

1. 입력 `date` 서버의 날짜를 확인합니다.

   날짜가 올바르지 않으면 방화벽에서 NTP 클라이언트 포트(일반적으로 UDP 123)가 열려 있는지 확인하십시오.

   다음을 시도해 보십시오. `ntpdate _[pool server hostname]_` 명령입니다. 실패하면 반환되는 오류를 검색합니다.

   다른 작업이 모두 실패하면 서버를 재부팅해 보십시오.

## phpinfo.php 만들기

다음 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 파일에는 PHP와 그 확장자에 대한 많은 정보가 표시됩니다.

>[!NOTE]
>
>사용 `phpinfo.php` 개발 시스템에서 _전용_. 프로덕션에서 보안 문제가 될 수 있습니다.

웹 서버의 docroot에 다음 코드를 추가합니다.

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

자세한 내용은 [phpinfo 수동 페이지](https://www.php.net/manual/en/function.phpinfo.php).

결과를 보려면 브라우저의 위치 또는 주소 필드에 다음 URL을 입력합니다.

```http
http://<web server host or IP>/phpinfo.php
```

404(찾을 수 없음) 오류가 표시되면 다음을 확인하십시오.

* 필요한 경우 웹 서버를 시작합니다.
* 방화벽이 포트 80에서 트래픽을 허용하는지 확인하십시오.

  [Ubuntu 도움말](https://help.ubuntu.com/community/UFW)

  [CentOS용 도움말](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

phpMyAdmin 응용 프로그램은 사용하기 쉬운 무료 데이터베이스 관리 유틸리티입니다. 이 옵션을 사용하여 데이터베이스의 내용을 확인하고 조작할 수 있습니다. phpMyAdmin에 MySQL 데이터베이스 관리 사용자로 로그인해야 합니다.

phpMyAdmin에 대한 자세한 내용은 [phpMyAdmin 홈 페이지](https://www.phpmyadmin.net/).

설치에 대한 자세한 내용은 [phpMyAdmin 설치 설명서](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>개발 시스템에서 phpMyAdmin 사용 _전용_. 프로덕션에서 보안 문제가 될 수 있습니다.

1. phpMyAdmin을 사용하려면 브라우저의 주소 또는 위치 필드에 다음 명령을 입력합니다.

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 메시지가 표시되면 MySQL 데이터베이스를 사용하여 로그인합니다. `root` 또는 관리 사용자의 사용자 이름과 암호를 입력합니다.
