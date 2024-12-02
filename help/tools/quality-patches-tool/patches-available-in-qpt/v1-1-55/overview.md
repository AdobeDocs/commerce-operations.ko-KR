---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.55에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
source-git-commit: 29845fd4a8c1c744aa780e60bb4154dfc3c1a02c
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool](QPT) v1.1.55

이 하위 섹션에서는 [!DNL Quality Patches Tool](QPT) v1.1.55에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.55에는 다음 패치가 포함됩니다.

1. **ACSD-58383**: 동시에 실행되는 두 개의 동일한 요청으로 [!DNL REST API]을(를) 통해 환불을 발행하고 중복 대변 메모를 만드는 문제를 해결했습니다.
1. **ACSD-58471**: 연결된 카탈로그 가격 규칙이 예정되어 있을 때 제품 세부 정보 페이지에서 동적 콘텐츠를 로드하지 못하는 문제를 해결했습니다.
1. **ACSD-58566**: `addPurchaseOrderComment` 돌연변이의 `created_at` 필드를 쿼리할 때 [!DNL GraphQL]에서 내부 서버 오류를 반환하는 문제를 해결했습니다.
1. **ACSD-58685**: 전자 메일 통신을 사용하지 않도록 설정한 상태에서 시작된 판매 전자 메일이 전자 메일 통신을 다시 사용하도록 설정한 후에도 계속 전송되는 문제를 해결했습니다.
1. **ACSD-58735**: 제한된 관리자가 연결된 웹 사이트의 [!UICONTROL Admin]에 있는 고객 계정 페이지에서 구매하지 않은 장바구니를 볼 수 없는 문제를 해결했습니다.
1. **ACSD-58828**: 클라이언트측 유효성 검사 메시지와 함께 필수 필드가 비어 있는 경우 서버측 유효성 검사 메시지 *주소가 필요함*&#x200B;이(가) 표시되는 문제를 해결합니다. 서버측 유효성 검사에는 빈 필수 필드에 대한 메시지가 표시되지 않으며 클라이언트측 유효성 검사에서는 오류 알림을 처리합니다. *필수 필드입니다.*
1. **ACSD-60344**: 자동 승인으로 **[!UICONTROL Purchase Order]**&#x200B;을(를) 사용할 때 중복 주문 확인 전자 메일이 전송되는 문제가 해결되었습니다.
1. **ACSD-61348**: 위시리스트 항목이 [!DNL GraphQL]을(를) 통해 표시되지만 다중 웹 사이트 환경의 상점 앞에는 표시되지 않는 문제를 해결했습니다.
1. **ACSD-61534**: `bin/magento config:set` 명령을 사용하여 디자인 구성을 설정할 수 없고 잠긴 값은 양식 조작을 통해 변경할 수 있는 문제를 해결했습니다. `--lock-env` 또는 `--lock-conf`을(를) 사용하여 [!DNL CLI]에서 설정된 잠긴 값은 업데이트할 수 없습니다.
1. **ACSD-61785**: `reward_update_notification`과(와) 동작을 맞추면서 [!DNL GraphQL] 돌연변이 및 [!DNL REST API] 호출을 통해 `reward_warning_notification` 특성을 업데이트할 수 없는 문제를 해결했습니다.
1. **ACSD-62591**: **[!UICONTROL User Agent Rules]**&#x200B;을(를) 구성할 때 테마가 제대로 전환되지 않는 문제를 해결했습니다.
1. **ACSD-62793**: 내보낸 데이터의 `datetime` 특성에 시간 구성 요소가 없는 문제를 해결했습니다. 또한 *[!UICONTROL Fields Enclosure]*&#x200B;이(가) *enabled*&#x200B;인 경우 `additional_attributes` 열의 특성 값은 큰따옴표로 묶입니다.
1. **ACSD-62332**: 제품 목록 [!DNL GraphQL] 쿼리가 10,000개 제품 중 `total_count`(으)로 제한되는 문제를 해결했습니다. 또한 [!DNL GraphQL]을(를) 통해 쿼리할 때 [!DNL Live Search]이(가) 검색 기준에서 현재 페이지를 *2* 페이지 대신 *1*(으)로 설정하는 문제를 해결합니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
