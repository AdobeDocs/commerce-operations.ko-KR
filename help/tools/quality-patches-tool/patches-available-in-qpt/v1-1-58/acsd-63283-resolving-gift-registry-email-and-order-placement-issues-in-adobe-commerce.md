---
title: 'ACSD-63283: Adobe Commerce에서 [!UICONTROL Gift Registry] 전자 메일 및 주문 배치 문제를 해결하고 있습니다.'
description: ACSD-63283 패치를 적용하여 [!UICONTROL Gift Registry]에서 항목을 정렬하면 예외가 발생하고 [!UICONTROL Gift Registry Updates]에 올바른 항목만 포함되는 Adobe Commerce 문제를 해결합니다.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: Adobe Commerce에서 [!UICONTROL Gift Registry] 전자 메일 및 주문 배치 문제를 해결하고 있습니다.

ACSD-63283 패치는 [!UICONTROL Gift Registry]에서 항목을 정렬하면 예외가 발생하고 [!UICONTROL Gift Registry Updates]에 올바른 항목만 포함되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63283입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

>[!NOTE]
>이 패치는 [ACSD-56280](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT 패치를 대체하고 확장합니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Adobe Commerce의 [!UICONTROL Gift Registry] 기능은 두 가지 중요한 문제의 영향을 받습니다.

* 고객이 [!UICONTROL Gift Registry]에서 항목을 주문하면 예외가 트리거되어 프로세스가 실패합니다.
* 또한 레지스트리 소유자에게 보내는 [!UICONTROL Gift Registry Updates] 전자 메일에 업데이트 중인 특정 레지스트리의 항목에 대한 업데이트를 제한하지 않고 모든 선물 레지스트리의 항목이 잘못 포함되어 있습니다.

<u>재현 단계</u>:

1. 제품 A와 제품 B, 이렇게 두 개의 제품을 만듭니다.
1. 고객 A와 고객 B, 이렇게 두 개의 고객을 만듭니다.
1. 고객 A로 로그인하고 새 [!UICONTROL Gift Registry]을(를) 만듭니다.
1. 제품 A의 제품 페이지로 이동하여 [!UICONTROL Wishlist]에 추가합니다. [!UICONTROL Wishlist Page]을(를) 열고 [!UICONTROL Gift Registry]을(를) 사용하여 제품 A를 [!UICONTROL Add to Gift Registry]&#x200B;(으)로 이동합니다.
1. 고객 B로 로그인하고 새 [!UICONTROL Gift Registry]을(를) 만든 다음 제품 B를 추가합니다.
1. 고객 B로서 [!UICONTROL Gift Registry] > **[!UICONTROL My Account]> [!UICONTROL Gift Registry] 전자 메일을 통해[!UICONTROL Share]**&#x200B;을(를) 공유하세요.
1. 고객 B로 로그아웃합니다.
1. 이메일에 받은 링크를 클릭합니다. 제품 B를 [!UICONTROL Cart]에 추가하고 주문합니다.

<u>예상 결과</u>:

고객 B는 기프트 레지스트리에서만 업데이트된 항목이 포함된 이메일을 수신합니다.

<u>실제 결과</u>:

고객 B는 모든 기프트 등록의 항목이 포함된 이메일을 받습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
