---
title: 소프트웨어 Recommendations
description: Adobe Commerce 및 Magento Open Source 배포의 최적 성능과 관련된 권장 소프트웨어 목록을 검토합니다.
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---

# 소프트웨어 권장 사항

의 프로덕션 인스턴스에는 다음 소프트웨어가 필요합니다. [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx 및 [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] 또는 OpenSearch](../installation/prerequisites/search-engine/overview.md)

다중 서버 배포 또는 비즈니스 확장을 계획하고 있는 판매자의 경우 다음을 권장합니다.

* [[!DNL Varnish] 캐시](../configuration/cache/config-varnish.md)
* [레디스](../configuration/cache/redis-session.md) 세션의 경우(2.0.6 이상)
* 별도의 Redis 인스턴스 [기본 캐시](../configuration/cache/redis-pg-cache.md) (페이지 캐시에 이 인스턴스를 사용하지 않음)

다음을 참조하십시오 [시스템 요구 사항](../installation/system-requirements.md) 각 소프트웨어 유형의 지원되는 버전에 대한 정보입니다.

## 운영 체제

운영 체제 구성 및 최적화는 다음과 유사합니다 [!DNL Commerce] 다른 고부하 웹 애플리케이션과 비교합니다. 서버가 처리하는 동시 연결 수가 증가하면 사용 가능한 소켓 수가 완전히 할당될 수 있습니다. Linux 커널은 TCP 연결을 &quot;재사용&quot;하는 메커니즘을 지원합니다. 이 메커니즘을 활성화하려면에서 다음 값을 설정하십시오 `/etc/sysctl.conf`:

>[!INFO]
>
>net.ipv4.tcp_tw_reuse를 활성화해도 들어오는 연결에 영향을 주지 않습니다.

```text
net.ipv4.tcp_tw_reuse = 1
```

