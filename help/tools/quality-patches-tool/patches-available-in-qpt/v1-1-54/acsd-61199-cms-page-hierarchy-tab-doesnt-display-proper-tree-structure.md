---
title: 'ACSD-61199: CMS 페이지 [!UICONTROL Hierarchy] 탭에 적절한 트리 구조가 표시되지 않음'
description: 기존 *[!UICONTROL Hierarchy]*이(가) 있는 Adobe Commerce 페이지를 편집할 때 CMS 페이지의 *[!UICONTROL Hierarchy]* 탭에 적절한 트리 구조가 표시되지 않는 CMS 문제를 해결하려면 ACSD-61199 패치를 적용합니다.
feature: Page Content
role: Admin, Developer
source-git-commit: bbe4e272d3a8bd82163bdd718d006a314287b650
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: CMS 페이지의 [!UICONTROL Hierarchy] 탭에 적절한 트리 구조가 표시되지 않음

ACSD-61199 패치는 기존 *[!UICONTROL Hierarchy]*&#x200B;을(를) 사용하여 CMS 페이지를 편집할 때 CMS 페이지의 *[!UICONTROL Hierarchy]* 탭에 적절한 트리 구조가 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61199입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

기존 *[!UICONTROL Hierarchy]*&#x200B;을(를) 사용하여 CMS 페이지를 편집할 때 CMS 페이지의 *[!UICONTROL Hierarchy]* 탭에 적절한 트리 구조가 표시되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**(으)로 이동합니다.
1. 새 **[!UICONTROL CMS page]** 만들기 *[!UICONTROL Hierarchy]*&#x200B;의 웹 사이트 루트에 추가됩니다.
1. 페이지를 저장합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**(으)로 이동합니다.
1. *[!UICONTROL Hierarchy]*&#x200B;에 다른 기존 페이지를 추가합니다.
1. *[!UICONTROL Hierarchy]* 저장.
1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**(으)로 이동합니다.
1. 기존 페이지를 편집하고 *[!UICONTROL Hierarchy]*&#x200B;을(를) 엽니다.

<u>예상 결과</u>:

*[!UICONTROL Hierarchy]*&#x200B;이(가) 예상대로 로드됩니다.

<u>실제 결과</u>:

*[!UICONTROL Hierarchy]*&#x200B;이(가) 탭에 로드되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

[[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
