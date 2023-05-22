---
title: 수동으로 마스터 데이터베이스 구성
description: 분할 데이터베이스 솔루션을 수동으로 구성하는 방법에 대한 지침을 참조하십시오.
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# 수동으로 마스터 데이터베이스 구성

{{ee-only}}

{{deprecate-split-db}}

Commerce 응용 프로그램이 이미 프로덕션에 있거나 사용자 지정 코드 또는 구성 요소를 이미 설치한 경우 분할 데이터베이스를 수동으로 구성해야 할 수 있습니다. 계속하기 전에 Adobe Commerce 지원 센터에 문의하여 이 작업이 필요한지 확인하십시오.

데이터베이스 수동 분할에는 다음이 포함됩니다.

- OMS(체크아웃 및 주문 관리 시스템) 데이터베이스 만들기
- 다음과 같은 일련의 SQL 스크립트를 실행합니다.

   - 외래 키 삭제
   - 영업 및 견적 데이터베이스 테이블 백업
   - 주 데이터베이스에서 판매 및 견적 데이터베이스로 테이블 이동

>[!WARNING]
>
>사용자 정의 코드가 Sales 및 Quote 데이터베이스의 테이블과 함께 JOIN을 사용하는 경우 _할 수 없음_ 분할 데이터베이스를 사용합니다. 사용자 지정 코드 또는 확장 작성자에게 문의하여 코드에서 JOIN을 사용하지 않는지 확인하십시오.

이 항목에서는 다음 이름 지정 규칙을 사용합니다.

- 기본 데이터베이스 이름은 입니다. `magento` 사용자 이름과 암호는 둘 다 `magento`
- 견적 데이터베이스 이름은 입니다. `magento_quote` 사용자 이름과 암호는 둘 다 `magento_quote`

   Quote 데이터베이스도 _체크아웃_ 데이터베이스.

- 판매 데이터베이스 이름은 입니다. `magento_sales` 사용자 이름과 암호는 둘 다 `magento_sales`

   영업 데이터베이스를 OMS 데이터베이스라고도 합니다.

>[!INFO]
>
>이 안내서에서는 세 데이터베이스 모두 Commerce 응용 프로그램과 동일한 호스트에 있다고 가정합니다. 그러나 데이터베이스 위치와 이름을 선택할 수 있는 권한은 사용자에게 있습니다. 우리는 우리의 예제가 지침을 따르기 쉽게 만들었으면 합니다.

## 상거래 시스템 백업

Adobe은 프로세스 중에 문제가 발생하는 경우 복원할 수 있도록 현재 데이터베이스와 파일 시스템을 백업하는 것을 강력히 권장합니다.

**시스템을 백업하려면**:

1. Commerce 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 다음 명령을 입력합니다.

   ```bash
   magento setup:backup --code --media --db
   ```

1. 다음 섹션을 계속합니다.

## 추가 마스터 데이터베이스 설정

이 섹션에서는 판매 및 견적 테이블에 대한 데이터베이스 인스턴스를 생성하는 방법에 대해 설명합니다.

**판매 및 OMS 견적 데이터베이스를 생성하려면**:

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. MySQL 명령 프롬프트에 액세스하려면 다음 명령을 입력합니다.

   ```bash
   mysql -u root -p
   ```

1. MySQL 입력 `root` 메시지가 표시되면 사용자의 암호.
1. 표시된 순서대로 다음 명령을 입력하여 데이터베이스 인스턴스를 생성합니다. `magento_quote` 및 `magento_sales` 사용자 이름과 암호가 동일한 경우:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 입력 `exit` 를 클릭하여 명령 프롬프트를 종료합니다.

1. 한 번에 하나씩 데이터베이스를 확인합니다.

   quote 데이터베이스:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL 모니터가 표시되면 데이터베이스가 제대로 만들어진 것입니다. 오류가 표시되면 이전 명령을 반복합니다.

1. 다음 섹션을 계속합니다.

## 판매 데이터베이스 구성

이 섹션에서는 인용 데이터베이스 테이블을 변경하고 해당 테이블에서 데이터를 백업하는 SQL 스크립트를 만들고 실행하는 방법에 대해 설명합니다.

영업 데이터베이스 테이블 이름은 다음으로 시작:

- `salesrule_`
- `sales_`
- `magento_sales_`
- 다음 `magento_customercustomattributes_sales_flat_order` 테이블도 영향을 받습니다

