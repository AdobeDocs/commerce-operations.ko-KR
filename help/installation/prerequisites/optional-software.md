---
title: 소프트웨어 옵션
description: Adobe Commerce 및 Magento Open Source의 온프레미스 설치를 지원하기 위해 설치할 수 있는 선택적 소프트웨어에 대해 자세히 알아보십시오.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# 소프트웨어 옵션

크론 관련 작업이 제대로 수행되도록 NTP를 설치하는 것이 좋습니다. (예를 들어 서버 날짜는 과거 또는 이후일 수 있습니다.)

이 주제에서 설명한 다른 선택적 유틸리티는 설치를 지원할 수 있습니다. 그러나 Adobe Commerce 또는 Magento Open Source을 설치하거나 사용할 필요는 없습니다.

## NTP(Network Time Protocol) 설치 및 구성

[NTP](https://www.ntp.org/) 서버가 [사용 가능한 풀 서버](https://www.ntppool.org/en/). 내부 네트워크든 외부 공용 서버든, NTP 서버를 사용하는 것이 좋습니다.

여러 호스트에 Adobe Commerce 또는 Magento Open Source을 배포하는 경우 NTP는 서버가 속한 시간대와 관계없이 시계를 모두 동기화하도록 보장하는 간단한 방법입니다. 또한 색인화 및 트랜잭션 전자 메일과 같은 크론 관련 작업은 서버 클럭에 따라 정확합니다.

### Ubuntu에 NTP 설치 및 구성

NTP를 설치하려면 다음 명령을 입력합니다.

```bash
apt-get install ntp
```

계속 [NTP 풀 서버 사용](#use-ntp-pool-servers).

### CentOS에서 NTP 설치 및 구성

NTP 설치 및 구성 방법:

1. 다음 명령을 입력하여 적절한 NTP 소프트웨어를 찾습니다.

   ```bash
   yum search ntp
   ```

1. 설치할 패키지를 선택합니다. For example, `ntp.x86_64`.

1. 패키지를 설치합니다.

   ```bash
   yum -y install ntp.x86_64
   ```

1. 서버가 시작될 때 NTP가 시작되도록 다음 명령을 입력합니다.

   ```bash
   chkconfig ntpd on
   ```

1. 다음 섹션을 계속 진행합니다.

### NTP 풀 서버 사용

풀 서버를 선택하는 것은 사용자의 책임입니다. NTP 풀 서버를 사용하는 경우 ntp.org를 사용하는 것이 좋습니다 [풀 서버](https://www.ntppool.org/en/) 에 설명된 대로 서버의 시간대에 근접합니다. [NTP 풀 프로젝트 페이지](https://www.ntppool.org/en/use.html). 배포에 있는 모든 호스트에서 사용 가능한 개인 NTP 서버가 있는 경우 해당 서버를 대신 사용할 수 있습니다.

1. 열기 `/etc/ntp.conf` 텍스트 편집기에서 을 참조하십시오.

1. 다음과 유사한 라인을 찾습니다.

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 해당 라인을 교체하거나 NTP 풀 서버 또는 다른 NTP 서버를 지정하는 추가 라인을 추가합니다. 두 개 이상을 지정하는 것이 좋습니다.

1. 미국 기반 NTP 서버 세 개를 사용하는 예는 다음과 같습니다.

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 변경 내용을 `/etc/ntp.conf` 텍스트 편집기를 종료합니다.

1. 서비스를 다시 시작합니다.

   * 우분투: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Enter 키 `date` 서버의 날짜를 확인합니다.

   날짜가 잘못된 경우 NTP 클라이언트 포트(일반적으로 UDP 123)가 방화벽에서 열려 있는지 확인하십시오.

   를 사용해 보십시오 `ntpdate _[pool server hostname]_` 명령. 실패하면 반환되는 오류를 검색합니다.

   다른 모든 작업이 실패하면 서버를 재부팅해 보십시오.

## phpinfo.php 만들기

다음 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 파일에는 [PHP](https://glossary.magento.com/php) 및 확장.

>[!NOTE]
>
>사용 `phpinfo.php` 개발 시스템에서 _전용_. 프로덕션 환경에서 보안 문제가 될 수 있습니다.

웹 서버의 docroot에 있는 아무 곳에나 다음 코드를 추가합니다.

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

자세한 내용은 [phpinfo 설명서 페이지](https://www.php.net/manual/en/function.phpinfo.php).

결과를 보려면 다음을 입력합니다 [URL](https://glossary.magento.com/url) 브라우저의 위치 또는 주소 필드에서 다음을 수행합니다.

```http
http://<web server host or IP>/phpinfo.php
```

404(찾을 수 없음) 오류가 표시되면 다음을 확인합니다.

* 필요한 경우 웹 서버를 시작합니다.
* 방화벽이 포트 80에서 트래픽을 허용하는지 확인하십시오.

   [Ubuntu 도움말](https://help.ubuntu.com/community/UFW)

   [CentOS 도움말](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

phpMyAdmin 응용 프로그램은 사용하기 쉽고 무료 데이터베이스 관리 유틸리티입니다. 이를 사용하여 데이터베이스의 내용을 확인하고 조작할 수 있습니다. phpMyAdmin에 MySQL 데이터베이스 관리 사용자로 로그인해야 합니다.

phpMyAdmin에 대한 자세한 내용은 [phpMyAdmin 홈 페이지](https://www.phpmyadmin.net/).

설치에 대한 자세한 내용은 [phpMyAdmin 설치 설명서](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>개발 시스템에서 phpMyAdmin 사용 _전용_. 프로덕션 환경에서 보안 문제가 될 수 있습니다.

1. phpMyAdmin을 사용하려면 브라우저의 주소 또는 위치 필드에 다음 명령을 입력합니다.

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 메시지가 표시되면 MySQL 데이터베이스를 사용하여 로그인합니다 `root` 또는 관리자 사용자 이름과 암호를 사용하여 정보를 검색할 수 있습니다.
