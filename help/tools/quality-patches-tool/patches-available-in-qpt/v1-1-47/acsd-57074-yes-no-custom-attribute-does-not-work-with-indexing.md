---
title: 'ACSD-57074: *Yes/No* ''attribute_code'' 속성에 ''price_*'' 접두사가 있는 사용자 지정 속성이 색인화에서 작동하지 않음'
description: ACSD-57074 패치를 적용하여 'attribute_code' 속성에 'price_*' 접두사가 있는 *Yes/No* 사용자 지정 속성이 색인화에서 작동하지 않는 Adobe Commerce 문제를 수정합니다.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: *특성에* 접두사가 있는 `price_*`Yes/No`attribute_code` 사용자 지정 특성이 인덱싱에서 작동하지 않습니다

ACSD-57074 패치는 *특성에* 접두사가 있는 `price_*`Yes/No`attribute_code` 사용자 지정 특성이 인덱싱과 함께 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.47이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57074입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*특성에* 접두사가 있는 `price_*`Yes/No`attribute_code` 사용자 지정 특성이 인덱싱에서 작동하지 않습니다.

<u>재현 단계</u>:

1. 다음 옵션을 사용하여 사용자 지정 제품 속성을 만듭니다.
   * *[!UICONTROL Catalog Input Type]*: *예/아니요*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *예*
1. 속성을 기본 속성 세트에 지정합니다.
1. 우리가 만든 속성으로 제품을 만듭니다.
1. 방금 만든 제품을 범주에 할당합니다.
1. 전체 색인 재지정을 실행합니다.

<u>예상 결과</u>:

제품이 지정된 카테고리에 표시됩니다.

<u>실제 결과</u>:

해당 제품은 프런트 카테고리 페이지에 나타나지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
