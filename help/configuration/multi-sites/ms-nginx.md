---
title: Nginx를 사용하여 여러 웹 사이트 설정
description: Nginx를 사용하여 여러 웹 사이트를 설정하려면 이 자습서를 따르십시오.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Nginx를 사용하여 여러 웹 사이트 설정

우리는 다음과 같이 가정합니다.

- 개발 시스템(랩톱, 가상 컴퓨터 또는 유사)에서 작업 중입니다.

   호스팅된 환경에 여러 웹 사이트를 배포하는 데 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.

   클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 이 항목에서 설명한 작업을 완료하면 [여러 웹 사이트 또는 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 에서 _Commerce Cloud 안내서_.

- 하나의 가상 호스트 파일에서 여러 도메인을 허용하거나 웹 사이트당 하나의 가상 호스트를 사용합니다. 가상 호스트 구성 파일은 `/etc/nginx/sites-available`.
- 를 사용합니다 `nginx.conf.sample` 이 자습서에서 설명한 수정 사항만 사용하여 Commerce에서 제공합니다.
- 상거래 소프트웨어는 `/var/www/html/magento2`.
- 기본값이 아닌 두 개의 웹 사이트가 있습니다.

   - `french.mysite.mg` 웹 사이트 코드 포함 `french` 보기 코드 저장 `fr`
   - `german.mysite.mg` 웹 사이트 코드 포함 `german` 보기 코드 저장 `de`
   - `mysite.mg` 기본 웹 사이트 및 기본 스토어 보기입니다.

>[!TIP]
>
>을(를) 참조하십시오. [웹 사이트 만들기](ms-admin.md#step-2-create-websites) 및 [저장소 보기 만들기](ms-admin.md#step-4-create-store-views) 를 참조하십시오.

다음은 ninx를 사용하여 여러 웹 사이트를 설정하는 로드맵입니다.

1. [웹 사이트, 저장소 및 저장소 보기 설정](ms-admin.md) 관리자.
1. 만들기 [Nginx 가상 호스트](#step-2-create-nginx-virtual-hosts))를 사용하여 많은 웹 사이트나 상거래 웹 사이트당 Nginx 가상 호스트 하나를 매핑합니다(아래에 자세히 설명되어 있음).
1. 의 값을 전달합니다 [이미지 변수](ms-overview.md) `$MAGE_RUN_TYPE` 및 `$MAGE_RUN_CODE` Magento이 제공한 를 사용하여 ninx를 `nginx.conf.sample` (아래에 자세히 설명되어 있습니다.)

   - `$MAGE_RUN_TYPE` 다음 중 하나를 수행할 수 있습니다. `store` 또는 `website`:

      - 사용 `website` 를 눌러 웹 사이트를 상점 앞에 로드합니다.
      - 사용 `store` 를 눌러 저장소 뷰에 있는 모든 저장소 보기를 로드합니다.
   - `$MAGE_RUN_CODE` 는 고유한 웹 사이트 또는 스토어 보기 코드로서 `$MAGE_RUN_TYPE`.


1. 상거래 관리자에서 기본 URL 구성을 업데이트합니다.

## 1단계: 관리자로부터 웹 사이트 만들기, 저장 및 보기 저장

자세한 내용은 [관리자에서 여러 웹 사이트, 저장소 및 보기 저장 설정](ms-admin.md).

## 2단계: Nginx 가상 호스트 만들기

이 절차에서는 웹 사이트에서 웹 사이트를 로드하는 방법을 설명합니다. [상점](https://glossary.magento.com/storefront). 웹 사이트를 사용하거나 보기를 저장할 수 있습니다. 저장소 뷰를 사용하는 경우 그에 따라 매개변수 값을 조정해야 합니다. 이 섹션의 작업을 `sudo` 권한.

하나만 사용하면 [nginx 가상 호스트 파일](#step-2-create-nginx-virtual-hosts)nginx 구성을 간단하고 깔끔하게 유지할 수 있습니다. 여러 가상 호스트 파일을 사용하여 각 저장소를 사용자 지정할 수 있습니다(사용자 지정 위치 사용). `french.mysite.mg` 예).

**하나의 가상 호스트를 만들려면** (간소화됨):

이 구성은 [nginx 구성](../../installation/prerequisites/web-server/nginx.md).

1. 텍스트 편집기를 열고 다음 컨텐츠를 라는 새 파일에 추가합니다. `/etc/nginx/sites-available/magento`:

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

1. 파일에 대한 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 서버 구성을 확인합니다.

   ```bash
   nginx -t
   ```

1. 성공하면 다음 메시지가 표시됩니다.

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   오류가 표시되면 가상 호스트 구성 파일의 구문을 확인합니다.

1. 에서 심볼 링크 만들기 `/etc/nginx/sites-enabled` 디렉토리:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

맵 지시어에 대한 자세한 내용은 [map 지시문에 대한 nginx 설명서](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**여러 가상 호스트를 생성하려면**:

1. 텍스트 편집기를 열고 다음 컨텐츠를 라는 새 파일에 추가합니다. `/etc/nginx/sites-available/french.mysite.mg`:

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

1. 이름이 인 다른 파일 만들기 `german.mysite.mg` 다음 내용이 있는 동일한 디렉토리에서 다음을 수행합니다.

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

1. 파일에 대한 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 서버 구성을 확인합니다.

   ```bash
   nginx -t
   ```

1. 성공하면 다음 메시지가 표시됩니다.

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   오류가 표시되면 가상 호스트 구성 파일의 구문을 확인합니다.

1. 에서 심볼 링크 만들기 `/etc/nginx/sites-enabled` 디렉토리:

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
>편집 안 함 `nginx.conf.sample` 파일; 코어 Commerce 파일입니다. 각 새 릴리스로 업데이트할 수 있습니다. 대신 를 복사합니다. `nginx.conf.sample` 파일에서 이름을 바꾼 다음 복사한 파일을 편집합니다.

**기본 응용 프로그램의 PHP 진입점을 편집하려면**:

를 수정하려면 `nginx.conf.sample` 파일**:

1. 텍스트 편집기를 열고 를 검토합니다. `nginx.conf.sample` 파일 ,`<magento2_installation_directory>/nginx.conf.sample`. 다음 섹션을 찾습니다.

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

1. 업데이트 `nginx.conf.sample` include 문 앞에 다음 두 줄을 포함하는 파일:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

기본 응용 프로그램에 대해 업데이트된 PHP 진입점 예는 다음과 같습니다.

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

에 대한 기본 URL을 업데이트해야 합니다. `french` 그리고 `german` 상거래 관리자의 웹 사이트.

### 프랑스어 웹 사이트 기본 URL 업데이트

1. 상거래 관리자에 로그인하고 **스토어** > **설정** > **구성** > **일반** > **웹**.
1. 변경 _구성 범위_ 변환 후 `french` 웹 사이트입니다.
1. 확장 **기본 URL** 섹션 및 업데이트 **기본 URL** 및 **기본 링크 URL** 값 `http://french.magento24.com/`.
1. 확장 **기본 URL(보안)** 섹션 및 업데이트 **보안 기본 URL** 및 **보안 기본 링크 URL** 값 `https://french.magento24.com/`.
1. 클릭 **구성 저장** 구성 변경 사항을 저장합니다.

### 독일어 웹 사이트 기본 URL 업데이트

1. 상거래 관리자에 로그인하고 **스토어** > **설정** > **구성** > **일반** > **웹**.
1. 변경 _구성 범위_ 변환 후 `german` 웹 사이트입니다.
1. 확장 **기본 URL** 섹션 및 업데이트 **기본 URL** 및 **기본 링크 URL** 값 `http://german.magento24.com/`.
1. 확장 **기본 URL(보안)** 섹션 및 업데이트 **보안 기본 URL** 및 **보안 기본 링크 URL** 값 `https://german.magento24.com/`.
1. 클릭 **구성 저장** 구성 변경 사항을 저장합니다.

### 캐시 정리

다음 명령을 실행하여 `config` 및 `full_page` 캐시

```bash
bin/magento cache:clean config full_page
```

## 사이트 확인

저장소 URL에 대해 DNS를 설정하지 않은 경우, 의 호스트에 정적 경로를 추가해야 합니다 `hosts` 파일:

1. 운영 체제 찾기 `hosts` 파일.
1. 정적 경로를 형식으로 추가합니다.

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. 브라우저에서 다음 URL 중 하나로 이동합니다.

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 호스팅된 환경에 여러 웹 사이트를 배포하는 데 추가 작업이 필요할 수 있습니다. 자세한 내용은 호스팅 공급자에게 문의하십시오.
>- 클라우드 인프라에서 Adobe Commerce을 설정하려면 추가 작업이 필요합니다. 참조 [여러 클라우드 웹 사이트 또는 저장소 설정](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 에서 _Commerce Cloud 안내서_.


### 문제 해결

- 프랑스어 및 독일어 사이트가 404를 반환하지만 관리자가 로드되는 경우 작업을 완료했는지 확인하십시오 [6단계: 기본 URL에 스토어 코드 추가](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 모든 URL이 404를 반환하는 경우 웹 서버를 다시 시작했는지 확인하십시오.
- Admin Console이 제대로 작동하지 않는 경우 가상 호스트를 올바르게 설정했는지 확인하십시오.
