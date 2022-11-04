---
title: Adobe Commerce 2.3.5 MariaDB용 업그레이드 사전 요구 사항
description: Adobe Commerce 2.3.5에서 업그레이드하도록 Adobe Commerce 데이터베이스를 준비하는 방법을 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Adobe Commerce 2.3.5 업그레이드 사전 요구 사항

이 문서에서는 버전 2.3.4 이하에서 Adobe Commerce 2.3.5로 업그레이드할 때 데이터베이스를 준비하는 방법에 대해 설명합니다.

이 업그레이드를 수행하려면 지원 팀이 Adobe Commerce에 대한 요구 사항을 충족하도록 클라우드 인프라의 MariaDB를 MariaDB 10.0에서 10.2로 업그레이드해야 합니다. Adobe Commerce 버전 2.3.5 이상

## 영향을 받는 제품 및 버전

Adobe Commerce 버전 2.3.4 이하 및 MariaDB 버전 10.0 이전 버전을 사용하는 Adobe Commerce on cloud infrastructure

## 업그레이드를 위한 데이터베이스 준비

Adobe Commerce 지원 팀에서 업그레이드 프로세스를 시작하기 전에 `COMPACT` to `DYNAMIC`. 또한 저장소 엔진 유형을 `MyISAM` to `InnoDB`.

계획을 생성하고 데이터베이스를 변환하도록 예약할 때 다음 지침을 염두에 두십시오.

- 변환 위치 `COMPACT` to `DYNAMIC` 큰 데이터베이스를 사용하면 표에 몇 시간이 걸릴 수 있습니다.

- 데이터 손상을 방지하기 위해 사이트가 라이브 상태일 때는 전환을 수행하지 마십시오.

- 사이트에서 낮은 트래픽 기간 동안 전환 작업을 완료합니다.

- 사이트로 전환 [유지 모드](../../../installation/tutorials/maintenance-mode.md) 실행 전 `ALTER` 명령.

### 데이터베이스 테이블 변환

클러스터의 한 노드에서 테이블을 변환할 수 있습니다. 변경 사항이 클러스터의 다른 코어 노드에 복제됩니다.

1. 클라우드 인프라 환경의 Adobe Commerce에서 SSH를 사용하여 노드 1에 연결합니다.

1. MariaDB에 로그인합니다.

1. 표 형식을 변환합니다.

   - 콤팩트에서 다이내믹 형식으로 변환할 테이블을 식별합니다.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - 변환 작업을 예약할 수 있도록 테이블 크기를 결정합니다.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      큰 표는 변환하는 데 시간이 더 오래 걸립니다. 필요한 유지 관리 창의 시간을 계획하기 위해, 어느 순서로 변환할 테이블 배치를 유지 관리 모드로 또는 나가는 경우 그에 따라 계획을 세워야 합니다

   - 모든 표를 한 번에 하나씩 동적 형식으로 변환합니다.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. 테이블 저장소 엔진을 업데이트합니다.

   - 사용할 테이블 식별 `MyISAM` 저장.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 사용할 표 변환 `MyISAM` 저장소 대상 `InnoDB` 저장.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. 전환을 확인합니다.

   변환을 완료한 후 코드 배포를 수행하면 일부 테이블이 원래 구성으로 되돌려질 수 있으므로 이 단계가 필요합니다.

   - MariaDB 버전 10.2로 업그레이드하기 하루 전에 데이터베이스에 로그인하여 쿼리를 실행하여 형식 및 저장소 엔진을 확인합니다.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 테이블이 복귀된 경우 테이블 형식 및 저장소 엔진을 변경하는 단계를 반복합니다.

## 추가 정보

[클라우드 인프라 기반의 Adobe Commerce을 위한 데이터베이스 우수 사례](../planning/database-on-cloud.md)
