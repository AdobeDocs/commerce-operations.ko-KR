---
title: 고급 온-프레미스 설치
description: 소유하는 인프라에 대한 Adobe Commerce 또는 Magento Open Source에 대한 고급 설치 시나리오에 대해 알아봅니다.
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '2327'
ht-degree: 0%

---


# 고급 온-프레미스 설치

>[!TIP]
>
>잃어버렸나요? 도움이 필요하십니까? 사용해 보세요 [빠른 설치 시작](composer.md) 또는 [참가자 설치](https://developer.adobe.com/commerce/contributor/guides/install/) 안내서.

>[!NOTE]
>
>SELinux를 활성화하도록 선택한 경우 [SELinux 및 iptables](prerequisites/security.md).

## 명령줄 인터페이스(CLI)

Adobe Commerce 및 Magento Open Source에는 설치 및 구성 작업을 위한 단일 명령줄 인터페이스가 있습니다. `<magento_root>/bin/magento`. 인터페이스는 다음을 포함하여 여러 작업을 수행합니다.

* 설치(데이터베이스 스키마 만들기 또는 업데이트, 배포 구성 만들기 등) 관련 작업
* 캐시를 지우고 있습니다.
* 재색인을 포함한 인덱스 관리.
* 번역 사전 및 번역 패키지를 만들고 있습니다.
* 플러그 인에 대한 공장 및 인터셉터와 같은 존재하지 않는 클래스를 생성하여 객체 관리자에 대한 종속성 주입 구성을 생성합니다.
* 정적 보기 파일을 배포하는 중입니다.
* 최소값에서 CSS 만들기

기타 이점:

* 단일 명령(`<magento_root>/bin/magento list`) 사용 가능한 모든 설치 및 구성 명령을 나열합니다.
* Symfony를 기반으로 일관된 사용자 인터페이스
* CLI는 확장 가능하므로 타사 개발자가 CLI를 &quot;플러그인&quot;할 수 있습니다. 이로 인해 사용자의 학습 곡선을 없앨 수 있습니다.
* 비활성화된 모듈에 대한 명령이 표시되지 않습니다.

이 항목에서는 CLI를 사용하여 Adobe Commerce 또는 Magento Open Source 소프트웨어를 설치하는 방법을 설명합니다. 구성에 대한 자세한 내용은 [구성 안내서](../configuration/overview.md).

필요한 경우 설치 관리자를 여러 번 실행할 수 있으므로 다음을 수행할 수 있습니다.

* 다른 값 제공

   예를 들어, SSL(Secure Sockets Layer)을 위해 웹 서버를 구성한 후 설치 관리자를 실행하여 SSL 옵션을 설정할 수 있습니다.

* 이전 설치의 실수 수정
* 다른 데이터베이스 인스턴스에 Adobe Commerce 또는 Magento Open Source 설치

## 설치를 시작하기 전에

시작하기 전에 다음 단계를 완료하십시오.

* 시스템이 [시스템 요구 사항](system-requirements.md).

* 모두 완료 [전제 조건](prerequisites/overview.md) 작업.

* 첫 번째 설치 단계를 완료합니다. 자세한 내용은 [설치 또는 업그레이드 경로](overview.md).

* 응용 프로그램 서버에 로그인한 후 [파일 시스템 소유자에게 전환](prerequisites/file-system/overview.md).

* 를 검토합니다. [설치 빠른 시작](composer.md) 개요.

>[!NOTE]
>
>에서 Adobe Commerce 또는 Magento Open Source을 설치해야 합니다. `bin` 하위 디렉토리.

다음과 같은 설치 작업을 완료하기 위해 다양한 옵션을 사용하여 설치 관리자를 여러 번 실행할 수 있습니다.

* 설치 단계 — 예를 들어, SSL(Secure Sockets Layer)을 위해 웹 서버를 구성한 후 설치 관리자를 다시 실행하여 SSL 옵션을 설정할 수 있습니다.

* 이전 설치의 오류를 수정합니다.

* 다른 데이터베이스 인스턴스에 Adobe Commerce 또는 Magento Open Source을 설치합니다.

>[!NOTE]
>
>기본적으로 동일한 데이터베이스 인스턴스에 소프트웨어를 설치하면 설치 프로그램이 데이터베이스를 덮어쓰지 않습니다. 선택 사항을 사용할 수 있습니다 `cleanup-database` 매개 변수를 사용하여 이 동작을 변경할 수 있습니다.

참조 - [업데이트, 다시 설치, 제거](tutorials/uninstall.md).

### 보안 설치

{{$include /help/_includes/secure-install.md}}

## 설치 프로그램 도움말 명령

다음 명령을 실행하여 일부 필수 인수에 대한 값을 찾을 수 있습니다.

| 설치 관리자 인수 | 명령 |
| ------------------ | ------------------------------- |
| 언어 | bin/magento 정보:language:list |
| 통화 | bin/magento 정보:currency:list |
| 시간대 | bin/magento 정보:timezone:list |

>[!NOTE]
>
>이러한 명령을 실행할 때 오류가 표시되는 경우 [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 명령줄에서 설치

install 명령은 다음 형식을 사용합니다.

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

다음 표에서는 설치 옵션 이름 및 값에 대해 설명합니다. 설치 명령 예는 [샘플 localhost 설치](#sample-localhost-installations).

>[!NOTE]
>
>공백이나 특수 문자가 포함된 모든 옵션은 작은 따옴표나 큰 따옴표로 묶어야 합니다.

**관리자 자격 증명:**

다음 옵션은 관리자 사용자의 사용자 정보 및 자격 증명을 지정합니다.

설치 중 또는 설치 후에 관리자 사용자를 만들 수 있습니다. 설치 중에 사용자를 만드는 경우 모든 관리자 자격 증명 변수가 필요합니다. 자세한 내용은 [샘플 localhost 설치](#sample-localhost-installations).

다음 표에는 사용 가능한 설치 매개 변수가 많이 제공되지만, 일부 설치 매개 변수는 제공하지 않습니다. 전체 목록에 대해서는 [명령줄 도구 참조](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--admin-firstname` | 관리자 사용자의 이름입니다. | 예 |
| `--admin-lastname` | 관리자 사용자의 성입니다. | 예 |
| `--admin-email` | 관리자 사용자의 전자 메일 주소입니다. | 예 |
| `--admin-user` | 관리자 사용자 이름. | 예 |
| `--admin-password` | 관리자 사용자 암호입니다. 암호는 길이가 7자 이상이어야 하며 하나 이상의 영문자와 하나 이상의 숫자 문자를 포함해야 합니다. 더 길고 복잡한 암호를 사용하는 것이 좋습니다. 전체 암호 문자열을 작은 따옴표로 묶습니다. For example, `--admin-password='A0b9%t3g'` | 예 |

**사이트 및 데이터베이스 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--base-url` | 다음 형식으로 관리자 및 저장소에 액세스하는 데 사용할 기본 URL입니다.<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**참고:** 구성표(http:// 또는 https://)과 후행 슬래시가 모두 필요합니다.<br><br>`<your install dir>` 는 Adobe Commerce 또는 Magento Open Source 소프트웨어를 설치할 docroot 상대 경로입니다. 웹 서버와 가상 호스트를 설정하는 방법에 따라 경로가 magento2일 수도 있고 비어 있을 수도 있습니다.<br><br>로컬 호스트에서 Adobe Commerce 또는 Magento Open Source에 액세스하려면 다음 중 하나를 사용할 수 있습니다 `http://127.0.0.1/<your install dir>/` 또는 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 가상 호스트 설정에 의해 정의되거나 Docker와 같은 가상화 환경에 의해 정의된 기본 URL을 나타냅니다. 예를 들어 호스트 이름으로 가상 호스트를 설정하는 경우 `magento.example.com`를 사용하여 소프트웨어를 설치할 수 있습니다. `--base-url={{base_url}}` 와 같은 URL을 사용하여 관리자에 액세스합니다 `http://magento.example.com/admin`. | 예 |
| `--backend-frontname` | 관리자 액세스를 위한 URI(Uniform Resource Identifier)입니다. 이 매개 변수를 생략하여 애플리케이션이 admin_jkgdfq 패턴을 사용하여 임의 URI를 생성하도록 할 수 있습니다</code>.<br><br>보안을 위해 임의 URI를 사용하는 것이 좋습니다. 무작위 URI는 해커나 악성 소프트웨어가 악용하기 더 어렵다.<br><br>설치 끝에 URI가 표시됩니다. 을 사용하여 언제든지 나중에 표시할 수 있습니다 `bin/magento info:adminuri` 명령.<br><br>값을 입력하도록 선택하는 경우 admin, backend와 같은 공통 단어를 사용하지 않는 것이 좋습니다. 관리자 URI에는 영숫자 값과 밑줄 문자(`_`)만 사용할 수 있습니다. | 아니요 |
| `--db-host` | 다음 중 하나를 사용합니다.<br><br>- 데이터베이스 서버의 정규화된 호스트 이름 또는 IP 주소입니다.<br><br>- `localhost` (기본값) 또는 `127.0.0.1` 데이터베이스 서버가 웹 서버와 동일한 호스트에 있는 경우 localhost는 MySQL 클라이언트 라이브러리가 UNIX 소켓을 사용하여 데이터베이스에 연결함을 의미합니다. `127.0.0.1` 클라이언트 라이브러리가 TCP 프로토콜을 사용하도록 합니다. 소켓에 대한 자세한 내용은 [PHP PDO_MYSQL 설명서](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**참고:** 선택적으로 www.example.com:9000 과 같은 호스트 이름에서 데이터베이스 서버 포트를 지정할 수 있습니다 | 예 |
| `--db-name` | 데이터베이스 테이블을 설치할 데이터베이스 인스턴스의 이름입니다.<br><br>기본값은 입니다. `magento2`. | 예 |
| `--db-user` | 데이터베이스 인스턴스 소유자의 사용자 이름입니다.<br><br>기본값은 입니다. `root`. | 예 |
| `--db-password` | 데이터베이스 인스턴스 소유자의 암호입니다. | 예 |
| `--db-prefix` | Adobe Commerce 또는 Magento Open Source 테이블이 이미 있는 데이터베이스 인스턴스에 데이터베이스 테이블을 설치하는 경우에만 사용합니다.<br><br>이 경우 설치 테이블을 식별하려면 접두어를 사용합니다. 일부 고객은 동일한 데이터베이스에 모든 테이블이 있는 서버에서 실행되는 둘 이상의 Adobe Commerce 또는 Magento Open Source 인스턴스를 가지고 있습니다.<br><br>접두사는 최대 5자 길이일 수 있습니다. 문자로 시작해야 하며 문자, 숫자 및 밑줄 문자만 포함할 수 있습니다.<br><br>이 옵션을 사용하면 이러한 고객이 둘 이상의 Adobe Commerce 또는 Magento Open Source 설치와 데이터베이스 서버를 공유할 수 있습니다. | 아니요 |
| `--db-ssl-key` | 클라이언트 키의 경로입니다. | 아니요 |
| `--db-ssl-cert` | 클라이언트 인증서에 대한 경로입니다. | 아니요 |
| `--db-ssl-ca` | 서버 인증서 경로입니다. | 아니요 |
| `--language` | 관리자 및 스토어에 사용할 언어 코드입니다. (아직 완료하지 않았다면 다음을 입력하여 언어 코드 목록을 볼 수 있습니다.) `bin/magento info:language:list` bin 디렉터리에서) | 아니요 |
| `--currency` | 스토어에 사용할 기본 통화입니다. (아직 수행하지 않았다면 다음을 입력하여 통화 목록을 볼 수 있습니다.) `bin/magento info:currency:list` bin 디렉터리에서) | 아니요 |
| `--timezone` | 관리자 및 저장소 창에서 사용할 기본 시간대입니다. (아직 수행하지 않았다면 을 입력하여 시간대 목록을 볼 수 있습니다. `bin/magento info:timezone:list` 에서 `bin/` 디렉토리). | 아니요 |
| `--use-rewrites` | `1` 즉, 상점 및 관리자에서 생성된 링크에 웹 서버 rewrites를 사용합니다.<br><br>`0` 웹 서버 rewrites 사용을 비활성화합니다. 기본값입니다. | 아니요 |
| `--use-secure` | `1` 저장소 URL에서 SSL(Secure Sockets Layer)을 사용할 수 있습니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` SSL 사용을 비활성화합니다. 이 경우 다른 모든 보안 URL 옵션도 0으로 간주됩니다. 기본값입니다. | 아니요 |
| `--base-url-secure` | 관리자 및 저장소에 액세스하는 데 사용할 보안 기본 URL로 다음 형식으로 저장됩니다. `http[s]://<host or ip>/<your install dir>/` | 아니요 |
| `--use-secure-admin` | `1` 는 SSL을 사용하여 관리자에 액세스함을 의미합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0` 은 사용자가 관리자에 SSL을 사용하지 않음을 의미합니다. 기본값입니다. | 아니요 |
| `--admin-use-security-key` | 1을 사용하면 애플리케이션이 임의로 생성된 키 값을 사용하여 관리자 및 양식의 페이지에 액세스합니다. 이러한 주요 값은 사이트 간 스크립트 위조 공격을 방지하는 데 도움이 됩니다. 기본값입니다.<br><br>`0` 키 사용을 비활성화합니다. | 아니요 |
| `--session-save` | 다음 중 하나를 사용합니다.<br><br>- `db` 세션 데이터를 데이터베이스에 저장 클러스터형 데이터베이스가 있는 경우 데이터베이스 저장소를 선택합니다. 그렇지 않으면 파일 기반 스토리지보다 많은 이점이 없을 수 있습니다.<br><br>- `files` 세션 데이터를 파일 시스템에 저장 파일 시스템 액세스 속도가 느리거나, 클러스터링된 데이터베이스가 있거나, 세션 데이터를 Redis에 저장하지 않는 한 파일 기반 세션 저장소가 적합합니다.<br><br>- `redis` 세션 데이터를 Redis에 저장 기본 또는 페이지 캐싱에 Redis를 사용하는 경우 Redis가 이미 설치되어 있어야 합니다. Redis에 대한 지원 구성에 대한 자세한 내용은 세션 저장소에 Redis 사용 을 참조하십시오. | 아니요 |
| `--key` | 키가 있는 경우 키를 지정하여 데이터베이스의 중요 데이터를 암호화합니다. 없는 경우 애플리케이션에서 자동으로 생성합니다. | 예 |
| `--cleanup-database` | Adobe Commerce 또는 Magento Open Source을 설치하기 전에 데이터베이스 테이블을 삭제하려면 값 없이 이 매개 변수를 지정하십시오. 그렇지 않으면 데이터베이스가 그대로 유지됩니다. | 아니요 |
| `--db-init-statements` | 고급 MySQL 구성 매개 변수입니다. MySQL 데이터베이스에 연결할 때 데이터베이스 초기화 문을 사용하여 실행합니다. 값을 설정하기 전에 이 참조와 유사한 참조를 참조하십시오.<br><br>기본값은 입니다. `SET NAMES utf8;`. | 아니요 |
| `--sales-order-increment-prefix` | 판매 주문의 접두사로 사용할 문자열 값을 지정합니다. 일반적으로 결제 프로세서의 고유한 주문 번호를 보장하는 데 사용됩니다. | 아니요 |

**검색 엔진 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--search-engine` | 검색 엔진으로 사용할 Elasticsearch 또는 OpenSearch 버전입니다. 가능한 값은 다음과 같습니다 `elasticsearch7`, `elasticsearch6`, 및 `elasticsearch5`. 기본값은 입니다. `elasticsearch7`. OpenSearch를 사용하려면 `elasticsearch7`. Elasticsearch 5은 더 이상 사용되지 않으며 권장되지 않습니다. | 아니요 |
| `--elasticsearch-host` | 검색 엔진이 실행 중인 호스트 이름 또는 IP 주소입니다. 기본값은 입니다. `localhost`. | 아니요 |
| `--elasticsearch-port` | 들어오는 HTTP 요청에 대한 포트입니다. 기본값은 입니다. `9200`. | 아니요 |
| `--elasticsearch-index-prefix` | 검색 엔진 인덱스를 식별하는 접두사입니다. 기본값은 입니다. `magento2`. | 아니요 |
| `--elasticsearch-timeout` | 시스템이 시간 초과되기 전 시간(초)입니다. 기본값은 입니다. `15`. | 아니요 |
| `--elasticsearch-enable-auth` | 검색 엔진 서버에서 인증을 사용하도록 설정합니다. 기본값은 입니다. `false`. | 아니요 |
| `--elasticsearch-username` | 검색 엔진을 인증할 사용자 ID입니다 | 아니요, 인증을 사용할 수 없는 경우 |
| `--elasticsearch-password` | 검색 엔진 인증을 위한 암호 | 아니요, 인증을 사용할 수 없는 경우 |

**[!DNL RabbitMQ]구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--amqp-host` | 를 사용하지 마십시오 `--amqp` 설치 설정을 이미 설정하지 않은 경우 옵션 [!DNL RabbitMQ]. 자세한 내용은 [!DNL RabbitMQ] 설치 및 구성에 대한 자세한 정보 [!DNL RabbitMQ].<br><br>호스트 이름 [!DNL RabbitMQ] 가 설치되어 있습니다. | 아니요 |
| `--amqp-port` | 연결하는 데 사용할 포트 [!DNL RabbitMQ]. 기본값은 5672입니다. | 아니요 |
| `--amqp-user` | 연결하는 사용자 이름 [!DNL RabbitMQ]. 기본 사용자를 사용하지 마십시오 `guest`. | 아니요 |
| `--amqp-password` | 연결하는 데 사용할 암호 [!DNL RabbitMQ]. 기본 암호를 사용하지 마십시오 `guest`. | 아니요 |
| `--amqp-virtualhost` | 연결할 가상 호스트 [!DNL RabbitMQ]. 기본값은 입니다. `/`. | 아니요 |
| `--amqp-ssl` | 연결 여부를 나타냅니다. [!DNL RabbitMQ]. 기본값은 입니다. `false`. 자세한 내용은 [!DNL RabbitMQ] 용 SSL 설정에 대한 정보 [!DNL RabbitMQ]. | 아니요 |
| `--consumers-wait-for-messages` | 소비자가 큐에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오 | 아니요 |

**구성 잠금 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--lock-provider` | 공급자 이름을 잠급니다.<br><br>사용 가능한 잠금 공급자: `db`, `zookeeper`, `file`.<br><br>기본 잠금 공급자: `db` | 아니요 |
| `--lock-db-prefix` | 사용 시 잠금 충돌을 방지하기 위한 특정 db 접두사 `db` 잠금 공급자.<br><br>기본값: `NULL` | 아니요 |
| `--lock-zookeeper-host` | 사용 시 Zookeeper 클러스터에 연결할 호스트 및 포트 `zookeeper` 잠금 공급자.<br><br>For example: `127.0.0.1:2181` | 예, `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper가 잠금을 저장하는 경로입니다.<br><br>기본 경로는 다음과 같습니다. `/magento/locks` | 아니요 |
| `--lock-file-path` | 파일 잠금이 저장되는 경로입니다. | 예, `--lock-provider=file` |

**소비자 구성 옵션:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Adobe Commerce 또는 Magento Open Source을 설치한 후 모듈을 활성화하거나 비활성화하려면 다음을 참조하십시오 [모듈 활성화 및 비활성화](tutorials/manage-modules.md).

**중요 데이터:**

{{$include /help/_includes/sensitive-data.md}}

### 샘플 localhost 설치

다음 예에서는 다양한 옵션을 사용하여 로컬에서 Adobe Commerce을 설치하는 명령을 보여줍니다.

#### 예제 1 - 관리자 사용자 계정이 있는 기본 설치

다음 예제에서는 다음 옵션을 사용하여 Adobe Commerce 또는 Magento Open Source을 설치합니다.

* 애플리케이션이 `magento2` 웹 서버 docroot에 대한 디렉토리 `localhost` 및 관리자 경로 `admin`; 따라서

   저장소 URL이 `http://127.0.0.1`

* 데이터베이스 서버가 웹 서버와 동일한 호스트에 있습니다.

   데이터베이스 이름은 `magento`, 사용자 이름과 암호는 `magento`

* 서버 다시 쓰기 사용

* 관리자는 다음 속성을 가집니다.

   * 이름과 성은 `Magento User`
   * 사용자 이름: `admin` 그리고 암호는 `admin123`
   * 전자 메일 주소: `user@example.com`

* 기본 언어는 다음과 같습니다 `en_US` (미국 영어)
* 기본 통화는 미국 달러입니다
* 기본 시간대는 미국 중부(미국/시카고)입니다.
* OpenSearch 1.2가 `es-host.example.com` 포트 9200에서 연결

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

성공적인 설치를 나타내는 메시지가 다음 표시와 유사합니다.

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 예제 2 — 관리자 사용자 계정이 없는 기본 설치

다음 예와 같이 관리자 사용자를 만들지 않고 Adobe Commerce 또는 Magento Open Source을 설치할 수 있습니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

설치가 성공적으로 수행되면 다음과 같은 메시지가 표시됩니다.

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

설치 후 을 사용하여 관리자 사용자를 만들 수 있습니다 `admin:user:create` 명령:
[관리자 만들기 또는 편집](tutorials/admin.md#create-or-edit-an-administrator)

#### 예제 3 - 추가 옵션을 사용하여 설치

다음 예제에서는 다음 옵션을 사용하여 Adobe Commerce 또는 Magento Open Source을 설치합니다.

* 애플리케이션이 `magento2` 웹 서버 docroot에 대한 디렉토리 `localhost` 및 관리자 경로 `admin`; 따라서

   저장소 URL이 `http://127.0.0.1`

* 데이터베이스 서버가 웹 서버와 동일한 호스트에 있습니다.

   데이터베이스 이름은 `magento`, 사용자 이름과 암호는 `magento`

* 관리자는 다음 속성을 가집니다.

   * 이름과 성은 `Magento User`
   * 사용자 이름: `admin` 그리고 암호는 `admin123`
   * 전자 메일 주소: `user@example.com`

* 기본 언어는 다음과 같습니다 `en_US` (미국 영어)
* 기본 통화는 미국 달러입니다
* 기본 시간대는 미국 중부(미국/시카고)입니다.
* 테이블 및 스키마를 설치하기 전에 설치 프로그램이 먼저 데이터베이스를 정리합니다
* 판매 주문 증가 접두사를 사용할 수 있습니다 `ORD$` 특수 문자를 포함하므로 [`$`]를 채울 때는 값을 큰따옴표로 묶어야 합니다.
* 세션 데이터는 데이터베이스에 저장됩니다
* 서버 다시 쓰기 사용
* Elasticsearch 7이 `es-host.example.com` 포트 9200에서 연결

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>한 줄에 명령을 입력하거나 이전 예와 같이 `\` 각 줄의 끝에 있는 문자입니다.

설치가 성공적으로 수행되면 다음과 같은 메시지가 표시됩니다.

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
