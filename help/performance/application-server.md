---
title: GraphQL 애플리케이션 서버
description: Adobe Commerce 배포에서 GraphQL Application Server를 활성화하려면 다음 지침을 따르십시오.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b89ed5ddb4c6361de22d4a4439ffcfcc3ec8d474
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 0%

---


# GraphQL 애플리케이션 서버

Commerce GraphQL Application Server를 사용하면 Adobe Commerce에서 Commerce GraphQL API 요청 중 상태를 유지할 수 있습니다. Swool Extension에 구축된 GraphQL Application Server는 요청 처리를 처리하는 작업자 스레드를 사용하는 프로세스로 작동합니다. GraphQL Application Server는 GraphQL API 요청 중 부트스트랩된 애플리케이션 상태를 보존하여 요청 처리 및 전반적인 제품 성능을 향상시킵니다. API 요청의 효율성이 훨씬 향상되었습니다.

GraphQL Application Server는 Adobe Commerce에만 사용할 수 있습니다. Magento Open Source에 사용할 수 없습니다. 다음을 수행해야 합니다. [Adobe Commerce 지원 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) Pro 프로젝트에서 GraphQL Application Server를 활성화하는 티켓입니다.

>[!NOTE]
>
>GraphQL Application Server는 현재 와(과) 호환되지 않습니다. [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). 현재 사용 중인 클라우드 인프라의 Adobe Commerce 고객 [!DNL AWS S3] 대상 [원격 저장소](../configuration/remote-storage/cloud-support.md) Adobe에서 2024년 말에 핫픽스를 릴리스할 때까지 GraphQL Application Server를 사용할 수 없습니다.

## 아키텍처

GraphQL Application Server는 Commerce GraphQL API 요청 간 상태를 유지하고 부트스트래핑을 사용하지 않습니다. 프로세스 간에 애플리케이션 상태를 공유하면 GraphQL 요청의 효율성이 크게 향상되어 응답 시간이 최대 30%까지 줄어듭니다.

공유 없는 PHP 실행 모델은 각 요청이 프레임워크의 부트스트래핑을 요구하기 때문에 지연의 관점에서 도전을 제공합니다. 이 부트스트랩 프로세스에는 구성 읽기, 부트스트랩 프로세스 설정, 서비스 클래스 객체 작성 등 시간이 많이 소요되는 작업이 포함됩니다.

요청 처리 논리를 애플리케이션 수준의 이벤트 루프로 전환하면 엔터프라이즈 수준에서 요청 처리를 간소화하는 문제를 해결할 수 있습니다. 이 방법을 사용하면 요청 실행 라이프사이클 중에 부트스트래핑할 필요가 없습니다.

## 장점

GraphQL Application Server를 사용하면 Adobe Commerce에서 연속적인 Commerce GraphQL API 요청 간에 상태를 유지할 수 있습니다. 요청 간에 애플리케이션 상태를 공유하면 처리 오버헤드를 최소화하고 요청 처리를 최적화하여 API 요청 효율성이 향상됩니다. 따라서 GraphQL 요청 응답 시간을 최대 30%까지 줄일 수 있습니다.

## 시스템 요구 사항

GraphQL Application Server를 실행하려면 다음이 필요합니다.

* PHP 8.2 이상
* Swool PHP 확장 v5+ 설치됨
* 예상 로드에 따른 적절한 RAM 및 CPU

## 클라우드 인프라에서 활성화 및 배포

다음 `ApplicationServer` 모듈(`Magento/ApplicationServer/`) GraphQL Application Server를 활성화합니다.

### Pro 프로젝트 활성화

Pro 프로젝트에 GraphQL 애플리케이션 서버를 배포하기 전에 다음 단계를 완료하십시오.

