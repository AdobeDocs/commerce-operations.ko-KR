---
title: 'ACSD-58735: 제한된 관리자는 연결된 웹 사이트의 고객 계정에서 구매하지 않은 장바구니를 볼 수 없습니다'
description: ACSD-58735 패치를 적용하여 제한된 관리자가 연결된 웹 사이트에 대한 Commerce 관리자의 고객 계정 페이지에서 포기한 장바구니를 볼 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735: 제한된 관리자는 연결된 웹 사이트의 고객 계정에서 구매하지 않은 장바구니를 볼 수 없습니다

ACSD-58735 패치는 제한된 역할을 가진 관리자가 Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** 탭에서 포기한 고객의 장바구니를 볼 수 없는 문제를 해결합니다.

여러 웹 사이트에 대한 그리드 보기를 표시할 때 포기한 장바구니가 기본적으로 관리 패널에 로드되어 있는 경우, 관련 스토어 ID를 표시할 수 없기 때문에 이 문제가 발생합니다.

이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-58735입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제한된 관리자는 관리 패널의 고객 계정 페이지에서 구매하지 않은 장바구니를 볼 수 없습니다.

<u>재현 단계</u>:

1. 한 웹 사이트에만 액세스할 수 있는 관리자 역할을 만듭니다.
1. 포기한 장바구니를 만듭니다.
1. 전체 권한을 가진 관리자로 로그인합니다. **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;을(를) 확인하고 장바구니가 표시되는지 확인하십시오.
1. 제한된 관리자로 **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]**&#x200B;을(를) 선택합니다.

<u>예상 결과</u>:

제한된 관리자는 연결된 웹 사이트에 대해 포기한 장바구니를 볼 수 있습니다.

<u>실제 결과</u>:

제한된 관리자는 연결된 웹 사이트에 대해 구매하지 않은 장바구니를 볼 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
