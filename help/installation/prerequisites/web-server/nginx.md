---
title: Nginx
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온프레미스 설치에 대한 Nginx 웹 서버를 설치하고 구성합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerce은 nginx 1.18(또는 [최신 메인라인 버전](https://nginx.org/en/linux_packages.html#mainline)). 최신 버전의 를 설치해야 합니다 `php-fpm`.

설치 지침은 사용 중인 운영 체제에 따라 다릅니다. 자세한 내용은 [PHP](../php-settings.md) 참조하십시오.

## 우분투

다음 섹션에서는 nginx, PHP 및 MySQL을 사용하여 Ubuntu에 Adobe Commerce 및 Magento Open Source 2.x를 설치하는 방법을 설명합니다.

### nginx 설치

```bash
sudo apt -y install nginx
```

다음을 수행할 수도 있습니다 [소스에서 인스턴스 작성](https://www.armanism.com/blog/install-nginx-on-ubuntu)

다음 섹션을 완료하고 애플리케이션을 설치한 후 샘플 구성 파일을 사용하여 [nginx 구성](#configure-nginx).

### php-fpm 설치 및 구성

Adobe Commerce 및 Magento Open Source은 몇 가지가 필요합니다 [PHP 확장](../php-settings.md) 제대로 작동하도록 합니다. 이러한 확장 외에 를 설치하고 구성해야 합니다 `php-fpm` nginx를 사용하는 경우 확장하십시오.

설치 및 구성하려면 `php-fpm`:

1. 설치 `php-fpm` 및 `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >이 명령은 사용 가능한 최신 버전의 PHP 7.2.X를 설치합니다. 자세한 내용은 [시스템 요구 사항](../../system-requirements.md) 지원되는 PHP 버전에 대해 설명합니다.

1. 를 엽니다. `php.ini` 편집기의 파일:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 다음 줄과 일치하도록 두 파일을 모두 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe Commerce 및 Magento Open Source을 테스트할 때 메모리 제한을 2G로 설정하는 것이 좋습니다. 을(를) 참조하십시오. [필수 PHP 설정](../php-settings.md) 추가 정보.

1. 편집기를 저장하고 종료합니다.

1. 를 다시 시작합니다. `php-fpm` 서비스:

   ```bash
   systemctl restart php7.2-fpm
   ```

### MySQL 설치 및 구성

을(를) 참조하십시오. [MySQL](../database/mysql.md) 추가 정보.

### 설치 및 구성

다음을 포함하여 Adobe Commerce 및 Magento Open Source을 다운로드하는 방법이 여러 가지가 있습니다.

* [작성기 메타카드 가져오기](../../composer.md)

* [Git 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

이 예는 명령줄을 사용하여 작성기 기반 설치를 보여 줍니다.

1. 로서의 [파일 시스템 소유자](../file-system/overview.md)를 눌러 애플리케이션 서버에 로그인합니다.

1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다. 이 예에서는 Ubuntu 기본값을 사용합니다 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 전체적으로 Composer를 설치합니다. Adobe Commerce 또는 Magento Open Source을 설치하기 전에 작성기가 종속성을 업데이트해야 합니다.

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open Source 또는 Adobe Commerce 메타패키지를 사용하여 작성기 프로젝트를 만듭니다.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   메시지가 표시되면 을 입력합니다 [인증 키](../authentication-keys.md). 사용자 _공개 키_ 사용자 이름 your _개인 키_ 은 암호입니다.

1. 응용 프로그램을 설치하기 전에 웹 서버 그룹에 대한 읽기-쓰기 권한을 설정합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 이 작업이 필요합니다.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 에서 설치 [명령줄](../../advanced.md). 이 예에서는 설치 디렉토리의 이름이 인 것으로 가정합니다 `magento2ee`, `db-host` 이(가) 동일한 시스템에 있습니다.`localhost`) 및 `db-name`, `db-user`, 및 `db-password` 모두 `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. 개발자 모드로 전환:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### nginx 구성

를 사용하여 nginx를 구성하는 것이 좋습니다 `nginx.conf.sample` 설치 디렉터리 및 nginx 가상 호스트에 제공된 구성 파일입니다.

이러한 지침은 nginx 가상 호스트에 Ubuntu 기본 위치를 사용하고 있다고 가정합니다(예: `/etc/nginx/sites-available`) 및 Ubuntu 기본 docroot(예: `/var/www/html`)의 경우 이러한 위치를 환경에 맞게 변경할 수 있습니다.

1. 사이트에 대한 새 가상 호스트 만들기:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 다음 구성을 추가합니다.

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >다음 `include` 지시문은 설치 디렉토리에 있는 샘플 nginx 구성 파일을 가리켜야 합니다.

1. 바꾸기 `www.magento-dev.com` 도메인 이름 포함. Adobe Commerce 또는 Magento Open Source을 설치할 때 지정한 기본 URL과 일치해야 합니다.

1. 편집기를 저장하고 종료합니다.

1. 에서 새 가상 호스트에 대한 symlink를 만들어 새로 만든 가상 호스트를 활성화합니다 `/etc/nginx/sites-enabled` 디렉토리:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 구문이 올바른지 확인합니다.

   ```bash
   nginx -t
   ```

1. ninx를 다시 시작합니다.

   ```bash
   systemctl restart nginx
   ```

### 설치 확인

웹 브라우저를 열고 사이트의 기본 URL로 이동합니다 [설치 확인](../../next-steps/verify.md).

## CentOS 7

다음 섹션에서는 nginx, PHP 및 MySQL을 사용하여 CentOS 7에 Adobe Commerce 및 Magento Open Source 2.x를 설치하는 방법을 설명합니다.

### nginx 설치

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

설치가 완료되면 ninx를 시작하고 부트 시 시작하도록 구성합니다.

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

다음 섹션을 완료하고 애플리케이션을 설치한 후 샘플 구성 파일을 사용하여 ninx를 구성합니다.

### php-fpm 설치 및 구성

Adobe Commerce 및 Magento Open Source은 몇 가지가 필요합니다 [PHP](../php-settings.md) 확장이 제대로 작동하는지 확인합니다. 이러한 확장 외에 를 설치하고 구성해야 합니다 `php-fpm` nginx를 사용하는 경우 확장하십시오.

1. 설치 `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. 를 엽니다. `/etc/php.ini` 파일을 편집기에 저장합니다.

1. 주석 처리를 취소합니다 `cgi.fix_pathinfo` 라인 및 값 변경 `0`.

1. 다음 줄과 일치하도록 파일을 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe Commerce 또는 Magento Open Source을 테스트할 때 메모리 제한을 2G로 설정하는 것이 좋습니다. 을(를) 참조하십시오. [필수 PHP 설정](../php-settings.md) 추가 정보.

1. 세션 경로 디렉토리의 주석을 해제하고 경로를 설정합니다.

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 편집기를 저장하고 종료합니다.

1. 열기 `/etc/php-fpm.d/www.conf` 참조하십시오.

1. 다음 줄과 일치하도록 파일을 편집합니다.

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 환경 라인의 주석 처리를 취소합니다.

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 편집기를 저장하고 종료합니다.

1. PHP 세션 경로에 대한 디렉터리를 만들고 소유자를 `apache` 사용자 및 그룹:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. PHP 세션 경로에 대한 디렉터리를 만들고 소유자를 `apache` 사용자 및 그룹:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. 시작 `php-fpm` 서비스를 사용하여 부팅 시 시작하도록 구성합니다.

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. 다음 사항을 확인합니다. `php-fpm` 서비스가 실행 중입니다.

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQL 설치 및 구성

을(를) 참조하십시오. [MySQL](..//database/mysql.md) 추가 정보.

### 설치 및 구성

다음을 포함하여 Adobe Commerce 및 Magento Open Source을 다운로드하는 방법이 여러 가지가 있습니다.

* [작성기 메타카드 가져오기](../../composer.md)

* [Git 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

이 예는 명령줄을 사용하여 작성기 기반 설치를 보여 줍니다.

1. 로서의 [파일 시스템 소유자](../file-system/overview.md)를 눌러 애플리케이션 서버에 로그인합니다.

1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다. 이 예에서는 Ubuntu 기본값을 사용합니다 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 전체적으로 Composer를 설치합니다. Adobe Commerce 또는 Magento Open Source을 설치하기 전에 작성기가 종속성을 업데이트해야 합니다.

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open Source 또는 Adobe Commerce 메타패키지를 사용하여 작성기 프로젝트를 만듭니다.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   메시지가 표시되면 을 입력합니다 [인증 키](../authentication-keys.md). 사용자 _공개 키_ 사용자 이름 your _개인 키_ 은 암호입니다.

1. 응용 프로그램을 설치하기 전에 웹 서버 그룹에 대한 읽기-쓰기 권한을 설정합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 이 작업이 필요합니다.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 에서 설치 [명령줄](../../advanced.md). 이 예에서는 설치 디렉토리의 이름이 인 것으로 가정합니다 `magento2ee`, `db-host` 이(가) 동일한 시스템에 있습니다.`localhost`) 및 `db-name`, `db-user`, 및 `db-password` 모두 `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 개발자 모드로 전환:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### nginx 구성

를 사용하여 nginx를 구성하는 것이 좋습니다 `nginx.conf.sample` 설치 디렉터리 및 nginx 가상 호스트에 제공된 구성 파일입니다.

이러한 지침은 Nginx 가상 호스트에 CentOS 기본 위치를 사용하고 있다고 가정합니다(예: `/etc/nginx/conf.d`) 및 기본 docroot(예: `/usr/share/nginx/html`)의 경우 이러한 위치를 환경에 맞게 변경할 수 있습니다.

1. 사이트에 대한 새 가상 호스트 만들기:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. 다음 구성을 추가합니다.

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >다음 `include` 지시문은 설치 디렉토리에 있는 샘플 nginx 구성 파일을 가리켜야 합니다.

1. 바꾸기 `www.magento-dev.com` 도메인 이름 포함.

1. 편집기를 저장하고 종료합니다.

1. 구문이 올바른지 확인합니다.

   ```bash
   nginx -t
   ```

1. ninx를 다시 시작합니다.

   ```bash
   systemctl restart nginx
   ```

### SELinux 및 Firewald 구성

SelInux는 CentOS 7에서 기본적으로 활성화됩니다. 실행 중인지 확인하려면 다음 명령을 사용하십시오.

```bash
sestatus
```

SELinux 및 firewall을 구성하려면 다음을 수행합니다.

1. SELinux 관리 도구 설치:

   ```bash
   yum -y install policycoreutils-python
   ```

1. 다음 명령을 실행하여 설치 디렉토리에 대한 보안 컨텍스트를 변경합니다.

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. firewald 패키지를 설치합니다.

   ```bash
   yum -y install firewalld
   ```

1. 방화벽 서비스를 시작하고 부팅 시 시작하도록 구성합니다.

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 다음 명령을 실행하여 웹 브라우저에서 기본 URL에 액세스할 수 있도록 HTTP 및 HTTPS용 포트를 엽니다.

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### 설치 확인

웹 브라우저를 열고 사이트의 기본 URL로 이동합니다 [설치 확인](../../next-steps/verify.md).
