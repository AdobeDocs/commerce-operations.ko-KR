---
title: 'ACSD-62118: [!UICONTROL Purchase Order] 메서드를 사용하여 수행한 B2B 주문에 대해 ''sales_order_tax_item'' 테이블이 완전히 업데이트되지 않음'
description: ACSD-62118 패치를 적용하여 [!UICONTROL Purchase Order] 메서드를 사용하여 B2B 주문을 할 때 'sales_order_tax_item' 테이블이 완전히 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62118: [!UICONTROL Purchase Order] 메서드를 사용하여 수행한 B2B 주문에 대해 `sales_order_tax_item` 테이블이 완전히 업데이트되지 않았습니다.

ACSD-62118 패치는 *[!UICONTROL Purchase Order]* 메서드를 사용하여 B2B 주문을 할 때 `sales_order_tax_item` 테이블이 완전히 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62118입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Purchase Order]* 메서드를 사용하여 B2B 주문을 수행하면 `sales_order_tax_item` 테이블이 완전히 업데이트되지 않습니다. 이 문제는 세금 계산 및 주문 처리에 영향을 줍니다. 특히 API를 통해 순서를 쿼리할 때 `applied_taxes` 배열이 비어 있으며 `tax_item_amount`과(와) `tax_item_percent`이(가) 모두 NULL입니다.

<u>재현 단계</u>:

1. **[!UICONTROL Product]**&#x200B;과(와) **[!UICONTROL Shipping]** 모두에 대한 세금 규칙을 추가합니다.
1. 회사 설정에서 **[!UICONTROL Purchase Order]** 메서드를 사용하도록 설정합니다.
1. 회사 관리자 사용자로 로그인합니다.
1. 오프라인 결제 방법을 사용하여 **[!UICONTROL Purchase Order]**&#x200B;을(를) 배치합니다.
1. [!UICONTROL Purchase Order]이(가) 자동 승인되고 주문으로 변환된 후 `sales_order_tax_item` 테이블과 REST API를 통해 세금 데이터를 확인하십시오.

<u>예상 결과</u>:

* `sales_order_tax_item` 테이블에는 `tax_item` 데이터가 있어야 합니다.
* `applied_taxes` 배열은 다른 결제 방법(예: 수표/금전 주문)과 마찬가지로 구매 주문에 대한 API 응답에 올바른 세금 정보를 표시해야 합니다.

<u>실제 결과</u>:

* `sales_order_tax_item` 테이블에 `tax_item` 데이터가 없습니다.
* *[!UICONTROL Purchase Order]*&#x200B;에 대한 API 응답에서 `applied_taxes` 및 `item_applied_taxes` 배열이 비어 있습니다.
* *[!UICONTROL Purchase Order]* 결제 방법을 사용할 때 세금 데이터가 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
