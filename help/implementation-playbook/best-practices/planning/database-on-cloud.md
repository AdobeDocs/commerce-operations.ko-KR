---
title: 클라우드 배포를 위한 데이터베이스 구성 모범 사례
description: 클라우드 인프라에 Adobe Commerce을 배포할 때 성능을 개선하기 위해 데이터베이스 및 애플리케이션 설정을 구성하는 방법에 대해 알아봅니다.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 데이터베이스 구성 모범 사례

클라우드 인프라에 Adobe Commerce을 배포할 때 데이터베이스 성능을 향상시키고 데이터베이스를 효율적으로 작업하는 모범 사례에 대해 알아봅니다.

## 영향을 받는 제품

클라우드 인프라의 Adobe Commerce

## 모든 MyISAM 테이블을 InnoDB로 변환

Adobe에서는 InnoDB 데이터베이스 엔진을 사용하는 것이 좋습니다. 기본 Adobe Commerce 설치에서 데이터베이스의 모든 테이블은 InnoDB 엔진을 사용하여 저장됩니다. 그러나 일부 타사 모듈(확장)에서는 MyISAM 형식으로 표를 도입할 수 있습니다. 타사 모듈을 설치한 후 데이터베이스를 확인하여 `myisam` 형식의 테이블을 식별하고 `innodb` 형식으로 변환하십시오.

### 모듈에 MyISAM 테이블이 포함되어 있는지 확인

설치하기 전에 타사 모듈 코드를 분석하여 MyISAM 테이블을 사용하는지 확인할 수 있습니다.

이미 확장을 설치한 경우 다음 쿼리를 실행하여 데이터베이스에 MyISAM 테이블이 있는지 확인합니다.

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 스토리지 엔진을 InnoDB로 변경

테이블을 선언하는 `db_schema.xml` 파일에서 해당 `engine` 노드의 `table` 특성 값을 `innodb`(으)로 설정합니다. 참조용으로 개발자 설명서에서 [선언적 스키마 구성 > 테이블 노드](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/)를 참조하십시오.

선언적 스키마는 Adobe Commerce on cloud infrastructure 버전 2.3에서 도입되었습니다.

## 기본 MySQL 검색에 대한 권장 검색 엔진 구성

Adobe에서는 Adobe Commerce 애플리케이션에 대한 서드파티 검색 도구를 구성할 계획이라도 항상 Adobe Commerce on cloud infrastructure 프로젝트에 대해 Elasticsearch 또는 OpenSearch를 설정할 것을 권장합니다. 이 구성은 서드파티 검색 도구가 실패할 경우 대체 옵션을 제공합니다.

사용하는 검색 엔진은 설치된 Adobe Commerce on cloud 버전에 따라 다릅니다.

- Adobe Commerce 2.4.4 이상의 경우 기본 MySQL 검색용 OpenSearch 서비스를 사용합니다.

- 이전 Adobe Commerce 버전의 경우 Elasticsearch을 사용합니다.

현재 사용 중인 검색 엔진을 확인하려면 다음 명령을 실행합니다.

```bash
./bin/magento config:show catalog/search/engine
```

구성 지침은 Adobe Commerce on cloud 개발자 안내서 를 참조하십시오.

- [OpenSearch 서비스 설정](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [Elasticsearch 서비스 설정](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## 사용자 지정 트리거 방지

가능한 경우 사용자 지정 트리거를 사용하지 마십시오.

트리거는 변경 사항을 감사 테이블에 기록하는 데 사용됩니다. Adobe에서는 다음과 같은 이유로 트리거 기능을 사용하는 대신 감사 테이블에 직접 작성하도록 애플리케이션을 구성할 것을 권장합니다.

- 트리거는 코드로 해석되며 MySQL은 트리거를 미리 컴파일하지 않습니다. 쿼리의 트랜잭션 공간에 후킹하면 테이블과 함께 수행되는 각 쿼리에 대한 파서 및 인터프리터에 오버헤드가 추가됩니다.
- 트리거는 원래 쿼리와 동일한 트랜잭션 공간을 공유하고 해당 쿼리가 테이블에서 잠금에 대해 경쟁하는 동안 트리거는 다른 테이블에서 잠금에 대해 독립적으로 경쟁합니다.

사용자 지정 트리거를 사용하는 방법에 대한 대안은 [MySQL 트리거](mysql-configuration.md#triggers)를 참조하세요.

## [!DNL ECE-Tools]을(를) 버전 2002.0.21 이상으로 업그레이드 {#ece-tools-version}

cron 교착 상태와 관련된 잠재적 문제를 방지하려면 ECE-Tools를 버전 2002.0.21 이상으로 업그레이드하십시오. 자세한 내용은 개발자 설명서에서 [`ece-tools` 버전 업데이트](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)를 참조하십시오.

## 인덱서 모드를 안전하게 전환

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

인덱서를 전환하면 [!DNL data definition language]&#x200B;(DDL) 문이 생성되어 트리거가 발생하여 데이터베이스가 잠길 수 있습니다. 구성을 변경하기 전에 웹 사이트를 유지 관리 모드로 전환하고 cron 작업을 비활성화하여 이 문제를 방지할 수 있습니다.
자세한 내용은 [Adobe Commerce 구성 가이드](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=ko#configure-indexers-1)에서 *인덱서 구성*&#x200B;을 참조하십시오.

## 프로덕션에서 DDL 문 실행 안 함

충돌(예: 테이블 수정 및 생성)을 방지하기 위해 프로덕션 환경에서 DDL 문을 실행하지 마십시오. `setup:upgrade` 프로세스는 예외입니다.

DDL 문을 실행해야 하는 경우 웹 사이트를 유지 관리 모드로 전환하고 cron 을 비활성화합니다(이전 섹션에서 인덱스를 안전하게 전환하기 위한 지침 참조).

## 주문 보관 사용

관리자의 주문 보관을 사용하면 주문 데이터가 증가할 때 판매 테이블에 필요한 공간을 줄일 수 있습니다. 보관을 사용하면 MySQL 디스크 공간이 절약되고 체크아웃 성능이 향상됩니다.

Adobe Commerce 판매자 설명서의 [보관 사용](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html?lang=ko)을 참조하십시오.

## 추가 정보

- [MySQL 저장소 엔진](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5 MariaDB 업그레이드 사전 요구 사항](../maintenance/mariadb-upgrade.md)
- [데이터베이스 성능 문제 해결 모범 사례](../maintenance/resolve-database-performance-issues.md)
