---
title: 'ACSD-63469: 고정 금액 장바구니 할인이 여러 규칙과 함께 올바르게 적용되지 않음'
description: 두 개 이상의 규칙이 적용될 때 전체 장바구니에 대한 고정 금액 할인이 제대로 적용되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-63469 패치를 적용합니다.
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-63469: 고정 금액 장바구니 할인이 여러 규칙과 함께 올바르게 적용되지 않음

ACSD-63469 패치는 두 개 이상의 규칙이 적용될 때 전체 장바구니에 대한 고정 금액 할인이 제대로 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63469입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 **[!UICONTROL Fixed amount discount for whole cart]** 규칙이 동시에 적용되고 제품에 할인 또는 특별 가격이 있는 경우 할인 값이 잘못 계산됩니다.

<u>재현 단계</u>:

1. 850달러와 85달러 두 가지 상품을 만들고 각각 765달러와 68달러로 특가를 설정한다.
1. 다음과 같이 두 개의 **[!UICONTROL Cart Price Rules]**&#x200B;을(를) 만듭니다.
   * 규칙 1
      * **[!UICONTROL Conditions]**: $850 제품의 경우 *수량*&#x200B;을(를) *같음 또는 2* 이상으로 설정하십시오.
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**/*$153* 적용
   * 규칙 2
      * **[!UICONTROL Conditions]**: $85 제품의 경우 *수량*&#x200B;을(를) *2*&#x200B;보다 크거나 같게 설정합니다.
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**/*$14* 적용
1. 각각 수량이 2인 두 제품을 장바구니에 추가합니다.

<u>예상 결과</u>:

장바구니에 적용되는 할인은 $167입니다.

<u>실제 결과</u>:

장바구니에 적용되는 할인은 $41입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
