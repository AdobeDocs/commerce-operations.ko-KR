---
title: 'ACSD-56886: 하위 제품이 비활성화되면 구성 가능한 제품이 품절 상태가 됩니다.'
description: ACSD-56886 패치를 적용하여 제품이 비활성화될 때 구성 가능한 제품의 재고가 부족해지는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886: 하위 제품이 비활성화되면 구성 가능한 제품이 품절 상태가 됩니다.

ACSD-56886 패치는 하위 제품이 비활성화될 때 구성 가능한 제품이 품절되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56886입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 제품이 비활성화되면 구성 가능한 제품이 품절 상태가 됩니다.

<u>재현 단계</u>:

1. 관리자로 로그인합니다.
1. **[!UICONTROL Update By Schedule]** 모드에서 모든 인덱서를 설정하십시오.
1. 다음과 같이 구성 가능한 제품을 만듭니다.

   * 이름 = *테스트 구성 가능 1*
   * 특성 = *color*
   * 값 = *빨강* 및 *검정*
   * **빨강** 하위 제품 가격 = *$100*;
   * &quot;검정색&quot; 자식 제품의 가격 = *$200*.

1. 구성 가능한 제품에 대해 다음과 같은 예정된 업데이트를 만듭니다.

   * 지금부터 시작 날짜 = *3*&#x200B;분.
   * 종료 날짜 = 시작 날짜로부터 *5*&#x200B;분 후.
   * 제품 이름 = *테스트 구성 가능 1 편집됨*.
   * **구성 가능** 섹션에서 **빨강** 하위 제품을 사용하지 않도록 설정하십시오.

1. 시작 날짜를 기다립니다.
1. Storefront에서 구성 가능한 제품 세부 사항을 엽니다.

<u>예상 결과</u>:

구성 가능한 제품은 **최저** 레이블과 함께 **재고 중**(으)로 표시됩니다.

<u>실제 결과</u>:

구성 가능한 제품이 **품절**(으)로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
