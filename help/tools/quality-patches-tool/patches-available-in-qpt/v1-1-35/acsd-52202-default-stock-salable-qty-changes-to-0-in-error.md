---
title: 'ACSD-52202: 비기본 재고가 순번 0으로 설정된 경우 기본 재고 판매 가능 수량이 오류로 0으로 변경됩니다.'
description: ACSD-52202 패치를 적용하여 주문에서 기본값이 아닌 재고가 0으로 설정될 때 기본 재고 판매 수량이 오류로 인해 0으로 변경되는 Adobe Commerce 문제를 수정합니다.
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202: 주문에서 비기본 재고가 0 수량으로 설정된 경우 기본 재고 판매 수량이 0으로 잘못 변경됩니다.

ACSD-52202 패치는 주문에서 기본값이 아닌 재고가 0으로 설정될 때 기본 재고 판매 가능 수량(수량)이 오류로 인해 0으로 변경되는 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52202입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문에서 기본 재고가 아닌 재고가 0 수량으로 설정된 경우 기본 재고 판매 수량이 0으로 잘못 변경됩니다.

<u>재현 단계</u>:

1. [!DNL Admin]에 로그인합니다.
1. **웹 사이트2**&#x200B;을(를) 만듭니다.
1. 사용자 지정 **source2**&#x200B;을(를) 만듭니다.
1. 사용자 지정 **stock2**&#x200B;을(를) 만듭니다.
1. **website1**&#x200B;에 **source2** 및 **stock2**&#x200B;을(를) 할당하고 기본 웹 사이트에 기본 소스 및 스톡을 할당하십시오.
1. 간단한 제품을 만들고 기본 원본의 경우 **qty** = *10*, **source2** 원본의 경우 *qty* = **1**&#x200B;을(를) 할당하십시오.
1. **website2**&#x200B;에 대해 *qty* = **1**&#x200B;을(를) 주문합니다.
1. 송장 및 선적을 생성합니다.
1. 간단한 제품 **판매 가능한 수량**&#x200B;을(를) 확인하십시오.

<u>예상 결과</u>:

**source2**&#x200B;에 대한 *판매 가능 수량* = **10**.

<u>실제 결과</u>:

두 소스의 **판매 가능 수량** = *0*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
