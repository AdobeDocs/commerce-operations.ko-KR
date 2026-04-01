---
title: 온-프레미스 배포용 Apache 설치
description: 온-프레미스 Adobe Commerce 배포용 Apache를 설치하고 구성하는 방법에 대해 알아봅니다. 필요한 모듈, 재작성 및 ".htaccess" 설정을 활성화합니다.
feature: Install, Configuration
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# 온-프레미스 배포용 Apache 설치 {#apache}

이 안내서에서는 Adobe Commerce 온-프레미스 배포용 Apache를 설치하고 Commerce에 필요한 Apache 설정을 구성하는 방법을 안내합니다. 여기에는 Ubuntu 및 CentOS에 대한 공유된 Apache 요구 사항 및 운영 체제별 절차가 포함됩니다. Adobe은 이 안내서에 제공된 구성 지침을 따라 Commerce 애플리케이션의 기능과 보안을 모두 유지하는 것을 권장합니다.

Adobe은 Adobe Commerce 릴리스의 [시스템 요구 사항](../../system-requirements.md)에 나열된 Apache 버전을 지원합니다. 지원되는 버전은 릴리스에 따라 다릅니다. Apache에도 지원되는 PHP 구성이 필요합니다. 관련 PHP 요구 사항에 대해서는 [PHP 설정](../php-settings.md)을 참조하십시오.

사용자 환경과 일치하는 섹션으로 시작합니다.

