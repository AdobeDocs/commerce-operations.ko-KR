---
title: 메시지 대기열 소비자
description: 관련된 기능 및 시스템 구성 설정을 포함하여 Adobe Commerce 메시지 대기열 소비자에 대해 알아봅니다.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# 메시지 대기열 소비자

다음 표에서 모든 메시지 대기열 소비자를 식별하고, 소비자가 수행하는 작업을 설명하고, 소비자와 연관된 관리 시스템 구성 설정을 식별합니다.

| 소비자 및 설명 | Adobe Commerce | Adobe Commerce 및 B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 항목 가져오기 또는 내보내기, 일괄 가격 변경, 웨어하우스에 제품 할당 등 [일괄 작업](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)의 각 개별 작업에 대한 메시지를 만듭니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) 옵션이&#x200B;**[!UICONTROL Run asynchronously]**(으)로 설정된 경우 필수입니다. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| 백그라운드에서 쿠폰을 비동기적으로 생성합니다. [일괄 쿠폰 생성](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 기능을 사용하는 데 필요합니다. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| [Adobe Commerce용 Adobe I/O Events](https://developer.adobe.com/commerce/events/get-started/)에서 우선 순위로 등록된 이벤트를 확인합니다. |
| `exportProcessor` | + | + | + |
| 대규모 데이터 세트(예: 200,000개 제품)의 [내보내기](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 동안 연결 시간 초과를 방지합니다. |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 주문이 배치되거나 제품이 제거된 후 비동기적으로 주가 지수를 수정합니다. 관리자 구성 설정에서 [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) 옵션을 사용하도록 설정한 경우 필수입니다. [성능 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update)를 참조하세요. |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 제품이 제거되면 제품 SKU별로 소스 항목을 비동기적으로 삭제합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) 스톡 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| 이전 재고 항목을 비동기적으로 처리하고, 이전 재고 항목을 업데이트하고, 기본 소스 항목을 업데이트하고, 특정 제품 SKU에 대한 재고를 다시 인덱싱합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) 일괄 작업을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 제품이 제거된 후 제품 SKU별로 예약을 비동기적으로 삭제합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) 스톡 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 제품이 제거된 후 제품 SKU별로 예약을 비동기적으로 업데이트합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) 스톡 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 재고에 지정된 각 제품의 판매 가능 수량을 비동기식으로 업데이트합니다. [!DNL Inventory Management]을(를) 사용하는 경우 이 소비자는 항상 실행 중이어야 합니다. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| 소스 항목을 비동기적으로 다시 인덱싱합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)이(가) &quot;[!UICONTROL asynchronous]&quot;(으)로 설정된 경우 필요합니다. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 비동기적으로 스톡을 다시 인덱싱합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)이(가) &quot;[!UICONTROL asynchronous]&quot;(으)로 설정된 경우 필요합니다. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 임시 데이터베이스 테이블을 만들고, 각 [고객 세그먼트](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)를 해당 테이블로 이동하고, 세그먼트 ID와 일치하는 모든 세그먼트를 삭제하고, 세그먼트 ID를 표시기로 사용하여 고객 세그먼트에 복사합니다. 이 작업은 모두 트랜잭션에서 수행되므로, 어떤 것이 실패하면 트랜잭션이 이 실행 전의 상태로 롤백됩니다. 거래가 끝난 후 소비자는 임시 테이블을 내려놓는다. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 제품, 카테고리, CMS 블록 및 CMS 페이지에 대해 할당된 미디어에 대한 링크가 자산에 올바르게 할당되도록 합니다. 더 이상 사용되지 않는 이전 에셋을 제거합니다. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| 미디어 자산 경로를 생성하고 확인합니다. 에셋의 절대 경로는 미디어 디렉터리 내에서 서버의 위치에 따라 결정됩니다. 필요한 경우 이미지 크기가 조정되고 생성된 경로 내의 미디어 디렉터리에 복사됩니다. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| `media_gallery_asset` 데이터베이스 테이블로 이미지 파일을 가져옵니다. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 카탈로그 이미지를 비동기적으로 [크기 조정](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images)합니다. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 협상 가능한 견적의 가격을 업데이트합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 비동기적으로 [주문을 처리](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)하여 주문을 받은 것으로 표시하고 메시지 대기열에 배치하여 선입선출 방식으로 처리합니다. 고객이 성공 메시지를 보기 전에 백엔드 프로세스가 완료될 때까지 기다릴 필요가 없기 때문에 처리할 수 있는 주문 수를 개선하기 위해 [모범 사례](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md)를 고려했습니다. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 관리자를 사용하여 [업데이트를 수행](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)한 후 데이터베이스의 제품 특성에 변경 내용을 비동기적으로 씁니다. |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 관리자를 사용하여 [업데이트](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html)한 후 데이터베이스의 특정 스토어 보기에 대한 제품 특성에 변경 내용을 비동기적으로 씁니다. |                |                         |                     |
| `product_alert` | + | + | + |
| 제품 가격 및 재고 변경에 대한 알림 이메일을 고객에게 보냅니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 구매 주문을 [주문](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules)&#x200B;(으)로 전환합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 구매 주문 이메일을 보냅니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 관련 [승인 규칙](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules)에 대해 구매 주문을 확인합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 저장 작업을 메시지 대기열에 배치하여 저장소 구성 변경 사항을 비동기적으로 저장하므로 많은 저장소 수준 구성을 포함하는 배포의 성능이 향상될 수 있습니다. [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) 모듈을 사용하는 데 필요합니다. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 일회용 쿠폰을 여러 번 사용할 수 있는 문제를 방지합니다. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 공유 카탈로그 범주에 할당된 범주를 업데이트합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 공유 카탈로그의 각 제품에 대한 가격을 업데이트합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 제품이 카탈로그에서 삭제되거나 장바구니에서 제거될 때 유효하지 않거나 비활성 가격 견적을 삭제합니다. 관리 시스템 구성 설정에서 [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) 옵션을 사용하도록 설정한 경우 필수입니다. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| 장바구니 가격 규칙의 변경 사항을 반영하도록 활성 장바구니를 업데이트합니다. [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html)을(를) 업데이트할 때 필요합니다. |                |                         |                     |

{style="table-layout:auto"}
