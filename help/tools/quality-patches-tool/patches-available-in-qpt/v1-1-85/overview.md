---
title: '개요: [!DNL Quality Patches Tool](QPT) v1.1.85'
description: 이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.85에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
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
