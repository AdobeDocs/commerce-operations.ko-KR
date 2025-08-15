---
title: 'ACSD-66118: [!UICONTROL Store View Code]을(를) 새로 고치지 않으면 [!UICONTROL Design Configuration]을(를) 업데이트하면 [!UICONTROL Configuration Cache] 설정이 지워집니다.'
description: '[!UICONTROL Store View Code]을(를) 제대로 새로 고치지 않은 경우 [!UICONTROL Design Configuration]을(를) 업데이트하면 [!UICONTROL Configuration Cache]​(테마 및 사용자 지정 설정)이 지워지는 Adobe Commerce 문제를 해결하려면 ACSD-66118 패치를 적용하십시오.'
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 468c780f355c99cf06d557e530e81c414a01961e
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-66118: **[!UICONTROL Store View Code]**&#x200B;을(를) 새로 고치지 않으면 **[!UICONTROL Design Configuration]**&#x200B;을(를) 업데이트하면 **[!UICONTROL Configuration Cache]** 설정이 지워집니다.

ACSD-66118 패치는 **[!UICONTROL Store View Code]**&#x200B;을(를) 새로 고치지 않으면 **[!UICONTROL Design Configuration]**&#x200B;을(를) 업데이트하면 **[!UICONTROL Configuration Cache]** 설정이 지워지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-66118입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Design Configuration]**&#x200B;을(를) 새로 고치지 않으면 **[!UICONTROL Store View Code]** 필드를 업데이트할 때 **[!UICONTROL Configuration Cache]** 설정(테마 및 사용자 지정 설정 등)이 지워집니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** 패널에 로그인합니다.
2. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**(으)로 이동합니다.
3. **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**&#x200B;에서 구성된 사용자 지정 테마가 있는 스토어 보기를 편집합니다.
4. **[!UICONTROL Code]** 필드를 변경합니다(예: `storeview_1`에서 `storeview_main`).
5. 변경 내용을 저장하려면 **[!UICONTROL Save Store View]**&#x200B;을(를) 클릭합니다.
6. 업데이트된 **[!UICONTROL Content]**&#x200B;의 *[!UICONTROL Design]* > **[!UICONTROL Configuration]** > **[!UICONTROL Store View]** 페이지를 새로 고치거나 다시 열면 테마가 선택되지 않습니다.

<u>예상 결과</u>:

**[!UICONTROL Store View Code]**&#x200B;을(를) 업데이트한 후에는 **[!UICONTROL Design Configuration]**(테마 및 사용자 지정 설정 포함)이 그대로 유지되어야 합니다.

<u>실제 결과</u>:

**[!UICONTROL Design Configuration]**&#x200B;이(가) 지워졌습니다. 테마는 기본값으로 되돌아가고 사용자 지정 설정은 손실됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
