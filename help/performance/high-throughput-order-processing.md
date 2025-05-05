---
title: 체크아웃 성능 모범 사례
description: Adobe Commerce 사이트에서 체크아웃 경험의 성능을 최적화하는 방법을 알아봅니다.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# 체크아웃 성능 모범 사례

Adobe Commerce의 [체크아웃](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) 프로세스는 Storefront 경험의 중요한 측면입니다. 기본 제공 [장바구니](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) 및 [체크아웃](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) 기능을 사용합니다.

성능은 사용자 경험을 좋게 유지하는 데 중요합니다. **처리량이 많은 주문 처리**&#x200B;에 대해 다음 옵션을 구성하여 체크아웃 성능을 최적화할 수 있습니다.

- [AsyncOrder](#asynchronous-order-placement) - 큐를 사용하여 주문을 비동기적으로 처리합니다.
- [지연된 합계 계산](#deferred-total-calculation)—체크아웃이 시작될 때까지 주문 합계에 대한 계산을 지연합니다.
- [장바구니 로드 시 인벤토리 확인](#disable-inventory-check) - 장바구니 항목의 인벤토리 유효성 검사를 건너뛰도록 선택합니다.
- [부하 분산](#load-balancing)—MySQL 데이터베이스 및 Redis 인스턴스에 대한 보조 연결을 사용하도록 설정합니다.

AsyncOrder, 지연된 합계 계산 및 장바구니 로드 구성 옵션에 대한 인벤토리 검사는 모두 독립적으로 작동합니다. 세 가지 기능을 동시에 사용하거나 모든 기능을 조합하여 활성화 및 비활성화할 수 있습니다.

>[!NOTE]
>
>사용자 지정 PHP 코드를 사용하여 기본 제공 장바구니 및 체크아웃 기능을 사용자 지정하지 마십시오. 잠재적인 성능 문제 외에도 사용자 정의 PHP 코드를 사용하면 복잡한 업그레이드 및 유지 관리 문제가 발생할 수 있습니다. 이러한 문제는 TCO를 증가시킵니다. PHP 기반 장바구니 및 체크아웃 사용자 지정이 불가피한 경우 [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)에서 승인한 확장 프로그램만 사용하십시오. 모든 마켓플레이스 확장은 Adobe Commerce 코딩 표준 및 모범 사례를 충족하는지 확인하기 위해 [광범위한 검토](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/)를 받아야 합니다.

## 비동기 주문 배치

_비동기 순서_ 모듈을 사용하면 순서를 `received`(으)로 표시하고 대기열에 주문을 배치하고 선입선출 방식으로 대기열의 주문을 처리하는 비동기 순서 배치를 사용할 수 있습니다. AsyncOrder는 기본적으로 **비활성화됨**&#x200B;입니다.

예를 들어 고객이 장바구니에 제품을 추가하고 **[!UICONTROL Proceed to Checkout]**&#x200B;을(를) 선택합니다. **[!UICONTROL Shipping Address]** 양식을 작성하고 기본 설정 **[!UICONTROL Shipping Method]**&#x200B;을(를) 선택한 다음 결제 방법을 선택하고 주문합니다. 장바구니가 지워지고 주문이 **[!UICONTROL Received]**(으)로 표시되지만 제품 수량이 아직 조정되지 않았으며 고객에게 판매 이메일도 전송되지 않았습니다. 주문을 받았는데, 주문이 완전히 처리되지 않아 주문 세부 사항은 아직 이용할 수 없습니다. `placeOrderProcess` 소비자가 시작할 때까지 큐에 남아 있으며 [인벤토리 확인](#disable-inventory-check) 기능(기본적으로 활성화됨)으로 주문을 확인하고 다음과 같이 주문을 업데이트합니다.

- **제품 사용 가능**—주문 상태가 _보류 중_(으)로 변경되고, 제품 수량이 조정되고, 주문 세부 정보가 포함된 이메일이 고객에게 전송되며, 주문 세부 정보가 **주문 및 반품** 목록에서 재주문과 같은 실행 가능한 옵션과 함께 볼 수 있게 됩니다.
- **제품 품절 또는 공급 부족**—주문 상태가 _거부됨_(으)로 변경되고, 제품 수량이 조정되지 않으며, 문제에 대한 주문 세부 정보가 포함된 전자 메일이 고객에게 전송되고, **주문 및 반품** 목록에서 실행 가능한 옵션이 없는 거부된 주문 세부 정보를 사용할 수 있습니다.

명령줄 인터페이스를 사용하여 이러한 기능을 사용하도록 설정하거나 [_모듈 참조 안내서_](https://developer.adobe.com/commerce/php/module-reference/)에 정의된 해당 README 파일에 따라 `app/etc/env.php` 파일을 편집하십시오.

**AsyncOrder를 사용하려면**:

명령줄 인터페이스를 사용하여 AsyncOrder를 활성화할 수 있습니다.

```bash
bin/magento setup:config:set --checkout-async 1
```

`set` 명령은 `app/etc/env.php` 파일에 다음 내용을 씁니다.

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

_모듈 참조 안내서_&#x200B;에서 [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)을(를) 참조하십시오.

**AsyncOrder를 사용하지 않도록 설정하려면**:

>[!WARNING]
>
>AsyncOrder 모듈을 비활성화하기 전에 _모두_ 비동기 순서 프로세스가 완료되었는지 확인해야 합니다.

명령줄 인터페이스를 사용하여 AsyncOrder를 비활성화할 수 있습니다.

```bash
bin/magento setup:config:set --checkout-async 0
```

`set` 명령은 `app/etc/env.php` 파일에 다음 내용을 씁니다.

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder 호환성

AsyncOrder는 제한된 Adobe Commerce 기능 세트를 지원합니다.

| 범주 | 지원되는 기능 |
|------------------|--------------------------------------------------------------------------|
| 체크아웃 유형 | OnePage 체크아웃<br>표준 체크아웃<br>B2B 협상 가능 견적 |
| 결제 방법 | 수표/우편환<br>배달 시 현금<br>Braintree<br>PayPal PayFlow Pro |
| 배송 방법 | 모든 배송 방법이 지원됩니다. |

다음 기능은 AsyncOrder에서 지원되지 않는 **&#x200B;**&#x200B;이지만 동기적으로 계속 작동합니다.

- 지원되는 기능 목록에 포함되지 않은 결제 방법
- 다중 주소 체크아웃
- 관리자 주문 만들기

#### 웹 API 지원

AsyncOrder 모듈이 활성화되면 다음 REST 끝점 및 GraphQL 돌연변이가 비동기적으로 실행됩니다.

**나머지:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL은 비동기식으로 협상 가능한 견적 주문 수행을 지원하지 않습니다.

#### 결제 방법 제외

개발자는 특정 결제 방법을 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 배열에 추가하여 비동기 주문 배치에서 명시적으로 제외할 수 있습니다. 제외된 결제 방법을 사용하는 주문은 동기적으로 처리됩니다.

### 협상 가능 견적 비동기 주문

_협상 가능한 견적 비동기 주문_ B2B 모듈을 사용하면 주문 항목을 `NegotiableQuote` 기능에 대해 비동기적으로 저장할 수 있습니다. AsyncOrder 및 NegotiableQuote가 활성화되어 있어야 합니다.

## 지연된 합계 계산

_지연된 총 계산_ 모듈은 장바구니에 대해 요청되거나 최종 체크아웃 단계 동안 총 계산을 지연시켜 체크아웃 프로세스를 최적화합니다. 활성화되면 고객이 장바구니에 제품을 추가할 때 소계만 계산됩니다.

지연된 총 계산은 기본적으로 **사용 안 함**&#x200B;입니다. 명령줄 인터페이스를 사용하여 이러한 기능을 사용하도록 설정하거나 [_모듈 참조 안내서_](https://developer.adobe.com/commerce/php/module-reference/)에 정의된 해당 README 파일에 따라 `app/etc/env.php` 파일을 편집하십시오.

**DeferredTotalCalculation을 사용하려면**:

명령줄 인터페이스를 사용하여 DeferredTotalCalculation을 활성화할 수 있습니다.

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

`set` 명령은 `app/etc/env.php` 파일에 다음 내용을 씁니다.

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation을 사용하지 않도록 설정하려면**:

명령줄 인터페이스를 사용하여 DeferredTotalCalculation을 비활성화할 수 있습니다.

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

`set` 명령은 `app/etc/env.php` 파일에 다음 내용을 씁니다.

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

_모듈 참조 안내서_&#x200B;에서 [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/)을(를) 참조하십시오.

### 고정 제품세

이연 합계 계산이 활성화된 경우 장바구니에 제품을 추가한 후 고정 제품 세금(FPT)이 제품 가격 및 미니 장바구니의 장바구니 소계에 포함되지 않습니다. 제품을 미니 장바구니에 추가할 때 FPT 계산이 연기됩니다. 최종 체크아웃으로 이동한 후 장바구니에 FPT가 올바르게 표시됩니다.

## 인벤토리 검사 비활성화

_장바구니 로드 시 인벤토리 사용_ 전역 설정은 장바구니에서 제품을 로드할 때 인벤토리 검사를 수행할지 여부를 결정합니다. 재고 확인 프로세스를 비활성화하면 모든 체크아웃 단계의 성능이 향상됩니다. 특히 장바구니에서 대량 제품을 처리할 때 더욱 그렇습니다.

비활성화되면 장바구니에 제품을 추가할 때 재고 확인이 발생하지 않습니다. 이 인벤토리 검사를 건너뛸 경우 일부 재고 부족 시나리오에서 다른 유형의 오류가 발생할 수 있습니다. 사용하지 않도록 설정한 경우에도 주문 배치 단계에서 인벤토리 확인 _always_&#x200B;이(가) 발생합니다.

**장바구니 로드 시 인벤토리 검사 사용**&#x200B;은(는) 기본적으로 사용(예로 설정)됩니다. 장바구니를 로드할 때 인벤토리 검사를 비활성화하려면 관리 UI **스토어** > **구성** > **카탈로그** > **인벤토리** > **재고 옵션** 섹션에서 **[!UICONTROL Enable Inventory Check On Cart Load]**&#x200B;을(를) `No`(으)로 설정하십시오. _사용 안내서_&#x200B;에서 [전역 옵션 구성](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) 및 [카탈로그 인벤토리](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview)를 참조하십시오.

## 로드 밸런싱

MySQL 데이터베이스 및 Redis 인스턴스에 대한 보조 연결을 활성화하면 서로 다른 노드에 대한 로드 밸런스를 조정할 수 있습니다.

Adobe Commerce은 여러 데이터베이스 또는 Redis 인스턴스를 비동기식으로 읽을 수 있습니다. 클라우드 인프라에서 Commerce을 사용하는 경우 `.magento.env.yaml` 파일의 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) 및 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) 값을 편집하여 보조 연결을 구성할 수 있습니다. 읽기-쓰기 트래픽을 처리하는 노드는 하나뿐이므로 변수를 `true`(으)로 설정하면 읽기 전용 트래픽에 대한 보조 연결이 만들어집니다. `env.php` 파일에서 기존 읽기 전용 연결 배열을 제거하려면 값을 `false`(으)로 설정하십시오.

`.magento.env.yaml` 파일의 예:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
