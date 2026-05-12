---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.79'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.79에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a8666ceccfe78536a624c67227692c98a521f555
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.79

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.79에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.79에는 다음 패치가 포함됩니다.
1. **ACP2E-4402**: 사용하지 않도록 설정된 제품이 사용하도록 설정된 후 관련 [!UICONTROL Target Rule] 결과에 다시 추가되지 않는 문제를 해결했습니다.
1. **ACP2E-4505**: 중복 브라우저 탭에서 오래된 데이터가 있는 범주를 저장하여 순환 종속성을 만들 수 있는 문제를 해결했습니다.
1. **ACP2E-4531**: CMS 페이지의 URL 키를 변경해도 페이지의 계층 URL이 업데이트되지 않는 문제를 해결했습니다.
1. **ACP2E-4601**: 특정 조건에서 결제 트랜잭션 처리가 비효율적으로 작동할 수 있는 문제를 해결했습니다.
1. **ACP2E-4603**: [!UICONTROL Catalog Permissions] 제품 다시 인덱스를 실행하면 기존 권한 인덱스 행이 변경되지 않아 업데이트된 범주 권한 부여가 제품에 안정적으로 반영되지 않는 문제를 해결했습니다.
1. **ACP2E-4706**: [!UICONTROL Target Rule] 인덱서가 [!UICONTROL Admin] 범위에서 활성화되지 않은 제품을 건너뛰는 문제를 해결했습니다.
1. **ACP2E-4720**: 장바구니 할인 규칙이 있는 번들 제품에 대해 무료 배송이 제대로 적용되지 않거나 제거되지 않는 문제를 해결했습니다.
1. **ACP2E-4411**: 장바구니 페이지와 여러 통화 스토어의 미니 장바구니에 번들 제품에 대해 잘못된 가격이 표시되는 문제를 해결했습니다.
1. **ACP2E-4475**: **[!UICONTROL Display Out of Stock Products]** 옵션이 활성화된 경우 제품 목록 페이지에서 가격 기준으로 품절 번들 제품을 잘못 필터링하고 정렬하는 문제가 수정되었습니다.
1. **ACP2E-4110**: 특별 가격이 포함된 번들 제품에 기본값이 아닌 통화로 PDP 및 PLP에 잘못된 금액이 표시되는 문제를 해결했습니다.
1. **AC-10698**: 시스템이 통화를 개별 주문과 연결하는 대신 모든 주문 수준에서 통화를 보내는 문제를 해결했습니다. 이제 주문당 거래 가격 및 합계가 [!DNL Google Tag]에 전송되어 전자 상거래 데이터 추적 정확도가 향상되었습니다.
1. **AC-10737**: `bin/magento setup:db:status` 명령이 JSON 데이터 형식을 인식하지 못하는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