1. 에서 클라우드 템플릿을 사용하여 클라우드 인프라에 Adobe Commerce 배포 [2.4.7-appserver 분기](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. 모든 상거래 사용자 지정 및 확장이 [호환 가능](https://developer.adobe.com/commerce/php/development/components/app-server/) GraphQL Application Server를 사용하는 경우입니다.
1. Commerce Cloud 프로젝트를 복제합니다.
1. 필요한 경우 &#39;application-server/nginx.conf.sample&#39; 파일에서 설정을 조정합니다.
1. 의 활성 &#39;웹&#39; 섹션에 주석 달기 `project_root/.magento.app.yaml` 전체 파일입니다.
1. 에서 다음 &#39;웹&#39; 섹션 구성의 주석 처리를 제거합니다. `project_root/.magento.app.yaml` GraphQL Application Server가 포함된 파일 `start` 명령입니다.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 다음 명령을 사용하여 업데이트된 파일을 git 인덱스에 추가합니다.

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Pro 프로젝트 배포

지원 단계를 완료한 후 변경 사항을 git 저장소에 푸시하여 GraphQL 애플리케이션 서버를 배포합니다.

```bash
git push
```

### 스타터 프로젝트 활성화

스타터 프로젝트에 GraphQL 애플리케이션 서버를 배포하기 전에 다음 단계를 완료하십시오.

1. 에서 클라우드 템플릿을 사용하여 클라우드 인프라에 Adobe Commerce 배포 [2.4.7-appserver 분기](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. 모든 Commerce 사용자 지정 및 확장이 GraphQL Application Server와 호환되는지 확인합니다.
1. 다음을 확인합니다. `CRYPT_KEY` 환경 변수가 인스턴스에 대해 설정됩니다. 클라우드 프로젝트 포털(온보딩 UI)에서 이 변수의 상태를 확인할 수 있습니다.
1. Commerce Cloud 프로젝트를 복제합니다.
1. 이름 바꾸기 `application-server/.magento/.magento.app.yaml.sample` 끝 `application-server/.magento/.magento.app.yaml` 필요한 경우 .magento.app.yaml에서 설정을 조정합니다.
1. 에서 다음 경로 구성의 주석 처리를 제거합니다. `project_root/.magento/routes.yaml` 리디렉션할 파일 `/graphql` GraphQL Application Server에 대한 트래픽.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 업데이트된 파일을 git 인덱스에 추가합니다.

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 변경 내용 커밋:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>루트의 모든 사용자 지정 설정이 `.magento.app.yaml` 파일이 적절하게 `application-server/.magento/.magento.app.yaml` 파일. 다음 이후 `application-server/.magento/.magento.app.yaml` 파일이 프로젝트에 추가되므로 루트와 함께 유지해야 합니다. `.magento.app.yaml` 파일. 예를 들어, [rabbitmq 구성](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) 또는 [웹 속성 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 에 동일한 구성을 추가해야 합니다. `application-server/.magento/.magento.app.yaml` 또한.

### 스타터 프로젝트 배포

지원 완료 후 [단계](#before-you-begin-a-cloud-starter-deployment), 변경 사항을 git 저장소에 푸시하여 GraphQL 애플리케이션 서버 배포:

```bash
git push
```

### 클라우드 프로젝트에 대한 지원 확인

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

1. SSH를 사용하여 클라우드 인스턴스에 액세스합니다. 다음 `project_root/var/log/application-server.log` 모든 GraphQL 요청에 대한 새 로그 레코드를 포함해야 합니다.

1. 다음 명령을 실행하여 GraphQL Application Server가 실행 중인지 확인할 수도 있습니다.

   ```bash
   ps aux|grep php
   ```

   다음이 표시됩니다. `bin/magento server:run` 여러 스레드를 사용한 프로세스입니다.

이러한 확인 단계가 성공하면 GraphQL Application Server가 실행되고 있으며 제공됩니다 `/graphql` 요청.

## 온-프레미스 프로젝트 활성화

다음 `ApplicationServer` 모듈(`Magento/ApplicationServer/`)은 GraphQL API용 GraphQL Application Server를 활성화합니다.

GraphQL Application Server를 로컬에서 실행하려면 Swool 확장을 설치하고 배포의 Nginx 구성 파일을 약간 변경해야 합니다.

### 전제 조건

를 활성화하기 전에 다음 단계를 완료하십시오. `ApplicationServer` 모듈:

* Nginx 구성
* Swool v5+ 확장 설치 및 구성

#### Nginx 구성

특정 상거래 배포에 따라 Nginx를 구성하는 방법이 결정됩니다. 일반적으로 Nginx 구성 파일의 기본 이름은 입니다 `nginx.conf` 및 는 다음 디렉터리 중 하나에 배치됩니다. `/usr/local/nginx/conf`, `/etc/nginx`, 또는 `/usr/local/etc/nginx`. 다음을 참조하십시오 [초급자 안내서](https://nginx.org/en/docs/beginners_guide.html) nginx 구성에 대한 자세한 내용은 을 참조하십시오.

샘플 Nginx 구성:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Swool 설치 및 구성

GraphQL Application Server를 로컬로 실행하려면 Swool 확장 프로그램(v5.0 이상)을 설치합니다. 이 확장을 설치하는 방법은 여러 가지가 있습니다.

다음 절차에서는 OSX 기반 시스템에 PHP 8.2용 Swool 확장을 설치하는 방법에 대해 설명합니다. Swool 확장을 설치하는 여러 방법 중 하나입니다.

```bash
pecl install swoole
```

설치하는 동안 Adobe Commerce에 대한 지원을 활성화하라는 메시지가 표시됩니다. `openssl`, `mysqlnd`, `sockets`, `http2`, 및 `postgres`. 입력 `yes` 을 제외한 모든 옵션 `postgres`.

### Swool 설치 확인

확장이 성공적으로 활성화되었는지 확인합니다.

```bash
php -m | grep swoole
```

### Swool 설치 시 발생하는 일반적인 오류

Swool 설치 중에 발생하는 모든 오류는 일반적으로 `pecl` 설치 단계. 일반적인 오류에는 누락이 포함됩니다 `openssl.h` 및 `pcre2.h` 파일. 이러한 오류를 해결하려면 이러한 두 패키지가 로컬 시스템에 설치되어 있는지 확인합니다.

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
pecl install swoole
```

#### pcre2.h 관련 문제 해결

관련 문제를 해결하려면 `pcre2.h`, 심볼릭 링크 `pcre2.h` 설치된 PHP 확장 디렉터리의 경로입니다. 설치된 특정 버전의 PHP와 `pcr2.h` 사용해야 하는 명령의 특정 버전을 결정합니다.

### GraphQL 애플리케이션 서버 실행

GraphQL 애플리케이션 서버 시작:

```bash
bin/magento server:run
```

이 명령은 9501에서 HTTP 포트를 시작합니다. GraphQL Application Server가 실행되면 포트 9501은 모든 GraphQL 쿼리에 대한 HTTP 프록시 서버가 됩니다.

GraphQL Application Server가 배포에서 실행 중인지 확인하려면 다음을 수행합니다.

```bash
ps aux | grep php
```

GraphQL Application Server가 실행 중인지 확인하는 추가 방법은 다음과 같습니다.

* 다음 확인: `/var/log/application-server.log` 처리된 GraphQL 요청과 관련된 항목에 대한 파일입니다.
* GraphQL Application Server가 실행되는 HTTP 포트에 연결해 보십시오. 예: `curl -g 'http://localhost:9501/graph`.

### GraphQL 요청이 처리 중인지 확인

GraphQL Application Server가 `X-Backend` 값이 있는 응답 헤더 `graphql_server` 처리되는 각 요청에 대해. GraphQL Application Server에서 요청을 처리했는지 확인하려면 이 응답 헤더를 확인합니다.

### 확장 및 사용자 지정 호환성 확인

확장 개발자 및 판매자는 먼저 확장 및 사용자 지정 코드가에 설명된 기술 지침을 준수하는지 확인해야 합니다 [기술 지침](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

코드 평가 시 다음 지침을 고려하십시오.

* 서비스 클래스(즉, 비헤이비어를 제공하지만 데이터는 제공하지 않는 클래스) `EventManager`) 상태를 변경할 수 없습니다.
* 시간 결합을 피하십시오.

## GraphQL 애플리케이션 서버 비활성화

GraphQL Application Server 비활성화 절차는 서버가 온-프레미스 또는 클라우드 배포에서 실행 중인지 여부에 따라 다릅니다.

### GraphQL 애플리케이션 서버(클라우드) 비활성화

1. 새 파일과 다른 코드 변경 사항이에 포함된 `AppServer Enabled` 배포를 준비하는 동안 커밋합니다.

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 다음 명령을 사용하여 이러한 변경 사항을 배포합니다.

   ```bash
   git push
   ```

### GraphQL 애플리케이션 서버 비활성화(온-프레미스)

1. 주석 달기 `/graphql` 섹션 / `nginx.conf` GraphQL Application Server를 활성화할 때 추가한 파일입니다.
1. nginx를 다시 시작합니다.

GraphQL Application Server를 비활성화하는 이 방법은 신속하게 성능을 테스트하거나 비교하는 데 유용할 수 있습니다.

### GraphQL Application Server가 비활성화되었는지 확인

GraphQL 요청이에 의해 처리 중인지 확인 `php-fpm` GraphQL Application Server 대신 다음 명령을 입력합니다. `ps aux | grep php`.

GraphQL Application Server가 비활성화된 후:

* `bin/magento server:run` 은(는) 비활성 상태입니다.
* `var/log/application-server.log` GraphQL 요청 뒤에 항목이 없습니다.

## GraphQL Application Server에 대한 통합 및 기능 테스트

확장 개발자는 두 가지 통합 테스트를 실행하여 GraphQL Application Server와의 확장 호환성을 확인할 수 있습니다. `GraphQlStateTest` 및 `ResetAfterRequestTest`.

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

확장 개발자는 GraphQL Application Server를 배포하는 동안 GraphQL에 대한 WebAPI 기능 테스트와 GraphQL에 대한 사용자 지정 자동화된 기능 테스트 또는 수동 기능 테스트를 실행해야 합니다. 이러한 기능 테스트는 개발자가 잠재적인 오류나 호환성 문제를 식별하는 데 도움이 됩니다.

#### 상태 모니터 모드

기능 테스트(또는 수동 테스트)를 실행하는 동안 애플리케이션 서버는 `--state-monitor mode` 상태가 의도하지 않게 재사용되는 클래스를 찾는 데 도움이 되도록 활성화되었습니다. 응용 프로그램 서버를 정상적으로 시작합니다. 단, `--state-monitor` 매개 변수.

```
bin/magento server:run --state-monitor
```

각 요청이 처리되면 새 파일이에 추가됩니다 `tmp` 디렉토리(예: ) `var/tmp/StateMonitor-thread-output-50-6nmxiK`. 테스트를 마치면 이러한 파일을 `bin/magento server:state-monitor:aggregate-output` 명령: 하나는 병합된 파일 두 개를 `XML` 및 1인치 `JSON`.

예:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

GraphQlStateTest와 같은 서비스 개체의 수정된 속성을 표시하는 XML 또는 JSON을 보는 데 사용하는 도구로 이러한 파일을 검사할 수 있습니다. 다음 `--state-monitor` 모드에서는 GraphQlStateTest와 동일한 건너뛰기 목록 및 필터 목록을 사용합니다.

>[!NOTE]
>
>를 사용하지 마십시오. `--state-monitor` 프로덕션의 모드 개발 및 테스트용으로만 설계되었습니다. 많은 출력 파일을 만들고 평소보다 느리게 실행됩니다.

>[!NOTE]
>
>`--state-monitor` 은(는) PHP 버전과 호환되지 않습니다. `8.3.0` - `8.3.4` PHP 가비지 수집기의 버그로 인해. PHP 8.3을 사용하는 경우 `8.3.5` 또는 이 기능을 사용하려면 그 이상이 필요합니다.

## 알려진 문제

### 작업자 스레드가 종료되는 경우 요청이 손실됩니다.

작업자 스레드에 문제가 있어 작업자 스레드가 종료되는 경우 동일한 작업자 스레드에 이미 큐에 있는 모든 HTTP 요청은 TCP 소켓 연결을 재설정합니다. 서버 앞에 NGIX와 같은 역방향 프록시가 있으면 이러한 오류가 다음과 같이 표시됩니다. `502` 오류. 작업자는 충돌로 사망할 수 있습니다, 메모리 킬러 또는 서드파티 확장의 PHP 오류. Swool HTTP Server의 기본 동작으로 인해 이 문제가 발생합니다. 기본적으로 HTTP 서버는에서 시작됩니다 `SWOOLE_BASE` 모드. 이 모드에서 들어오는 HTTP 요청은 작업자 스레드가 여전히 이전 요청을 처리 중인 경우에도 큐의 작업자 스레드에 할당됩니다. 이 항목을 로 변경하면 `SWOOLE_PROCESS` 그러면 주요 프로세스에 의해 연결이 유지되고 훨씬 더 많은 프로세스 간 통신을 사용합니다. 에 대한 단점 `SWOOLE_PROCESS` 그것은 PHP ZTS를 지원하지 않는다는 것입니다. 읽기 [Swool 설명서](https://wiki.swoole.com/en/#/learn?id=swoole_process) 추가 정보.

### 애플리케이션 서버는 특정 조건에서 이전 속성 구성을 사용할 수 있습니다.

다음 `CatalogGraphQl\Model\Config\AttributeReader` 위치: `2.4.7` GraphQL 요청이 이전 특성 구성 상태를 사용하여 응답을 받게 하는 드문 버그가 포함되어 있습니다. 이에 대한 수정 사항이에 게재됨 `2.4-develop`, 하지만 다음 시간 내 아님: `2.4.7` 릴리스.
