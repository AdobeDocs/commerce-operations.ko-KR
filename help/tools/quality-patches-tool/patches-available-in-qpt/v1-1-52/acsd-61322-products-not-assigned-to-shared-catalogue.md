---
title: 'ACSD-61322: [!UICONTROL Shared Catalogue]에 할당되지 않은 제품이 XML 사이트 맵에 포함되어 있습니다.'
description: ACSD-61322 패치를 적용하여 기본(일반) 그룹의 [!UICONTROL Shared Catalog]에 할당되지 않은 제품/범주가 여전히 XML 사이트 맵에 포함된 Adobe Commerce 문제를 해결합니다.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: [!UICONTROL Shared Catalogue]에 할당되지 않은 제품이 XML 사이트 맵에 포함되어 있습니다.

ACSD-61322 패치는 기본(일반) 그룹의 [!UICONTROL Shared Catalog]에 할당되지 않은 제품/범주가 여전히 XML 사이트 맵에 포함되어 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61322입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기본(일반) 그룹의 [!UICONTROL Shared Catalog]에 할당되지 않은 제품/범주는 여전히 XML 사이트 맵에 포함됩니다.

<u>재현 단계</u>:

1. 몇 가지 카테고리를 만들고 제품을 추가합니다(예: 카테고리 2가 있는 카테고리 1).
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**(으)로 이동하여 *[!UICONTROL Company and Shared Catalog]*&#x200B;을(를) 활성화합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**(으)로 이동하여 기본 카탈로그를 수정하십시오.
1. **[!UICONTROL Select]** 드롭다운에서 **[!UICONTROL Set Pricing and Structure]**&#x200B;을(를) 선택하고 **[!UICONTROL Configure]**&#x200B;을(를) 클릭합니다.
1. *범주 1 > 범주 2* 범주 아래에서 [!UICONTROL Shared Catalog]에 있지 않아야 하는 일부 제품을 선택 취소합니다.
1. **[!UICONTROL Next]**&#x200B;을(를) 클릭하고 카탈로그를 생성합니다.
1. 상점 첫 화면에서 고객 계정을 만듭니다.
1. *범주 1 > 범주 2* 범주로 이동합니다. [!UICONTROL Shared Catalog]에 할당된 제품만 표시됩니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]**(으)로 이동하여 새 사이트 맵을 생성합니다.
1. Storefront에서 `sitemap.xml`을(를) 엽니다.
1. [!UICONTROL Shared Catalog]에 포함하지 않은 제품을 검색합니다.

<u>예상 결과</u>:

사이트 맵에 [!UICONTROL Shared Catalog]에 할당되지 않은 제품 및 범주에 대한 링크가 포함되어 있지 않습니다.

<u>실제 결과</u>:

사이트 맵에 [!UICONTROL Shared Catalog]에 할당되지 않은 제품 및 범주에 대한 링크가 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
