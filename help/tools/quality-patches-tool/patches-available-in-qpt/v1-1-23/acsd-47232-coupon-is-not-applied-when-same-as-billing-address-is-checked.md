---
title: 'ACSD-47232: [!UICONTROL Same as Billing Address]을(를) 선택하면 쿠폰이 적용되지 않습니다.'
description: '[!UICONTROL Same as Billing Address]이(가) 확인 상태일 때 쿠폰이 적용되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-47232 패치를 적용하세요.'
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232: [!UICONTROL Same as Billing Address]을(를) 선택하면 쿠폰이 적용되지 않습니다.

ACSD-47232 패치는 **[!UICONTROL Same as Billing Address]**&#x200B;을(를) 확인했을 때 쿠폰이 적용되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47232입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Same as Billing Address]**&#x200B;을(를) 선택하면 쿠폰이 적용되지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. 가중치 = *8*&#x200B;인 간단한 제품을 만듭니다.
1. 기본 청구 및 배송 주소로 새 고객을 만듭니다.
1. 쿠폰으로 장바구니 가격 규칙을 만듭니다.
   * **[!UICONTROL Conditions]** 섹션에서 *총 무게가 5*&#x200B;보다 크거나 같은 항목 추가
1. [!UICONTROL Commerce] 관리자에서 새 주문을 만들어 보세요.
   * 방금 만든 고객 사용
   * 제품 추가
   * 쿠폰을 적용해 보세요

<u>예상 결과</u>:

쿠폰이 적용됩니다.

<u>실제 결과</u>:

다음과 유사한 오류가 발생했습니다. *123 쿠폰 코드가 유효하지 않습니다. 코드를 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
