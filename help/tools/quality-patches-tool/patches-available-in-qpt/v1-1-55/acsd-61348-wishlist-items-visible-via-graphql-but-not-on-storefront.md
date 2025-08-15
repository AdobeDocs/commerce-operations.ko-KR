---
title: 'ACSD-61348: 위시리스트 항목이 GraphQL을 통해 표시되지만 상점 앞에는 표시되지 않음'
description: ACSD-61348 패치를 적용하여 위시리스트 항목이 GraphQL을 통해 표시되지만 다중 웹 사이트 환경의 상점 앞에는 표시되지 않는 Adobe Commerce 문제를 수정합니다.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: 위시리스트 항목이 GraphQL을 통해 표시되지만 상점 앞에는 표시되지 않음

ACSD-61348 패치를 사용하면 위시리스트 항목이 GraphQL을 통해 표시되지만 다중 웹 사이트 환경의 상점 앞에는 표시되지 않는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61348입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p5

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

위시리스트 항목은 GraphQL을 통해 볼 수 있지만, 다중 웹 사이트 환경의 상점 앞에는 볼 수 없습니다.

<u>재현 단계</u>:

1. 두 개의 웹 사이트를 구성합니다.
1. **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**(으)로 이동한 다음 **[!UICONTROL Share Customer Accounts]**&#x200B;을(를) *[!UICONTROL Global]*(으)로 설정합니다.
1. **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]**(으)로 이동한 다음 **[!UICONTROL Enable Multiple Wish Lists]**&#x200B;을(를) *예*(으)로 설정합니다.
1. **[!UICONTROL Config General]** > **[!UICONTROL Web]**(으)로 이동한 다음 **[!UICONTROL Add Store Code to URLs]**&#x200B;을(를) *예*(으)로 설정합니다.
1. 간단한 제품을 만들어 두 번째 웹 사이트에 할당합니다.
1. 고객을 만들고 로그인합니다.
1. 위시리스트에 제품을 추가합니다.
1. 제품을 기본 웹 사이트에 할당합니다.
1. 기본 웹 사이트의 *[!UICONTROL Wishlist]* 페이지로 이동합니다.

<u>예상 결과</u>:

제품이 위시리스트에 있습니다.

<u>실제 결과</u>:

위시리스트에 제품이 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
