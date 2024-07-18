---
title: 업그레이드를 위한 유지 관리 모드 옵션
description: 업그레이드를 실행하는 동안 고객이 Adobe Commerce 상점 첫 화면에서 볼 수 있는 사용자 지정 유지 관리 모드 페이지를 만듭니다.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 업그레이드를 위한 유지 관리 모드 옵션

이 항목에서는 Magento 응용 프로그램을 업그레이드하는 동안 사용자에게 표시할 사용자 지정 유지 관리 페이지를 만드는 방법에 대해 설명합니다. 사용자 지정 페이지 만들기는 선택 사항이지만 업그레이드 과정에서 사이트에 액세스할 수 있으므로 권장됩니다.

사용자를 리디렉션할 사용자 지정 페이지를 만들면 사이트에 대한 액세스가 차단되고 사이트가 유지 관리 중임을 사용자에게 알립니다.

>[!NOTE]
>
>`root` 권한이 있는 사용자로 이 섹션의 작업을 수행해야 합니다. 개발자 모드에서는 사용자 지정 유지 관리 페이지를 설정할 수 없습니다.

## 사용자 지정 유지 관리 페이지 만들기

유지 관리 페이지를 만들고 리디렉션하려면 먼저 다음 이름의 유지 관리 페이지를 만듭니다.

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

다음 내용을 추가합니다.

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Apache의 사용자 지정 유지 관리 페이지

이 섹션에서는 사용자 지정 유지 관리 페이지를 만드는 방법과 트래픽을 리디렉션하는 방법에 대해 설명합니다.

이 섹션의 예에서는 유지 관리 페이지를 설정하는 한 가지 방법인 다음 파일을 수정하는 방법을 보여 줍니다.

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default`(Ubuntu), `/etc/httpd/conf/httpd.conf`(CentOS)

트래픽을 사용자 지정 유지 관리 페이지로 리디렉션하려면 다음을 수행하십시오.

1. Apache 구성을 업데이트하여 다음 작업을 수행합니다.

   - 모든 트래픽을 유지 관리 페이지로 리디렉션
   - 허용 목록에 추가하다 특정 IP를 업그레이드하여 관리자가 Magento 소프트웨어를 업그레이드할 수 있습니다.

   다음 예제 허용 목록 192.0.2.110입니다.

   Apache 구성 파일의 끝에 다음 내용을 추가합니다.

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Apache 다시 시작:

   - CentOS: `service httpd restart`
   - 우분투: `service apache2 restart`

1. 다음 명령을 입력합니다.

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [시스템을 업그레이드합니다](../implementation/perform-upgrade.md).
1. 사이트가 올바르게 작동하는지 테스트합니다.
1. 업그레이드가 완료되면 `maintenance.enable`을(를) 삭제합니다.

## nginx에 대한 사용자 지정 유지 관리 페이지

이 섹션에서는 사용자 지정 유지 관리 페이지를 만드는 방법과 트래픽을 리디렉션하는 방법에 대해 설명합니다.

트래픽을 사용자 지정 유지 관리 페이지로 리디렉션하려면 다음을 수행하십시오.

1. 텍스트 편집기를 사용하여 서버 블록이 포함된 nginx 구성 파일을 엽니다.
1. 서버 블록에 다음 내용을 추가하십시오. `server`은(는) 명확하게 하기 위해서만 표시되며, 두 번째 서버 블록은 추가하지 마십시오.

   `/var/www/html/magento2`에 Magento이 설치된 시스템의 다음 허용 목록 IP 주소 192.0.2.110 및 192.0.2.115:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 다음 명령을 입력합니다.

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. nginx 구성을 다시 로드합니다.

   ```bash
   service nginx reload
   ```

1. [시스템을 업그레이드합니다](../implementation/perform-upgrade.md).
1. 사이트가 올바르게 작동하는지 테스트합니다.
1. 업그레이드가 완료되면 `maintenance.enable`을(를) 삭제하거나 이름을 바꾸십시오.
1. nginx 구성을 다시 로드합니다.

   ```bash
   service nginx reload
   ```
