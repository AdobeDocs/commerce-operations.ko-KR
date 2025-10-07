---
title: B2B 확장 구성 경로 참조
description: Adobe Commerce의 B2B 확장 구성 경로 및 값에 대해 알아봅니다. 회사, 결제, 견적 및 B2B 관련 구성 옵션을 살펴봅니다.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# B2B 확장 구성 경로 참조

_Adobe Commerce용 B2B가 설치된 인스턴스에 사용할 수 있습니다._

이 항목에서는 Commerce Enterprise B2B 확장에 대한 구성 경로를 나열합니다. [`magento app:config:dump` 명령](../cli/export-configuration.md)은(는) 이러한 값을 소스 제어에 있어야 하는 공유 구성 파일 `app/etc/config.php`에 씁니다.

>[!INFO]
>
>이 참조에는 Adobe Commerce용 B2B에 고유한 _only_ 구성 경로가 나열됩니다. 이 확장에는 Adobe Commerce에 대한 모든 구성 경로가 포함됩니다.

이러한 구성 경로에 대해서는 다음을 참조하십시오.

- [결제 구성 경로](config-reference-payment.md)
- [중요한 시스템별 구성 경로 참조](config-reference-sens.md)

선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 [환경 변수를 사용하여 구성 설정을 무시하십시오](override-config-settings.md#environment-variables).

## 일반 범주

이 섹션에는 관리자의 **[!UICONTROL Stores]** > 설정 > **[!UICONTROL Configuration]** > **[!UICONTROL General]** 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### B2B 기능 경로

이러한 구성 값은 **[!UICONTROL Stores]** > 설정 > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 회사 활성화 | `btob/website_configuration/company_active` | | | |
| 공유 카탈로그 활성화 | `btob/website_configuration/sharedcatalog_active` | | | |
| B2B 견적 활성화 | `btob/website_configuration/negotiablequote_active` | | | |
| 빠른 주문 활성화 | `btob/website_configuration/quickorder_active` | | | |
| 구매요청 목록 활성화 | `btob/website_configuration/requisition_list_active` | | | |
| 해당 결제 방법 | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| 결제 방법 | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## 고객 범주

이 섹션에는 관리자의 **[!UICONTROL Stores]** > 설정 > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 회사 구성 경로

이러한 구성 값은 **[!UICONTROL Stores]** > 설정 > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|
| Storefront에서 회사 등록 허용 | `company/general/allow_company_registration` | | | |
| 회사 등록 전자 메일 수신자 | `company/email/company_registration` | | | ![중요](/help/assets/configuration/cloud-sens.png) |
| 회사 등록 이메일 사본 발송 대상 | `company/email/company_registration_copy` | | | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 복사 전송 방법 | `company/email/company_copy_method` | | | |
| 기본 회사 등록 이메일 | `company/email/company_notify_admin_template` | | | |
| 고객 관련 이메일 | `company/email/heading_customer` | | | |
| 기본 영업 담당자 지정 이메일 | `company/email/customer_sales_representative_template` | | | |
| 고객 이메일에 회사 기본 할당 | `company/email/customer_company_customer_assign_template` | | | |
| 회사 관리자 이메일 기본 할당 | `company/email/customer_assign_super_user_template` | | | |
| 기본 회사 관리자 비활성 이메일 | `company/email/customer_inactivate_super_user_template` | | | |
| 기본 회사 관리자가 구성원 전자 메일로 변경됨 | `company/email/customer_remove_super_user_template` | | | |
| 기본 고객 상태 활성 이메일 | `company/email/customer_account_activated_template` | | | |
| 기본 고객 상태 비활성 이메일 | `company/email/customer_account_locked_template` | | | |
| 회사 상태 변경 | `company/email/heading_company_status` | | | |
| 회사 상태 변경 이메일 수신자 | `company/email/company_status_change` | | | |
| 회사 상태 변경 이메일 사본 다음으로 보내기 | `company/email/company_status_change_copy` | | | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 복사 전송 방법 | `company/email/company_status_copy_method` | | | |
| 활성 1 이메일에 대한 기본 회사 상태 변경 | `company/email/company_status_pending_approval_to_active_template` | | | |
| 활성 2 이메일에 대한 기본 회사 상태 변경 | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| 거부된 이메일에 대한 기본 회사 상태 변경 | `company/email/company_status_rejected_template` | | | |
| 차단된 전자 메일로 기본 회사 상태 변경 | `company/email/company_status_blocked_template` | | | |
| 승인 보류 이메일에 대한 기본 회사 상태 변경 | `company/email/company_status_pending_approval_template` | | | |
| 회사 신용 | `company/email/heading_company_credit` | | | |
| 회사 신용 변경 이메일 발신자 | `company/email/company_credit_change` |  | | ![중요](/help/assets/configuration/cloud-sens.png) |
| 다음으로 회사 크레딧 변경 이메일 사본 보내기 | `company/email/company_credit_change_copy` | | | |
| 이메일 복사 전송 방법 | `company/email/company_credit_copy_method` | | | |
| 할당된 이메일 템플릿 | `company/email/credit_allocated_email_template` | | | |
| 업데이트된 이메일 템플릿 | `company/email/credit_updated_email_template` | | | |
| 정산된 이메일 템플릿 | `company/email/credit_reimbursed_email_template` | | | |
| 환불 이메일 템플릿 | `company/email/credit_refunded_email_template` | | | |
| 되돌린 전자 메일 템플릿 | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### 구매요청 목록 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고객** > **구매요청 목록**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 구매요청 목록 수 | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## 판매 범주

이 섹션에는 **스토어** > 설정 > **구성** > **판매**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 영업 이메일 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **판매 이메일**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 활성화됨 | `sales_email/quote/enabled` | | | |
| 업데이트된 견적 템플리트(구매자에게) | `sales_email/quote/updated_buyer_template` | | | |
| 거부된 견적 템플리트(구매자에게) | `sales_email/quote/declined_buyer_template` | | | |
| 새 견적 템플리트(판매자에게) | `sales_email/quote/new_seller_template` | | | |
| 업데이트된 견적 템플릿(판매자에게) | `sales_email/quote/updated_seller_template` | | | |
| 견적 만료(48시간 이내) | `sales_email/quote/expire_two_days_template` | | | |
| 견적 만료(24시간 후) | `sales_email/quote/expire_one_day_template` | | | |
| 만료 날짜 재설정 | `sales_email/quote/expire_reset_template` | | | |
| 다음으로 견적 이메일 사본 보내기 | `sales_email/quote/copy_to` | | | ![중요](/help/assets/configuration/cloud-sens.png) |
| 견적 전송 전자 메일 복사 방법 | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### 따옴표 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **견적**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 최소 금액 | `quote/general/minimum_amount` | | | |
| 최소 금액 메시지 | `quote/general/minimum_amount_message` | | | |
| 기본 만료 기간 | `quote/general/default_expiration_period` | | | |
| 업로드할 파일 형식 | `quote/attached_files/file_formats` | | | |
| 최대 파일 크기 | `quote/attached_files/maximum_file_size` | | | |
| 최소 금액 | `quote/general/minimum_amount` | | | |
| 최소 금액 메시지 | `quote/general/minimum_amount_message` | | | |
| 기본 만료 기간 | `quote/general/default_expiration_period` | | | |
| 업로드할 파일 형식 | `quote/attached_files/file_formats` | | | |
| 최대 파일 크기 | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## 결제 방법 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **결제 방법**&#x200B;의 관리자에서 사용할 수 있습니다.

>[!INFO]
>
>사용 가능한 경로는 머천트 국가의 선택에 따라 결정됩니다.

| 이름 | 구성 경로 | 암호화되었습니까? | 시스템별? | 민감한? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 활성화됨 | `payment/au/companycredit/active` | | | |
| 제목 | `payment/au/companycredit/title` | | | |
| 새 주문 상태 | `payment/au/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/au/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/au/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/au/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/au/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/au/companycredit/sort_order` | | | |
| 활성화됨 | `payment/es/companycredit/active` | | | |
| 제목 | `payment/es/companycredit/title` | | | |
| 새 주문 상태 | `payment/es/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/es/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/es/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/es/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/es/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/es/companycredit/sort_order` | | | |
| 활성화됨 | `payment/companycredit/active` | | | |
| 제목 | `payment/companycredit/title` | | | |
| 새 주문 상태 | `payment/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/companycredit/sort_order` | | | |
| 활성화됨 | `payment/nz/companycredit/active` | | | |
| 제목 | `payment/nz/companycredit/title` | | | |
| 새 주문 상태 | `payment/nz/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/nz/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/nz/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/nz/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/nz/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/nz/companycredit/sort_order` | | | |
| 활성화됨 | `payment/us/companycredit/active` | | | |
| 제목 | `payment/us/companycredit/title` | | | |
| 새 주문 상태 | `payment/us/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/us/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/us/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/us/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/us/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/us/companycredit/sort_order` | | | |
| 활성화됨 | `payment/gb/companycredit/active` | | | |
| 제목 | `payment/gb/companycredit/title` | | | |
| 새 주문 상태 | `payment/gb/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/gb/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/gb/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/gb/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/gb/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/gb/companycredit/sort_order` | | | |
| 활성화됨 | `payment/de/companycredit/active` | | | |
| 제목 | `payment/de/companycredit/title` | | | |
| 새 주문 상태 | `payment/de/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/de/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/de/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/de/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/de/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/de/companycredit/sort_order` | | | |
| 활성화됨 | `payment/other/companycredit/active` | | | |
| 제목 | `payment/other/companycredit/title` | | | |
| 새 주문 상태 | `payment/other/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/other/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/other/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/other/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/other/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/other/companycredit/sort_order` | | | |
| 활성화됨 | `payment/ca/companycredit/active` | | | |
| 제목 | `payment/ca/companycredit/title` | | | |
| 새 주문 상태 | `payment/ca/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/ca/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/ca/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/ca/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/ca/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/ca/companycredit/sort_order` | | | |
| 활성화됨 | `payment/hk/companycredit/active` | | | |
| 제목 | `payment/hk/companycredit/title` | | | |
| 새 주문 상태 | `payment/hk/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/hk/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/hk/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/hk/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/hk/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/hk/companycredit/sort_order` | | | |
| 활성화됨 | `payment/jp/companycredit/active` | | | |
| 제목 | `payment/jp/companycredit/title` | | | |
| 새 주문 상태 | `payment/jp/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/jp/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/jp/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/jp/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/jp/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/jp/companycredit/sort_order` | | | |
| 활성화됨 | `payment/fr/companycredit/active` | | | |
| 제목 | `payment/fr/companycredit/title` | | | |
| 새 주문 상태 | `payment/fr/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/fr/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/fr/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/fr/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/fr/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/fr/companycredit/sort_order` | | | |
| 활성화됨 | `payment/it/companycredit/active` | | | |
| 제목 | `payment/it/companycredit/title` | | | |
| 새 주문 상태 | `payment/it/companycredit/order_status` | | | |
| 해당 국가의 결제 | `payment/it/companycredit/allowspecific` | | | |
| 특정 국가에서 결제 | `payment/it/companycredit/specificcountry` | | | |
| 최소 주문 총계 | `payment/it/companycredit/min_order_total` | | | |
| 최대 주문 총계 | `payment/it/companycredit/max_order_total` | | | |
| 정렬 순서 | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
