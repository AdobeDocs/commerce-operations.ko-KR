---
title: 'ACSD-65822: 번들 및 구성 가능한 제품 수량이 장바구니에 올바르게 반영되지 않음'
description: ACSD-65822 패치를 적용하여 번들 제품을 추가할 때 관리 패널의 고객 장바구니 섹션에 수량이 0으로 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822: 번들 및 구성 가능한 제품 수량이 [!UICONTROL Shopping Cart]에 올바르게 반영되지 않았습니다.

ACSD-65822 패치는 번들 및 구성 가능한 제품 수량이 **[!UICONTROL Shopping Cart]** 아래의 *[!UICONTROL Customer's Activities]* 섹션에 올바르게 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65822입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

번들 및 구성 가능한 제품 수량이 **[!UICONTROL Shopping Cart]** 아래의 *[!UICONTROL Customer's Activities]* 섹션에 올바르게 표시되지 않습니다.

<u>재현 단계</u>:

1. 상점 첫 화면에서 사용자를 만듭니다.
2. 관리 패널에서 **[!UICONTROL Bundle product]**&#x200B;을(를) 만듭니다.
3. 로그인한 사용자는 상점 첫 화면에서 번들 제품을 지정된 수량의 장바구니에 추가합니다.
4. *관리자* 패널에서 **[!UICONTROL Customers]**(으)로 이동하여 1단계에서 만든 고객에 대해 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
5. **[!UICONTROL Create Order]**&#x200B;을(를) 클릭합니다.
6. 왼쪽의 *[!UICONTROL Customer's Activities]*&#x200B;에서 **[!UICONTROL Shopping Cart]** 섹션을 확인하십시오. 선택한 수량과 함께 번들 제품이 표시됩니다.

<u>예상 결과</u>:

번들 품목 수량은 상점 전면의 수량과 일치해야 합니다.

<u>실제 결과</u>:

번들 항목 수량은 0으로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
