---
title: 온-프레미스 배포용 Nginx 설치
description: 온-프레미스 Adobe Commerce 배포용 Nginx 웹 서버를 설치하고 구성하는 방법에 대해 알아봅니다. PHP-FPM 및 가상 호스트를 설정합니다.
feature: Install, Configuration
badgePaas: label="온-프레미스" type="Informative" url="https://experienceleague.adobe.com/ko/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온-프레미스 프로젝트에만 적용됩니다."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# 온-프레미스 배포용 Nginx 설치 {#nginx}

이 안내서에서는 Adobe Commerce 온-프레미스 배포용 Ngix를 설치하고 Commerce에 필요한 Ngix 설정을 구성하는 방법을 안내합니다. 여기에는 PHP-FPM 구성을 위한 지침과 함께 Ubuntu 및 CentOS에 대한 운영 체제별 절차가 포함되어 있습니다. Adobe은 이 안내서에 제공된 구성 지침을 따라 Commerce 애플리케이션의 기능과 보안을 모두 유지하는 것을 권장합니다.

Adobe은 Adobe Commerce 릴리스의 [시스템 요구 사항](../../system-requirements.md)에 나열된 Nginx 버전을 지원합니다. 지원되는 버전은 릴리스에 따라 다릅니다. Nginx에도 지원되는 PHP-FPM 구성이 필요합니다. 관련 PHP 요구 사항은 [PHP](../php-settings.md)을 참조하십시오.

## Ubuntu에 설치

이 섹션을 사용하여 Nginx, PHP 및 MySQL이 있는 Ubuntu에 Adobe Commerce을 설치합니다.

### Nginx 설치

```bash
sudo apt -y install nginx
```

