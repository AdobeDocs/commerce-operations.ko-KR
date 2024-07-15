---
title: 배포 구성 만들기 또는 업데이트
description: Adobe Commerce 배포 구성을 관리하려면 다음 단계를 따르십시오.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# 배포 구성 만들기 또는 업데이트

이 명령을 사용하기 위한 필수 구성 요소가 없습니다.

## 배포 구성 만들기 또는 업데이트

[배포 구성](../../configuration/reference/deployment-files.md)은(는) 응용 프로그램을 초기화하고 부트스트랩해야 하는 정보를 제공합니다.

다음 경우에 이 명령을 사용할 수 있습니다.

* 이전에 응용 프로그램을 설치하고 배포 구성을 수정하려고 합니다.
* 배포 구성만 만들고 다른 방법으로 설치를 계속합니다
* 다른 항목에 영향을 주지 않고 배포 구성을 업데이트하려면

명령 옵션:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

다음 표에서는 설치 매개 변수와 값의 의미에 대해 설명합니다.

| 매개 변수 | 값 | 필수? |
|--- |--- |--- |
| `--backend-frontname` | 관리자에 액세스할 UNIFORM 리소스 식별자([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))입니다.<br><br>악용을 방지하려면 admin, backend와 같은 일반적인 단어를 사용하지 않는 것이 좋습니다. 관리자 URI에는 영숫자 값과 밑줄 문자(`_`)만 포함될 수 있습니다. | 아니요 |
| `--db-host` | <br><br>- 데이터베이스 서버의 정규화된 호스트 이름 또는 IP 주소를 사용합니다.데이터베이스 서버가 웹 서버와 동일한 호스트에 있는 경우 <br><br>- `localhost`(기본값) 또는 `127.0.0.1`. localhost는 MySQL 클라이언트 라이브러리가 UNIX 소켓을 사용하여 데이터베이스에 연결하는 것을 의미합니다. `127.0.0.1`을(를) 사용하면 클라이언트 라이브러리에서 TCP 프로토콜을 사용합니다. 소켓에 대한 자세한 내용은 [PHP PDO_MYSQL 설명서](https://www.php.net/manual/en/ref.pdo-mysql.php)를 참조하십시오.<br><br>**참고:** 필요에 따라 `www.example.com:9000`과(와) 같은 호스트 이름에 데이터베이스 서버 포트를 지정할 수 있습니다. | 아니요 |
| `--db-name` | 데이터베이스 테이블을 설치할 데이터베이스 인스턴스의 이름입니다.<br><br>기본값은 `magento2`입니다. | 아니요 |
| `--db-user` | 데이터베이스 인스턴스 소유자의 사용자 이름.<br><br>기본값은 `root`입니다. | 아니요 |
| `--db-password` | 데이터베이스 인스턴스 소유자의 암호입니다. | 아니요 |
| `--db-prefix` | Adobe Commerce 테이블이 이미 있는 데이터베이스 인스턴스에 데이터베이스 테이블을 설치하는 경우에만 사용합니다.<br><br>이 경우 접두사를 사용하여 이 설치에 사용할 테이블을 식별하십시오. 일부 고객은 동일한 데이터베이스에 있는 모든 테이블이 있는 서버에서 두 개 이상의 Adobe Commerce 인스턴스를 실행하고 있습니다.<br><br>접두사는 최대 5자까지 사용할 수 있습니다. 문자로 시작해야 하며 문자, 숫자 및 밑줄 문자만 포함할 수 있습니다.<br><br>이 옵션을 사용하면 두 개 이상의 Adobe Commerce 설치와 데이터베이스 서버를 공유할 수 있습니다. | 아니요 |
| `--session-save` | <br><br>- `db` 중 하나를 사용하여 [데이터베이스](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)에 세션 데이터를 저장합니다. 클러스터된 데이터베이스가 있는 경우 데이터베이스 저장소를 선택하십시오. 그렇지 않으면 파일 기반 저장소에 비해 이점이 별로 없을 수 있습니다.<br><br>- `files` 파일 시스템에 세션 데이터를 저장합니다. 파일 시스템 액세스가 느리거나 클러스터된 데이터베이스가 있거나 세션 데이터를 Redis에 저장하려는 경우가 아니면 파일 기반 세션 저장소가 적절합니다.<br><br>- `redis`에서 세션 데이터를 [세션 저장소에 Redis를 사용](../../configuration/cache/config-redis.md)합니다. 기본 또는 페이지 캐싱에 Redis를 사용하는 경우 Redis가 이미 설치되어 있어야 합니다. | 아니요 |
| `--key` | 키가 있으면 데이터베이스에서 [중요 데이터](#sensitive-data)를 암호화할 키를 지정하십시오. 없는 경우 애플리케이션에서 자동으로 생성합니다. | 아니요 |
| `--db-init-statements` | 고급 MySQL 구성 매개 변수. MySQL 데이터베이스에 연결할 때 데이터베이스 초기화 문을 사용하여 실행합니다.<br><br>기본값은 `SET NAMES utf8;`입니다.<br><br>값을 설정하기 전에 [이 항목](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)과(와) 유사한 참조를 참조하십시오. | 아니요 |
| `--http-cache-hosts` | 제거 요청을 전송할 HTTP 캐시 게이트웨이 호스트를 쉼표로 구분한 목록입니다. (예: 바니시 서버) 이 매개변수를 사용하여 동일한 요청에서 제거할 호스트를 지정합니다. (호스트가 하나만 있거나 여러 개 있는 경우에는 문제가 되지 않습니다.)<br><br>형식은 `<hostname or ip>:<listen port>`이어야 합니다. 포트 80인 경우 `<listen port>`을(를) 생략할 수 있습니다. 예: `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. 공백 문자로 호스트를 구분하지 마십시오. | 아니요 |

## 구성 데이터 가져오기

프로덕션 시스템을 설정할 때 `config.php` 및 `env.php`에서 데이터베이스로 구성 설정을 가져오는 것이 좋습니다.
이러한 설정에는 구성 경로 및 값, 웹 사이트, 스토어, 스토어 조회수 및 테마가 포함됩니다.

웹 사이트, 스토어, 스토어 보기 및 테마를 가져온 후 제품 속성을 만들고 프로덕션 시스템의 웹 사이트, 스토어 및 스토어 보기에 적용할 수 있습니다.

프로덕션 시스템에서 다음 명령을 실행하여 구성 파일(`config.php` 및 `env.php`)에서 데이터베이스로 데이터를 가져옵니다.

```bash
bin/magento app:config:import [-n, --no-interaction]
```

선택적 `[-n, --no-interaction]` 플래그를 사용하면 추가 확인 없이 명령을 실행할 수 있습니다.

자세한 내용은 [구성 파일에서 데이터 가져오기](../../configuration/cli/import-configuration.md)를 확인하세요.

### 중요 데이터

{{$include /help/_includes/sensitive-data.md}}
