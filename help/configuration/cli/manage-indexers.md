---
title: 인덱서 관리
description: Commerce 인덱서를 보고 관리하는 방법의 예를 참조하십시오.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: a8f845813971eb32053cc5b2e390883abf3a104e
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---

# 인덱서 관리

{{file-system-owner}}

모든 인덱서의 목록을 보려면 다음과 같이 하십시오.

```bash
bin/magento indexer:info
```

이 목록은 다음과 같이 표시됩니다.

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
> Live Search, Catalog Service 또는 Product Recommendations을 사용하는 Adobe Commerce 가맹점에서는 [SaaS 기반 가격 인덱싱](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## 인덱서 상태 보기

모든 인덱서 또는 특정 인덱서의 상태를 보려면 이 명령을 사용하십시오. 예를 들어 인덱서를 다시 인덱싱해야 하는지 확인합니다.

명령 옵션:

```bash
bin/magento indexer:status [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서의 상태를 봅니다.

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

## 색인 재지정

이 명령을 사용하여 모든 인덱서 또는 선택한 인덱서를 한 번만 다시 인덱싱합니다.

>[!INFO]
>
>이 명령은 한 번만 다시 인덱싱합니다. 인덱서를 최신 상태로 유지하려면 [cron job](../cli/configure-cron-jobs.md).

명령 옵션:

```bash
bin/magento indexer:reindex [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서를 다시 인덱싱합니다.

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
>모든 인덱서를 리인덱싱하는 것은 많은 수의 제품, 고객, 카테고리 및 프로모션 규칙이 있는 스토어에 시간이 오래 걸릴 수 있습니다.

### 병렬 모드로 리인덱싱

{{php-process-control}}

인덱서는 범위가 지정되고 다중 스레드가 제공되어 병렬 모드에서 리인덱싱을 지원합니다. 인덱서의 차원으로 병렬화하고 여러 스레드에서 실행하므로 처리 시간이 단축됩니다.

이 맥락에서, `dimension` 는 리인덱싱 범위입니다(예: a). `website` 또는 특정 `customer_group`.

인덱스 병렬 처리는 범위가 지정된 인덱서에만 영향을 줍니다. 즉, Commerce는 모든 데이터를 한 테이블에 보관하는 대신 인덱서를 범위로 사용하여 데이터를 여러 테이블로 분할합니다.

다음 인덱스를 병렬 모드로 실행할 수 있습니다.

- `Catalog Search Fulltext` 스토어 조회수는 비슷한 수준입니다.
- `Category Product` 스토어 조회수는 비슷한 수준입니다.
- `Catalog Price` 은 웹 사이트 및 고객 그룹별로 유사할 수 있습니다.
- `Catalog Permissions` 은 고객 그룹별로 비슷할 수 있습니다.

>[!INFO]
>
>카탈로그 검색 전체 텍스트 및 범주 제품에 대한 병렬화가 기본적으로 활성화됩니다.

병렬화를 사용하려면 제품 가격 인덱서에 사용할 수 있는 차원 모드 중 하나를 설정합니다.

- `none` (기본값)
- `website`
- `customer_group`
- `website_and_customer_group`

예를 들어 웹 사이트당 모드를 설정하려면 다음을 수행합니다.

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

카탈로그 권한에 대한 병렬화를 사용하려면 카탈로그 권한 인덱서에 사용할 수 있는 차원 모드 중 하나를 설정합니다.

- `none` (기본값)
- `customer_group`

또는 현재 모드를 확인하려면 다음을 수행하십시오.

```bash
bin/magento indexer:show-dimensions-mode
```

병렬 모드로 다시 인덱싱하려면 환경 변수를 사용하여 reindex 명령을 실행합니다 `MAGE_INDEXER_THREADS_COUNT`또는 환경 변수를 `env.php` 파일. 이 변수는 색인 재지정 처리를 위한 스레드 수를 설정합니다.

예를 들어 다음 명령은 `Catalog Search Fulltext` 세 스레드의 인덱서:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 인덱서 재설정

이 명령을 사용하여 모든 인덱서 또는 특정 인덱서의 상태를 무효화합니다.

명령 옵션:

```bash
bin/magento indexer:reset [indexer]
```

위치 ```[indexer]``` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서를 무효화합니다.

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

이 명령을 사용하여 다음 인덱서 옵션을 설정합니다.

- **저장 시 업데이트(`realtime`)**: 관리자가 변경되면 인덱싱된 데이터가 업데이트됩니다. (예를 들어, 관리자 권한으로 제품을 카테고리에 추가한 후 카테고리 제품 색인이 다시 색인화됩니다.) 이것이 기본값입니다.
- **예약별 업데이트(`schedule`)**: 데이터는 cron 작업에 의해 설정된 일정에 따라 색인화됩니다.

[색인화에 대해 자세히 알아보기](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 현재 구성 표시

현재 인덱서 구성을 보려면 다음 작업을 수행하십시오.

```bash
bin/magento indexer:show-mode [indexer]
```

위치 `[indexer]` 는 공백으로 구분된 인덱서 목록입니다. 생략 `[indexer]` 모든 인덱서 모드를 표시합니다. 예를 들어 모든 인덱서의 모드를 표시하려면 다음을 수행합니다.

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

### 인덱서 모드 설정

>[!IMPORTANT]
>
>다음을 설정하십시오. [!DNL Customer Grid] 포함 `realtime` 대신 `schedule`. 다음 [!DNL Customer Grid] 를 사용해야만 다시 인덱싱할 수 있습니다. [!UICONTROL Update on Save] 옵션을 선택합니다. 이 인덱스는 다음을 지원하지 않습니다. `Update by Schedule` 옵션을 선택합니다. 다음 명령줄을 사용하여 저장 시 이 인덱서를 업데이트하도록 설정하십시오. `php bin/magento indexer:set-mode realtime customer_grid`
>
>다음을 참조하십시오 [인덱서 구성에 대한 우수 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) 다음에서 _구현 플레이북_.

>[!INFO]
>
>인덱서 모드를 전환하기 전에 웹 사이트를 로 설정합니다. [유지 보수](../../installation/tutorials/maintenance-mode.md) 모드 및 [cron 작업 비활성화](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). 이렇게 하면 데이터베이스 잠금이 발생하지 않습니다.

인덱서 구성을 지정하려면 다음을 수행합니다.

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

위치:

- `realtime`- 저장 시 업데이트할 선택한 인덱서를 설정합니다.
- `schedule`- cron 스케줄에 따라 저장할 지정된 인덱서를 설정합니다.
- `indexer`- 공백으로 구분된 인덱서 목록입니다. 생략 `indexer` 모든 인덱서를 동일한 방식으로 구성합니다.

예를 들어 범주 제품 및 제품 범주 인덱서만 일정에 따라 업데이트하도록 변경하려면 다음을 입력합니다.

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

샘플 결과:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

인덱서 모드가 로 설정되면 인덱서 관련 데이터베이스 트리거가 추가됩니다. `schedule` 인덱서 모드가 로 설정되면 제거 `realtime`. 인덱서가 로 설정된 동안 데이터베이스에서 트리거가 누락된 경우 `schedule`, 인덱서를 다음으로 변경 `realtime` 다시 다음으로 변경 `schedule`. 그러면 트리거가 재설정됩니다.

### 인덱서 상태 설정 [!BADGE 2.4.7-베타]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="2.4.7 베타 버전에서만 사용 가능"}

이 명령을 사용하면 관리자가 하나 이상의 인덱서의 작동 상태를 수정하여 데이터 가져오기, 업데이트 또는 유지 관리와 같은 광범위한 작업 중에 시스템 성능을 최적화할 수 있습니다.

명령 구문:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

위치:

- `invalid`- 인덱서가 최신 상태가 아닌 것으로 표시하여 일시 중단되지 않는 한 다음 cron 실행 시 다시 인덱싱하도록 요청합니다.
- `suspended`- 인덱서에 대한 자동 cron 트리거 업데이트를 일시적으로 중지합니다. 이 상태는 실시간 및 예약 모드 모두에 적용되므로 집중 작업 중에 자동 업데이트가 일시 중지되도록 할 수 있습니다.
- `valid`- 인덱서 데이터가 최신 상태이며 다시 인덱싱할 필요가 없음을 나타냅니다.
- `indexer`- 공백으로 구분된 인덱서 목록입니다. 생략 `indexer` 모든 인덱서를 동일한 방식으로 구성합니다.

예를 들어 특정 인덱서를 일시 중단하려면 다음을 입력합니다.

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

샘플 결과:

```terminal
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### 일시 중단된 인덱서 상태 관리

인덱서가 로 설정된 경우 `suspended` 상태는 주로 자동 재색인화 및 구체화된 뷰 갱신에 영향을 줍니다. 다음은 간단한 개요입니다.

**리인덱싱 건너뜀**: 자동 리인덱싱은 다음에 대해 우회합니다. `suspended` 인덱서 및 이를 공유하는 모든 인덱서 `shared_index`. 이렇게 하면 중단된 프로세스와 관련된 데이터를 리인덱싱하지 않음으로써 시스템 자원이 보존됩니다.

**구체화된 뷰 갱신 생략됨**: 리인덱싱과 유사하게 와 관련된 구체화된 뷰에 대한 업데이트입니다. `suspended` 인덱서 또는 공유 인덱스도 일시 중지됩니다. 이러한 동작은 서스펜션 기간 동안 시스템 부하를 더 감소시킨다.

>[!INFO]
>
>다음 `indexer:reindex` 명령은 로 표시된 인덱서를 포함하여 모든 인덱서를 다시 인덱싱합니다. `suspended`자동 업데이트가 일시 중지된 경우 수동 업데이트에 유용합니다.

>[!IMPORTANT]
>
>인덱서 상태 변경 `valid` 출처: `suspended` 또는 `invalid` 주의해야 합니다. 이렇게 하면 누적된 인덱싱되지 않은 데이터가 있는 경우 성능이 저하될 수 있습니다.
>
>상태를 수동으로 업데이트하기 전에 모든 데이터가 정확하게 색인화되도록 하는 것이 중요합니다 `valid` 시스템 성능 및 데이터 무결성을 유지 관리합니다.
