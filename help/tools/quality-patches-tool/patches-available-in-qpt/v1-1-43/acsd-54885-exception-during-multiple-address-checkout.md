---
title: 'ACSD-54885: 관리자가 고객으로 로그인할 때 여러 주소를 체크 아웃하는 동안 예외 발생'
description: ACSD-54885 패치를 적용하여 관리자가 *[!UICONTROL Login as Customer]* 기능을 사용할 때 여러 주소를 체크아웃하는 동안 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885: 관리자가 고객으로 로그인할 때 여러 주소를 체크 아웃하는 동안 예외 발생

ACSD-54885 패치는 관리자가 *[!UICONTROL Login as Customer]* 기능을 사용할 때 여러 주소를 체크 아웃하는 동안 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54885입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 *[!UICONTROL Login as Customer]* 기능을 사용하는 경우 여러 주소를 체크 아웃하는 동안 오류가 발생합니다.

<u>재현 단계</u>:

1. *[!UICONTROL Login as Customer]*&#x200B;이(가) 활성화되어 있는지 확인하십시오. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**(으)로 이동합니다.
1. 간단한 제품을 만듭니다.
1. 주소가 있는 새 고객 계정을 만듭니다.
1. 백엔드의 고객 계정으로 이동합니다.

   * **[!UICONTROL Account Information]** 탭으로 이동하여 *[!UICONTROL Allow remote shopping assistance]* = *예*&#x200B;를 설정합니다.
   * **[!UICONTROL Login as Customer]**&#x200B;을(를) 클릭합니다.

1. 제품을 장바구니에 추가하고 *[!UICONTROL Checkout with multiple addresses]*(으)로 진행합니다.
1. 제품 수량을 업데이트합니다.
1. 장바구니로 돌아가십시오.

<u>예상 결과</u>:

장바구니를 업데이트하고 여러 주소 체크아웃을 사용할 수 있습니다.

<u>실제 결과</u>:

장바구니로 돌아가면 다음 오류가 발생합니다.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
