---
title: MySQL 지침
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 대한 MySQL 및 MariaDB를 설치 및 구성합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# 일반 MySQL 지침

자세한 내용은 [시스템 요구 사항](../../system-requirements.md) 지원되는 버전의 MySQL에 대해 설명합니다.

Adobe _강하게_ 데이터베이스를 설정할 때는 다음 표준을 준수하는 것이 좋습니다.

* Adobe Commerce 및 Magento Open Source 사용 [MySQL 데이터베이스 트리거](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 다시 색인화하는 동안 데이터베이스 액세스를 개선합니다. 인덱서 모드가 [예약](../../../configuration/cli/manage-indexers.md#configure-indexers). 사용자 지정 트리거로 인해 향후 Adobe Commerce 및 Magento Open Source 버전과 호환되지 않는 문제가 발생할 수 있으므로 애플리케이션에서 데이터베이스의 사용자 지정 트리거를 지원하지 않습니다.
* 숙지하십시오 [이러한 잠재적 MySQL 트리거 제한 사항](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 계속하기 전에
* 데이터베이스 보안 자세를 강화하려면 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) 잘못된 데이터 값을 저장하지 않도록 하는 SQL 모드로서, 이로 인해 원치 않는 데이터베이스 상호 작용이 발생할 수 있습니다.
* Adobe Commerce 및 Magento Open Source 작업 _not_ mySQL 문 기반 복제를 지원합니다. 를 사용해야 합니다. _전용_ [행 기반 복제](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce 및 Magento Open Source은 현재 `CREATE TEMPORARY TABLE` 트랜잭션 내에 있는 문, [호환되지 않음](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 데이터베이스 구현에서는 다음과 같은 GTID 기반 복제를 사용합니다 [Google Cloud SQL 2세대 인스턴스](https://cloud.google.com/sql/docs/features#differences). MySQL for Cloud SQL 8.0을 다른 방법으로 고려하십시오.

>[!NOTE]
>
>웹 서버와 데이터베이스 서버가 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에 설명된 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md).

## Ubuntu에 MySQL 설치

Adobe Commerce 및 Magento Open Source 2.4를 설치하려면 MySQL 8.0을 새로 설치해야 합니다. 시스템에 MySQL을 설치하는 방법에 대한 지침은 아래 링크를 따르십시오.

* [우분투](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

많은 수의 제품을 가져올 것으로 예상되면 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 기본값은 16MB입니다.

>[!NOTE]
>
>기본값은 클라우드 인프라의 Adobe Commerce에 적용됩니다 _및_ 온-프레미스 프로젝트. Adobe Commerce on cloud infrastructure pro 고객은 지원 티켓을 열어 `max_allowed_packet` 값. Adobe Commerce on cloud infrastructure Starter 고객은 의 구성을 업데이트하여 가치를 높일 수 있습니다 `/etc/mysql/mysql.cnf` 파일.

값을 늘리려면 `/etc/mysql/mysql.cnf` 파일을 텍스트 편집기에서 열고 `max_allowed_packet`. 변경 내용을 `mysql.cnf` 파일에서 텍스트 편집기를 닫고 MySQL(`service mysql restart`).

설정한 값을 선택적으로 확인하려면 다음 명령을 `mysql>` 프롬프트:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

그럼, [데이터베이스 인스턴스 구성](#configuring-the-database-instance).

## MySQL 8 변경 사항

Adobe Commerce 및 Magento Open Source 2.4에 대해 MySQL 8에 대한 지원을 추가했습니다.
이 섹션에서는 개발자가 알아야 하는 MySQL 8의 주요 변경 사항에 대해 설명합니다.

### 정수 유형(패딩)의 너비가 제거됨

정수 데이터 형식(TINYINT, SMALLINT, MEDIUMUNT, INT, BIGINT)에 대한 표시 너비 사양이 MySQL 8.0.17에서 더 이상 사용되지 않습니다. 출력에 데이터 형식 정의를 포함하는 문은 TINYINT(1)를 제외하고 정수 형식의 표시 너비를 더 이상 표시하지 않습니다. MySQL Connectors에서는 TINYINT(1) 열이 부울 열로 시작되었다고 가정합니다. 이 예외는 그들이 계속 그 가정을 할 수 있도록 해줍니다.

#### 예

mysql 8.19에서 admin_user 설명

| 필드 | 유형 | Null | 키 | 기본값 | 추가 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 아니요 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 예 |  | `NULL` |  |
| `lastname` | `varchar(32`) | 예 |  | `NULL` |  |
| `email` | `varchar(128)` | 예 |  | `NULL` |  |
| `username` | `varchar(40)` | 예 | UNI | `NULL` |  |
| `password` | `varchar(255)` | 아니요 |  | `NULL` |  |
| `created` | `timestamp` | 아니요 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 아니요 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 업데이트 시 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 예 |  | `NULL` |  |
| `lognum` | `smallint unsigned` | 아니요 |  | `0` |  |

제외 _TINYINT(1)_, 모든 정수 패딩(TINYINT > 1, SMALLINT, MEDIUMUNT, INT, BIGINT)은 `db_schema.xml` 파일.

자세한 내용은 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 기본 정렬 기준 동작

8.0 이전의 항목은 외래 키로 정렬되었습니다. 기본 정렬 순서는 사용되는 엔진에 따라 다릅니다.
코드가 특정 정렬에 종속되는 경우 항상 정렬 순서를 지정합니다.

### GROUP BY에 대해 사용되지 않는 ASC 및 DESC 구분자

MySQL 8.0.13부터 사용되지 않음 `ASC` 또는 `DESC` 구분자 `GROUP BY` 절이 제거되었습니다. 이전에 `GROUP BY` 정렬하면 이전 MySQL 버전과 다른 결과가 나타날 수 있습니다. 특정 정렬 순서를 만들려면 `ORDER BY` 절.

## Commerce 및 MySQL 8

MySQL 8을 제대로 지원하기 위해 Adobe Commerce 및 Magento Open Source이 일부 변경되었습니다.

### 쿼리 및 삽입 동작

Adobe Commerce 및 Magento Open Source에서 SET SQL_MODE=&quot;를 설정하여 일반 유효성 검사 동작을 사용하지 않도록 설정했습니다. `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 유효성 검사가 비활성화되어 있으면 MySQL에서 데이터를 잘라낼 수 있습니다. MySQL에서 쿼리 동작이 변경되었습니다. `Select * on my_table where IP='127.0.0.1'` 이제 IP 주소가 정수가 아닌 문자열로 올바르게 표시되므로 더 이상 결과를 반환하지 않습니다.

## MySQL 5.7에서 MySQL 8로 업그레이드

MySQL을 버전 5.7에서 버전 8로 제대로 업데이트하려면 다음 단계를 순서대로 수행해야 합니다.

1. Adobe Commerce 또는 Magento Open Source을 2.4.0으로 업그레이드하십시오. 모든 테스트를 수행하고 시스템이 예상대로 작동하는지 확인하십시오.
1. 유지 관리 모드 사용:

   ```bash
   bin/magento maintenance:enable
   ```

1. 데이터베이스 백업 만들기:

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL을 버전 8로 업데이트합니다.
1. 백업된 데이터를 MySQL로 가져옵니다.
1. 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드 비활성화:

   ```bash
   bin/magento maintenance:disable
   ```

## 데이터베이스 인스턴스 구성

이 섹션에서는 Adobe Commerce 또는 Magento Open Source에 대한 데이터베이스 인스턴스를 만드는 방법을 설명합니다. 새 데이터베이스 인스턴스가 권장되지만 선택적으로 기존 데이터베이스 인스턴스로 Adobe Commerce 또는 Magento Open Source을 설치할 수 있습니다.

MySQL 데이터베이스 인스턴스를 구성하려면

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. MySQL 명령 프롬프트로 이동합니다.

   ```bash
   mysql -u root -p
   ```

1. MySQL 입력 `root` 메시지가 표시되면 사용자의 암호입니다.
1. 다음 명령을 표시된 순서대로 입력하여 이름이 인 데이터베이스 인스턴스를 생성합니다 `magento` 사용자 이름 포함 `magento`:

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

1. Enter 키 `exit` 명령 프롬프트를 종료하려면 다음을 수행하십시오.

1. 데이터베이스를 확인합니다.

   ```bash
   mysql -u magento -p
   ```

   MySQL 모니터가 표시되면 데이터베이스를 제대로 만들었습니다. 오류가 표시되면 이전 명령을 반복합니다.

1. 웹 서버와 데이터베이스 서버가 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에 설명된 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md).

   비즈니스에 적합한 데이터베이스 인스턴스를 구성하는 것이 좋습니다. 데이터베이스를 구성할 때는 다음 사항에 유의하십시오.

   * 인덱서는 더 높은 값을 필요로 합니다. `tmp_table_size` 및 `max_heap_table_size` 값(예: 64M). 를 구성하는 경우 `batch_size` 매개 변수를 사용하면 테이블 크기 설정과 함께 해당 값을 조정하여 인덱서 성능을 향상시킬 수 있습니다. 자세한 내용은 [최적화 안내서](../../../performance/configuration.md) 추가 정보.

   * 최적의 성능을 위해 모든 MySQL 및 Adobe Commerce 또는 Magento Open Source 인덱스 테이블을 메모리에 유지할 수 있는지 확인합니다(예: 구성). `innodb_buffer_pool_size`).

   * MariaDB 10.4에서 재색인화를 수행하는 데 다른 MariaDB 또는 MySQL 버전과 비교하여 시간이 더 오래 걸립니다. 자세한 내용은 [구성 우수 사례](../../../performance/configuration.md#indexers).

1. MySQL용 `TIMESTAMP` 애플리케이션의 선언적 스키마 아키텍처에 필요한 환경 설정 및 구성을 따르는 필드, 시스템 변수 `explicit_defaults_for_timestamp` 를 로 설정해야 합니다. `on`.

   참조:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   이 설정을 사용하지 않으면 `bin/magento setup:db:status` 항상 `Declarative Schema is not up to date`.

>[!NOTE]
>
>다음 `explicit_defaults_for_timestamp` 설정은 더 이상 사용되지 않습니다. 이 설정은 향후 MySQL 릴리스에서 제거될 더 이상 사용되지 않는 타임스탬프 동작을 제어합니다. 이러한 동작을 제거하면 `explicit_defaults_for_timestamp` 설정도 제거됩니다.

>[!WARNING]
>
>클라우드 인프라 프로젝트에서 Adobe Commerce을 사용하려면 `explicit_defaults_for_timestamp` MySQL(MariaDB)에 대한 설정은 기본적으로 _해제_.

MariaDB 10.4에서 재색인화를 수행하는 데 다른 MariaDB 또는 MySQL 버전과 비교하여 시간이 더 오래 걸립니다. 색인 재지정 속도를 높이려면 다음 MariaDB 구성 매개 변수를 설정하는 것이 좋습니다.

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_selection = 1
