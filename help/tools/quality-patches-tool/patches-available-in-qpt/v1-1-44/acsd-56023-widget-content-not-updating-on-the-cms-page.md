---
title: 'ACSD-56023: 위젯 콘텐츠가 CMS 페이지에서 업데이트되지 않음'
description: ACSD-56023 패치를 적용하여 CMS 페이지에서 위젯 콘텐츠가 업데이트되지 않는 Adobe Commerce 문제를 해결합니다
feature: CMS
role: Admin, Developer
exl-id: 723b7f64-ed8a-45f9-9151-f99169cd1a04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56023: 위젯 콘텐츠가 CMS 페이지에서 업데이트되지 않음

ACSD-56023 패치는 CMS 페이지에서 위젯 콘텐츠가 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56023입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

위젯 콘텐츠가 CMS 페이지에서 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 몇 가지 제품을 만듭니다.
1. 새 CMS 페이지를 만들고 콘텐츠에 새 제품 위젯 을 추가합니다.

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. 상점 첫 화면에서 만든 페이지를 엽니다. 캐시해야 합니다.
1. [관리자]에서 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;을(를) 엽니다.
1. 편집할 제품을 선택하고 **[!UICONTROL Set Product as New]**&#x200B;을(를) *예*(으)로 전환하십시오.
1. 상점 첫 화면에서 만든 *CMS 페이지*(으)로 다시 이동합니다.

<u>예상 결과</u>:

페이지에 제품이 포함된 *새 제품 위젯*&#x200B;이 있습니다.

<u>실제 결과</u>:

페이지에 *새 제품 위젯*&#x200B;이 포함되어 있지 않으며 새 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
