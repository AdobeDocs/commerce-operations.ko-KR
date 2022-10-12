---
title: 고객 개인 정보 참조(버전 1.x)
description: Magento 1.x에서 고객 개인 정보에 대한 데이터 흐름 및 데이터베이스 엔티티 매핑에 대해 알아봅니다.
source-git-commit: 0640b59cc529123911537475bbfc179c917ac258
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---


# 고객 개인 정보 참조(버전 1.x)

>[!NOTE]
>
>Adobe Commerce 및 Magento Open Source 판매자와 개발자가 개인 정보 보호 규정을 준수할 수 있도록 준비하는 데 도움이 되는 일련의 주제입니다. 법적 의무를 준수해야 하는지 및 어떻게 준수해야 하는지 확인하려면 법률 자문을 구하십시오.

다음과 같은 개인 정보 보호 규정에 대한 규정 준수 프로그램을 개발할 때 참조할 수 있도록 다음 데이터 흐름 다이어그램 및 데이터베이스 엔티티 매핑을 사용합니다.

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 데이터 흐름 다이어그램

데이터 흐름 다이어그램은 고객과 관리자가 상점 및 관리자에서 입력하고 검색할 수 있는 데이터 유형을 보여줍니다.

### 프런트 엔드 데이터 시작 지점

사용자는 계정 등록, 체크아웃 중 및 유사한 이벤트에 고객, 주소 및 결제 정보를 입력할 수 있습니다.

![프런트 엔드 데이터 시작 지점](../../assets/security-compliance/frontend-data-entry-points.svg)

### 프런트 엔드 데이터 액세스 포인트

고객이 로그인하고 여러 다른 페이지를 보거나 체크 아웃하면 상거래에 고객 정보가 로드됩니다.

![프런트 엔드 데이터 액세스 포인트](../../assets/security-compliance/frontend-data-access-points.svg)

### 백엔드 데이터 시작 지점

상인은 관리자의 고객, 주소 및 결제 정보를 입력하여 고객 또는 주문을 생성할 수 있습니다.

![백엔드 데이터 시작 지점](../../assets/security-compliance/backend-data-entry-points.svg)

### 백엔드 데이터 액세스 포인트

상거래(Commerce)는 상인이 여러 유형의 그리드를 보고, 그리드를 클릭하여 세부 정보를 확인하고, 다양한 기타 작업을 수행할 때 고객 정보를 로드합니다.

![백엔드 데이터 액세스 포인트](../../assets/security-compliance/backend-data-access-points.svg)

## 데이터베이스 엔터티

Magento 1은 고객, 판매 및 기타 데이터베이스 테이블에 고객 정보를 저장합니다.

### 고객 데이터

Magento 1은 `customer_entity` 및 `customer_address_entity` 표. 이 두 테이블 모두 사용자 지정 고객 속성을 포함할 수 있는 여러 참조 테이블이 있습니다.

#### `customer_entity` 및 참조 테이블

다음 열 `customer_entity`에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `email` | varchar(255) |

다음 표에서는 `customer_entity` 및 은 사용자 지정 고객 속성을 포함할 수 있습니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | 십진수(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 텍스트 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` 및 참조 테이블

다음 표 참조 `customer_address_entity` 및 은 사용자 지정 고객 속성을 포함할 수 있습니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | 십진수(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 텍스트 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 데이터 순서 지정

다음 `sales_flat_order` 및 관련 테이블에는 고객의 이름, 청구 및 배송 주소 및 관련 정보가 포함됩니다.

#### `sales_flat_order` 표

다음 열 `sales_order` 에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` 표

다음 `sales_flat_order_address` 테이블에는 고객의 주소가 포함되어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | 텍스트 |

#### `sales_flat_order_grid` 표

다음 열 `sales_flat_order_grid` 에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` 표

다음 열 `sales_flat_order_payment` 에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### 견적 데이터

따옴표에는 고객 이름, 이메일, 주소 및 관련 정보가 포함되어 있습니다.

#### `sales_flat_quote` 표

다음 열 `sales_flat_quote` 에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` 표

다음 열 `sales_flat_quote_address` 에는 고객 정보가 들어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment` 표

다음 `sales_flat_quote_payment` 표에는 신용 카드 정보 및 기타 트랜잭션 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### 데이터 아카이브

다음 표 및 열에는 고객 정보가 포함됩니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 영업 데이터

다음 표 및 열에는 고객 정보가 포함됩니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA 데이터

다음 RMA 테이블 및 열에는 고객 정보가 포함됩니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### 기타 데이터

다음 표 및 열에는 고객 정보가 포함됩니다.

| 표 | 열 | 데이터 유형 |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | 텍스트 |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | 텍스트 |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

고객을 참조하는 기타 테이블:

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