커널 매개 변수 `net.core.somaxconn` 연결을 기다리는 열린 소켓의 최대 수를 제어합니다. 이 값은 1024로 안전하게 늘릴 수 있지만 이 값을 처리하는 서버의 기능과 상관 관계가 있어야 합니다. 이 커널 매개 변수를 활성화하려면에서 다음 값을 설정하십시오. `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento은 PHP 7.3 및 7.4를 완전히 지원합니다. 요청 처리 시 최대 속도와 효율성을 얻기 위해 PHP를 구성할 때 고려해야 할 몇 가지 요소가 있습니다.

### 확장 프로그램

활성 PHP 확장 목록을 다음에 필요한 확장으로 제한하는 것이 좋습니다. [!DNL Commerce] 기능.

Magento Open Source 및 Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* 내선 번호
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* 외부 소켓
* 이스트나트륨
* 내선 토큰화기
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

또한 Adobe Commerce에는 다음이 필요합니다.

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* 내선 번호
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* 외부 소켓
* 이스트나트륨
* -spl
* 내선 토큰화기
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

확장을 추가하면 라이브러리 로드 시간이 증가합니다.

>[!INFO]
>
>`php-mcrypt` 이(가) PHP 7.2에서 제거되어 [`sodium` 라이브러리](https://www.php.net/manual/en/book.sodium.php). 다음을 확인합니다. [나트륨](https://www.php.net/manual/en/sodium.installation.php) 는 PHP를 업그레이드할 때 올바르게 활성화됩니다.

>[!INFO]
>
>프로파일링 및 디버깅 확장이 있으면 페이지의 응답 시간에 부정적인 영향을 줄 수 있습니다. 예를 들어 디버그 세션이 없는 활성 xDebug 모듈은 페이지 응답 시간을 최대 30%까지 늘릴 수 있습니다.

### PHP 설정

모든 작업의 성공적인 실행을 보장 [!DNL Commerce] 데이터 또는 코드를 디스크에 덤프하지 않는 경우 다음과 같이 메모리 제한을 설정하십시오.

```text
memory_limit=1G
```

디버깅을 위해 이 값을 2G로 늘립니다.

#### Realpath_cache 구성

개선하려면 [!DNL Commerce] 성능, 다음 권장 사항 추가 또는 업데이트 `realpath_cache` 의 설정 `php.ini` 파일. 이 구성을 사용하면 PHP 프로세스가 페이지를 로드할 때마다 경로를 조회하는 대신 파일에 경로를 캐시할 수 있습니다. 다음을 참조하십시오 [성능 조정](https://www.php.net/manual/en/ini.core.php) PHP 설명서에서 참조하십시오.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### 바이트 코드

최대 속도를 내려면 [!DNL Commerce] php 7에서는 OpCache 모듈을 활성화하고 올바르게 구성해야 합니다. 모듈에는 다음 설정이 권장됩니다.

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcache에 대한 메모리 할당을 미세 조정할 때 Magento의 코드 베이스와 모든 확장의 크기를 고려하십시오. Magento의 성능 팀은 설치된 확장의 평균 수에 대해 opcache에 충분한 공간을 제공하므로 테스트에 이전 예의 값을 사용합니다.

메모리 부족 시스템이 있고 확장 또는 사용자 지정이 많이 설치되어 있지 않은 경우 다음 설정을 사용하여 유사한 결과를 얻으십시오.

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

다음을 활성화하는 것이 좋습니다. [PHP APCu 확장](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) 및 [구성 `composer` 지원](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) 을 클릭하여 성능을 최대화합니다. 이 확장은 열린 파일의 파일 위치를 캐시하여 성능을 향상시킵니다. [!DNL Commerce] 페이지, Ajax 호출 및 끝점을 포함한 서버 호출.

편집 `apcu.ini` 다음을 포함할 파일:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## 웹 서버

Magento은 Nginx 및 Apache 웹 서버를 완전히 지원합니다. [!DNL Commerce] 에서 권장되는 구성 파일 샘플을 제공합니다.  `<magento_home>/nginx.conf.sample` (Nginx) 및  `<magento_home>.htaccess.sample` (Apache) 파일입니다.  Nginx 샘플에는 성능 향상을 위한 설정이 포함되어 있으며 재구성이 거의 필요하지 않도록 설계되었습니다. 샘플 파일에 정의된 몇 가지 주요 구성 모범 사례는 다음과 같습니다.

* 브라우저에서 정적 콘텐츠를 캐싱하기 위한 설정
* PHP용 메모리 및 실행 시간 설정
* 컨텐츠 압축 설정

또한 아래 나열된 대로 입력 요청 처리를 위한 스레드 수를 구성해야 합니다.

| 웹 서버 | 속성 이름 | 위치 | 관련 정보 |
|--- | --- | --- | ---|
| Ngix | `worker_connections` | `/etc/nginx/nginx.conf` (데비안) | [성능을 위한 NGINX 조정](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache 성능 조정](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM 일반 지시문](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

이 문서에서는 자세한 내용을 제공하지 않습니다. [!DNL MySQL] 각 스토어와 환경이 다르기 때문에 지침을 조정할 수 있지만, 일반적인 권장 사항을 제공할 수 있습니다.

에 대한 많은 개선 사항이 있습니다. [!DNL MySQL] 5.7.9 당사는 다음을 확신하고 있습니다. [!DNL MySQL] 는 양호한 기본 설정으로 배포됩니다. 가장 중요한 설정은 다음과 같습니다.

| 매개 변수 | 기본값 | 설명 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 기본값은 8로 설정되어 여러 스레드에서 동일한 인스턴스에 액세스하려는 문제를 방지합니다. |
| `innodb_buffer_pool_size` | 128MB | 위에서 설명한 여러 풀 인스턴스와 결합하면 기본 메모리 할당이 1024MB입니다. 전체 크기는 모든 버퍼 풀에서 나누어집니다. 최상의 효율성을 위해 다음 조합을 지정합니다. `innodb_buffer_pool_instances` 및 `innodb_buffer_pool_size` 각 버퍼 풀 인스턴스가 최소 1GB가 되도록 합니다. |
| `max_connections` | 150 | 값 `max_connections` 매개 변수는 응용 프로그램 서버에 구성된 총 PHP 스레드 수와 상호 연관되어야 합니다. 일반적으로 소규모 환경에서는 300개, 중간 환경에서는 1,000개를 사용하는 것이 좋습니다. |
| `innodb_thread_concurrency` | 0 | 이 구성에 대한 최상의 값은 다음 공식에 의해 계산되어야 합니다. `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento은 다음을 적극 권장합니다. [!DNL Varnish] 를 저장소의 전체 페이지 캐시 서버로 사용합니다. PageCache 모듈은 코드 베이스에 계속 있지만, 개발 목적으로만 사용해야 합니다. 함께 또는 대신 사용해서는 안 됩니다. [!DNL Varnish].

