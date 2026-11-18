---
title: '개요: [!DNL Quality Patches Tool](QPT) v1.1.85'
description: 이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.85에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a094ba2e1af14f7139524bf5fa3ee55b169770d2
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.85

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.85에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.85에는 다음 패치가 포함됩니다.

1. **ACP2E-4929**: **[!UICONTROL Compare Products]** 페이지의 특성 레이블에 현재 저장소 보기 대신 다른 저장소 보기의 번역이 표시되는 문제를 해결했습니다.
1. **ACP2E-5075**: 범주 조건이 있는 고정 금액 장바구니 가격 규칙이 규칙이 번들 상위 제품만 일치할 때 동적 가격 번들 제품의 모든 하위 항목에 할인을 잘못 적용한 문제를 해결했습니다.
1. **ACP2E-5077**: 동시 `customerCart` GraphQL 쿼리 또는 `POST /V1/carts/mine` REST 요청이 아직 활성 카트가 없는 고객에 대해 중복 활성 카트를 만드는 문제를 해결했습니다.
1. **ACP2E-5088**: 세션이 만료되면 고객의 영구 장바구니가 지워지는 문제를 해결합니다.
1. **ACP2E-3991**: 클라이언트 IP 주소가 올바르게 확인되지 않는 문제를 해결했습니다.
1. **ACP2E-5092**: 지역 없이 저장된 회사 주소의 해당 국가에 지역이 추가되면 **[!UICONTROL Company Profile]** 페이지와 관리자 고객 편집 페이지에 오류가 표시되는 문제가 해결되었습니다.
1. **ACP2E-5124**: **[!UICONTROL Validation Strategy]**&#x200B;이(가) **[!UICONTROL Stop on Error]**(으)로 설정되어 있을 때 유효성 검사가 실패한 후 유효성 검사 결과에서 **[!UICONTROL Import]** 단추를 사용할 수 있는 문제를 해결했습니다.
1. **AC-17456**: 관리 패널의 **[!UICONTROL Design Configuration]** 페이지에서 **[!UICONTROL Global]** 범위를 편집하면 PHP 8.4 및 8.5에서 *HTTP 500* 오류가 반환되는 문제가 해결되었습니다.
1. **ACP2E-5212**: **[!UICONTROL Quick Order]**&#x200B;에서 확장명이 `.csv`인 CSV가 아닌 파일을 허용하는 문제를 해결했습니다.
1. **ACP2E-5300**: 키워드 검색에서 관리 패널 **[!UICONTROL Orders]** 그리드에서 공백으로 구분되거나 쉼표로 구분된 여러 주문 번호를 검색하는 경우 일치하는 주문이 반환되지 않는 문제를 해결했습니다.
1. **ACP2E-5354**: REST API를 통해 고객을 업데이트하면 회사 계정과 연결된 고객이 관리 **[!UICONTROL Customers]** 그리드에 여러 번 표시되는 문제가 해결되었습니다.
1. **ACP2E-5208**: 변경 사항이 없는 경우에도 모든 Storefront 페이지 탐색에서 **[!UICONTROL Requisition List]** 섹션이 다시 로드되는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
