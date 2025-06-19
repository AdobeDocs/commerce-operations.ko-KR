---
title: 'ACSD-59967: JavaScript 오류로 인해  [!DNL Google Maps] 이(가) 올바르게 렌더링되지 않습니다.'
description: ACSD-59967 패치를 적용하여 JavaScript 오류로 인해  [!DNL Google Maps] 이(가) 올바르게 렌더링되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967: JavaScript 오류로 인해 [!DNL Google Maps]이(가) 올바르게 렌더링되지 않습니다.

ACSD-59967 패치는 JavaScript 오류로 인해 [!DNL Google Maps]이(가) 올바르게 렌더링되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-59967입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

JavaScript 오류로 인해 [!DNL Google Maps]이(가) 올바르게 렌더링되지 않습니다.

<u>재현 단계</u>:

1. 올바른 [!DNL Google Maps] 키를 생성합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**&#x200B;에서 [!DNL Google Maps] API 키를 구성합니다.
1. **[!UICONTROL Google Maps API Key]** 필드에 [!DNL Google API Key]을(를) 추가하고 구성을 저장합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**(으)로 이동합니다.
1. **[!UICONTROL Row]** 요소 및 **[!UICONTROL Maps]** 요소를 추가합니다.

<u>예상 결과</u>:

콘솔에 JavaScript 오류가 없으며 맵이 *Storefront* 및 *Admin*&#x200B;에서 제대로 렌더링됩니다.

<u>실제 결과</u>:

JavaScript 오류가 콘솔에 표시되고 맵이 제대로 렌더링되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
