---
title: 'ACSD-55628: 회사 등록 양식에 파일 업로드 중, 상점 첫 화면에서 고객 특성에 대한 파일 대체'
description: ACSD-55628 패치를 적용하여 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 대체할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: a008a205-ec1d-4a1d-9cd2-75f10a937057
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '415'
ht-degree: 1%
---
# ACSD-55628: 회사 등록 양식에 파일 업로드 중, 상점 첫 화면에서 고객 특성에 대한 파일 대체

>[!NOTE]
>
>이 패치는 [ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md)을(를) 대체합니다.

ACSD-55628 패치는 회사 등록 양식에 파일을 업로드하고 상점 첫 화면에서 고객 속성에 대한 파일을 바꾸는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55628입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2 &lt; 2.4.5 및 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

상점 첫 화면의 고객 특성에 대한 파일을 바꿀 수 없습니다.

<u>재현 단계</u>:

1. 다음 값으로 새 고객 속성을 만듭니다.

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *예*
   * *[!UICONTROL Forms to Use In]*: *사용 가능한 모든 옵션*

1. 상점 첫 화면에서 고객으로 로그인한 다음 **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**&#x200B;을(를) 엽니다.
1. 새 이미지를 업로드하고 저장합니다.
1. 페이지를 새로 고칩니다. 이전 이미지를 삭제하고 새 이미지를 업로드합니다. 변경 사항을 저장합니다.

<u>예상 결과</u>:

새 이미지가 저장됩니다.

<u>실제 결과</u>:

이전 이미지가 여전히 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]&#x200B;[&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