[소스에서 Nginx를 빌드](https://www.armanism.com/blog/install-nginx-on-ubuntu)할 수도 있습니다.

다음 섹션을 완료하고 응용 프로그램을 설치한 후 샘플 구성 파일을 사용하여 [Nginx를 구성](#configure-nginx)합니다. 이 권장 구성은 Commerce 애플리케이션의 기능과 보안을 모두 유지합니다.

### PHP-FPM 설치 및 구성

Adobe Commerce이 제대로 작동하려면 여러 [PHP 확장](../php-settings.md)이 필요합니다. Nginx를 사용하는 경우 이러한 확장 외에도 `php-fpm` 확장 프로그램을 설치하고 구성해야 합니다.

`php-fpm`을(를) 설치하고 구성하려면:

1. Adobe Commerce 릴리스에서 지원하는 PHP 버전용 `php-fpm` 및 `php-cli` 패키지를 설치하십시오. Ubuntu에서 패키지 이름은 일반적으로 다음 패턴을 따릅니다.

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >`<php-version>`을(를) 설치 중인 Adobe Commerce 릴리스의 [시스템 요구 사항](../../system-requirements.md)에 나열된 지원되는 PHP 부 버전으로 바꾸십시오. 다음 단계에서 파일 경로, 서비스 이름 및 소켓 경로에 동일한 값을 사용합니다.

1. 편집기에서 `php.ini` 파일을 엽니다.

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. 다음 라인과 일치하도록 두 파일을 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe은 Adobe Commerce을 테스트할 때 메모리 제한을 2GB로 설정하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../php-settings.md)을 참조하세요.

1. 저장하고 편집기를 종료합니다.

1. `php-fpm` 서비스 다시 시작:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### MySQL 설치 및 구성

자세한 내용은 [MySQL](../database/mysql.md)을 참조하세요.

### Adobe Commerce 설치

다음과 같은 여러 가지 방법으로 Adobe Commerce을 다운로드할 수 있습니다.

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

1. [명령줄](../../advanced.md)에서 설치합니다. 이 예제에서는 설치 디렉터리 이름이 `magento2ee`이고 데이터베이스 호스트가 동일한 컴퓨터(`localhost`)에 있다고 가정합니다.

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >설치 중인 Adobe Commerce 릴리스에 필요한 `--search-engine` 값과 일치하는 호스트/포트 옵션을 사용하십시오. 2.4.6 이전 버전의 경우 Elasticsearch 7 또는 OpenSearch용 `elasticsearch7` 옵션과 함께 `--elasticsearch-*`을(를) 사용합니다. 버전 2.4.6 이상의 경우 해당 릴리스에서 지원하는 검색 엔진 값 및 해당 CLI 옵션을 사용하십시오.

1. 개발자 모드로 전환:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx 구성

Adobe에서는 Commerce 응용 프로그램의 기능과 보안을 모두 유지하기 위해 설치 디렉터리와 Nginx 가상 호스트 구성에 제공된 `nginx.conf.sample` 구성 파일을 사용하여 Nginx를 구성할 것을 권장합니다.

>[!IMPORTANT]
>
>`nginx.conf.sample` 파일은 필요한 응용 프로그램 라우팅과 보안 강화 규칙을 제공합니다. 예를 들어 서버에 업로드된 유해 스크립트의 실행을 제한합니다. 이 파일을 사용하지 않거나 해당 규칙을 수정하지 않는 경우 사용자 지정 nginx 구성에서 동일한 보안 컨트롤을 구현해야 합니다.

이 지침에서는 Nginx 가상 호스트(예: `/etc/nginx/sites-available`)에 대해 Ubuntu 기본 위치를 사용하고 Ubuntu 기본 docroot(예: `/var/www/html`)를 사용하고 있다고 가정합니다. 이러한 위치를 환경에 맞게 변경할 수 있습니다.

1. 사이트에 대한 새 가상 호스트를 만듭니다.

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 다음 구성을 추가합니다.

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
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

1. Nginx 다시 시작:

   ```bash
   systemctl restart nginx
   ```

### 설치 확인

설치를 확인하려면 웹 브라우저를 열고 사이트의 기본 URL로 이동합니다. 자세한 내용은 [설치 확인](../../next-steps/verify.md)을 참조하세요.

## CentOS 7에 설치

이 섹션을 사용하여 Nginx, PHP 및 MySQL이 있는 CentOS 7에 Adobe Commerce을 설치합니다.

### Nginx 설치

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

다음 섹션을 완료하고 응용 프로그램을 설치한 후 샘플 구성 파일을 사용하여 Nginx를 구성합니다.

### PHP-FPM 설치 및 구성

Adobe Commerce이 제대로 작동하려면 여러 [PHP](../php-settings.md) 확장이 필요합니다. Nginx를 사용하는 경우 이러한 확장 외에도 `php-fpm` 확장 프로그램을 설치하고 구성해야 합니다.

1. `php-fpm` 설치:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. 편집기에서 `/etc/php.ini` 파일을 엽니다.

   >[!NOTE]
   >
   >설치 중인 Adobe Commerce 릴리스에서 지원하는 PHP 버전에 대해 `php-fpm`을(를) 제공하는 패키지를 설치하십시오. 패키지 이름은 저장소 및 운영 체제에 따라 다릅니다. [시스템 요구 사항](../../system-requirements.md)을 참조하세요.

1. `cgi.fix_pathinfo` 줄의 주석 처리를 제거하고 값을 `0`(으)로 변경합니다.

1. 다음 행과 일치하도록 파일을 편집합니다.

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe은 Adobe Commerce을 테스트할 때 메모리 제한을 2GB로 설정하는 것이 좋습니다. 자세한 내용은 [필수 PHP 설정](../php-settings.md)을 참조하세요.

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

1. PHP 세션 경로에 대한 디렉터리를 만들고 소유자를 `nginx` 사용자 및 그룹으로 변경합니다.

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. PHP-FPM 소켓에 대한 디렉터리를 만들고 소유자를 `nginx` 사용자 및 그룹으로 변경합니다.

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
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

자세한 내용은 [MySQL](../database/mysql.md)을 참조하세요.

### Adobe Commerce 설치

다음과 같은 여러 가지 방법으로 Adobe Commerce을 다운로드할 수 있습니다.

* [Composer 메타패키지 가져오기](../../composer.md)

* [git 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

이 예에서는 명령줄을 사용한 작성기 기반 설치를 보여 줍니다.

1. [파일 시스템 소유자](../file-system/overview.md)(으)로 응용 프로그램 서버에 로그인합니다.

1. 웹 서버 docroot 디렉토리 또는 가상 호스트 docroot로 구성한 디렉토리로 변경합니다. 이 예제에서는 CentOS 기본값 `/usr/share/nginx/html`을(를) 사용합니다.

   ```bash
   cd /usr/share/nginx/html
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
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. [명령줄](../../advanced.md)에서 설치합니다. 이 예제에서는 설치 디렉터리 이름이 `magento2ee`이고 데이터베이스 호스트가 동일한 컴퓨터(`localhost`)에 있다고 가정합니다.

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 개발자 모드로 전환:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx 구성

설치 디렉터리의 `nginx.conf.sample` 파일과 Nginx 가상 호스트 구성을 사용하여 Nginx를 구성하는 것이 좋습니다.

>[!IMPORTANT]
>
>`nginx.conf.sample` 파일은 필요한 응용 프로그램 라우팅과 보안 강화 규칙을 제공합니다. 예를 들어 서버에 업로드된 유해 스크립트의 실행을 제한합니다. 이 파일을 사용하지 않거나 해당 규칙을 수정하지 않는 경우 사용자 지정 nginx 구성에서 동일한 보안 컨트롤을 구현해야 합니다.

이러한 지침은 Nginx 가상 호스트(예: `/etc/nginx/conf.d`)에 대해 CentOS 기본 위치를 사용하고 있으며 기본 docroot(예: `/usr/share/nginx/html`)를 사용하고 있다고 가정합니다. 이러한 위치를 환경에 맞게 변경할 수 있습니다.

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

1. Nginx 다시 시작:

   ```bash
   systemctl restart nginx
   ```

### SELinux 및 firewalld 구성

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

설치를 확인하려면 웹 브라우저를 열고 사이트의 기본 URL로 이동합니다. 자세한 내용은 [설치 확인](../../next-steps/verify.md)을 참조하세요.
