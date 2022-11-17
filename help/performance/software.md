---
title: 소프트웨어 Recommendations
description: Adobe Commerce 및 Magento Open Source 배포의 최적 성능과 관련된 권장 소프트웨어 목록을 검토합니다.
source-git-commit: 8572cc8702d6f7e9c40b64110a9ba18aa5784f44
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---


# 소프트웨어 권장 사항

Adobe에서는 다음 소프트웨어를 [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx 및 [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] 또는 OpenSearch](../installation/prerequisites/search-engine/overview.md)

다중 서버 배포 또는 비즈니스 확장을 계획하는 상인의 경우 다음을 권장합니다.

* [[!DNL Varnish] 캐시](../configuration/cache/config-varnish.md)
* [레디스](../configuration/cache/redis-session.md) 세션(2.0.6 이상에서)
* Redis 인스턴스를 [기본 캐시](../configuration/cache/redis-pg-cache.md) (페이지 캐시에 이 인스턴스를 사용하지 마십시오.)

자세한 내용은 [시스템 요구 사항](../installation/system-requirements.md) 각 소프트웨어 유형의 지원되는 버전에 대한 정보.

## 운영 체제

운영 체제 구성 및 최적화는 [!DNL Commerce] 다른 고로드 웹 응용 프로그램과 비교한 것입니다. 서버에서 처리하는 동시 연결 수가 증가하면 사용 가능한 소켓 수가 완전히 할당될 수 있습니다. Linux 커널은 TCP 연결을 &quot;재사용&quot;하는 메커니즘을 지원합니다. 이 메커니즘을 활성화하려면 다음 값을 `/etc/sysctl.conf`:

>[!INFO]
>
>net.ipv4.tcp_tw_reuse를 활성화해도 들어오는 연결에 영향을 주지 않습니다.

```text
net.ipv4.tcp_tw_reuse = 1
```

