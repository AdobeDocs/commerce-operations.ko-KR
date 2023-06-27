---
title: 다음 [!UICONTROL Indexing] 탭
description: 에 대해 알아보기 [!UICONTROL Indexing] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 다음 [!UICONTROL Indexing] 탭

다음 **[!UICONTROL Indexing]** 탭은 색인화와 관련된 문제를 설명하고 잠재적 원인을 식별하려고 합니다.

## [!UICONTROL Core index invalidated]

![코어 색인 무효화](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

다음 **[!UICONTROL Core index invalidated]** 프레임은 선택한 기간에 대한 색인화 무효화를 봅니다. 인덱싱이 다른 리소스 집약적인 작업과 동시에 발생하는 경우 [!DNL crons]따라서 사이트 리소스에 많은 부하가 걸릴 수 있습니다.

* `%Catalog Product Rule indexer has been invalidated%`) as `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) as `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) as `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) as `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) as `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) as `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) as `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) as `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) as `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) as `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) as `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) as `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) as `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![코어 색인 재빌드](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

다음 **[!UICONTROL Core index rebuilds]** 프레임은 선택한 기간에 대한 핵심 인덱스 재빌드를 봅니다. 다음은 인덱스 재구축 완료를 나타내기 위해 로그에서 구문 분석된 문자열입니다.

* `%Catalog Product Rule index has been rebuilt%`) as `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) as `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) as `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) as `category_products_idx`
* `%Customer Grid index has been rebuilt%`) as `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) as `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) as `product_categories_idx`
* `%Product EAV index has been rebuilt%`) as `product_eav_idx`
* `%Product Price index has been rebuilt%`) as `product_price_idx`
* `%Stock index has been rebuilt%`) as `stock_idx`
* `%Inventory index has been rebuilt successfully%`) as `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) as `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) as `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch 인덱스 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

다음 **[!UICONTROL catalogsearch index table(s)]** frame은 선택한 기간에 대한 catalogsearch 인덱스 테이블을 봅니다. 이 쿼리는 테이블에 대해 데이터 저장소 작업의 기간을 보고 있습니다. `%catalogsearch%` 테이블 이름.

## [!UICONTROL product index table(s)]

![제품 색인 테이블](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

다음 **[!UICONTROL product index table(s)]** 프레임은 선택한 기간 동안의 제품 인덱스 테이블을 살펴봅니다. 이 쿼리는 테이블에 대해 데이터 저장소 작업의 기간을 보고 있습니다. `%product%` 테이블 이름.
