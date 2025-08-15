---
title: '개요: [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: 이 하위 섹션에서는  [!DNL Quality Patches Tool] (QPT) v1.1.64에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 개요: [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.64

이 하위 섹션에서는 [!DNL Quality Patches Tool]&#x200B;(QPT) v1.1.64에서 사용할 수 있는 패치로 해결된 문제에 대한 자세한 설명을 제공합니다.

QPT v1.1.64에는 다음 패치가 포함됩니다.

1. **ACP2E-3838**: [!DNL Page Builder] CORS 오류로 인해 프로덕션 모드의 관리 패널에 변경 내용이 저장되지 않는 문제를 해결했습니다.
1. **ACP2E-3841**: `subselect` 조건이 사용되고 **[!UICONTROL Free Shipping]**&#x200B;이(가) 활성화된 경우 다중 배송 제품에 대한 장바구니 가격 규칙이 올바르게 적용되지 않는 문제를 해결했습니다.
1. **ACSD-63139**: 제품 특성에 수천 개의 옵션 값이 들어 있을 때 제품 내보내기가 실패하는 문제를 해결했습니다.
1. **ACSD-65100**: **[!UICONTROL Maximum Width]** 구성에서 **[!UICONTROL Maximum Height]** 및 **[!UICONTROL Media Gallery Image Optimization]**&#x200B;의 값을 제거하면 이미지 최적화 프로세스 중에 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-65127**: 프로덕션 모드에서 JavaScript 축소를 사용하면 [!DNL TinyMCE] 6에서 브라우저 콘솔에 오류가 발생하여 기능과 사용자 환경에 영향을 주는 문제를 해결했습니다.
1. **ACSD-65787**: 테이블 데이터를 처리할 때 정의되지 않은 배열 키 `SchemaBuilder`열&#x200B;*(으)로 인해 스키마를 만들거나 업데이트하는 동안* 클래스가 충돌하는 문제를 해결했습니다.
1. **ACSD-65223**: [!DNL B2B] 구매 주문에 대해 수동으로 선택한 약관 및 계약으로 인해 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-65540**: `REGEXP_LIKE` 테이블을 업데이트할 때 `company_structure` 함수가 없어서 SQL 구문 오류가 발생하는 문제를 해결했습니다.
1. **ACSD-65684**: `Magento_Company` 테이블에서 많은 레코드(~100,000+)를 처리할 때 [!DNL B2B] 1.5.2로 업데이트한 후 `company_structure` 모듈을 업그레이드하는 데 시간이 너무 오래 걸리는 성능 문제를 해결했습니다.

왼쪽의 메뉴를 사용하여 특정 패치 페이지로 이동합니다.
