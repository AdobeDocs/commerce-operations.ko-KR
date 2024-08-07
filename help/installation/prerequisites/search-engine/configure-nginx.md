---
title: 검색 엔진에 대한 Nginx 구성
description: Adobe Commerce의 온-프레미스 설치를 위한 Nginx 웹 서버를 사용하여 검색 엔진을 구성하려면 다음 단계를 따르십시오.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# 검색 엔진에 대한 Nginx 구성

{{$include /help/_includes/web-server-communication.md}}

## 프록시 설정

>[!NOTE]
>
>2.4.4에 OpenSearch 지원이 추가되었습니다. OpenSearch는 호환 가능한 Elasticsearch 포크입니다. 자세한 내용은 [OpenSearch로 Elasticsearch 마이그레이션](../../../upgrade/prepare/opensearch-migration.md)을 참조하십시오.

이 섹션에서는 Adobe Commerce에서 이 서버에서 실행 중인 검색 엔진을 사용할 수 있도록 nginx를 *unsecure* 프록시로 구성하는 방법에 대해 설명합니다. 이 섹션에서는 HTTP 기본 인증 설정에 대해 설명하지 않습니다. [nginx와의 보안 통신](#secure-communication-with-nginx)에서 설명합니다.

>[!NOTE]
>
>이 예제에서 프록시가 보안되지 않은 이유는 보다 쉽게 설정하고 확인할 수 있기 때문입니다. 원하는 경우 이 프록시에 TLS를 사용할 수 있습니다. 그렇게 하려면 보안 서버 블록 구성에 프록시 정보를 추가해야 합니다.

### 전역 구성에서 추가 구성 파일 지정

전역 `/etc/nginx/nginx.conf`에 다음 줄이 포함되어 있는지 확인하여 다음 섹션에서 설명한 다른 구성 파일을 로드합니다.

```conf
include /etc/nginx/conf.d/*.conf;
```

### nginx를 프록시로 설정

이 섹션에서는 ngnx 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 텍스트 편집기를 사용하여 다음 내용이 포함된 `/etc/nginx/conf.d/magento_es_auth.conf` 파일을 만드십시오.

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. nginx 다시 시작:

   ```bash
   service nginx restart
   ```

1. 다음 명령을 입력하여 프록시가 작동하는지 확인합니다.

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   예를 들어 프록시가 포트 8080을 사용하는 경우:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   성공을 나타내는 다음 디스플레이와 유사한 메시지:

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Nginx와의 보안 통신

이 섹션에서는 보안 프록시로 [HTTP 기본 인증](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html)을 설정하는 방법에 대해 설명합니다. TLS와 HTTP Basic 인증을 함께 사용하면 모든 사람이 Elasticsearch 또는 OpenSearch나 애플리케이션 서버와의 통신을 가로채지 못합니다.

nginx는 기본적으로 HTTP 기본 인증을 지원하므로 프로덕션 환경에서는 권장되지 않는 [다이제스트 인증](https://www.nginx.com/resources/wiki/modules/auth_digest/)을 사용하는 것이 좋습니다.

추가 리소스:

* [Ubuntu 14.04(Digital Ocean)에서 Nginx를 사용하여 암호 인증을 설정하는 방법](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Nginx를 사용한 기본 HTTP 인증(HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearch에 대한 Nginx 구성 예](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

자세한 내용은 다음 섹션을 참조하십시오.

* [암호 만들기](#create-a-password)
* [nginx에 대한 액세스 설정](#set-up-access-to-nginx)
* [검색 엔진에 대한 제한된 컨텍스트 설정](#set-up-a-restricted-context-for-the-search-engine)
* [통신이 안전한지 확인](#secure-communication-with-nginx)

### 암호 만들기

Apache `htpasswd` 명령을 사용하여 Elasticsearch 또는 OpenSearch(이 예제에서는 `magento_elasticsearch`)에 액세스할 수 있는 사용자의 암호를 인코딩하는 것이 좋습니다.

암호를 생성하려면:

1. `htpasswd`이(가) 이미 설치되어 있는지 확인하려면 다음 명령을 입력하십시오.

   ```bash
   which htpasswd
   ```

   경로가 표시되면 경로가 설치되고, 명령이 출력을 반환하지 않으면 `htpasswd`이(가) 설치되지 않습니다.

1. 필요한 경우 `htpasswd`을(를) 설치합니다.

   * 우분투: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. 암호를 저장할 `/etc/nginx/passwd` 디렉터리 만들기:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >보안상의 이유로 `<filename>`은(는) 숨겨야 합니다. 즉, 마침표로 시작해야 합니다.

1. *(선택 사항).* 암호 파일에 다른 사용자를 추가하려면 `-c`(만들기) 옵션 없이 동일한 명령을 입력하십시오.

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. `/etc/nginx/passwd`의 내용이 올바른지 확인하십시오.

### nginx에 대한 액세스 설정

이 섹션에서는 ngnx 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

>[!WARNING]
>
>표시된 예는 *비보안* 프록시에 대한 것입니다. 보안 프록시를 사용하려면 수신 포트를 제외한 다음 내용을 보안 서버 블록에 추가하십시오.

텍스트 편집기를 사용하여 `/etc/nginx/conf.d/magento_es_auth.conf`(비보안) 또는 보안 서버 블록을 다음 내용으로 수정합니다.

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
>앞의 예에 표시된 검색 엔진 수신 포트는 예제일 뿐입니다. 보안상의 이유로 기본이 아닌 수신 포트를 사용하는 것이 좋습니다.

### 검색 엔진에 대한 제한된 컨텍스트 설정

이 섹션에서는 검색 엔진 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 다음 명령을 입력하여 인증 구성을 저장할 디렉토리를 만듭니다.

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 텍스트 편집기를 사용하여 다음 내용이 포함된 `/etc/nginx/auth/magento_elasticsearch.conf` 파일을 만드십시오.

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

1. 보안 프록시를 설정하는 경우 `/etc/nginx/conf.d/magento_es_auth.conf`을(를) 삭제하세요.
1. nginx를 다시 시작하고 다음 섹션을 계속합니다.

   ```bash
   service nginx restart
   ```

#### 확인

{{$include /help/_includes/verify-secure-communication.md}}
