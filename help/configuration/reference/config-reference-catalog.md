---
title: 카탈로그 구성 경로 참조
description: 카탈로그 구성 값 목록을 참조하십시오.
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 47bda51cdcab964c37d9f652d467d69d795d8641
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# 카탈로그 구성 경로 참조

이 섹션에는 **스토어** > 설정 > **구성** > **카탈로그**&#x200B;에서 관리자의 옵션에 사용할 수 있는 변수 이름과 구성 경로가 나열됩니다.

[`magento app:config:dump` 명령](../cli/export-configuration.md)은(는) 이러한 값을 소스 제어에 있어야 하는 공유 구성 파일 `app/etc/config.php`에 씁니다. 선택적으로 구성 설정을 무시하거나 중요한 설정을 설정하려면 [환경 변수를 사용하여 구성 설정을 무시하십시오](override-config-settings.md#environment-variables). 이 항목은 _not_&#x200B;에 [중요 및 시스템 특정 값을 나열합니다](config-reference-sens.md).

## 카탈로그 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **카탈로그**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| SKU용 마스크 | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메타 제목 마스크 | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메타 키워드에 대한 마스크 | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 메타 설명에 대한 마스크 | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 목록 모드 | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 그리드 허용 값의 페이지당 제품 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 그리드 기본값의 페이지당 제품 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 허용된 값 목록의 페이지당 제품 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 목록의 페이지당 제품 기본값 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 목록 정렬 기준 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 페이지당 모든 제품 허용 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 플랫 카탈로그 범주 사용 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 플랫 카탈로그 제품 사용 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품당 색상 견본 | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트가 리뷰를 쓰도록 허용 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 가격 변경 시 경고 허용 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 경고 이메일 템플릿 | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품이 재입고되는 경우 경고 허용 | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 스톡 경고 이메일 템플릿 | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 경고 이메일 발신자 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 시간 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 발신자 | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 템플릿 | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 현재 항목에 표시 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최근에 본 기본 제품 수 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최근에 비교한 기본 제품 수 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 비디오 자동 시작 | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 관련 비디오 표시 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 비디오 자동 다시 시작 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그 가격 범위 | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 제품 가격 | `catalog/price/default_product_price` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제품 수 표시 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 탐색 단계 계산 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 가격 탐색 단계 | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 가격 간격을 단일 가격으로 표시 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 가격 간격 수 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 간격 분할 제한 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 깊이 | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최소 쿼리 길이 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 쿼리 길이 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 검색 엔진 | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr 서버 시간 초과 | `catalog/search/solr_server_timeout` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 색인 지정 모드 | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 검색 제안 활성화 | `catalog/search/search_suggestion_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 검색 제안 수 | `catalog/search/search_suggestion_count` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 각 제안에 대한 결과 개수 표시 | `catalog/search/search_suggestion_count_results_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 검색 권장 사항 활성화 | `catalog/search/search_recommendations_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 권장 사항 수 검색 | `catalog/search/search_recommendations_count` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 각 추천에 대한 결과 개수 표시 | `catalog/search/search_recommendations_count_results_enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 일치시킬 최소 용어 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| &quot;범주/제품&quot; URL 재작성 생성 | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 인기 검색어 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 URL 접미사 | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 범주 URL 접미사 | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품 URL에 카테고리 경로 사용 | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL 키가 변경된 경우 URL에 대한 영구 리디렉션 만들기 | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 페이지 제목 구분 기호 | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 범주에 표준 링크 메타 태그 사용 | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 제품에 정식 링크 메타 태그 사용 | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사용 | `catalog/magento_catalogpermissions/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 범주 검색 허용 | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 그룹 | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 랜딩 페이지 | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 제품 가격 표시 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 그룹 | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 장바구니에 추가 허용 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 고객 그룹 | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 카탈로그 검색 허용 기준 | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 다운로드 사용을 위한 주문 항목 상태 | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 최대 다운로드 수 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 공유 가능 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 샘플 제목 | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 기본 링크 제목 | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 창에서 링크 열기 | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Disposition 사용 | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 다운로드 가능한 항목이 포함되어 있는 경우 게스트 체크아웃 비활성화 | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript 캘린더 사용 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 날짜 필드 순서 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시간 형식 | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 년 범위 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그 이벤트 기능 활성화 | `catalog/magento_catalogevent/enabled` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| Storefront에서 카탈로그 이벤트 위젯 활성화 | `catalog/magento_catalogevent/lister_output` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 이벤트 슬라이더 위젯에 표시할 이벤트 수 | `catalog/magento_catalogevent/lister_widget_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 이벤트 슬라이더 위젯에서 클릭당 스크롤할 이벤트 | `catalog/magento_catalogevent/lister_widget_scroll` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 관련 제품 목록의 최대 제품 수 | `catalog/magento_targetrule/related_position_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 관련 제품 표시 | `catalog/magento_targetrule/related_position_behavior` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 관련 제품 목록의 제품에 대한 회전 모드 | `catalog/magento_targetrule/related_rotation_mode` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 교차 판매 제품 목록의 최대 제품 수 | `catalog/magento_targetrule/crosssell_position_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 크로스셀 제품 표시 | `catalog/magento_targetrule/crosssell_position_behavior` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 교차 판매 제품 목록의 제품에 대한 회전 모드 | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 상향 판매 제품 목록의 최대 제품 수 | `catalog/magento_targetrule/upsell_position_limit` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 상향 판매 제품 표시 | `catalog/magento_targetrule/upsell_position_behavior` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 상향 판매 제품 목록의 제품에 대한 회전 모드 | `catalog/magento_targetrule/upsell_rotation_mode` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 인벤토리 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **인벤토리**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 주문 시 재고 감소 | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 주문이 취소될 경우 품목 상태를 재고로 설정 | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 품절 제품 표시 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 왼쪽 임계값만 | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront에서 재고의 제품 가용성 표시 | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 카탈로그와 동기화 | `cataloginventory/options/synchronize_with_catalog` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 재고 관리 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 미납 주문 | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 지연된 재고 업데이트 사용 | `cataloginventory/item_options/use_deferred_stock_update` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 장바구니에서 허용되는 최대 수량 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 재고 부족 임계값 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 장바구니에 허용된 최소 수량 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 아래 수량에 대해 알림 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수량 증가 활성화 | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 수량 증가 | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 대변 메모 항목을 재고로 자동 반환 | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 비동기적으로 실행 | `cataloginventory/bulk_operations/async` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 비동기 배치 크기 | `cataloginventory/bulk_operations/batch_size` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 공급자 | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 계산 모드 | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 값 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 시각적 머천다이저 경로

[!BADGE PaaS만]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce 온 클라우드 프로젝트(Adobe 관리 PaaS 인프라) 및 온프레미스 프로젝트에만 적용됩니다."}

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **시각적 머천다이저**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 범주 규칙에 대한 표시 속성 | `visualmerchandiser/options/smart_attributes` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 최소 재고 임계값 | `visualmerchandiser/options/minimum_stock_threshold` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 색상 속성 코드 | `visualmerchandiser/options/color_attribute_code` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |
| 색상 순서 | `visualmerchandiser/options/color_order` | ![Commerce 전용](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML 사이트 맵 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **XML 사이트 맵**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 빈도 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 우선순위 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 우선순위 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 사이트 맵에 이미지 추가 | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 우선순위 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 활성화됨 | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 시작 시간 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 빈도 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 발신자 | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 오류 이메일 템플릿 | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 파일당 최대 URL 수 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 파일 크기 | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Robots.txt 제출 활성화 | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS 피드 경로

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **RSS 피드**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| RSS 활성화 | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSS 활성화 | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 새 제품 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 특별 제품 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 쿠폰/할인 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최상위 수준 범주 | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 고객 주문 상태 알림 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 친구에게 이메일 보내기

이러한 구성 값은 **스토어** > 설정 > **구성** > **카탈로그** > **친구에게 전자 메일**&#x200B;의 관리자에서 사용할 수 있습니다.

| 이름 | 구성 경로 | Commerce만 해당? |
|--------------|--------------|--------------|
| 활성화됨 | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 이메일 템플릿 선택 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 게스트 허용 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 최대 수신자 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1시간 내에 전송된 최대 제품 수 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 전송 제한 기준 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
