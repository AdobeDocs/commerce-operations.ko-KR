---
title: 'ACSD-62755: [!DNL TinyMCE] 7에는 글꼴 크기와 글꼴이 편집기 초기화 설정에 추가되어야 합니다.'
description: '[!DNL TinyMCE] 7을(를) 사용하려면 *글꼴 크기* 및 *글꼴 패밀리*를 편집기 초기화 설정 내에 구체적으로 추가해야 하는 Adobe Commerce 문제를 해결하려면 ACSD-62755 패치를 적용합니다.'
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%
---
# ACSD-62755: [!DNL TinyMCE] 7에는 글꼴 크기와 글꼴이 편집기 초기화 설정에 추가되어야 합니다.

ACSD-62755 패치는 [!DNL TinyMCE] 7에서 편집기 초기화 설정 내에 *글꼴 크기* 및 *글꼴 패밀리* 선택기를 추가해야 하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 상태에서 사용할 수 있습니다. 패치 ID는 ACSD-62755입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p10

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL TinyMCE] 7을(를) 사용하려면 편집기 초기화 설정 내에 *글꼴 크기* 및 *글꼴 패밀리* 선택기를 구체적으로 추가해야 합니다.

<u>재현 단계</u>:

**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]**(으)로 이동한 다음 *[!UICONTROL Show Editor]*&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

*글꼴 크기* 및 *글꼴 모음* 선택기가 WYSIWYG 편집기에 표시됩니다.

<u>실제 결과</u>:

WYSIWYG 편집기에 *글꼴 크기* 선택기가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
