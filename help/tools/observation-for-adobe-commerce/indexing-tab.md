---
title: '[!UICONTROL Indexing] 탭'
description: '[!UICONTROL Indexing]의  [!DNL Observation for Adobe Commerce] 탭에 대해 알아봅니다.'
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# [!UICONTROL Indexing] 탭

**[!UICONTROL Indexing]** 탭은 인덱싱과 관련된 문제를 설명하고 잠재적 원인을 식별하려고 합니다.

## [!UICONTROL Core index invalidated]

![코어 인덱스가 무효화됨](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

**[!UICONTROL Core index invalidated]** 프레임은 선택한 기간에 대한 인덱싱 무효화를 살펴봅니다. 리소스 집약적인 다른 [!DNL crons]과(와) 동시에 인덱싱이 발생하면 사이트 리소스에 많은 부하가 걸립니다.

* `%Catalog Product Rule indexer has been invalidated%`(으)로 `catalog_product_rule_idx_reset`)
* `%Catalog Rule Product indexer has been invalidated%`(으)로 `catalog_rule_product_idx_reset`)
* `%Catalog Search indexer has been invalidated%`(으)로 `catalog_search_idx_reset`)
* `%Category Products indexer has been invalidated%`(으)로 `category_products_idx_reset`)
* `%Customer Grid indexer has been invalidated%`(으)로 `customer_grid_idx_reset`)
* `%Design Config Grid indexer has been invalidated%`(으)로 `design_config_grid_idx_`)
* `%Product Categories indexer has been invalidated%`(으)로 `product_categories_idx_reset`)
* `%Product EAV indexer has been invalidated%`(으)로 `product_eav_idx_reset`)
* `%Product Price indexer has been invalidated%`(으)로 `product_price_idx_reset`)
* `%Stock indexer has been invalidated%`(으)로 `stock_idx_reset`)
* `%Inventory indexer has been invalidated%`(으)로 `inventory_idx_reset`)
* `%Inventory indexer has been invalidated%`(으)로 `inventory_idx_reset`)
* `%Sales Rule indexer has been invalidated%`(으)로 `sales_rule_idx_reset`)

## [!UICONTROL Core index rebuilds]

![코어 인덱스 다시 빌드](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

**[!UICONTROL Core index rebuilds]** 프레임은 선택한 기간 동안 핵심 인덱스 다시 빌드를 봅니다. 다음은 인덱스 재구축 완료를 나타내기 위해 로그에서 구문 분석된 문자열입니다.

* `%Catalog Product Rule index has been rebuilt%`(으)로 `catalog_product_rule_idx`)
* `%Catalog Rule Product index has been rebuilt%`(으)로 `catalog_rule_product_idx`)
* `%Catalog Search index has been rebuilt%`(으)로 `catalog_search_idx`)
* `%Category Products index has been rebuilt successfully%`(으)로 `category_products_idx`)
* `%Customer Grid index has been rebuilt%`(으)로 `customer_grid_idx`)
* `%Design Config Grid index has been rebuilt%`(으)로 `design_config_grid_idx`)
* `%Product Categories index has been rebuilt%`(으)로 `product_categories_idx`)
* `%Product EAV index has been rebuilt%`(으)로 `product_eav_idx`)
* `%Product Price index has been rebuilt%`(으)로 `product_price_idx`)
* `%Stock index has been rebuilt%`(으)로 `stock_idx`)
* `%Inventory index has been rebuilt successfully%`(으)로 `inventory_idx`)
* `%Product/Target Rule index has been rebuilt successfully%`(으)로 `prod_target_rule_idx`)
* `%Sales Rule index has been rebuilt successfully%`(으)로 `sales_rule_idx`)


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch 인덱스 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

**[!UICONTROL catalogsearch index table(s)]** 프레임은 선택한 기간 동안 catalogsearch 인덱스 테이블을 봅니다. 이 쿼리는 테이블 이름에 `%catalogsearch%`이(가) 있는 테이블에 대한 데이터 저장소 작업의 기간을 보고 있습니다.

## [!UICONTROL product index table(s)]

![제품 인덱스 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

**[!UICONTROL product index table(s)]** 프레임은 선택한 기간 동안 제품 인덱스 테이블을 봅니다. 이 쿼리는 테이블 이름에 `%product%`이(가) 있는 테이블에 대한 데이터 저장소 작업의 기간을 보고 있습니다.
