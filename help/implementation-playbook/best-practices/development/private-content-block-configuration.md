---
title: 비공개 콘텐츠 블록에 대한 우수 사례
description: 저장소 성능을 최적화하기 위해 개인 콘텐츠 블록을 구성하는 모범 사례에 대해 배웁니다.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 비공개 콘텐츠 블록에 대한 우수 사례

개인 콘텐츠 블록에 이 포함된 경우 `_isScopePrivate` 변수를 채울 수 없습니다. 비공개 블록이 캐시되지 않으므로 서버 로드를 증가시키는 각 고객 요청에 대해 동일한 데이터를 검색해야 합니다.

를 사용하는 대신 `_isScopePrivate` 개인 컨텐츠에 대한 변수와 사용자가 알 수 없는 데이터를 표시할 블록 및 템플릿을 만듭니다. 이 데이터는 Adobe Commerce에 의해 사용자별 데이터로 대체됩니다 [UI 구성 요소](https://glossary.magento.com/ui-component/)- 사전 렌더링 데이터를 보다 효율적으로 처리합니다. 자세한 내용은 [비공개 컨텐츠](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 에서 _[!DNL Commerce PHP Extensions Guide]_.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 잠재적인 성능 영향

를 포함하는 개인 콘텐츠 블록이 있는 사이트 `_isScopePrivate` 변수는 AJAX 요청을 트리거하여 각 고객 요청에 대해 동일한 데이터를 검색합니다. 이에 따라 응답 시간이 증가하고 고객 등록, 장바구니 업데이트, 주문 제출 및 결제 거래와 같은 비즈니스 크리티컬 상점 운영을 처리하는 데 사용할 수 있는 추가 리소스를 사용합니다.

## 추가 정보

- [비공개 컨텐츠](../../../performance/configuration.md#client-side-optimization-settings)
- [높은 처리량 AJAX 요청으로 인해 성능이 저하됨](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


