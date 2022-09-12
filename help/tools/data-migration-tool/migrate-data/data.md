---
title: 데이터 마이그레이션
description: 를 사용하여 Magento 1에서 Magento 2으로 데이터를 마이그레이션하는 방법을 배웁니다. [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# 데이터 마이그레이션

시작하기 전에 다음 단계를 수행하여 준비하십시오.

1. 다음 방법으로 애플리케이션 서버에 로그인합니다. [파일 시스템 소유자](../../../installation/prerequisites/file-system/overview.md).
1. 응용 프로그램 설치 디렉토리로 변경하거나 시스템에 추가되었는지 확인합니다 `PATH`.

자세한 내용은 [첫 단계](overview.md#first-steps) 섹션을 참조하십시오.

## 데이터 마이그레이션 명령 실행

데이터 마이그레이션을 시작하려면 다음을 실행하십시오.

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

위치:

* `[-a|--auto]` 무결성 검사 오류가 발생할 때 마이그레이션이 중지되지 않도록 하는 선택적 인수입니다.

* `[-r|--reset]` 는 처음부터 마이그레이션을 시작하는 선택적 인수입니다. 마이그레이션을 테스트하는 데 이 인수를 사용할 수 있습니다.

* `{<path to config.xml>}` 의 절대 파일 시스템 경로입니다. `config.xml`; 이 인수는 필수입니다.

이 단계에서 [!DNL Data Migration Tool] Magento 1 데이터베이스에서 마이그레이션 테이블에 대해 추가 테이블 및 트리거를 만듭니다. 이 변수는 [증분/델타](delta.md) 마이그레이션 단계입니다. 추가 테이블에는 최종 마이그레이션 실행 후 변경된 레코드에 대한 정보가 포함되어 있습니다. 데이터베이스 트리거는 이러한 추가 테이블을 채우는 데 사용되므로 특정 테이블에서 새 작업을 수행하는 경우(레코드가 추가/수정/제거됨) 이러한 데이터베이스 트리거가 이 작업에 대한 정보를 추가 테이블에 저장합니다. 델타 마이그레이션 프로세스를 실행하면 [!DNL Data Migration Tool] 이러한 테이블에서 처리되지 않은 레코드를 확인하고 필요한 컨텐츠를 Magento 2 데이터베이스로 마이그레이션합니다.

새로운 각 테이블에는 다음이 포함됩니다.

* `m2_cl` 접두사
* `INSERT`, `UPDATE`, `DELETE` 이벤트 트리거.

예를 들어 `sales_flat_order` a [!DNL Data Migration Tool] 만들기:

* `m2_cl_sales_flat_order` 표:

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` 트리거:

   ```sql
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
     END
   ;;
   ```

>[!NOTE]
>
>다음 [!DNL Data Migration Tool] 실행 시 현재 진행 상황을 저장합니다. 오류나 사용자 개입이 실행을 중지하면 마지막으로 알려진 양호한 상태에서 진행 상태가 다시 시작됩니다. 강제 실행 [!DNL Data Migration Tool] 처음부터 실행하려면 `--reset` 변합니다. 이 경우 이전에 마이그레이션한 데이터가 복제되지 않도록 Magento 2 데이터베이스 덤프를 복원하는 것이 좋습니다.


## 가능한 일관성 오류

실행하는 동안 [!DNL Data Migration Tool] Magento 1과 Magento 2 데이터베이스 간의 불일치를 보고하고 다음과 같은 메시지를 표시할 수 있습니다.

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

자세한 내용은 [문제 해결](https://support.magento.com/hc/en-us/articles/360033020451) 자세한 내용 및 권장 사항에 대해서는 이 안내서의 섹션을 참조하십시오.

## 다음 마이그레이션 단계

[변경 사항 마이그레이션](delta.md)
