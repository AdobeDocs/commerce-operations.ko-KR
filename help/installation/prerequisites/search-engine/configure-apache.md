---
title: 검색 엔진에 대한 Apache 구성
description: Adobe Commerce의 온-프레미스 설치용 Apache 웹 서버를 사용하여 검색 엔진을 구성하려면 다음 단계를 따르십시오.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 검색 엔진에 대한 Apache 구성

{{$include /help/_includes/web-server-communication.md}}

## 프록시 설정

>[!NOTE]
>
>2.4.4에 OpenSearch 지원이 추가되었습니다. OpenSearch는 호환 가능한 Elasticsearch 포크입니다. 자세한 내용은 [OpenSearch로 Elasticsearch 마이그레이션](../../../upgrade/prepare/opensearch-migration.md)을 참조하십시오.

이 섹션에서는 Adobe Commerce에서 이 서버에서 실행되는 검색 엔진을 사용할 수 있도록 Apache를 *비보안* 프록시로 구성하는 방법에 대해 설명합니다. 이 섹션에서는 HTTP 기본 인증 설정에 대해 설명하지 않습니다. 이는 [Apache와의 보안 통신](#secure-communication-with-apache)에서 설명합니다.

>[!NOTE]
>
>이 예제에서 프록시가 보안되지 않은 이유는 보다 쉽게 설정하고 확인할 수 있기 때문입니다. 이 프록시에 TLS를 사용할 수 있습니다. 프록시 정보를 보안 가상 호스트 구성에 추가해야 합니다.

### Apache 2.4용 프록시 설정

이 섹션에서는 가상 호스트를 사용하여 프록시를 구성하는 방법에 대해 설명합니다.

1. 다음과 같이 `mod_proxy`을(를) 사용합니다.

   ```bash
   a2enmod proxy_http
   ```

1. 텍스트 편집기를 사용하여 `/etc/apache2/sites-available/000-default.conf` 열기
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

이 섹션에서는 Apache에서 [HTTP 기본](https://datatracker.ietf.org/doc/html/rfc2617) 인증을 사용하여 Apache와 검색 엔진 간의 통신을 보호하는 방법에 대해 설명합니다. 추가 옵션은 다음 리소스 중 하나를 참조하십시오.

* [Apache 2.4 인증 및 권한 부여 자습서](https://httpd.apache.org/docs/2.4/howto/auth.html)

다음 섹션 중 하나를 참조하십시오.

* [암호 파일 만들기](#create-a-password)
* [보안 가상 호스트 구성](#secure-communication-with-apache)

### 암호 만들기

보안상의 이유로 웹 서버 docroot를 제외한 모든 위치에서 암호 파일을 찾을 수 있습니다. 이 예제에서는 암호 파일을 새 디렉터리에 저장하는 방법을 보여 줍니다.

#### 필요한 경우 htpasswd 설치

먼저 다음과 같이 Apache `htpasswd` 유틸리티가 설치되어 있는지 확인합니다.

1. `htpasswd`이(가) 이미 설치되어 있는지 확인하려면 다음 명령을 입력하십시오.

   ```bash
   which htpasswd
   ```

   경로가 표시되면 경로가 설치되고, 명령이 출력을 반환하지 않으면 `htpasswd`이(가) 설치되지 않습니다.

1. 필요한 경우 `htpasswd`을(를) 설치합니다.

   * 우분투: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### 암호 파일 만들기

`root` 권한이 있는 사용자로 다음 명령을 입력하십시오.

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

위치

* `<username>`은(는) 다음과 같을 수 있습니다.

   * cron 설정: 웹 서버 사용자 또는 다른 사용자.

  이 예제에서는 웹 서버 사용자를 사용하지만 사용자의 선택은 사용자가 결정합니다.

   * Elasticsearch 설정: 이 예제에서 사용자 이름은 `magento_elasticsearch`입니다.

* `<password file name>`은(는) 숨겨진 파일(`.`(으)로 시작)이어야 하며 사용자 이름을 반영해야 합니다. 자세한 내용은 이 섹션의 뒷부분에서 예를 참조하십시오.

화면의 지침에 따라 사용자의 암호를 생성합니다.

#### 예시

**예 1: cron**
cron에 대해 한 명의 사용자에 대해서만 인증을 설정해야 합니다. 이 예제에서는 웹 서버 사용자를 사용합니다. 웹 서버 사용자의 암호 파일을 만들려면 다음 명령을 입력합니다.

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**예 2: Elasticsearch**
두 명의 사용자에 대한 인증을 설정해야 합니다. 하나는 nginx에 액세스할 수 있고 다른 하나는 Elasticsearch에 액세스할 수 있습니다. 이러한 사용자의 암호 파일을 생성하려면 다음 명령을 입력합니다.

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 추가 사용자 추가

암호 파일에 다른 사용자를 추가하려면 `root` 권한을 가진 사용자로 다음 명령을 입력하십시오.

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Apache와의 보안 통신

이 섹션에서는 [HTTP 기본 인증](https://httpd.apache.org/docs/2.2/howto/auth.html)을 설정하는 방법에 대해 설명합니다. TLS와 HTTP Basic 인증을 함께 사용하면 모든 사람이 Elasticsearch 또는 OpenSearch나 애플리케이션 서버와의 통신을 가로채지 못합니다.

이 섹션에서는 Apache 서버에 액세스할 수 있는 사용자를 지정하는 방법에 대해 설명합니다.

1. 텍스트 편집기를 사용하여 보안 가상 호스트에 다음 콘텐츠를 추가합니다.

   * Apache 2.4: `/etc/apache2/sites-available/default-ssl.conf` 편집

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

1. 보안 가상 호스트에 이전 명령을 추가한 경우 이전에 비보안 가상 호스트에 추가한 `Listen 8080` 및 `<VirtualHost *:8080>` 지시문을 제거하십시오.

1. 변경 사항을 저장하고 텍스트 편집기를 종료한 다음 Apache를 다시 시작합니다.

   * CentOS: `service httpd restart`
   * 우분투: `service apache2 restart`

#### 확인

{{$include /help/_includes/verify-secure-communication.md}}
