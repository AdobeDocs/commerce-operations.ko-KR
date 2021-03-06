---
title: 규모에 맞게 경험 제공
description: Adobe Commerce 및 Adobe Experience Manager을 사용하여 경험을 규모에 맞게 전달하는 방법을 알아봅니다.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Adobe Commerce, Commerce Integration Framework 및 Adobe Experience Manager을 사용하여 규모에 맞게 경험을 제공합니다

CIF를 커넥터로 사용하는 AEM과 Adobe Commerce 간의 권장 통합 패턴은 AEM에서 프레젠테이션 레이어(&quot;glass&quot;)를 소유하고 Adobe Commerce에서 상거래 백엔드를 &quot;헤드리스&quot; 백엔드로 구동하는 것입니다. 이 통합 접근 방식은 각 애플리케이션의 장점을 활용합니다. Adobe Commerce의 AEM 및 전자 상거래 작업의 작성, 개인화 및 옴니채널 기능.

AEM/CIF/Adobe Commerce 환경에서는 전자 상거래 사이트 방문자가 처음에 AEM에 도달합니다. AEM은 디스패처 캐시에서 사용할 수 있는 요청된 페이지가 있는지 확인합니다. 페이지가 존재하는 경우, 이 캐시된 페이지는 방문자에게 전달되며, 추가 처리가 필요하지 않습니다. 디스패처가 요청한 페이지를 포함하지 않거나 만료된 경우 디스패처가 필요한 경우 eCommerce 데이터를 위해 Adobe Commerce을 호출하여 페이지 작성을 AEM 게시자에게 요청합니다. 그런 다음 작성된 페이지가 방문자에게 제공하도록 디스패처에 전달되고 캐시되므로 다른 방문자의 후속 요청에서 서버에 추가 로드를 배치할 필요가 없습니다.

![Experience Manager 및 Adobe Commerce 아키텍처의 개요 다이어그램](../assets/commerce-at-scale/overview.png)

서버측 렌더링 및 클라이언트측 렌더링의 조합은 AEM/CIF/Adobe Commerce 모델에서 사용할 수 있습니다. 사용자 브라우저 내에서 특정 구성 요소에 대해 Adobe Commerce을 직접 호출하여 정적 콘텐츠 및 클라이언트측 렌더링을 전달함으로써 자주 변경되거나 개인 동적 콘텐츠를 전달할 수 있는 서버측 렌더링입니다.

AEM 전자 상거래 상점 예제의 제품 세부 사항 페이지에 있는 여러 구성 요소의 예는 아래 예에서 볼 수 있습니다.

![Experience Manager 및 Adobe Commerce 아키텍처의 개요 다이어그램](../assets/commerce-at-scale/product-details-page.svg)

## 서버측 렌더링

제품 세부 사항 페이지(PDP) 및 제품 목록 페이지(PLP)와 같은 전자 상거래 페이지는 자주 변경되지 않으며, AEM CIF 코어 구성 요소를 사용하여 서버 측에서 렌더링된 후 완전히 캐시되도록 적합합니다. AEM에서 만든 일반 템플릿을 사용하여 페이지를 AEM 게시자에서 렌더링해야 합니다. 이러한 구성 요소는 GraphQL API를 통해 Adobe Commerce에서 데이터를 가져옵니다. 이러한 페이지는 동적으로 작성되어 서버에서 렌더링되고 AEM 디스패처에서 캐시된 다음 브라우저에 전달됩니다. 위의 예에서 보라색 상자에 이러한 예제가 표시됩니다.

## 클라이언트측 렌더링

PDP(Product Detail Page)와 같이 재고 수준/가용성 또는 가격과 같은 동적 속성이 표시되는 경우 클라이언트측 구성 요소를 사용할 수 있습니다. 위의 서버측 렌더링 접근 방식을 사용하여 템플릿 페이지를 디스패처에 작성하고 캐시할 수 있지만 정적 페이지 자체 내에서 동적 클라이언트측 웹 구성 요소가 있을 수 있습니다. 이러한 동적 구성 요소는 GraphQL API를 통해 Adobe Commerce에서 클라이언트의 브라우저에서 직접 데이터를 가져와 PDP에서 실시간 현재 가격 또는 재고 수준을 확인할 수 있습니다. 이렇게 하면 일반적으로 실시간으로 표시되어야 하는 컨텐츠가 페이지 로드 시 항상 가져오게 됩니다. 위의 예에서 빨간색 상자에 예제가 표시됩니다.

AEM 템플릿과 클라이언트측 렌더링 조합을 체크아웃 프로세스 중에 사용할 수도 있습니다. 클라이언트측 장바구니 구성 요소는 장바구니, 체크아웃 양식 및 결제 서비스 공급자와의 통합을 렌더링합니다. 이 하이브리드 접근 방식은 계정 만들기, 계정 로그인 및 잊어버린 암호와 같은 Adobe Commerce 계정 관리 기능에도 사용할 수 있습니다.