설치 [!DNL Varnish] 웹 계층 앞에 있는 별도의 서버에서. 모든 수신 요청을 수락하고 캐시된 페이지 복사본을 제공해야 합니다. 허용하려면 [!DNL Varnish] 보안 페이지에서 효과적으로 작업하기 위해 SSL 종료 프록시를 앞에 배치할 수 있습니다. [!DNL Varnish]. Nginx를 이 용도로 사용할 수 있습니다.

[!DNL Commerce] 샘플 구성 파일 배포 [!DNL Varnish] (버전 4 및 5) - 성능에 대한 모든 권장 설정이 포함되어 있습니다. 성능 측면에서 가장 중요한 요소는 다음과 같습니다.

* **백엔드 상태 확인** 투표 [!DNL Commerce] 서버가 적시에 응답하고 있는지 여부를 판별하기 위한 서버.
* **유예 모드** 다음을 지시할 수 있습니다. [!DNL Varnish] 개체를 TTL(Time to Live) 기간 이상으로 캐시에 보관하고 다음의 오래된 콘텐츠를 제공합니다. [!DNL Commerce] 은(는) 정상이 아니거나 새 콘텐츠를 아직 가져오지 않은 경우 입니다.
* **Saint 모드** 비정상 블랙리스트 [!DNL Commerce] 서버를 구성합니다. 따라서 비정상 백엔드는 을 사용할 때 트래픽을 제공할 수 없습니다 [!DNL Varnish] 로드 밸런서로 사용됩니다.

다음을 참조하십시오 [고급 [!DNL Varnish] 구성](../configuration/cache/config-varnish-advanced.md) 를 참조하십시오.

### 에셋 성능 최적화

일반적으로 최적의 성능을 위해 CDN에 자산(이미지, JS, CSS 등)을 저장하는 것이 좋습니다.

사이트에 많은 수의 로케일을 배포할 필요가 없고 서버가 대다수 고객과 동일한 지역에 있는 경우 에셋을에 저장하면 저렴한 비용으로 상당한 성능 이득을 얻을 수 있습니다. [!DNL Varnish] CDN을 사용하는 대신

에셋을에 저장하려면 [!DNL Varnish]에 다음 VCL 항목을 추가합니다. `default.vcl` 파일 생성자 [!DNL Commerce] 대상 [!DNL Varnish] 5.

의 끝 `if` 의 PURGE 요청에 대한 명령문 `vcl_recv` 서브루틴, 추가:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

다음에서 `vcl_backend_response` 서브루틴, 다음을 찾음 `if` 에 대한 쿠키를 설정 해제하는 문 `GET` 또는 `HEAD` 요청.
업데이트됨 `if` 블록은 다음과 같아야 합니다.

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

다시 시작 [!DNL Varnish] 사이트를 업그레이드하거나 자산을 배포/업데이트할 때마다 캐시된 자산을 플러시하는 서버입니다.

## 캐싱 및 세션 서버

Magento은 Redis, Memcache, 파일 시스템, 데이터베이스 등 캐시 및 세션 데이터를 저장하는 다양한 옵션을 제공합니다. 이러한 옵션 중 일부는 아래에 설명되어 있습니다.

### 단일 웹 노드 설정

하나의 웹 노드만으로 모든 트래픽을 처리할 계획이라면, 원격 Redis 서버에 캐시를 두는 것은 적절하지 않습니다. 대신 파일 시스템 또는 로컬 Redis 서버를 사용합니다. 파일 시스템을 사용하려면 캐시 폴더를 RAM 파일 시스템에 마운트된 볼륨에 배치합니다. 로컬 Redis 서버를 사용하려면 HTTP를 통해 데이터를 교환하는 대신 직접 연결을 위한 소켓을 사용하도록 Redis를 구성하는 것이 좋습니다.

### 여러 웹 노드 설정

여러 웹 노드를 설정하는 경우 Redis가 가장 적합한 옵션입니다. 이유 [!DNL Commerce] 성능을 향상시키기 위해 많은 데이터를 적극적으로 캐시합니다. 웹 노드와 Redis 서버 사이의 네트워크 채널에 주목하십시오. 요청 처리를 위해 채널이 병목 현상이 되지 않도록 하려는 경우

>[!INFO]
>
>수백, 수천 개의 동시 요청을 처리해야 하는 경우 Redis 서버에 대한 최대 1Gbit(또는 더 넓은 채널)의 채널이 필요할 수 있습니다.
