---
title: 'ACSD-45675: 제품 내보내기에서 기본 스토어 보기 범위의 카테고리 이름을 사용합니다.'
description: ACSD-45675 패치는 제품 내보내기가 기본 스토어 보기 범위의 카테고리 이름을 사용하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45675입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# ACSD-45675: 제품 내보내기에서 기본 스토어 보기 범위의 카테고리 이름을 사용합니다.

ACSD-45675 패치는 제품 내보내기가 기본 스토어 보기 범위의 카테고리 이름을 사용하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45675입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 내보내기는 기본 스토어 보기 범위의 카테고리 이름을 사용합니다.

<u>재현 단계</u>:

1. 기본 저장소 내에 사용자 지정 저장소 보기 **[!UICONTROL Thai]**&#x200B;을(를) 만듭니다.
1. **[!UICONTROL Thai]**&#x200B;을(를) 기본 웹 사이트의 기본 스토어 보기로 설정합니다.
1. **[!UICONTROL Default Category]** 아래에 다음 범주 구조를 만듭니다.

   *[!UICONTROL Default category/Tea/Black]*

1. **[!UICONTROL Tea]** 범주를 선택하고 **[!UICONTROL Scope]**&#x200B;을(를) **[!UICONTROL Thai]**(으)로 변경합니다.
1. **[!UICONTROL Category Name]**&#x200B;을(를) **[!UICONTROL ชาดำ]**(으)로 설정합니다.
1. 간단한 제품 **[!UICONTROL SP001]**&#x200B;을(를) 만들고 범주 **[!UICONTROL Black]**&#x200B;을(를) 할당합니다.
1. 크론이 실행되지 않도록 하십시오.
1. 제품 내보내기를 수행합니다. SKU별로 필터링하고 **[!UICONTROL SP001]**&#x200B;을(를) 선택합니다.
1. 내보낸 CSV에서 **[!UICONTROL categories]** 열을 확인합니다.

<u>예상 결과</u>:

내보내는 동안 스토어를 선택하지 않았으므로 다음과 같은 범주 경로가 필요합니다. *[!UICONTROL Default Category/Tea/Black]*.

<u>실제 결과</u>:

범주 경로에 혼합 언어가 있습니다. *[!UICONTROL Default Category/ชาดำ/Black]*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 품질 패치 도구 안내서의 [[!DNL Quality Patches Tools] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
