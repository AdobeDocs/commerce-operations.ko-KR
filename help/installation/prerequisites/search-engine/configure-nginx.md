---
title: 검색 엔진에 대한 Nginx 구성
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온프레미스 설치에 대한 Nginx 웹 서버로 검색 엔진을 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# 검색 엔진에 대한 Nginx 구성

{{$include /help/_includes/web-server-communication.md}}

## 프록시 설정

>[!NOTE]
>
>OpenSearch 지원이 2.4.4에 추가되었습니다. OpenSearch는 Elasticsearch의 호환 가능한 포크입니다. 자세한 내용은 [OpenSearch로 Elasticsearch 마이그레이션](../../../upgrade/prepare/opensearch-migration.md) 추가 정보.

이 섹션에서는 nginx를 *비보안* 이 서버에서 실행 중인 검색 엔진을 사용할 수 있도록 프록시입니다. 이 섹션에서는 HTTP 기본 인증 설정에 대해 다루지 않습니다. 그것은 [nginx와의 보안 통신](#secure-communication-with-nginx).

>[!NOTE]
>
>이 예에서 프록시가 보안되지 않은 이유는 프록시를 설정하고 확인하는 것이 더 쉽기 때문입니다. 필요한 경우 이 프록시와 함께 TLS를 사용할 수 있습니다. 이렇게 하려면 보안 서버 블록 구성에 프록시 정보를 추가해야 합니다.

### 글로벌 구성에서 추가 구성 파일을 지정합니다

전역 확인 `/etc/nginx/nginx.conf` 에는 다음 섹션에서 설명한 다른 구성 파일이 로드되도록 다음 줄이 포함되어 있습니다.

```conf
include /etc/nginx/conf.d/*.conf;
```

### nginx를 프록시로 설정

이 섹션에서는 nginx 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 텍스트 편집기를 사용하여 파일을 만듭니다 `/etc/nginx/conf.d/magento_es_auth.conf` 다음 내용으로 채우십시오.

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. ninx를 다시 시작합니다.

   ```bash
   service nginx restart
   ```

1. 다음 명령을 입력하여 프록시가 작동하는지 확인합니다.

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   예를 들어 프록시가 포트 8080을 사용하는 경우

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   성공을 나타내는 메시지가 다음 표시와 유사합니다.

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## nginx와의 보안 통신

이 섹션에서는 설정 방법을 설명합니다 [HTTP 기본 인증](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 보안 프록시로 설정합니다. TLS 및 HTTP 기본 인증을 함께 사용하면 누구나 Elasticsearch 또는 OpenSearch 또는 애플리케이션 서버와의 통신을 가로채지 못합니다.

기본적으로 HTTP Basic 인증을 지원하므로 다음과 같은 인증을 수행하는 것이 좋습니다. [다이제스트 인증](https://www.nginx.com/resources/wiki/modules/auth_digest/): 프로덕션에서 권장되지 않습니다.

추가 리소스:

* [Ubuntu 14.04(Digital Ocean)에서 Nginx를 사용하여 암호 인증을 설정하는 방법](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Nginx(HowtoForge)를 사용한 기본 HTTP 인증](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearch에 대한 Nginx 구성 예](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

자세한 내용은 다음 섹션을 참조하십시오.

* [암호 만들기](#create-a-password)
* [nginx 액세스 설정](#set-up-access-to-nginx)
* [검색 엔진에 대해 제한된 컨텍스트 설정](#set-up-a-restricted-context-for-the-search-engine)
* [통신이 안전한지 확인](#secure-communication-with-nginx)

### 암호 만들기

Apache를 사용하는 것이 좋습니다 `htpasswd` Elasticsearch 또는 OpenSearch( 이름이 지정된 )에 액세스할 수 있는 사용자의 암호를 인코딩하는 명령 `magento_elasticsearch` 이 예에서 ).

암호를 만들려면

1. 다음 명령을 입력하여 `htpasswd` 이미 설치되어 있습니다.

   ```bash
   which htpasswd
   ```

   경로가 표시되면 설치됩니다. 명령이 출력을 반환하지 않으면 `htpasswd` 이 설치되어 있지 않습니다.

1. 필요한 경우 를 설치합니다. `htpasswd`:

   * 우분투: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. 만들기 `/etc/nginx/passwd` 암호를 저장할 디렉토리:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >보안상의 이유로 `<filename>` 숨겨야 합니다. 즉, 마침표로 시작해야 합니다.

1. *(선택 사항).* 암호 파일에 다른 사용자를 추가하려면 `-c` (만들기) 옵션:

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 다음 내용이 `/etc/nginx/passwd` 가 올바릅니다.

### nginx 액세스 설정

이 섹션에서는 nginx 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

>[!WARNING]
>
>표시된 예는 *비보안* 프록시 호출. 보안 프록시를 사용하려면 다음 내용(수신 포트 제외)을 보안 서버 블록에 추가합니다.

텍스트 편집기를 사용하여 다음 중 하나를 수정합니다 `/etc/nginx/conf.d/magento_es_auth.conf` (비보안) 또는 다음 내용이 포함된 보안 서버 블록

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>앞의 예제에 표시된 검색 엔진 수신 포트는 예시에만 해당됩니다. 보안상의 이유로 기본이 아닌 수신 대기 포트를 사용하는 것이 좋습니다.

### 검색 엔진에 대해 제한된 컨텍스트 설정

이 섹션에서는 검색 엔진 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 인증 구성을 저장할 디렉토리를 만들려면 다음 명령을 입력합니다.

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 텍스트 편집기를 사용하여 파일을 만듭니다 `/etc/nginx/auth/magento_elasticsearch.conf` 다음 내용으로 채우십시오.

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. 보안 프록시를 설정한 경우 를 삭제합니다. `/etc/nginx/conf.d/magento_es_auth.conf`.
1. ninx를 다시 시작하고 다음 섹션을 계속합니다.

   ```bash
   service nginx restart
   ```

#### 확인

{{$include /help/_includes/verify-secure-communication.md}}
