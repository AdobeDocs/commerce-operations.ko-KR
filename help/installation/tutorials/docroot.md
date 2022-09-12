---
title: 보안을 향상하기 위해 docroot 수정
description: Adobe Commerce 또는 Magento Open Source 온-프레미스 파일 시스템에 대한 권한 없는 브라우저 기반 액세스를 차단합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# 보안을 향상하기 위해 docroot 수정

Apache 웹 서버가 있는 표준 설치에서는 Adobe Commerce 및 Magento Open Source이 기본 웹 루트에 설치됩니다. `/var/www/html/magento2`.

다음 `magento2/` 디렉토리에는 다음이 포함됩니다.

- `pub/`
- `setup/`
- `var/`

응용 프로그램은 `/var/www/html/magento2/pub`. 나머지 파일 시스템은 브라우저에서 액세스할 수 있으므로 취약합니다.
웹 로드를 `pub/` 디렉토리는 사이트 방문자가 브라우저에서 파일 시스템의 중요한 영역에 액세스하지 못하도록 합니다.

이 항목에서는 기존 인스턴스에서 Apache docroot를 변경하여 `pub/` 디렉토리. 더 안전합니다.

## nginx에 대한 참고 사항

사용 중인 경우 [nginx](../prerequisites/web-server/nginx.md) 그리고 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 설치 디렉터리에 포함된 파일은 이미 `pub/` 디렉토리.

사이트를 정의하는 서버 블록에서 을 사용하는 경우 `nginx.conf.sample` 구성은 서버의 docroot 설정을 재정의하여 `pub/` 디렉토리. 예를 들어 다음 구성에서 마지막 줄을 참조하십시오.

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

이 자습서를 완료하려면 [램프](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) 스택:

- Linux
- Apache(2.4+)
- MySQL(5.7+)
- PHP(7.4)
- Elasticsearch(7.x) 또는 OpenSearch(1.2)
- Adobe Commerce 또는 Magento Open Source(2.4+)

>[!NOTE]
>
>을(를) 참조하십시오. [전제 조건](../prerequisites/overview.md) 그리고 [설치 안내서](../overview.md) 추가 정보.

## 1. 서버 구성 편집

가상 호스트 파일의 이름과 위치는 실행 중인 Apache 버전에 따라 다릅니다. 이 예에서는 Apache v2.4에서 가상 호스트 파일의 이름과 위치를 보여줍니다.

1. 애플리케이션 서버에 로그인합니다.
1. 가상 호스트 파일 편집:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 경로에 `pub/` 디렉토리 `DocumentRoot` 지시문:

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

1. Apache를 다시 시작합니다.

   ```bash
   systemctl restart apache2
   ```

## 2. 기본 URL을 업데이트합니다

응용 프로그램을 설치할 때 서버 호스트 이름 또는 IP 주소에 디렉토리 이름을 추가한 경우(예: `http://192.168.33.10/magento2`) 제거해야 합니다.

>[!NOTE]
>
>바꾸기 `192.168.33.10` 서버의 호스트 이름 사용.

1. 데이터베이스에 로그인:

   ```bash
   mysql -u <user> -p
   ```

1. 응용 프로그램을 설치할 때 만든 데이터베이스를 지정합니다.

   ```shell
   use <database-name>
   ```

1. 기본 URL을 업데이트합니다.

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. env.php 파일을 업데이트합니다.

다음 노드를 `env.php` 파일.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

자세한 내용은 [env.php 참조](../../configuration/reference/config-reference-envphp.md) 추가 정보.

## 4. 스위치 모드

[애플리케이션 모드](../../configuration/bootstrap/application-modes.md)포함 `production` 및 `developer`는 보안을 강화하고 개발을 더 쉽게 하도록 설계되었습니다. 이름이 제안하는 대로 `developer` 응용 프로그램을 확장하거나 사용자 지정할 때 모드 및 `production` 라이브 환경에서 실행할 때 모드.

모드 간을 전환하는 것은 서버 구성이 제대로 작동하는지 확인하는 중요한 단계입니다. CLI 툴을 사용하여 모드 간에 전환할 수 있습니다.

1. 설치 디렉토리로 이동합니다.
1. 다음으로 전환 `production` 모드.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 브라우저를 새로 고친 다음 storefront가 제대로 표시되는지 확인합니다.
1. 다음으로 전환 `developer` 모드.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 브라우저를 새로 고친 다음 storefront가 제대로 표시되는지 확인합니다.

## 5. 상점 전면 확인

로 이동합니다. [상점](https://glossary.magento.com/storefront) 웹 브라우저에서 모든 것이 제대로 작동하는지 확인하십시오.

1. 웹 브라우저를 열고 주소 표시줄에 서버의 호스트 이름 또는 IP 주소를 입력합니다. For example, `http://192.168.33.10`.

   다음 그림은 샘플 저장소 전면 페이지를 보여줍니다. 다음과 같이 표시되는 경우 설치가 성공했습니다!

   ![성공적으로 설치를 확인하는 저장소](../../assets/installation/install-success_store.png)

   자세한 내용은 [문제 해결 섹션](https://support.magento.com/hc/en-us/articles/360032994352) 페이지에 404(찾을 수 없음)가 표시되거나 이미지, CSS 및 JS와 같은 다른 자산을 로드하지 못하는 경우.

1. 브라우저에서 응용 프로그램 디렉터리에 액세스해 보십시오. 주소 표시줄의 서버의 호스트 이름 또는 IP 주소에 디렉토리 이름을 추가합니다.

   404 또는 &quot;액세스 거부&quot; 메시지가 표시되면 파일 시스템에 대한 액세스를 성공적으로 제한했습니다.

   ![액세스가 거부되었습니다.](../../assets/installation/access-denied.png)
