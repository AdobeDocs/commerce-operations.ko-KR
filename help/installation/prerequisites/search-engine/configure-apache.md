---
title: 검색 엔진에 대한 Apache 구성
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치를 위한 Apache 웹 서버를 사용하여 검색 엔진을 구성합니다.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 검색 엔진에 대한 Apache 구성

{{$include /help/_includes/web-server-communication.md}}

## 프록시 설정

>[!NOTE]
>
>2.4.4에 OpenSearch 지원이 추가되었습니다. OpenSearch는 호환 가능한 Elasticsearch 포크입니다. 다음을 참조하십시오 [OpenSearch로 Elasticsearch 마이그레이션](../../../upgrade/prepare/opensearch-migration.md) 추가 정보.

이 섹션에서는 Apache as a 를 구성하는 방법을 설명합니다. *비보안* 프록시를 통해 Adobe Commerce에서 이 서버에서 실행 중인 검색 엔진을 사용할 수 있습니다. 이 섹션에서는 HTTP 기본 인증 설정에 대해 설명하지 않습니다. [Apache와의 보안 통신](#secure-communication-with-apache).

>[!NOTE]
>
>이 예제에서 프록시가 보안되지 않은 이유는 보다 쉽게 설정하고 확인할 수 있기 때문입니다. 이 프록시에 TLS를 사용할 수 있습니다. 프록시 정보를 보안 가상 호스트 구성에 추가해야 합니다.

### Apache 2.4용 프록시 설정

이 섹션에서는 가상 호스트를 사용하여 프록시를 구성하는 방법에 대해 설명합니다.

1. 사용 `mod_proxy` 다음과 같이:

   ```bash
   a2enmod proxy_http
   ```

1. 텍스트 편집기를 사용하여 열기 `/etc/apache2/sites-available/000-default.conf`
1. 파일의 맨 위에 다음 지시문을 추가합니다.

   ```conf
   Listen 8080
   ```

1. 파일 하단에 다음 내용을 추가합니다.

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Apache 다시 시작:

   ```bash
   service apache2 restart
   ```

1. 다음 명령을 입력하여 프록시가 작동하는지 확인합니다.

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   예를 들어, Elasticsearch을 사용하고 프록시가 포트 8080을 사용하는 경우:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   성공을 나타내는 다음 디스플레이와 유사한 메시지:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Apache와의 보안 통신

이 섹션에서는 를 사용하여 Apache와 검색 엔진 간의 통신을 보호하는 방법에 대해 설명합니다. [HTTP 기본](https://datatracker.ietf.org/doc/html/rfc2617) apache를 사용한 인증. 추가 옵션은 다음 리소스 중 하나를 참조하십시오.

* [Apache 2.4 인증 및 권한 부여 자습서](https://httpd.apache.org/docs/2.4/howto/auth.html)

다음 섹션 중 하나를 참조하십시오.

* [암호 파일 만들기](#create-a-password)
* [보안 가상 호스트 구성](#secure-communication-with-apache)

### 암호 만들기

보안상의 이유로 웹 서버 docroot를 제외한 모든 위치에서 암호 파일을 찾을 수 있습니다. 이 예제에서는 암호 파일을 새 디렉터리에 저장하는 방법을 보여 줍니다.

#### 필요한 경우 htpasswd 설치

먼저 Apache가 있는지 확인합니다. `htpasswd` 유틸리티는 다음과 같이 설치됩니다.

1. 다음 명령을 입력하여 다음을 확인합니다 `htpasswd` 이(가) 이미 설치되어 있습니다.

   ```bash
   which htpasswd
   ```

   경로가 표시되면 설치됩니다. 명령이 출력을 반환하지 않으면 `htpasswd` 이(가) 설치되지 않았습니다.

1. 필요한 경우 설치 `htpasswd`:

   * 우분투: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### 암호 파일 만들기

사용자로 다음 명령을 입력합니다. `root` 권한:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

위치

* `<username>` 다음과 같을 수 있습니다.

   * cron 설정: 웹 서버 사용자 또는 다른 사용자.

  이 예제에서는 웹 서버 사용자를 사용하지만 사용자의 선택은 사용자가 결정합니다.

   * Elasticsearch 설정: 사용자의 이름이 다음과 같습니다. `magento_elasticsearch` 이 예에서

* `<password file name>` 은(는) 숨겨진 파일이어야 합니다(다음으로 시작). `.`) 및 에는 사용자의 이름이 반영되어야 합니다. 자세한 내용은 이 섹션의 뒷부분에서 예를 참조하십시오.

화면의 지침에 따라 사용자의 암호를 생성합니다.

#### 예

**예 1: cron**
cron에 대해 한 명의 사용자에 대해서만 인증을 설정해야 합니다. 이 예제에서는 웹 서버 사용자를 사용합니다. 웹 서버 사용자의 암호 파일을 만들려면 다음 명령을 입력합니다.

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**예제 2: Elasticsearch**
두 명의 사용자에 대한 인증을 설정해야 합니다. 하나는 nginx에 액세스할 수 있고 다른 하나는 Elasticsearch에 액세스할 수 있습니다. 이러한 사용자의 암호 파일을 생성하려면 다음 명령을 입력합니다.

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 추가 사용자 추가

암호 파일에 다른 사용자를 추가하려면 다음 명령을 `root` 권한:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Apache와의 보안 통신

이 섹션에서는 설정 방법을 설명합니다 [HTTP 기본 인증](https://httpd.apache.org/docs/2.2/howto/auth.html). TLS와 HTTP Basic 인증을 함께 사용하면 모든 사람이 Elasticsearch 또는 OpenSearch나 애플리케이션 서버와의 통신을 가로채지 못합니다.

이 섹션에서는 Apache 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 텍스트 편집기를 사용하여 보안 가상 호스트에 다음 콘텐츠를 추가합니다.

   * Apache 2.4: 편집 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 보안 가상 호스트에 이전 항목을 추가한 경우 `Listen 8080` 및 `<VirtualHost *:8080>` 비보안 가상 호스트에 이전에 추가한 지시문입니다.

1. 변경 사항을 저장하고 텍스트 편집기를 종료한 다음 Apache를 다시 시작합니다.

   * CentOS: `service httpd restart`
   * 우분투: `service apache2 restart`

#### 확인

{{$include /help/_includes/verify-secure-communication.md}}
