---
title: 영업 구성 경로 참조
description: 판매 구성 값 목록을 참조하십시오.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# 영업 구성 경로 참조

이 섹션에는 아래 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다. **스토어** > 설정 > **구성** > **판매**.

다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 공유 구성 파일에 이러한 값을 씁니다. `app/etc/config.php`: 소스 제어에 있어야 합니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 다음을 참조하십시오. [환경 변수를 사용하여 구성 설정을 재정의합니다.](override-config-settings.md#environment-variables). 이 주제에서는 다음을 수행합니다. _아님_ 목록 [중요 및 시스템별 값](config-reference-sens.md).

## 영업 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **판매**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 고객 IP 숨기기 | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 소계 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 할인 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 세금 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고정 제품세 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 총계 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기프트 카드 | `sales/totals_sort/giftcardaccount` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 스토어 크레딧 | `sales/totals_sort/customerbalance` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 순서 재지정 허용 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF 인쇄용 로고(200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML 인쇄 보기용 로고 | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주소 | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용 | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 금액 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 금액에 세금 포함 | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 설명 메시지 | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 표시할 오류 | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 여러 주소 체크아웃에서 각 주소를 개별적으로 확인 | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다중 주소 설명 메시지 | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 표시할 다중 주소 오류 | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 집계된 데이터 사용 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 보류 중인 지급 주문 수명(분) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 수준에서 선물 메시지 허용 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 항목에 대한 선물 메시지 허용 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 수준에서 선물 포장 허용 | `sales/gift_options/wrapping_allow_order` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 주문 항목에 대한 선물 포장 허용 | `sales/gift_options/wrapping_allow_items` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 선물 영수증 허용 | `sales/gift_options/allow_gift_receipt` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 인쇄된 카드 허용 | `sales/gift_options/allow_printed_card` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 인쇄된 카드의 기본 가격 | `sales/gift_options/printed_card_price` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 맵 활성화 | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 실제 가격 표시 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 팝업 텍스트 메시지 | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 &quot;무슨 내용입니까&quot; 문자 메시지 | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront의 내 계정에서 SKU별 주문 활성화 | `sales/product_sku/my_account_enable` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 단추 텍스트 | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 그룹 | `sales/product_sku/allowed_groups` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보관 사용 | `sales/magento_salesarchive/active` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 구매한 주문 보관 | `sales/magento_salesarchive/age` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보관할 주문 상태 | `sales/magento_salesarchive/order_statuses` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 상점 첫 화면에서 RMA 사용 | `sales/magento_rma/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제품 수준에서 RMA 활성화 | `sales/magento_rma/enabled_on_product` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 저장소 주소 사용 | `sales/magento_rma/use_store_address` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 영업 이메일 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **영업 이메일**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 비동기 전송 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 확인 전자 메일 보낸 사람 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 확인 템플릿 | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 새 주문 확인 템플릿 | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 전송 이메일 복사 방법 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 댓글 전자 메일 보낸 사람 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 주석 전자 메일 템플릿 | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 주문 주석 이메일 템플릿 | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 댓글 보내기 이메일 복사 방법 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 전자 메일 보낸 사람 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 전자 메일 템플릿 | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 인보이스 이메일 템플릿 | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 전자 메일 복사 전송 방법 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 주석 전자 메일 보낸 사람 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 주석 전자 메일 템플릿 | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 인보이스 댓글 이메일 템플릿 | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 송장 주석 전송 전자 메일 복사 방법 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 이메일 발신자 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 이메일 템플릿 | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 배송 이메일 템플릿 | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 이메일 복사 방법 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 댓글 전자 메일 보낸 사람 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 댓글 전자 메일 템플릿 | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 배송 댓글 이메일 템플릿 | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 발송 의견 보내기 전자 메일 복사 방법 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 전자 메일 보낸 사람 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 전자 메일 템플릿 | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 대변 메모 이메일 템플릿 | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 이메일 복사 전송 방법 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 댓글 전자 메일 보낸 사람 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 주석 전자 메일 템플릿 | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트용 메모 메모 댓글 전자 메일 템플릿 | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 주석 전송 전자 메일 복사 방법 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sales_email/magento_rma/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 이메일 발신자 | `sales_email/magento_rma/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 전자 메일 템플릿 | `sales_email/magento_rma/template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 게스트용 RMA 이메일 템플릿 | `sales_email/magento_rma/guest_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 이메일 복사 전송 방법 | `sales_email/magento_rma/copy_method` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `sales_email/magento_rma_auth/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 인증 전자 메일 보낸 사람 | `sales_email/magento_rma_auth/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 인증 전자 메일 템플릿 | `sales_email/magento_rma_auth/template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 게스트용 RMA 인증 이메일 템플릿 | `sales_email/magento_rma_auth/guest_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 인증 전자 메일 복사 전송 방법 | `sales_email/magento_rma_auth/copy_method` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `sales_email/magento_rma_comment/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 댓글 전자 메일 보낸 사람 | `sales_email/magento_rma_comment/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 댓글 전자 메일 템플릿 | `sales_email/magento_rma_comment/template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 게스트용 RMA 댓글 이메일 템플릿 | `sales_email/magento_rma_comment/guest_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 이메일 복사 전송 방법 | `sales_email/magento_rma_comment/copy_method` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `sales_email/magento_rma_customer_comment/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 댓글 전자 메일 보낸 사람 | `sales_email/magento_rma_customer_comment/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 댓글 전자 메일 수신자 | `sales_email/magento_rma_customer_comment/recipient` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 댓글 전자 메일 템플릿 | `sales_email/magento_rma_customer_comment/template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| RMA 이메일 복사 전송 방법 | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 헤더에 주문 ID 표시 | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 헤더에 주문 ID 표시 | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 헤더에 주문 ID 표시 | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 세금 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **세금**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 운송에 대한 세금 분류 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 증여 옵션에 대한 세금 분류 | `tax/classes/wrapping_tax_class` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제품에 대한 기본 세금 분류 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객에 대한 기본 세금 분류 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음을 기준으로 하는 세금 계산 방법 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음을 기준으로 세금 계산 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그 가격 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 가격 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 세금 적용 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 할인 적용 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 세금 적용 | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 국경 간 무역 사용 | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 국가 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 상태 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 게시물 코드 | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그에 제품 가격 표시 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 가격 표시 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 표시 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 소계 표시 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 금액 표시 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 선물 포장 가격 표시 | `tax/cart_display/gift_wrapping` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 인쇄된 카드 가격 표시 | `tax/cart_display/printed_card` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 세금을 주문 합계에 포함 | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전체 세금 요약 표시 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 영(0) 세금 소계 표시 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 표시 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 소계 표시 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 금액 표시 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 선물 포장 가격 표시 | `tax/sales_display/gift_wrapping` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 인쇄된 카드 가격 표시 | `tax/sales_display/printed_card` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 세금을 주문 합계에 포함 | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전체 세금 요약 표시 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 영(0) 세금 소계 표시 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT 활성화 | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 목록에 가격 표시 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 보기 페이지에 가격 표시 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 영업 모듈에 가격 표시 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일에 가격 표시 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT에 세금 적용 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 소계에 FPT 포함 | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 체크아웃 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **체크아웃**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| Onepage 체크아웃 활성화 | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트 체크아웃 허용 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 청구 주소 표시 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용 약관 | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 견적 라이프타임(일) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 제품 리디렉션 추가 후 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 그룹화된 제품 이미지 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 구성 가능한 제품 이미지 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 견적 라이프타임 미리 보기(분) | `checkout/cart/preview_quota_lifetime` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 장바구니 요약 표시 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니 사이드바 표시 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최근에 추가된 최대 표시 항목 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 실패 전자 메일 보낸 사람 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 실패 이메일 수신자 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 실패 템플릿 | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전송 결제 실패 이메일 복사 방법 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 배송 설정 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **배송 설정**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 사용자 정의 배송 정책 적용 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송 정책 | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 다중 배송 설정 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **다중 배송 설정**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 여러 주소로 배송 허용 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 복수 주소로 운송할 수 있는 최대 수량 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 게재 방법 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **게재 방법**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 활성화됨 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메서드 이름 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유형 | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메서드 이름 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 금액 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메서드 이름 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 조건 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 계산에 가상 제품 포함 | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 내보내기 | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가져오기 | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 체크아웃이 활성화됨 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA에 대해 활성화됨 | `carriers/ups/active_rma` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| UPS 유형 | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 모드 | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 배송의 출처 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게이트웨이 URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 협상된 요금 활성화 | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 패키지 요청 유형 | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 컨테이너 | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가중치 단위 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대상 유형 | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 패키지 중량(지원되는 최대 배송 중량은 배송 담당자에게 문의하십시오.) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 픽업 방법 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 패키지 중량(최소 지원 배송 중량은 배송 업체에 문의하십시오.) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 적용됨 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 메서드 | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자유 메서드 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 임계값 활성화 | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 금액 임계값 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 체크아웃이 활성화됨 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA에 대해 활성화됨 | `carriers/usps/active_rma` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 모드 | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 패키지 요청 유형 | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 컨테이너 | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Length | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 폭 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 높이 | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 둘레 | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가공 가능하 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 패키지 중량(지원되는 최대 배송 중량은 배송 담당자에게 문의하십시오.) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 적용됨 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 메서드 | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자유 메서드 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 임계값 활성화 | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 금액 임계값 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 체크아웃이 활성화됨 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA에 대해 활성화됨 | `carriers/fedex/active_rma` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 웹 서비스 URL(프로덕션) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 웹 서비스 URL(샌드박스) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 패키지 요청 유형 | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 패키징 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 드롭오프 | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가중치 단위 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 패키지 중량(지원되는 최대 배송 중량은 배송 담당자에게 문의하십시오.) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 적용됨 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주거용 배달 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 메서드 | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허브 ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자유 메서드 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 임계값 활성화 | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 금액 임계값 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 체크아웃이 활성화됨 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA에 대해 활성화됨 | `carriers/dhl/active_rma` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 컨텐츠 유형 | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 수수료 계산 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 처리 적용됨 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 취급 수수료 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 순서 구분 두께 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가중치 단위 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 높이 | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 깊이 | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 폭 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 메서드 | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 메서드 | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 준비 시간 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시된 오류 메시지 | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자유 메서드 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자유 메서드 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 임계값 활성화 | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 무료 배송 금액 임계값 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로 배송 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로 배송 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당되지 않는 경우 메서드 표시 | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **GOOGLE API**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 사용 | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계정 유형 | `google/analytics/type` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 콘텐츠 실험 활성화 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그 페이지의 목록 속성 | `google/analytics/catalog_page_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 크로스셀 블록의 목록 속성 | `google/analytics/crosssell_block_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 업셀 블록의 목록 속성 | `google/analytics/upsell_block_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 관련 제품 블록의 목록 속성 | `google/analytics/related_block_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 검색 결과 페이지의 목록 속성 | `google/analytics/search_page_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 프로모션 필드 &quot;레이블&quot;에 대한 &#39;내부 프로모션&#39;. | `google/analytics/promotions_list_value` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 사용 | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 언어 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 변환 형식 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 색상 | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 레이블 | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 값 유형 | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전환 값 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 기프트 카드 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **판매** > **기프트 카드**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 기프트 카드 알림 이메일 발신자 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기프트 카드 알림 이메일 템플릿 | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 상환 가능하 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 라이프타임(일) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 선물 메시지 허용 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 선물 메시지 최대 길이 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 항목이 다음과 같은 경우 기프트 카드 계정 생성 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기프트 카드 전자 메일 보낸 사람 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기프트 카드 템플릿 | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 길이 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 형식 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 접두사 | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 접미사 | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X자마다 대시 | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 풀 크기 | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 낮은 코드 풀 임계값 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
