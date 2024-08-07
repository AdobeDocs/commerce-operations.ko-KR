---
title: 보안을 향상하도록 docroot 수정
description: Adobe Commerce 온-프레미스 파일 시스템에 대한 무단 브라우저 기반 액세스를 차단합니다.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# 보안을 향상하도록 docroot 수정

Apache 웹 서버가 있는 표준 설치에서 Adobe Commerce은 기본 웹 루트 `/var/www/html/magento2`에 설치됩니다.

`magento2/` 디렉터리에는 다음 항목이 포함되어 있습니다.

- `pub/`
- `setup/`
- `var/`

응용 프로그램이 `/var/www/html/magento2/pub`에서 제공됩니다. 나머지 파일 시스템은 브라우저에서 액세스할 수 있으므로 취약합니다.
webroot를 `pub/` 디렉터리로 설정하면 사이트 방문자가 브라우저에서 파일 시스템의 중요한 영역에 액세스하지 못합니다.

이 항목에서는 보다 안전한 `pub/` 디렉터리에서 파일을 제공하도록 기존 인스턴스의 Apache docroot를 변경하는 방법에 대해 설명합니다.

## nginx에 대한 참고 사항

설치 디렉터리에 포함된 [nginx](../prerequisites/web-server/nginx.md) 및 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 파일을 사용하는 경우 `pub/` 디렉터리에서 파일을 이미 제공하고 있을 수 있습니다.

사이트를 정의하는 서버 블록에서 사용하는 경우 `nginx.conf.sample` 구성은 서버의 docroot 설정을 재정의하여 `pub/` 디렉터리의 파일을 제공합니다. 예를 들어 다음 구성의 마지막 줄을 참조하십시오.

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## 시작하기 전에

이 자습서를 완료하려면 LAMP 스택에서 실행되는 작업 설치에 액세스해야 합니다.

- 리눅스
- Apache (2.4+)
- MySQL(5.7+)
- PHP (7.4)
- Elasticsearch(7.x) 또는 OpenSearch(1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>자세한 내용은 [필수 구성 요소](../prerequisites/overview.md) 및 [설치 안내서](../overview.md)를 참조하십시오.

## 1. 서버 구성 편집

가상 호스트 파일의 이름과 위치는 실행 중인 Apache 버전에 따라 다릅니다. 이 예는 Apache v2.4에서 가상 호스트 파일의 이름과 위치를 보여 줍니다.

1. 애플리케이션 서버에 로그인합니다.
1. 가상 호스트 파일 편집:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. `pub/` 디렉터리의 경로를 `DocumentRoot` 지시문에 추가합니다.

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Apache 다시 시작:

   ```bash
   systemctl restart apache2
   ```

## 2. 기본 URL 업데이트

응용 프로그램을 설치할 때 기본 URL을 만들기 위해 서버의 호스트 이름 또는 IP 주소에 디렉터리 이름을 추가한 경우(예: `http://192.168.33.10/magento2`) 이를 제거해야 합니다.

>[!NOTE]
>
>`192.168.33.10`을(를) 서버의 호스트 이름으로 바꾸십시오.

1. 데이터베이스에 로그인:

   ```bash
   mysql -u <user> -p
   ```

1. 응용 프로그램을 설치할 때 만든 데이터베이스를 지정합니다.

   ```shell
   use <database-name>
   ```

1. 기본 URL 업데이트:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. env.php 파일 업데이트

`env.php` 파일에 다음 노드를 추가합니다.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

자세한 내용은 [env.php 참조](../../configuration/reference/config-reference-envphp.md)를 참조하십시오.

## 4. 모드 전환

`production` 및 `developer`을(를) 포함하는 [응용 프로그램 모드](../../configuration/bootstrap/application-modes.md)은(는) 보안을 강화하고 개발을 더 쉽게 하도록 설계되었습니다. 이름을 통해 알 수 있듯이 응용 프로그램을 확장하거나 사용자 지정할 때는 `developer` 모드로 전환하고, 라이브 환경에서 실행할 때는 `production` 모드로 전환해야 합니다.

모드 간 전환은 서버 구성이 제대로 작동하는지 확인하는 중요한 단계입니다. CLI 도구를 사용하여 모드 간에 전환할 수 있습니다.

1. 설치 디렉토리로 이동합니다.
1. `production` 모드로 전환합니다.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 브라우저를 새로 고치고 상점 전면이 제대로 표시되는지 확인하십시오.
1. `developer` 모드로 전환합니다.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 브라우저를 새로 고치고 상점 전면이 제대로 표시되는지 확인하십시오.

## 5. 상점 첫 화면 확인

웹 브라우저의 상점 앞으로 이동하여 모든 것이 제대로 작동하는지 확인하십시오.

1. 웹 브라우저를 열고 주소 표시줄에 서버의 호스트 이름 또는 IP 주소를 입력합니다. 예: `http://192.168.33.10`.

   다음 그림은 샘플 상점 첫 페이지를 보여줍니다. 다음과 같이 표시된다면 설치가 성공적으로 완료되었습니다.

   ![설치를 확인하는 Storefront](../../assets/installation/install-success_store.png)

   페이지에 404(찾을 수 없음)가 표시되거나 이미지, CSS 및 JS와 같은 다른 자산을 로드하지 못하는 경우 [문제 해결 섹션](https://support.magento.com/hc/en-us/articles/360032994352)을 참조하세요.

1. 브라우저에서 응용 프로그램 디렉터리에 액세스해 보십시오. 주소 표시줄에서 서버의 호스트 이름 또는 IP 주소에 디렉터리 이름을 추가합니다.

   404 또는 &quot;액세스 거부&quot; 메시지가 표시되면 파일 시스템에 대한 액세스를 제한한 것입니다.

   ![액세스 거부됨](../../assets/installation/access-denied.png)
