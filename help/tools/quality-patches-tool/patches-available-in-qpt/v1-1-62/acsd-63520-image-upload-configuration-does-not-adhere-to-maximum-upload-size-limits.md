---
title: 'ACSD-63520: 이미지 업로드 구성을 통해 업로드된 이미지가 구성된 크기 제한을 초과합니다.'
description: ACSD-63520 패치를 적용하여 [관리] 패널의 이미지 업로드 구성을 통해 업로드된 이미지가 구성된 최대 업로드 크기 제한을 준수하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63520: [!UICONTROL Image Upload Configuration]을(를) 통해 업로드된 이미지가 구성된 크기 제한을 초과합니다.

ACSD-63520 패치는 [!UICONTROL Images Upload Configuration]을(를) 통해 업로드된 이미지가 구성된 최대 업로드 크기 제한을 준수하지 않는 문제를 해결합니다. 이 문제를 해결하려면 [!UICONTROL Admin] 패널에서 [!UICONTROL Images Upload Configuration] 설정을 구성하십시오. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-63520입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 [!DNL Adobe Commerce] 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인하십시오. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Admin] 패널의 [!UICONTROL Images Upload Configuration]을(를) 통해 업로드된 이미지는 최대 업로드 크기 제한을 준수하지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** 패널에 로그인합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]**(으)로 이동하여 다음을 설정합니다.
   * 품질: 100
   * 프론트엔드 크기 조정 활성화: 예
   * 최대 너비: 800
   * 최대 높이: 600
1. **[!UICONTROL Media Gallery Image Optimization]**&#x200B;을(를) 확장하고 다음을 설정합니다.
   * 이미지 최적화 활성화: 예
   * 최대 너비: 1000
   * 최대 높이: 1000
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**(으)로 이동합니다.
   1. **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** 및 **[!UICONTROL Price]**&#x200B;을(를) 추가합니다.
   1. **[!UICONTROL Create Configurations]**&#x200B;을(를) 클릭하고 **[!UICONTROL Attributes]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
   1. 크기(S, M, L, XL)를 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
   1. **[!UICONTROL Images]**&#x200B;에서 **[!UICONTROL Apply single set of images to all SKUs]**&#x200B;을(를) 선택합니다.
   1. 이미지를 업로드하고(최소 1024x1024) **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
   1. **[!UICONTROL Generate Product]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

이미지는 구성된 업로드 크기 및 크기 조정 제한을 따라야 합니다.

<u>실제 결과</u>:

이미지 크기가 조정되지 않으며 구성된 업로드 크기 제한을 초과합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
