---
title: 'ACP2E-4050: [!UICONTROL Free Shipping]이(가) 다중 배송 체크아웃과 함께 적용되지 않음'
description: ACP2E-4050 패치를 적용하여 [!UICONTROL Free Shipping]에 하위 선택 조건 및 특정 가격의 제품이 포함된 경우 다중 주소 체크아웃 동안 [!UICONTROL Cart Price Rules]이(가) 적용되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]**&#x200B;이(가) 다중 배송 체크아웃과 함께 적용되지 않음

ACP2E-4050 패치는 **[!UICONTROL Free Shipping]**&#x200B;에 하위 선택 조건 및 특정 가격의 제품이 포함된 경우 다중 배송 체크아웃 중에 **[!UICONTROL Cart Price Rules]**&#x200B;이(가) 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-4050입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p10

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Free Shipping]**&#x200B;에 하위 선택 조건 및 특정 가격의 제품이 포함된 경우 **[!UICONTROL Cart Price Rules]**&#x200B;은(는) 다중 배달 체크아웃 중에 적용되지 않습니다.

<u>재현 단계</u>:

1. 두 개의 주소로 고객 계정을 만듭니다.
1. **[!UICONTROL Free Shipping]**&#x200B;을(를) 사용하도록 설정하고 **[!UICONTROL Minimum Order Amount]**&#x200B;을(를) *999999*(으)로 설정합니다.
1. [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules]&#x200B;(으)로 이동하고 다음 조건을 사용하여 장바구니 가격 규칙을 만듭니다.

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. 샘플 데이터를 설치합니다.
1. 다음 제품을 지정된 순서로 장바구니에 추가합니다.
   * Wayfarer 메신저 백
   * Olivia 1/4 Zip Light 재킷
   * 스프라이트 요가 컴패니언 키트.
1. 장바구니를 열고 **[!UICONTROL Free Shipping]** 옵션을 사용할 수 있는지 확인하십시오.
1. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;을(를) 클릭합니다.
1. 단순 제품에 대해 다른 배송 주소를 선택하십시오.
1. **[!UICONTROL Go to Shipping Information]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

**[!UICONTROL Free Shipping]**&#x200B;은(는) 구성 및 번들 제품 배송에 적용됩니다.

<u>실제 결과</u>:

**[!UICONTROL Free Shipping]**&#x200B;을(를) 사용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
