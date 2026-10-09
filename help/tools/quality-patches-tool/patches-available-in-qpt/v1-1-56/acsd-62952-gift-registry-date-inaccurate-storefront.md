---
title: 'ACSD-62952: 상점 첫 화면에 잘못 표시된 선물 등록 날짜'
description: ACSD-62952 패치를 적용하여 선물 등록 날짜가 상점 첫 화면에 잘못 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-62952: 상점 첫 화면에 잘못 표시된 선물 등록 날짜

ACSD-62952 패치를 사용하면 Gift Registry 날짜가 상점 앞에 잘못 표시되는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62952입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

공유 선물 레지스트리의 상점 앞에 표시되는 이벤트 날짜가 실제 날짜보다 하루 빠르게 잘못 표시됩니다.

<u>재현 단계</u>:

1. 프론트엔드에 고객으로 로그인합니다.
1. [!UICONTROL My Account] 대시보드에서 **[!UICONTROL Gift Registry]**&#x200B;을(를) 클릭합니다.
1. 기존 레지스트리가 없는 경우 레지스트리를 만들고 날짜를 지정합니다.
1. 장바구니에 품목을 추가합니다.
1. 장바구니 페이지에서 **[!UICONTROL Add all items to Gift Registry]**&#x200B;을(를) 클릭합니다.
1. 선물 레지스트리를 공유합니다.

<u>예상 결과</u>:

선물 레지스트리에 올바른 이벤트 날짜가 표시됩니다.

<u>실제 결과</u>:

초대 이메일에서 열린 선물 등록에는 이벤트 날짜가 하루 전으로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
