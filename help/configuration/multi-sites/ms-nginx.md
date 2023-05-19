---
title: Nginx를 사용하여 여러 웹 사이트 설정
description: Nginx를 사용하여 여러 웹 사이트를 설정하려면 이 자습서를 따르십시오.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Nginx를 사용하여 여러 웹 사이트 설정

다음과 같이 가정합니다.

- 개발 컴퓨터(랩톱, 가상 컴퓨터 또는 이와 유사한 컴퓨터)에서 작업 중입니다.

   호스팅 환경에서 여러 웹 사이트를 배포하려면 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.

   클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 이 항목에서 설명한 작업을 완료한 후 다음을 참조하십시오. [여러 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 다음에서 _클라우드 인프라의 Commerce 안내서_.

- 하나의 가상 호스트 파일에서 여러 도메인을 허용하거나 웹 사이트당 하나의 가상 호스트를 사용합니다. 가상 호스트 구성 파일은에 있습니다 `/etc/nginx/sites-available`.
- 다음을 사용합니다. `nginx.conf.sample` 이 자습서에서 설명한 수정 사항만 Commerce에서 제공합니다.
- Commerce 소프트웨어는 `/var/www/html/magento2`.
- 기본 이외의 두 개의 웹 사이트가 있습니다.

   - `french.mysite.mg` 웹 사이트 코드 사용 `french` 및 스토어 보기 코드 `fr`
   - `german.mysite.mg` 웹 사이트 코드 사용 `german` 및 스토어 보기 코드 `de`
   - `mysite.mg` 는 기본 웹 사이트 및 기본 스토어 보기입니다

>[!TIP]
>
>을(를) 참조하십시오 [웹 사이트 만들기](ms-admin.md#step-2-create-websites) 및 [스토어 조회수 만들기](ms-admin.md#step-4-create-store-views) 를 참조하십시오.

다음은 ngix를 사용하여 여러 웹 사이트를 설정하는 로드맵입니다.

1. [웹 사이트, 스토어 및 스토어 조회수 설정](ms-admin.md) 관리에서.
1. 만들기 [Nginx 가상 호스트](#step-2-create-nginx-virtual-hosts))을 클릭하여 많은 웹 사이트 또는 Commerce 웹 사이트당 하나의 Nginx 가상 호스트를 매핑합니다(아래 설명된 단계).
1. 의 값 전달 [MAGE 변수](ms-overview.md) `$MAGE_RUN_TYPE` 및 `$MAGE_RUN_CODE` 제공된 Magento을 사용하여 nginx에 보내기 `nginx.conf.sample` (아래에 자세히 설명된 단계).

   - `$MAGE_RUN_TYPE` 다음 중 하나일 수 있습니다. `store` 또는 `website`:

      - 사용 `website` 상점에서 웹 사이트를 로드합니다.
      - 사용 `store` 상점 전면의 상점 보기를 로드합니다.
   - `$MAGE_RUN_CODE` 는 다음에 해당하는 고유한 웹 사이트 또는 스토어 보기 코드입니다. `$MAGE_RUN_TYPE`.


1. Commerce 관리자의 기본 URL 구성을 업데이트합니다.

## 1단계: 관리자에서 웹 사이트, 스토어 및 스토어 보기 만들기

다음을 참조하십시오 [관리자에서 여러 웹 사이트, 스토어 및 스토어 보기 설정](ms-admin.md).

## 2단계: nginx 가상 호스트 생성

이 단계에서는 상점 첫 화면에서 웹 사이트를 로드하는 방법에 대해 설명합니다. 웹 사이트 또는 스토어 보기를 사용할 수 있습니다. 스토어 보기를 사용하는 경우 매개 변수 값을 적절하게 조정해야 합니다. 다음 사용자와 함께 이 섹션의 작업을 완료해야 합니다. `sudo` 권한.

하나만 사용 [nginx 가상 호스트 파일](#step-2-create-nginx-virtual-hosts), nginx 구성을 단순하고 깔끔하게 유지할 수 있습니다. 여러 가상 호스트 파일을 사용하여 각 스토어를 사용자 정의할 수 있습니다( 의 사용자 지정 위치 사용). `french.mysite.mg` 예).

**가상 호스트 1개를 만들려면** (간소화됨):

이 구성은 다음 경우에 확장됩니다 [nginx 구성](../../installation/prerequisites/web-server/nginx.md).

1. 텍스트 편집기를 열고 다음 내용을 라는 새 파일에 추가합니다 `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 파일에 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 서버 구성 확인:

   ```bash
   nginx -t
   ```

1. 성공하면 다음 메시지가 표시됩니다.

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   오류가 표시되면 가상 호스트 구성 파일의 구문을 확인합니다.

1. 에서 심볼 링크 만들기 `/etc/nginx/sites-enabled` 디렉터리:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

map 지시문에 대한 자세한 내용은 [map 지시문의 nginx 설명서](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**여러 가상 호스트를 생성하려면 다음을 수행합니다**:

1. 텍스트 편집기를 열고 다음 내용을 라는 새 파일에 추가합니다 `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 이름이 인 다른 파일 만들기 `german.mysite.mg` 다음 내용이 포함된 동일한 디렉터리에서:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 파일에 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 서버 구성 확인:

   ```bash
   nginx -t
   ```

1. 성공하면 다음 메시지가 표시됩니다.

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   오류가 표시되면 가상 호스트 구성 파일의 구문을 확인합니다.

1. 에서 심볼 링크 만들기 `/etc/nginx/sites-enabled` 디렉터리:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 3단계: nginx.conf.sample 수정

>[!TIP]
>
>편집 안 함 `nginx.conf.sample` 파일: 새로운 릴리스마다 업데이트될 수 있는 핵심 Commerce 파일입니다. 대신 `nginx.conf.sample` 파일 이름을 변경한 다음 복사한 파일을 편집합니다.

**기본 응용 프로그램의 PHP 진입점을 편집하려면**:

을 수정하려면 다음을 수행합니다 `nginx.conf.sample` 파일**:

1. 텍스트 편집기를 열고 다음을 검토합니다. `nginx.conf.sample` 파일 ,`<magento2_installation_directory>/nginx.conf.sample`. 다음 섹션을 찾습니다.

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. 업데이트 `nginx.conf.sample` include 문 앞에 다음 두 줄이 있는 파일:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

기본 응용 프로그램에 대해 업데이트된 PHP 진입점의 예는 다음과 같습니다.

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## 4단계: 기본 URL 구성 업데이트

에 대한 기본 URL을 업데이트해야 합니다. `french` 및 `german` 상거래 관리자의 웹 사이트.

### 프랑스어 웹 사이트 기본 URL 업데이트

1. Commerce 관리자에 로그인하고 다음으로 이동합니다. **스토어** > **설정** > **구성** > **일반** > **웹**.
1. 변경 _구성 범위_ (으)로 `french` 웹 사이트입니다.
1. 확장 **기본 URL** 섹션 및 업데이트 **기본 URL** 및 **기본 링크 URL** 값: 까지 `http://french.magento24.com/`.
1. 확장 **기본 URL(보안)** 섹션 및 업데이트 **Secure Base URL** 및 **Secure Base 링크 URL** 값: 까지 `https://french.magento24.com/`.
1. 클릭 **구성 저장** 구성 변경 사항을 저장합니다.

### 독일어 웹 사이트 기본 URL 업데이트

1. Commerce 관리자에 로그인하고 다음으로 이동합니다. **스토어** > **설정** > **구성** > **일반** > **웹**.
1. 변경 _구성 범위_ (으)로 `german` 웹 사이트입니다.
1. 확장 **기본 URL** 섹션 및 업데이트 **기본 URL** 및 **기본 링크 URL** 값: 까지 `http://german.magento24.com/`.
1. 확장 **기본 URL(보안)** 섹션 및 업데이트 **Secure Base URL** 및 **Secure Base 링크 URL** 값: 까지 `https://german.magento24.com/`.
1. 클릭 **구성 저장** 구성 변경 사항을 저장합니다.

### 캐시 정리

다음 명령을 실행하여 `config` 및 `full_page` 캐시합니다.

```bash
bin/magento cache:clean config full_page
```

## 사이트 확인

스토어의 URL에 대해 DNS를 설정하지 않은 경우 `hosts` 파일:

1. 운영 체제 찾기 `hosts` 파일.
1. 정적 경로를 다음 형식으로 추가합니다.

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 브라우저에서 다음 URL 중 하나로 이동합니다.

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 호스팅 환경에서 여러 웹 사이트를 배포하려면 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.
>- 클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 다음을 참조하십시오. [여러 클라우드 웹 사이트 또는 스토어 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 다음에서 _클라우드 인프라의 Commerce 안내서_.


### 문제 해결

- 프랑스어 및 독일어 사이트가 404를 반환하지만 관리자가 로드되는 경우 을 완료했는지 확인합니다. [6단계: 기본 URL에 스토어 코드 추가](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 모든 URL이 404를 반환하는 경우 웹 서버를 다시 시작했는지 확인하십시오.
- 관리자가 제대로 작동하지 않는 경우 가상 호스트를 제대로 설정했는지 확인하십시오.
