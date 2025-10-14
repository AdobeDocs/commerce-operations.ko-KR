---
title: 'ACSD-60673: 체크아웃 시 여러 결제 방법에 대해 [!UICONTROL Cart Price Rule] 문제가 해결되었습니다.'
description: ACSD-60673 패치를 적용하여 결제 방법 조건을 사용하는 [!UICONTROL Cart Price Rule]의 할인이 항상 합계에 나열되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: 체크아웃 시 여러 결제 방법에 대해 [!UICONTROL Cart Price Rule] 문제가 해결되었습니다.

ACSD-60673 패치는 결제 방법 조건을 사용하는 [!UICONTROL Cart Price Rule]의 할인이 항상 합계에 나열되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60673입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크아웃 시 여러 결제 방법에 대한 [!UICONTROL Cart Price Rule]이(가) 특정 결제 방법에 올바르게 적용되지 않습니다.

<u>필수 구성 요소</u>

**[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** 및 **[!UICONTROL Bank Transfer]**&#x200B;이(가) 활성화되어 있는지 확인하십시오.

<u>재현 단계</u>:

1. **[!UICONTROL Multiple Payment Methods]** 사용
1. *[!UICONTROL Cart Price Rule]* 만들기
   * **[!UICONTROL Conditions]** 설정: 결제 방법을 **[!UICONTROL Money Order]**(또는 계좌 이체)로
   * 모든 제품에 대해 **[!UICONTROL Actions]** = *25%* 할인 선택
1. 가상 제품을 만듭니다.
1. 새 견적 및 게스트 고객 *[!UICONTROL Status]*&#x200B;을(를) 복사하려면 상점으로 이동하여 쿠키를 지우십시오.
1. 가상 제품을 장바구니에 추가합니다.
1. *체크아웃*&#x200B;을 진행합니다.
1. *[!UICONTROL Cart Price Rule]*&#x200B;에 정의된 결제 방법을 클릭합니다.
1. *[!UICONTROL Billing Address]*&#x200B;을(를) 업데이트합니다.
1. 할인이 총 금액에 표시되는지 확인합니다.
1. 결제 방법을 변경하려면 확인란을 클릭하십시오.
1. 할인이 표시되는지 확인합니다.

<u>예상 결과</u>:

해당 결제 방법으로 전환하기 위한 확인란을 클릭하면 *총계*&#x200B;에 할인이 표시됩니다.

<u>실제 결과</u>:

할인은 *합계*&#x200B;에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
