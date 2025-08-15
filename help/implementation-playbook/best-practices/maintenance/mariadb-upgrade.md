---
title: MariaDB에 대한 Adobe Commerce 업그레이드 사전 요구 사항
description: Adobe Commerce 데이터베이스를 준비하여 이전 버전에서 MariaDB를 업그레이드하는 방법에 대해 알아봅니다.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# MariaDB에 대한 업그레이드 사전 요구 사항

MariaDB를 사용하는 경우 클라우드 인프라에서 Adobe Commerce을 업그레이드하기 전에 데이터베이스 소프트웨어를 업그레이드해야 할 수도 있습니다. For example:

- Adobe Commerce 2.4.6(MariaDB 버전 10.5.1 이상)
- Adobe Commerce 2.3.5(MariaDB 버전 10.3 이하)

## Adobe Commerce 2.4.6

MariaDB 10.5.1부터 이전 임시 형식의 열은 `/* mariadb-5.3 */` 테이블의 `SHOW CREATE TABLE` 열뿐만 아니라 `SHOW COLUMNS`, `DESCRIBE`, `COLUMN_TYPE` 문의 출력에서도 `INFORMATION_SCHEMA.COLUMNS` 주석으로 표시됩니다. [MariaDB 설명서를 참조하십시오](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce은 MariaDB 주석으로 인해 날짜 열을 적절한 데이터 형식에 매핑할 수 없으므로 사용자 지정 코드에 예기치 않은 동작이 발생할 수 있습니다.

이전 버전에서 버전 10.6으로 MariaDB를 업그레이드할 때 예기치 않은 동작이 발생하지 않도록 Adobe에서는 열을 새 내부 형식으로 마이그레이션하는 것이 좋습니다.

### 기본 구성

MariaDB 10.1.2에서는 MySQL 5.6에서 새로운 임시 형식을 도입하였다. `mysql56_temporal_format` 시스템 변수를 사용하면 변경 테이블을 실행하거나 데이터베이스를 가져올 때 데이터베이스가 이전 날짜 형식을 새 날짜 형식으로 자동 변환할 수 있습니다. 클라우드 인프라의 Adobe Commerce에서 `mysql56_temporal_format`에 대한 기본 구성이 항상 활성화되어 있습니다.

### 날짜 열 마이그레이션

다음 쿼리는 MariaDB를 10.5.1 이상으로 업그레이드한 후 마이그레이션해야 하는 영향을 받는 테이블과 열을 보여 줍니다.

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

열을 새 내부 날짜 형식으로 마이그레이션하려면 데이터베이스를 다시 가져오거나 열 정의가 동일한 식별된 열에서 를 변경해야 합니다. 다음 쿼리는 필요한 변경 쿼리를 생성합니다.

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>예기치 않은 동작이 발생하지 않도록 새 코드를 배포하려면 열을 새 내부 날짜 형식 _이전_(으)로 마이그레이션해야 합니다.

## Adobe Commerce 2.3.5

클라우드 인프라의 MariaDB 서비스를 버전 10.0 또는 10.2에서 버전 10.3, 10.4 또는 10.5로 업그레이드합니다. MariaDB 버전 10.3 이상에서는 데이터베이스가 동적 테이블 행 형식을 사용해야 하며 Adobe Commerce에서는 테이블에 InnoDB 스토리지 엔진을 사용해야 합니다. 이 문서에서는 이러한 MariaDB 요구 사항을 준수하도록 데이터베이스를 업데이트하는 방법에 대해 설명합니다.

데이터베이스를 준비한 후에는 Adobe Commerce 업그레이드 프로세스를 진행하기 전에 클라우드 인프라에서 MariaDB 서비스 버전을 업데이트하기 위한 Adobe Commerce 지원 티켓을 제출하십시오.

### 업그레이드를 위해 데이터베이스 준비

Adobe Commerce 지원 팀이 업그레이드 프로세스를 시작하기 전에 데이터베이스 테이블을 변환하여 데이터베이스를 준비합니다.

- 행 형식을 `COMPACT`에서 `DYNAMIC`(으)로 변환
- 저장소 엔진을 `MyISAM`에서 `InnoDB`(으)로 변경

변환을 계획하고 예약할 때 다음 고려 사항을 염두에 두십시오.

- `COMPACT`에서 `DYNAMIC` 테이블로 변환하는 데 큰 데이터베이스가 있으면 몇 시간이 걸릴 수 있습니다.

- 데이터 손상을 방지하려면 라이브 사이트에서 변환 작업을 완료하지 마십시오.

- 사이트의 낮은 트래픽 기간 동안 전환 작업을 완료합니다.

- 데이터베이스 테이블을 변환하는 명령을 실행하기 전에 사이트를 [유지 관리 모드](../../../installation/tutorials/maintenance-mode.md)(으)로 전환하십시오.

#### 데이터베이스 테이블 행 형식 변환

클러스터의 한 노드에서 테이블을 변환할 수 있습니다. 변경 사항이 다른 서비스 노드에 자동으로 복제됩니다.

1. 클라우드 인프라 환경의 Adobe Commerce에서 SSH를 사용하여 노드 1에 연결합니다.

1. MariaDB에 로그인.

1. 콤팩트에서 동적 형식으로 변환할 테이블을 식별합니다.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 전환 작업을 예약할 수 있도록 테이블 크기를 결정합니다.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   큰 표는 변환하는 데 시간이 더 오래 걸립니다. 테이블을 검토하고 우선 순위 및 테이블 크기별로 변환 작업을 일괄 처리하여 필요한 유지 관리 기간을 계획합니다.

1. 모든 표를 한 번에 하나씩 동적 형식으로 변환합니다.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### 데이터베이스 테이블 저장소 형식 변환

클러스터의 한 노드에서 테이블을 변환할 수 있습니다. 변경 사항이 다른 서비스 노드에 자동으로 복제됩니다.

저장소 형식을 변환하는 프로세스는 Adobe Commerce Starter 및 Adobe Commerce Pro 프로젝트에 따라 다릅니다.

- Starter 아키텍처의 경우 MySQL `ALTER` 명령을 사용하여 형식을 변환합니다.
- Pro 아키텍처에서 MySQL `CREATE` 및 `SELECT` 명령을 사용하여 `InnoDB` 저장소가 있는 데이터베이스 테이블을 만들고 기존 테이블의 데이터를 새 테이블로 복사합니다. 이 방법을 사용하면 변경 사항이 클러스터의 모든 노드에 복제됩니다.

**Adobe Commerce Pro 프로젝트에 대한 테이블 저장소 형식 변환**

1. `MyISAM` 저장소를 사용하는 테이블을 식별합니다.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 모든 표를 한 번에 하나씩 `InnoDB` 저장소 형식으로 변환합니다.

   - 이름 충돌을 방지하기 위해 기존 테이블의 이름을 변경합니다.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - 기존 테이블의 데이터를 사용하여 `InnoDB` 저장소를 사용하는 테이블을 만듭니다.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - 새 테이블에 모든 필수 데이터가 있는지 확인합니다.

   - 이름을 변경한 원래 테이블을 삭제합니다.


**Adobe Commerce 스타터 프로젝트에 대한 테이블 저장소 형식 변환**

1. `MyISAM` 저장소를 사용하는 테이블을 식별합니다.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. `MyISAM` 저장소를 사용하는 테이블을 `InnoDB` 저장소로 변환합니다.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### 데이터베이스 변환 확인

MariaDB 버전 10.3, 10.4 또는 10.6으로 업그레이드하기 하루 전에 모든 테이블에 올바른 행 형식 및 스토리지 엔진이 있는지 확인합니다. 변환을 완료한 후 코드 배포를 수행하면 일부 테이블이 원래 구성으로 되돌아갈 수 있으므로 확인이 필요합니다.

1. 데이터베이스에 로그인합니다.

1. `COMPACT` 행 형식이 아직 있는 테이블을 확인합니다.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 여전히 `MyISAM` 저장소 형식을 사용하는 테이블을 확인합니다.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 테이블이 되돌려진 경우 단계를 반복하여 테이블 행 형식 및 저장 영역 엔진을 변경합니다.

### 저장소 엔진 변경

[MyISAM 테이블을 InnoDB로 변환](../planning/database-on-cloud.md)을 참조하세요.
