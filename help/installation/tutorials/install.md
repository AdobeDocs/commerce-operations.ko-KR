---
title: Adobe Commerce 설치
description: 소유한 인프라에 Adobe Commerce을 설치하려면 다음 단계를 따르십시오.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 47525e8d8379061b254bfa90ab46e27a1ee2f524
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# Adobe Commerce 설치

시작하기 전에 다음 단계를 완료하십시오.

* 시스템이 [시스템 요구 사항](../system-requirements.md)에서 설명한 요구 사항을 충족하는지 확인하십시오.

* [필수 구성 요소](../prerequisites/overview.md) 작업을 모두 완료하십시오.

* 첫 번째 설치 단계를 완료합니다. [설치 또는 업그레이드 경로](../overview.md)를 참조하세요.

* 응용 프로그램 서버에 로그인한 후 [파일 시스템 소유자로 전환](../prerequisites/file-system/overview.md)합니다.

* [명령줄 설치 시작](../composer.md) 개요를 검토하십시오.

>[!NOTE]
>
>`bin` 하위 디렉터리에서 응용 프로그램을 설치해야 합니다.

설치 관리자를 다양한 옵션으로 여러 번 실행하여 다음과 같은 설치 작업을 완료할 수 있습니다.

* 단계적으로 설치 - 예를 들어 웹 서버에서 SSL(Secure Sockets Layer)을 구성한 후 설치 관리자를 다시 실행하여 SSL 옵션을 설정할 수 있습니다.

* 이전 설치에서 발생한 오류를 수정합니다.

* 다른 데이터베이스 인스턴스에 응용 프로그램을 설치합니다.

>[!NOTE]
>
>동일한 데이터베이스 인스턴스에 Commerce 소프트웨어를 설치하는 경우 기본적으로 설치 관리자는 데이터베이스를 덮어쓰지 않습니다. 선택적 `cleanup-database` 매개 변수를 사용하여 이 동작을 변경할 수 있습니다.

[업데이트, 다시 설치, 제거](uninstall.md)도 참조하세요.

## 보안 설치

{{$include /help/_includes/secure-install.md}}

## 설치 관리자 도움말 명령

다음 명령을 실행하여 일부 필수 인수의 값을 찾을 수 있습니다.

| 설치 관리자 인수 | 명령 |
| ------------------ | ------------------------------- |
| 언어 | `magento info:language:list` |
| 통화 | `magento info:currency:list` |
| 시간대 | `magento info:timezone:list` |

>[!NOTE]
>
>이 명령을 실행할 때 오류가 표시되면 [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)에 설명된 대로 설치 종속성을 업데이트했는지 확인하십시오.

## 명령줄에서 설치

install 명령은 다음 형식을 사용합니다.

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

