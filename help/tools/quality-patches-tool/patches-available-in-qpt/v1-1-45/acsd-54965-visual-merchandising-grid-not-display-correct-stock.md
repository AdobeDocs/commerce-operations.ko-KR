---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] 그리드에 올바른 재고가 표시되지 않습니다.'
description: ACSD-54965 패치를 적용하여 제품이 사용자 지정 재고에 할당될 때 [!UICONTROL Visual Merchandising] 그리드에 올바른 재고가 표시되지 않는 Adobe Commerce 문제를 수정하십시오.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] 그리드에 올바른 재고가 표시되지 않습니다.

ACSD-54965 패치는 제품이 사용자 지정 재고에 할당될 때 [!UICONTROL Visual Merchandising] 그리드에 올바른 재고가 표시되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-54965입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 사용자 지정 스톡에 할당되면 [!UICONTROL Visual Merchandising] 그리드에 올바른 스톡이 표시되지 않습니다.

<u>재현 단계</u>:

1. 새 소스를 만듭니다.
1. 새 재고를 생성합니다.
1. 다음 두 가지 제품을 만듭니다.
   * 사용자 정의 재고가 있는 하나의 제품만.
   * 기본 재고가 있는 하나의 제품만.
1. 이 제품을 범주에 추가합니다.
1. [!UICONTROL visual Merchandising] 눈금(*[!UICONTROL Products in Category]*)으로 이동합니다.

<u>실제 결과</u>:

*[!UICONTROL All Store Views]* 범위에서 사용자 지정 재고가 있는 제품에 수량이 표시되지 않습니다. *[!UICONTROL Default Store View]* 범위를 선택한 경우에만 사용자 지정 스톡에 제품 수량이 표시됩니다.

<u>예상 결과</u>:

범위가 *[!UICONTROL All Store Views]*&#x200B;인 경우 격자에 모든 재고 정보가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
