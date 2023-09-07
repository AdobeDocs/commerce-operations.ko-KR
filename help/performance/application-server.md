---
title: GraphQL API용 Application Server
description: Adobe Commerce 배포에서 GraphQL API용 Application Server를 활성화하려면 다음 지침을 따르십시오.
badgeCoreBeta: label="2.4.7-베타1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: 4f83a2181f6a7880b77dc07729574365def71f1d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# GraphQL API용 Application Server

GraphQL API용 Commerce Application Server를 사용하면 Adobe Commerce에서 Commerce GraphQL API 요청 간 상태를 유지하고 각 요청에 대한 부트스트랩 시간을 줄일 수 있습니다. 프로세스 간에 애플리케이션 상태를 공유하면 API 요청의 효율성이 훨씬 향상됩니다.

이 베타 버전의 응용 프로그램 서버는 PHP 8.1 또는 8.2를 실행하는 온-프레미스 배포에서만 사용할 수 있습니다. 클라우드 기반 배포를 지원하지 않습니다. 아직 B2B GraphQL 기능을 지원하지 않습니다. 이 버전의 PHP 애플리케이션 서버가 구성된 경우 GraphQL 요청이 온-프레미스 배포에서 예상대로 작동하지 않을 수 있습니다.

## Application Server를 사용할 수 있는 사용자

응용 프로그램 서버는 온-프레미스 Commerce 배포에서만 사용할 수 있습니다.

## GraphQL API용 Application Server 활성화

다음 `ApplicationServer` 모듈(`Magento/ApplicationServer/`) GraphQL API용 Application Server를 활성화합니다.

Application Server를 실행하려면 Open Swool 확장을 설치하고 이 응용 프로그램 서버를 로컬로 실행하려면 배포의 Nginx 구성 파일을 약간 변경해야 합니다.

### 시작하기 전에

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

PHP(v22)용 Open Swole 확장과 이 확장에 필요한 Composer 패키지를 하나의 명령으로 모두 설치할 수 있습니다.

### Open Swool 설치

다음을 입력합니다.

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
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