>[!INFO]
>
>이 섹션에는 특정 데이터베이스 테이블 이름이 있는 스크립트가 포함되어 있습니다. 사용자 지정을 수행했거나 사용자 지정에 대한 작업을 수행하기 전에 전체 테이블 목록을 보려면 [참조 스크립트](#reference-scripts).

자세한 내용은 다음을 참조하십시오.

- [판매 데이터베이스 SQL 스크립트 생성](#create-sales-database-sql-scripts)
- [영업 데이터 백업](#back-up-sales-data)

### 판매 데이터베이스 SQL 스크립트 생성

Commerce 서버에 로그인할 때 사용자가 액세스할 수 있는 위치에 다음 SQL 스크립트를 만듭니다. 예를 들어, 다음 계정으로 로그인하거나 명령을 실행하는 경우 `root`에서 스크립트를 만들 수 있습니다. `/root/sql-scripts` 디렉토리.

#### 외래 키 제거

이 스크립트는 판매 데이터베이스에서 비판매 테이블을 참조하는 외래 키를 제거합니다.

다음 스크립트를 만들고 다음과 같은 이름을 지정합니다 `1_foreign-sales.sql`. 바꾸기 `<your main DB name>` (데이터베이스 이름 포함)

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### 판매 데이터베이스 구성

이전 스크립트를 실행합니다.

1. MySQL 데이터베이스에 다음으로 로그인 `root` 또는 관리 사용자:

   ```bash
   mysql -u root -p
   ```

1. 위치: `mysql>` 프롬프트에서 다음과 같이 스크립트를 실행합니다.

   ```shell
   source <path>/<script>.sql
   ```

   예를 들어,

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. 스크립트를 실행한 후 다음을 입력합니다. `exit`.

### 영업 데이터 백업

이 섹션에서는 별도의 판매 데이터베이스에서 복원할 수 있도록 기본 Commerce 데이터베이스에서 판매 테이블을 백업하는 방법에 대해 설명합니다.

현재 다음 위치에 있는 경우: `mysql>` 프롬프트, 입력 `exit` 를 입력하여 명령 셸로 돌아갑니다.

다음 실행 `mysqldump` 명령 셸에서 한 번에 하나씩 명령을 실행합니다. 각 변수에서 다음을 대체합니다.

- `<your database root username>` 데이터베이스 루트 사용자 이름 사용
- `<your database root user password>` 사용자 암호 사용
- `<your main Commerce DB name>` 상거래 데이터베이스 이름 사용
- `<path>` 쓰기 가능한 파일 시스템 경로 사용

#### 스크립트 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### 스크립트 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### 스크립트 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### 스크립트 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 판매 데이터 복원

이 스크립트는 견적 데이터베이스에 판매 데이터를 복원합니다.

#### NDB 요구 사항

를 사용하는 경우 [네트워크 데이터베이스(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 클러스터:

1. 덤프 파일에서 테이블을 InnoDb에서 NDB 유형으로 변환:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB 테이블이 FULLTEXT를 지원하지 않으므로 덤프에서 FULLTEXT 키가 있는 행을 제거합니다.

#### 데이터 복원

다음 명령을 실행합니다.

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

위치

- `<your sales DB name>` (판매 데이터베이스 이름 포함)

   이 항목에서 샘플 데이터베이스 이름은 `magento_sales`.

- `<root username>` MySQL 루트 사용자 이름 사용
- `<root user password>` 사용자 암호 사용
- 이전에 만든 백업 파일의 위치를 확인합니다(예: `/var/sales.sql`)

## 견적 데이터베이스 구성

이 섹션에서는 판매 데이터베이스 테이블에서 외래 키를 삭제하고 테이블을 판매 데이터베이스로 이동하는 데 필요한 작업에 대해 설명합니다.

>[!INFO]
>
>이 섹션에는 특정 데이터베이스 테이블 이름이 있는 스크립트가 포함되어 있습니다. 사용자 지정을 수행했거나 사용자 지정에 대한 작업을 수행하기 전에 전체 테이블 목록을 보려면 [참조 스크립트](#reference-scripts).

따옴표 데이터베이스 테이블 이름 시작 문자 `quote`. 다음 `magento_customercustomattributes_sales_flat_quote` 및 `magento_customercustomattributes_sales_flat_quote_address` 테이블도 영향을 받습니다

### 견적 테이블에서 외래 키 삭제

이 스크립트는 견적 테이블에서 비견적 테이블을 참조하는 외래 키를 제거합니다. 바꾸기 `<your main Commerce DB name>` Commerce 데이터베이스의 이름으로 바꿉니다.

다음 스크립트를 만들고 다음과 같은 이름을 지정합니다 `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

다음과 같이 스크립트를 실행합니다.

1. MySQL 데이터베이스에 루트 또는 관리 사용자로 로그인합니다.

   ```bash
   mysql -u root -p
   ```

1. 위치: `mysql >` 프롬프트에서 다음과 같이 스크립트를 실행합니다.
   `source <path>/<script>.sql`

   예를 들어,

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. 스크립트가 실행된 후 을 입력합니다. `exit`.

### 견적 테이블 백업

이 섹션에서는 주 데이터베이스에서 따옴표 테이블을 백업하고 따옴표 데이터베이스에서 복원하는 방법에 대해 설명합니다.

명령 프롬프트에서 다음 명령을 실행합니다.

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB 요구 사항

를 사용하는 경우 [네트워크 데이터베이스(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 클러스터:

1. 덤프 파일에서 테이블을 InnoDb에서 NDB 유형으로 변환:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB 테이블이 FULLTEXT를 지원하지 않으므로 덤프에서 FULLTEXT 키가 있는 행을 제거합니다.

### 인용 데이터베이스에 테이블 복원

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## 데이터베이스에서 판매 및 견적 테이블 삭제

Commerce 데이터베이스의 Sales 및 Quote 테이블을 스크립팅합니다. 바꾸기 `<your main DB name>` Commerce 데이터베이스의 이름으로 바꿉니다.

다음 스크립트를 만들고 다음과 같은 이름을 지정합니다 `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

다음과 같이 스크립트를 실행합니다.

1. MySQL 데이터베이스에 루트 또는 관리 사용자로 로그인합니다.

   ```bash
   mysql -u root -p
   ```

1. 위치: `mysql>` 프롬프트에서 다음과 같이 스크립트를 실행합니다.

   ```shell
   source <path>/<script>.sql
   ```

   예를 들어,

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. 스크립트가 실행된 후 을 입력합니다. `exit`.

## 배포 구성 업데이트

데이터베이스를 수동으로 분할하는 마지막 단계는 Commerce의 배포 구성에 연결 및 리소스 정보를 추가하는 것입니다. `env.php`.

배포 구성을 업데이트하려면 다음을 수행하십시오.

1. Commerce 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 배포 구성 백업:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. 열기 `<magento_root>/app/etc/env.php` 텍스트 편집기에서 다음 섹션에서 설명한 지침을 사용하여 업데이트합니다.

### 데이터베이스 연결 업데이트

다음으로 시작하는 블록 찾기 `'default'` (아래) `'connection'`) 및 추가 `'checkout'` 및 `'sales'` 섹션. 샘플 값을 사이트에 적합한 값으로 바꿉니다.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### 리소스 업데이트

다음으로 시작하는 블록 찾기 `'resource'` 및 추가 `'checkout'` 및 `'sales'` 섹션에 다음과 같이 설명되어 있습니다.

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## 참조 스크립트

이 섹션에서는 영향을 받는 테이블에 대해 작업을 수행하지 않고 전체 목록을 인쇄하도록 실행할 수 있는 스크립트를 제공합니다. 데이터베이스를 수동으로 분할하기 전에 영향을 받는 테이블을 확인하는 데 사용할 수 있습니다. 이 기능은 데이터베이스 스키마를 사용자 지정하는 확장을 사용하는 경우 유용합니다.

이러한 스크립트를 사용하려면:

1. 이 섹션에서 각 스크립트의 내용으로 SQL 스크립트를 만듭니다.
1. 각 스크립트에서 `<your main DB name>` Commerce 데이터베이스의 이름으로 바꿉니다.

   이 항목에서 샘플 데이터베이스 이름은 `magento`.

1. 다음에서 각 스크립트 실행 `mysql>` 다음으로 프롬프트 작성 `source <script name>`
1. 출력을 검사합니다.
1. 각 스크립트의 결과를 다른 SQL 스크립트에 복사하여 파이프 문자 제거(`|`).
1. 다음에서 각 스크립트 실행 `mysql>` 다음으로 프롬프트 작성 `source <script name>`.

   이 두 번째 스크립트를 실행하면 기본 상거래 데이터베이스에서 작업이 수행됩니다.

### 외래 키(판매 테이블) 제거

이 스크립트는 판매 데이터베이스에서 비판매 테이블을 참조하는 외래 키를 제거합니다.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### 외래 키(견적 테이블) 제거

이 스크립트는 견적 테이블에서 비견적 테이블을 참조하는 외래 키를 제거합니다.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### 판매 테이블 삭제

이 스크립트는 상거래 데이터베이스에서 판매 테이블을 삭제합니다.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### 견적 테이블 삭제

다음으로 시작하는 모든 테이블 끌어 놓기 `quote_`.
