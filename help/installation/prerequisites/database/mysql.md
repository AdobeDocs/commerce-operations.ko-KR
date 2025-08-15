---
title: MySQL 지침
description: Adobe Commerce의 온프레미스 설치용 MySQL 및 MariaDB를 설치하고 구성하려면 다음 단계를 따르십시오.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# 일반 MySQL 지침

지원되는 MySQL 버전은 [시스템 요구 사항](../../system-requirements.md)을 참조하십시오.

Adobe _강력하게_&#x200B;에서는 데이터베이스를 설정할 때 다음 표준을 준수하는 것이 좋습니다.

* Adobe Commerce은 리인덱싱하는 동안 데이터베이스 액세스를 개선하기 위해 [MySQL 데이터베이스 트리거](https://dev.mysql.com/doc/refman/8.0/en/triggers.html)를 사용합니다. 인덱서 모드가 [일정](../../../configuration/cli/manage-indexers.md#configure-indexers)(으)로 설정되면 생성됩니다. 사용자 지정 트리거는 향후 Adobe Commerce 버전과 호환되지 않을 수 있으므로 응용 프로그램은 데이터베이스에서 사용자 지정 트리거를 지원하지 않습니다.
* 계속하기 전에 [이러한 잠재적인 MySQL 트리거 제한 사항](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html)을 숙지하십시오.
* 데이터베이스 보안 상태를 향상시키려면 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL 모드를 활성화하여 잘못된 데이터 값을 저장하여 원치 않는 데이터베이스 상호 작용이 발생할 수 있습니다.
* Adobe Commerce은 MySQL 문 기반 복제를 지원하지 _않습니다_. _전용_ [행 기반 복제](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html)를 사용해야 합니다.

>[!WARNING]
>
>Adobe Commerce은 현재 트랜잭션 내에서 `CREATE TEMPORARY TABLE` 문을 사용합니다. 이 문은 데이터베이스 구현에서 [Google Cloud SQL 2세대 인스턴스](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html)와 같은 GTID 기반 복제를 사용하는 [호환되지 않음](https://cloud.google.com/sql/docs/features#differences)입니다. 대안으로 Cloud SQL 8.0용 MySQL을 고려해 보십시오.

>[!NOTE]
>
>웹 서버와 데이터베이스 서버가 서로 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에서 설명한 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md)을 참조하십시오.

## Ubuntu에 MySQL 설치

Adobe Commerce 2.4를 사용하려면 MySQL 8.0을 완전히 설치해야 합니다. 컴퓨터에 MySQL을 설치하는 방법은 아래 링크를 참조하십시오.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

많은 수의 제품을 가져오려면 기본값인 16MB보다 큰 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html)의 값을 늘릴 수 있습니다.

>[!NOTE]
>
>기본값은 클라우드 인프라 _및_&#x200B;의 온-프레미스 프로젝트에 적용되는 Adobe Commerce입니다. Adobe Commerce on cloud infrastructure Pro 고객은 지원 티켓을 열어 `max_allowed_packet` 값을 늘려야 합니다. 클라우드 인프라 시작 고객의 Adobe Commerce은 `/etc/mysql/mysql.cnf` 파일에서 구성을 업데이트하여 값을 높일 수 있습니다.

값을 늘리려면 텍스트 편집기에서 `/etc/mysql/mysql.cnf` 파일을 열고 `max_allowed_packet`의 값을 찾습니다. 변경 내용을 `mysql.cnf` 파일에 저장하고 텍스트 편집기를 닫은 다음 MySQL(`service mysql restart`)을 다시 시작합니다.

설정한 값을 선택적으로 확인하려면 `mysql>` 프롬프트에 다음 명령을 입력하십시오.

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

그런 다음 [데이터베이스 인스턴스를 구성](#configuring-the-database-instance)합니다.

## MySQL 8 변경 사항

Adobe Commerce 2.4에 대해 MySQL 8에 대한 지원이 추가되었습니다.
이 섹션에서는 개발자가 알아야 하는 MySQL 8의 주요 변경 사항에 대해 설명합니다.

### 정수 유형(패딩)에 대한 너비가 제거됨

정수 데이터 형식(TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT)에 대한 표시 너비 사양은 MySQL 8.0.17에서 더 이상 사용되지 않습니다. 출력에 데이터 유형 정의를 포함하는 문은 TINYINT(1)를 제외하고 더 이상 정수 유형의 표시 너비를 표시하지 않습니다. MySQL 커넥터는 TINYINT(1) 열이 부울 열로 시작되었다고 가정합니다. 이 예외를 사용하면 계속해서 해당 가정을 할 수 있습니다.

#### 예

mysql 8.19에서 admin_user 설명

| 필드 | 유형 | Null | 키 | 기본값 | 추가 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 아니요 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 예 | | `NULL` | |
| `lastname` | `varchar(32`) | 예 | | `NULL` | |
| `email` | `varchar(128)` | 예 | | `NULL` | |
| `username` | `varchar(40)` | 예 | 유니 | `NULL` | |
| `password` | `varchar(255)` | 아니요 | | `NULL` | |
| `created` | `timestamp` | 아니요 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 아니요 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 업데이트의 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 예 | | `NULL` | |
| `lognum` | `smallint unsigned` | 아니요 | | `0` | |

_TINYINT(1)_&#x200B;을(를) 제외하고 모든 정수 패딩(TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT)은 `db_schema.xml` 파일에서 제거해야 합니다.

자세한 내용은 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature)을(를) 참조하십시오.

### 기본 정렬 기준 동작

