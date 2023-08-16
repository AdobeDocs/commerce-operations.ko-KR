---
title: MySQL 지침
description: Adobe Commerce 및 Magento Open Source의 온프레미스 설치에 MySQL 및 MariaDB를 설치하고 구성하려면 다음 단계를 따르십시오.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# 일반 MySQL 지침

다음을 참조하십시오 [시스템 요구 사항](../../system-requirements.md) 지원되는 버전의 MySQL용

Adobe _강력하게_ 는 데이터베이스를 설정할 때 다음 표준을 준수할 것을 권장합니다.

* Adobe Commerce 및 Magento Open Source 사용 [MySQL 데이터베이스 트리거](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 리인덱싱하는 동안 데이터베이스 액세스를 개선합니다. 이러한 속성은 인덱서 모드가 로 설정되면 생성됩니다. [예약](../../../configuration/cli/manage-indexers.md#configure-indexers). 사용자 지정 트리거는 향후 Adobe Commerce 및 Magento Open Source 버전과 호환되지 않을 수 있으므로 응용 프로그램은 데이터베이스에서 사용자 지정 트리거를 지원하지 않습니다.
* 다음 내용에 대해 숙지하십시오. [이러한 잠재적인 MySQL 트리거 제한 사항](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 계속하기 전에
* 데이터베이스 보안 상태를 향상시키려면 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) 원하지 않는 데이터베이스 상호 작용이 발생할 수 있는 잘못된 데이터 값을 저장하지 않도록 하는 SQL 모드입니다.
* Adobe Commerce 및 Magento Open Source 작업 _아님_ mySQL 문 기반 복제를 지원합니다. 다음을 사용해야 합니다. _전용_ [행 기반 복제](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce은 현재 `CREATE TEMPORARY TABLE` 다음과 같은 트랜잭션 내 명령문 [호환되지 않음](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 데이터베이스 구현에서는 다음과 같은 GTID 기반 복제를 사용합니다. [Google Cloud SQL 2세대 인스턴스](https://cloud.google.com/sql/docs/features#differences). 대안으로 Cloud SQL 8.0용 MySQL을 고려해 보십시오.

>[!NOTE]
>
>웹 서버와 데이터베이스 서버가 서로 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에서 설명한 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md).

## Ubuntu에 MySQL 설치

Adobe Commerce 및 Magento Open Source 2.4를 사용하려면 MySQL 8.0을 완전히 설치해야 합니다. 컴퓨터에 MySQL을 설치하는 방법은 아래 링크를 참조하십시오.

* [우분투](https://ubuntu.com/server/docs/databases-mysql)
* [센트OS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

많은 수의 제품을 가져올 것으로 예상되는에 대한 값을 늘릴 수 있습니다. [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 기본값인 16MB보다 큽니다.

>[!NOTE]
>
>기본값은 클라우드 인프라의 Adobe Commerce에 적용됩니다 _및_ 온-프레미스 프로젝트 Adobe Commerce on cloud infrastructure Pro 고객은 지원 티켓을 열어 `max_allowed_packet` 값. Adobe Commerce on cloud infrastructure Starter 고객은 의 구성을 업데이트하여 가치를 높일 수 있습니다. `/etc/mysql/mysql.cnf` 파일.

값을 높이려면 `/etc/mysql/mysql.cnf` 파일을 텍스트 편집기에 넣고 `max_allowed_packet`. 변경 내용을 `mysql.cnf` 파일을 닫고 텍스트 편집기를 닫은 다음 MySQL을 다시 시작합니다(`service mysql restart`).

설정한 값을 선택적으로 확인하려면 `mysql>` 프롬프트:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

그런 다음, [데이터베이스 인스턴스 구성](#configuring-the-database-instance).

## MySQL 8 변경 사항

Adobe Commerce 및 Magento Open Source 2.4에 대해 MySQL 8에 대한 지원이 추가되었습니다.
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
| `modified` | `timestamp` | 아니요 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 업데이트 시 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 예 | | `NULL` | |
| `lognum` | `smallint unsigned` | 아니요 | | `0` | |

를 제외하고 _TINYINT(1)_, 모든 정수 패딩(TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT)은 `db_schema.xml` 파일.

자세한 내용은 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 기본 정렬 기준 동작

8.0 이전에는 항목이 외래 키로 정렬되었습니다. 기본 정렬 순서는 사용된 엔진에 따라 다릅니다.
코드가 특정 정렬에 따라 달라지는 경우 항상 정렬 순서를 지정하십시오.

### 그룹화 기준(GROUP BY)에 대해 더 이상 사용되지 않는 ASC 및 DESC 한정자

MySQL 8.0.13부터 사용되지 않음 `ASC` 또는 `DESC` 한정자 `GROUP BY` 조항이 제거되었습니다. 이전에 의존했던 쿼리 `GROUP BY` 정렬하면 이전 MySQL 버전과 다른 결과가 나타날 수 있습니다. 지정된 정렬 순서를 생성하려면 다음을 제공합니다. `ORDER BY` 절.

## Commerce 및 MySQL 8

MySQL 8을 제대로 지원하기 위해 Adobe Commerce 및 Magento Open Source이 일부 변경되었습니다.

### 쿼리 및 삽입 동작

Adobe Commerce 및 Magento Open Source은에서 SET SQL_MODE=&#39;&#39;를 설정하여 일반 유효성 검사 동작을 비활성화했습니다. `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 유효성 검사가 비활성화되어 있으면 MySQL에서 데이터를 잘라낼 수 있습니다. MySQL에서 쿼리 동작이 변경되었습니다. `Select * on my_table where IP='127.0.0.1'` 이제 IP 주소가 정수가 아닌 문자열로 제대로 표시되므로 가 더 이상 결과를 반환하지 않습니다.

## MySQL 5.7에서 MySQL 8로 업그레이드

MySQL을 버전 5.7에서 버전 8로 올바르게 업데이트하려면 다음 단계를 순서대로 수행해야 합니다.

1. Adobe Commerce 또는 Magento Open Source을 2.4.0으로 업그레이드하십시오. 모든 것을 테스트하고 시스템이 예상대로 작동하는지 확인하십시오.
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

이 섹션에서는 Adobe Commerce 또는 Magento Open Source에 대한 데이터베이스 인스턴스를 생성하는 방법에 대해 설명합니다. 새 데이터베이스 인스턴스가 권장되지만 선택적으로 기존 데이터베이스 인스턴스와 함께 Adobe Commerce 또는 Magento Open Source을 설치할 수 있습니다.

MySQL 데이터베이스 인스턴스를 구성하려면 다음을 수행합니다.

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. MySQL 명령 프롬프트로 이동:

   ```bash
   mysql -u root -p
   ```

1. MySQL 입력 `root` 메시지가 표시되면 사용자의 암호.
1. 표시된 순서대로 다음 명령을 입력하여 이름이 인 데이터베이스 인스턴스를 생성합니다. `magento` (사용자 이름 포함) `magento`:

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

1. 입력 `exit` 를 클릭하여 명령 프롬프트를 종료합니다.

1. 데이터베이스 확인:

   ```bash
   mysql -u magento -p
   ```

   MySQL 모니터가 표시되면 데이터베이스가 제대로 만들어진 것입니다. 오류가 표시되면 이전 명령을 반복합니다.

1. 웹 서버와 데이터베이스 서버가 서로 다른 호스트에 있는 경우 데이터베이스 서버 호스트에서 이 항목에서 설명한 작업을 수행한 다음 [원격 MySQL 데이터베이스 연결 설정](mysql-remote.md).

   비즈니스에 맞게 데이터베이스 인스턴스를 구성하는 것이 좋습니다. 데이터베이스를 구성할 때는 다음 사항에 유의하십시오.

   * 인덱서는 더 높아야 합니다. `tmp_table_size` 및 `max_heap_table_size` 값(예: 64M) 를 구성하는 경우 `batch_size` 매개 변수를 사용하면 테이블 크기 설정과 함께 이 값을 조정하여 인덱서 성능을 향상시킬 수 있습니다. 다음을 참조하십시오. [최적화 안내서](../../../performance/configuration.md) 추가 정보.

   * 최적의 성능을 위해 모든 MySQL 및 Adobe Commerce 또는 Magento Open Source 인덱스 테이블을 메모리에 유지할 수 있는지 확인합니다(예: 구성). `innodb_buffer_pool_size`).

   * MariaDB 10.4에 대한 리인덱싱은 다른 MariaDB 또는 MySQL 버전에 비해 시간이 더 걸립니다. 다음을 참조하십시오 [구성 모범 사례](../../../performance/configuration.md#indexers).

1. MySQL용 `TIMESTAMP` 응용 프로그램의 선언적 스키마 아키텍처인 시스템 변수에 필요한 환경 설정 및 컴포지션을 따르는 필드 `explicit_defaults_for_timestamp` 은(는) 로 설정되어야 합니다. `on`.

   참조:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [마리아DB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   이 설정을 활성화하지 않으면, `bin/magento setup:db:status` 항상 다음 보고서 포함 `Declarative Schema is not up to date`.

>[!NOTE]
>
>다음 `explicit_defaults_for_timestamp` 설정이 더 이상 사용되지 않습니다. 이 설정은 향후 MySQL 릴리스에서 제거될 더 이상 사용되지 않는 타임스탬프 동작을 제어합니다. 이러한 비헤이비어가 제거되면 `explicit_defaults_for_timestamp` 설정도 제거됩니다.

>[!WARNING]
>
>클라우드 인프라 프로젝트의 Adobe Commerce의 경우 `explicit_defaults_for_timestamp` mySQL(MariaDB)에 대해 설정된 기본값은 _끔_.

{{$include /help/_includes/maria-db-config.md}}