다음 표에서는 설치 명령 등의 설치 옵션 이름 및 값에 대해 설명합니다. [샘플 localhost 설치](#sample-localhost-installations)를 참조하십시오.

>[!NOTE]
>
>공백이나 특수 문자가 포함된 옵션은 작은따옴표나 큰따옴표로 묶어야 합니다.

**관리자 자격 증명:**

다음 옵션은 관리자에 대한 사용자 정보 및 자격 증명을 지정합니다.

Adobe Commerce 버전 2.2.8 이상에서는 설치 중 또는 설치 후에 관리자 사용자를 만들 수 있습니다. 설치 중에 사용자를 만드는 경우 모든 관리자 자격 증명 변수가 필요합니다. [샘플 localhost 설치](#sample-localhost-installations)를 참조하십시오.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--admin-firstname` | 관리자 사용자의 이름입니다. | 예 |
| `--admin-lastname` | 관리자 사용자의 성. | 예 |
| `--admin-email` | 관리자 사용자의 이메일 주소입니다. | 예 |
| `--admin-user` | 관리자 사용자 이름. | 예 |
| `--admin-password` | 관리자 사용자 암호입니다. 암호는 길이가 7자 이상이어야 하며 최소 하나의 영문자와 최소 하나의 숫자를 포함해야 합니다. 보다 길고 복잡한 암호를 사용하는 것이 좋습니다. 전체 암호 문자열을 작은 따옴표로 묶습니다. For example, `--admin-password='A0b9%t3g'` | 예 |

**사이트 및 데이터베이스 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--base-url` | <br><br>`http[s]://<host or ip>/<your install dir>/` 형식 중 하나로 관리자 및 상점 앞에 액세스하는 데 사용할 기본 URL입니다.<br><br>**참고:** 구성표(http:// 또는 https://)와 뒤쪽 슬래시가 모두 필요합니다.<br><br>`<your install dir>`은(는) 응용 프로그램을 설치할 docroot 상대 경로입니다. 웹 서버와 가상 호스트를 설정하는 방법에 따라 경로가 magento2이거나 비어 있을 수 있습니다.<br><br>localhost에서 응용 프로그램에 액세스하려면 `http://127.0.0.1/<your install dir>/` 또는 `http://127.0.0.1/<your install dir>/`을(를) 사용합니다.<br><br>- `{{base_url}}`: 가상 호스트 설정 또는 Docker와 같은 가상화 환경에서 정의한 기본 URL을 나타냅니다. 예를 들어 호스트 이름 commerce.example.com을 사용하여 가상 호스트를 설정하는 경우 `--base-url={{base_url}}`을(를) 사용하여 응용 프로그램을 설치하고 `http://commerce.example.com/admin`과(와) 같은 URL로 관리자에 액세스할 수 있습니다. | 예 |
| `--backend-frontname` | 관리자에 액세스할 수 있는 URI(Uniform Resource Identifier)입니다. 이 매개 변수를 생략하면 응용 프로그램에서 다음 패턴으로 임의의 URI를 생성할 수 있습니다. <code>admin_jkgdfq</code>.<br><br>보안을 위해 임의의 URI를 사용하는 것이 좋습니다. 무작위 URI는 해커나 악성 소프트웨어가 악용하기 더 어렵다.<br><br>설치가 끝날 때 URI가 표시됩니다. 나중에 언제든지 `magento info:adminuri` 명령을 사용하여 표시할 수 있습니다.<br><br>값을 입력하기로 선택한 경우 admin, backend와 같은 일반적인 단어를 사용하지 않는 것이 좋습니다. 관리자 URI에는 영숫자 값과 밑줄 문자(`_`)만 포함될 수 있습니다. | 아니요 |
| `--db-host` | <br><br>- 데이터베이스 서버의 정규화된 호스트 이름 또는 IP 주소를 사용합니다.<br><br>- `localhost`(기본값) 또는 `127.0.0.1`(데이터베이스 서버가 웹 서버와 동일한 호스트에 있는 경우).localhost는 MySQL 클라이언트 라이브러리가 UNIX 소켓을 사용하여 데이터베이스에 연결함을 의미합니다. `127.0.0.1`을(를) 사용하면 클라이언트 라이브러리에서 TCP 프로토콜을 사용합니다. 소켓에 대한 자세한 내용은 [PHP PDO_MYSQL 설명서](https://www.php.net/manual/en/ref.pdo-mysql.php)를 참조하십시오.<br><br>**참고:** www.example.com과 같은 호스트 이름에 데이터베이스 서버 포트를 선택적으로 지정할 수 있습니다.:9000 | 예 |
| `--db-name` | 데이터베이스 테이블을 설치할 데이터베이스 인스턴스의 이름입니다.<br><br>기본값은 `magento2`입니다. | 예 |
| `--db-user` | 데이터베이스 인스턴스 소유자의 사용자 이름.<br><br>기본값은 `root`입니다. | 예 |
| `--db-password` | 데이터베이스 인스턴스 소유자의 암호입니다. | 예 |
| `--db-prefix` | Adobe Commerce 테이블이 이미 있는 데이터베이스 인스턴스에 데이터베이스 테이블을 설치하는 경우에만 사용합니다.<br><br>이 경우 접두사를 사용하여 이 설치에 사용할 테이블을 식별하십시오. 일부 고객은 동일한 데이터베이스에 있는 모든 테이블이 있는 서버에서 두 개 이상의 Adobe Commerce 인스턴스를 실행하고 있습니다.<br><br>접두사는 최대 5자까지 사용할 수 있습니다. 문자로 시작해야 하며 문자, 숫자 및 밑줄 문자만 포함할 수 있습니다.<br><br>이 옵션을 사용하면 두 개 이상의 설치에서 데이터베이스 서버를 공유할 수 있습니다. | 아니요 |
| `--db-ssl-key` | 클라이언트 키 경로. | 아니요 |
| `--db-ssl-cert` | 클라이언트 인증서 경로. | 아니요 |
| `--db-ssl-ca` | 서버 인증서 경로. | 아니요 |
| `--language` | 관리자 및 상점 첫 화면에서 사용할 언어 코드. (아직 확인하지 않은 경우 bin 디렉터리에서 `magento info:language:list`을(를) 입력하여 언어 코드 목록을 볼 수 있습니다.) | 아니요 |
| `--currency` | 상점 첫 화면에서 사용할 기본 통화. (아직 완료하지 않은 경우 bin 디렉터리에서 `magento info:currency:list`을(를) 입력하여 통화 목록을 볼 수 있습니다.) | 아니요 |
| `--timezone` | 관리자 및 상점 첫 화면에서 사용할 기본 시간대. (아직 확인하지 않은 경우 bin 디렉터리에서 `magento info:timezone:list`을(를) 입력하여 시간대 목록을 볼 수 있습니다.) | 아니요 |
| `--use-rewrites` | `1`은(는) storefront 및 Admin에서 생성된 링크에 대해 웹 서버 다시 쓰기를 사용함을 의미합니다.<br><br>`0`은(는) 웹 서버 다시 쓰기를 사용하지 않도록 설정합니다. 이것이 기본값입니다. | 아니요 |
| `--use-secure` | `1`을(를) 사용하면 상점 URL에서 SSL(Secure Sockets Layer)을 사용할 수 있습니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0`은(는) SSL 사용을 비활성화합니다. 이 경우 다른 모든 보안 URL 옵션도 0이라고 가정합니다. 이것이 기본값입니다. | 아니요 |
| `--base-url-secure` | 관리자 및 상점 첫 화면에 액세스할 때 사용할 보안 기본 URL은 `http[s]://<host or ip>/<your install dir>/` 형식입니다. | 아니요 |
| `--use-secure-admin` | `1`은(는) SSL을 사용하여 관리자에 액세스함을 의미합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0`은(는) 관리자가 SSL을 사용하지 않음을 의미합니다. 이것이 기본값입니다. | 아니요 |
| `--admin-use-security-key` | 1을 사용하면 애플리케이션이 임의로 생성된 키 값을 사용하여 관리자 및 양식의 페이지에 액세스합니다. 이러한 키 값은 크로스 사이트 스크립트 위조 공격을 방지하는 데 도움이 됩니다. 이것이 기본값입니다.<br><br>`0`이(가) 키 사용을 비활성화합니다. | 아니요 |
| `--session-save` | <br><br>- `db` 중 하나를 사용하여 데이터베이스에 세션 데이터를 저장합니다. 클러스터된 데이터베이스가 있는 경우 데이터베이스 저장소를 선택하십시오. 그렇지 않으면 파일 기반 저장소에 비해 이점이 별로 없을 수 있습니다.<br><br>- `files` 파일 시스템에 세션 데이터를 저장합니다. 파일 시스템 액세스가 느리거나 클러스터된 데이터베이스가 있거나 세션 데이터를 Redis에 저장하려는 경우가 아니면 파일 기반 세션 저장소가 적절합니다.Redis에 세션 데이터를 저장하는 <br><br>- `redis`. 기본 또는 페이지 캐싱에 Redis를 사용하는 경우 Redis가 이미 설치되어 있어야 합니다. Redis에 대한 지원 구성에 대한 자세한 내용은 세션 저장소에 Redis 사용 을 참조하십시오. | 아니요 |
| `--key` | 키가 있는 경우 데이터베이스에서 중요한 데이터를 암호화할 키를 지정합니다. 없는 경우 애플리케이션에서 자동으로 생성합니다. | 예 |
| `--cleanup-database` | 응용 프로그램을 설치하기 전에 데이터베이스 테이블을 삭제하려면 값 없이 이 매개 변수를 지정합니다. 그렇지 않으면 데이터베이스가 그대로 유지됩니다. | 아니요 |
| `--db-init-statements` | 고급 MySQL 구성 매개 변수. MySQL 데이터베이스에 연결할 때 데이터베이스 초기화 문을 사용하여 실행합니다. 값을 설정하기 전에 이 참조와 유사한 참조를 참조하십시오.<br><br>기본값은 `SET NAMES utf8;`입니다. | 아니요 |
| `--sales-order-increment-prefix` | 판매 주문의 접두사로 사용할 문자열 값을 지정합니다. 일반적으로 결제 처리자의 고유한 주문 번호를 보장하는 데 사용됩니다. | 아니요 |

>[!TIP]
>
>설치하는 동안 원격 저장소 서비스를 사용하려면 [구성 가이드](../../configuration/remote-storage/remote-storage.md)에서 _원격 저장소 구성_&#x200B;을 참조하세요.

**검색 엔진 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--search-engine` | 검색 엔진의 버전입니다. 가능한 값은 `elasticsearch7`, `elasticsearch6` 및 `elasticsearch5`입니다. 기본값은 `elasticsearch7`입니다. OpenSearch를 검색 엔진으로 설치한 경우 `elasticsearch7` 값을 지정하십시오. Elasticsearch 5는 더 이상 사용되지 않으며 권장되지 않습니다. | 아니요 |
| `--elasticsearch-host` | 검색 엔진이 실행 중인 호스트 이름 또는 IP 주소입니다. 기본값은 `localhost`입니다. | 아니요 |
| `--elasticsearch-port` | 수신 HTTP 요청의 포트입니다. 기본값은 `9200`입니다. | 아니요 |
| `--elasticsearch-index-prefix` | 검색 색인을 식별하는 접두사입니다. 기본값은 `magento2`입니다. | 아니요 |
| `--elasticsearch-timeout` | 시스템 제한 시간(초)입니다. 기본값은 `15`입니다. | 아니요 |
| `--elasticsearch-enable-auth` | 검색 엔진 서버에서 인증을 활성화합니다. 기본값은 `false`입니다. | 아니요 |
| `--elasticsearch-username` | 인증할 사용자 ID | 인증이 활성화되지 않은 경우 아니요 |
| `--elasticsearch-password` | 인증할 암호 | 인증이 활성화되지 않은 경우 아니요 |

**[!DNL RabbitMQ]구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--amqp-host` | `--amqp`의 설치를 아직 설정하지 않은 한 [!DNL RabbitMQ] 옵션을 사용하지 마십시오. [!DNL RabbitMQ] 설치 및 구성에 대한 자세한 내용은 [!DNL RabbitMQ] 설치 를 참조하십시오.<br><br>호스트 이름([!DNL RabbitMQ]이 설치되어 있음). | 아니요 |
| `--amqp-port` | [!DNL RabbitMQ]에 연결하는 데 사용할 포트입니다. 기본값은 5672입니다. | 아니요 |
| `--amqp-user` | [!DNL RabbitMQ]에 연결하기 위한 사용자 이름입니다. 기본 사용자 `guest`을(를) 사용하지 마십시오. | 아니요 |
| `--amqp-password` | [!DNL RabbitMQ]에 연결하기 위한 암호입니다. 기본 암호 `guest`을(를) 사용하지 마십시오. | 아니요 |
| `--amqp-virtualhost` | [!DNL RabbitMQ]에 연결하기 위한 가상 호스트입니다. 기본값은 `/`입니다. | 아니요 |
| `--amqp-ssl` | [!DNL RabbitMQ]에 연결할지 여부를 나타냅니다. 기본값은 `false`입니다. [!DNL RabbitMQ]의 SSL 설정에 대한 자세한 내용은 [!DNL RabbitMQ]을(를) 참조하십시오. | 아니요 |
| `--consumers-wait-for-messages` | 소비자는 대기열에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오 | 아니요 |

**ActiveMQ Artemis 구성 옵션:**

>[!NOTE]
>
>ActiveMQ Artemis는 Adobe Commerce 2.4.6 이상 버전에서 도입되었습니다.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--stomp-host` | ActiveMQ Artemis의 설치를 아직 설정하지 않은 경우 `--stomp` 옵션을 사용하지 마십시오. ActiveMQ Artemis 설치 및 구성에 대한 자세한 내용은 ActiveMQ Artemis 설치 를 참조하십시오.<br><br>ActiveMQ Artemis가 설치된 호스트 이름입니다. | 아니요 |
| `--stomp-port` | ActiveMQ Artemis에 연결하는 데 사용할 포트입니다. 기본값은 61613입니다. | 아니요 |
| `--stomp-user` | ActiveMQ Artemis에 연결하기 위한 사용자 이름입니다. 기본 사용자 `artemis`을(를) 사용하지 마십시오. | 아니요 |
| `--stomp-password` | ActiveMQ Artemis에 연결하기 위한 암호입니다. 기본 암호 `artemis`을(를) 사용하지 마십시오. | 아니요 |
| `--stomp-ssl` | SSL을 사용하여 ActiveMQ Artemis에 연결할지를 나타냅니다. 기본값은 `false`입니다. ActiveMQ Artemis용 SSL 설정에 대한 자세한 내용은 ActiveMQ Artemis 를 참조하십시오. | 아니요 |
| `--consumers-wait-for-messages` | 소비자는 대기열에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오 | 아니요 |

**원격 저장소 옵션:**

| 이름 | 설명 | 필수? |
|--- |--- |--- |
| `remote-storage-driver` | 어댑터 이름<br>가능한 값:<br>**파일**: 원격 스토리지를 사용하지 않도록 설정하고 로컬 파일 시스템을 사용&#x200B;<br>**aws-s3**: [Amazon Simple Storage Service(Amazon S3) 사용](https://aws.amazon.com/s3/) | 아니요 |
| `remote-storage-bucket` | 개체 저장소 또는 컨테이너 이름 | 아니요 |
| `remote-storage-prefix` | 선택적 접두사(개체 저장소 내부의 위치) | 아니요 |
| `remote-storage-region` | 지역 이름 | 아니요 |
| `remote-storage-key` | 선택적 액세스 키 | 아니요 |
| `remote-storage-secret` | 선택적 비밀 키 | 아니요 |

**구성 옵션 잠금:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--lock-provider` | 공급자 이름 잠금<br><br>사용 가능한 잠금 공급자: `db`, `zookeeper`, `file`.<br><br>기본 잠금 공급자: `db` | 아니요 |
| `--lock-db-prefix` | `db` 잠금 공급자를 사용할 때 잠금 충돌을 방지하기 위한 특정 DB 접두사입니다.<br><br>기본값: `NULL` | 아니요 |
| `--lock-zookeeper-host` | `zookeeper` 잠금 공급자를 사용하는 경우 Zookeeper 클러스터에 연결할 호스트 및 포트입니다.<br><br>예: `127.0.0.1:2181` | 예, `--lock-provider=zookeeper`을(를) 설정하는 경우 |
| `--lock-zookeeper-path` | Zookeeper가 잠금을 저장하는 경로입니다.<br><br>기본 경로는 `/magento/locks`입니다. | 아니요 |
| `--lock-file-path` | 파일 잠금이 저장되는 경로입니다. | 예, `--lock-provider=file`을(를) 설정하는 경우 |

**소비자 구성 옵션:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>응용 프로그램을 설치한 후 모듈을 사용하거나 사용하지 않으려면 [모듈 사용 및 사용 안 함](manage-modules.md)을 참조하세요.

**중요 데이터:**

{{$include /help/_includes/sensitive-data.md}}

### 샘플 localhost 설치

다음 예는 다양한 옵션을 사용하여 로컬로 Adobe Commerce을 설치하는 명령을 보여 줍니다.

#### 예제 1 - 관리자 계정을 사용한 기본 설치

다음 예제에서는 다음 옵션을 사용하여 애플리케이션을 설치합니다.

* 응용 프로그램이 `magento2`의 웹 서버 docroot에 상대적인 `localhost` 디렉터리에 설치되어 있고 관리자의 경로는 `admin`이므로 다음과 같습니다.

  상점 URL은 `http://127.0.0.1`입니다.

* 데이터베이스 서버가 웹 서버와 동일한 호스트에 있습니다.

  데이터베이스 이름은 `magento`이고 사용자 이름과 암호는 모두 `magento`입니다.

* 서버 재작성 사용

* 관리자는 다음과 같은 속성을 갖습니다.

   * 이름과 성은 `Commerce User`입니다.
   * 사용자 이름은 `admin`이고 암호는 `admin123`입니다.
   * 전자 메일 주소는 `user@example.com`입니다.

* 기본 언어는 `en_US`입니다(미국 영어).
* 기본 통화는 미국 달러입니다
* 기본 시간대는 미국 중부(아메리카/시카고)입니다.
* Elasticsearch 7이 `es-host.example.com`에 설치되어 있고 포트 9200에 연결됩니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

성공적인 설치를 나타내는 다음 디스플레이와 유사한 메시지:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 예제 2 - 관리자 계정이 없는 기본 설치

다음 예와 같이 관리자 사용자를 생성하지 않고 응용 프로그램을 설치할 수 있습니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

설치가 완료되면 다음과 같은 메시지가 표시됩니다.

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

설치 후 `admin:user:create` 명령을 사용하여 관리자 사용자를 만들 수 있습니다.
[관리자 만들기 또는 편집](admin.md#create-or-edit-an-administrator)

#### 예제 3 - 추가 옵션과 함께 설치

다음 예제에서는 다음 옵션을 사용하여 애플리케이션을 설치합니다.

* Magapplication이 `magento2`의 웹 서버 docroot에 상대적인 `localhost` 디렉터리에 설치되어 있고 관리자의 경로가 `admin`이므로:

  상점 URL은 `http://127.0.0.1`입니다.

* 데이터베이스 서버가 웹 서버와 동일한 호스트에 있습니다.

  데이터베이스 이름은 `magento`이고 사용자 이름과 암호는 모두 `magento`입니다.

* 관리자는 다음과 같은 속성을 갖습니다.

   * 이름과 성은 `Commerce User`입니다.
   * 사용자 이름은 `admin`이고 암호는 `admin123`입니다.
   * 전자 메일 주소는 `user@example.com`입니다.

* 기본 언어는 `en_US`입니다(미국 영어).
* 기본 통화는 미국 달러입니다
* 기본 시간대는 미국 중부(아메리카/시카고)입니다.
* 설치 관리자는 먼저 테이블과 스키마를 설치하기 전에 데이터베이스를 정리합니다
* `ORD$` 판매 주문 증분 접두사를 사용합니다(특수 문자 [`$`]이(가) 포함되어 있으므로 값을 큰따옴표로 묶어야 함).
* 세션 데이터가 데이터베이스에 저장됩니다.
* 서버 재작성 사용
* Elasticsearch 7이 `es-host.example.com`에 설치되어 있고 포트 9200에 연결됩니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>명령을 한 줄에 입력하거나 앞의 예제와 같이 각 줄의 끝에 `\` 문자를 사용하여 입력해야 합니다.

설치가 완료되면 다음과 같은 메시지가 표시됩니다.

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 예제 4 - ActiveMQ Artemis와 함께 설치

다음 예는 ActiveMQ Artemis를 메시지 브로커로 사용하여 Adobe Commerce을 설치하는 방법을 보여 줍니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>ActiveMQ Artemis를 설치하려면 Adobe Commerce 2.4.6 이상이 필요합니다.

>[!TIP]
>
>응용 프로그램 서버에 액세스할 수 있는 사용자 계정이 한 개 있는 경우 [마스크 설정](../next-steps/set-umask.md)을 참조하세요. 이러한 유형의 설정은 공유 호스팅에 일반적으로 사용됩니다.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
