---
title: 인덱서 관리
description: 상거래 인덱스를 보고 관리하는 방법에 대한 예를 참조하십시오.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 795d4e9d1910d0ad826eb6c82ac451ac58e43063
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---

# 인덱서 관리

{{file-system-owner}}

모든 인덱서 목록을 보려면 다음을 수행합니다.

```bash
bin/magento indexer:info
```

목록이 다음과 같이 표시됩니다.

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> 라이브 검색, 카탈로그 서비스 또는 제품 Recommendations을 사용하는 Adobe Commerce 가맹점은 [SaaS 기반의 가격 인덱싱](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## 인덱서 상태 보기

모든 인덱서 또는 특정 인덱서의 상태를 보려면 이 명령을 사용합니다. 예를 들어 색인을 다시 인덱싱해야 하는지 확인합니다.

명령 옵션:

```bash
bin/magento indexer:status [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서의 상태를 확인합니다.

샘플 결과:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## 다시 색인화

이 명령을 사용하여 모든 또는 선택한 인덱서를 한 번만 다시 색인화합니다.

>[!INFO]
>
>이 명령은 한 번만 다시 인덱싱합니다. 인덱스를 최신 상태로 유지하려면 [cron 작업](../cli/configure-cron-jobs.md).

명령 옵션:

```bash
bin/magento indexer:reindex [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서를 다시 색인화합니다.

샘플 결과:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>모든 인덱서를 재색인화하는 데 많은 제품, 고객, 카테고리 및 프로모션 규칙이 있는 저장소에 시간이 오래 걸릴 수 있습니다.

### 병렬 모드에서 재인덱싱

인덱서 범위가 지정되고 다중 스레드되어 병렬 모드에서 재색인화를 지원합니다. 인덱서의 차원으로 병렬화하고 여러 스레드에서 실행되므로 처리 시간이 줄어듭니다.

이 상황에선 `dimension` 는 재색인의 범위입니다(예: a) `website` 또는 특정 `customer_group`.

인덱스 병렬화는 범위 인덱서에만 영향을 주며, 이는 Commerce가 모든 데이터를 하나의 테이블에 유지하는 대신 인덱서를 범위로 사용하여 데이터를 여러 테이블로 분할함을 의미합니다.

병렬 모드에서 다음 인덱스를 실행할 수 있습니다.

- `Catalog Search Fulltext` 는 스토어 보기를 따라 다를 수 있습니다.
- `Category Product` 는 스토어 보기를 따라 다를 수 있습니다.
- `Catalog Price` 는 웹 사이트 및 고객 그룹과 병행할 수 있습니다.
- `Catalog Permissions` 는 고객 그룹과 병행할 수 있습니다.

>[!INFO]
>
>카탈로그 검색 전체 텍스트 및 범주 제품에 대한 병렬화는 기본적으로 활성화되어 있습니다.

병렬화를 사용하려면 제품 가격 인덱서에 사용할 수 있는 차원 모드 중 하나를 설정합니다.

- `none` (기본값)
- `website`
- `customer_group`
- `website_and_customer_group`

예를 들어 웹 사이트별 모드를 설정하려면 다음을 수행하십시오.

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

카탈로그 권한에 병렬 처리를 사용하려면 카탈로그 권한 인덱서에 사용할 수 있는 차원 모드 중 하나를 설정합니다.

- `none` (기본값)
- `customer_group`

또는 현재 모드를 확인하려면:

```bash
bin/magento indexer:show-dimensions-mode
```

병렬 모드에서 다시 색인화하려면 환경 변수를 사용하여 reindex 명령을 실행합니다 `MAGE_INDEXER_THREADS_COUNT`또는 환경 변수를 `env.php` 파일. 이 변수는 재인덱스 처리를 위한 스레드 수를 설정합니다.

예를 들어 다음 명령은 `Catalog Search Fulltext` 세 가지 스레드에 대한 색인입니다.

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 인덱서 다시 설정

모든 인덱서 또는 특정 인덱서의 상태를 무효화하려면 이 명령을 사용합니다.

명령 옵션:

```bash
bin/magento indexer:reset [indexer]
```

위치 ```[indexer]``` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서를 무효화하려면 다음을 수행합니다.

샘플 결과:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## 인덱서 구성

다음 인덱서 옵션을 설정하려면 이 명령을 사용하십시오.

- **저장 시 업데이트(`realtime`)**: 인덱싱된 데이터는 관리자에서 변경할 때 업데이트됩니다. (예를 들어, 카테고리 제품 색인은 제품이 관리자의 카테고리에 추가된 후 다시 색인화됩니다.) 기본값입니다.
- **예약별 업데이트(`schedule`)**: 데이터는 cron 작업에서 설정한 일정에 따라 인덱싱됩니다.

[색인 생성에 대해 자세히 알아보기](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 현재 구성 표시

현재 인덱서 구성을 보려면 다음을 수행하십시오.

```bash
bin/magento indexer:show-mode [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서의 모드를 표시합니다. 예를 들어 모든 인덱서의 모드를 표시하려면 다음을 수행합니다.

샘플 결과:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### 인덱서 구성

>[!INFO]
>
>인덱서 모드를 전환하기 전에 웹 사이트를 [유지 관리](../../installation/tutorials/maintenance-mode.md) 모드 및 [cron 작업 비활성화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). 이렇게 하면 데이터베이스 잠금이 발생하지 않습니다.

인덱서 구성을 지정하려면 다음을 수행합니다.

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

위치:

- `realtime`- 저장 시 업데이트할 선택한 인덱스를 설정합니다.
- `schedule`- 지정된 인덱서를 크론 일정에 따라 저장하도록 설정합니다.
- `indexer`- 공백으로 구분된 인덱서 목록입니다. 생략 `indexer` 모든 인덱스를 같은 방식으로 구성합니다.

예를 들어 범주 제품 및 제품 범주 인덱서만 일정에 따라 갱신하도록 변경하려면 다음을 입력합니다.

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

샘플 결과:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

인덱서 모드가 로 설정되어 있으면 인덱서 관련 데이터베이스 트리거가 추가됩니다. `schedule` 인덱서 모드가 로 설정되어 있으면 제거되고 `realtime`. 인덱서가 `schedule`로 색인을 변경합니다. `realtime` 그리고 다시 `schedule`. 그러면 트리거가 재설정됩니다.
