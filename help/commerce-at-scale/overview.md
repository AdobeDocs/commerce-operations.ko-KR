---
title: 규모에 맞게 경험 제공
description: Adobe Commerce 및 Adobe Experience Manager을 통해 규모에 맞게 경험을 전달하는 방법을 알아봅니다.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Adobe Commerce, Commerce Integration Framework 및 Adobe Experience Manager을 통해 규모에 맞게 경험을 제공합니다

CIF를 커넥터로 사용하는 AEM과 Adobe Commerce 간의 권장 통합 패턴은 AEM이 프레젠테이션 레이어(&quot;유리&quot;)를 소유하고 Adobe Commerce이 상거래 백엔드를 &quot;headless&quot; 백엔드로 제공하는 것입니다. 이 통합 접근 방식은 AEM의 작성, 개인화 및 옴니채널 기능과 Adobe Commerce의 전자 상거래 작업 등 각 애플리케이션의 장점을 활용합니다.

AEM/CIF/Adobe Commerce 환경에서는 전자 상거래 사이트 방문자가 처음에 AEM에 도착합니다. AEM은 요청된 페이지를 디스패처 캐시에 사용할 수 있는지 확인합니다. 페이지가 존재하면 이 캐시된 페이지가 방문자에게 제공되며 추가 처리가 필요하지 않습니다. Dispatcher에 요청된 페이지가 포함되어 있지 않거나 만료된 경우 Dispatcher는 AEM 게시자에게 페이지 작성을 요청하고, 게시자는 필요한 경우 전자 상거래 데이터에 대해 Adobe Commerce을 호출하여 페이지를 작성합니다. 그런 다음 빌드된 페이지가 방문자에게 제공될 디스패처에 전달되고 캐시되므로 다른 방문자의 동일한 페이지에 대한 후속 요청 시 서버에 추가 로드가 배치될 필요가 없습니다.

![Adobe Experience Manager 및 Adobe Commerce 아키텍처 개요 다이어그램](../assets/commerce-at-scale/overview.png)

AEM/CIF/Adobe Commerce 모델에서는 서버측 렌더링과 클라이언트측 렌더링을 결합하여 사용할 수 있습니다. 서버측 렌더링은 정적 콘텐츠를 전달하고 클라이언트측 렌더링은 자주 변경되거나 개인 다이내믹 콘텐츠를 전달하며, 사용자의 브라우저 내에서 특정 구성 요소에 대해 Adobe Commerce을 직접 호출합니다.

제품 세부 사항 페이지의 AEM 전자 상거래 상점 예제의 여러 구성 요소에 대한 예는 아래 예에서 확인할 수 있습니다.

![Adobe Experience Manager 및 Adobe Commerce 아키텍처 개요 다이어그램](../assets/commerce-at-scale/product-details-page.svg)

## 서버측 렌더링

PDP(제품 세부 사항 페이지) 및 PLP(제품 목록 페이지)와 같은 전자 상거래 페이지는 자주 변경되지 않으며 AEM CIF 핵심 구성 요소를 사용하여 서버측에서 렌더링된 후 완전히 캐시되는 데 적합합니다. 페이지는 AEM에서 만든 일반 템플릿을 사용하여 AEM 게시자에서 렌더링해야 합니다. 이러한 구성 요소는 GraphQL API를 통해 Adobe Commerce에서 데이터를 가져옵니다. 이러한 페이지는 동적으로 생성되고, 서버에 렌더링되고, AEM Dispatcher에 캐시된 다음 브라우저에 전달됩니다. 이에 대한 예는 위 예의 자주색 상자에 나와 있습니다.

## 클라이언트측 렌더링

예를 들어 PDP(Product Detail Page)와 같은 재고 수준/가용성 또는 가격과 같은 보다 동적 속성이 표시되는 경우 클라이언트측 구성 요소를 사용할 수 있습니다. 위의 서버측 렌더링 접근 방식을 사용하여 템플릿 페이지를 Dispatcher에 빌드하고 캐시할 수 있지만 정적 페이지 자체 내에 동적 클라이언트측 웹 구성 요소가 있을 수 있습니다. 이러한 동적 구성 요소는 GraphQL API를 통해 Adobe Commerce에서 클라이언트의 브라우저에서 직접 데이터를 가져와 PDP에서 실시간으로 현재 가격 또는 재고 수준을 확인할 수 있습니다. 이렇게 하면 일반적으로 실시간으로 표시되어야 하는 콘텐츠를 항상 페이지 로드 시 가져올 수 있습니다. 이에 대한 예는 위 예의 빨간색 상자에 나와 있습니다.

체크아웃 프로세스 중에 AEM 템플릿과 클라이언트측 렌더링을 함께 사용할 수도 있습니다. 클라이언트측 장바구니 구성 요소는 장바구니를 렌더링하고, 체크아웃 양식과 결제 서비스 공급자와의 통합을 수행합니다. 이 하이브리드 접근 방식은 계정 만들기, 계정에 로그인 및 잊어버린 암호와 같은 Adobe Commerce의 계정 관리 기능에도 사용할 수 있습니다.
