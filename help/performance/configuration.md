---
title: 구성 모범 사례
description: 다음 모범 사례를 사용하여 Adobe Commerce 또는 Magento Open Source 배포의 응답 시간을 최적화합니다.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# 구성 모범 사례

Commerce는 더 높은 처리량을 제공할 뿐만 아니라 페이지의 응답 시간을 향상시키는 데 사용할 수 있는 많은 설정 및 도구를 제공합니다.

## 크론 작업

의 모든 비동기 작업 [!DNL Commerce] Linux를 사용하여 수행됩니다. `cron` 명령입니다. 다음을 참조하십시오 [cron 구성 및 실행](../configuration/cli/configure-cron-jobs.md) 을(를) 올바르게 구성합니다.

## 인덱서

인덱서는 다음 중 하나에서 실행할 수 있습니다. **[!UICONTROL Update on Save]** 또는 **[!UICONTROL Update on Schedule]** 모드. 다음 **[!UICONTROL Update on Save]** 카탈로그 또는 기타 데이터가 변경될 때마다 모드가 즉시 색인화됩니다. 이 모드는 스토어에서 업데이트 및 탐색 작업의 강도가 낮다고 가정합니다. 이로 인해 고부하 작업 중에 상당한 지연이 발생하고 데이터를 사용할 수 없게 될 수 있습니다. 다음을 사용하는 것이 좋습니다. **일정에 따라 업데이트** 성능 목적으로 데이터 업데이트에 대한 정보를 저장하고 특정 cron 작업을 통해 백그라운드의 부분별로 색인화를 수행하기 때문입니다. 각 의 모드를 변경할 수 있습니다 [!DNL Commerce] 인덱서에서 별도로 사용  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 구성 페이지를 참조하십시오. 다음 [!UICONTROL Customer Grid] 인덱스는 항상 로 설정되어야 합니다. **[!UICONTROL Update on Save]** 모드.

>[!TIP]
>
>MariaDB 10.4 및 10.6에 대한 리인덱싱은 다른 MariaDB에 비해 시간이 더 소요되거나 [!DNL MySQL] 버전. 에 설명된 기본 MariaDB 구성 설정을 수정하는 것이 좋습니다. [설치 사전 요구 사항](../installation/prerequisites/database/mysql.md).

## 캐시

프로덕션에서 스토어를 시작할 때 의 모든 캐시를 활성화합니다. **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 페이지를 가리키도록 업데이트하는 중입니다. 다음을 사용하는 것이 좋습니다. [!DNL Varnish]: 효율적인 프로덕션 페이지 캐시 솔루션입니다.

## 비동기 이메일 알림

