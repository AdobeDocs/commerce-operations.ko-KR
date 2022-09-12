---
title: 구성 우수 사례
description: 이러한 우수 사례를 사용하여 Adobe Commerce 또는 Magento Open Source 배포의 응답 시간을 최적화합니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---


# 구성 우수 사례

상거래 에서는 페이지에서 응답 시간을 향상시키고 더 높은 처리량을 제공하는 데 사용할 수 있는 많은 설정 및 도구를 제공합니다.

## 크론 작업

의 모든 비동기 작업 [!DNL Commerce] 는 Linux를 사용하여 수행됩니다 `cron` 명령. 자세한 내용은 [크론 구성 및 실행](../configuration/cli/configure-cron-jobs.md) 를 클릭하여 올바르게 구성합니다.

## 인덱서

인덱서는 다음 중 하나에서 실행할 수 있습니다. **[!UICONTROL Update on Save]** 또는 **[!UICONTROL Update on Schedule]** 모드. 다음 **[!UICONTROL Update on Save]** 모드는카탈로그나 다른 데이터가 변경될 때마다 즉시 색인화됩니다. 이 모드에서는 저장소의 업데이트 및 탐색 작업이 적은 것으로 가정합니다. 이로 인해 많은 로드 중에 상당한 지연과 데이터 가용성이 저하될 수 있습니다. 을 사용하는 것이 좋습니다 **일정에 따라 업데이트** 데이터 업데이트에 대한 정보를 저장하고 특정 cron 작업을 통해 백그라운드에 있는 부분별로 색인화를 수행하므로 프로덕션 모드에서 모드 각 [!DNL Commerce] 색인은  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 구성 페이지.

MariaDB 10.4에서 재색인화를 수행하는 데 다른 MariaDB에 비해 시간이 더 오래 걸립니다 [!DNL MySQL] 버전. 해결 방법으로, 기본 MariaDB 구성을 수정하고 다음 매개 변수를 설정하는 것이 좋습니다.

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## 캐시

프로덕션에서 저장소를 시작할 때 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 페이지. 을 사용하는 것이 좋습니다 [!DNL Varnish]효율적인 프로덕션 페이지 캐시 솔루션이므로

## 비동기 이메일 알림

