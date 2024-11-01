---
title: 'ACSD-60234: [!DNL PayPal] 할인 적용 시 잘못된 금액이 표시됨'
description: ACSD-60234 패치를 적용하여 결제 방법을 통해 할인을 적용할 때  [!DNL PayPal] 잘못된 금액이 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Products, Configuration
role: Admin, Developer
source-git-commit: 334e9f740b49d87fc20ee8950d85adb9612c00b7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234: 할인 적용 시 [!DNL PayPal]에 잘못된 금액이 표시됩니다.

ACSD-60234 패치는 결제 방법을 통해 할인을 적용할 때 [!DNL PayPal]에 잘못된 금액이 표시되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.51이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60234입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

결제 방법을 통해 할인이 적용되면 [!DNL PayPal]에 잘못된 금액이 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**&#x200B;에서 *[!DNL PayPal Express]*&#x200B;을(를) 구성합니다.
   * [!UICONTROL Enable In-Context Checkout]은(는) [!UICONTROL Yes] 또는 [!UICONTROL NO]일 수 있습니다. 두 시나리오에서 문제가 재현됩니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**&#x200B;에서 *[!UICONTROL Cart Rule]*&#x200B;을(를) 만듭니다.
   * 조건: 다음 조건이 모두 true인 경우: *[!UICONTROL Payment Method]*&#x200B;은(는) *[!DNL PayPal Express Checkout]*&#x200B;입니다.
   * 작업: 모든 작업
1. 제품을 만듭니다.
1. 상점으로 이동하여 장바구니에 제품을 추가한 다음 체크아웃의 **[!UICONTROL Payment Method]** 단계로 이동합니다.
1. *[!DNL PayPal Express]*&#x200B;을(를) 선택하고 할인이 올바르게 적용되었는지 확인하십시오.
1. **[!DNL PayPal]** 단추를 클릭합니다.
1. 로그인하고 팝업의 콘텐츠를 확인합니다.

<u>예상 결과</u>:

[!DNL PayPal]에 전달된 결제 금액에는 장바구니에 있는 할인 금액이 포함되어 있습니다.

<u>실제 결과</u>:

총 결제금액에는 할인이 포함되어 있지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
