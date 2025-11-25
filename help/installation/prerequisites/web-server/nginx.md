---
title: Ngix
description: Adobe Commerce의 온-프레미스 설치를 위한 Nginx 웹 서버를 설치하고 구성하려면 다음 단계를 따르십시오.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Ngix

Adobe Commerce은 nginx 1.x(또는 [최신 메인라인 버전](https://nginx.org/en/linux_packages.html#mainline))를 지원합니다. 최신 버전의 `php-fpm`도 설치해야 합니다.

설치 지침은 사용 중인 운영 체제에 따라 다릅니다. 자세한 내용은 [PHP](../php-settings.md)을 참조하세요.

## 우분투

다음 섹션에서는 nginx, PHP 및 MySQL을 사용하여 Ubuntu에 Adobe Commerce 2.x를 설치하는 방법에 대해 설명합니다.

### nginx 설치

```bash
sudo apt -y install nginx
```

[소스에서 nginx를 빌드](https://www.armanism.com/blog/install-nginx-on-ubuntu)할 수도 있습니다.

다음 섹션을 완료하고 응용 프로그램을 설치한 후 샘플 구성 파일을 사용하여 [nginx를 구성](#configure-nginx)합니다.

### php-fpm 설치 및 구성

Adobe Commerce이 제대로 작동하려면 여러 [PHP 확장](../php-settings.md)이 필요합니다. nginx를 사용하는 경우 이러한 확장 외에도 `php-fpm` 확장 프로그램을 설치하고 구성해야 합니다.

`php-fpm`을(를) 설치하고 구성하려면:

1. `php-fpm` 및 `php-cli` 설치:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >이 명령은 사용 가능한 최신 버전의 PHP 7.2.X를 설치합니다. 지원되는 PHP 버전은 [시스템 요구 사항](../../system-requirements.md)을 참조하십시오.

1. 편집기에서 `php.ini` 파일을 엽니다.

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 다음 라인과 일치하도록 두 파일을 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe Commerce을 테스트할 때 메모리 제한을 2G로 설정하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../php-settings.md)을 참조하세요.

1. 저장하고 편집기를 종료합니다.

1. `php-fpm` 서비스 다시 시작:

   ```bash
   systemctl restart php7.2-fpm
   ```

### MySQL 설치 및 구성

자세한 내용은 [MySQL](../database/mysql.md)을 참조하세요.

### 설치 및 구성

Adobe Commerce을 다운로드하는 방법에는 다음을 포함하여 몇 가지가 있습니다.

* [Composer 메타패키지 가져오기](../../composer.md)

* [git 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

이 예에서는 명령줄을 사용한 작성기 기반 설치를 보여 줍니다.

1. [파일 시스템 소유자](../file-system/overview.md)(으)로 응용 프로그램 서버에 로그인합니다.

1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다. 이 예제에서는 Ubuntu 기본 `/var/www/html`을(를) 사용합니다.

   ```bash
   cd /var/www/html
   ```

1. Composer를 전체적으로 설치합니다. Composer는 Adobe Commerce을 설치하기 전에 종속성을 업데이트해야 합니다.

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Adobe Commerce 메타패키지를 사용하여 작성기 프로젝트를 만듭니다.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   메시지가 표시되면 [인증 키](../authentication-keys.md)를 입력하십시오. _공개 키_&#x200B;은(는) 사용자 이름이고 _개인 키_&#x200B;은(는) 암호입니다.

1. 응용 프로그램을 설치하기 전에 웹 서버 그룹에 대한 읽기/쓰기 권한을 설정합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 해야 합니다.

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

1. [명령줄](../../advanced.md)에서 설치합니다. 이 예제에서는 설치 디렉터리 이름이 `magento2ee`이고 `db-host`이(가) 같은 컴퓨터(`localhost`)에 있으며 `db-name`, `db-user` 및 `db-password`이(가) 모두 `magento`이라고 가정합니다.

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

설치 디렉터리 및 nginx 가상 호스트에 제공된 `nginx.conf.sample` 구성 파일을 사용하여 nginx를 구성하는 것이 좋습니다.

이 지침은 nginx 가상 호스트(예: `/etc/nginx/sites-available`)에 대해 Ubuntu 기본 위치를 사용하고 있고 Ubuntu 기본 docroot(예: `/var/www/html`)도 사용하고 있다고 가정하지만, 사용자 환경에 맞게 이러한 위치를 변경할 수 있습니다.

1. 사이트에 대한 새 가상 호스트를 만듭니다.

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
   >`include` 지시문은 설치 디렉터리의 샘플 nginx 구성 파일을 가리켜야 합니다.

1. `www.magento-dev.com`을(를) 도메인 이름으로 바꾸십시오. 이 URL은 Adobe Commerce 설치 시 지정한 기본 URL과 일치해야 합니다.

1. 저장하고 편집기를 종료합니다.

1. `/etc/nginx/sites-enabled` 디렉터리에 symlink를 만들어 새로 만든 가상 호스트를 활성화합니다.

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 구문이 올바른지 확인합니다.

   ```bash
   nginx -t
   ```

1. nginx 다시 시작:

   ```bash
   systemctl restart nginx
   ```

### 설치 확인

웹 브라우저를 열고 사이트의 기본 URL로 이동하여 [설치를 확인](../../next-steps/verify.md)합니다.

## 센트OS 7

다음 섹션에서는 nginx, PHP 및 MySQL을 사용하여 CentOS 7에 Adobe Commerce 2.x를 설치하는 방법을 설명합니다.

### nginx 설치

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

설치가 완료되면 ngix를 시작하고 부팅 시 시작되도록 구성합니다.

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

다음 섹션을 완료하고 애플리케이션을 설치한 후 샘플 구성 파일을 사용하여 nginx를 구성하겠습니다.

### php-fpm 설치 및 구성

Adobe Commerce이 제대로 작동하려면 여러 [PHP](../php-settings.md) 확장이 필요합니다. nginx를 사용하는 경우 이러한 확장 외에도 `php-fpm` 확장 프로그램을 설치하고 구성해야 합니다.

1. `php-fpm` 설치:

   ```bash
   yum -y install php70w-fpm
   ```

1. 편집기에서 `/etc/php.ini` 파일을 엽니다.

1. `cgi.fix_pathinfo` 줄의 주석 처리를 제거하고 값을 `0`(으)로 변경합니다.

1. 다음 행과 일치하도록 파일을 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe Commerce을 테스트할 때 메모리 제한을 2G로 설정하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../php-settings.md)을 참조하세요.

1. 세션 경로 디렉토리의 주석 처리를 제거하고 경로를 설정합니다.

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 저장하고 편집기를 종료합니다.

1. 편집기에서 `/etc/php-fpm.d/www.conf` 열기

1. 다음 행과 일치하도록 파일을 편집합니다.

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 환경 라인의 주석 처리를 제거합니다.

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 저장하고 편집기를 종료합니다.

1. PHP 세션 경로에 대한 디렉터리를 만들고 소유자를 `apache` 사용자 및 그룹으로 변경합니다.

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. PHP 세션 경로에 대한 디렉터리를 만들고 소유자를 `apache` 사용자 및 그룹으로 변경합니다.

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. `php-fpm` 서비스를 시작하고 부팅 시 시작되도록 구성하십시오.

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. `php-fpm` 서비스가 실행 중인지 확인합니다.

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQL 설치 및 구성

자세한 내용은 [MySQL](..//database/mysql.md)을 참조하세요.

### 설치 및 구성

Adobe Commerce을 다운로드하는 방법에는 다음을 포함하여 몇 가지가 있습니다.

* [Composer 메타패키지 가져오기](../../composer.md)

* [git 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

이 예에서는 명령줄을 사용한 작성기 기반 설치를 보여 줍니다.

1. [파일 시스템 소유자](../file-system/overview.md)(으)로 응용 프로그램 서버에 로그인합니다.

1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다. 이 예제에서는 Ubuntu 기본 `/var/www/html`을(를) 사용합니다.

   ```bash
   cd /var/www/html
   ```

1. Composer를 전체적으로 설치합니다. Composer는 Adobe Commerce을 설치하기 전에 종속성을 업데이트해야 합니다.

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Adobe Commerce 메타패키지를 사용하여 작성기 프로젝트를 만듭니다.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   메시지가 표시되면 [인증 키](../authentication-keys.md)를 입력하십시오. _공개 키_&#x200B;은(는) 사용자 이름이고 _개인 키_&#x200B;은(는) 암호입니다.

1. 응용 프로그램을 설치하기 전에 웹 서버 그룹에 대한 읽기/쓰기 권한을 설정합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 해야 합니다.

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

1. [명령줄](../../advanced.md)에서 설치합니다. 이 예제에서는 설치 디렉터리 이름이 `magento2ee`이고 `db-host`이(가) 같은 컴퓨터(`localhost`)에 있으며 `db-name`, `db-user` 및 `db-password`이(가) 모두 `magento`이라고 가정합니다.

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

설치 디렉터리 및 nginx 가상 호스트에 제공된 `nginx.conf.sample` 구성 파일을 사용하여 nginx를 구성하는 것이 좋습니다.

이러한 지침에서는 nginx 가상 호스트(예: `/etc/nginx/conf.d`)와 기본 docroot(예: `/usr/share/nginx/html`)에 대해 CentOS 기본 위치를 사용하고 있다고 가정하지만 환경에 맞게 이러한 위치를 변경할 수 있습니다.

1. 사이트에 대한 새 가상 호스트를 만듭니다.

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
   >`include` 지시문은 설치 디렉터리의 샘플 nginx 구성 파일을 가리켜야 합니다.

1. `www.magento-dev.com`을(를) 도메인 이름으로 바꾸십시오.

1. 저장하고 편집기를 종료합니다.

1. 구문이 올바른지 확인합니다.

   ```bash
   nginx -t
   ```

1. nginx 다시 시작:

   ```bash
   systemctl restart nginx
   ```

### SELinux 및 Firewalld 구성

SELinux는 CentOS 7에서 기본적으로 활성화됩니다. 다음 명령을 사용하여 실행 중인지 확인하십시오.

```bash
sestatus
```

SELinux 및 firewall을 구성하려면 다음을 수행합니다.

1. SELinux 관리 도구를 설치합니다.

   ```bash
   yum -y install policycoreutils-python
   ```

1. 다음 명령을 실행하여 설치 디렉토리의 보안 컨텍스트를 변경합니다.

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

1. Firewalld 패키지를 설치합니다.

   ```bash
   yum -y install firewalld
   ```

1. 방화벽 서비스를 시작하고 부팅 시 시작되도록 구성합니다.

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 웹 브라우저에서 기본 URL에 액세스할 수 있도록 다음 명령을 실행하여 HTTP 및 HTTPS용 포트를 엽니다.

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

웹 브라우저를 열고 사이트의 기본 URL로 이동하여 [설치를 확인](../../next-steps/verify.md)합니다.
