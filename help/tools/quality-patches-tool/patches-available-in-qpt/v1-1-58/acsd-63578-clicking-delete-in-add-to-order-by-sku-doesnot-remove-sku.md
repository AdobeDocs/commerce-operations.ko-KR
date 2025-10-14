---
title: 'ACSD-63578: [!UICONTROL Delete]에서 [!UICONTROL Add to Order by SKU] 아이콘을 클릭해도 SKU가 제거되지 않습니다.'
description: ACSD-63578 패치를 적용하여 관리자의 [!UICONTROL Delete]에서 [!UICONTROL Add to Order by SKU] 아이콘을 클릭해도 SKU가 제거되지 않는 Adobe Commerce 문제를 수정하십시오.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: **[!UICONTROL Delete]**&#x200B;에서 *[!UICONTROL Add to Order by SKU]* 아이콘을 클릭해도 SKU가 제거되지 않습니다.

ACSD-63578 패치는 관리자의 **[!UICONTROL Delete]**&#x200B;에서 *[!UICONTROL Add to Order by SKU]* 아이콘을 클릭해도 SKU가 제거되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63578입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자의 **[!UICONTROL Delete]**&#x200B;에서 *[!UICONTROL Add to Order by SKU]* 아이콘을 클릭해도 주문에서 SKU가 제거되지 않습니다.

<u>재현 단계</u>:

1. 관리자 > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동한 다음 **[!UICONTROL Create New Order]**&#x200B;을(를) 클릭합니다.
1. 고객을 선택합니다.
1. **[!UICONTROL Add to Order by SKU]**&#x200B;을(를) 클릭합니다.
   * SKU를 입력합니다.
   * **[!UICONTROL Add another]** 단추를 클릭합니다.
1. **[!UICONTROL Delete]** 아이콘을 클릭합니다.

<u>예상 결과</u>:

* 제품이 추가되고 관리자의 주문에서 제거됩니다.

<u>실제 결과</u>:

* **[!UICONTROL Delete]** 아이콘이 작동하지 않습니다.
* 콘솔에 오류가 있습니다.

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
