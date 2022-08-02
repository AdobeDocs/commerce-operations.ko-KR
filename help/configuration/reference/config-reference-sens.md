---
title: 민감하고 시스템별 경로
description: 시스템별 및 중요한 구성 값 목록을 참조하십시오.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '3711'
ht-degree: 0%

---


# 구분 및 시스템별 설정

이 항목에서는 시스템별 및 중요 설정에 대한 구성 경로를 나열합니다.

- 다음 [`magento app:config:dump` 명령](../cli/export-configuration.md) 시스템별 구성 파일에 시스템 특정 설정을 씁니다. `app/etc/env.php`다음 작업을 수행합니다. _not_ 소스 제어에 있어야 합니다. 또한 모든 상거래 인스턴스에 대한 공유 구성을 `app/etc/config.php`, 이 파일 _다음과 같이 하십시오._ 소스 제어에 있어야 합니다.
- 다음 [`magento config:sensitive:set` 명령](../cli/set-configuration-values.md) 중요한 설정을 씁니다. `app/etc/env.php`.

   에서 설명한 대로 구성 변수를 사용하여 중요한 값을 설정할 수도 있습니다. [환경 변수를 사용하여 구성 설정 무시](../reference/override-config-settings.md#environment-variables).

기타 구성 경로 목록은 다음을 참조하십시오.

- [지급을 제외한 모든 구성 경로](../reference/config-reference-general.md)
- [결제 구성 경로](../reference/config-reference-payment.md).

>[!INFO]
>
>이 항목에 나열된 모든 구성 경로는 민감합니다. 다음 `System-specific?` 열에는 시스템 특정 값도 표시됩니다.

## 일반 카테고리 구분 및 시스템별 경로

이 섹션에는 관리자 아래의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **일반**.

### 웹 경로 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **웹**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 기본 URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 기본 링크 URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 정적 보기 파일에 대한 기본 URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 사용자 미디어 파일의 기본 URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 보안 기본 URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 보안 기본 링크 URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 정적 보기 파일에 대한 보안 기본 URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 사용자 미디어 파일에 대한 보안 기본 URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 기본 웹 URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 기본 경로 없음 URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 쿠키 경로 | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 쿠키 도메인 | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 쿠키 수명 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| HTTP만 사용 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 쿠키 제한 모드 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 통화 설정 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **통화 설정**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 전자 메일 주소 구분 및 시스템별 경로 저장

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **이메일 구성** > **일반** > **이메일 주소 저장**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 발신자 이름 | `trans_email/ident_general/name` |  |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보낸 사람 이메일 | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발신자 이름 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보낸 사람 이메일 | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발신자 이름 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보낸 사람 이메일 | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발신자 이름 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보낸 사람 이메일 | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발신자 이름 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보낸 사람 이메일 | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 연락처 및 시스템 특정 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **연락처**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 전자 메일 보내기 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 발신자 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 템플릿 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 새로운 Relic 보고 민감성 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **일반** > **새 Relic 보고**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 새 Relic 계정 ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 Relic 응용 프로그램 ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 Relic API 키 | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 통찰력 API 키 | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 Relic API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 통찰력 API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 고객 카테고리에 맞는 시스템 특정 경로

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **고객**.

### 고객 구성 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고객** > **고객 구성**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 기본 이메일 도메인 | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## 카탈로그 카테고리

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **카탈로그**.

### 카탈로그 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **카탈로그** > **카탈로그**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| YouTube API 키 | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Solr 서버 호스트 이름 | `catalog/search/solr_server_hostname` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Solr 서버 포트 | `catalog/search/solr_server_port` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Solr 서버 사용자 이름 | `catalog/search/solr_server_username` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Solr 서버 암호 | `catalog/search/solr_server_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 솔루션 서버 경로 | `catalog/search/solr_server_path` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch 서버 호스트 이름 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch 서버 포트 | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch 인덱스 접두사 | `catalog/search/elasticsearch_index_prefix` | !<!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch HTTP 인증 활성화 | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP 사용자 이름 | `catalog/search/elasticsearch_username` | !<!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP 암호 | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| Elasticsearch 서버 시간 초과 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 재고 감지 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **카탈로그** > **인벤토리**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API 키 | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### XML 사이트 맵 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **카탈로그** > **XML 사이트 맵**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 판매 카테고리

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **영업**.

### 배송 설정 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **배송 설정**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 국가 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 지역/주 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 우편 번호 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 구/군/시 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 주소 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 주소 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 계정 | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 영업 전자 메일 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **영업 이메일**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 주문 이메일 복사본 전송 대상 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 주문 주석 전자 메일 복사본 전송 대상 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 송장 전자 메일 복사 발송 대상 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 송장 주석 전자 메일 복사 발송 대상 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발송 전자 메일 복사 발송 대상 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 발송 주석 전자 메일 복사 발송 대상 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 대변 메모 전자 메일 복사 전송 위치 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 대변 메모 설명 전자 메일 복사 전송 대상 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 픽업 준비 전자 메일 복사본 보내기 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 체크 아웃 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **체크아웃**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 지급 실패 전자 메일 복사본 전송 대상 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Google API에 민감한 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **Google API**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 컨테이너 Id | `google/analytics/container_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 게재 방법은 중요하며 시스템별 경로가

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **배달 방법**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 게이트웨이 URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 보안 게이트웨이 URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 제목 | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용자 ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 사용자 ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 라이선스 번호 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 추적 XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 게이트웨이 XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 출하 번호 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 디버그 | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 계정 ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 키 | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 미터 번호 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 디버그 | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 계정 번호 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 게이트웨이 URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 모드 | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 영업 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **영업**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 연락처 이름 | `sales/magento_rma/store_name` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 주소 | `sales/magento_rma/address` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 주소 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 구/군/시 | `sales/magento_rma/city` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 시/도 | `sales/magento_rma/region_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 우편 번호 | `sales/magento_rma/zip` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 국가 | `sales/magento_rma/country_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| RMA 전자 메일 복사 발송 대상 | `sales_email/magento_rma/copy_to` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| RMA 인증 전자 메일 복사 발송 대상 | `sales_email/magento_rma_auth/copy_to` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| RMA 주석 전자 메일 복사 발송 대상 | `sales_email/magento_rma_comment/copy_to` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| RMA 주석 전자 메일 복사 발송 대상 | `sales_email/magento_rma_customer_comment/copy_to` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Google API 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **영업** > **Google API**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 계정 번호 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 고급 카테고리

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **고급**.

### 관리자 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **관리**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 지정 관리 URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 사용자 지정 관리자 경로 | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 시스템 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **시스템**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 목록 | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 오류 이메일 발신자 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 개발자 구분 및 시스템별 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **개발자**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 허용된 IP(쉼표로 구분됨) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 고급 카테고리

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **고급**.

### 시스템 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **시스템**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 호스트 | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 포트(25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 백엔드 호스트 | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 백엔드 포트 | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 개발자 경로

이러한 구성 값은 의 관리자에서 사용할 수 있습니다 **스토어** > 설정 > **구성** > **고급** > **개발자**.

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 세션 저장소 키에 JS 오류 로그 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## 지불 구분 및 시스템별 경로

이 섹션에는 아래의 관리자의 옵션에 사용할 수 있는 변수 이름 및 구성 경로가 나열됩니다 **스토어** > 설정 > **구성** > **영업** > **결제**.

### 일반 변수

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? |
|--------------|--------------|--------------|--------------|
| 머천트 국가 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

>[!INFO]
>
>이 변수에 대한 선택은 다음 중 어느 것을 결정합니다 [국제 경로](#international-paths) 사용할 수 있습니다.

### PayPal 민감성 및 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| PayPal 머천트 계정과 연결된 이메일(선택 사항) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 머천트 계정 ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 게시자 ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 로그인 | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 사용자 지정 끝점 호스트 이름 또는 IP 주소 | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 모드 | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 디버그 모드 | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 디버그 모드 | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| SFTP 자격 증명 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payflow Pro 민감성 및 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 사용자 지정 경로 | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 사용자 | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 파트너 | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프록시 호스트 | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프록시 포트 | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 디버그 모드 | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| SFTP 자격 증명 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 신용 카드 설정 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal 페이플로우 링크 구분 및 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 암호 | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 프록시 사용 | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 프록시 호스트 | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 프록시 포트 | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 디버그 모드 | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 취소 URL 및 반환 URL에 대한 URL 메서드 | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 디버그 모드 | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| SFTP 자격 증명 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Pro 민감성 및 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API 사용자 이름 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 암호 | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 서명 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 인증서 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프록시 호스트 | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프록시 포트 | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 모드 | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| SFTP 자격 증명 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Pro Hosted 민감하고 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 디버그 모드 | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| SFTP 자격 증명 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Braintree 구분 및 시스템별 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Merchant ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 공개 키 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 개인 키 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 머천트 계정 ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Count Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 머천트 이름 대체 | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 전화 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 주문 경로 확인 /

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 확인 보내기 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 국제 경로

| 이름 | 구성 경로 | 상거래 전용? | 암호화됨? | 시스템별? | 민감한가? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 트랜잭션 키 | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_au/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_au/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_au/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_au/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_au/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_au/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 모드 | `payment_au/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_au/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_au/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_au/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_au/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_au/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_au/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_es/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_es/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_es/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_es/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_es/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_es/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_es/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 디버그 | `payment_es/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_es/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_es/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_es/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_es/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_es/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_es/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_es/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_nz/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_nz/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_nz/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_nz/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_nz/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_nz/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_nz/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_nz/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_nz/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 프록시 호스트 | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프록시 포트 | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 디버그 모드 | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 취소 URL 및 반환 URL에 대한 URL 메서드 | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_us/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_us/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_us/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_us/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_us/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_us/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_us/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_us/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_us/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_us/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_us/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_gb/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_gb/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_gb/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_gb/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_gb/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_gb/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_gb/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_gb/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_gb/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_de/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_de/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_de/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_de/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 트랜잭션 키 | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 결제 응답 암호 | `payment_de/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_de/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 디버그 | `payment_de/worldpay/debug` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_de/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_de/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_de/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_de/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_de/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_de/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_de/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 게이트웨이 URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 트랜잭션 키 | `payment_other/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_other/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_other/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 주문 상태 | `payment_other/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_other/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_other/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_other/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_other/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_other/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_other/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_other/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_other/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_other/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_other/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_other/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_ca/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_ca/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_ca/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 주문 상태 | `payment_ca/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 테스트 모드 | `payment_ca/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_ca/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 원격 관리자 인증 암호 | `payment_ca/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_ca/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_ca/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_ca/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_ca/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_ca/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_ca/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_ca/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_ca/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_hk/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_hk/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_hk/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_hk/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 결제 응답 암호 | `payment_hk/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_hk/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_hk/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 키 | `payment_hk/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_hk/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_hk/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_hk/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_hk/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_hk/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_jp/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_jp/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_jp/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 주문 상태 | `payment_jp/cybersource/order_status` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 테스트 모드 | `payment_jp/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_jp/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_jp/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_jp/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_jp/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_jp/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_jp/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_jp/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_jp/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_jp/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_jp/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_fr/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_fr/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_fr/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_fr/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_fr/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_fr/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_fr/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_fr/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_fr/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_fr/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_fr/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_fr/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_fr/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_fr/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 게이트웨이 URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 거래 세부 사항 URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_it/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_it/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_it/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_it/cybersource/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 결제 응답 암호 | `payment_it/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_it/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 테스트 모드 | `payment_it/worldpay/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 샌드박스 모드 | `payment_it/eway/sandbox_flag` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) |
| 라이브 API 키 | `payment_it/eway/live_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 API 암호 | `payment_it/eway/live_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 라이브 클라이언트측 암호화 키 | `payment_it/eway/live_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 키 | `payment_it/eway/sandbox_api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 API 암호 | `payment_it/eway/sandbox_api_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| 샌드박스 클라이언트측 암호화 키 | `payment_it/eway/sandbox_encryption_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 키 | `fraud_protection/signifyd/api_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  | ![시스템 특정](/help/assets/configuration/cloud-env.png) | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_au/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_au/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_es/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_es/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_es/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 |
| SFTP 자격 증명 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | !![Commerce-only]([enc] |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_nz/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_nz/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_nz/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_nz/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_nz/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_nz/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 결제 응답 암호 | `payment_nz/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_nz/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_nz/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_nz/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_us/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_us/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_us/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_us/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 결제 응답 암호 | `payment_us/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_us/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_us/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_us/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_gb/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_gb/cybersource/transaction_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_gb/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 액세스 키 | `payment_gb/cybersource/access_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 비밀 키 | `payment_gb/cybersource/secret_key` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션 키 | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_gb/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 결제 응답 암호 | `payment_gb/worldpay/response_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_gb/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 인증 암호 | `payment_gb/worldpay/auth_password` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_de/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_de/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_de/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 원격 관리자 설치 ID | `payment_de/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_de/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 주문 상태 | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_other/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_other/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_other/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_other/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_other/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 새 주문 상태 | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_ca/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_ca/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_ca/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_ca/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_ca/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_hk/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_hk/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_hk/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_hk/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_hk/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 서명 필드 | `payment_hk/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_jp/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_jp/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_jp/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |
| 원격 관리자 설치 ID | `payment_jp/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_jp/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 서명 필드 | `payment_jp/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_fr/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_fr/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_fr/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_fr/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_fr/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 서명 필드 | `payment_fr/worldpay/signature_fields` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| SFTP 자격 증명 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 수표 지급 대상 | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 확인 보내기 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| API 로그인 ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 이메일 고객 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant&#39;s Email | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_it/cybersource/merchant_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 프로필 ID | `payment_it/cybersource/profile_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) | ![암호화된](/help/assets/configuration/cloud-enc.png) |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 설치 ID | `payment_it/worldpay/installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 원격 관리자 설치 ID | `payment_it/worldpay/admin_installation_id` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |
| 트랜잭션에 대한 MD5 비밀 | `payment_it/worldpay/md5_secret` | ![상거래 전용](/help/assets/configuration/cloud-ee.png) |  |  | ![중요](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}
