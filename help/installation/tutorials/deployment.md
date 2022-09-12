---
title: 배포 구성 만들기 또는 업데이트
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 배포 구성을 관리합니다.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# 배포 구성 만들기 또는 업데이트

이 명령을 사용하기 위한 사전 요구 사항이 없습니다.

## 배포 구성 만들기 또는 업데이트

[배포 구성](../../configuration/reference/deployment-files.md) 는 응용 프로그램을 초기화하고 부트스트랩에 필요한 정보를 제공합니다.

다음 경우 이 명령을 사용할 수 있습니다.

* 이전에 응용 프로그램을 설치했으며 배포 구성을 수정하려고 했습니다
* 배포 구성만 만들고 다른 방법으로 설치를 계속하려는 경우
* 다른 영향을 주지 않고 배포 구성을 업데이트하려면

명령 옵션:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

다음 표에서는 설치 매개 변수 및 값의 의미에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))을 클릭하여 관리자에 액세스합니다.<br><br>악용을 방지하기 위해 admin, backend와 같은 공통 단어를 사용하지 않는 것이 좋습니다. 관리자 URI에는 영숫자 값과 밑줄 문자(`_`)만 사용할 수 있습니다. | 아니요 |
| `--db-host` | 다음 중 하나를 사용합니다.<br><br>- 데이터베이스 서버의 정규화된 호스트 이름 또는 IP 주소입니다.<br><br>- `localhost` (기본값) 또는 `127.0.0.1` 데이터베이스 서버가 웹 서버와 동일한 호스트에 있는 경우 localhost는 MySQL 클라이언트 라이브러리가 UNIX 소켓을 사용하여 데이터베이스에 연결함을 의미합니다. `127.0.0.1` 클라이언트 라이브러리가 TCP 프로토콜을 사용하도록 합니다. 소켓에 대한 자세한 내용은 [PHP PDO_MYSQL 설명서](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**참고:** 선택적으로 데이터베이스 서버 포트를 호스트 이름에서 지정할 수 있습니다. `www.example.com:9000` | 아니요 |
| `--db-name` | 데이터베이스 테이블을 설치할 데이터베이스 인스턴스의 이름입니다.<br><br>기본값은 입니다. `magento2`. | 아니요 |
| `--db-user` | 데이터베이스 인스턴스 소유자의 사용자 이름입니다.<br><br>기본값은 입니다. `root`. | 아니요 |
| `--db-password` | 데이터베이스 인스턴스 소유자의 암호입니다. | 아니요 |
| `--db-prefix` | Adobe Commerce 및 Magento Open Source 테이블이 이미 있는 데이터베이스 인스턴스에 데이터베이스 테이블을 설치하는 경우에만 사용합니다.<br><br>이 경우 설치 테이블을 식별하려면 접두어를 사용합니다. 일부 고객은 동일한 데이터베이스에 모든 테이블이 있는 서버에서 실행되는 둘 이상의 Adobe Commerce 또는 Magento Open Source 인스턴스를 가지고 있습니다.<br><br>접두사는 최대 5자 길이일 수 있습니다. 문자로 시작해야 하며 문자, 숫자 및 밑줄 문자만 포함할 수 있습니다.<br><br>이 옵션을 사용하면 이러한 고객이 둘 이상의 Adobe Commerce 또는 Magento Open Source 설치와 데이터베이스 서버를 공유할 수 있습니다. | 아니요 |
| `--session-save` | 다음 중 하나를 사용합니다.<br><br>- `db` 세션 데이터를 [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). 클러스터형 데이터베이스가 있는 경우 데이터베이스 저장소를 선택합니다. 그렇지 않으면 파일 기반 스토리지보다 많은 이점이 없을 수 있습니다.<br><br>- `files` 세션 데이터를 파일 시스템에 저장 파일 시스템 액세스 속도가 느리거나, 클러스터링된 데이터베이스가 있거나, 세션 데이터를 Redis에 저장하지 않는 한 파일 기반 세션 저장소가 적합합니다.<br><br>- `redis` 세션 데이터를 [세션 저장소에 Redis 사용](../../configuration/cache/config-redis.md). 기본 또는 페이지 캐싱에 Redis를 사용하는 경우 Redis가 이미 설치되어 있어야 합니다. | 아니요 |
| `--key` | 키가 있는 경우 암호화할 키를 지정합니다 [중요 데이터](#sensitive-data) 참조하십시오. 없는 경우 애플리케이션에서 자동으로 생성합니다. | 아니요 |
| `--db-init-statements` | 고급 MySQL 구성 매개 변수입니다. MySQL 데이터베이스에 연결할 때 데이터베이스 초기화 문을 사용하여 실행합니다.<br><br>기본값은 입니다. `SET NAMES utf8;`.<br><br>와 유사한 참조를 참조하십시오 [이거요](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 값을 설정하기 전에 먼저 | 아니요 |
| `--http-cache-hosts` | 삭제 요청을 보낼 HTTP 캐시 게이트웨이 호스트의 쉼표로 구분된 목록입니다. (예: Varnish 서버) 이 매개 변수를 사용하여 동일한 요청에서 제거할 호스트 또는 호스트를 지정합니다. 호스트가 하나만 있거나 여러 호스트가 있는 것은 문제가 되지 않습니다.<br><br>형식은 다음 이어야 합니다. `<hostname or ip>:<listen port>`를 생략할 수 있는 위치 `<listen port>` 포트 80이면 For example, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. 공백 문자로 호스트를 분리하지 마십시오. | 아니요 |

## 구성 데이터 가져오기

프로덕션 시스템을 설정할 때 구성 설정을 가져오는 것이 좋습니다. `config.php` 및 `env.php` 데이터베이스에 추가합니다.
이러한 설정에는 구성 경로 및 값, 웹 사이트, 저장소, 보기 및 테마가 포함됩니다.

웹 사이트, 저장, 보기 및 테마를 가져온 후에는 제품 속성을 만들고 제품 속성을 프로덕션 시스템의 웹 사이트, 저장소 및 저장소 보기에 적용할 수 있습니다.

프로덕션 시스템에서 다음 명령을 실행하여 구성 파일에서 데이터를 가져옵니다(`config.php` 및 `env.php`) 를 데이터베이스에 추가합니다.

```bash
bin/magento app:config:import [-n, --no-interaction]
```

선택 사항입니다 `[-n, --no-interaction]` 플래그를 사용하면 추가적인 확인 없이 명령을 실행할 수 있습니다.

자세한 내용은 [구성 파일에서 데이터 가져오기](../../configuration/cli/import-configuration.md)

### 중요 데이터

{{$include /help/_includes/sensitive-data.md}}
