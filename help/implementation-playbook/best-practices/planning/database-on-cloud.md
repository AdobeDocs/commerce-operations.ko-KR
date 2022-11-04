---
title: 클라우드 배포를 위한 데이터베이스 구성 우수 사례
description: 클라우드 인프라에서 Adobe Commerce을 배포할 때 성능을 개선하기 위해 데이터베이스 및 애플리케이션 설정을 구성하는 방법을 알아봅니다.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# 데이터베이스 구성에 대한 우수 사례

클라우드 인프라에서 Adobe Commerce을 배포할 때 데이터베이스 성능을 향상시키고 데이터베이스와 효율적으로 작업하는 모범 사례에 대해 알아봅니다.

## 영향을 받는 제품

Adobe Commerce on cloud 인프라

## 모든 MyISAM 테이블을 InnoDB로 변환

InnoDB 데이터베이스 엔진을 사용하는 것이 좋습니다. 기본 Adobe Commerce 설치에서는 데이터베이스의 모든 테이블이 InnoDB 엔진을 사용하여 저장됩니다. 그러나 일부 타사 모듈(확장)에서는 MyISAM 형식으로 표를 도입할 수 있습니다. 타사 모듈을 설치한 후 데이터베이스를 확인하여 `myisam` 형식으로 변환한 다음 `innodb` 형식 지정

### 모듈에 MyISAM 테이블이 포함되어 있는지 확인합니다.

설치하기 전에 타사 모듈 코드를 분석하여 MyISAM 테이블을 사용하는지 확인할 수 있습니다.

확장을 이미 설치한 경우 다음 쿼리를 실행하여 데이터베이스에 MyISAM 테이블이 있는지 확인합니다.

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 저장소 엔진을 InnoDB로 변경합니다.

에서 `db_schema.xml` 테이블을 선언하는 파일에서 `engine` 해당 속성에 대한 속성 값 `table` 노드 끝 `innodb`. 자세한 내용은 [선언적 스키마 > 테이블 노드 구성](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 개발자 설명서에서 를 참조하십시오.

선언적 구성표는 클라우드 인프라 버전 2.3의 Adobe Commerce에서 도입되었습니다.

## 네이티브 MySQL 검색에 대한 권장 검색 엔진 구성

Adobe에서는 Adobe Commerce 애플리케이션에 대해 타사 검색 도구를 구성할 계획이라도 클라우드 인프라 프로젝트에서 Adobe Commerce에 대한 Elasticsearch 또는 OpenSearch를 항상 설정할 것을 권장합니다. 이 구성에서는 타사 검색 도구가 실패할 경우 대체 옵션을 제공합니다.

사용하는 검색 엔진은 설치된 Adobe Commerce on cloud 버전에 따라 다릅니다.

- Adobe Commerce 2.4.4 이상 버전의 경우, OpenSearch 서비스를 사용하여 기본 MySQL 검색을 사용하십시오.

- 이전 Adobe Commerce 버전의 경우 Elasticsearch을 사용하십시오.

현재 사용 중인 검색 엔진을 확인하려면 다음 명령을 실행하십시오.

```bash
./bin/magento config:show catalog/search/engine
```

구성 지침은 클라우드에 대한 Adobe Commerce 개발자 안내서 를 참조하십시오.

- [OpenSearch 서비스 설정](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Elasticsearch 서비스 설정](https://devdocs.magento.com/cloud/project/services-elastic.html)

## 사용자 지정 트리거 방지

가능하면 사용자 지정 트리거를 사용하지 마십시오.

트리거는 변경 사항을 감사 테이블에 기록하는 데 사용됩니다. Adobe은 다음과 같은 이유로 트리거 기능을 사용하는 대신 애플리케이션을 감사 테이블에 직접 쓰도록 구성할 것을 권장합니다.

- 트리거는 코드로 해석되며 MySQL은 트리거를 미리 컴파일하지 않습니다. 쿼리의 트랜잭션 공간에 후킹하는 경우 테이블로 수행된 각 쿼리에 대한 파서와 인터프리터에 오버헤드를 추가합니다.
- 트리거는 원래 쿼리와 동일한 트랜잭션 공간을 공유하며, 이러한 쿼리는 테이블의 잠금을 위해 경합하는 반면 트리거는 다른 테이블의 잠금에 대해 독립적으로 경쟁합니다.

사용자 지정 트리거를 사용하는 대체 요소에 대해 알아보려면 [MySQL 트리거를 효과적으로 사용](mysql-triggers-usage.md) 지원 기술 자료에서

## 업그레이드 [!DNL ECE-Tools] 버전 2002.0.21 이상으로 {#ece-tools-version}

cron deadlock과 관련된 잠재적인 문제를 방지하려면 ECE-Tools를 버전 2002.0.21 이상으로 업그레이드하십시오. 자세한 내용은 [업데이트 `ece-tools` 버전](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 개발자 설명서에서 를 참조하십시오.

## 인덱서 모드를 안전하게 전환합니다.

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

절체 인덱서 생성 [!DNL data definition language] 데이터베이스 잠금이 발생할 수 있는 트리거를 생성하는 (DDL) 문 구성을 변경하기 전에 웹 사이트를 유지 관리 모드로 전환하고 크론 작업을 비활성화하여 이 문제를 방지할 수 있습니다.
자세한 내용은 [인덱서 구성](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) 에서 *Adobe Commerce 구성 안내서*.

## 프로덕션에서 DDL 문 실행 안 함

테이블 수정 및 생성과 같은 충돌을 방지하기 위해 운영 환경에서 DDL 문을 실행하지 마십시오. 다음 `setup:upgrade` 프로세스는 예외입니다.

DDL 문을 실행해야 하는 경우 웹 사이트를 유지 관리 모드로 설정하고 cron을 비활성화합니다(이전 섹션에서 인덱스를 안전하게 전환하는 지침 참조).

## 주문 아카이빙 사용

주문 데이터가 증가함에 따라 영업 테이블에 필요한 공간을 줄이려면 관리자로부터 주문 아카이빙을 활성화합니다. 아카이빙을 통해 MySQL 디스크 공간이 절약되고 체크아웃 성능이 향상됩니다.

자세한 내용은 [보관 사용](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) ( Adobe Commerce Merchant 설명서).

## 추가 정보

- [InnoDB와 MYISAM의 주요 차이점은 무엇입니까?](http://www.expertphp.in/article/what-are-the-main-differences-between-innodb-and-myisam)
- [Adobe Commerce 2.3.5 MariaDB용 업그레이드 사전 요구 사항](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [데이터베이스 성능 문제를 해결하기 위한 우수 사례](../maintenance/resolve-database-performance-issues.md)