&quot;비동기 이메일 알림&quot; 설정을 활성화하면 이메일 알림 체크 아웃 및 주문 처리를 처리하는 프로세스가 백그라운드로 이동합니다. 이 기능을 사용하려면 다음 위치로 이동하십시오. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 다음을 참조하십시오 [영업 이메일](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 다음에서 _Magento Open Source 사용 안내서_ 추가 정보.

## 비동기 주문 데이터 처리

상점가의 집중 매물이 동시에 발생할 수 있습니다. [!DNL Commerce] 에서는 집중 주문 처리를 수행하고 있습니다. 다음을 구성할 수 있습니다. [!DNL Commerce] 데이터베이스 수준에서 이 두 트래픽 패턴을 구별하여 해당 테이블의 읽기 및 쓰기 작업 간의 충돌을 방지합니다. 주문 데이터를 비동기식으로 저장하고 인덱싱할 수 있습니다. 주문이 임시 저장소에 보관되고 충돌 없이 Order Management 그리드로 일괄 이동됩니다. 에서 이 옵션을 활성화할 수 있습니다. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 다음을 참조하십시오 [예약된 그리드 업데이트](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 다음에서 _Magento Open Source 사용 안내서_ 추가 정보.

>[!WARNING]
>
>다음 **[!UICONTROL Developer]** 탭 및 옵션은 다음 위치에서만 사용할 수 있습니다. [개발자 모드](../configuration/cli/set-mode.md). [클라우드 인프라의 Adobe Commerce](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 은(는) 을 지원하지 않습니다. `Developer` 모드.

## 비동기 구성 저장

저장소 수준 구성이 많은 프로젝트의 경우 저장소 구성을 저장하는 데 과도한 시간이 소요되거나 시간 초과가 발생할 수 있습니다. 다음 _비동기 구성_ 모듈은 소비자를 사용하여 메시지 큐의 저장을 처리하는 cron 작업을 실행하여 비동기 구성을 저장할 수 있습니다. 비동기 구성: **비활성화됨** 기본적으로.

명령줄 인터페이스를 사용하여 AsyncConfig를 활성화할 수 있습니다.

```bash
bin/magento setup:config:set --config-async 1
```

다음 `set` 명령은 다음 내용을 `app/etc/env.php` 파일:

```conf
...
   'config' => [
       'async' => 1
   ]
```

다음 소비자를 시작하여 선입선출 방식으로 대기열에 있는 메시지 처리를 시작합니다.

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## 지연된 재고 업데이트

집중 판매 시기에는 [!DNL Commerce] 주문과 관련된 재고 갱신을 연기할 수 있습니다. 이를 통해 작업 수를 최소화하고 주문 배치 프로세스를 가속화할 수 있습니다. 그러나 이 옵션은 재고량이 마이너스로 이어질 수 있으므로 위험성이 있으며 스토어에서 미납주문이 활성화된 경우에만 사용할 수 있습니다. 이 옵션은 주문형 재고를 쉽게 다시 채울 수 있는 스토어의 체크아웃 플로우에서 상당한 성능 향상을 가져올 수 있습니다. 사이트에서 지연된 재고 갱신을 활성화하려면 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 다음을 참조하십시오 [재고 관리](https://docs.magento.com/user-guide/catalog/inventory.html) 다음에서 _Adobe Commerce 사용 안내서_ 추가 정보.

>[!INFO]
>
>이 옵션은 다음 경우에만 사용할 수 있습니다. **[!UICONTROL Backorder with any mode]** 활성화되었습니다.

>[!INFO]
>
>이 옵션은 에서도 작동합니다. [비동기 주문 배치](high-throughput-order-processing.md#asynchronous-order-placement) 과 조화하여 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## 클라이언트측 최적화 설정

상점가의 응답성을 개선하려면 [!DNL Commerce] 인스턴스를 기본 또는 개발자 모드에서 관리자로 이동하여 다음 설정을 변경합니다.

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 설정 그룹 | 설정 | 값 |
| ------------------- | -------------------------- | ------ |
| 그리드 설정 | 비동기 인덱싱 | 사용 |
| CSS 설정 | CSS 파일 축소 | 예 |
| [!DNL JavaScript] 설정 | 축소 [!DNL JavaScript] 파일 | 예 |
| [!DNL JavaScript] 설정 | 사용 [!DNL JavaScript] 번들 | 예 |
| 템플릿 설정 | 축소 HTML | 예 |

>[!INFO]
>
>다음 **[!UICONTROL Developer]** 탭 및 옵션은 다음 위치에서만 사용할 수 있습니다. [개발자 모드](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] 클라우드 인프라에서](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 은(는) 을 지원하지 않습니다. `Developer` 모드.

를 활성화하면 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 옵션을 사용하면 Commerce에서 모든 JS 리소스를 상점 첫 페이지에 로드된 하나 또는 번들 세트로 병합할 수 있습니다. JS를 번들링하면 서버에 대한 요청이 줄어들어 페이지 성능이 향상됩니다. 또한 브라우저가 JS 리소스를 첫 번째 호출에 캐시하고 이후의 모든 탐색에 다시 사용할 수 있도록 지원합니다. 또한 모든 JS가 텍스트로 로드되므로 이 옵션은 소극적 평가도 제공합니다. 페이지에서 특정 작업이 트리거된 후에만 코드 분석 및 평가를 시작합니다. 그러나 모든 JS 콘텐츠는 첫 번째 호출에서 로드되므로 첫 번째 페이지 로드 시간이 매우 중요한 저장소에는 이 설정이 권장되지 않습니다.

>[!INFO]
>
>다음을 참조하십시오 [클라우드 인프라 및 Adobe Commerce의 Adobe Commerce에서 CSS 및 Javascript 파일 최적화](https://support.magento.com/hc/en-us/articles/360044482152) css 및 Javascript 최적화에 대한 자세한 내용은 Adobe Commerce 도움말 센터 를 참조하십시오.

### 번들링 팁

* 축소 및 번들링(예: [r.js](https://requirejs.org/)). [!DNL Commerce] 기본 제공 메커니즘은 최적의 상태가 아니며 대체 메커니즘으로 제공됩니다.
* HTTP/2 프로토콜을 활성화하면 JS 번들링을 사용하는 대신 사용할 수 있습니다. 프로토콜은 많은 동일한 이점을 제공한다. 클라우드 인프라 프로젝트의 Adobe Commerce에서 기본적으로 활성화됩니다.
* JS 및 CSS 파일은 페이지의 HEAD 섹션에서 동기적으로 로드된 JS용으로만 설계되었으므로 병합과 같이 더 이상 사용되지 않는 설정을 사용하지 않는 것이 좋습니다. 이 기술을 사용하면 번들링 및 requireJS 논리가 제대로 작동하지 않을 수 있습니다.

## 고객 세그먼트 유효성 검사

숫자가 많은 상인들 [고객 세그먼트](https://docs.magento.com/user-guide/marketing/customer-segments.html) 은 고객 로그인 및 장바구니에 제품 추가와 같은 고객 작업에 대해 상당한 성능 저하를 경험할 수 있습니다.

고객 작업은 고객 세그먼트에 대한 유효성 검사 프로세스를 트리거하며, 이로 인해 성능이 저하될 수 있습니다. 기본적으로 Adobe Commerce은 각 세그먼트를 실시간으로 확인하여 일치하는 고객 세그먼트와 일치하지 않는 고객 세그먼트를 정의합니다.

성능 저하를 방지하려면 **[!UICONTROL Real-time Check if Customer is Matched by Segment]** 시스템 구성 옵션 대상 **아니요** 결합된 단일 조건 SQL 쿼리를 통해 고객 세그먼트의 유효성을 검사합니다.

이 최적화를 사용하려면 다음 위치로 이동하십시오. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

이 설정은 시스템에 고객 세그먼트가 많은 경우 고객 세그먼트 유효성 검사 성능을 향상시킵니다. 그러나 에서는 작동하지 않습니다 [데이터베이스 분할](../configuration/storage/multi-master.md) 구현 또는 등록된 고객이 없는 경우.

## 데이터베이스 유지 관리 일정 {#database}

스테이징 및 프로덕션 인스턴스에 대해 정기적인 데이터베이스 백업을 수행하는 것이 좋습니다. 백업 작업의 I/O 집약적 특성으로 인해 백업 속도가 느려지고 잠재적인 문제가 발생할 수 있습니다. 여러 환경에 대해 데이터베이스 프로세스를 동시에 실행하면 사용 가능한 리소스에 대한 경합으로 인해 속도가 느려질 수 있습니다.

성능을 향상시키려면 백업이 사용량이 적은 시간에 한 번에 하나씩 연속적으로 실행되도록 예약하십시오. 이 방법을 사용하면 입출력 경합을 방지하고 특히 작은 인스턴스, 큰 데이터베이스 등의 경우 완료 시간을 줄일 수 있습니다.

예를 들어 스토어에서 방문 횟수가 적을 경우 준비 데이터베이스가 뒤따르는 프로덕션 데이터베이스의 백업을 예약하는 것이 좋습니다.

## 그리드의 제품 수 제한

대형 카탈로그의 제품 그리드 성능을 향상시키려면 를 사용하여 그리드의 제품 수를 제한하는 것이 좋습니다. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** 시스템 구성 설정입니다.

이 시스템 구성 설정은 기본적으로 비활성화되어 있습니다. 활성화하면 그리드의 제품 수를 특정 값으로 제한할 수 있습니다. **[!UICONTROL Records Limit]** 은(는) 최소 기본값이 인 사용자 정의 가능한 설정입니다. `20000`.
다음의 경우 **[!UICONTROL Limit Number of Products in Grid]** 설정이 활성화되고 그리드의 제품 수가 레코드 제한보다 큰 경우 제한된 레코드 컬렉션이 반환됩니다. 제한에 도달하면 검색된 총 레코드, 선택한 레코드 수 및 페이지 매김 요소가 그리드 헤더에서 숨겨집니다.

그리드의 총 제품 수가 제한되는 경우, 제품 그리드 질량 작용에 영향을 미치지 않는다. 제품 격자 프레젠테이션 레이어에만 영향을 줍니다. 예를 들어, 제한된 수의 `20000` 그리드의 제품에서 사용자가 **[!UICONTROL Select All]**&#x200B;를 선택하고 **[!UICONTROL Update attributes]** 대량 작업을 수행하고 일부 속성을 업데이트합니다. 따라서 모든 제품이 업데이트되며, 제한된 컬렉션은 아닙니다. `20000` 레코드.

제품 격자 제한은 UI 구성 요소에서 사용하는 제품 컬렉션에만 영향을 줍니다. 따라서 모든 제품 그리드가 이 제한의 영향을 받는 것은 아닙니다. 사용 중인 항목만 `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
다음 페이지에서만 제품 그리드 컬렉션을 제한할 수 있습니다.

* 카탈로그 제품 표
* 관련/상향 판매/교차 판매 제품 그리드 추가
* 번들 제품에 제품 추가
* 그룹 제품에 제품 추가
* 관리자: 주문 생성 페이지

제품 그리드를 제한하지 않으려는 경우 필터를 보다 정확하게 사용하여 결과 컬렉션에 보다 적은 항목을 포함할 수 있습니다. **[!UICONTROL Records Limit]**.