커널 매개 변수 `net.core.somaxconn` 연결을 기다리는 최대 열린 소켓 수를 제어합니다. 이 값은 1024로 안전하게 증가시킬 수 있지만 이 양을 처리하는 서버의 기능과 상관관계가 있어야 합니다. 이 커널 매개 변수를 사용하려면 다음 값을 `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento은 PHP 7.3 및 7.4를 완전히 지원합니다. 요청 처리 시 최대 속도와 효율성을 얻으려면 PHP를 구성할 때 고려해야 할 몇 가지 요소가 있습니다.

### PHP 확장

활성 PHP 확장 목록을 필요한 확장으로 제한하는 것이 좋습니다 [!DNL Commerce] 기능을 사용할 수 있습니다.

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
* ext-pcre
* ext_pdo_mysql
* ext-simplexml
* ext-soap
* 외부 소켓
* 나트륨
* ext-tokenizer
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
* ext-pcre
* ext_pdo_mysql
* ext-simplexml
* ext-soap
* 외부 소켓
* 나트륨
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

확장을 더 추가하면 라이브러리 로드 시간이 증가합니다.

>[!INFO]
>
>`php-mcrypt` 이 PHP 7.2에서 제거되어 [`sodium` 라이브러리](https://www.php.net/manual/en/book.sodium.php). 확인 [나트륨](https://www.php.net/manual/en/sodium.installation.php) PHP를 업그레이드할 때 이 올바르게 활성화됩니다.

>[!INFO]
>
>프로파일링 및 디버깅 확장이 있으면 페이지의 응답 시간에 부정적인 영향을 줄 수 있습니다. 예를 들어 디버그 세션이 없는 활성 xDebug 모듈은 페이지 응답 시간을 최대 30%까지 늘릴 수 있습니다.

### PHP 설정

모든 사람의 성공적인 실행을 보장하기 위해 [!DNL Commerce] 데이터나 코드를 디스크에 덤프하지 않고 인스턴스를 다음과 같이 메모리 제한을 설정합니다.

```text
memory_limit=1G
```

디버깅을 위해 이 값을 2G로 늘립니다.

#### Realpath_cache 구성

개선 [!DNL Commerce] 성능, 다음 권장 사항을 추가하거나 업데이트합니다. `realpath_cache` 의 설정 `php.ini` 파일. 이 구성을 사용하면 PHP 프로세스가 페이지가 로드될 때마다 경로를 찾는 대신 파일에 대한 경로를 캐시할 수 있습니다. 자세한 내용은 [성능 조정](https://www.php.net/manual/en/ini.core.php) PHP 설명서에서 참조할 수 있습니다.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

최대 속도를 [!DNL Commerce] php 7에서는 OpCache 모듈을 활성화하고 올바르게 구성해야 합니다. 이러한 설정은 모듈에 권장됩니다.

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcache에 대한 메모리 할당을 세밀하게 조정할 때 Magento의 코드 베이스와 모든 확장의 크기를 고려합니다. Magento 성능 팀은 설치된 평균 확장 수에 대해 opcache에 충분한 공간을 제공하므로 이전 예제의 값을 사용하여 테스트합니다.

메모리 부족 컴퓨터가 있고 확장이나 사용자 지정 항목이 많지 않은 경우 다음 설정을 사용하여 유사한 결과를 얻으십시오.

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

를 활성화하는 것이 좋습니다 [PHP APCu 확장](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) 및 [구성 `composer` 그것을 지원하다](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) 을 추가하여 성능을 극대화할 수 있습니다. 이 확장은 열린 파일의 파일 위치를 캐시하여 성능을 높입니다 [!DNL Commerce] 페이지, Ajax 호출 및 끝점을 포함한 서버 호출.

편집 `apcu.ini` 다음을 포함할 파일:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## 웹 서버

Magento은 Nginx 및 Apache 웹 서버를 완전히 지원합니다. [!DNL Commerce] 에서는 샘플 권장 구성 파일을 제공합니다.  `<magento_home>/nginx.conf.sample` (Nginx) 및  `<magento_home>.htaccess.sample` (Apache) 파일.  Nginx 샘플에는 성능 향상을 위한 설정이 포함되어 있으며, 재구성이 거의 필요하지 않도록 설계되었습니다. 샘플 파일에 정의된 몇 가지 기본 구성 모범 사례는 다음과 같습니다.

* 브라우저에서 정적 콘텐츠를 캐시하는 설정
* PHP에 대한 메모리 및 실행 시간 설정
* 콘텐츠 압축 설정

아래 나열된 대로 입력 요청 처리를 위한 스레드 수도 구성해야 합니다.

| 웹 서버 | 속성 이름 | 위치 | 관련 정보 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [성능을 위한 NGINX 조정](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache 성능 조정](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM 공통 지시문](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

이 문서는 자세한 정보를 제공하지 않습니다 [!DNL MySQL] 조정 지침은 각 스토어와 환경이 다르기 때문에 조정되지만, 일반적인 권장 사항을 만들 수도 있습니다.

에 대한 많은 개선 사항이 있습니다 [!DNL MySQL] 5.7.9 당사는 [!DNL MySQL] 은 적절한 기본 설정으로 배포됩니다. 가장 중요한 설정은 다음과 같습니다.

| 매개 변수 | 기본값 | 설명 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 동일한 인스턴스에 액세스하려는 여러 스레드에 문제가 발생하지 않도록 기본값이 8로 설정되어 있습니다. |
| `innodb_buffer_pool_size` | 128MB | 위에 설명된 다중 풀 인스턴스와 결합하면 기본 메모리 할당이 1024MB입니다. 전체 크기는 모든 버퍼 풀 간에 나눠집니다. 최상의 효율성을 위해 다음 조합을 지정합니다. `innodb_buffer_pool_instances` 및 `innodb_buffer_pool_size` 따라서 각 버퍼 풀 인스턴스가 최소 1GB입니다. |
| `max_connections` | 150년 | 의 값 `max_connections` 매개 변수는 응용 프로그램 서버에 구성된 총 PHP 스레드 수와 상호 연결되어 있어야 합니다. 일반적인 권장 사항은 중소기업 300명, 중간 환경의 경우 1,000개입니다. |
| `innodb_thread_concurrency` | 0 | 이 구성에 대한 가장 좋은 값은 다음 공식을 사용하여 계산해야 합니다. `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

을 사용하는 것이 좋습니다. [!DNL Varnish] 를 저장소의 전체 페이지 캐시 서버로 사용합니다. PageCache 모듈은 여전히 코드 베이스에 있지만 개발 목적으로만 사용해야 합니다. 이 함수는 [!DNL Varnish].

