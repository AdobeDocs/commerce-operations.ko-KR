---
title: 'ACSD-61799: 여러 고정 할인 카트 규칙이 견적에 적용된 잘못된 총 할인 계산'
description: ACSD-61799 패치를 적용하여 고정 할인이 적용된 여러 장바구니 규칙이 견적에 적용될 때 총 할인이 잘못 계산되는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
source-git-commit: 737204ae7418f49fdebfffbf351304796e9f5eb0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: 여러 고정 할인 카트 규칙이 견적에 적용된 잘못된 총 할인 계산

ACSD-61799 패치는 고정 할인이 적용된 여러 장바구니 규칙이 견적에 적용될 때 총 할인이 잘못 계산되는 문제를 해결/수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61799입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Fixed amount discount for the whole cart]*&#x200B;이(가) 있는 여러 장바구니 규칙이 장바구니에 적용되는 경우 총 할인이 잘못 계산됩니다.

<u>재현 단계</u>:

1. 가격이 $1000인 제품 4개를 만듭니다.
1. 전체 장바구니에 대해 $100 할인을 제공하는 조건 없이 장바구니 가격 규칙 3개를 만듭니다.
1. 규칙이 적용되지 않도록 하는 조건으로 전체 장바구니에 대해 $100 할인을 제공하는 다른 장바구니 가격 규칙을 만듭니다.
1. 규칙을 비활성화합니다.
1. 장바구니에 3개의 제품을 추가하고 장바구니에서 할인을 확인합니다.
1. 장바구니에 추가 제품을 추가하고 장바구니에서 할인을 확인합니다.
1. 비활성화된 장바구니 가격 규칙을 활성화합니다.
1. 장바구니 페이지를 업데이트하고 장바구니에서 할인을 확인합니다.

<u>예상 결과</u>:

1. 장바구니에 추가 제품을 추가해도 할인 금액이 변경되지 않습니다.
1. 적용되지 않는 조건이 있는 장바구니 가격 규칙을 활성화해도 할인 금액이 변경되지 않습니다.

<u>실제 결과</u>:

1. 장바구니에 추가 제품을 추가하면 할인 금액이 변경됩니다.
1. 적용되지 않는 조건이 있는 장바구니 가격 규칙을 활성화하면 할인 금액이 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
