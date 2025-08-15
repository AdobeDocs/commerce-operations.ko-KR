---
title: 'ACSD-52399: 판매 가능한 수량 0이 있는 제품이 재고로 표시됨'
description: ACSD-52399 패치를 적용하여 Adobe Commerce 문제를 해결합니다. 구성 가능한 제품 옵션이 판매 가능한 수량이 0인 경우 제품 페이지에서 *재고 있음*이 표시됩니다.
feature: Products, Configuration
role: Admin, Developer
exl-id: 7b7332bb-15ae-44b6-a347-38ac7c9001db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52399: 판매 가능한 수량 0이 있는 제품이 재고로 표시됨

ACSD-52399 패치는 판매 가능 수량이 영(0)인 구성 가능한 제품 옵션이 제품 페이지에서 *재고 있음*&#x200B;을 표시하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52399입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

판매 가능 수량이 영(0)인 구성 가능한 제품 옵션은 제품 페이지에 *재고 있음*&#x200B;이 표시됩니다.

<u>재현 단계</u>:

1. 0(판매 가능 수량) 제품 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 상점 첫 화면의 제품 페이지로 이동하여 구성 가능한 제품을 선택하고 변형/구성을 확인합니다.
1. **[!UICONTROL Add to Cart]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

*[!UICONTROL Add to Cart]*&#x200B;재고 부족&#x200B;*제품 구성을 선택할 때는* 단추를 사용할 수 없습니다.

<u>실제 결과</u>:

구성 가능한 변형은 상점 첫 화면에서 사용할 수 있으며 선택한 후 장바구니에 추가할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
