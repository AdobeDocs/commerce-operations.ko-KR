---
title: 'ACSD-63299: 구성 가능한 제품에 대한 특별 가격이 상점 앞에 표시되지 않음'
description: ACSD-63299 패치를 적용하여 특별 가격 속성이 구성 가능한 제품의 특별 가격 표시에 더 이상 영향을 주지 않는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: 구성 가능한 제품에 대한 특별 가격이 상점 앞에 표시되지 않음

ACSD-63299 패치는 특별 가격 속성이 구성 가능한 제품의 특별 가격 표시에 더 이상 영향을 주지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63299입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Adobe Commerce]에서 특별 가격 특성에 대한 *제품 목록에 사용됨* 값을 변경해도 구성 가능한 제품에 대한 특별 가격이 표시되는 방식에는 더 이상 영향을 주지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**(으)로 이동합니다.
1. ***[!UICONTROL special_price]*** 특성을 찾아 **[!UICONTROL Storefront Properties]**(으)로 이동합니다.
1. ***[!UICONTROL Used in Product Listing]***&#x200B;을(를) ***[!UICONTROL No]***(으)로 변경합니다.
1. 하나의 하위 항목으로 구성 가능한 제품 만들기:
   * 이름 및 SKU: 테스트
   * 가격: $159.00
   * 색상을 기준으로 옵션을 생성합니다. 새 색상 추가: 파랑
   * 저장
1. 하위 제품을 열고 다음 단계를 수행합니다.
   * **[!UICONTROL Advanced Pricing]**&#x200B;의 특별 가격을 99.90달러로 설정
   * [!UICONTROL Visibility]을(를) **[!UICONTROL Catalog, Search]**(으)로 변경합니다.
1. 간단한 제품 페이지를 열고 특별 가격이 표시되는지 확인합니다.
1. 구성 가능한 제품 페이지를 엽니다.
1. 파란색 제품을 선택합니다.

<u>예상 결과</u>:

간편 제품에 대해서도 특가가 있는 것과 같은 방식으로 보인다.

<u>실제 결과</u>:

1. 구성 가능한 제품을 선택하면 전체 가격이 표시됩니다.
1. 섹션 *최저가...*($99.90)와 실제 가격($99.90 + $59.10 = $159.00) 간에 불일치가 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
