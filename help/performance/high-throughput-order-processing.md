---
title: 높은 처리량 주문 처리
description: Adobe Commerce 배포에 대한 주문 배치 및 체크아웃 경험을 최적화합니다.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# 높은 처리량 주문 처리

다음 모듈 세트를 구성하여 주문 배치 및 체크아웃 경험을 최적화할 수 있습니다 **대량 주문 처리**:

- [AsyncOrder](#asynchronous-order-placement)- 대기열을 사용하여 주문을 비동기적으로 처리합니다.
- [지연된 합계 계산](#deferred-total-calculation)- 체크아웃이 시작될 때까지 주문 합계에 대한 계산을 연기합니다.
- [견적 로드 시 인벤토리 검사](#disable-inventory-check)—장바구니 항목의 인벤토리 유효성 검사를 건너뛰도록 선택합니다.

AsyncOrder, 지연된 합계 계산 및 재고 검사 등의 모든 기능은 독립적으로 작동합니다. 세 가지 기능을 동시에 사용하거나 모든 조합으로 기능을 활성화 및 비활성화할 수 있습니다.

## 비동기 주문 배치

다음 _비동기 순서_ 모듈은 순서를 로 표시하는 비동기 순서 배치를 활성화합니다. `received`는 대기열에 주문을 넣고 선입선출 방식으로 대기열의 주문을 처리합니다. AsyncOrder는 **비활성화됨** 기본적으로.

예를 들어 고객이 장바구니에 제품을 추가하고 을 선택합니다 **[!UICONTROL Proceed to Checkout]**. 다음을 입력합니다. **[!UICONTROL Shipping Address]** 양식, 기본 설정 선택 **[!UICONTROL Shipping Method]**&#x200B;을 클릭하고 결제 방법을 선택한 다음 주문합니다. 장바구니가 지워졌습니다. 주문이 다음과 같이 표시됩니다. **[!UICONTROL Received]**, 그러나 제품 수량이 아직 조정되지 않았으며 고객에게 판매 이메일도 전송되지 않았습니다. 주문을 받았는데, 주문이 완전히 처리되지 않아 주문 세부 사항은 아직 이용할 수 없습니다. 이 워크플로우는 다음 시간까지 큐에 남아 있습니다. `placeOrderProcess` 소비자가 시작하고 다음을 사용하여 주문 확인 [재고 점검](#disable-inventory-check) 기능(기본적으로 활성화됨)을 추가하고 순서를 다음과 같이 업데이트합니다.

- **사용 가능한 제품**- 주문 상태가 다음으로 변경됨 _보류 중_, 제품 수량이 조정되고 주문 세부 사항이 포함된 이메일이 고객에게 전송되며 성공적인 주문 세부 사항이에서 볼 수 있게 됩니다. **주문 및 반품** 순서 재지정과 같이 실행 가능한 옵션이 있는 목록
- **제품 품절 또는 공급 부족**- 주문 상태가 다음으로 변경됨 _거부됨_, 제품 수량이 조정되지 않고 문제에 대한 주문 세부 사항이 포함된 이메일이 고객에게 전송되며 거부된 주문 세부 사항은 다음에서 사용할 수 있습니다. **주문 및 반품** 실행할 수 있는 옵션이 없는 목록입니다.

명령줄 인터페이스를 사용하여 이러한 기능을 활성화하거나 `app/etc/env.php` 파일에 정의된 해당 추가 정보 파일에 따른 파일 [_모듈 참조 안내서_][mrg].

**AsyncOrder를 활성화하려면**:

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

다음을 참조하십시오 [AsyncOrder] 다음에서 _모듈 참조 안내서_.

**AsyncOrder를 비활성화하려면**:

>[!WARNING]
>
>AsyncOrder 모듈을 비활성화하기 전에 다음을 확인해야 합니다. _모두_ 비동기 주문 프로세스가 완료되었습니다.

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

AsyncOrder는 제한된 집합 [!DNL Commerce] 기능.

| 범주 | 지원되는 기능 |
|------------------|--------------------------------------------------------------------------|
| 체크아웃 유형 | OnePage 체크아웃<br>표준 체크아웃<br>B2B 협상 가능 견적 |
| 결제 방법 | 수표/우편환<br>배달 현금<br>Braintree<br>PayPal PayFlow 프로 |
| 배송 방법 | 모든 배송 방법이 지원됩니다. |

다음 기능은 다음과 같습니다 **아님** asyncOrder에서 지원되지만 동기적으로 계속 작동합니다.

- 지원되는 기능 목록에 포함되지 않은 결제 방법
- 다중 주소 체크아웃
- 관리자 주문 만들기

#### 웹 API 지원

AsyncOrder 모듈이 활성화되면 다음 REST 끝점 및 GraphQL 돌연변이가 비동기적으로 실행됩니다.

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL은 비동기식으로 협상 가능한 견적 주문 수행을 지원하지 않습니다.

#### 결제 방법 제외

개발자는 특정 결제 방법을 비동기 주문 배치에 추가하여 명시적으로 제외할 수 있습니다. `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 배열입니다. 제외된 결제 방법을 사용하는 주문은 동기적으로 처리됩니다.

### 협상 가능 견적 비동기 주문

다음 _협상 가능 견적 비동기 주문_ B2B 모듈을 사용하면 주문 항목을 를 위해 비동기적으로 저장할 수 있습니다. `NegotiableQuote` 기능. AsyncOrder 및 NegotiableQuote가 활성화되어 있어야 합니다.

## 지연된 합계 계산

다음 _지연된 합계 계산_ 모듈은 장바구니에 대해 요청되거나 최종 체크아웃 단계 동안 총 계산을 연기하여 체크아웃 프로세스를 최적화합니다. 활성화되면 고객이 장바구니에 제품을 추가할 때 소계만 계산됩니다.

DeferredTotalCalculation은 **비활성화됨** 기본적으로. 명령줄 인터페이스를 사용하여 이러한 기능을 활성화하거나 `app/etc/env.php` 파일에 정의된 해당 추가 정보 파일에 따른 파일 [_모듈 참조 안내서_][mrg].

**DeferredTotalCalculation을 사용하려면**:

명령줄 인터페이스를 사용하여 DeferredTotalCalculation을 활성화할 수 있습니다.

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

다음을 참조하십시오 [지연된 총계 계산] 다음에서 _모듈 참조 안내서_.

### 고정 제품세

DeferredTotalCalculation이 활성화되면 제품을 장바구니에 추가한 후 고정 제품 세금(FPT)이 제품 가격 및 미니 장바구니의 장바구니 소계에 포함되지 않습니다. 제품을 미니 장바구니에 추가할 때 FPT 계산이 연기됩니다. 최종 체크아웃으로 이동한 후 장바구니에 FPT가 올바르게 표시됩니다.

## 인벤토리 검사 비활성화

다음 _장바구니 로드 시 인벤토리 활성화_ 글로벌 설정은 장바구니에서 제품을 로드할 때 인벤토리 검사를 수행할지 여부를 결정합니다. 재고 확인 프로세스를 비활성화하면 모든 체크아웃 단계의 성능이 향상됩니다. 특히 장바구니에서 대량 제품을 처리할 때 더욱 그렇습니다.

비활성화되면 장바구니에 제품을 추가할 때 재고 확인이 발생하지 않습니다. 이 인벤토리 검사를 건너뛸 경우 일부 재고 부족 시나리오에서 다른 유형의 오류가 발생할 수 있습니다. 인벤토리 검사 _항상_ 비활성화된 경우에도 주문 배치 단계에서 발생합니다.

**장바구니 로드 시 인벤토리 확인 활성화** 는 기본적으로 활성화되어 있습니다(예로 설정). 장바구니를 로드할 때 인벤토리 검사를 비활성화하려면 다음을 설정하십시오. **[!UICONTROL Enable Inventory Check On Cart Load]** 끝 `No` 관리자 UI에서 **스토어** > **구성** > **카탈로그** > **인벤토리** > **스톡 옵션** 섹션. 다음을 참조하십시오 [글로벌 옵션 구성][global] 및 [카탈로그 인벤토리][inventory] 다음에서 _사용 안내서_.

## 로드 밸런싱

MySQL 데이터베이스 및 Redis 인스턴스에 대한 보조 연결을 활성화하면 서로 다른 노드에 대한 로드 밸런스를 조정할 수 있습니다.

Adobe Commerce은 여러 데이터베이스 또는 Redis 인스턴스를 비동기식으로 읽을 수 있습니다. 클라우드 인프라에서 Commerce을 사용하는 경우 를 편집하여 보조 연결을 구성할 수 있습니다. [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) 및 [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) 의 값 `.magento.env.yaml` 파일. 한 노드만 읽기-쓰기 트래픽을 처리해야 하므로 변수를 로 설정합니다. `true` 그러면 읽기 전용 트래픽에 대한 보조 연결이 만들어집니다. 값을 다음으로 설정 `false` 에서 기존 읽기 전용 연결 배열을 제거하려면 `env.php` 파일.

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
[지연된 총계 계산]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
