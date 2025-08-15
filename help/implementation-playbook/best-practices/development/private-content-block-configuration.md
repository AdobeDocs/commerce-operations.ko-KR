---
title: 비공개 콘텐츠 블록에 대한 우수 사례
description: 상점 성능을 최적화하기 위해 개인 콘텐츠 블록을 구성하는 모범 사례에 대해 알아봅니다.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# 비공개 콘텐츠 블록에 대한 우수 사례

개인 콘텐츠 블록에 `_isScopePrivate` 변수가 포함되어 있으면 블록을 캐시할 수 없습니다. 비공개 블록은 캐시되지 않으므로 Adobe Commerce은 각 고객 요청에 대해 동일한 데이터를 검색해야 서버 로드가 증가합니다.

비공개 콘텐츠에 대해 `_isScopePrivate` 변수를 사용하는 대신 사용자와 관계없는 데이터를 표시할 블록 및 템플릿을 만드십시오. 이 데이터는 Adobe Commerce UI 구성 요소에 의해 사용자별 데이터로 대체되므로 렌더링 데이터를 보다 효율적으로 처리할 수 있습니다. 지침은 [의 ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)개인 콘텐츠&#x200B;_[!DNL Commerce PHP Extensions Guide]_를 참조하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 성능에 영향을 미칠 수 있음

`_isScopePrivate` 변수가 포함된 개인 콘텐츠 블록이 있는 사이트는 각 고객 요청에 대해 동일한 데이터를 검색하도록 AJAX 요청을 트리거합니다. 이렇게 하면 응답 시간이 늘어나고 고객 등록, 장바구니 업데이트, 주문 제출 및 결제 거래와 같은 비즈니스 크리티컬한 상점 운영을 처리하는 데 사용할 수 있는 추가 리소스가 사용됩니다.

## 추가 정보

- [비공개 콘텐츠](../../../performance/configuration.md#client-side-optimization-settings)
- [처리량이 많은 AJAX 요청으로 인해 성능이 저하됨](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
