---
title: Apache
description: Adobe Commerce의 온-프레미스 설치용 Apache 웹 서버를 설치하고 구성하려면 다음 단계를 따르십시오.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce은 Apache 2.4.x를 지원합니다.

## Apache 필수 지시문

1. URL에 문제를 일으킬 수 있는 인코딩된 슬래시를 디코딩하지 않도록 서버 구성(전역) 또는 가상 호스트 구성에서 `AllowEncodedSlashes`을(를) 설정하십시오. 예를 들어 API를 통해 SKU에서 슬래시가 있는 제품을 검색할 때 변환하지 않으려고 합니다. 샘플 블록이 완료되지 않았으며 다른 지시문이 필요합니다.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache rewrites 및 htaccess

이 항목에서는 Apache 2.4 재작성을 활성화하고 [분산 구성 파일 `.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample)에 대한 설정을 지정하는 방법에 대해 설명합니다.

Adobe Commerce은 서버 재작성 및 `.htaccess`을(를) 사용하여 Apache에 디렉터리 수준 지침을 제공합니다. 이 항목의 다른 모든 섹션에도 다음 지침이 포함되어 있습니다.

이 섹션을 사용하여 Apache 2.4 재작성을 활성화하고 [분산 구성 파일 `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)에 대한 설정을 지정하십시오.

Adobe Commerce은 서버 재작성 및 `.htaccess`을(를) 사용하여 Apache에 디렉터리 수준 지침을 제공합니다.

>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

1. Apache 재작성 모듈 활성화:

   ```bash
   a2enmod rewrite
   ```

1. 응용 프로그램에서 배포된 `.htaccess` 구성 파일을 사용할 수 있도록 하려면 [Apache 2.4 설명서](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)의 지침을 참조하십시오.

   >[!TIP]
   >
   >Apache 2.4에서 서버의 기본 사이트 구성 파일은 `/etc/apache2/sites-available/000-default.conf`입니다.

   예를 들어 `000-default.conf`의 끝에 다음을 추가할 수 있습니다.

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >경우에 따라 추가 매개 변수가 필요할 수 있습니다. 자세한 내용은 [Apache 2.4 설명서](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)를 참조하십시오.

1. Apache 설정을 변경한 경우 Apache를 다시 시작합니다.

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 이전 Apache 버전에서 업그레이드한 경우 먼저 `<Directory "/var/www/html">`에서 `<Directory "/var/www">` 또는 `000-default.conf`을(를) 찾습니다.
   >- Adobe Commerce 소프트웨어를 설치할 디렉터리에 대한 지시문에서 `AllowOverride` 값을 변경해야 합니다. 예를 들어 웹 서버 docroot에 설치하려면 `<Directory /var/www>`에서 지시문을 편집하십시오.

>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

## Apache 필수 모듈

Adobe Commerce을 사용하려면 다음 Apache 모듈이 설치되어 있어야 합니다.

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apache 버전 확인

현재 실행 중인 Apache 버전을 확인하려면 다음을 입력합니다.

```bash
apache2 -v
```

결과는 다음과 유사하게 표시됩니다.

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Apache가 *설치되지 않은*&#x200B;경우 다음을 참조하십시오.
   - [Ubuntu에서 Apache 설치 또는 업그레이드](#installing-apache-on-ubuntu)
   - [CentOS에 Apache 설치](#installing-apache-on-centos)

## Ubuntu에서 Apache 설치 또는 업그레이드

다음 섹션에서는 Apache 설치 또는 업그레이드 방법에 대해 설명합니다.

- Apache 설치
- PHP 7.4를 사용하려면 Ubuntu에서 Apache 2.4로 업그레이드하십시오.

### Ubuntu에 Apache 설치

Apache의 기본 버전을 설치하려면

1. Apache 설치

   ```bash
   apt-get -y install apache2
   ```

1. 설치를 확인합니다.

   ```bash
   apache2 -v
   ```

   결과는 다음과 유사하게 표시됩니다.

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. [다시 쓰기 및 `.htaccess`](#apache-rewrites-and-htaccess)을(를) 사용하도록 설정합니다.

### 우분투에서 Apache 업그레이드

Apache 2.4로 업그레이드하려면 다음을 수행하십시오.

1. Apache 2.4가 있는 `ppa:ondrej` 저장소 추가:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Apache 2.4 설치:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >충족되지 않는 종속성으로 인해 &#39;apt-get install&#39; 명령이 실패한 경우 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)과(와) 같은 리소스를 참조하십시오.

1. 설치를 확인합니다.

   ```bash
   apache2 -v
   ```

   다음과 유사한 메시지가 표시되어야 합니다.

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. [다시 쓰기 및 `.htaccess`](#apache-rewrites-and-htaccess)을(를) 사용하도록 설정합니다.

## CentOS에 Apache 설치

Adobe Commerce은 Apache 서버 재쓰기가 필요합니다. 또한 응용 프로그램에서 재작성 규칙을 지정하는 데 사용하는 `.htaccess`에서 사용할 수 있는 지시문 형식을 지정해야 합니다.

Apache 설치 및 구성은 기본적으로 소프트웨어를 설치하고, 다시 쓰기를 활성화하고, `.htaccess` 지시문을 지정하는 3단계 프로세스입니다.

### Apache 설치

1. 아직 설치하지 않은 경우 Apache 2.4를 설치합니다.

   ```bash
   yum -y install httpd
   ```

1. 설치 확인:

   ```bash
   httpd -v
   ```

   설치가 성공했는지 확인하는 다음 디스플레이와 유사한 메시지:

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 다음 섹션을 계속합니다.

   >[!NOTE]
   >
   >Apache 2.4가 기본적으로 CentOS와 함께 제공되더라도 다음 섹션을 참조하여 구성하십시오.

### CentOS용 rewrites 및 .htaccess 활성화

1. 편집할 `/etc/httpd/conf/httpd.conf` 파일 열기:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   ```conf
   <Directory "/var/www/html">
   ```

1. `AllowOverride`의 값을 `All`(으)로 변경합니다.

   For example,

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >`Order`에 대한 이전 값이 모든 경우에 작동하지 않을 수 있습니다. 자세한 내용은 Apache 설명서([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order))를 참조하십시오.

1. 파일을 저장하고 텍스트 편집기를 종료합니다.

1. Apache 설정을 적용하려면 Apache를 다시 시작합니다.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

### Ubuntu에 대한 재작성 및 .htaccess 활성화

1. 편집할 `/etc/apache2/sites-available/default` 파일 열기:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   `<Directory "/var/www/html">`

1. `AllowOverride`의 값을 `All`(으)로 변경합니다.

   For example:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. 파일을 저장하고 텍스트 편집기를 종료합니다.

1. `mod_rewrite` 모듈을 사용하도록 Apache 구성:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. 변경 사항을 적용하려면 Apache를 다시 시작하십시오.

   ```bash
   service apache2 restart
   ```

## 403(사용할 수 없음) 오류 해결

사이트에 액세스하려고 할 때 403 금지된 오류가 발생하는 경우 Apache 구성 또는 가상 호스트 구성을 업데이트하여 사이트 방문자를 사용할 수 있도록 할 수 있습니다.

### Apache 2.4에 대해 403 금지된 오류 해결

웹 사이트 방문자가 사이트에 액세스할 수 있도록 하려면 [지시문 필요](https://httpd.apache.org/docs/2.4/howto/access.html) 중 하나를 사용하십시오.

For example:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>`Order`에 대한 이전 값이 모든 경우에 작동하지 않을 수 있습니다. 자세한 내용은 [Apache 설명서](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)를 참조하십시오.
