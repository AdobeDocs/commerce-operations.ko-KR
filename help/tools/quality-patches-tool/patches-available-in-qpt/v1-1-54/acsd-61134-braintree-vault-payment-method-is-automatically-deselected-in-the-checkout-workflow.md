---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] 결제 방법이 체크아웃 워크플로우에서 자동으로 선택 해제되었습니다.'
description: ACSD-61134 패치를 적용하여 구매자가 *[!UICONTROL My billing and shipping address are the same]* 확인란을 선택 취소하여 청구 주소를 업데이트할 때 체크아웃 워크플로에서 *[!UICONTROL Braintree Vault]* 결제 방법이 자동으로 선택 취소되는 Adobe Commerce 문제를 해결하십시오.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* 결제 방법이 체크아웃 워크플로우에서 자동으로 선택 해제되었습니다.

ACSD-61134 패치는 쇼핑객이 *[!UICONTROL My billing and shipping address are the same]* 확인란을 선택 취소하여 청구 주소를 업데이트할 때 체크아웃 워크플로에서 *[!UICONTROL Braintree Vault]* 결제 방법이 자동으로 선택 취소되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61134입니다. 이 문제는 Adobe Commerce 2.4.7-Beta1에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Braintree Vault]* 결제 방법이 체크아웃 워크플로우에서 자동으로 선택 해제됩니다.

<u>재현 단계</u>:

1. *[!UICONTROL Vault]*&#x200B;을(를) 사용하도록 설정하여 *[!DNL Braintree]* 결제 방법을 구성하십시오.
1. *[!UICONTROL Vault]*&#x200B;에서 카드를 체크아웃하고 저장합니다.
1. 다른 제품을 체크아웃합니다.
1. *[!UICONTROL Shipping]* 페이지에서 새 배송 주소를 추가하여 두 개의 주소를 선택할 수 있도록 합니다.
1. *[!UICONTROL Payment]* 페이지에서 결제 방법을 선택하고 **[!UICONTROL My billing and shipping addresses are the same]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

선택한 결제 방법은 선택된 상태로 유지됩니다.

<u>실제 결과</u>:

선택한 결제 방법이 선택 취소되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
