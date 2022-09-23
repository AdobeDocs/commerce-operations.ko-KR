---
title: Apache
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온프레미스 설치에 대한 Apache 웹 서버를 설치하고 구성합니다.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---


# Apache

Adobe Commerce은 Apache 2.4.x를 지원합니다.

## Apache 필수 지시문

1. 설정 `AllowEncodedSlashes` 인코딩된 슬래시를 디코딩하지 않도록 서버 구성(전역) 또는 가상 호스트 구성에서 URL에 문제가 발생할 수 있습니다. 예를 들어 API를 통해 SKU에서 슬래시가 있는 제품을 검색할 때 해당 제품을 전환하지 않도록 합니다. 샘플 블록이 완전하지 않으며 다른 지시어가 필요합니다.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache rewrites 및 htaccess

이 항목에서는 Apache 2.4 rewrites를 활성화하고 를 위한 설정을 지정하는 방법에 대해 설명합니다 [분산 구성 파일, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce 및 Magento Open Source은 서버 rewrites 및 를 사용합니다 `.htaccess` 를 사용하여 Apache에 대한 디렉토리 수준 지침을 제공할 수 있습니다. 다음 지침은 이 항목의 다른 모든 섹션에도 포함되어 있습니다.

이 섹션을 사용하여 Apache 2.4 재쓰기를 활성화하고 설정을 지정합니다. [분산 구성 파일, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce 및 Magento Open Source은 서버 rewrites 및 를 사용합니다 `.htaccess` 를 사용하여 Apache에 대한 디렉토리 수준 지침을 제공할 수 있습니다.

>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

1. Apache rewrite 모듈을 활성화합니다.

   ```bash
   a2enmod rewrite
   ```

1. 응용 프로그램에서 분산 장치를 사용하도록 설정하려면 `.htaccess` 구성 파일의 경우 [Apache 2.4 설명서](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Apache 2.4에서 서버의 기본 사이트 구성 파일은 다음과 같습니다 `/etc/apache2/sites-available/000-default.conf`.

   예를 들어 `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >경우에 따라 추가 매개 변수가 필요할 수 있습니다. 자세한 내용은 [Apache 2.4 설명서](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Apache 설정을 변경한 경우 Apache를 다시 시작합니다.

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 이전 Apache 버전에서 업그레이드한 경우 먼저 를 찾습니다 `<Directory "/var/www/html">` 또는 `<Directory "/var/www">` in `000-default.conf`.
   >- 값을 변경해야 합니다. `AllowOverride` 를 입력합니다. 예를 들어 웹 서버 docroot에 설치하려면 `<Directory /var/www>`.


>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

## Apache 필수 모듈

Adobe Commerce 및 Magento Open Source을 사용하려면 다음 Apache 모듈을 설치해야 합니다.

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apache 버전을 확인합니다

현재 실행 중인 Apache 버전을 확인하려면 다음을 입력합니다.

```bash
apache2 -v
```

결과는 다음과 유사하게 표시됩니다.

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Apache가 *not* 설치됨:
   - [Ubuntu에서 Apache 설치 또는 업그레이드](#installing-apache-on-ubuntu)
   - [CentOS에 Apache 설치](#installing-apache-on-centos)

## Ubuntu에서 Apache 설치 또는 업그레이드

다음 섹션에서는 Apache를 설치하거나 업그레이드하는 방법에 대해 설명합니다.

- Apache 설치
- PHP 7.4를 사용하려면 Ubuntu의 Apache 2.4로 업그레이드하십시오.

### Ubuntu에 Apache 설치

기본 버전의 Apache를 설치하려면 다음을 수행하십시오.

1. Apache 설치

   ```bash
   apt-get -y install apache2
   ```

1. 설치를 확인합니다.

   ```bash
   apache2 -v
   ```

   결과는 다음과 유사하게 표시됩니다.

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. 활성화 [rewrites 및 `.htaccess`](#apache-rewrites-and-htaccess).

### Ubuntu에서 Apache 업그레이드

Apache 2.4로 업그레이드하려면 다음을 수행하십시오.

1. 추가 `ppa:ondrej` Apache 2.4가 있는 저장소:

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
   >충족되지 않은 종속성으로 인해 &#39;apt-get install&#39; 명령이 실패하는 경우 다음과 같은 리소스를 참조하십시오 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. 설치를 확인합니다.

   ```bash
   apache2 -v
   ```

   다음과 유사한 메시지가 표시됩니다.

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 활성화 [rewrites 및 `.htaccess`](#apache-rewrites-and-htaccess).

## CentOS에 Apache 설치

Adobe Commerce 및 Magento Open Source을 사용하려면 Apache 사용 서버 재쓰기가 필요합니다. 또한 사용할 수 있는 지시어 유형을 지정해야 합니다 `.htaccess`: 애플리케이션이 재작성 규칙을 지정하는 데 사용하는 것입니다.

Apache를 설치하고 구성하는 것은 기본적으로 3단계 프로세스입니다. 소프트웨어를 설치하고, 다시 쓰기를 활성화하고, `.htaccess` 지시어

### Apache 설치

1. 아직 설치하지 않았다면 Apache 2.4를 설치합니다.

   ```bash
   yum -y install httpd
   ```

1. 설치 확인:

   ```bash
   httpd -v
   ```

   다음 표시와 유사한 메시지를 통해 설치가 성공했는지 확인합니다.

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 다음 섹션을 계속 진행합니다.

   >[!NOTE]
   >
   >Apache 2.4가 기본적으로 CentOS와 함께 제공되더라도 다음 섹션을 참조하여 구성합니다.

### CentOS에 대해 rewrites 및 .htaccess 사용

1. 열기 `/etc/httpd/conf/httpd.conf` 편집할 파일:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   ```conf
   <Directory "/var/www/html">
   ```

1. 값 변경 `AllowOverride` to `All`.

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
   >에 대한 이전 값 `Order` 모든 경우에 작동하지 않을 수 있습니다. 자세한 내용은 Apache 설명서 ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. 파일을 저장하고 텍스트 편집기를 종료합니다.

1. Apache 설정을 적용하려면 Apache를 다시 시작합니다.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다.

### Ubuntu에 대해 rewrites 및 .htaccess 사용

1. 열기 `/etc/apache2/sites-available/default` 편집할 파일:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   `<Directory "/var/www/html">`

1. 값 변경 `AllowOverride` to `All`.

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

1. 를 사용하도록 Apache 구성 `mod_rewrite` 모듈:

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

## 403(금지된) 오류 해결

사이트에 액세스하려고 할 때 403 금지된 오류가 발생하는 경우 Apache 구성 또는 가상 호스트 구성을 업데이트하여 사이트 방문자가 액세스할 수 있도록 할 수 있습니다.

### Apache 2.4에 대해 금지된 오류 해결

웹 사이트 방문자가 사이트에 액세스할 수 있도록 하려면 다음 중 하나를 사용합니다 [지시 필요](https://httpd.apache.org/docs/2.4/howto/access.html).

예:

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
>에 대한 이전 값 `Order` 모든 경우에 작동하지 않을 수 있습니다. 자세한 내용은 [Apache 설명서](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).