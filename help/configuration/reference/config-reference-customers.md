---
title: 고객 구성 경로 참조
description: 고객 구성 값 목록을 참조하십시오.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# 고객 구성 경로 참조

이 섹션에는 아래 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다. **스토어** > 설정 > **구성** > **고객**.

다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 공유 구성 파일에 이러한 값을 씁니다. `app/etc/config.php`: 소스 제어에 있어야 합니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 다음을 참조하십시오. [환경 변수를 사용하여 구성 설정을 재정의합니다.](override-config-settings.md#environment-variables). 이 주제에서는 다음을 수행합니다. _아님_ 목록 [중요 및 시스템별 값](config-reference-sens.md).

## 뉴스레터 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **뉴스레터**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 게스트 구독 허용 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인해야 함 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인 이메일 발신자 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인 이메일 템플릿 | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 성공 이메일 발신자 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 성공 이메일 템플릿 | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 구독 취소 이메일 발신자 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 구독 취소 | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 고객 구성 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **고객 구성**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 온라인 시간(분) 간격 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 계정 공유 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 그룹에 자동 지정 활성화 | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 다음을 기준으로 세금 계산 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 그룹 | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유효한 VAT ID에 대한 그룹 - 국내 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유효한 VAT ID에 대한 그룹 - 유니온 내 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 잘못된 VAT ID에 대한 그룹 | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유효성 검사 오류 그룹 | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 각 트랜잭션에 대한 유효성 검사 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| VAT ID를 기반으로 자동 그룹 변경 비활성화를 위한 기본값 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront에 VAT 번호 표시 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 환영 전자 메일 | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 없는 기본 환영 이메일 | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 발신자 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 확인 필요 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 확인 링크 이메일 | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 환영 전자 메일 | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용자에게 친숙한 고객 ID 생성 | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 재설정 보호 유형 | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 암호 재설정 요청 수 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 재설정 요청 사이의 최소 시간 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 잊음 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 미리 알림 | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 재설정 템플릿 | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 템플릿 이메일 발신자 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 복구 링크 만료 기간(시간) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그인/암호 찾기 양식에 자동 완성 사용 | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 필수 문자 클래스 수 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계정 잠금에 대한 최대 로그인 실패 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 암호 길이 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 잠금 시간(분) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 상세 주소의 줄 수 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 접두사 표시 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 접두사 드롭다운 옵션 | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가운데 이름 표시(초기) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 접미어 표시 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 접미사 드롭다운 옵션 | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 생년월일 표시 | `customer/address/dob_show`<br>최신 보안 및 개인 정보 보호 모범 사례를 준수하면서 이러한 데이터를 수집하거나 처리하기 전에 고객의 전체 생년월일(월, 일, 년)과 전체 이름 등의 기타 개인 식별자 저장과 관련된 잠재적 법적 및 보안 위험을 알고 있어야 합니다. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 세금/VAT 번호 표시 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 성별 표시 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 스토어 신용 기능 활성화 | `customer/magento_customerbalance/is_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객에게 스토어 크레딧 내역 표시 | `customer/magento_customerbalance/show_history` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 환불 저장소 크레딧 자동 | `customer/magento_customerbalance/refund_automatically` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 저장소 크레딧 업데이트 이메일 발신자 | `customer/magento_customerbalance/email_identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 신용 업데이트 이메일 템플릿 저장 | `customer/magento_customerbalance/email_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 로그인 후 고객을 계정 대시보드로 리디렉션 | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 텍스트 | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 텍스트 한 줄 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 세그먼트 기능 활성화 | `customer/magento_customersegment/is_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| Storefront에서 CAPTCHA 활성화 | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 글꼴 | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 모드 | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그인 시도 실패 횟수 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA 시간 초과(분) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기호 수 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA에 사용된 기호 | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대소문자 구분 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 위시리스트 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **위시리스트**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 활성화됨 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 여러 위시 목록 활성화 | `wishlist/general/multiple_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 여러 위시 목록 수 | `wishlist/general/multiple_wishlist_number` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 이메일 발신자 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 보낼 수 있는 최대 이메일 수 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 텍스트 길이 제한 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 위시리스트 요약 표시 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 초대 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **초대**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 초대 기능 활성화 | `magento_invitation/general/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| Storefront에서 초대 활성화 | `magento_invitation/general/enabled_on_front` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 참조된 고객 그룹 | `magento_invitation/general/registration_use_inviter_group` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 새 계정 등록 | `magento_invitation/general/registration_required_invitation` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객이 초대 이메일에 사용자 정의 메시지를 추가하도록 허용 | `magento_invitation/general/allow_customer_message` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 한 번에 최대 초대 전송 허용 | `magento_invitation/general/max_invitation_amount_per_send` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 초대 이메일 발신자 | `magento_invitation/email/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 초대 이메일 템플릿 | `magento_invitation/email/template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 보상 포인트 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **보상 점수**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 보상 포인트 기능 활성화 | `magento_reward/general/is_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| Storefront에서 보상 포인트 기능 활성화 | `magento_reward/general/is_enabled_on_front` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객은 보상 포인트 내역을 볼 수 있습니다. | `magento_reward/general/publish_history` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보상 포인트 잔고 상환 임계값 | `magento_reward/general/min_points_balance` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 상한 보상 점수 합계 | `magento_reward/general/max_points_balance` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보상 포인트 만료 기간(일) | `magento_reward/general/expiration_days` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보상 포인트 만료 계산 | `magento_reward/general/expiry_calculation` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 자동으로 환불 보상 포인트 | `magento_reward/general/refund_automatically` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 환불 금액에서 보상 포인트 자동 공제 | `magento_reward/general/deduct_automatically` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 랜딩 페이지 | `magento_reward/general/landing_page` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 구매 | `magento_reward/points/order` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 등록 | `magento_reward/points/register` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 뉴스레터 등록 | `magento_reward/points/newsletter` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객에게 초대 전환 | `magento_reward/points/invitation_customer` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 전환 수량 제한으로의 초대 | `magento_reward/points/invitation_customer_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 초대를 주문으로 변환 | `magento_reward/points/invitation_order` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 주문 전환 수량 제한으로의 초대 | `magento_reward/points/invitation_order_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 주문 리워드로 초대 전환 | `magento_reward/points/invitation_order_frequency` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제출 검토 | `magento_reward/points/review` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보상 검토 제출 수량 제한 | `magento_reward/points/review_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 이메일 발신자 | `magento_reward/notification/email_sender` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 기본적으로 고객 구독 | `magento_reward/notification/subscribe_by_default` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 잔액 업데이트 이메일 | `magento_reward/notification/balance_update_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 보상 포인트 만료 경고 이메일 | `magento_reward/notification/expiry_warning_template` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 다음 이전 만료 경고(일) | `magento_reward/notification/expiry_day_before` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 프로모션 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **프로모션**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 미리 알림 이메일 활성화 | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 간격 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 분/시간 | `promo/magento_reminder/minutes` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 시작 시간 | `promo/magento_reminder/time` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 한 번의 실행당 최대 이메일 수 | `promo/magento_reminder/limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 이메일 전송 실패 임계값 | `promo/magento_reminder/threshold` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 미리 알림 전자 메일 보낸 사람 | `promo/magento_reminder/identity` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 코드 길이 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 형식 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 접두사 | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 코드 접미사 | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X자마다 대시 | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 선물 레지스트리 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **선물 등록**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 선물 레지스트리 활성화 | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 등록자 수 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 발신자 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 발신자 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 전송 이메일 임계값 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 발신자 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 지속적인 장바구니 경로

이러한 구성 값은 다음 위치의 관리자에서 사용할 수 있습니다. **스토어** > 설정 > **구성** > **고객** > **지속적인 장바구니**.

| 이름 | 구성 경로 | 상업용으로만 사용할 수 있습니까? |
|--------------|--------------|--------------|
| 지속성 활성화 | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지속성 수명(초) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| &quot;내 정보 저장&quot; 사용 | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| &quot;내 정보 저장&quot; 기본값 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그아웃 시 지속성 지우기 | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니 유지 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persist 위시 목록 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최근에 주문한 항목 유지 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 현재 비교되는 제품 유지 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 비교 내역 유지 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최근에 본 제품 유지 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 그룹 멤버십 및 세분화 유지 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
