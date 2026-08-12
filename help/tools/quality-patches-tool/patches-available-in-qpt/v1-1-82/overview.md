---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.82'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.82에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 2864bda142df307248f5e29524eaf42441538f5b
workflow-type: tm+mt
source-wordcount: 489
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.82

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.82에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.82에는 다음 패치가 포함됩니다.

1. **ACP2E-4815**: 로그에 PHP 예외를 발생시킨 여러 GraphQL 문제를 수정하고, GraphQL을 통해 주문 후 생성된 고객 계정과의 주문 연결을 수정하고, HTTP 사양을 통해 GraphQL과의 응답을 정렬합니다.
1. **ACP2E-4194**: GraphQL 응답이 잘못되거나 승인되지 않았거나 잘못된 요청에 대해 잘못된 HTTP 상태 코드를 반환하는 문제를 해결했습니다.
1. **[ACP2E-4682](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682.md)**: 견적 isActive 상태를 확인하는 Storefront 페이지를 방문하면 페이지가 로드될 때마다 빈 견적 레코드가 생성되는 문제를 해결합니다.
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)**: 관리자가 관리자의 **[!UICONTROL Add Products By SKU]**&#x200B;을(를) 사용하여 기본 카탈로그의 제품을 공유 카탈로그에 연결되어 있지 않은 고객 그룹에 할당된 회사의 주문에 추가할 수 없는 문제를 해결했습니다.
1. **[ACP2E-4593](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593.md)**: 다중 웹 사이트 배포의 보조 웹 사이트에서 웹 사이트 제한에 대해 표시되는 CMS 페이지가 잘못될 수 있는 문제를 해결했습니다.
1. **ACP2E-4695**: 카탈로그 규칙 인덱서가 과도한 메모리를 사용하고 완료하지 못해 불안정하고 메모리 부족 오류가 발생하는 문제를 해결했습니다.
1. **[ACP2E-4698](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698.md)**: 페이지 빌더 텍스트 콘텐츠에서 이미지를 다시 편집하면 이식 가능한 미디어 지시문을 유지하는 대신 절대 미디어 URL을 저장할 수 있는 문제를 해결했습니다.
1. **[ACP2E-4797](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797.md)**: 데이터베이스가 utf8mb4를 지원하도록 구성된 경우에도 관리자의 WYSIWYG 편집기 또는 페이지 빌더 콘텐츠에 4바이트 유니코드 문자 입력이 잘못 차단되는 문제를 해결했습니다.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**: 보상 포인트 내역이 큰 스토어에서 보상 포인트 만료가 느리게 실행되어 보상 포인트 만료가 지연되는 문제를 해결했습니다.
1. **[ACP2E-4799](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799.md)**: `requisition_lists GraphQL` 쿼리가 쿼리 기준과 일치하는 총 구매요청 목록 수 대신 현재 페이지의 항목 수만 반영하는 `total_count` 값을 반환하는 문제를 해결했습니다.
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**: 첫 번째 판매 가능한 하위 제품이 목록에 늦게 나타날 때 하위 제품이 많은 구성 가능한 제품에 대해 체크아웃 API 요청이 상당히 느려지는 문제를 해결했습니다.
1. **ACP2E-4840**: `products` GraphQL 쿼리에서 요청한 수량 값이 *null*&#x200B;을 반환하는 문제를 해결했습니다.
1. **[ACP2E-4870](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870.md)**: 제품 경고 전자 메일 알림이 스토어 보기 전자 메일 설정을 무시하는 문제를 해결했습니다.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**: 관리자에서 주소록이 큰 고객 계정을 볼 때 예기치 않게 관리자 사용자가 기록되는 문제가 해결되었습니다.
1. **[ACP2E-4894](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894.md)**: 대량 저장소에서 **[!UICONTROL Asynchronous Indexing]**&#x200B;을(를) 사용하도록 설정한 경우 새 주문이 Admin Order Management 그리드에 표시되는 것이 지연되는 문제를 해결했습니다.
1. **ACP2E-4981**: 페이지 빌더 제품 회전 메뉴에 관리자의 위치가 반영되지 않은 순서로 제품이 표시되고 일치하는 하위 제품이 개별적으로 표시될 때 구성 가능한 제품을 포함하는 문제가 수정되었습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
