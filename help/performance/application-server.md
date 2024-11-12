---
title: GraphQL 애플리케이션 서버
description: Adobe Commerce 배포에서 GraphQL Application Server를 활성화하려면 다음 지침을 따르십시오.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c5446f0273705b158297c0a253054742ec95b44e
workflow-type: tm+mt
source-wordcount: '2082'
ht-degree: 0%

---


# GraphQL 애플리케이션 서버

Commerce GraphQL Application Server를 사용하면 Adobe Commerce에서 Commerce GraphQL API 요청 중 상태를 유지할 수 있습니다. Swool Extension에 구축된 GraphQL Application Server는 요청 처리를 처리하는 작업자 스레드를 사용하는 프로세스로 작동합니다. GraphQL Application Server는 GraphQL API 요청 중 부트스트랩된 애플리케이션 상태를 보존하여 요청 처리 및 전반적인 제품 성능을 향상시킵니다. API 요청의 효율성이 훨씬 향상되었습니다.

GraphQL Application Server는 Adobe Commerce에만 사용할 수 있습니다. Magento Open Source에 사용할 수 없습니다. Cloud Pro 프로젝트의 경우 GraphQL Application Server를 사용하려면 [Adobe Commerce 지원 제출](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) 티켓을 제출해야 합니다.

>[!NOTE]
>
>GraphQL Application Server는 현재 [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/)과(와) 호환되지 않습니다. 현재 [원격 저장소](../configuration/remote-storage/cloud-support.md)에 대해 [!DNL AWS S3]을(를) 사용하는 클라우드 인프라의 Adobe Commerce 고객은 Adobe이 2024년 말에 핫픽스를 릴리스할 때까지 GraphQL Application Server를 사용할 수 없습니다.

## 아키텍처

GraphQL Application Server는 Commerce GraphQL API 요청 간 상태를 유지하므로 부트스트래핑이 필요하지 않습니다. 프로세스 간에 애플리케이션 상태를 공유하면 GraphQL 요청의 효율성이 크게 향상되어 응답 시간이 최대 30%까지 줄어듭니다.

공유 없는 PHP 실행 모델은 각 요청이 프레임워크의 부트스트래핑을 요구하기 때문에 지연의 관점에서 도전을 제공합니다. 이 부트스트랩 프로세스에는 구성 읽기, 부트스트랩 프로세스 설정, 서비스 클래스 객체 작성 등 시간이 많이 소요되는 작업이 포함됩니다.

요청 처리 논리를 애플리케이션 수준의 이벤트 루프로 전환하면 엔터프라이즈 수준에서 요청 처리를 간소화하는 문제를 해결할 수 있습니다. 이 방법을 사용하면 요청 실행 라이프사이클 중에 부트스트래핑할 필요가 없습니다.

## 장점

GraphQL Application Server를 사용하면 Adobe Commerce에서 연속적인 Commerce GraphQL API 요청 간에 상태를 유지할 수 있습니다. 요청 간에 애플리케이션 상태를 공유하면 처리 오버헤드를 최소화하고 요청 처리를 최적화하여 API 요청 효율성이 향상됩니다. 따라서 GraphQL 요청 응답 시간을 최대 30%까지 줄일 수 있습니다.

## 시스템 요구 사항

GraphQL Application Server를 실행하려면 다음이 필요합니다.

* Commerce 버전 2.4.7+
* PHP 8.2 이상
* Swool PHP 확장 v5+ 설치됨
* 예상 로드에 따른 적절한 RAM 및 CPU

## 클라우드 인프라에서 활성화 및 배포

`ApplicationServer` 모듈(`Magento/ApplicationServer/`)은 GraphQL Application Server를 사용하도록 설정합니다.

### Pro 프로젝트 활성화

>[!NOTE]
>
>애플리케이션 서버는 Cloud Pro 인스턴스의 옵트인 기능입니다. 활성화하려면 지원 요청을 제출하십시오.

Pro 프로젝트에서 Application Server 기능을 활성화한 후 GraphQL Application Server를 배포하기 전에 다음 단계를 완료하십시오.

