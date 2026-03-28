---
title: 중요 및 시스템별 경로
description: Adobe Commerce의 민감하고 시스템별 구성 경로에 대해 알아봅니다. 보안 구성 및 환경 변수 관리를 살펴봅니다.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# 중요 및 시스템별 설정

이 항목에는 시스템별 및 중요 설정에 대한 구성 경로가 나열되어 있습니다.

- [`magento app:config:dump` 명령](../cli/export-configuration.md)은(는) 시스템별 구성 파일 `app/etc/env.php`에 시스템별 설정을 기록하며, 이는 소스 제어에 _해서는 안 됩니다_. 또한 모든 Commerce 인스턴스에 대한 공유 구성을 `app/etc/config.php`에 씁니다. 이 파일은 _소스 제어에 있어야_&#x200B;합니다.
- [`magento config:sensitive:set` 명령](../cli/set-configuration-values.md)이(가) 중요한 설정을 `app/etc/env.php`에 씁니다.

  [환경 변수를 사용하여 구성 설정을 재정의](../reference/override-config-settings.md#environment-variables)할 때 설명한 대로 구성 변수를 사용하여 중요한 값을 설정할 수도 있습니다.

기타 구성 경로 목록은 다음을 참조하십시오.

- [지급을 제외한 모든 구성 경로](../reference/config-reference-general.md)
- [결제 구성 경로](../reference/config-reference-payment.md).

>[!INFO]
>
>이 항목에 나열된 모든 구성 경로는 중요합니다. `System-specific?` 열에는 시스템별로 다른 값도 표시됩니다.

## 일반 범주 구분 및 시스템별 경로

이 섹션에는 **스토어** > 설정 > **구성** > **일반**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 웹 경로 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **일반** > **웹**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 기본 URL | `web/unsecure/base_url` |  | | 시스템별 | |
| 기본 링크 URL | `web/unsecure/base_link_url` |  | | 시스템별 | |
| 정적 보기 파일의 기본 URL | `web/unsecure/base_static_url` |  | | 시스템별 | |
| 사용자 미디어 파일의 기본 URL | `web/unsecure/base_media_url` |  | | 시스템별 | |
| Secure Base URL | `web/secure/base_url` |  | | 시스템별 | |
| Secure Base 링크 URL | `web/secure/base_link_url` |  | | 시스템별 | |
| 정적 보기 파일에 대한 보안 기본 URL | `web/secure/base_static_url` |  | | 시스템별 | |
| 사용자 미디어 파일용 Secure Base URL | `web/secure/base_media_url` |  | | 시스템별 | |
| 기본 웹 URL | `web/default/front` |  | | 시스템별 | |
| 기본 경로 없음 URL | `web/default/no_route` |  | | 시스템별 | |
| 쿠키 경로 | `web/cookie/cookie_path` |  | | 시스템별 | |
| 쿠키 도메인 | `web/cookie/cookie_domain` |  | | 시스템별 | |
| 쿠키 수명 | `web/cookie/cookie_lifetime` |  | | 시스템별 | |
| HTTP만 사용 | `web/cookie/cookie_httponly` |  | | 시스템별 | |
| 쿠키 제한 모드 | `web/cookie/cookie_restriction` |  | | 시스템별 | |

{style="table-layout:auto"}

### 통화 설정 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **일반** > **통화 설정**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
| --- | --- | --- | --- | --- | --- |
| 오류 이메일 수신자 | `currency/import/error_email` |  | | | 중요 |

{style="table-layout:auto"}

### 이메일 주소 구분 및 시스템별 경로 저장

이러한 구성 값은 **스토어** > 설정 > **이메일 구성** > **일반** > **이메일 주소 저장**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 보낸 사람 이름 | `trans_email/ident_general/name` | | | | 중요 |
| 보낸 사람 이메일 | `trans_email/ident_general/email` |  | | | 중요 |
| 보낸 사람 이름 | `trans_email/ident_sales/name` |  | | | 중요 |
| 보낸 사람 이메일 | `trans_email/ident_sales/email` |  | | | 중요 |
| 보낸 사람 이름 | `trans_email/ident_support/name` |  | | | 중요 |
| 보낸 사람 이메일 | `trans_email/ident_support/email` |  | | | 중요 |
| 보낸 사람 이름 | `trans_email/ident_custom1/name` |  | | | 중요 |
| 보낸 사람 이메일 | `trans_email/ident_custom1/email` |  | | | 중요 |
| 보낸 사람 이름 | `trans_email/ident_custom2/name` |  | | | 중요 |
| 보낸 사람 이메일 | `trans_email/ident_custom2/email` |  | | | 중요 |

{style="table-layout:auto"}

### 연락처 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **일반** > **연락처**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 이메일 발송 대상 | `contact/email/recipient_email` |  | | | 중요 |
| 이메일 발신자 | `contact/email/sender_email_identity` |  | | | 중요 |
| 이메일 템플릿 | `contact/email/email_template` |  | | | 중요 |

{style="table-layout:auto"}

### New Relic 보고 중요 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **일반** > **New Relic 보고**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic 계정 ID | `newrelicreporting/general/account_id` |  | | | 중요 |
| New Relic 애플리케이션 ID | `newrelicreporting/general/app_id` |  | | | 중요 |
| New Relic API 키 | `newrelicreporting/general/api` |  | 암호화됨 | | 중요 |
| Insights API 키 | `newrelicreporting/general/insights_insert_key` |  | 암호화됨 | | 중요 |
| NEW RELIC API URL | `newrelicreporting/general/api_url` |  | | 시스템별 | 중요 |
| Insights API URL | `newrelicreporting/general/insights_api_url` |  | | 시스템별 | 중요 |

{style="table-layout:auto"}

## 고객 범주 구분 및 시스템별 경로

이 섹션에는 **스토어** > 설정 > **구성** > **고객**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 고객 구성 관련 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고객** > **고객 구성**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 기본 이메일 도메인 | `customer/create_account/email_domain` |  | | 시스템별 | |

{style="table-layout:auto"}

## 카탈로그 범주

이 섹션에는 **스토어** > 설정 > **구성** > **카탈로그**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 카탈로그 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **카탈로그**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `catalog/productalert_cron/error_email` |  | | | 중요 |
| YouTube API 키 | `catalog/product_video/youtube_api_key` |  | | | 중요 |
| Solr 서버 호스트 이름 | `catalog/search/solr_server_hostname` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| Solr 서버 포트 | `catalog/search/solr_server_port` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| Solr 서버 사용자 이름 | `catalog/search/solr_server_username` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| Solr 서버 암호 | `catalog/search/solr_server_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| Solr 서버 경로 | `catalog/search/solr_server_path` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| Elasticsearch 서버 호스트 이름 | `catalog/search/elasticsearch_server_hostname` |  | | 시스템별 | 중요 |
| Elasticsearch 서버 포트 | `catalog/search/elasticsearch_server_port` |  | | 시스템별 | 중요 |
| Elasticsearch 색인 접두사 | `catalog/search/elasticsearch_index_prefix` |  | | 시스템별 | 중요 |
| Elasticsearch HTTP 인증 활성화 | `catalog/search/elasticsearch_enable_auth` |  | | 시스템별 | |
| Elasticsearch HTTP 사용자 이름 | `catalog/search/elasticsearch_username` |  | | 시스템별 | |
| Elasticsearch HTTP 암호 | `catalog/search/elasticsearch_password` |  | | 시스템별 | |
| Elasticsearch 서버 시간 초과 | `catalog/search/elasticsearch_server_timeout` |  | | 시스템별 | |
| Elasticsearch HTTP 사용자 이름 | `catalog/search/elasticsearch_username` | | | 시스템별 | |
| Elasticsearch HTTP 암호 | `catalog/search/elasticsearch_password` | | | 시스템별 | |
| Elasticsearch 서버 시간 초과 | `catalog/search/elasticsearch_server_timeout` | | | 시스템별 | |
| OpenSearch 서버 호스트 이름 | `catalog/search/opensearch_server_hostname` | | | 시스템별 | 중요 |
| OpenSearch 서버 포트 | `catalog/search/opensearch_server_port` | | | 시스템별 | 중요 |
| OpenSearch 색인 접두사 | `catalog/search/opensearch_index_prefix` | | | 시스템별 | 중요 |
| OpenSearch HTTP 인증 활성화 | `catalog/search/opensearch_enable_auth` | | | 시스템별 | |
| OpenSearch HTTP 사용자 이름 | `catalog/search/opensearch_username` | | | 시스템별 | |
| OpenSearch HTTP 암호 | `catalog/search/opensearch_password` | | | 시스템별 | |
| OpenSearch 서버 시간 초과 | `catalog/search/opensearch_server_timeout` | | | 시스템별 | |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearch 설정은 Adobe Commerce 2.4.6에서 도입되었습니다.

### 인벤토리 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **인벤토리**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원| 암호화되었습니까? | 시스템별? | 중요? | |
------------------------------------------ ----------------------------
| Google API 키 | `cataloginventory/source_selection_distance_based_google/api_key` | | 암호화됨 | 중요 |

### XML 사이트 맵 중요 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **XML 사이트 맵**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `sitemap/generate/error_email` |  | | | 중요 |

{style="table-layout:auto"}

## 판매 범주

이 섹션에는 **스토어** > 설정 > **구성** > **판매**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 배송 설정 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **배송 설정**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 국가 | `shipping/origin/country_id` |  | | | 중요 |
| 지역/주 | `shipping/origin/region_id` |  | | | 중요 |
| ZIP/우편 번호 | `shipping/origin/postcode` |  | | | 중요 |
| 도시 | `shipping/origin/city` |  | | | 중요 |
| 상세 주소 | `shipping/origin/street_line1` |  | | | 중요 |
| 상세 주소 2 | `shipping/origin/street_line2` |  | | | 중요 |
| 라이브 계정 | `carriers/ups/is_account_live` |  | | 시스템별 | |

{style="table-layout:auto"}

### 영업 이메일 민감성 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **판매 이메일**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 주문 이메일 사본 발송 대상 | `sales_email/order/copy_to` |  | | | 중요 |
| 주문 주석 이메일 사본 보내기 대상 | `sales_email/order_comment/copy_to` |  | | | 중요 |
| 다음으로 인보이스 이메일 사본 보내기 | `sales_email/invoice/copy_to` |  | | | 중요 |
| 다음 대상에게 송장 주석 이메일 사본 보내기 | `sales_email/invoice_comment/copy_to` |  | | | 중요 |
| 다음으로 배송 이메일 사본 보내기 | `sales_email/shipment/copy_to` |  | | | 중요 |
| 다음 대상에게 배송 댓글 이메일 사본 보내기: | `sales_email/shipment_comment/copy_to` |  | | | 중요 |
| 다음 대상에게 대변 메모 이메일 사본 보내기 | `sales_email/creditmemo/copy_to` |  | | | 중요 |
| 다음 대상에게 대변 메모 주석 이메일 사본 보내기 | `sales_email/creditmemo_comment/copy_to` |  | | | 중요 |
| (으)로 픽업 준비 이메일 사본 보내기 | `sales_email/temando_pickup/copy_to` |  | | | 중요 |

{style="table-layout:auto"}

### 중요 및 시스템별 경로 체크아웃

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **체크아웃**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 다음 대상에게 결제 실패 이메일 사본 보내기 | `checkout/payment_failed/copy_to` |  | | | 중요 |

{style="table-layout:auto"}

### Google API 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **Google API**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 컨테이너 ID | `google/analytics/container_id` | Commerce Enterprise 전용 | | | 중요 |

{style="table-layout:auto"}

### 전달 방법 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **게재 방법**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 게이트웨이 URL | `carriers/usps/gateway_url` |  | | | 중요 |
| 보안 게이트웨이 URL | `carriers/usps/gateway_secure_url` |  | | | 중요 |
| 제목 | `carriers/usps/title` |  | | | |
| 사용자 ID | `carriers/usps/userid` |  | 암호화됨 | | 중요 |
| 암호 | `carriers/usps/password` |  | 암호화됨 | | 중요 |
| 사용자 ID | `carriers/ups/username` |  | 암호화됨 | | 중요 |
| 암호 | `carriers/ups/password` |  | 암호화됨 | | 중요 |
| 액세스 라이선스 번호 | `carriers/ups/access_license_number` |  | 암호화됨 | | 중요 |
| 추적 XML URL | `carriers/ups/tracking_xml_url` |  | | | 중요 |
| 게이트웨이 XML URL | `carriers/ups/gateway_xml_url` |  | | | 중요 |
| 배송자 번호 | `carriers/ups/shipper_number` |  | | | 중요 |
| 디버그 | `carriers/ups/debug` |  | | | 중요 |
| 계정 ID | `carriers/fedex/account` |  | 암호화됨 | | 중요 |
| 키 | `carriers/fedex/key` |  | 암호화됨 | | 중요 |
| 미터 번호 | `carriers/fedex/meter_number` |  | 암호화됨 | | 중요 |
| 암호 | `carriers/fedex/password` |  | 암호화됨 | | 중요 |
| 액세스 ID | `carriers/dhl/id` |  | 암호화됨 | | 중요 |
| 암호 | `carriers/dhl/password` |  | 암호화됨 | | 중요 |
| 디버그 | `carriers/dhl/debug` |  | | | |
| 계정 번호 | `carriers/dhl/account` |  | | | 중요 |
| 게이트웨이 URL | `carriers/dhl/gateway_url` |  | | | 중요 |
| 샌드박스 모드 | `carriers/fedex/sandbox_mode` |  | | | 중요 |

{style="table-layout:auto"}

### 영업에 민감한 시스템 특정 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **판매**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 연락처 이름 | `sales/magento_rma/store_name` | Commerce Enterprise 전용 | | | 중요 |
| 상세 주소 | `sales/magento_rma/address` | Commerce Enterprise 전용 | | | 중요 |
| 상세 주소 | `sales/magento_rma/address1` |  | | | 중요 |
| 도시 | `sales/magento_rma/city` | Commerce Enterprise 전용 | | | 중요 |
| 시/도 | `sales/magento_rma/region_id` | Commerce Enterprise 전용 | | | 중요 |
| ZIP/우편 번호 | `sales/magento_rma/zip` | Commerce Enterprise 전용 | | | 중요 |
| 국가 | `sales/magento_rma/country_id` | Commerce Enterprise 전용 | | | 중요 |
| RMA 전자 메일 사본 보내기 대상 | `sales_email/magento_rma/copy_to` | Commerce Enterprise 전용 | | | 중요 |
| RMA 인증 전자 메일 사본 보내기 대상 | `sales_email/magento_rma_auth/copy_to` | Commerce Enterprise 전용 | | | 중요 |
| RMA 주석 이메일 사본 보내기 대상 | `sales_email/magento_rma_comment/copy_to` | Commerce Enterprise 전용 | | | 중요 |
| RMA 주석 이메일 사본 보내기 대상 | `sales_email/magento_rma_customer_comment/copy_to` | Commerce Enterprise 전용 | | | 중요 |

{style="table-layout:auto"}

### Google API 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **판매** > **Google API**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 계정 번호 | `google/analytics/account` |  | | | 중요 |

{style="table-layout:auto"}

## 고급 범주

이 섹션에는 **스토어** > 설정 > **구성** > **고급**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 관리자 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고급** > **관리자**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 지정 관리자 URL | `admin/url/custom` |  | | | 중요 |
| 사용자 지정 관리자 경로 | `admin/url/custom_path` |  | | | 중요 |

{style="table-layout:auto"}

### 시스템 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고급** > **시스템**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 오류 이메일 수신자 | `system/magento_scheduled_import_export_log/error_email` |  | | | 중요 |
| 액세스 목록 | `system/full_page_cache/varnish/access_list` |  |  | | 중요 |
| 오류 이메일 발신자 | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | 중요 |

{style="table-layout:auto"}

### 개발자 구분 및 시스템별 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고급** > **개발자**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 허용된 IP(쉼표로 구분) | `dev/restrict/allow_ips` |  | | 시스템별 | 중요 |

{style="table-layout:auto"}

## 고급 범주

이 섹션에는 **스토어** > 설정 > **구성** > **고급**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 시스템 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고급** > **시스템**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 호스트 | `system/smtp/host` |  | | 시스템별 | 중요 |
| 포트 (25) | `system/smtp/port` |  | | 시스템별 | 중요 |
| 백엔드 호스트 | `system/full_page_cache/varnish/backend_host` |  | | 시스템별 | 중요 |
| 백엔드 포트 | `system/full_page_cache/varnish/backend_port` |  | | 시스템별 | 중요 |

{style="table-layout:auto"}

### 개발자 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **고급** > **개발자**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 세션 저장소 키에 JS 오류 기록 | `dev/js/session_storage_key` | ![Commerce 전용 아님](/help/assets/configuration/red-x.png) | | 시스템별 | |

{style="table-layout:auto"}

## 결제 구분 및 시스템별 경로

이 섹션에는 **스토어** > 설정 > **구성** > **판매** > **결제**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

### 일반 변수

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? |
|--------------|--------------|--------------|--------------|
| 판매국 | `paypal/general/merchant_country` |  | 중요 |

{style="table-layout:auto"}

>[!INFO]
>
>이 변수에 대한 선택 사항에 따라 사용할 수 있는 [국제 경로](#international-paths)가 결정됩니다.

### PayPal 구분 및 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| PayPal 판매자 계정과 연결된 이메일(선택 사항) | `paypal/general/business_account` |  | | | 중요 |
| 판매자 계정 ID | `payment/paypal_express/merchant_id` |  | | | 중요 |
| 게시자 ID | `payment/paypal_express_bml/publisher_id` |  | | | 중요 |
| 암호 | `paypal/fetch_reports/ftp_password` |  | 암호화됨 | | 중요 |
| 로그인 | `paypal/fetch_reports/ftp_login` |  | 암호화됨 | | 중요 |
| 사용자 지정 끝점 호스트 이름 또는 IP 주소 | `paypal/fetch_reports/ftp_ip` |  | | 시스템별 | 중요 |
| 샌드박스 모드 | `paypal/fetch_reports/ftp_sandbox` |  | | 시스템별 | |
| 디버그 모드 | `payment/paypal_express/debug` |  | | 시스템별 | |
| 디버그 모드 | `payment/paypal_billing_agreement/debug` |  | | 시스템별 | |
| SFTP 자격 증명 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |

{style="table-layout:auto"}

### PayPal Payflow Pro 민감하고 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 | `payment/payflow_advanced/user` |  | 암호화됨 | | 중요 |
| 암호 | `payment/payflow_advanced/pwd` |  | 암호화됨 | | 중요 |
| 사용자 지정 경로 | `paypal/fetch_reports/ftp_path` |  | | 시스템별 | 중요 |
| 사용자 | `payment/payflowpro/user` |  | 암호화됨 | | 중요 |
| 암호 | `payment/payflowpro/pwd` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment/payflowpro/sandbox_flag` |  | | 시스템별 | |
| 파트너 | `payment/payflowpro/partner` |  | | | 중요 |
| 프록시 호스트 | `payment/payflowpro/proxy_host` |  | | 시스템별 | 중요 |
| 프록시 포트 | `payment/payflowpro/proxy_port` |  | | 시스템별 | 중요 |
| 디버그 모드 | `payment/payflowpro/debug` |  | | 시스템별 | |
| SFTP 자격 증명 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | 시스템별 | |
| 신용 카드 설정 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | 중요 |

{style="table-layout:auto"}

### PayPal Payflow Link 중요 및 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 사용자 | `payment/payflow_link/user` |  | 암호화됨 | | 중요 |
| 암호 | `payment/payflow_link/pwd` |  | 암호화됨 | | 중요 |
| 테스트 모드 | `payment/payflow_link/sandbox_flag` |  | | 시스템별 | |
| 프록시 사용 | `payment/payflow_link/use_proxy` |  | | 시스템별 | |
| 프록시 호스트 | `payment/payflow_link/proxy_host` |  | | 시스템별 | |
| 프록시 포트 | `payment/payflow_link/proxy_port` |  |  | 시스템별 | |
| 디버그 모드 | `payment/payflow_link/debug` |  | | 시스템별 | |
| URL 취소 및 URL 반환에 대한 URL 메서드 | `payment/payflow_link/url_method` |  | | 시스템별 | |
| 디버그 모드 | `payment/payflow_express/debug` |  | | 시스템별 | |
| SFTP 자격 증명 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 중요 |

{style="table-layout:auto"}

### PayPal 결제 Pro 민감성 및 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API 사용자 이름 | `paypal/wpp/api_username` |  | 암호화됨 | | 중요 |
| API 암호 | `paypal/wpp/api_password` |  | 암호화됨 | | 중요 |
| API 서명 | `paypal/wpp/api_signature` |  | 암호화됨 | | 중요 |
| API 인증서 | `paypal/wpp/api_cert` |  | | | 중요 |
| 프록시 호스트 | `paypal/wpp/proxy_host` |  | | 시스템별 | 중요 |
| 프록시 포트 | `paypal/wpp/proxy_port` |  | | 시스템별 | 중요 |
| 샌드박스 모드 | `paypal/wpp/sandbox_flag` |  | | 시스템별 | |
| SFTP 자격 증명 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |

{style="table-layout:auto"}

### PayPal Payments Pro 호스팅되는 민감하고 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 디버그 모드 | `payment/hosted_pro/debug` |  | | 시스템별 | |
| SFTP 자격 증명 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |

{style="table-layout:auto"}

### Braintree 구분 및 시스템별 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 판매자 ID | `payment/braintree/merchant_id` |  | | | 중요 |
| 공개 키 | `payment/braintree/public_key` |  | 암호화됨 | | 중요 |
| 개인 키 | `payment/braintree/private_key` |  | 암호화됨 | | 중요 |
| 판매자 계정 ID | `payment/braintree/merchant_account_id` |  | | | 중요 |
| 비용 판매자 ID | `payment/braintree/kount_id` |  | | | 중요 |
| 판매자 이름 재정의 | `payment/braintree_paypal/merchant_name_override` |  | | | 중요 |
| 전화 | `payment/braintree/descriptor_phone` |  | | | 중요 |
| URL | `payment/braintree/descriptor_url` |  | | 시스템별 | |

{style="table-layout:auto"}

### 주문 경로 확인 / 금액

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 수표 발송 대상 | `payment/checkmo/mailing_address` |  | | | 중요 |
| 수표 발송 대상 | `payment_us/checkmo/mailing_address` |  | | | 중요 |

{style="table-layout:auto"}

### 국제 경로

| 이름 | 구성 경로 | Commerce 버전 지원 | 암호화되었습니까? | 시스템별? | 민감한? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 거래 키 | `payment_au/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_au/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_au/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_au/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_au/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_au/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_au/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_au/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_au/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_au/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 샌드박스 모드 | `payment_au/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_au/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_au/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_au/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_au/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_au/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_au/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_es/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_es/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_es/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_es/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_es/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_es/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_es/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_es/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_es/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_es/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 거래를 위한 MD5 암호 | `payment_es/worldpay/md5_secret` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 디버그 | `payment_es/worldpay/debug` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_es/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_es/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_es/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_es/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_es/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_es/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_es/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_nz/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_nz/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_nz/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 테스트 모드 | `payment_nz/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 테스트 모드 | `payment_nz/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_nz/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_nz/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_nz/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_nz/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_nz/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 샌드박스 API 암호 | `payment_nz/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_nz/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment/payflow_advanced/sandbox_flag` |  | | 시스템별 | |
| 프록시 호스트 | `payment/payflow_advanced/proxy_host` |  | | 시스템별 | 중요 |
| 프록시 포트 | `payment/payflow_advanced/proxy_port` |  | | 시스템별 | |
| 디버그 모드 | `payment/payflow_advanced/debug` |  | | 시스템별 | |
| URL 취소 및 URL 반환에 대한 URL 메서드 | `payment/payflow_advanced/url_method` |  | | 시스템별 | |
| 테스트 모드 | `payment_us/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_us/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_us/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 액세스 키 | `payment_us/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_us/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_us/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 테스트 모드 | `payment_us/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_us/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_us/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_us/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_us/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_us/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_us/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_us/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | |
| 테스트 모드 | `payment_gb/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 테스트 모드 | `payment_gb/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_gb/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 테스트 모드 | `payment_gb/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_gb/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_gb/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_gb/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_gb/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_gb/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_gb/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_gb/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_de/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_de/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_de/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_de/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 거래 키 | `payment_de/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_de/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_de/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_de/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 결제 응답 암호 | `payment_de/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_de/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 디버그 | `payment_de/worldpay/debug` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_de/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_de/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_de/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_de/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_de/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_de/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_de/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_other/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_other/authorizenet_directpost/test` |  | | 시스템별 | 중요 |
| 게이트웨이 URL | `payment_other/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_other/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | |
| 거래 키 | `payment_other/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_other/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_other/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 새 주문 상태 | `payment_other/cybersource/order_status` | Commerce Enterprise 전용 | | 시스템별 | |
| 테스트 모드 | `payment_other/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_other/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_other/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_other/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_other/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_other/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_other/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_other/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_other/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_other/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_other/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_ca/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_ca/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_ca/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_ca/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_ca/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_ca/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 새 주문 상태 | `payment_ca/cybersource/order_status` | Commerce Enterprise 전용 | | | |
| 테스트 모드 | `payment_ca/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_ca/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | |
| 원격 관리자 인증 암호 | `payment_ca/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_ca/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_ca/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_ca/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_ca/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_ca/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_ca/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 샌드박스 API 암호 | `payment_ca/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_ca/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_hk/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_hk/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_hk/authorizenet_directpost/cgi_url` |  | | | 중요 |
| 거래 세부 정보 URL | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_hk/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_hk/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_hk/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_hk/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 결제 응답 암호 | `payment_hk/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_hk/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_hk/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 라이브 API 키 | `payment_hk/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 라이브 API 암호 | `payment_hk/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_hk/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_hk/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_hk/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_hk/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_jp/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_jp/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_jp/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_jp/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_jp/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_jp/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 새 주문 상태 | `payment_jp/cybersource/order_status` | Commerce Enterprise 전용 | | 시스템별 | |
| 테스트 모드 | `payment_jp/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_jp/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_jp/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_jp/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_jp/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_jp/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_jp/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_jp/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_jp/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_jp/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_jp/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_fr/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_fr/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_fr/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_fr/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_fr/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_fr/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_fr/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_fr/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_fr/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_fr/worldpay/sandbox_flag` | Commerce Enterprise 전용 |  | 시스템별 | |
| 샌드박스 모드 | `payment_fr/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_fr/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_fr/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_fr/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_fr/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_fr/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_fr/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 거래 키 | `payment_it/authorizenet_directpost/trans_key` |  | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_it/authorizenet_directpost/test` |  | | 시스템별 | |
| 게이트웨이 URL | `payment_it/authorizenet_directpost/cgi_url` |  | | 시스템별 | 중요 |
| 거래 세부 정보 URL | `payment_it/authorizenet_directpost/cgi_url_td` |  | | 시스템별 | 중요 |
| 거래 키 | `payment_it/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 액세스 키 | `payment_it/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 비밀 키 | `payment_it/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 테스트 모드 | `payment_it/cybersource/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 결제 응답 암호 | `payment_it/worldpay/response_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 원격 관리자 인증 암호 | `payment_it/worldpay/auth_password` | Commerce Enterprise 전용 | | 시스템별 | 중요 |
| 테스트 모드 | `payment_it/worldpay/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 샌드박스 모드 | `payment_it/eway/sandbox_flag` | Commerce Enterprise 전용 | | 시스템별 | |
| 라이브 API 키 | `payment_it/eway/live_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 API 암호 | `payment_it/eway/live_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 라이브 클라이언트측 암호화 키 | `payment_it/eway/live_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 키 | `payment_it/eway/sandbox_api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 API 암호 | `payment_it/eway/sandbox_api_password` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| 샌드박스 클라이언트측 암호화 키 | `payment_it/eway/sandbox_encryption_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| API 키 | `fraud_protection/signifyd/api_key` | Commerce Enterprise 전용 | 암호화됨 | 시스템별 | 중요 |
| API URL | `fraud_protection/signifyd/api_url` | Commerce Enterprise 전용 |  | 시스템별 | 중요 |
| SFTP 자격 증명 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| API 로그인 ID | `payment_au/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_au/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_au/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 원격 관리자 설치 ID | `payment_au/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_au/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 발송 대상 | `payment_es/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_es/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_es/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_es/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_es/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_es/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 원격 관리자 설치 ID | `payment_es/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | | | | | |
| SFTP 자격 증명 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| API 로그인 ID | `payment_nz/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_nz/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_nz/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_nz/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 거래 키 | `payment_nz/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_nz/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 액세스 키 | `payment_nz/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 비밀 키 | `payment_nz/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_nz/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 결제 응답 암호 | `payment_nz/worldpay/response_password` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_nz/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 인증 암호 | `payment_nz/worldpay/auth_password` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_nz/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 중요 |
| API 로그인 ID | `payment_us/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 거래 키 | `payment_us/authorizenet_directpost/trans_key` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_us/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_us/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_us/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 거래 키 | `payment_us/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_us/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_us/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 결제 응답 암호 | `payment_us/worldpay/response_password` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_us/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 인증 암호 | `payment_us/worldpay/auth_password` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_us/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 중요 |
| SFTP 자격 증명 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 발송 대상 | `payment_gb/checkmo/mailing_address` |  | | | 중요 |
| 판매자 ID | `payment_gb/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 거래 키 | `payment_gb/cybersource/transaction_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_gb/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 액세스 키 | `payment_gb/cybersource/access_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 비밀 키 | `payment_gb/cybersource/secret_key` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| API 로그인 ID | `payment_gb/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 거래 키 | `payment_gb/authorizenet_directpost/trans_key` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_gb/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | 중요 |
| 설치 ID | `payment_gb/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 결제 응답 암호 | `payment_gb/worldpay/response_password` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_gb/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 인증 암호 | `payment_gb/worldpay/auth_password` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_de/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_de/checkmo/mailing_address` |  | | | 중요 |
| 판매자 ID | `payment_de/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_de/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| API 로그인 ID | `payment_de/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_de/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_de/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 설치 ID | `payment_de/worldpay/installation_id` | Commerce Enterprise 전용 | | | |
| 원격 관리자 설치 ID | `payment_de/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_de/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 중요 |
| SFTP 자격 증명 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_other/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_other/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_other/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 새 주문 상태 | `payment_other/authorizenet_directpost/order_status` |  | | | 중요 |
| 판매자 전자 메일 | `payment_other/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_other/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_other/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_other/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_other/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_other/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_ca/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_ca/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_ca/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 새 주문 상태 | `payment_ca/authorizenet_directpost/order_status` |  | | | 중요 |
| 이메일 고객 | `payment_ca/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_ca/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_ca/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_ca/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_ca/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_ca/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_ca/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | 중요 |
| SFTP 자격 증명 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_hk/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_hk/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_hk/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_hk/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_hk/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_hk/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_hk/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_hk/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_hk/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_hk/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| 서명 필드 | `payment_hk/worldpay/signature_fields` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_jp/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_jp/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_jp/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_jp/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_jp/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_jp/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_jp/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_jp/worldpay/installation_id` | Commerce Enterprise 전용 | | | |
| 원격 관리자 설치 ID | `payment_jp/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_jp/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| 서명 필드 | `payment_jp/worldpay/signature_fields` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_fr/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_fr/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_fr/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_fr/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_fr/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_fr/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_fr/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_fr/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_fr/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_fr/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |
| 서명 필드 | `payment_fr/worldpay/signature_fields` | Commerce Enterprise 전용 | | | 중요 |
| SFTP 자격 증명 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 중요 |
| SFTP 자격 증명 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 중요 |
| 수표 지급 대상 | `payment_it/checkmo/payable_to` |  | | | 중요 |
| 수표 발송 대상 | `payment_it/checkmo/mailing_address` |  | | | 중요 |
| API 로그인 ID | `payment_it/authorizenet_directpost/login` |  | 암호화됨 | | 중요 |
| 판매자 MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | 암호화됨 | | 중요 |
| 이메일 고객 | `payment_it/authorizenet_directpost/email_customer` |  | | | 중요 |
| 판매자 전자 메일 | `payment_it/authorizenet_directpost/merchant_email` |  | | | 중요 |
| 판매자 ID | `payment_it/cybersource/merchant_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 프로필 ID | `payment_it/cybersource/profile_id` | Commerce Enterprise 전용 | 암호화됨 | | 중요 |
| 설치 ID | `payment_it/worldpay/installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 원격 관리자 설치 ID | `payment_it/worldpay/admin_installation_id` | Commerce Enterprise 전용 | | | 중요 |
| 거래를 위한 MD5 암호 | `payment_it/worldpay/md5_secret` | Commerce Enterprise 전용 | | | 중요 |

{style="table-layout:auto"}
