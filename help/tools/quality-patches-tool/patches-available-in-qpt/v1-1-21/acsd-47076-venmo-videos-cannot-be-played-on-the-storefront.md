---
title: 'ACSD-47076: [!DNL Vimeo] 비디오가 상점 앞에서 재생될 수 없습니다.'
description: ACSD-47076 패치를 적용하여  [!DNL Vimeo] 비디오가 상점 전면에서 재생될 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Storefront
role: Admin
exl-id: 156b961b-e507-44fe-9b26-d73136e336a9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-47076: [!DNL Vimeo]개의 비디오를 상점 전면에서 재생할 수 없습니다.

ACSD-47076 패치를 사용하면 상점 전면에서 [!DNL Vimeo] 비디오를 재생할 수 없는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-47076입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Vimeo]개의 비디오를 상점 전면에서 재생할 수 없습니다.

<u>재현 단계</u>:

1. Commerce [!UICONTROL Admin] > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > 제품 편집 페이지 > **[!UICONTROL Images and Videos]**&#x200B;에서 제품에 [!DNL Vimeo] 비디오를 추가합니다.
1. 상점에서 제품을 열고 비디오를 재생합니다.

<u>예상 결과</u>:

[!DNL Vimeo] 비디오를 재생할 수 있습니다.

<u>실제 결과</u>:

[!DNL Vimeo] 비디오는 상점 전면에서 재생할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
