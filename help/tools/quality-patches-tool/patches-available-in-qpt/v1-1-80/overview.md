---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.80'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.80에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: f8a08611109d9c8e5e686e0c451b0a58ecc12e21
workflow-type: tm+mt
source-wordcount: 596
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.80

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.80에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.80에는 다음 패치가 포함됩니다.

1. **ACP2E-4239**: 날짜 특성을 사용하는 관리자 그리드 필터가 선택한 날짜, 저장된 UTC 값 및 구성된 저장소 시간대 간의 시간대 차이로 인해 잘못된 결과를 반환하는 문제를 해결했습니다.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: **[!UICONTROL Login as Customer]** 흐름 동안 `quote` 데이터베이스 테이블에서 null 견적 레코드가 생성되는 문제를 해결합니다.
1. **ACP2E-4481**: 주문이 취소된 후 번들 제품 판매량이 올바르게 계산되지 않는 문제를 해결했습니다.
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)**: 특성 집합이 큰 제품에 대해 Admin에서 제품을 저장하거나 편집하는 것이 느려지는 문제를 해결했습니다.
1. **ACP2E-4493**: 비동기 인덱싱이 활성화된 경우 판매 주문 보관 그리드에 잘못된 주문 상태가 표시되는 문제가 해결되었습니다.
1. **ACP2E-4496**: analytics cron 작업이 실행 중에 성능 저하를 일으켜 전체 시스템 성능이 향상되는 문제를 해결했습니다.
1. **ACP2E-4533**: 스토어 코드가 URL에 포함되어 있을 때 자리 표시자 이미지가 Storefront에서 로드되지 않는 문제를 해결했습니다.
1. **ACP2E-4552**: GraphQL 응답에서 회사 상태가 반환되지 않는 문제를 해결했습니다.
1. **[ACP2E-4610](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610.md)**: `sales_clean_quotes` cron 작업에 성능 문제가 있는 문제를 해결했습니다.
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)**: GraphQL 응답에서 회사 상태가 반환되지 않는 문제를 해결했습니다.
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)**: analytics cron 작업이 실행 중에 성능 저하를 일으켜 전체 시스템 성능이 향상되는 문제를 해결했습니다.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: 스토어 코드가 URL에 포함되어 있을 때 자리 표시자 이미지가 상점 앞에 로드되지 않는 문제를 해결했습니다.
1. **ACP2E-4610**: `sales_clean_quotes` cron 작업에 성능 문제가 있는 문제를 해결했습니다.
1. **[ACP2E-4615](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615.md)**: *PayPal 게이트웨이가 요청을 거부한다는 PayPal 오류가 발생하여 온라인 주문 환불이 실패하는 문제를 해결합니다. 내부 오류입니다.*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)**: 일부 Storefront JavaScript 파일이 두 번 요청 및 실행되어 간헐적인 중복 로드와 불안정한 동작이 발생하는 문제를 해결했습니다.
1. **ACP2E-4653**: REST API를 통해 규칙을 검색하거나 업데이트할 때 **[!UICONTROL Category (Parent Only)]** 및 **[!UICONTROL Category (Children Only)]**&#x200B;에 대한 **[!UICONTROL Cart Price Rule]** 조건 특성 범위가 노출되지 않는 문제를 해결했습니다.
1. **ACP2E-4808**: storefront 제품 페이지의 Weight 속성에 구성된 측정 단위(lbs 또는 kgs) 없이 **[!UICONTROL Additional Information]** 또는 **[!UICONTROL More Information]** 섹션의 원시 숫자 값만 표시되는 문제를 해결합니다.
1. **[ACP2E-4813](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813.md)**: 체크아웃 시 USPS 배송 방법을 사용할 수 없으며 여러 패키지로 분할된 주문을 포함하여 특정 제품에 대한 배송 예상 가격이 올바르지 않은 문제를 해결했습니다.
1. **ACP2E-4626**: 일부 Storefront JavaScript 파일이 두 번 요청 및 실행되어 간헐적인 중복 로드와 불안정한 동작이 발생하는 문제를 해결했습니다.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: [!DNL REST] API를 통해 규칙을 검색하거나 업데이트할 때 **[!UICONTROL Category (Parent Only)]** 및 **[!UICONTROL Category (Children Only)]**&#x200B;에 대한 장바구니 가격 규칙 조건 특성 범위가 노출되지 않는 문제를 해결했습니다.
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: storefront 제품 페이지의 Weight 속성에 구성된 측정 단위(lbs 또는 kgs) 없이 **[!UICONTROL Additional Information]** 또는 **[!UICONTROL More Information]** 섹션의 원시 숫자 값만 표시되는 문제를 해결합니다.
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: [!DNL REST] API의 배송 주소 유효성 검사가 Admin에 정의된 특성 구성을 따르지 않는 문제를 해결했습니다.
1. **ACP2E-4813**: 체크아웃 시 USPS 배송 방법을 사용할 수 없으며 여러 패키지로 분할된 주문을 포함하여 특정 제품에 대한 배송 예상 가격이 올바르지 않은 문제를 해결했습니다.
1. **[ACSD-53502](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502.md)**: New Relic 모니터링 스크립트에 대한 재귀적 호출로 인해 iOS [!DNL Safari]의 상점 앞부분에서 **[!UICONTROL Add to Cart]**&#x200B;이(가) 간헐적으로 실패하여 페이지가 다시 로드되는 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
