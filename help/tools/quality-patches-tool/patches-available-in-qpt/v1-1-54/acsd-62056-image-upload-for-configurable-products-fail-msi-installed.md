---
title: 'ACSD-62056: MSI가 설치된 경우 구성 가능한 제품에 대한 이미지 업로드가 실패합니다'
description: MSI가 설치된 경우 구성 가능한 제품에 대한 이미지가 추가되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-62056 패치를 적용합니다.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: MSI가 설치된 경우 구성 가능한 제품에 대한 이미지 업로드가 실패합니다

ACSD-62056 패치는 MSI가 설치된 경우 구성 가능한 제품에 대한 이미지가 추가되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-62056입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Inventory Management/MSI]이(가) 활성화된 구성 가능한 제품을 편집할 때 이미지 추가 옵션이 작동하지 않습니다. [!UICONTROL Apply a single set of images to all SKUs] 및 [!UICONTROL Apply unique images by attribute to each SKU] 옵션에 모두 영향을 줍니다.

<u>필수 구성 요소</u>:

[!UICONTROL Inventory Management/MSI]개의 모듈이 설치되고 사용하도록 설정되었습니다.

<u>재현 단계</u>:

1. 새 소스를 만듭니다.
1. 새 재고를 생성하고 새 출처를 지정합니다.
1. 구성 가능한 제품을 편집합니다.
1. **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 다음 중 하나를 선택하고 이미지를 추가합니다.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>예상 결과</u>:

이미지가 추가됩니다.

<u>실제 결과</u>:

이미지가 추가되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
