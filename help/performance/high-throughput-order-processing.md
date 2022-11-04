---
title: 높은 처리량 주문 처리
description: Adobe Commerce 또는 Magento Open Source 배포를 위해 주문 배치 및 체크아웃 경험을 최적화합니다.
source-git-commit: 45ffa6487d94feba3d6c2a6d5d938108b1fef91d
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---


# 높은 처리량 주문 처리

에 대해 다음 모듈 세트를 구성하여 주문 배치 및 체크아웃 경험을 최적화할 수 있습니다 **높은 처리량 주문 처리**:

- [AsyncOrder](#asynchronous-order-placement)—큐를 사용하여 주문을 비동기식으로 처리합니다.
- [지연된 총 계산](#deferred-total-calculation)- 체크아웃이 시작될 때까지 주문 합계에 대한 계산을 정의합니다.
- [견적 로드 시 재고 확인](#disable-inventory-check)- 장바구니 항목의 재고 확인을 건너뛰도록 선택합니다.

모든 기능(AsyncOrder, 지연된 총 계산 및 Inventory Check)은 독립적으로 작동합니다. 세 기능을 모두 동시에 사용하거나 모든 조합에서 기능을 활성화 및 비활성화할 수 있습니다.

## 비동기 순서 배치

다음 _비동기 순서_ 모듈은 비동기 순서 배치를 활성화하고, 이 위치는 순서를 `received`를 지정하면 큐에 순서를 배치하고 큐의 주문을 선입선출 방식으로 처리합니다. AsyncOrder가 **비활성화됨** 기본적으로 제공됩니다.

예를 들어 고객이 장바구니에 제품을 추가하고 을(를) 선택합니다 **[!UICONTROL Proceed to Checkout]**. 그들은 **[!UICONTROL Shipping Address]** 양식을 선택하고 **[!UICONTROL Shipping Method]**&#x200B;을(를) 선택하고 결제 방법을 선택한 다음, 순서를 지정합니다. 장바구니가 지워지고, 주문이 다음과 같이 표시됩니다 **[!UICONTROL Received]**&#x200B;하지만 제품 수량이 아직 조정되지 않았고 고객에게 판매 이메일도 전송되지 않습니다. 주문이 접수되었지만 주문이 완전히 처리되지 않았기 때문에 주문 세부 사항을 아직 사용할 수 없습니다. 큐에서 `placeOrderProcess` 소비자가 를 사용하여 주문을 시작하고 확인합니다. [인벤토리 확인](#disable-inventory-check) 기능(기본적으로 활성화됨)을 사용하고 순서를 다음과 같이 업데이트합니다.

- **사용 가능한 제품**- 주문 상태가 _보류 중_&#x200B;를 설정하는 경우 제품 수량이 조정되고 주문 세부 사항이 포함된 이메일이 고객에게 전송되며 주문 세부 사항이 에서 볼 수 있게 됩니다 **주문 및 반품** 재정렬과 같은 실행 가능한 옵션이 있는 목록.
- **재고 부족 또는 공급 부족**- 주문 상태가 _거부됨_&#x200B;로 지정하는 경우 제품 수량이 조정되지 않고, 문제에 대한 주문 세부 사항이 포함된 이메일이 고객에게 전송되며, 주문 세부 사항은 **주문 및 반품** 실행 가능한 옵션이 없는 목록.

명령줄 인터페이스를 사용하여 이러한 기능을 활성화하거나 `app/etc/env.php` 파일에 정의된 해당 README 파일에 따른 파일 [_모듈 참조 안내서_][mrg].

**AsyncOrder를 사용하려면**:

명령줄 인터페이스를 사용하여 AsyncOrder를 활성화할 수 있습니다.

```bash
bin/magento setup:config:set --checkout-async 1
```

다음 `set` 명령은 다음 내용을 `app/etc/env.php` 파일:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

자세한 내용은 [AsyncOrder] 에서 _모듈 참조 안내서_.

**AsyncOrder를 비활성화하려면**:

>[!WARNING]
>
>AsyncOrder 모듈을 비활성화하기 전에 다음을 확인해야 합니다 _모두_ 비동기 주문 프로세스가 완료되었습니다.

명령줄 인터페이스를 사용하여 AsyncOrder를 비활성화할 수 있습니다.

```bash
bin/magento setup:config:set --checkout-async 0
```

다음 `set` 명령은 다음 내용을 `app/etc/env.php` 파일:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder 호환성

AsyncOrder는 제한된 집합 집합을 지원합니다. [!DNL Commerce] 기능.

| 카테고리 | 지원되는 기능 |
|------------------|--------------------------------------------------------------------------|
| 체크아웃 유형 | OnePage 체크아웃<br>표준 체크아웃<br>B2B 협상 가능 견적 |
| 결제 방법 | 수표/화폐 주문<br>배달 시 현금<br>Braintree<br>PayPal PayFlow Pro |
| 배송 방법 | 모든 배송 방법이 지원됩니다. |

다음 기능은 다음과 같습니다 **not** AsyncOrder에서 지원되지만 계속 동기적으로 작동합니다.

- 지원 기능 목록에 포함되지 않은 결제 방법
- 다중 주소 체크아웃
- 관리 주문 생성

#### 웹 API 지원

AsyncOrder 모듈이 활성화되면 다음 REST 종단점 및 GraphQL 변형이 비동기적으로 실행됩니다.

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL은 협상 가능한 견적 주문을 비동기식으로 배치하는 것을 지원하지 않습니다.

#### 결제 방법 제외

개발자는 비동기 주문 배치에서 특정 지급 방법을 명시적으로 제외시킬 수 있습니다. `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 배열입니다. 제외된 지급 방법을 사용하는 주문은 동기식으로 처리됩니다.

### 협상 가능한 견적 비동기 주문

다음 _협상 가능한 견적 비동기 주문_ B2B 모듈을 사용하면 `NegotiableQuote` 기능을 사용할 수 있습니다. AsyncOrder 및 협상가능 Quote가 활성화되어 있어야 합니다.

## 지연된 총 계산

다음 _지연된 총 계산_ 모듈은 장바구니에 대해 요청되거나 최종 체크아웃 단계 동안 총 계산을 지연하여 체크아웃 프로세스를 최적화합니다. 활성화되면 고객이 장바구니에 제품을 추가하므로 소계만 계산됩니다.

DelayedTotalCalculation이 **비활성화됨** 기본적으로 제공됩니다. 명령줄 인터페이스를 사용하여 이러한 기능을 활성화하거나 `app/etc/env.php` 파일에 정의된 해당 README 파일에 따른 파일 [_모듈 참조 안내서_][mrg].

**지연된 총계 계산을 사용하려면**:

명령줄 인터페이스를 사용하여 DelayedTotalCalculation을 활성화할 수 있습니다.

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

다음 `set` 명령은 다음 내용을 `app/etc/env.php` 파일:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation을 비활성화하려면**:

명령줄 인터페이스를 사용하여 DeferredTotalCalculation을 비활성화할 수 있습니다.

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

다음 `set` 명령은 다음 내용을 `app/etc/env.php` 파일:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

자세한 내용은 [DelayedTotalCalculating] 에서 _모듈 참조 안내서_.

### 제품 세금 고정

DelayedTotalCalculation이 활성화되면 장바구니에 제품을 추가한 후 미니 장바구니의 제품 가격 및 장바구니 소계에 고정 제품 세금(FPT)이 포함되지 않습니다. 제품을 미니 장바구니에 추가할 때 FPT 계산이 지연됩니다. 최종 체크아웃으로 이동한 후 장바구니에 PPT가 올바르게 표시됩니다.

## 재고 확인 사용 안 함

다음 _장바구니 로드 시 인벤토리 활성화_ 글로벌 설정은 장바구니에서 제품을 로드할 때 재고 확인을 수행할지 여부를 결정합니다. 인벤토리 확인 프로세스를 비활성화하면 모든 체크아웃 단계의 성능이 향상되며, 특히 장바구니에서 대량 제품을 처리할 때 성능이 향상됩니다.

비활성화하면 장바구니에 제품을 추가할 때 재고 확인이 발생하지 않습니다. 이 인벤토리 검사를 건너뛴 경우 일부 재고 부족 시나리오에서 다른 유형의 오류가 발생할 수 있습니다. 재고 확인 _항상_ 비활성화된 경우에도 주문 배치 단계에서 발생합니다.

**장바구니 로드 시 재고 확인 활성화** 기본적으로 활성화되어 있습니다(예로 설정). 장바구니를 로드할 때 재고 확인을 비활성화하려면 **[!UICONTROL Enable Inventory Check On Cart Load]** to `No` 관리자 UI에서 **스토어** > **구성** > **카탈로그** > **인벤토리** > **스톡 옵션** 섹션을 참조하십시오. 자세한 내용은 [글로벌 옵션 구성][global] 및 [카탈로그 인벤토리][inventory] 에서 _사용 안내서_.

## 로드 밸런싱

MySQL 데이터베이스 및 Redis 인스턴스에 대해 보조 연결을 활성화하여 여러 노드에 대한 로드 밸런싱을 수행할 수 있습니다.

Adobe Commerce은 여러 데이터베이스 또는 Redis 인스턴스를 비동기식으로 읽을 수 있습니다. 클라우드 인프라에서 상거래를 사용하는 경우, [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) 및 [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) 의 값 `.magento.env.yaml` 파일. 한 노드만 읽기-쓰기 트래픽을 처리해야 하므로 변수를 로 설정합니다. `true` 따라서 읽기 전용 트래픽에 대한 보조 연결이 만들어집니다. 값을 로 설정합니다. `false` 기존 읽기 전용 연결 배열을 `env.php` 파일.

의 예 `.magento.env.yaml` 파일:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/global-options.html
[inventory]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[DelayedTotalCalculating]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
