---
title: "다음 [!UICONTROL Indexing] tab"
description: 에 대해 알아보기 [!UICONTROL Indexing] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 다음 [!UICONTROL Indexing] 탭

다음 **[!UICONTROL Indexing]** 탭에서 색인 지정 및 잠재적 원인 식별과 관련된 문제를 설명합니다.

## [!UICONTROL Core index invalidated]

![코어 인덱스가 무효화됨](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

다음 **[!UICONTROL Core index invalidated]** 프레임은 선택한 기간에 대한 색인 무효화를 확인합니다. 다른 리소스 집약적인 경우와 동시에 색인화가 발생하는 경우 [!DNL crons]를 입력하면 사이트 리소스에 많은 로드가 발생합니다.

* `%Catalog Product Rule indexer has been invalidated%`) `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![코어 인덱스 다시 빌드](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

다음 **[!UICONTROL Core index rebuilds]** 프레임은 선택한 기간에 걸쳐 코어 인덱스를 다시 만듭니다. 다음은 색인 재작성 완료를 나타내기 위해 로그에서 구문 분석되는 문자열입니다.

* `%Catalog Product Rule index has been rebuilt%`) `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) `category_products_idx`
* `%Customer Grid index has been rebuilt%`) `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) `product_categories_idx`
* `%Product EAV index has been rebuilt%`) `product_eav_idx`
* `%Product Price index has been rebuilt%`) `product_price_idx`
* `%Stock index has been rebuilt%`) `stock_idx`
* `%Inventory index has been rebuilt successfully%`) `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![카탈로그 검색 색인 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

다음 **[!UICONTROL catalogsearch index table(s)]** 프레임은 선택한 시간대에 대해 카탈로그 검색 색인 테이블을 살펴봅니다. 이 쿼리는 `%catalogsearch%` 테이블 이름에 있는 Null입니다.

## [!UICONTROL product index table(s)]

![제품 인덱스 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

다음 **[!UICONTROL product index table(s)]** 프레임은 선택한 기간에 걸쳐 제품 색인 테이블을 봅니다. 이 쿼리는 `%product%` 테이블 이름에 있는 Null입니다.
