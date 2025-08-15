---
title: 'ACSD-60267: 구성 가능한 제품 옵션을 통해 제품을 추가할 때 FPT가 잘못 적용됩니다.'
description: ACSD-60267 패치를 적용하여 간단한 제품을 장바구니에 직접 추가할 때 고정 제품 세금(FPT)이 올바르게 적용되지만 구성 가능한 제품 옵션을 통해 동일한 제품을 선택할 경우 실패하는 Adobe Commerce 문제를 수정합니다.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: 구성 가능한 제품 옵션을 통해 제품을 추가할 때 FPT가 잘못 적용됩니다.

ACSD-60267 패치는 간단한 제품을 장바구니에 직접 추가할 때 고정 제품 세금(FPT)이 올바르게 적용되지만 구성 가능한 제품 옵션을 통해 동일한 제품을 선택할 경우 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko) 1.1.54가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60267입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고정 제품 세금(FPT)은 FPT가 있는 간단한 제품을 장바구니에 추가할 때 제대로 작동하지만 구성 가능한 제품 선택을 통해 제품을 추가할 때는 FPT가 추가되지 않습니다.

<u>재현 단계</u>:

1. *[!UICONTROL Enable FPT]*&#x200B;관리자&#x200B;*>* > *>* > **[!UICONTROL Configuration]**(으)로 이동하여 **[!UICONTROL Sales]**&#x200B;을(를) **[!UICONTROL Tax]**&#x200B;예&#x200B;**[!UICONTROL Fixed Product Taxes]**(으)로 설정합니다.
1. FPT 특성을 만들어 *[!UICONTROL Attribute Set]*&#x200B;에 할당합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;을(를) 엽니다.
1. *[!UICONTROL Default Label]*&#x200B;에 대해 특성을 식별하는 레이블을 입력하십시오.
1. *[!UICONTROL Catalog Input for Store Owner]*&#x200B;을(를) *[!UICONTROL Fixed Product Tax]*(으)로 설정합니다.
1. 새 세금 및 영역을 만들어 새 *[!UICONTROL Tax Rule]*&#x200B;에 할당합니다.
1. 두 가지 간단한 제품으로 구성 가능한 제품을 만들 수 있습니다.
1. 이제 이러한 간단한 제품에 두 개의 다른 FPT 값을 할당합니다.
1. 상점에서 가격을 다시 매기고 확인하십시오.
1. 제품을 장바구니에 추가하고 소계를 확인합니다.

<u>예상 결과</u>:

* *[!UICONTROL Catalog]* 페이지에는 FPT를 포함한 가격이 표시됩니다.
* 장바구니의 소계에는 FPT가 포함됩니다.

<u>실제 결과</u>:

* *[!UICONTROL Catalog]* 페이지에 FPT 값을 포함한 가격이 표시되지 않습니다.
* 소계 및 요약이 잘못되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
