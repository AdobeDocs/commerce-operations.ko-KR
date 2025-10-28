---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.72에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3493a89d40e3dee377be715e71e2f977a3afd382
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.72

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.72에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.72에는 다음 패치가 포함됩니다.
1. **ACSD-68040**: [!DNL MariaDB] 10.6에서 프론트엔드 검색 페이지의 속도가 느려집니다.
1. **ACSD-67941**: 필터 이름을 알 수 없는 GraphQL 요청으로 인해 PHP 예외 로그가 발생합니다.
1. **ACSD-68064**: 예약된 업데이트를 만들면 중첩된 범주가 많은 환경에서 항목이 중복됩니다.
1. **ACSD-66807**: `report_viewed_product_index` 테이블에 제품 페이지 보기 수가 잘못되었습니다.
1. **ACSD-67383**: 같은 세션에 두 개의 회사 관리자 계정을 사용하여 고객으로 로그인하면 *cartId가 있는 해당 엔터티가 없음* 오류가 발생합니다.
1. **ACSD-67518**: 행 수가 배치 크기를 초과하면 고급 보고에서 중복된 머리글 행을 생성합니다.
1. **ACSD-67639**: **[!UICONTROL Dynamic Price]**&#x200B;이(가) *아니요*(으)로 설정된 번들 제품에 대해 대변 메모를 만들지 못했습니다.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: 캐시 플러시 후 `media_gallery`개의 항목이 장바구니 GraphQL 제품 노드에서 반환되지 않습니다.
1. **ACSD-67946**: 장바구니 업데이트에 중복 오류 배너가 표시됩니다.
1. **ACSD-68011**: /V1/sharedCatalog/:id/assignProducts API를 통해 공유 카탈로그에 할당된 존재하지 않는 SKU입니다.
1. **ACSD-68118**: `customerCart` [!DNL GraphQL] 쿼리가 스토어 보기에 대해 잘못된 제품 특성 값을 반환합니다.
1. **ACSD-68092**: 예약된 업데이트와 기본 제품 데이터 간의 부적절한 동기화로 인해 다중 저장 후 번들 제품 옵션이 손실됩니다.
1. **ACSD-67424**: `updated_at` `GET /carts/search` API 응답의 [!DNL REST] 값이 협상 가능한 견적을 사용할 때 **[!UICONTROL Admin panel]**&#x200B;에 표시된 값과 일치하지 않습니다.
1. **ACSD-67187**: 기본이 아닌 웹 사이트로 제한된 관리 사용자에게 오류가 표시됩니다. *&quot;*계속하려면 적어도 공개 공유 카탈로그를 만드십시오*. 회사 그리드의 **[!UICONTROL Add New Company]** 단추에 액세스할 수 없습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
