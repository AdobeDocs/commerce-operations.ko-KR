---
title: 메시지 대기열 소비자
description: 관련된 기능 및 시스템 구성 설정을 포함하여 Adobe Commerce 및 Magento Open Source 메시지 대기열 소비자에 대해 알아봅니다.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# 메시지 대기열 소비자

다음 표에서 모든 메시지 대기열 소비자를 식별하고, 소비자가 수행하는 작업을 설명하고, 소비자와 연관된 관리 시스템 구성 설정을 식별합니다.

| 소비자 및 설명 | Adobe Commerce | Adobe Commerce 및 B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 의 각 개별 작업에 대한 메시지 만들기 [대량 작업](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)예를 들어, 항목을 가져오거나 내보내고, 가격을 대량으로 변경하고, 제품을 창고에 지정하는 등의 작업을 수행할 수 있습니다. 필요한 경우: [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 옵션이 로 설정되어 있습니다.**[!UICONTROL Run asynchronously]**관리자 시스템 구성 설정에서 을 참조하십시오. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| 백그라운드에서 쿠폰을 비동기적으로 생성합니다. 을(를) 사용하는 데 필요합니다. [배치 쿠폰 생성](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 기능. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| 에서 우선 순위로 등록된 이벤트를 확인합니다. [Adobe Commerce에 대한 이벤트 Adobe I/O](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| 다음 기간 동안 연결 시간 초과 방지 [내보내기](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 대용량 데이터 세트(예: 20만 개 제품) |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 주문이 배치되거나 제품이 제거된 후 비동기적으로 주가 지수를 수정합니다. 필요한 경우: [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 옵션은 관리자 구성 설정에서 활성화됩니다. 다음을 참조하십시오 [성능 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 제품이 제거되면 제품 SKU별로 소스 항목을 비동기적으로 삭제합니다. 필요한 경우: [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| 이전 재고 항목을 비동기적으로 처리하고, 이전 재고 항목을 업데이트하고, 기본 소스 항목을 업데이트하고, 특정 제품 SKU에 대한 재고를 다시 인덱싱합니다. 필요한 경우: [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 대량 작업은 관리 시스템 구성 설정에서 사용할 수 있습니다. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 제품이 제거된 후 제품 SKU별로 예약을 비동기적으로 삭제합니다. 필요한 경우: [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 제품이 제거된 후 제품 SKU별로 예약을 비동기적으로 업데이트합니다. 필요한 경우: [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 재고에 지정된 각 제품의 판매 가능 수량을 비동기식으로 업데이트합니다. 을(를) 사용하는 경우 이 소비자는 항상 실행 중이어야 합니다. [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| 소스 항목을 비동기적으로 다시 인덱싱합니다. 필요한 경우: [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 이(가) &quot;[!UICONTROL asynchronous]관리 시스템 구성 설정에서 &quot;&quot;를 참조하십시오. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 비동기적으로 스톡을 다시 인덱싱합니다. 필요한 경우: [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 이(가) &quot;[!UICONTROL asynchronous]관리 시스템 구성 설정에서 &quot;&quot;를 참조하십시오. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 임시 데이터베이스 테이블을 만들고 각 테이블을 이동합니다. [고객 세그먼트](https://docs.magento.com/user-guide/marketing/customer-segments.html) 에서 세그먼트 ID와 일치하는 모든 세그먼트를 삭제하고 세그먼트 ID를 지표로 사용하여 고객 세그먼트에 복사합니다. 이 작업은 모두 트랜잭션에서 수행되므로, 어떤 것이 실패하면 트랜잭션이 이 실행 전의 상태로 롤백됩니다. 거래가 끝난 후 소비자는 임시 테이블을 내려놓는다. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 제품, 카테고리, CMS 블록 및 CMS 페이지에 대해 할당된 미디어에 대한 링크가 자산에 올바르게 할당되었는지 확인합니다. 더 이상 사용되지 않는 이전 에셋을 제거합니다. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| 미디어 자산 경로를 생성하고 확인합니다. 에셋의 절대 경로는 미디어 디렉터리 내에서 서버의 위치에 따라 결정됩니다. 필요한 경우 이미지 크기가 조정되고 생성된 경로 내의 미디어 디렉터리에 복사됩니다. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 이미지 파일을 로 가져옵니다. `media_gallery_asset` 데이터베이스 테이블. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 비동기적으로 [크기 조정](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 카탈로그 이미지. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 협상 가능한 견적의 가격을 업데이트합니다. 필요한 경우: [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 비동기적으로 [주문 처리](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)를 사용하여 주문을 받은 것으로 표시하고 메시지 대기열에 배치한 다음 선입선출 방식으로 처리합니다. 고려됨 [모범 사례](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 고객이 성공 메시지를 보기 전에 백엔드 프로세스가 완료될 때까지 기다릴 필요가 없기 때문에 처리할 수 있는 주문 수를 늘릴 수 있습니다. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 관리자를에 사용한 후 데이터베이스의 제품 속성에 대한 변경 사항을 비동기식으로 기록합니다. [업데이트](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 관리자를에 사용한 후 데이터베이스의 특정 스토어 보기에 대한 제품 속성에 변경 사항을 비동기식으로 기록합니다. [업데이트](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| 제품 가격 및 재고 변경에 대한 알림 이메일을 고객에게 보냅니다. 필요한 경우 필수 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 구매 발주를 다음으로 변환 [주문](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 필요한 경우: [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 구매 주문 이메일을 보냅니다. 필요한 경우: [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 관련성이 있는 구매 발주를 검증합니다. [승인 규칙](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 필요한 경우: [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 저장 작업을 메시지 대기열에 배치하여 저장소 구성 변경 사항을 비동기적으로 저장하므로 많은 저장소 수준 구성을 포함하는 배포의 성능이 향상될 수 있습니다. 을(를) 사용하는 데 필요합니다. [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) 모듈. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 다음을 방지합니다. [문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 일회용 쿠폰을 여러 번 사용할 수 있는 경우. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 공유 카탈로그 범주에 할당된 범주를 업데이트합니다. 필요한 경우: [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 공유 카탈로그의 각 제품에 대한 가격을 업데이트합니다. 필요한 경우: [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 제품이 카탈로그에서 삭제되거나 장바구니에서 제거될 때 유효하지 않거나 비활성 가격 견적을 삭제합니다. 필요한 경우: [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 옵션은 관리 시스템 구성 설정에서 활성화됩니다. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 장바구니 가격 규칙의 변경 사항을 반영하도록 활성 장바구니를 업데이트합니다. 업데이트할 때 필요 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
