---
title: 데이터베이스 성능 문제 해결 모범 사례
description: 클라우드 인프라에 배포된 Adobe Commerce 사이트에서 성능을 저하시키는 데이터베이스 문제를 해결하는 방법에 대해 알아봅니다.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# 데이터베이스 성능 문제 해결 모범 사례

이 문서에서는 클라우드 인프라 사이트에서 Adobe Commerce의 데이터베이스 성능에 부정적인 영향을 주는 데이터베이스 문제를 해결하는 방법에 대해 설명합니다.

## 영향을 받는 버전

클라우드 인프라 기반 Adobe Systems Commerce

## 장기 실행 쿼리 식별 및 해결Identify and resolve long running queries

느리게 실행되는 MySQL 쿼리가 있는지 확인합니다. 클라우드 인프라 기반 Adobe Systems 상거래 계획 및 도구 가용성에 따라 다음을 수행할 수 있습니다.

### MySQL로 데이터베이스 쿼리 분석

MySQL을 사용하여 클라우드 인프라 기반 Adobe Systems Commerce 프로젝트에서 장기 실행 쿼리를 식별하고 해결할 수 있습니다.

1. [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 문을 실행합니다.
1. 오래 실행되는 쿼리가 표시되면 각 쿼리에 대해 [MySQL `EXPLAIN` 및 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/)을(를) 실행하여 쿼리가 오래 실행되는 이유를 확인하세요.
1. 발견된 문제를 기반으로, 쿼리를 더 빨리 실행할 수 있도록 수정하는 단계를 수행하십시오.

### Percona Toolkit을 사용하여 쿼리 분석(Pro 아키텍처에만 해당)

Adobe Commerce 프로젝트가 Pro 아키텍처에 배포된 경우 Percona Toolkit을 사용하여 쿼리를 분석할 수 있습니다.

1. MySQL 느린 쿼리 로그에 대해 `pt-query-digest --type=slowlog` 명령을 실행합니다.
   * 느린 쿼리 로그의 위치를 찾으려면 개발자 설명서의 (https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs)를 참조하세요 **[!UICONTROL Log locations > Service Logs]**.
   * [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 문서를 참조하십시오.
1. 발견된 문제에 따라 쿼리가 더 빠르게 실행되도록 쿼리를 수정하는 단계를 수행합니다.

## 모든 테이블에 기본 키가 있는지 확인

기본 키를 정의하는 것은 좋은 데이터베이스 및 테이블 디자인을 위한 요구 사항입니다. 기본 키는 모든 테이블에서 단일 행을 고유하게 식별하는 방법을 제공합니다.

기본 키가 없는 테이블이 있는 경우 Adobe Commerce의 기본 데이터베이스 엔진(InnoDB)은 첫 번째 고유하고 null이 아닌 키를 기본 키로 사용합니다. 고유 키를 사용할 수 없는 경우 InnoDB는 숨겨진 기본 키(6바이트)를 만듭니다. 암시적으로 정의된 기본 키의 문제는 기본 키를 제어할 수 없다는 것입니다. 또한 기본 키가 없는 모든 테이블에 대해 암시적 값이 전역적으로 할당됩니다. 이러한 테이블에서 동시 쓰기를 수행하는 경우 이 구성으로 인해 경합 문제가 발생할 수 있습니다. 이 경우 전역 숨겨진 기본 키 인덱스 증가도 공유되므로 성능 문제가 발생할 수 있습니다.

기본 키가 없는 테이블에 대한 기본 키를 정의하여 이러한 문제를 방지합니다.

### 기본 키 없이 테이블 식별 및 업데이트

1. 다음 SQL 쿼리를 사용하여 기본 키가 없는 테이블을 식별합니다.

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 기본 키가 누락된 테이블의 경우 선언적 스키마를 `db_schema.xml` 다음과 유사한 노드 로 업데이트하여 기본 키를 추가합니다.

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   노드 추가 시 및 `column name` 변수를 사용자 지정 사용자 지정 값으로 바꿉니다`referenceID`.

자세한 내용은 개발자 설명서에서 선언적 스키마[&#128279;](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 구성을 참조하세요.

## 중복 인덱스 식별 및 제거

데이터베이스에서 중복 인덱스를 식별하고 제거합니다.

### 중복 인덱스 확인

Pro 또는 Starter 클라우드 아키텍처에서 중복 인덱스를 확인하려면 다음 SQL 쿼리를 실행합니다.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

이 쿼리는 열 이름과 중복 인덱스의 이름을 반환합니다.

Pro 아키텍처 판매자는 Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 명령을 사용하여 검사를 실행할 수도 있습니다.

### 중복 인덱스 제거

SQL [DROP INDEX 문을](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 사용하여 중복 인덱스를 제거합니다.

```SQL
DROP INDEX
```

## 추가 정보

[클라우드 배포에 대한 데이터베이스 구성 우수 사례](../planning/database-on-cloud.md)
