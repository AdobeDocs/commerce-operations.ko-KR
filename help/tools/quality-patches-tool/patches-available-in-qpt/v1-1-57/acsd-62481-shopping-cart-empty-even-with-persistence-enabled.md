---
title: 'ACSD-62481: [!UICONTROL Persistence]이(가) 활성화된 경우에도 장바구니가 비어 있음'
description: ACSD-62481 패치를 적용하여 체크아웃 중에 로그인 팝업을 사용할 때 장바구니 기능이 지속되는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Checkout
role: Admin, Developer
source-git-commit: 27a98c42f2c514b3dd1a2f59c140b60b7ac26592
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-62481: *[!UICONTROL Persistence]*&#x200B;이(가) 활성화된 경우에도 장바구니가 비어 있음

ACSD-62481 패치는 체크아웃 중에 로그인 팝업을 사용할 때 장바구니 기능 *[!UICONTROL Remember Me]* 확인란이 부족하여 로그아웃 후 제품이 장바구니에서 사라지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62481입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크아웃 중에 로그인 팝업을 사용할 때 장바구니 기능 *[!UICONTROL Remember Me]* 확인란이 없기 때문에 장바구니 기능이 실패합니다. 이렇게 하면 로그아웃한 후 제품이 장바구니에서 사라집니다.

<u>재현 단계</u>:

1. 관리자에서 다음과 같이 게스트 계정 및 영구 장바구니 설정을 구성합니다.

   * **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**(으)로 이동하고 *[!UICONTROL Allow Guest Checkout]*&#x200B;을(를) *아니요*(으)로 설정합니다.

      * **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.

   * **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]**(으)로 이동하고 *[!UICONTROL Enable Persistence]*&#x200B;을(를) *예*(으)로 설정합니다.
   * 다른 모든 설정은 기본값으로 두고 *[!UICONTROL Clear Persistence on Sign Out]*&#x200B;을(를) *아니요*(으)로 변경합니다.

      * **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.

1. 카탈로그에 간단한 제품을 추가하려면 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]**(으)로 이동하십시오.

   * 필요한 최소 세부 정보를 입력하고 재고가 있는지 확인합니다.

1. 프런트 엔드에서 기본 양식 `(../customer/account/create/)`을(를) 사용하여 고객 계정을 만들고 로그아웃합니다.
1. 제품을 장바구니에 게스트로 추가합니다.
1. 오른쪽 상단에 있는 아이콘을 사용하여 미니 장바구니를 연 다음 **[!UICONTROL View and Edit Cart]**&#x200B;을(를) 클릭합니다.
1. 체크아웃을 진행합니다.
1. 표시되는 팝업 대화 상자를 통해 새 고객 계정에 로그인하고 로그아웃합니다.

<u>예상 결과</u>:

장바구니는 이전에 로그인한 사용자의 제품을 유지합니다.

<u>실제 결과</u>:

* 장바구니가 비어 있습니다.
* 팝업 로그인 대화 상자에 *[!UICONTROL Remember Me]* 옵션이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