&quot;비동기 이메일 알림&quot; 설정을 활성화하면 체크아웃 및 주문 처리 이메일 알림을 처리하는 프로세스를 백그라운드로 이동합니다. 이 기능을 사용하려면 다음 위치로 이동하십시오. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 자세한 내용은 [영업 이메일](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 에서 _Magento Open Source 사용 안내서_ 추가 정보.

## 비동기 주문 데이터 처리

매장 전면의 집중 매출이 동시에 발생하는 경우도 있습니다 [!DNL Commerce] 에서는 많은 주문 처리를 수행하고 있습니다. 다음을 구성할 수 있습니다 [!DNL Commerce] 해당 테이블에서 읽기 및 쓰기 작업 간의 충돌을 방지하기 위해 데이터베이스 수준에서 이러한 두 트래픽 패턴을 구분하려면 주문 데이터를 비동기식으로 저장하고 색인화할 수 있습니다. 주문은 임시 스토리지에 배치되고 충돌 없이 Order Management 그리드로 일괄 이동합니다. 다음 위치에서 이 옵션을 활성화할 수 있습니다. **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 자세한 내용은 [예약된 그리드 업데이트](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 에서 _Magento Open Source 사용 안내서_ 추가 정보.

>[!WARNING]
>
>다음 **[!UICONTROL Developer]** 탭과 옵션은 [개발자 모드](../configuration/cli/set-mode.md). [Adobe Commerce on cloud 인프라](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 을 지원하지 않음 `Developer` 모드.

## 지연된 스톡 업데이트

집중 판매 시기에는 [!DNL Commerce] 주문과 관련된 주식 업데이트를 연기할 수 있습니다. 이렇게 하면 작업 수가 최소화되고 주문 배치 프로세스를 가속화할 수 있습니다. 그러나 이 옵션은 위험하며 이 옵션은 음수 재고량으로 이어질 수 있으므로 역주문이 저장소에서 활성화된 경우에만 사용할 수 있습니다. 이 옵션을 사용하면 필요에 따라 재고를 쉽게 다시 채울 수 있는 저장소의 체크아웃 플로우에 상당한 성능 향상을 가져올 수 있습니다. 사이트에서 지연된 스톡 업데이트를 활성화하려면 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 자세한 내용은 [인벤토리 관리](https://docs.magento.com/user-guide/catalog/inventory.html) 에서 _Adobe Commerce 사용 안내서_ 추가 정보.

>[!INFO]
>
>이 옵션은 **[!UICONTROL Backorder with any mode]** 이 활성화되어 있습니다.

## 클라이언트 측 최적화 설정

고객의 저장소 응답성을 향상시키기 위해 [!DNL Commerce] 예를 들어, 기본 또는 개발자 모드에서 관리자로 이동하여 다음 설정을 변경합니다.

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 설정 그룹 | 설정 | 값 |
| ------------------- | -------------------------- | ------ |
| 그리드 설정 | 비동기 색인 지정 | 활성화 |
| CSS 설정 | CSS 파일 축소 | 예 |
| [!DNL JavaScript] 설정 | 축소 [!DNL JavaScript] 파일 | 예 |
| [!DNL JavaScript] 설정 | 활성화 [!DNL JavaScript] 번들링 | 예 |
| 템플릿 설정 | 축소 HTML | 예 |

>[!INFO]
>
>다음 **[!UICONTROL Developer]** 탭과 옵션은 [개발자 모드](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] 클라우드 인프라](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 을 지원하지 않음 `Developer` 모드.

를 활성화하면 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 옵션을 사용하면 Commerce에서 모든 JS 리소스를 storefront 페이지에 로드되는 하나 또는 번들 세트에 병합할 수 있습니다. JS를 번들이면 서버에 대한 요청이 적으므로 페이지 성능이 향상됩니다. 또한 브라우저가 첫 번째 호출 시 JS 리소스를 캐시하고 모든 추가 탐색을 위해 다시 사용하는 데 도움이 됩니다. 모든 JS가 텍스트로 로드되므로 이 옵션은 레이지 평가도 제공합니다. 페이지에서 특정 작업이 트리거된 후에만 코드 분석 및 평가를 시작합니다. 그러나 첫 번째 페이지 로드 시간이 매우 중요한 저장소는 모든 JS 컨텐츠가 첫 번째 호출에 로드되므로 권장되지 않습니다.

>[!INFO]
>
>자세한 내용은 [클라우드 인프라 및 Adobe Commerce에서 Adobe Commerce에 대한 CSS 및 Javascript 파일 최적화](https://support.magento.com/hc/en-us/articles/360044482152) CSS 및 Javascript 최적화에 대한 자세한 내용은 Adobe Commerce 도움말 센터_ 를 참조하십시오.

### 번들 팁

* 축소 및 번들링(예: )에 타사 도구를 사용하는 것이 좋습니다 [r.js](https://requirejs.org/)). [!DNL Commerce] 기본 제공 메커니즘은 최적이 아니며 대체 요소로 제공됩니다.
* HTTP2 프로토콜을 활성화하는 것은 JS 번들링을 사용하는 것과 좋은 대안이 될 수 있습니다. 프로토콜은 거의 동일한 이점을 제공합니다.
* JS 및 CSS 파일 병합과 같이 더 이상 사용되지 않는 설정은 페이지의 HEAD 섹션에서 동기적으로 로드된 JS에만 사용하도록 설계되었으므로 사용하지 않는 설정을 사용하는 것이 좋습니다. 이 기술을 사용하면 번들링 및 requireJS 논리가 잘못 작동할 수 있습니다.

## 데이터베이스 유지 관리 일정 {#database}

스테이징 및 프로덕션 인스턴스에 대해 주기적 데이터베이스 백업을 수행하는 것이 좋습니다. I/O의 집약적인 백업 작업으로 인해 백업 속도가 느려지고 잠재적인 문제가 발생할 수 있습니다. 여러 환경에 대해 동시에 데이터베이스 프로세스를 실행하면 사용 가능한 리소스에 대한 경합 때문에 실행 속도가 느려질 수 있습니다.

성능을 향상시키기 위해 백업을 연속적으로 실행하도록 예약합니다. 한 번에 하나씩, 피크 시간 동안. 이 방법을 사용하면 I/O 경쟁을 피할 수 있고, 특히 더 작은 인스턴스, 더 큰 데이터베이스 등의 경우 완료 시간을 줄일 수 있습니다.

예를 들어 저장소에서 방문 횟수가 적으면 프로덕션 데이터베이스의 백업 다음에 스테이징 데이터베이스를 예약하는 것이 좋습니다.
