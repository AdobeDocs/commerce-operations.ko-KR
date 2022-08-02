---
title: 결제 구성 경로 참조
description: 구성 가능한 결제 방법 값 목록을 참조하십시오.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '4133'
ht-degree: 0%

---


# 결제 구성 경로 참조

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **결제 방법**.

다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 이 값을 공유 구성 파일에 씁니다. `app/etc/config.php`: 소스 제어에서 사용해야 합니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 다음을 참조하십시오 [환경 변수를 사용하여 구성 설정 무시](override-config-settings.md#environment-variables). 이 주제의 기능은 다음과 같습니다 _not_ list [구분 및 시스템 특정 값](config-reference-sens.md).

설정은 결제 방법으로 추가로 구성됩니다.

## PayPal 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 이 솔루션 활성화 | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 컨텍스트 내 체크아웃 경험 활성화 | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 신용 사용 | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 신용 사용 | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 위치 | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 위치 | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 위치 | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 위치 | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 크기 | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 세부 사항 페이지에 표시 | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 표시 | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니 라인 항목 전송 | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 검토 단계 건너뛰기 | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니 라인 항목 전송 | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 운송 옵션 이전 | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 바로 가기 단추 맛 | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Guest 체크아웃 활성화 | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객의 청구 주소 필요 | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 청구 계약 등록 | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니 라인 항목 전송 | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 청구 계약 마법사에서 허용 | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동 가져오기 사용 | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약 | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시간 | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 제품 로고 | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 페이지 스타일 | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 헤더 이미지 URL | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 헤더 배경색 | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 머리글 테두리 색상 | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 페이지 배경색 | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이 솔루션 활성화 | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 주문 PayPal 신용 | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 세부 사항 페이지에 표시 | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 승인 기간(일) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문 유효 기간(일) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 하위 권한 수 | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 표시 | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## PayPal Payments Pro

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| API 인증 메서드 | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API에서 프록시 사용 | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Payments Pro 호스팅 솔루션(영국)

이러한 옵션은 영국을 로 선택한 경우에만 사용할 수 있습니다. [상인 국가](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 이 솔루션 활성화 | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지급 정보 단계에서 Express Checkout 표시 | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## PayPal Payflow Pro

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 저장소 사용 | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 저장소 제목 | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 신용 카드 유형 | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV 항목 필요 | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS 거리가 일치하지 않음 | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Zip이 일치하지 않음 | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 국제 AVS 표시기가 일치하지 않습니다. | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카드 보안 코드가 일치하지 않음 | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 공급업체 | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 프록시 사용 | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 파트너 | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 공급업체 | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 프록시 사용 | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이 솔루션 활성화 | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV 항목을 편집할 수 있음 | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV 항목 필요 | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전자 메일 보내기 확인 | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## PayPal 페이플로우 링크

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 파트너 | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 공급업체 | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Payflow 링크 활성화 | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Express 체크아웃 활성화 | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 주문 PayPal 신용 | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 지급 출처 | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 적용 가능한 국가 | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 확인 활성화 | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV 항목을 편집할 수 있음 | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV 항목 필요 | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전자 메일 보내기 확인 | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 0 하위 합계 체크아웃 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 활성화됨 | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 납품 지급 경로의 현금

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 활성화됨 | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 은행 이전 지급 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 활성화됨 | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 주문 경로 확인 또는 결제

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 활성화됨 | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 구매 주문 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 활성화됨 | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 국제 경로

>[!INFO]
>
>사용 가능한 경로는 선택한 경로에 따라 결정됩니다 [머천트 국가](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| SFTP 자격 증명 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이 솔루션 활성화 | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인 보내기 | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_nz/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_nz/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_nz/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_nz/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_nz/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_nz/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_nz/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_nz/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_nz/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_nz/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_nz/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_nz/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_nz/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_nz/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_nz/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_nz/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_nz/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_nz/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_nz/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_nz/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_nz/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_nz/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_nz/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_nz/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_nz/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_nz/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_nz/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_nz/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_nz/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_nz/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_nz/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_nz/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_nz/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_hk/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_hk/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_hk/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_hk/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_hk/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_hk/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_hk/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_hk/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_hk/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_hk/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_hk/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_hk/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_hk/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_hk/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_hk/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_hk/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_hk/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_hk/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_hk/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_hk/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_hk/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_hk/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_hk/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_hk/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_hk/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_hk/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 샌드박스 모드 | `payment_hk/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_hk/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_hk/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_hk/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_hk/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_hk/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_hk/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_es/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_es/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_es/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 프로필 ID | `payment_es/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |
| 새 주문 상태 | `payment_es/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_es/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_es/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_es/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_es/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_es/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_es/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_es/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_es/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_es/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 설치 ID | `payment_es/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 원격 관리자 설치 ID | `payment_es/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_es/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_es/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_es/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트 모드 | `payment_es/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_es/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_es/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_es/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_es/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_es/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_es/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_es/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_es/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_es/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_es/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_es/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_es/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_es/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_es/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_es/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_es/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_it/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_it/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_it/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_it/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_it/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_it/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_it/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_it/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_it/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_it/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_it/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_it/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_it/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_it/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_it/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_it/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_it/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_it/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_it/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_it/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_it/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_it/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_it/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_it/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_it/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_it/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_it/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_it/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_it/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_it/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_it/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_it/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_it/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_fr/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_fr/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_fr/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_fr/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_fr/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_fr/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_fr/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_fr/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_fr/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_fr/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_fr/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_fr/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_fr/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_fr/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_fr/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_fr/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_fr/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_fr/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_fr/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_fr/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_fr/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_fr/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_fr/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_fr/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_fr/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_fr/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_fr/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_fr/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_fr/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_fr/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_fr/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_fr/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_jp/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_jp/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_jp/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_jp/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_jp/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_jp/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_jp/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_jp/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_jp/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_jp/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_jp/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_jp/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_jp/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_jp/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_jp/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_jp/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_jp/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_jp/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_jp/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_jp/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_jp/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_jp/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_jp/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_jp/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_jp/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_jp/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_jp/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_jp/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_jp/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_jp/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_jp/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인 보내기 | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_au/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_au/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_au/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Merchant ID | `payment_au/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |
| 프로필 ID | `payment_au/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |
| 새 주문 상태 | `payment_au/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_au/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_au/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_au/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_au/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_au/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_au/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_au/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_au/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_au/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 설치 ID | `payment_au/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_au/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_au/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_au/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_au/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트 모드 | `payment_au/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_au/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_au/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_au/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_au/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_au/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_au/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_au/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_au/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_au/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_au/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_au/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_au/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_au/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_au/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_au/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_au/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이 솔루션 활성화 | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_ca/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_ca/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_ca/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_ca/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_ca/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_ca/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_ca/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_ca/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_ca/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_ca/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_ca/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_ca/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_ca/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_ca/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_ca/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_ca/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_ca/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_ca/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_ca/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_ca/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_ca/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_ca/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_ca/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_ca/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_ca/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_ca/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_ca/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_ca/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_ca/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_ca/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_ca/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_ca/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 고객 | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_other/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_other/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_other/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_other/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_other/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_other/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_other/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_other/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_other/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_other/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_other/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_other/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_other/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_other/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_other/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_other/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_other/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_other/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_other/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_other/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_other/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_other/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_other/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_other/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_other/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_other/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_other/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_other/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_other/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_other/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_other/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_other/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_de/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_de/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_de/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_de/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_de/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_de/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_de/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_de/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_de/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_de/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_de/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_de/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_de/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_de/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_de/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트 모드 | `payment_de/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_de/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_de/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_de/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_de/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_de/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_de/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_de/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_de/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_de/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_de/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_de/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_de/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_de/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_de/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_de/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_de/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_gb/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_gb/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_gb/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_gb/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_gb/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_gb/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_gb/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_gb/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_gb/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_gb/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_gb/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_gb/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_gb/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_gb/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_gb/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_gb/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_gb/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_gb/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_gb/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_gb/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_gb/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_gb/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_gb/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_gb/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_gb/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_gb/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_gb/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_gb/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_gb/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_gb/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_gb/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_gb/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_gb/eway/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약된 가져오기 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 신용 사용 | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 설정 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음과 같은 경우 트랜잭션 거부: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 가져오기 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 머천트 페이지 스타일 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 자동으로 모든 품목 송장 | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지침 | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수표 지급 대상 | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 결제 조치 | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제목 | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 주문 상태 | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수락된 통화 | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 디버그 | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 유형 | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 신용 카드 확인 | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 해당 국가로부터의 결제 | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특정 국가로부터의 지불 | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 주문 총액 | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 주문 총액 | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정렬 순서 | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `payment_us/cybersource/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_us/cybersource/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_us/cybersource/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 새 주문 상태 | `payment_us/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_us/cybersource/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_us/cybersource/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_us/cybersource/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_us/cybersource/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 주문 총액 | `payment_us/cybersource/min_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 최대 주문 총액 | `payment_us/cybersource/max_order_total` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_us/cybersource/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_us/worldpay/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_us/worldpay/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 편집 허용 | `payment_us/worldpay/fix_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연락처 정보 숨기기 | `payment_us/worldpay/hide_contact` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 서명 필드 | `payment_us/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_us/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트에 대한 지급 조치 | `payment_us/worldpay/test_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_us/worldpay/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_us/worldpay/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_us/worldpay/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| CVV에 대한 주문 상태를 사기 의심으로 설정 | `payment_us/worldpay/cvv_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| Postcode AVS에 대한 주문 상태를 사기 의심으로 설정 | `payment_us/worldpay/avs_fraud_case` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_us/worldpay/sort_order` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 활성화됨 | `payment_us/eway/active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 연결 유형 | `payment_us/eway/connection_type` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 제목 | `payment_us/eway/title` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 결제 조치 | `payment_us/eway/payment_action` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 디버그 | `payment_us/eway/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 카드 유형 | `payment_us/eway/cctypes` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 해당 국가로부터의 결제 | `payment_us/eway/allowspecific` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 특정 국가로부터의 지불 | `payment_us/eway/specificcountry` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 정렬 순서 | `payment_us/eway/sort_order` |  |

{style=&quot;table-layout:auto&quot;}
