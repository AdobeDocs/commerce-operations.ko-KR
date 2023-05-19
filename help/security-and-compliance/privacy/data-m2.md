---
title: 고객 개인 정보 참조(버전 2.x)
description: Adobe Commerce 및 Magento Open Source 2.x에서 고객 개인 정보에 대한 데이터 흐름 다이어그램 및 데이터베이스 엔티티 매핑에 대해 알아봅니다.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 고객 개인 정보 참조(버전 2.x)

>[!NOTE]
>
>이는 Adobe Commerce 및 Magento Open Source 판매자와 개발자가 개인 정보 보호 규정 준수를 준비하는 데 도움이 되는 일련의 항목 중 하나입니다. 귀하의 비즈니스가 법적 의무를 준수하는지 여부와 그 방법을 결정하려면 법률 고문과 상의하십시오.

다음과 같은 개인 정보 보호 규정을 위한 준수 프로그램을 개발할 때 참조할 수 있도록 다음 데이터 흐름 다이어그램 및 데이터베이스 엔티티 매핑을 사용하십시오.

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 데이터 흐름 다이어그램

데이터 흐름 다이어그램은 고객 및 관리자가 상점 및 관리자로부터 입력하고 검색할 수 있는 데이터 유형을 보여 줍니다.

### 프론트엔드 데이터 진입점

사용자는 계정 등록 시, 체크아웃 시, 유사한 이벤트 시 고객, 주소, 결제 정보를 입력할 수 있다.

![프론트엔드 데이터 진입점](../../assets/security-compliance/frontend-data-entry-points.svg)

### 프론트엔드 데이터 액세스 포인트

Adobe Commerce 및 Magento Open Source은 고객이 로그인하고 여러 페이지를 보거나 체크아웃할 때 고객 정보를 로드합니다.

![프론트엔드 데이터 액세스 포인트](../../assets/security-compliance/frontend-data-access-points.svg)

### 백엔드 데이터 진입점

판매자는 관리자로부터 고객 또는 주문을 생성할 때 고객 정보, 주소 데이터 및 결제 데이터를 입력할 수 있습니다.

![백엔드 데이터 진입점](../../assets/security-compliance/backend-data-entry-points.svg)

### 백엔드 데이터 액세스 포인트

Adobe Commerce 및 Magento Open Source은 판매자가 여러 유형의 그리드를 볼 때 고객 정보를 로드하고, 그리드를 클릭하여 자세한 정보를 확인하고, 기타 다양한 작업을 수행할 수 있습니다.

![백엔드 데이터 액세스 포인트](../../assets/security-compliance/backend-data-access-points.svg)

## 데이터베이스 엔티티

Adobe Commerce 및 Magento Open Source은 주로 고객, 주소, 주문, 견적 및 결제 테이블에 고객별 정보를 저장합니다. 다른 표에는 고객 ID에 대한 참조가 포함되어 있습니다.

### 고객 데이터

Adobe Commerce 및 Magento Open Source은 다음 고객 속성을 저장하도록 구성할 수 있습니다.

- 생일
- 이메일
- 이름
- 성별
- 성
- 가운데 이름/처음
- 이름 접두사
- 이름 접미사

>[!NOTE]
>
>최신 보안 및 개인 정보 보호 모범 사례를 준수하면서 이러한 데이터를 수집하거나 처리하기 전에 고객의 전체 생년월일(월, 일, 년)과 전체 이름 등의 기타 개인 식별자 저장과 관련된 잠재적 법적 및 보안 위험을 알고 있어야 합니다.

#### `customer_entity` 및 &#39;customer_entity&#39; 참조

의 다음 열 `customer_entity` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | 날짜 |
| `gender` | smallint(5) |

다음 표는 다음을 참조합니다. `customer_entity` 및 에는 사용자 지정 고객 특성이 포함될 수 있습니다.

| 표 | 열 | 데이터 유형 |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | 십진수(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 텍스트 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` 표

의 다음 열 `customer_grid_flat` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| -------------------- | ------------ |
| `name` | 텍스트 |
| `email` | varchar(255) |
| `dob` | 날짜 |
| `gender` | int(11) |
| `shipping_full` | 텍스트 |
| `billing_full` | 텍스트 |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### 주소 데이터

Adobe Commerce 및 Magento Open Source은 다음 고객 속성을 저장합니다.

- 도시
- 회사
- 국가
- 팩스
- 이름
- 성
- 가운데 이름/처음
- 이름 접두사
- 이름 접미사
- 전화 번호
- 시/도
- 시/도 ID
- 상세 주소
- VAT 번호
- Zip/우편 번호

#### `customer_address_entity` 및 `customer_address_entity` 참조

의 다음 열 `customer_address_entity` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | 텍스트 |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

다음 표는 다음을 참조합니다. `customer_address_entity` 및 에는 사용자 지정 고객 특성이 포함될 수 있습니다.

| 표 | 열 | 데이터 유형 |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | 십진수(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 텍스트 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 주문 데이터

다음 `sales_order` 및 관련 테이블에는 고객 이름, 청구 및 배송 주소 및 관련 데이터가 포함되어 있습니다.

#### `sales_order` 표

의 다음 열 `sales_order` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` 표

다음 `sales_order_address` 테이블에는 고객의 주소가 들어 있습니다.

| 열 | 데이터 유형 |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` 표

의 다음 열 `sales_order_grid` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### 견적 데이터

견적에는 고객의 이름, 이메일, 주소 및 관련 정보가 포함되어 있습니다.

#### `quote` 표

의 다음 열 `quote` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` 표

의 다음 열 `quote_address` 표에는 고객 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### 결제 데이터

다음 `sales_order_payment` 표에는 신용 카드 정보 및 기타 트랜잭션 정보가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | 텍스트 |

### 초대 데이터

고객이 비공개 판매 및 이벤트에 초대장을 보낼 수 있도록 Adobe Commerce 및 Magento Open Source을 구성할 수 있습니다.

#### `magento_invitation` 표

다음 `magento_invitation` 표에는 고객 ID, 이메일 및 참조 ID가 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` 표

다음 `magento_invitation_track` 표에는 고객 정보도 포함되어 있습니다.

| 열 | 데이터 유형 |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### 고객을 참조하는 기타 테이블

다음 표에는 `customer_id` 열:

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
