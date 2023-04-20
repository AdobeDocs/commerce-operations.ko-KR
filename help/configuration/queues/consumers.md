---
title: 메시지 큐 소비자
description: 연결된 기능 및 시스템 구성 설정을 포함하여 Adobe Commerce 및 Magento Open Source 메시지 큐 소비자에 대해 알아봅니다.
source-git-commit: f9db986510a3ec8e62b9d628da40fdfd9741479f
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---


# 메시지 큐 소비자

다음 표는 모든 메시지 큐 소비자를 식별하고, 이들이 수행하는 작업을 설명하고, 사용자와 연관된 관리 시스템 구성 설정을 식별합니다.

| 소비자 및 설명 | Adobe Commerce | Adobe Commerce과 B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 각 개별 작업에 대한 메시지를 만듭니다 [대량 작업](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)예: 품목 임포트 또는 익스포트, 일괄 스케일에서 가격 변경, 창고에 제품 지정 필요한 경우 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) 옵션이&#x200B;**[!UICONTROL Run asynchronously]**( Admin System 구성 설정) 아래에 그룹화됩니다. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| 백그라운드에서 쿠폰을 비동기식으로 생성합니다. 를 사용해야 합니다. [일괄 쿠폰 생성](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 기능. |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| 에서 우선 순위로 등록된 이벤트를 확인합니다 [Adobe Commerce에 대한 이벤트 Adobe I/O](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| 다음 중 연결 시간 초과를 방지합니다. [내보내기](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 대규모 데이터 세트(예: 200,000개 제품) |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 주문이 제출되거나 제품이 제거된 후 스톡 색인을 비동기식으로 수정합니다. 필요한 경우 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 옵션이 관리자 구성 설정에서 활성화되어 있습니다. 자세한 내용은 [성능 우수 사례](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 제품을 제거할 때 제품 SKU별로 소스 항목을 비동기적으로 삭제합니다. 필요한 경우 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 스톡 옵션이 관리 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `inventory.mass.update` | + | + | + |
| 특정 제품 SKU에 대한 기존 재고 항목을 비동기식으로 처리하고, 이전 재고 항목을 업데이트하고, 기본 소스 항목을 업데이트하고, 인벤토리를 다시 색인화합니다. 필요한 경우 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 대량 작업은 관리 시스템 구성 설정에서 사용할 수 있습니다. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 제품을 제거한 후 제품 SKU별로 예약을 비동기적으로 삭제합니다. 필요한 경우 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 스톡 옵션이 관리 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 제품이 제거된 후 제품 SKU별로 예약을 비동기식으로 업데이트합니다. 필요한 경우 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 스톡 옵션이 관리 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 재고에 지정된 각 제품의 판매 가능한 수량을 비동기식으로 업데이트합니다. 사용 중인 경우 이 소비자는 항상 실행 중이어야 합니다 [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| 소스 항목을 비동기식으로 다시 인덱싱합니다. 필요한 경우 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 가 &quot;(으)로 설정되어 있습니다.[!UICONTROL asynchronous]&quot;&quot;을 클릭합니다. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 주식을 비동기식으로 다시 인덱싱합니다. 필요한 경우 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) 가 &quot;(으)로 설정되어 있습니다.[!UICONTROL asynchronous]&quot;&quot;을 클릭합니다. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 임시 데이터베이스 테이블을 만들고 각 [고객 세그먼트](https://docs.magento.com/user-guide/marketing/customer-segments.html) 세그먼트 ID와 일치하는 모든 세그먼트를 삭제하고 세그먼트 ID를 지표로 사용하여 고객 세그먼트에 복사합니다. 이 작업은 모두 트랜잭션에서 수행되므로 오류가 발생하면 이 실행 전에 발생한 트랜잭션으로 롤백합니다. 거래 후, 소비자는 임시 테이블을 삭제합니다. |  |  |  |
| `media.content.synchronization` | + | + | + |
| 제품, 카테고리, CMS 블록 및 CMS 페이지에 대해 지정된 미디어에 대한 링크가 자산에 올바르게 할당되도록 합니다. 더 이상 사용되지 않는 이전 자산을 제거합니다. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| 미디어 자산 경로를 생성하고 검증합니다. 자산의 절대 경로는 미디어 디렉토리 내에서 자산의 위치에 따라 결정됩니다. 이미지 크기가 조정되고(필요한 경우) 생성된 경로 내의 미디어 디렉토리에 복사됩니다. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 에 이미지 파일 가져오기 `media_gallery_asset` 데이터베이스 테이블. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 비동기적 [크기 조절](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) 카탈로그 이미지. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| 협상 가능한 견적에 대한 가격을 업데이트합니다. 필요한 경우 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 비동기적 [주문 처리](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): 주문을 수신됨으로 표시하고 메시지 큐에 넣어 선입선출 방식으로 처리합니다. 로 간주됨 [모범 사례](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 성공 메시지를 보기 전에 고객이 백엔드 프로세스가 완료될 때까지 기다릴 필요가 없으므로 처리할 수 있는 주문 수를 개선하기 위해 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 관리자를 사용한 후 데이터베이스의 제품 속성에 대한 변경 사항을 비동기식으로 작성합니다 [업데이트 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 관리자를 사용하여 다음 작업을 수행한 후 데이터베이스의 특정 저장소 보기에 대한 제품 속성 변경 사항을 비동기식으로 기록합니다. [업데이트 만들기](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| 제품 가격 및 재고 변경에 대해 고객에게 알림 이메일을 보냅니다. 필요한 경우 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 구매 발주를 [주문](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 필요한 경우 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 구매 주문 이메일을 보냅니다. 필요한 경우 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 관련 항목에 대해 구매 발주 검증 [승인 규칙](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 필요한 경우 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 다음을 금지합니다. [문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 단일 사용 쿠폰을 여러 번 사용할 수 있는 곳입니다. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 공유 카탈로그 카테고리에 지정된 카테고리를 업데이트합니다. 필요한 경우 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 공유 카탈로그의 각 제품에 대한 가격을 업데이트합니다. 필요한 경우 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 카탈로그에서 제품을 삭제하거나 카트에서 제거할 때 유효하지 않거나 비활성 가격 견적을 삭제합니다. 필요한 경우 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 옵션이 관리자 시스템 구성 설정에서 활성화되어 있습니다. |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 장바구니 가격 규칙의 변경 사항을 반영하도록 활성 장바구니를 업데이트합니다. 업데이트할 때 필요합니다. [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