- Apache가 이미 설치되어 있는 경우 [Apache 요구 사항 검토](#review-apache-requirements)(으)로 시작하십시오.
- Ubuntu에 Apache를 설치하거나 업그레이드하려면 [Ubuntu에 Apache 설치 또는 업그레이드](#installing-or-upgrading-apache-on-ubuntu)로 이동하십시오.
- CentOS에 Apache를 설치해야 하는 경우 [CentOS에 Apache 설치](#installing-apache-on-centos)로 이동하십시오.

## Apache 요구 사항 검토

Adobe Commerce을 호스팅하는 모든 Apache 서버에서 다음 요구 사항을 완료합니다.

### 필요한 지시어 구성

URL에 문제를 일으킬 수 있는 인코딩된 슬래시를 디코딩하지 않도록 서버 구성(전역) 또는 가상 호스트 구성에서 `AllowEncodedSlashes`을(를) 설정하십시오. 예를 들어 API를 통해 SKU에서 슬래시가 있는 제품을 검색할 때 슬래시가 변환되지 않도록 해야 합니다. 다음 예제 블록은 완료되지 않았으며 다른 지시문이 필요합니다.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### 재작성 및 .htaccess 구성 {#apache-rewrites-and-htaccess}

이 섹션을 사용하여 Apache에서 [분산 `.htaccess` 파일을 다시 쓰고 구성하도록 설정합니다](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce은 서버 재작성 및 `.htaccess`을(를) 사용하여 Apache에 디렉터리 수준 지침을 제공합니다.

>[!IMPORTANT]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다. 또한 Apache가 `.htaccess`에 정의된 Adobe Commerce 보안 보호를 적용하지 못하도록 할 수 있습니다.

1. Apache 재작성 모듈 활성화:

   ```bash
   a2enmod rewrite
   ```

1. 응용 프로그램에서 배포된 `.htaccess` 구성 파일을 사용하도록 설정하십시오.

   1. Ubuntu에서 `/etc/apache2/sites-available/000-default.conf`을(를) 편집합니다. 다른 Apache 레이아웃의 경우 또는 추가 매개 변수가 필요한 경우 [Apache 설명서](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) 및 [Apache 액세스 제어 설명서](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)를 참조하십시오.

   1. Adobe Commerce을 설치할 디렉터리에 대한 `AllowOverride` 지시문을 추가하거나 업데이트합니다.

   예를 들어, 기본 `docroot`에 Adobe Commerce을 설치하는 경우 `000-default.conf`에 다음 블록을 추가하십시오.

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >이전 Apache 버전에서 업그레이드한 경우 먼저 `<Directory "/var/www/html">`에서 기존 `<Directory "/var/www">` 또는 `000-default.conf` 블록을 찾으십시오. 다른 `docroot`에 Adobe Commerce을 설치하는 경우 해당 경로에 대해 일치하는 `<Directory>` 블록을 업데이트하십시오.

1. 변경 사항을 적용하려면 Apache를 다시 시작하십시오.

   ```bash
   service apache2 restart
   ```

### 필수 모듈 설치

Adobe Commerce을 사용하려면 다음 Apache 모듈이 설치되어 있어야 합니다.

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apache가 설치되었는지 확인

Apache가 설치되었는지 확인하고 현재 버전을 보려면 다음을 입력합니다.

```bash
apache2 -v
```

결과는 다음과 유사한 정보를 표시합니다.

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Apache가 *설치되지 않은*&#x200B;경우 다음을 참조하십시오.
   - [Ubuntu에서 Apache 설치 또는 업그레이드](#installing-or-upgrading-apache-on-ubuntu)
   - [CentOS에 Apache 설치](#installing-apache-on-centos)

## Ubuntu에서 Apache 설치 또는 업그레이드 {#installing-or-upgrading-apache-on-ubuntu}

Ubuntu에 Apache를 설치하고 구성하는 프로세스는 다음 3단계입니다.

1. 소프트웨어를 설치합니다.
1. 재작성을 활성화합니다.
1. `.htaccess` 지시문을 지정하십시오.

Apache 서버 재작성을 구성할 때 응용 프로그램에서 재작성 규칙 및 보안 보호를 지정하는 데 사용하는 `.htaccess`에서 사용할 수 있는 지시문 유형을 지정해야 합니다.

### Ubuntu에 Apache 설치

1. 아직 설치하지 않은 경우 Apache를 설치합니다.

   ```bash
   apt-get -y install apache2
   ```

1. 설치 확인:

   ```bash
   apache2 -v
   ```

   설치가 성공했는지 확인하는 다음 디스플레이와 유사한 메시지:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 다음 섹션을 계속합니다.

   >[!NOTE]
   >
   >Ubuntu에서 Apache가 기본적으로 제공되더라도 다음 섹션을 참조하여 구성하십시오.

### Ubuntu에서 Apache 업그레이드

Apache가 이미 설치되어 있고 `2.4` 이전 버전을 사용 중인 경우 Apache `2.4` 또는 배포한 Adobe Commerce 버전에서 지원하는 최신 버전으로 업그레이드하십시오. [시스템 요구 사항](../../system-requirements.md)을 참조하세요.

1. 패키지 정보 업데이트:

   ```bash
   apt-get -y update
   ```

1. 필요한 경우 환경에 지원되는 Apache 버전을 제공하는 저장소를 추가합니다.

1. Apache 설치 또는 업그레이드:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >일치하지 않는 종속성으로 인해 `apt-get install` 명령이 실패한 경우 운영 체제 패키지 설명서나 배포 지원 리소스를 참조하십시오.

1. 설치 확인:

   ```bash
   apache2 -v
   ```

1. 설치된 버전이 [시스템 요구 사항](../../system-requirements.md)에서 Adobe Commerce 릴리스에 대해 지원되는 버전과 일치하는지 확인하십시오.

1. Ubuntu[에 대해 `.htaccess`다시 쓰기 및 &#x200B;](#enable-rewrites-and-htaccess-for-ubuntu)을(를) 사용하도록 설정합니다.

### Ubuntu에 대한 재작성 및 .htaccess 활성화

1. 편집할 `/etc/apache2/sites-available/000-default.conf` 파일을 엽니다.

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다. 또한 Apache가 `.htaccess`에 정의된 Adobe Commerce 보안 보호를 적용하지 못하도록 할 수 있습니다.

## CentOS에 Apache 설치 {#installing-apache-on-centos}

CentOS에 Apache를 설치하고 구성하는 작업은 다음 세 단계로 진행됩니다.

1. 소프트웨어 설치
2. 재작성 사용
3. `.htaccess` 지시문을 지정하십시오.

Apache 서버 재작성을 구성할 때 응용 프로그램에서 재작성 규칙 및 보안 보호를 지정하는 데 사용하는 `.htaccess`에서 사용할 수 있는 지시문 유형을 지정해야 합니다.

### Apache 설치

1. 아직 설치하지 않았다면 Apache를 설치합니다.

   ```bash
   yum -y install httpd
   ```

1. 설치 확인:

   ```bash
   httpd -v
   ```

   설치가 성공했는지 확인하는 다음 디스플레이와 유사한 메시지:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 다음 섹션을 계속합니다.

   >[!NOTE]
   >
   >Apache가 기본적으로 CentOS와 함께 제공되더라도 다음 섹션을 참조하여 구성하십시오.

### CentOS용 rewrites 및 .htaccess 활성화

1. 편집할 `/etc/httpd/conf/httpd.conf` 파일을 엽니다.

   ```bash
   vim /etc/httpd/conf/httpd.conf
   ```

1. 다음으로 시작하는 블록을 찾습니다.

   ```conf
   <Directory "/var/www/html">
   ```

1. `AllowOverride`의 값을 `All`(으)로 변경합니다.

   For example:

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
   >`Order`에 대한 이전 값이 모든 경우에 작동하지 않을 수 있습니다. 자세한 내용은 [Apache 설명서](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)를 참조하십시오.

1. 파일을 저장하고 텍스트 편집기를 종료합니다.

1. Apache 설정을 적용하려면 Apache를 다시 시작합니다.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>이러한 설정을 활성화하지 않으면 일반적으로 상점 또는 관리자에 스타일이 표시되지 않습니다. 또한 Apache가 `.htaccess`에 정의된 Adobe Commerce 보안 보호를 적용하지 못하도록 할 수 있습니다.

## 403(사용할 수 없음) 오류 해결

사이트에 액세스하려고 할 때 403 금지된 오류가 발생하는 경우 Apache 구성 또는 가상 호스트 구성을 업데이트하여 사이트 방문자를 사용할 수 있도록 할 수 있습니다.

### Apache에 대해 403 금지된 오류 해결

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
