---
title: 데이터베이스 성능 문제를 해결하기 위한 우수 사례
description: 클라우드 인프라에 배포된 Adobe Commerce 사이트의 성능이 느린 데이터베이스 문제를 해결하는 방법을 알아봅니다.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---


<!--Consider moving this topic to the Maintenance section-->

# 데이터베이스 성능 문제를 해결하기 위한 우수 사례

이 문서에서는 클라우드 인프라 사이트에서 Adobe Commerce의 데이터베이스 성능에 부정적인 영향을 주는 데이터베이스 문제를 해결하는 방법을 설명합니다.

## 영향을 받는 버전

Adobe Commerce on cloud 인프라

## 장기 실행 쿼리 식별 및 해결

MySQL 쿼리를 느리게 실행할지 여부를 결정합니다. 클라우드 인프라 계획과 도구 가용성에 따라 Adobe Commerce에서 다음을 수행할 수 있습니다.

### MySQL을 사용하여 데이터베이스 쿼리 분석

MySQL을 사용하여 클라우드 인프라 프로젝트에서 Adobe Commerce에서 실행되는 긴 쿼리를 식별하고 해결할 수 있습니다.

1. 를 실행합니다. [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 문.
1. 긴 실행 쿼리가 표시되면 를 실행합니다 [MySQL `EXPLAIN` 및 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 각 URL에 대해 쿼리를 오랫동안 실행하는 방법을 알아봅니다.
1. 발견된 문제를 바탕으로 쿼리를 보다 빠르게 실행할 수 있도록 수정하는 단계를 수행하십시오.

### Percona Toolkit을 사용하여 쿼리를 분석합니다(Pro 아키텍처만 해당).

Adobe Commerce 프로젝트가 Pro 아키텍처에 배포된 경우 Percona Toolkit을 사용하여 쿼리를 분석할 수 있습니다.

1. 를 실행합니다. `pt-query-digest --type=slowlog` MySQL 느린 쿼리 로그에 대한 명령입니다.
   * 느린 쿼리 로그 위치를 찾으려면 를 참조하십시오 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) 을 개발자 설명서에서 참조하십시오.
   * 자세한 내용은 [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 설명서.
1. 발견된 문제를 바탕으로 쿼리를 보다 빠르게 실행할 수 있도록 수정하는 단계를 수행하십시오.

## 모든 테이블에 기본 키가 있는지 확인합니다.

기본 키를 정의하는 것은 좋은 데이터베이스 및 테이블 디자인을 위한 요구 사항입니다. 기본 키는 테이블에서 단일 행을 고유하게 식별하는 방법을 제공합니다.

기본 키가 없는 테이블이 있는 경우, Adobe Commerce(InnoDB)의 기본 데이터베이스 엔진은 null이 아닌 첫 번째 고유 키를 기본 키로 사용합니다. 사용 가능한 고유 키가 없으면 숨겨진 기본 키(6바이트)가 만들어집니다. 암묵적으로 정의된 기본 키의 문제는 해당 키를 제어할 수 없다는 것입니다. 또한 기본 키가 없는 모든 테이블에 대해 암시적 값이 전체적으로 할당됩니다. 이러한 테이블에서 동시에 쓰기를 수행할 경우 이 구성으로 인해 충돌 문제가 발생할 수 있습니다. 이 경우 테이블이 전역 숨겨진 기본 키 인덱스 증가도 공유하므로 성능 문제가 발생할 수 있습니다.

없는 테이블에 대한 기본 키를 정의하여 이러한 문제를 방지합니다.

### 기본 키 없이 테이블 식별 및 업데이트

1. 다음 SQL 쿼리를 사용하여 기본 키 없이 테이블을 식별합니다.

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 기본 키가 없는 테이블의 경우 `db_schema.xml` (선언적 스키마)

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   노드를 추가할 때 `referenceID` 및 `column name` 변수를 사용자 지정 값으로 채우는 방법을 설명합니다.

자세한 내용은 [선언적 스키마 구성](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 개발자 설명서에서 를 참조하십시오.

## 중복 인덱스 식별 및 제거

데이터베이스의 중복 인덱스를 식별하고 제거합니다.

### 중복 인덱스 확인

Pro 또는 Starter 클라우드 아키텍처에서 중복 인덱스를 확인하려면 다음 SQL 쿼리를 실행합니다.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

쿼리는 중복 인덱스의 열 이름 및 이름을 반환합니다.

Pro Architecture 상인도 Percona Toolkit을 사용하여 검사를 실행할 수 있습니다  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 명령.

### 중복 인덱스 제거

SQL 사용 [DROP INDEX 문](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 중복 인덱스를 제거하려면

```SQL
DROP INDEX
```

## 추가 정보

[클라우드 배포를 위한 데이터베이스 구성 우수 사례](../planning/database-on-cloud.md)

