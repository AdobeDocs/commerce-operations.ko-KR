---
title: 고급 온-프레미스 설치
description: 소유한 인프라의 Adobe Commerce에 대한 고급 설치 시나리오에 대해 알아봅니다.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 0%

---

# 고급 온-프레미스 설치

>[!TIP]
>
>잃어버렸나? 도움의 손길이 필요하십니까? [빠른 시작 설치](composer.md) 또는 [기여자 설치](https://developer.adobe.com/commerce/contributor/guides/install/) 가이드를 사용해 보세요.

>[!NOTE]
>
>SELinux를 사용하도록 선택한 경우 [SELinux 및 iptables](prerequisites/security.md)을(를) 참조하십시오.

## 명령줄 인터페이스(CLI)

Adobe Commerce에는 설치 및 구성 작업을 위한 단일 명령줄 인터페이스가 있습니다. `<magento_root>/bin/magento`. 인터페이스는 다음을 포함하여 여러 작업을 수행합니다.

* 설치(및 관련 작업(예: 데이터베이스 스키마 생성 또는 업데이트, 배포 구성 만들기)
* 캐시를 지우는 중입니다.
* 색인 재지정을 포함한 색인 관리.
* 번역 사전 및 번역 패키지 만들기.
* 플러그인에 대한 공장 및 인터셉터와 같이 존재하지 않는 클래스를 생성하여 객체 관리자에 대한 종속성 삽입 구성을 생성합니다.
* 정적 보기 파일을 배포하는 중입니다.
* Less에서 CSS를 만드는 중입니다.

기타 이점:

* 사용 가능한 모든 설치 및 구성 명령이 하나의 명령(`<magento_root>/bin/magento list`)에 나열됩니다.
* Symfony 기반의 일관된 사용자 인터페이스.
* CLI는 타사 개발자가 &quot;플러그인&quot;할 수 있도록 확장 가능합니다. 이는 사용자의 학습곡선을 제거할 수 있다는 추가적인 이점이 있다.
* 비활성화된 모듈에 대한 명령이 표시되지 않습니다.

이 항목에서는 CLI를 사용하여 Adobe Commerce 소프트웨어를 설치하는 방법에 대해 설명합니다. 구성에 대한 자세한 내용은 [구성 가이드](../configuration/overview.md)를 참조하십시오.

필요한 경우 설치 관리자를 여러 번 실행할 수 있으므로 다음과 같은 작업을 수행할 수 있습니다.

* 다른 값 제공

  예를 들어 SSL(Secure Sockets Layer)에 대해 웹 서버를 구성한 후 설치 관리자를 실행하여 SSL 옵션을 설정할 수 있습니다.

* 이전 설치에서의 실수 수정
* 다른 데이터베이스 인스턴스에 Adobe Commerce 설치

## 설치를 시작하기 전에

시작하기 전에 다음 단계를 완료하십시오.

* 시스템이 [시스템 요구 사항](system-requirements.md)에서 설명한 요구 사항을 충족하는지 확인하십시오.

* [필수 구성 요소](prerequisites/overview.md) 작업을 모두 완료하십시오.

* 첫 번째 설치 단계를 완료합니다. [설치 또는 업그레이드 경로](overview.md)를 참조하세요.

* 응용 프로그램 서버에 로그인한 후 [파일 시스템 소유자로 전환](prerequisites/file-system/overview.md)합니다.

* [설치 빠른 시작](composer.md) 개요를 검토하십시오.

>[!NOTE]
>
>`bin` 하위 디렉터리에서 Adobe Commerce을 설치해야 합니다.

설치 관리자를 다양한 옵션으로 여러 번 실행하여 다음과 같은 설치 작업을 완료할 수 있습니다.

* 단계적으로 설치 — 예를 들어 웹 서버에서 SSL(Secure Sockets Layer)을 구성한 후 설치 관리자를 다시 실행하여 SSL 옵션을 설정할 수 있습니다.

* 이전 설치에서 발생한 오류를 수정합니다.

* 다른 데이터베이스 인스턴스에 Adobe Commerce을 설치합니다.

>[!NOTE]
>
>동일한 데이터베이스 인스턴스에 소프트웨어를 설치하는 경우 기본적으로 설치 관리자는 데이터베이스를 덮어쓰지 않습니다. 선택적 `cleanup-database` 매개 변수를 사용하여 이 동작을 변경할 수 있습니다.

[업데이트, 다시 설치, 제거](tutorials/uninstall.md)도 참조하세요.

### 보안 설치

{{$include /help/_includes/secure-install.md}}

## 설치 관리자 도움말 명령

다음 명령을 실행하여 일부 필수 인수의 값을 찾을 수 있습니다.

| 설치 관리자 인수 | 명령 |
| ------------------ | ------------------------------- |
| 언어 | `bin/magento info:language:list` |
| 통화 | `bin/magento info:currency:list` |
| 시간대 | `bin/magento info:timezone:list` |

>[!NOTE]
>
>이 명령을 실행할 때 오류가 표시되면 [설치 종속성 업데이트](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/)에 설명된 대로 설치 종속성을 업데이트했는지 확인하십시오.

## 명령줄에서 설치

install 명령은 다음 형식을 사용합니다.

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

다음 표에서는 설치 옵션 이름 및 값에 대해 설명합니다. 예를 들어 설치 명령은 [샘플 localhost 설치](#sample-localhost-installations)를 참조하십시오.

>[!NOTE]
>
>공백이나 특수 문자가 포함된 옵션은 작은따옴표나 큰따옴표로 묶어야 합니다.

**관리자 자격 증명:**

다음 옵션은 관리자에 대한 사용자 정보 및 자격 증명을 지정합니다.

설치 중 또는 설치 후에 관리 사용자 를 만들 수 있습니다. 설치 중에 사용자 만드는 경우 모든 관리자 자격 증명 변수가 필요합니다. 샘플 localhost 설치를[&#128279;](#sample-localhost-installations) 참조하세요.

다음 표에서는 사용 가능한 많은 설치 매개 변수를 제공하지만 전부는 아닙니다. 전체 목록은 명령 줄 도구 참조[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises)를 참조하십시오.

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--admin-firstname` | 관리자 사용자의 이름입니다. | 예 |
| `--admin-lastname` | 관리자 사용자의 성. | 예 |
| `--admin-email` | 관리자 사용자의 이메일 주소입니다. | 예 |
| `--admin-user` | 관리자 사용자 이름. | 예 |
| `--admin-password` | 관리자 사용자 암호. 암호는 길이가 7자 이상이어야 하며 최소 하나의 영문자와 최소 하나의 숫자를 포함해야 합니다. 보다 길고 복잡한 암호를 사용하는 것이 좋습니다. 전체 암호 문자열을 작은 따옴표로 묶습니다. For example, `--admin-password='A0b9%t3g'` | 예 |

**사이트 및 데이터베이스 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--base-url` | <br><br>`http[s]://<host or ip>/<your install dir>/` 형식 중 하나로 관리자 및 상점 앞에 액세스하는 데 사용할 기본 URL입니다.<br><br>**참고:** 구성표(http:// 또는 https://)와 뒤쪽 슬래시가 모두 필요합니다.<br><br>`<your install dir>`은(는) Adobe Commerce 소프트웨어를 설치할 docroot 상대 경로입니다. 웹 서버와 가상 호스트를 설정하는 방법에 따라 경로가 magento2이거나 비어 있을 수 있습니다.<br><br>Adobe Commerce 또는 MagenAdobe Commerce에 액세스하려면 `http://127.0.0.1/<your install dir>/` 또는 `http://127.0.0.1/<your install dir>/`을(를) 사용하십시오.<br><br>- `{{base_url}}`: 가상 호스트 설정 또는 Docker와 같은 가상화 환경에서 정의한 기본 URL을 나타냅니다. 예를 들어 호스트 이름이 `magento.example.com`인 가상 호스트를 설정하는 경우 `--base-url={{base_url}}`로 소프트웨어를 설치하고 `http://magento.example.com/admin`과(와) 같은 URL로 관리자에 액세스할 수 있습니다. | 예 |
| `--backend-frontname` | 관리자에 액세스할 수 있는 URI(Uniform Resource Identifier)입니다. 이 매개 변수를 생략하면 응용 프로그램에서 다음 패턴으로 임의의 URI를 생성할 수 있습니다. <code>admin_jkgdfq</code>.<br><br>보안을 위해 임의의 URI를 사용하는 것이 좋습니다. 무작위 URI는 해커나 악성 소프트웨어가 악용하기 더 어렵다.<br><br>설치가 끝날 때 URI가 표시됩니다. 나중에 언제든지 `bin/magento info:adminuri` 명령을 사용하여 표시할 수 있습니다.<br><br>값을 입력하기로 선택한 경우 admin, backend와 같은 일반적인 단어를 사용하지 않는 것이 좋습니다. 관리자 URI에는 영숫자 값과 밑줄 문자(`_`)만 포함될 수 있습니다. | 아니요 |
| `--db-host` | <br><br>- 데이터베이스 서버의 정규화된 호스트 이름 또는 IP 주소를 사용합니다.<br><br>- `localhost`(기본값) 또는 `127.0.0.1`(데이터베이스 서버가 웹 서버와 동일한 호스트에 있는 경우).localhost는 MySQL 클라이언트 라이브러리가 UNIX 소켓을 사용하여 데이터베이스에 연결함을 의미합니다. `127.0.0.1`을(를) 사용하면 클라이언트 라이브러리에서 TCP 프로토콜을 사용합니다. 소켓에 대한 자세한 내용은 [PHP PDO_MYSQL 설명서](https://www.php.net/manual/en/ref.pdo-mysql.php)를 참조하십시오.<br><br>**참고:** www.example.com:9000과 같은 호스트 이름에 데이터베이스 서버 포트를 선택적으로 지정할 수 있습니다. | 예 |
| `--db-name` | 데이터베이스 테이블을 설치할 데이터베이스 인스턴스의 이름입니다.<br><br>기본값은 `magento2`입니다. | 예 |
| `--db-user` | 데이터베이스 인스턴스 소유자의 사용자 이름.<br><br>기본값은 `root`입니다. | 예 |
| `--db-password` | 데이터베이스 인스턴스 소유자의 암호입니다. | 예 |
| `--db-prefix` | Adobe Commerce 테이블이 이미 있는 데이터베이스 인스턴스에 데이터베이스 테이블을 설치하는 경우에만 사용합니다.<br><br>이 경우 접두사를 사용하여 이 설치에 사용할 테이블을 식별하십시오. 일부 고객은 동일한 데이터베이스에 모든 테이블이 있는 Adobe Commerce 또는 MagenAdobe Commerceserver를 두 개 이상 가지고 있습니다.<br><br>접두사는 최대 5자까지 사용할 수 있습니다. 문자로 시작해야 하며 문자, 숫자 및 밑줄 문자만 포함할 수 있습니다.<br><br>이 옵션을 사용하면 두 개 이상의 Adobe Commerce 설치와 데이터베이스 서버를 공유할 수 있습니다 |
| `--db-ssl-key` | 클라이언트 키 경로. | 아니요 |
| `--db-ssl-cert` | 클라이언트 인증서 경로. | 아니요 |
| `--db-ssl-ca` | 서버 인증서 경로. | 아니요 |
| `--language` | 관리자 및 상점 첫 화면에서 사용할 언어 코드. (아직 확인하지 않은 경우 bin 디렉터리에서 `bin/magento info:language:list`을(를) 입력하여 언어 코드 목록을 볼 수 있습니다.) | 아니요 |
| `--currency` | 상점 첫 화면에서 사용할 기본 통화. (아직 완료하지 않은 경우 bin 디렉터리에서 `bin/magento info:currency:list`을(를) 입력하여 통화 목록을 볼 수 있습니다.) | 아니요 |
| `--timezone` | 관리자 및 상점 첫 화면에서 사용할 기본 시간대. (아직 수행하지 않은 경우 디렉토리에서 `bin/` 입력하여 `bin/magento info:timezone:list` 표준 시간대 목록을 볼 수 있습니다.) | 아니요 |
| `--use-rewrites` | `1` 는 storefront 및 Admin에서 생성된 링크에 대해 웹 서버 재작성을 사용함을 의미합니다.<br><br>`0` 웹 서버 다시 쓰기를 사용하지 않도록 설정합니다. 기본값입니다. | 아니요 |
| `--use-secure` | `1`을(를) 사용하면 상점 URL에서 SSL(Secure Sockets Layer)을 사용할 수 있습니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0`은(는) SSL 사용을 비활성화합니다. 이 경우 다른 모든 보안 URL 옵션도 0이라고 가정합니다. 이것이 기본값입니다. | 아니요 |
| `--base-url-secure` | 관리자 및 상점 첫 화면에 액세스할 때 사용할 보안 기본 URL은 `http[s]://<host or ip>/<your install dir>/` 형식입니다. | 아니요 |
| `--use-secure-admin` | `1`은(는) SSL을 사용하여 관리자에 액세스함을 의미합니다. 이 옵션을 선택하기 전에 웹 서버가 SSL을 지원하는지 확인하십시오.<br><br>`0`은(는) 관리자가 SSL을 사용하지 않음을 의미합니다. 이것이 기본값입니다. | 아니요 |
| `--admin-use-security-key` | 1은 애플리케이션 사용자가 임의로 생성된 키 값을 사용하여 관리 및 양식의 페이지에 액세스하도록 합니다. 이러한 키 값은 사이트 간 스크립트 위조 공격을 방지하는 데 도움이 됩니다. 이것이 기본값입니다.<br><br>`0`이(가) 키 사용을 비활성화합니다. | 아니요 |
| `--session-save` | <br><br>- `db` 중 하나를 사용하여 데이터베이스에 세션 데이터를 저장합니다. 클러스터된 데이터베이스가 있는 경우 데이터베이스 저장소를 선택하십시오. 그렇지 않으면 파일 기반 저장소에 비해 이점이 별로 없을 수 있습니다.<br><br>- `files` 파일 시스템에 세션 데이터를 저장합니다. 파일 시스템 액세스가 느리거나 클러스터된 데이터베이스가 있거나 세션 데이터를 Redis에 저장하려는 경우가 아니면 파일 기반 세션 저장소가 적절합니다.Redis에 세션 데이터를 저장하는 <br><br>- `redis`. 기본 또는 페이지 캐싱에 Redis를 사용하는 경우 Redis가 이미 설치되어 있어야 합니다. Redis에 대한 지원 구성에 대한 자세한 내용은 세션 저장소에 Redis 사용 을 참조하십시오. | 아니요 |
| `--key` | 키가 있는 경우 데이터베이스에서 중요한 데이터를 암호화할 키를 지정합니다. 없는 경우 애플리케이션에서 자동으로 생성합니다. | 예 |
| `--cleanup-database` | Adobe Commerce을 설치하기 전에 데이터베이스 테이블을 삭제하려면 값 없이 이 매개 변수를 지정합니다. 그렇지 않으면 데이터베이스가 그대로 유지됩니다. | 아니요 |
| `--db-init-statements` | 고급 MySQL 구성 매개 변수입니다. MySQL 데이터베이스에 연결할 때 실행할 데이터베이스 초기화 문을 사용합니다. 값을 설정하기 전에 이와 유사한 참조를 참조하십시오.<br><br>`SET NAMES utf8;`기본값은 입니다. | 아니요 |
| `--sales-order-increment-prefix` | 판매 주문의 접두사로 사용할 문자열 값을 지정합니다. 일반적으로 결제 처리자의 고유한 주문 번호를 보장하는 데 사용됩니다. | 아니요 |

**검색 엔진 구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--search-engine` | 검색 엔진으로 사용할 Elasticsearch 또는 OpenSearch 버전입니다. 기본값은 `elasticsearch7`입니다. Elasticsearch 5는 더 이상 사용되지 않으므로 권장되지 않습니다. | 아니요 |
| `--elasticsearch-host` | Elasticsearch이 실행 중인 호스트 이름 또는 IP 주소입니다. 기본값은 `localhost`입니다. | 아니요 |
| `--elasticsearch-port` | 수신 HTTP 요청에 대한 Elasticsearch 포트입니다. 기본값은 `9200`입니다. | 아니요 |
| `--elasticsearch-index-prefix` | Elasticsearch 검색 색인을 식별하는 접두사입니다. 기본값은 `magento2`입니다. | 아니요 |
| `--elasticsearch-timeout` | 시스템 제한 시간(초)입니다. 기본값은 `15`입니다. | 아니요 |
| `--elasticsearch-enable-auth` | Elasticsearch 서버에서 인증을 활성화합니다. 기본값은 `false`입니다. | 아니요 |
| `--elasticsearch-username` | Elasticsearch 서버에 인증할 사용자 ID입니다. | 인증이 활성화되지 않은 경우 아니요 |
| `--elasticsearch-password` | Elasticsearchserver에 인증하기 위한 암호입니다. | 인증이 활성화되지 않은 경우 아니요 |
| `--opensearch-host` | OpenSearch가 실행 중인 호스트 이름 또는 IP 주소입니다. 기본값은 `localhost`입니다. | 아니요 |
| `--opensearch-port` | 수신 HTTP 요청에 대한 OpenSearch 포트. 기본값은 `9200`입니다. | 아니요 |
| `--opensearch-index-prefix` | OpenSearch 검색 인덱스를 식별하는 접두사입니다. 기본값은 `magento2`입니다. | 아니요 |
| `--opensearch-timeout` | 시스템 제한 시간(초)입니다. 기본값은 `15`입니다. | 아니요 |
| `--opensearch-enable-auth` | OpenSearch 서버에서 인증을 활성화합니다. 기본값은 `false`입니다. | 아니요 |
| `--opensearch-username` | OpenSearch 서버에 인증할 사용자 ID입니다. | 인증이 활성화되지 않은 경우 아니요 |
| `--opensearch-password` | OpenSearch 서버에 인증하기 위한 암호입니다. | 인증이 활성화되지 않은 경우 아니요 |

**[!DNL RabbitMQ]구성 옵션:**

| 이름 | 값 | 필수? |
|--- |--- |--- |
| `--amqp-host` | [!DNL RabbitMQ]의 설치를 아직 설정하지 않은 한 `--amqp` 옵션을 사용하지 마십시오. [!DNL RabbitMQ] 설치 및 구성에 대한 자세한 내용은 [!DNL RabbitMQ] 설치 를 참조하십시오.<br><br>호스트 이름([!DNL RabbitMQ]이 설치되어 있음). | 아니요 |
| `--amqp-port` | [!DNL RabbitMQ]에 연결하는 데 사용할 포트입니다. 기본값은 5672입니다. | 아니요 |
| `--amqp-user` | [!DNL RabbitMQ]에 연결하기 위한 사용자 이름입니다. 기본 사용자 `guest`을(를) 사용하지 마십시오. | 아니요 |
| `--amqp-password` | [!DNL RabbitMQ]에 연결하기 위한 암호입니다. 기본 암호 `guest`을(를) 사용하지 마십시오. | 아니요 |
| `--amqp-virtualhost` | 에 연결 [!DNL RabbitMQ]하기 위한 가상 호스트. 기본값은 `/`입니다. | 아니요 |
| `--amqp-ssl` | 에 연결 [!DNL RabbitMQ]할지 여부를 나타냅니다. 기본값은 `false`입니다. [!DNL RabbitMQ]의 SSL 설정에 대한 자세한 내용은 [!DNL RabbitMQ]을(를) 참조하십시오. | 아니요 |
| `--consumers-wait-for-messages` | 소비자는 대기열에서 메시지를 기다려야 합니까? 1 - 예, 0 - 아니오 | 아니요 |

**잠금 구성 옵션:**

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
>Adobe Commerce 설치 후 모듈을 사용하거나 사용하지 않으려면 [모듈 사용 및 사용 안 함](tutorials/manage-modules.md)을 참조하세요.

**중요 데이터:**

{{$include /help/_includes/sensitive-data.md}}

### 샘플 localhost 설치

다음 예는 다양한 옵션을 사용하여 로컬로 Adobe Commerce을 설치하는 명령을 보여 줍니다.

#### 예제 1 - 관리자 계정을 사용한 기본 설치

다음 예에서는 다음 옵션과 함께 Adobe Commerce을 설치합니다.

* 애플리케이션 위치는 웹 서버 docroot `localhost` 에 상대적인 `magento2` 디렉토리에 설치되며 관리자 경로는 다음과 같습니다`admin`.

  상점 URL `http://127.0.0.1`

* 데이터베이스 서버는 웹 서버와 동일한 호스트 상에 있습니다.

  데이터베이스 이름은 `magento`이고 사용자 이름과 암호 모두 `magento`

* 서버 다시 쓰기 사용

* 관리자는 다음과 같은 속성을 갖습니다.

   * 이름과 성은 `Magento User`입니다.
   * 사용자 이름은 `admin`이고 암호는 `admin123`입니다.
   * 전자 메일 주소는 `user@example.com`입니다.

* 기본 언어는 `en_US`입니다(미국 영어).
* 기본 통화는 미국 달러입니다
* 기본 시간대는 미국 중부(아메리카/시카고)입니다.
* OpenSearch 1.2가 `os-host.example.com`에 설치되어 있으며 포트 9200에 연결됩니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

성공적인 설치를 나타내는 다음 디스플레이와 유사한 메시지:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 예제 2— 관리자 계정이 없는 기본 설치

다음 예와 같이 관리자 사용자를 작성하지 않고 Adobe Commerce을 설치할 수 있습니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
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
[관리자 만들기 또는 편집](tutorials/admin.md#create-or-edit-an-administrator)

#### 예제 3 - 추가 옵션과 함께 설치

다음 예에서는 다음 옵션과 함께 Adobe Commerce을 설치합니다.

* 응용 프로그램이 `localhost`의 웹 서버 docroot에 상대적인 `magento2` 디렉터리에 설치되어 있고 관리자의 경로는 `admin`이므로 다음과 같습니다.

  상점 URL은 `http://127.0.0.1`입니다.

* 데이터베이스 서버가 웹 서버와 동일한 호스트에 있습니다.

  데이터베이스 이름은 `magento`이고 사용자 이름과 암호는 모두 `magento`입니다.

* 관리자는 다음과 같은 속성을 갖습니다.

   * 이름과 성은 `Magento User`입니다.
   * 사용자 이름은 `admin`이고 암호는 `admin123`입니다.
   * 이메일 주소는 `user@example.com`

* 기본 언어는 (미국 영어)입니다 `en_US` .
* 기본 통화는 미국 달러입니다.
* 기본 시간대는 미국 중부(아메리카/시카고)입니다.
* 설치 관리자는 테이블 및 스키마를 설치하기 전에 먼저 데이터베이스를 정리합니다
* 판매 주문 증분 접두사 `ORD$`을(를) 사용할 수 있습니다. 특수 문자 [`$`]이(가) 포함되어 있으므로 값을 큰따옴표로 묶어야 합니다.
* 세션 데이터가 데이터베이스에 저장됩니다.
* 서버 재작성 사용
* OpenSearch가 `os-host.example.com`에 설치되어 있으며 포트 9200에 연결됩니다.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>명령을 한 줄에 입력하거나 앞의 예제와 같이 각 줄의 끝에 `\` 문자를 사용하여 입력해야 합니다.

설치에 성공하면 다음과 같은 메시지가 좋아요 표시됩니다.

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
