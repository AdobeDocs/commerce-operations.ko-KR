---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# 10월 보안 패치에 포함된 핫픽스(2.4.4 제외)

이 릴리스에는 Braintree 결제 게이트웨이 관련 문제를 해결하기 위한 핫픽스가 포함되어 있습니다.

이 시스템에는 이제 결제 게이트웨이로 Braintree을 사용할 때 3DS VISA 위임 요구 사항을 이행하는 데 필요한 필드가 포함됩니다. 이를 통해 모든 거래가 VISA가 정한 최신 보안 표준을 준수하도록 할 수 있다. 이전에는 이러한 추가 필드가 전송된 결제 정보에 포함되지 않아 새로운 비자 요건을 준수하지 않을 수 있었습니다.

<!--
BUNDLE-3360
-->