1. [2.4.7-appserver 분기](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)의 클라우드 템플릿을 사용하여 클라우드 인프라에 Adobe Commerce을 배포합니다.
1. 모든 Commerce 사용자 지정 및 확장이 GraphQL Application Server와 [호환](https://developer.adobe.com/commerce/php/development/components/app-server/)되는지 확인하십시오.
1. Commerce Cloud 프로젝트를 복제합니다.
1. 필요한 경우 &#39;application-server/nginx.conf.sample&#39; 파일에서 설정을 조정합니다.
1. `project_root/.magento.app.yaml` 파일의 활성 &#39;웹&#39; 섹션을 완전히 주석 처리하십시오.
1. GraphQL Application Server `start` 명령이 포함된 `project_root/.magento.app.yaml` 파일에서 다음 &#39;웹&#39; 섹션 구성의 주석 처리를 제거하십시오.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 다음 명령을 실행하여 `/application-server/start.sh`을(를) 실행할 수 있는지 확인하십시오.

   ```bash
   chmod +x application-server/start.sh
   ```

1. 다음 명령을 사용하여 업데이트된 파일을 git 인덱스에 추가합니다.

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Pro 프로젝트 배포

지원 단계를 완료한 후 변경 사항을 Git 저장소에 푸시하여 GraphQL 애플리케이션 서버를 배포합니다.

```bash
git push
```

### 스타터 프로젝트 활성화

스타터 프로젝트에 GraphQL 애플리케이션 서버를 배포하기 전에 다음 단계를 완료하십시오.

1. [2.4.7-appserver 분기](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)의 클라우드 템플릿을 사용하여 클라우드 인프라에 Adobe Commerce을 배포합니다.
1. 모든 Commerce 사용자 지정 및 확장이 GraphQL Application Server와 호환되는지 확인합니다.
1. 인스턴스에 대해 `CRYPT_KEY` 환경 변수가 설정되어 있는지 확인하십시오. 클라우드 콘솔에서 이 변수의 상태를 확인할 수 있습니다.
1. Commerce Cloud 프로젝트를 복제합니다.
1. `application-server/.magento/.magento.app.yaml.sample`의 이름을 `application-server/.magento/.magento.app.yaml`(으)로 변경하고 필요한 경우 .magento.app.yaml에서 설정을 조정합니다.
1. `project_root/.magento/routes.yaml` 파일에서 다음 경로의 구성 주석을 제거하여 `/graphql` 트래픽을 GraphQL Application Server로 리디렉션합니다.

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
>루트 `.magento.app.yaml` 파일의 모든 사용자 지정 설정이 `application-server/.magento/.magento.app.yaml` 파일로 적절하게 마이그레이션되었는지 확인하십시오. `application-server/.magento/.magento.app.yaml` 파일이 프로젝트에 추가되면 루트 `.magento.app.yaml` 파일뿐 아니라 유지해야 합니다. 예를 들어 [RabbitMQ 서비스를 구성](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq)하거나 [웹 속성을 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property)해야 하는 경우 `application-server/.magento/.magento.app.yaml`에도 동일한 구성을 추가해야 합니다.

### 스타터 프로젝트 배포

활성화 [단계](#before-you-begin-a-cloud-starter-deployment)를 완료한 후 변경 내용을 Git 저장소에 푸시하여 GraphQL 애플리케이션 서버를 배포합니다.

```bash
git push
```

### 클라우드 프로젝트에 대한 지원 확인

1. 인스턴스에 대해 GraphQL 쿼리 또는 돌연변이를 수행하여 `graphql` 끝점에 액세스할 수 있는지 확인합니다. For example:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   예상 응답은 다음 예제와 유사해야 합니다.

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. SSH를 사용하여 클라우드 인스턴스에 액세스합니다. `project_root/var/log/application-server.log`에는 모든 GraphQL 요청에 대한 새 로그 레코드가 포함되어야 합니다.

1. 다음 명령을 실행하여 GraphQL Application Server가 실행 중인지 확인할 수도 있습니다.

   ```bash
   ps aux|grep php
   ```

   여러 스레드가 있는 `bin/magento server:run` 프로세스가 표시됩니다.

이러한 확인 단계가 성공하면 GraphQL Application Server가 실행되고 `/graphql`개의 요청을 제공합니다.

## 온-프레미스 프로젝트 활성화

`ApplicationServer` 모듈(`Magento/ApplicationServer/`)은 GraphQL API용 GraphQL Application Server를 사용하도록 설정합니다.

GraphQL Application Server를 로컬에서 실행하려면 Swool 확장을 설치하고 배포의 Nginx 구성 파일을 약간 변경해야 합니다.

### 전제 조건

`ApplicationServer` 모듈을 활성화하기 전에 다음 단계를 완료하십시오.

* Nginx 구성
* Swool v5+ 확장 설치 및 구성

#### Nginx 구성

특정 Commerce 배포에 따라 Nginx 구성 방법이 결정됩니다. 일반적으로 Nginx 구성 파일은 기본적으로 이름이 `nginx.conf`이고 다음 디렉터리 중 하나에 배치됩니다. `/usr/local/nginx/conf`, `/etc/nginx` 또는 `/usr/local/etc/nginx`. Nginx 구성에 대한 자세한 내용은 _[초보자 안내서](https://nginx.org/en/docs/beginners_guide.html)_&#x200B;를 참조하십시오.

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

설치하는 동안 Adobe Commerce은 `openssl`, `mysqlnd`, `sockets`, `http2` 및 `postgres`에 대한 지원을 사용하도록 설정하는 프롬프트를 표시합니다. `postgres`을(를) 제외한 모든 옵션에 대해 `yes`을(를) 입력하십시오.

### Swool 설치 확인

확장이 성공적으로 활성화되었는지 확인합니다.

```bash
php -m | grep swoole
```

### Swool 설치 시 발생하는 일반적인 오류

Swool 설치 중에 발생하는 모든 오류는 일반적으로 `pecl` 설치 단계에서 발생합니다. 일반적인 오류에는 누락된 `openssl.h` 및 `pcre2.h` 파일이 포함됩니다. 이러한 오류를 해결하려면 이러한 두 패키지가 로컬 시스템에 설치되어 있는지 확인합니다.

* 다음을 실행하여 `openssl`의 위치를 확인하세요.

```bash
openssl version -d
```

이 명령은 `openssl`이(가) 설치된 경로를 표시합니다.

* 다음을 실행하여 `pcre2`의 위치를 확인하세요.

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

`openssl`과(와) 관련된 문제를 해결하려면 다음을 실행하십시오.

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

로컬 `dev` 환경의 경로를 사용하고 있는지 확인하십시오.

#### openssl 관련 문제 해결 확인

다음 명령을 다시 실행하여 openssl 관련 문제가 해결되었는지 확인할 수 있습니다.

```bash
pecl install swoole
```

#### pcre2.h 관련 문제 해결

`pcre2.h`과(와) 관련된 문제를 해결하려면 설치된 PHP 확장 디렉터리에 `pcre2.h` 경로를 심볼릭 링크하십시오. 설치된 특정 버전의 PHP와 `pcr2.h`은(는) 사용해야 하는 명령의 특정 버전을 결정합니다.

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

* 처리된 GraphQL 요청과 관련된 항목이 있는지 `/var/log/application-server.log` 파일을 확인하십시오.
* GraphQL Application Server가 실행되는 HTTP 포트에 연결해 보십시오. 예: `curl -g 'http://localhost:9501/graph`.

### GraphQL 요청이 처리 중인지 확인

GraphQL Application Server는 처리하는 각 요청에 값 `graphql_server`이(가) 있는 `X-Backend` 응답 헤더를 추가합니다. GraphQL Application Server에서 요청을 처리했는지 여부를 확인하려면 이 응답 헤더를 확인합니다.

### 확장 및 사용자 지정 호환성 확인

확장 개발자 및 판매자는 먼저 확장 및 사용자 지정 코드가 _[기술 지침](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_&#x200B;에 설명된 지침을 준수하는지 확인해야 합니다.

코드 평가 시 다음 지침을 고려하십시오.

* 서비스 클래스(즉, 동작을 제공하지만 데이터는 제공하지 않는 클래스(예: `EventManager`) 상태를 변경할 수 없습니다.
* 시간 결합을 피하십시오.

## GraphQL 애플리케이션 서버 비활성화

GraphQL Application Server 비활성화 절차는 서버가 온-프레미스 또는 클라우드 배포에서 실행 중인지 여부에 따라 다릅니다.

### GraphQL 애플리케이션 서버(클라우드) 비활성화

1. 배포를 준비하는 동안 `AppServer Enabled` 커밋에 포함된 새 파일과 다른 코드 변경 내용을 모두 제거합니다.

1. 다음 명령을 사용하여 변경 내용을 커밋합니다.

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 다음 명령을 사용하여 이러한 변경 사항을 배포합니다.

   ```bash
   git push
   ```

### GraphQL 애플리케이션 서버 비활성화(온-프레미스)

1. GraphQL Application Server를 사용하도록 설정할 때 추가한 `nginx.conf` 파일의 `/graphql` 섹션을 주석 처리합니다.
1. nginx를 다시 시작합니다.

GraphQL 애플리케이션 서버를 비활성화하는 이 방법은 성능을 빠르게 테스트하거나 비교하는 데 유용할 수 있습니다.

### GraphQL Application Server가 비활성화되었는지 확인

`php-fpm`이(가) GraphQL Application Server 대신 GraphQL 요청을 처리하고 있는지 확인하려면 다음 명령을 입력하십시오. `ps aux | grep php`.

GraphQL Application Server가 비활성화된 후:

* `bin/magento server:run`이(가) 비활성 상태입니다.
* `var/log/application-server.log`에 GraphQL 요청 후 항목이 없습니다.

## GraphQL Application Server에 대한 통합 및 기능 테스트

확장 개발자는 두 가지 통합 테스트를 실행하여 GraphQL Application Server와의 확장 호환성을 확인할 수 있습니다. `GraphQlStateTest` 및 `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest`이(가) 공유 개체에서 여러 요청에 다시 사용해서는 안 되는 상태를 감지합니다.

이 테스트는 `ObjectManager`에서 생성한 서비스 개체의 상태 변경을 검색하도록 설계되었습니다. 테스트에서는 동일한 GraphQL 쿼리를 두 번 실행하고 두 번째 쿼리 전후의 서비스 개체 상태를 비교합니다.

#### GraphQlStateTest 실패 및 잠재적인 개선 사항

* **목록을 추가, 건너뛰기 또는 필터링할 수 없음**. 목록 추가, 건너뛰기 또는 필터링에 대한 오류가 표시되면 상태를 변경할 수 있는 서비스 클래스의 팩토리를 사용하기 위해 이전 버전과 호환되는 방식으로 클래스를 리팩터링할 수 있는지 여부를 고려하십시오.

* **클래스에 변경 가능한 상태가 있습니다**. 클래스 자체가 변경 가능한 상태를 표시하는 경우 이 상태를 우회하도록 코드를 다시 작성하십시오. 성능상의 이유로 변경 가능한 상태가 필요한 경우 `ResetAfterRequestInterface`을(를) 구현하고 `_resetState()`을(를) 사용하여 개체를 초기 생성 상태로 다시 설정합니다.

* **초기화 메시지** 전에 형식화된 속성 $x에 액세스하면 안 됩니다. 이 유형의 메시지가 실패하면 지정된 속성이 생성자에 의해 초기화되지 않았음을 나타냅니다. 이는 객체가 처음 구성된 후에는 사용할 수 없기 때문에 발생하는 시간적 결합의 형태이다. 속성에서 데이터를 검색하는 Collector가 PHP 반사 기능을 사용하기 때문에 속성이 비공개인 경우에도 이러한 결합이 발생합니다. 이 경우, 시간적 결합을 피하고 변경 가능한 상태를 피하도록 클래스를 리팩터링해 보십시오. 리팩터링으로 오류가 해결되지 않으면 속성 형식을 null 허용 형식으로 변경하여 null로 초기화할 수 있습니다.  속성이 배열인 경우 속성을 빈 배열로 초기화해 보십시오.

`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`을(를) 실행하여 `GraphQlStateTest` 실행

### ResetAfterRequestTest

`ResetAfterRequestTest`은(는) `ResetAfterRequestInterface`을(를) 구현하는 모든 클래스를 찾고 `_resetState()` 메서드가 `ObjectManager`에 의해 만들어진 후 유지된 동일한 상태로 개체의 상태를 반환하는지 확인합니다.  이 테스트에서는 `ObjectManager`을(를) 사용하여 서비스 개체를 만든 다음 해당 개체를 복제하고 `_resetState()`을(를) 호출한 다음 두 개체를 비교합니다. 테스트에서는 개체 인스턴스화와 `_resetState()` 사이에 메서드를 호출하지 않으므로 변경 가능한 상태 재설정을 확인하지 않습니다. `_resetState()`의 버그 또는 오타가 원래 상태와 다른 상태로 설정되어 있는 문제를 찾습니다.

#### ResetAfterRequestTest 실패 및 잠재적인 재구성

* **클래스에 일관되지 않은 속성 값이 있습니다**. 이 테스트가 실패하면 `_resetState()` 메서드가 호출된 후 생성 후 개체에 있는 속성 값이 다른 결과를 사용하여 클래스가 변경되었는지 확인합니다. 작업 중인 클래스에 `_resetState()` 메서드 자체가 포함되어 있지 않으면 클래스 계층 구조에 이 메서드를 구현하는 슈퍼클래스가 있는지 확인합니다.

* **초기화 메시지** 전에 형식화된 속성 $x에 액세스하면 안 됩니다. 이 문제는 `GraphQlStateTest`에서도 발생합니다.

  `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`을(를) 실행하여 `ResetAfterRequestTest`을(를) 실행합니다.

### 기능 테스트

GraphQL Application Server를 배포하는 동안 확장 개발자는 WebAPI 기능 테스트와 GraphQL에 대한 사용자 지정 자동화된 기능 테스트 또는 수동 기능 테스트를 실행해야 합니다. 이러한 기능 테스트는 개발자가 잠재적인 오류나 호환성 문제를 식별하는 데 도움이 됩니다.

#### 상태 모니터 모드

기능 테스트(또는 수동 테스트)를 실행하는 동안 상태가 의도하지 않게 재사용되는 클래스를 찾는 데 도움이 되도록 `--state-monitor mode`을(를) 활성화한 상태로 GraphQL Application Server를 실행할 수 있습니다. `--state-monitor` 매개 변수를 추가하지 않고 응용 프로그램 서버를 정상적으로 시작합니다.

```
bin/magento server:run --state-monitor
```

각 요청이 처리되면 새 파일이 `tmp` 디렉터리에 추가됩니다(예: `var/tmp/StateMonitor-thread-output-50-6nmxiK`). 테스트를 완료하면 이러한 파일을 `bin/magento server:state-monitor:aggregate-output` 명령과 병합하여 `XML`과(와) `JSON`에 하나씩 두 개의 병합된 파일을 만들 수 있습니다.

예:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

`GraphQlStateTest`과(와) 같이 수정된 서비스 개체의 속성을 표시하는 XML 또는 JSON을 보는 데 사용하는 모든 도구를 사용하여 이러한 파일을 검사할 수 있습니다. `--state-monitor` 모드에서는 GraphQlStateTest와 동일한 건너뛰기 목록 및 필터 목록을 사용합니다.

>[!NOTE]
>
>프로덕션에서 `--state-monitor` 모드를 사용하지 마십시오. 개발 및 테스트용으로만 설계되었습니다. 많은 출력 파일을 생성하고 평소보다 느리게 실행됩니다.

>[!NOTE]
>
>PHP 가비지 수집기의 버그로 인해 `--state-monitor`이(가) PHP 버전 `8.3.0` - `8.3.4`과(와) 호환되지 않습니다. PHP 8.3을 사용하는 경우 이 기능을 사용하려면 `8.3.5` 이상으로 업그레이드해야 합니다.
