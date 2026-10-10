---
title: 'ACSD-50887: *[!UICONTROL Use in Search]* 옵션 없이 *[!UICONTROL Use in Search Results Layered Navigation]*이(가) 예로 설정됨'
description: ACSD-50887 패치를 적용하여 제품 속성 *[!UICONTROL Use in Search Results Layered Navigation]*을(를) *예*로 설정할 수 있고 *[!UICONTROL Use in Search]* 옵션도 *예*로 설정되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;이(가) *[!UICONTROL Use in Search]* 옵션 없이 *예*(으)로 설정됨

ACSD-50887 패치는 *[!UICONTROL Use in Search]* 옵션도 *예*(으)로 설정되지 않고 제품 특성 속성 *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;을(를) *예*(으)로 설정할 수 있는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-50887입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Use in Search]* 옵션도 *예*(으)로 설정하지 않고 제품 특성 속성 *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;을(를) *예*(으)로 설정할 수 있습니다.

이러한 설정은 함께 사용하도록 설계되었습니다. 패치가 적용된 상태에서 *[!UICONTROL Use in Search]* 옵션이 *No*(으)로 설정되어 있으면 *No*(으)로 설정된 것처럼 *[!UICONTROL Use in Search Results Layered Navigation]* 옵션이 작동하지 않습니다.

<u>재현 단계</u>:

1. 관리자에서 **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**(으)로 이동하여 다중 선택 유형의 특성을 만들고 다음을 설정합니다.

   * *[!UICONTROL Use in Search]= 아니요*
   * *[!UICONTROL Use in Layered Navigation]= (모든 옵션)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= 예*
   * *이름 = Test_attribute*
   * *옵션*:
     * *스티커*
     * *선택기*

1. 기본 속성 집합에 새 속성을 추가합니다.
1. 다음 두 가지 제품을 만듭니다.

   1. 첫 번째 제품:
      * 이름 = 스티커
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 옵션 *스티커* 선택

   1. 두 번째 제품:
      * 이름 = 선택기
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 두 옵션 모두 선택

1. `catalogsearch_fulltext` 다시 인덱싱 실행:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 상점 전면에서 *스티커*&#x200B;라는 단어를 검색합니다.

<u>예상 결과</u>:

*[!UICONTROL Use in Search]*&#x200B;이(가) *아니요*(으)로 설정되어 있으면 [!DNL Elasticsearch]에서 Test_attribute를 인덱싱하지 않으므로 *스티커* 제품만 반환됩니다.

<u>실제 결과</u>:

두 제품 모두 반품됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]&#x200B;[&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
