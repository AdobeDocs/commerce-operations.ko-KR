---
title: 보안 크론 PHP
description: 브라우저에서 cron.php 파일을 실행할 수 있는 사용자를 제한합니다.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# 보안 크론 PHP

이 항목에서는 보안 설정에 대해 설명합니다 `pub/cron.php` 악의적인 악용에 사용되지 않도록 하기 위해. cron을 보호하지 않으면 모든 사용자가 cron을 실행하여 상거래 애플리케이션을 공격할 수 있습니다.

cron 작업은 예약된 여러 작업을 실행하며 상거래 구성의 중요한 부분입니다. 예약된 작업에는 다음이 포함되지만 이에 국한되지는 않습니다.

- 리인덱싱
- 전자 메일 생성
- 뉴스레터 생성
- 사이트 맵 생성 중

>[!INFO]
>
>을(를) 참조하십시오 [cron 구성 및 실행](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) cron 그룹에 대한 자세한 정보를 제공합니다.

다음과 같은 방법으로 cron 작업을 실행할 수 있습니다.

- 사용 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 명령줄 또는 crontab의 명령
- 액세스 `pub/cron.php?[group=<name>]` 웹 브라우저에서

>[!INFO]
>
>를 사용하는 경우 아무 작업도 하지 않아도 됩니다. [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 이미 안전한 다른 프로세스를 사용하므로 cron을 실행하는 명령입니다.

## Apache를 사용한 보안 크론

이 섹션에서는 Apache에서 HTTP 기본 인증을 사용하여 cron을 보호하는 방법에 대해 설명합니다. 이러한 지침은 CentOS 6의 Apache 2.2를 기반으로 합니다. 자세한 내용은 다음 리소스 중 하나를 참조하십시오.

- [Apache 2.2 인증 및 권한 부여 자습서](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4 인증 및 권한 부여 자습서](https://httpd.apache.org/docs/2.4/howto/auth.html)

### 암호 파일 만들기

보안상의 이유로 웹 서버 docroot를 제외한 모든 위치에서 암호 파일을 찾을 수 있습니다. 이 예제에서는 암호 파일을 새 디렉토리에 저장합니다.

사용자로 다음 명령을 입력합니다. `root` 권한:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

위치 `<username>` 웹 서버 사용자 또는 다른 사용자일 수 있습니다. 이 예제에서는 웹 서버 사용자를 사용하지만 사용자의 선택은 사용자가 결정합니다.

화면의 지침에 따라 사용자의 암호를 생성합니다.

암호 파일에 다른 사용자를 추가하려면 다음 명령을 `root` 권한:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### 인증된 cron 그룹을 생성할 사용자 추가(선택 사항)

그룹 파일을 포함한 암호 파일에 두 명 이상의 사용자를 추가하여 cron을 실행할 수 있도록 설정할 수 있습니다.

암호 파일에 다른 사용자를 추가하려면 다음 작업을 수행하십시오.

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

승인된 그룹을 만들려면 웹 서버 docroot 외부의 아무 곳에나 그룹 파일을 만듭니다. 그룹 파일은 그룹의 이름과 그룹의 사용자를 지정합니다. 이 예에서 그룹 이름은 입니다. `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

파일의 내용:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### 의 보안 크론 `.htaccess`

크론을 보호하려면 `.htaccess` 파일:

1. 파일 시스템 소유자로 Commerce 서버에 로그인하거나 파일 시스템 소유자로 전환합니다.
1. 열기 `<magento_root>/pub/.htaccess` 텍스트 편집기에서.

   (이유 `cron.php` 은(는)에 있습니다. `pub` 디렉터리, 편집 `.htaccess` 만 해당)

1. _한 명 이상의 사용자에 대한 크론 액세스._ 기존 항목 바꾸기 `<Files cron.php>` 지시문에 다음을 포함합니다.

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _그룹에 대한 크론 액세스._ 기존 항목 바꾸기 `<Files cron.php>` 지시문에 다음을 포함합니다.

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 변경 내용 저장 `.htaccess` 텍스트 편집기를 종료합니다.
1. 계속 [cron이 안전한지 확인](#verify-cron-is-secure).

## Nginx로 cron 보호

이 섹션에서는 Nginx 웹 서버를 사용하여 cron을 보호하는 방법에 대해 설명합니다. 다음 작업을 수행해야 합니다.

1. Nginx에 대한 암호화된 암호 파일 설정
1. 에 액세스할 때 암호 파일을 참조하도록 nginx 구성을 수정합니다 `pub/cron.php`

### 암호 파일 만들기

계속하기 전에 다음 리소스 중 하나를 참조하여 암호 파일을 생성하십시오.

- [Ubuntu 14.04 (DigitalOcean)에서 Nginx를 사용하여 암호 인증을 설정하는 방법](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Nginx를 사용한 기본 HTTP 인증(howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### 의 보안 크론 `nginx.conf.sample`

Commerce는 즉시 최적화된 샘플 nginx 구성 파일을 제공합니다. cron 을 보호하기 위해 수정하는 것이 좋습니다.

1. 다음에 추가 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 파일:

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.nginx 다시 시작:

```bash
systemctl restart nginx
```

1. 계속 [cron이 안전한지 확인](#verify-cron-is-secure).

## cron이 안전한지 확인

이를 확인하는 가장 쉬운 방법 `pub/cron.php` 은(는) 가 행을에서 생성하고 있는지 확인하는 데 안전합니다. `cron_schedule` 비밀번호 인증을 설정한 후의 데이터베이스 테이블입니다. 이 예제에서는 SQL 명령을 사용하여 데이터베이스를 확인하지만 원하는 도구를 모두 사용할 수 있습니다.

>[!INFO]
>
>다음 `default` 이 예제에서 실행 중인 cron은에 정의된 일정에 따라 실행됩니다. `crontab.xml`. 일부 cron 작업은 하루에 한 번만 실행됩니다. 브라우저에서 cron을 처음 실행하면 `cron_schedule` 테이블이 업데이트되지만 이후 `pub/cron.php` 요청은 구성된 일정에 따라 실행됩니다.

**cron이 안전한지 확인하려면**:

1. Commerce 데이터베이스 사용자 또는 로 데이터베이스에 로그인합니다. `root`.

   예를 들어,

   ```bash
   mysql -u magento -p
   ```

1. 상거래 데이터베이스 사용:

   ```shell
   use <database-name>;
   ```

   예를 들어,

   ```shell
   use magento;
   ```

1. 에서 모든 행 삭제 `cron_schedule` 데이터베이스 테이블:

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. 브라우저에서 cron 실행:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   예:

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. 메시지가 표시되면 인증된 사용자의 이름과 암호를 입력합니다. 다음 그림은 예를 보여 줍니다.

   ![HTTP Basic을 사용하여 cron 인증](../../assets/configuration/cron-auth.png)

1. 행이 표에 추가되었는지 확인합니다.

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## 웹 브라우저에서 cron 실행

웹 브라우저를 사용하여 개발 중과 같이 언제든지 cron 을 실행할 수 있습니다.

>[!WARNING]
>
>실행 _아님_ 먼저 보호하지 않고 브라우저에서 cron을 실행합니다.

Apache 웹 서버를 사용하는 경우 `.htaccess` 브라우저에서 cron을 실행하기 전에 다음 파일을 확인하십시오.

1. Commerce 파일 시스템에 쓸 수 있는 권한이 있는 사용자로 Commerce 서버에 로그인합니다.
1. 텍스트 편집기에서 다음 중 하나를 엽니다(Magento 시작 지점에 따라 다름).

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. 다음 내용을 삭제하거나 주석을 답니다.

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   예를 들어,

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.

   그런 다음 다음과 같이 웹 브라우저에서 cron을 실행할 수 있습니다.

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

위치:

- `<your hostname or IP>` 는 Commerce 설치의 호스트 이름 또는 IP 주소입니다
- `<Commerce root>` 는 Commerce 소프트웨어를 설치한 웹 서버 docroot 관련 디렉토리입니다

   Commerce 응용 프로그램을 실행하는 데 사용하는 정확한 URL은 웹 서버와 가상 호스트를 구성한 방식에 따라 다릅니다.

- `<group name>` 은(는) 모든 유효한 cron 그룹 이름입니다(선택 사항).

예를 들어,

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>cron을 두 번 실행해야 합니다. 먼저 실행할 작업을 검색하고 다시 실행하여 작업 자체를 실행합니다. 을(를) 참조하십시오 [cron 구성 및 실행](../cli/configure-cron-jobs.md) cron 그룹에 대한 자세한 정보를 제공합니다.
