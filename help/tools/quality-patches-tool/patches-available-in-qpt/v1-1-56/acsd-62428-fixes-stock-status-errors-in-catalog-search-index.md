---
title: 'ACSD-62428: 카탈로그 검색 색인의 재고 상태 오류'
description: SKU가 검색 가능한 속성으로 설정되지 않은 경우 카탈로그 검색 색인의 'is_out_of_stock' 값이 잘못 설정되는 문제를 해결하려면 ACSD-62428 패치를 적용합니다.
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: 카탈로그 검색 색인의 재고 상태 오류

ACSD-62428 패치는 SKU 특성이 검색 가능으로 설정되지 않은 경우 카탈로그 검색 색인의 `is_out_of_stock` 값이 잘못된 값으로 설정되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56에서 사용할 수 있습니다. 패치 ID는 ACSD-62428입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

SKU가 검색 가능한 속성으로 구성되지 않아 재고 표현이 정확하지 않은 경우 카탈로그 검색 색인의 `is_out_of_stock` 값이 잘못된 값으로 설정되었습니다.

<u>재현 단계</u>:

1. 사용자 지정 [!UICONTROL Source] 및 사용자 지정 [!UICONTROL Stock]을(를) 만듭니다.
1. 간단한 제품 3개를 만들고 인벤토리를 사용자 지정 [!UICONTROL Source]에 할당합니다. 이러한 제품을 범주에 할당합니다.
1. 보다 쉬운 복제를 위해 *[!UICONTROL Inventory (MSI) Indexer]*&#x200B;을(를) *[!UICONTROL Update on Save]*(으)로 설정하십시오.
1. *[!UICONTROL Source Item Status]*&#x200B;을(를) *[!UICONTROL In Stock]*(으)로 설정하고 *[!UICONTROL Quantity]*&#x200B;을(를) 할당합니다.
1. 제품을 저장합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동하여 **[!UICONTROL SKU]** 특성을 엽니다.
1. *[!UICONTROL Use In]*&#x200B;을(를) *[!UICONTROL No]*(으)로 설정합니다.
1. 제품 수량을 변경합니다(0으로 설정되지 않았는지 확인).
1. 제품을 저장합니다.

<u>예상 결과</u>:

SKU가 검색 가능한 특성이 아닌 경우에도 `is_out_of_stock` 값은 제품의 재고 상태를 정확하게 반영합니다.

<u>실제 결과</u>:

`is_out_of_stock` 값이 1로 잘못 설정되어 있고 SKU 특성이 인덱싱된 데이터에 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