8.0 이전에는 항목이 외래 키로 정렬되었습니다. 기본 정렬 순서는 사용된 엔진에 따라 다릅니다.
코드가 특정 정렬에 따라 달라지는 경우 항상 정렬 순서를 지정하십시오.

### 그룹화 기준(GROUP BY)에 대해 더 이상 사용되지 않는 ASC 및 DESC 한정자

MySQL 8.0.13부터 `ASC` 절에 대해 더 이상 사용되지 않는 `DESC` 또는 `GROUP BY` 한정자가 제거되었습니다. 이전에 `GROUP BY` 정렬에 의존했던 쿼리는 이전 MySQL 버전과 다른 결과를 생성할 수 있습니다. 지정된 정렬 순서를 만들려면 `ORDER BY` 절을 제공합니다.

## Commerce 및 MySQL 8

MySQL 8을 제대로 지원하기 위해 Adobe Commerce이 일부 변경되었습니다.

### 쿼리 및 삽입 동작

Adobe Commerce이 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`에서 SET SQL_MODE=&#39;&#39;를 설정하여 일반 유효성 검사 동작을 비활성화했습니다. 유효성 검사가 비활성화되어 있으면 MySQL에서 데이터를 잘라낼 수 있습니다. MySQL에서 쿼리 동작이 변경되었습니다. `Select * on my_table where IP='127.0.0.1'`은(는) 이제 IP 주소가 정수가 아닌 문자열로 올바르게 표시되므로 더 이상 결과를 반환하지 않습니다.

## MySQL 5.7에서 MySQL 8로 업그레이드

MySQL을 버전 5.7에서 버전 8로 올바르게 업데이트하려면 다음 단계를 순서대로 수행해야 합니다.

1. Adobe Commerce을 2.4.0으로 업그레이드하십시오.
모든 것을 테스트하고 시스템이 예상대로 작동하는지 확인하십시오.
1. 유지 관리 모드 활성화:

   ```bash
   bin/magento maintenance:enable
   ```

1. 데이터베이스 백업 만들기:

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL을 버전 8로 업데이트합니다.
1. 백업된 데이터를 MySQL로 가져옵니다.
1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드 비활성화:

   ```bash
   bin/magento maintenance:disable
   ```

## 데이터베이스 인스턴스 구성

이 섹션에서는 Adobe Commerce에 대한 데이터베이스 인스턴스를 생성하는 방법에 대해 설명합니다. 새 데이터베이스 인스턴스가 권장되지만 선택적으로 기존 데이터베이스 인스턴스와 함께 Adobe Commerce을 설치할 수 있습니다.

MySQL 데이터베이스 인스턴스를 구성하려면 다음을 수행합니다.

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. MySQL 명령 프롬프트로 이동:

   ```bash
   mysql -u root -p
   ```

1. 메시지가 표시되면 MySQL `root` 사용자의 암호를 입력하십시오.
1. 사용자 이름이 `magento`인 데이터베이스 인스턴스 `magento`을(를) 만들려면 표시된 순서대로 다음 명령을 입력하십시오.

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. 명령 프롬프트를 종료하려면 `exit`을(를) 입력하십시오.

1. 데이터베이스 확인:

   ```bash
   mysql -u magento -p
   ```

   MySQL 모니터가 표시되면 데이터베이스가 제대로 만들어진 것입니다. 오류가 표시되면 이전 명령을 반복합니다.

1. 웹 서버와 데이터베이스 서버가 서로 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에서 설명한 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md)을 참조하십시오.

   비즈니스에 맞게 데이터베이스 인스턴스를 구성하는 것이 좋습니다. 데이터베이스를 구성할 때는 다음 사항에 유의하십시오.

   * 인덱서에는 더 높은 `tmp_table_size` 및 `max_heap_table_size` 값(예: 64M)이 필요합니다. `batch_size` 매개 변수를 구성하는 경우 테이블 크기 설정과 함께 해당 값을 조정하여 인덱서 성능을 향상시킬 수 있습니다. 자세한 내용은 [최적화 안내서](../../../performance/configuration.md)를 참조하세요.

   * 최적의 성능을 위해 모든 MySQL 및 Adobe Commerce 인덱스 테이블을 메모리에 유지할 수 있는지 확인하십시오(예: `innodb_buffer_pool_size` 구성).

   * MariaDB 10.4에 대한 리인덱싱은 다른 MariaDB 또는 MySQL 버전에 비해 시간이 더 걸립니다. [구성 모범 사례](../../../performance/configuration.md#indexers)를 참조하세요.

1. MySQL `TIMESTAMP` 필드가 응용 프로그램의 선언적 스키마 아키텍처에 필요한 환경 설정 및 컴포지션을 따르도록 하려면 시스템 변수 `explicit_defaults_for_timestamp`을(를) `on`(으)로 설정해야 합니다.

   참조:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   이 설정을 사용하지 않으면 `bin/magento setup:db:status`은(는) 항상 `Declarative Schema is not up to date`을(를) 보고합니다.

>[!NOTE]
>
>`explicit_defaults_for_timestamp` 설정이 사용되지 않습니다. 이 설정은 향후 MySQL 릴리스에서 제거될 더 이상 사용되지 않는 타임스탬프 동작을 제어합니다. 이러한 동작을 제거하면 `explicit_defaults_for_timestamp` 설정도 제거됩니다.

>[!WARNING]
>
>클라우드 인프라 프로젝트의 Adobe Commerce의 경우 MySQL(MariaDB)에 대한 `explicit_defaults_for_timestamp` 설정이 기본적으로 _OFF_&#x200B;로 설정됩니다.

{{$include /help/_includes/maria-db-config.md}}
