---
title: 일반 구성 경로 참조
description: 일반 및 고급 구성 값 목록을 참조하십시오.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---


# 일반 및 고급 구성 경로 참조

이 항목에는 일반 및 고급 구성 경로와 _not_ [구분 및 시스템 특정 값](config-reference-sens.md). 다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 이 값을 공유 구성 파일에 씁니다. `app/etc/config.php`: 소스 제어에서 사용해야 합니다.

선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 다음을 참조하십시오 [환경 변수를 사용하여 구성 설정 무시](override-config-settings.md#environment-variables).

## 일반 카테고리

이 섹션에는 관리자 아래의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **일반**.

### 일반 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > 일반 > **일반**.

| 이름 | 구성 경로 | 상거래 전용? | 민감한가? |
|--------------|--------------|--------------|--------------|
| 기본 국가 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![중요](/help/assets/configuration/cloud-sens.png) |
| 국가 허용 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![중요](/help/assets/configuration/cloud-sens.png) |
| 우편 번호는 다음에 선택 사항입니다 | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![중요](/help/assets/configuration/cloud-sens.png) |
| 유럽 연합 국가 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![중요](/help/assets/configuration/cloud-sens.png) |
| 상위 대상 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 상태는 | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 국가 선택 사항인 경우 상태 선택 허용 | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 표준 시간대 | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 로케일 | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 무게 단위 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 첫째 주 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 주말 일수 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 액세스 제한 | `general/restriction/is_active` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |
| 제한 모드 | `general/restriction/mode` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |
| 시작 페이지 | `general/restriction/http_redirect` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |
| 랜딩 페이지 | `general/restriction/cms_page` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |
| HTTP 응답 | `general/restriction/http_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |
| 저장소 이름 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 스토어 전화 번호 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 저장 작업 시간 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 국가 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 지역/주 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 우편 번호 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 구/군/시 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 주소 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 주소 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| VAT 번호 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 단일 저장소 모드 활성화 | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style=&quot;table-layout:auto&quot;}

### 웹 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **웹**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| Url에 스토어 코드 추가 | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 URL로 자동 리디렉션 | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 웹 서버 다시 작성 사용 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront에서 보안 URL 사용 | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자에서 보안 URL 사용 | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP Strict Transport Security(HSTS) 활성화 | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 비보안 요청 업그레이드 | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Offloader 헤더 | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS 홈 페이지 | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS 경로 없음 페이지 | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS 쿠키 없음 페이지 | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS 페이지에 대한 탐색 표시 | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 쿠키 수명 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP만 사용 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 쿠키 제한 모드 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| REMOTE_ADDR의 유효성을 확인합니다. | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_VIA 유효성 검사 | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_X_FORWARDED_FOR의 유효성 검사 | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_USER_AGENT 유효성 검사 | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront에서 SID 사용 | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 쿠키가 비활성화된 경우 CMS-페이지로 리디렉션합니다. | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript가 비활성화되어 있는지 알림 표시 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로컬 저장소 사용 안 함 알림 표시 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 통화 설정 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **통화 설정**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 기본 통화 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 표시 통화 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 통화 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| 연결 시간 초과(초) | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 연결 시간 초과(초) | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 연결 시간 초과(초) | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 서비스 | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 시간 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 수신자 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 발신자 | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 템플릿 | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 연락처 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **연락처**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 연락처 사용 | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전자 메일 보내기 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 발신자 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 보고서 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **보고서**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 연간 시작 | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이번 달 시작 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 컨텐츠 관리 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **콘텐츠 관리**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| WYSIWYG 편집기 활성화 | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그에 대한 WYSIWYG에서 미디어 컨텐츠에 대한 정적 URL 사용 | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계층 기능 활성화 | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계층 메타데이터 활성화 | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계층 메뉴의 기본 레이아웃 | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 새 Relic 보고 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **새 Relic 보고**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| New Relic 통합 활성화 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 Relic 응용 프로그램 이름 | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cron 활성화 | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 고급 카테고리

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **고급**.

### 관리 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **관리**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 암호 분실 이메일 템플릿 | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 보낸 사람 분실 및 재설정 | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용자 알림 템플릿 | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 페이지 | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용자 지정 관리 URL 사용 | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용자 지정 관리자 경로 사용 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자 계정 공유 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 재설정 보호 유형 | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 복구 링크 만료 기간(시간) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 암호 재설정 요청 수 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 재설정 요청 사이의 최소 시간 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL에 암호 키 추가 | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그인은 대/소문자를 구분합니다 | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자 세션 라이프타임(초) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 잠금 계정에 대한 최대 로그인 실패 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 잠금 시간(분) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 수명(일) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 암호 변경 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 차트 활성화 | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자에서 CAPTCHA 활성화 | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 글꼴 | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 표시 모드 | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그인 시도 실패 횟수 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA 시간 초과(분) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기호 수 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA에 사용된 기호 | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대/소문자 구분 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화된 작업 | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 시스템 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **시스템**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 성공적인 메시지 수명 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 후 메시지 다시 시도 진행 중 | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 실패한 메시지 수명 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 메시지 수명 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약 생성 간격 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 일정 예약 | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 내에서 실행되지 않는 경우 부재 중 | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기록 정리 간격 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 성공 내역 라이프타임 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 실패 기록 수명 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 별도의 프로세스 사용 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약 생성 간격 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 일정 예약 | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 내에서 실행되지 않는 경우 부재 중 | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기록 정리 간격 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 성공 내역 라이프타임 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 실패 기록 수명 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약 생성 간격 | `system/cron/staging/schedule_generate_every` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 일정 예약 | `system/cron/staging/schedule_ahead_for` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 내에서 실행되지 않는 경우 부재 중 | `system/cron/staging/schedule_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 기록 정리 간격 | `system/cron/staging/history_cleanup_every` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 성공 내역 라이프타임 | `system/cron/staging/history_success_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 실패 기록 수명 | `system/cron/staging/history_failure_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 별도의 프로세스 사용 | `system/cron/staging/use_separate_process` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 예약 생성 간격 | `system/cron/catalog/event/schedule_generate_every` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 일정 예약 | `system/cron/catalog/event/schedule_ahead_for` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 내에서 실행되지 않는 경우 부재 중 | `system/cron/catalog/event/schedule_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 기록 정리 간격 | `system/cron/catalog/event/history_cleanup_every` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 성공 내역 라이프타임 | `system/cron/catalog/event/history_success_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 실패 기록 수명 | `system/cron/catalog/event/history_failure_lifetime` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 별도의 프로세스 사용 | `system/cron/catalog/event/use_separate_process` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 별도의 프로세스 사용 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 통신 비활성화 | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 반환 경로 설정 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 반환 경로 이메일 | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 설치된 통화 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPS를 사용하여 피드 가져오기 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 업데이트 빈도 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 마지막 업데이트 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 백업 활성화 | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 백업 유형 | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 시간 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유지 관리 모드 | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그 항목 수명, 일 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그 보관 빈도 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 응용 프로그램 캐싱 | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 공개 콘텐츠의 TTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 유예 기간 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 구성 내보내기 | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 로그에 저장된 일 수 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 미디어 저장소 | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 미디어 데이터베이스 선택 | `system/media_storage_configuration/media_database` (Commerce 2.4.3에서 사용 안 함) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 환경 업데이트 시간 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 파일 저장, 일 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 예약된 파일 기록 정리 사용 | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 시간 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 템플릿 | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

### 개발자 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **개발자**.

| 이름 | 구성 경로 | 상거래 전용? |
|--------------|--------------|--------------|
| 워크플로우 유형 | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symlink 허용 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Html 축소 | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront에 대한 템플릿 경로 힌트 사용 | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자에 대한 템플릿 경로 힌트 활성화 | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 힌트에 블록 이름 추가 | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 파일에 로그 | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| syslog에 로그 | `dev/syslog/syslog_logging` |  |
| Storefront에 대해 활성화됨 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관리자가 활성화됨 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript 파일 병합 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript 번들 활성화 | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript 파일 축소 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 번역 전략 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 세션 저장소에 JS 오류 기록 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS 파일 병합 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS 파일 축소 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이미지 어댑터 | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 정적 파일 서명 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 비동기 색인 지정 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 캐시 사용자 정의 속성 | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
