---
title: GraphQL API용 Application Server
description: Adobe Commerce 배포에서 GraphQL API용 Application Server를 활성화하려면 다음 지침을 따르십시오.
badgeCoreBeta: label="2.4.7-베타" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# GraphQL API용 Application Server

GraphQL API용 Commerce Application Server를 사용하면 Adobe Commerce에서 Commerce GraphQL API 요청 중 상태를 유지할 수 있습니다. Open Swool 확장에 구축된 Application Server는 요청 처리를 처리하는 작업자 스레드를 사용하는 프로세스로 작동합니다. Application Server는 GraphQL API 요청 중 부트스트랩된 애플리케이션 상태를 보존하여 요청 처리 및 전반적인 제품 성능을 향상시킵니다. API 요청의 효율성이 훨씬 향상되었습니다.

Application Server는 Cloud Starter 및 온프레미스 배포에서만 지원됩니다. Beta 중에는 Cloud Pro 인스턴스에서 사용할 수 없습니다. Magento Open Source 배포에는 사용할 수 없습니다.

## Application Server 아키텍처 개요

Application Server는 Commerce GraphQL API 요청 사이의 상태를 유지하고 부트스트래핑을 사용하지 않습니다. 프로세스 간에 애플리케이션 상태를 공유하면 GraphQL 요청의 효율성이 크게 향상되어 응답 시간이 최대 30%까지 줄어듭니다.

공유 없는 PHP 실행 모델은 각 요청이 프레임워크의 부트스트래핑을 요구하기 때문에 지연의 관점에서 도전을 제공합니다. 이 부트스트랩 프로세스에는 구성 읽기, 부트스트랩 프로세스 설정, 서비스 클래스 객체 작성 등 시간이 많이 소요되는 작업이 포함됩니다.

요청 처리 논리를 애플리케이션 수준의 이벤트 루프로 전환하면 엔터프라이즈 수준에서 요청 처리를 간소화하는 문제를 해결할 수 있습니다. 이 방법을 사용하면 요청 실행 라이프사이클 중에 부트스트래핑할 필요가 없습니다.

## 애플리케이션 서버 사용의 이점

Application Server를 사용하면 Adobe Commerce에서 연속적인 Commerce GraphQL API 요청 간에 상태를 유지할 수 있습니다. 요청 간에 애플리케이션 상태를 공유하면 처리 오버헤드를 최소화하고 요청 처리를 최적화하여 API 요청 효율성이 향상됩니다. 따라서 GraphQL 요청 응답 시간을 최대 30%까지 줄일 수 있습니다.

## 시스템 요구 사항

응용 프로그램 서버를 실행하려면 다음이 필요합니다.

* PHP 8.2 이상
* Windows PHP 확장 v22+ 설치 열기
* 예상 로드에 따른 적절한 RAM 및 CPU

## Cloud Starter용 Application Server 활성화

다음 `ApplicationServer` 모듈(`Magento/ApplicationServer/`) GraphQL API용 Application Server를 활성화합니다. Application Server는 온-프레미스 및 Cloud Starter 배포에서만 지원됩니다. Beta 중에는 Cloud Pro 인스턴스에서 사용할 수 없습니다.

### Cloud Starter 배포를 시작하기 전에

응용 프로그램 서버를 배포하기 전에 다음 작업을 완료하십시오.

