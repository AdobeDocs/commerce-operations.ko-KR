---
title: 'ACSD-62755: [!DNL TinyMCE] 7에는 글꼴 크기와 글꼴이 편집기 초기화 설정에 추가되어야 합니다.'
description: ACSD-62755 패치를 적용하여  [!DNL TinyMCE] 7에서 *글꼴 크기* 및 *글꼴 패밀리*를 편집기 초기화 설정 내에 특별히 추가해야 하는 Adobe Commerce 문제를 해결합니다.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
source-git-commit: 4aba81ea12cc08370881d3cc108e94ba410a2198
workflow-type: tm+mt
source-wordcount: '305'
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
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