설치 [!DNL Varnish] 웹 계층 앞에 있는 별도의 서버에서 모든 수신 요청을 수락하고 캐시된 페이지 사본을 제공해야 합니다. 허용 [!DNL Varnish] 보안 페이지를 사용하여 효과적으로 작업하려면 SSL 종료 프록시를 [!DNL Varnish]. Nginx는 이러한 용도로 사용할 수 있습니다.

[!DNL Commerce] 에 대한 샘플 구성 파일 배포 [!DNL Varnish] (버전 4 및 5) 성능 권장 설정이 모두 포함된 제품입니다. 성능 측면에서 가장 중요한 것은 다음과 같습니다.

* **백엔드 상태 확인** 여론 조사 [!DNL Commerce] 서버가 적시에 응답하는지 여부를 확인합니다.
* **유예 모드** 를 사용하면 [!DNL Varnish] 개체의 TTL(Time to Live) 기간을 초과하여 캐시에 저장하고 이 오래된 콘텐츠를 제공하는 경우 [!DNL Commerce] 은 정상이 아니거나 새 콘텐츠를 아직 가져오지 않은 경우 적합합니다.
* **Saint 모드** 블랙리스트에 비정상 [!DNL Commerce] 구성할 수 있는 시간에 대한 서버입니다. 따라서, 비정상 백엔드는 [!DNL Varnish] 로드 밸런서로서 사용됩니다.

자세한 내용은 [고급 [!DNL Varnish] 구성](../configuration/cache/config-varnish-advanced.md) 를 참조하십시오.

### 자산 성능 최적화

일반적으로 최적의 성능을 위해 CDN에 자산(이미지, JS, CSS 등)을 저장하는 것이 좋습니다.

사이트에 많은 로케일을 배포할 필요가 없고 서버가 다수의 고객과 동일한 영역에 있는 경우 자산을 에 저장하여 저가로 큰 성능 이득을 볼 수 있습니다 [!DNL Varnish] cdn을 사용하는 대신

자산을 [!DNL Varnish]에서 다음 VCL 항목을 추가합니다. `default.vcl` 생성된 파일 [!DNL Commerce] 대상 [!DNL Varnish] 5.

의 끝 `if` 다음에서 PURGE 요청에 대한 문 `vcl_recv` 서브루틴:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

에서 `vcl_backend_response` 서브루틴에서 `if` 쿠키의 설정을 해제하는 문 `GET` 또는 `HEAD` 요청.
업데이트된 내용 `if` 블록은 다음과 같이 표시되어야 합니다.

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

를 다시 시작합니다. [!DNL Varnish] 사이트를 업그레이드하거나 자산을 배포/업데이트할 때마다 캐시된 자산을 플러시할 서버입니다.

## 캐싱 및 세션 서버

Magento은 Redis, Memcache, 파일 시스템 및 데이터베이스를 포함하여 캐시 및 세션 데이터를 저장하는 다양한 옵션을 제공합니다. 이러한 옵션 중 일부는 아래에 설명되어 있습니다.

### 단일 웹 노드 설정

하나의 웹 노드만 사용하여 모든 트래픽을 제공하려는 경우 원격 Redis 서버에 캐시를 설정하는 것은 적합하지 않습니다. 대신 파일 시스템 또는 로컬 Redis 서버를 사용합니다. 파일 시스템을 사용하려면 캐시 폴더를 RAM 파일 시스템에 마운트된 볼륨에 넣습니다. 로컬 Redis 서버를 사용하려면 HTTP를 통해 데이터를 교환하는 대신 직접 연결에 소켓을 사용하도록 Redis를 구성하는 것이 좋습니다.

### 여러 웹 노드 설정

여러 웹 노드 설정의 경우 Redis가 가장 적합한 옵션입니다. 왜냐면 [!DNL Commerce] 성능을 향상시키기 위해 많은 데이터를 능동적으로 캐시하고, 웹 노드와 Redis 서버 간 네트워크 채널에 주의를 기울입니다. 채널이 요청 처리에 대한 병목 현상이 되지 않도록 합니다.

>[!INFO]
>
>수백, 수천 개의 동시 요청을 제공해야 하는 경우 Redis 서버에 최대 1Gbit(또는 그 이상)의 채널이 필요할 수 있습니다.