1. Adobe Commerce이 Commerce Cloud에 설치되어 있는지 확인합니다.
1. 다음을 확인합니다. `CRYPT_KEY` 환경 변수가 인스턴스에 대해 설정됩니다. 클라우드 프로젝트 포털(온보딩 UI)에서 이 변수의 상태를 확인할 수 있습니다.
1. Commerce Cloud 프로젝트를 복제합니다.
1. 만들기 `graphql` 폴더의 폴더 `project_root` 폴더를 삭제합니다.
1. 추가 사용자 정의 추가 `.magento.app.yaml` 에 포함된 파일 [magento.app.yaml 파일 컨텐츠](#magento.app.yaml-file-content) 을(를) 대상으로 한 주제 `project_root/graphql` 폴더를 삭제합니다.
1. 편집 `project_root/.magento/routes.yaml` 다음 지시문을 포함할 파일:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. 다음 명령을 사용하여 업데이트된 파일을 git 인덱스에 추가합니다.

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Cloud Starter에 애플리케이션 서버 배포

전제 조건 작업을 수행한 후 다음 명령을 사용하여 Application Server를 배포합니다.

```bash
git push
```

### Cloud Starter에서 Application Server 활성화 확인

1. 클라우드 프로젝트 사용자 인터페이스를 엽니다. 다음에 대한 추가 SSH 액세스 포인트가 표시됩니다. `graphql` 응용 프로그램.

1. SSH를 사용하여 graphql 애플리케이션 액세스 포인트를 사용하여 클라우드 인스턴스에 액세스한 다음 다음 명령을 실행합니다.

   ```bash
   ps aux|grep php
   ```

1. 인스턴스에 대해 GraphQL 쿼리 또는 돌연변이를 수행하여 `graphql` 엔드포인트에 액세스할 수 있습니다. For example:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   예상 응답은 다음 예제와 유사해야 합니다.

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. SSH를 사용하여 GraphQL 애플리케이션 액세스 포인트를 통해 클라우드 인스턴스에 액세스합니다. 다음 `project_root/var/log/magento-server.log` 모든 GraphQL 요청에 대한 새 로그 레코드를 포함해야 합니다.

이러한 확인 단계가 성공하면 테스트 주기 실행을 계속할 수 있습니다.


## Application Server 온-프레미스 배포 사용

다음 `ApplicationServer` 모듈(`Magento/ApplicationServer/`) GraphQL API용 Application Server를 활성화합니다.

Application Server를 실행하려면 Open Swool 확장을 설치하고 이 응용 프로그램 서버를 로컬로 실행하려면 배포의 Nginx 구성 파일을 약간 변경해야 합니다.

### 온-프레미스 배포를 시작하기 전에

활성화하기 전에 다음 두 작업을 완료하십시오. `ApplicationServer` 모듈:

* Nginx 구성

* Open Swool v22 확장 설치 및 구성

### Nginx 구성

특정 상거래 배포에 따라 Nginx를 구성하는 방법이 결정됩니다. 일반적으로 Nginx 구성 파일의 기본 이름은 입니다 `nginx.conf` 및 는 다음 디렉터리 중 하나에 배치됩니다. `/usr/local/nginx/conf`, `/etc/nginx`, 또는 `/usr/local/etc/nginx`. 다음을 참조하십시오 [초급자 안내서](https://nginx.org/en/docs/beginners_guide.html) nginx 구성에 대한 자세한 내용은 을 참조하십시오.

샘플 Nginx 구성:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Open Swool 설치 및 구성

응용 프로그램 서버를 로컬로 실행하려면 Open Swool v22 확장을 설치합니다. 이 확장을 설치하는 방법은 여러 가지가 있습니다.

## 응용 프로그램 서버 실행

응용 프로그램 서버를 시작합니다.

```bash
bin/magento server:run
```

이 명령은 9501에서 HTTP 포트를 시작합니다. Application Server가 실행되면 포트 9501은 모든 GraphQL 쿼리에 대한 HTTP 프록시 서버가 됩니다.

## 예: Open Swool(OSX) 설치

이 절차는 OSX 기반 시스템용 PHP 8.2에 Open Swool 확장을 설치하는 방법을 보여줍니다. Open Swool 확장을 설치하는 여러 방법 중 하나입니다.

### Open Swool 설치

다음을 입력합니다.

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

설치하는 동안 Adobe Commerce에 대한 지원을 활성화하라는 메시지가 표시됩니다. `openssl`, `mysqlnd`, `sockets`, `http2`, 및 `postgres`. 입력 `yes` 을 제외한 모든 옵션 `postgres`.

### Open Swool 설치 확인

실행 `php -m | grep openswoole` 확장이 성공적으로 활성화되었는지 확인합니다.

### Open Swool 설치 시 발생하는 일반적인 오류

Open Swool 설치 중에 발생하는 모든 오류는 일반적으로 `pecl` 설치 단계. 일반적인 오류에는 누락이 포함됩니다 `openssl.h` 및 `pcre2.h` 파일. 이러한 오류를 해결하려면 이러한 두 패키지가 로컬 시스템에 설치되어 있는지 확인합니다.

* 위치 확인 `openssl` 다음을 실행함으로써:

```bash
openssl version -d
```

이 명령은 경로를 표시합니다. `openssl` 이(가) 설치되었습니다.

* 위치 확인 `pcre2` 다음을 실행함으로써:

```bash
pcre2-config --prefix 
```

명령 출력에서 파일이 누락되었음을 나타내는 경우 Homebrew를 사용하여 누락된 패키지를 설치합니다.

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### openssl 문제 해결

관련 문제를 해결하려면 `openssl`, 실행:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

로컬의 경로를 사용 중인지 확인합니다. `dev` 환경.

#### openssl 관련 문제 해결 확인

다음 명령을 다시 실행하여 openssl 관련 문제가 해결되었는지 확인할 수 있습니다.

```bash
pecl install openswoole-22.0.0
```

#### pcre2.h 관련 문제 해결

관련 문제를 해결하려면 `pcre2.h`, 심볼릭 링크 `pcre2.h` 설치된 PHP 확장 디렉터리의 경로입니다. 설치된 특정 버전의 PHP와 `pcr2.h` 사용해야 하는 명령의 특정 버전을 결정합니다.

### 애플리케이션 서버가 실행 중인지 확인

응용 프로그램 서버가 배포에서 실행 중인지 확인하려면 다음 명령을 실행합니다.

```bash
ps aux | grep php
```

Application Server가 실행 중인지 확인하는 추가 방법은 다음과 같습니다.

* 다음 확인: `/var/log/magento-server.log` 처리된 GraphQL 요청과 관련된 항목에 대한 파일입니다.
* 응용 프로그램 서버가 실행되는 HTTP 포트에 연결하십시오. For example: `curl -g 'http://localhost:9501/graph`.

### GraphQL 요청이 애플리케이션 서버에서 처리 중인지 확인

Application Server가 `X-Backend` 값이 있는 응답 헤더 `graphql_server` 처리되는 각 요청에 대해. 요청이 Application Server에서 처리되었는지 확인하려면 이 응답 헤더를 확인합니다.

### 애플리케이션 서버와의 확장 및 사용자 지정 호환성 확인

확장 개발자 및 판매자는 먼저 확장 및 사용자 지정 코드가에 설명된 기술 지침을 준수하는지 확인해야 합니다 [기술 지침](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

코드 평가 시 다음 지침을 고려하십시오.

* 서비스 클래스(즉, 비헤이비어를 제공하지만 데이터는 제공하지 않는 클래스) `EventManager`) 상태를 변경할 수 없습니다.
* 시간 결합을 피하십시오.

## 응용 프로그램 서버 사용 안 함

응용 프로그램 서버를 사용하지 않도록 설정하는 절차는 서버가 온-프레미스에서 실행 중인지 또는 클라우드 배포에서 실행 중인지 여부에 따라 다릅니다.

### Cloud Starter에서 Application Server 비활성화

1. 새 파일과 다른 코드 변경 사항이에 포함된 `AppServer Enabled` 배포를 준비하는 동안 커밋합니다.

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 다음 명령을 사용하여 이러한 변경 사항을 배포합니다.

   ```bash
   git push
   ```

### 응용 프로그램 서버 사용 안 함

1. 주석 달기 `/graphql` 섹션 / `nginx.conf` Application Server를 활성화할 때 추가한 파일입니다.
1. nginx를 다시 시작합니다.

애플리케이션 서버를 비활성화하는 이 방법은 신속하게 성능을 테스트하거나 비교하는 데 유용할 수 있습니다.

### Application Server가 비활성화되었는지 확인

GraphQL 요청이에 의해 처리 중인지 확인 `php-fpm` Application Server 대신 다음 명령을 입력합니다. `ps aux | grep php`.

Application Server가 비활성화된 후:

* `bin/magento server:run` 은(는) 비활성 상태입니다.
* `var/log/magento-server.log` GraphQL 요청 뒤에 항목이 없습니다.

## PHP 응용 프로그램 서버에 대한 통합 및 기능 테스트

확장 개발자는 두 가지 통합 테스트를 실행하여 확장 호환성 및 애플리케이션 서버와의 호환성을 확인할 수 있습니다. `GraphQlStateTest` 및 `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` 은(는) 공유 객체에서 여러 요청에 재사용해서는 안 되는 상태를 감지합니다.

이 테스트는 가 생성하는 서비스 개체의 상태 변경을 검색하도록 설계되었습니다. `ObjectManager`. 테스트에서는 동일한 GraphQL 쿼리를 두 번 실행하고 두 번째 쿼리 전후의 서비스 개체 상태를 비교합니다. 

#### GraphQlStateTest 실패 및 잠재적인 개선 사항

* **목록을 추가, 건너뛰거나 필터링할 수 없음**. 목록을 추가, 건너뛰기 또는 필터링하는 것이 안전하지 않다는 오류가 발생하면 상태를 변경할 수 있는 서비스 클래스의 팩토리를 사용하기 위해 이전 버전과 호환되는 방식으로 클래스를 리팩터링할 수 있는지 여부를 고려하십시오.

* **클래스에 변경 가능한 상태가 표시됩니다.**. 클래스 자체가 변경 가능한 상태를 표시하는 경우 이 상태를 우회하도록 코드를 다시 작성하십시오. 성능상의 이유로 변경 가능한 상태가 필요한 경우 `ResetAfterRequestInterface` 및 사용 `_resetState()` 객체를 초기 생성 상태로 재설정합니다.

* **입력 속성 $x은(는) 초기화 메시지 전에 액세스하면 안 됩니다.**. 이 유형의 메시지가 실패하면 지정된 속성이 생성자에 의해 초기화되지 않았음을 나타냅니다. 이는 객체가 처음 구성된 후에는 사용할 수 없기 때문에 발생하는 시간적 결합의 형태이다. 속성에서 데이터를 검색하는 Collector가 PHP 반사 기능을 사용하기 때문에 속성이 비공개인 경우에도 이러한 결합이 발생합니다. 이 경우, 시간적 결합을 피하고 변경 가능한 상태를 피하도록 클래스를 리팩터링해 보십시오. 리팩터링으로 오류가 해결되지 않으면 속성 형식을 null 허용 형식으로 변경하여 null로 초기화할 수 있습니다.  속성이 배열인 경우 속성을 빈 배열로 초기화해 보십시오.

실행 `GraphQlStateTest` 실행함으로써 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` 를 구현하는 모든 클래스를 찾습니다. `ResetAfterRequestInterface` 및 확인 `_resetState()` 메서드는에서 빌드한 후 유지한 것과 동일한 상태로 개체의 상태를 반환합니다. `ObjectManager`.  이 테스트는 다음을 사용하여 서비스 개체를 만듭니다. `ObjectManager`, 그런 다음 해당 개체를 복제합니다. `_resetState()`를 클릭한 다음 두 개체를 비교합니다. 테스트에서는 개체 인스턴스화와 사이에 메서드를 호출하지 않습니다. `_resetState()`따라서 변경할 수 있는 상태 재설정을 확인하지 않습니다. 버그 또는 오타가 있는 곳에서 문제를 발견합니다 `_resetState()` 은 상태를 원래 상태와는 다른 것으로 설정할 수 있습니다.

#### ResetAfterRequestTest 실패 및 잠재적인 재구성

* **클래스에 일관되지 않은 속성 값이 있습니다.**. 이 테스트가 실패할 경우 클래스가 변경되었는지 확인하고, 그 결과 작성 후 개체의 속성 값이 작성 후 개체와 다른 경우 `_resetState()` 메서드가 호출됩니다. 작업 중인 클래스에 `_resetState()` 메서드 자체를 실행한 다음 클래스 계층 구조에서 슈퍼클래스를 구현하는 슈퍼클래스를 확인합니다.

* **입력 속성 $x은(는) 초기화 메시지 전에 액세스하면 안 됩니다.**. 이 문제는 또한 `GraphQlStateTest`.
 
실행 `ResetAfterRequestTest` 다음을 실행하여: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### 기능 테스트

확장 개발자는 Application Server를 배포하는 동안 GraphQL에 대한 WebAPI 기능 테스트와 GraphQL에 대한 사용자 정의 자동화된 기능 테스트 또는 수동 기능 테스트를 실행해야 합니다. 이러한 기능 테스트는 개발자가 잠재적인 오류나 호환성 문제를 식별하는 데 도움이 됩니다.

## magento.app.yaml 파일 컨텐츠

다음을 참조하십시오 [Cloud Starter 배포를 시작하기 전에](#Before-you-begin-a-Cloud-Starter-deployment) 에 다음 코드를 추가하는 방법에 대한 지침은 `project_root/graphql` 폴더를 삭제합니다.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
