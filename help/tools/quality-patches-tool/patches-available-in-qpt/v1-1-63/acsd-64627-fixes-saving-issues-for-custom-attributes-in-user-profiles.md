---
title: 'ACSD-64627: [!UICONTROL Company Structure]에 사용자 지정 고객 특성을 저장할 수 없습니다.'
description: '[!UICONTROL Company Structure] 내에서 사용자를 추가하거나 편집할 때 사용자 지정 고객 특성을 저장할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-64627 패치를 적용하십시오.'
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627: [!UICONTROL Company Structure]에 사용자 지정 고객 특성을 저장할 수 없습니다.

ACSD-64627 패치를 사용하면 **[!UICONTROL Company Structure]** 페이지에서 사용자를 추가하거나 편집할 때 사용자 지정 고객 특성을 저장할 수 없는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64627입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Company Structure]** 페이지에서 사용자를 추가하거나 편집할 때 사용자 지정 고객 특성이 저장되지 않습니다.

<u>재현 단계</u>:

1. B2B 기능이 활성화된 Adobe Commerce 인스턴스를 설치합니다.
1. *이(가)*(으)로 설정된 **[!UICONTROL Input Type]** custom_upload *[!UICONTROL File (attachment)]*(이)라는 새 고객 특성을 만듭니다.
1. *이(가)*(으)로 설정된 **[!UICONTROL Input Type]** image_attachment *[!UICONTROL Image File]*(이)라는 다른 고객 특성을 만듭니다.
1. **[!UICONTROL Show on Storefront]**&#x200B;을(를) *예*(으)로 설정하여 두 특성이 모두 상점 앞에 표시되도록 합니다. 모든 양식 선택:
   * 고객 등록
   * 고객 계정 편집
   * 관리자 체크아웃
1. 새 회사를 만들고 활성화합니다.
1. 회사 관리자로 상점 첫 화면에 로그인합니다.
1. **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** 또는 **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**(으)로 이동합니다.
1. **[!UICONTROL Add New User]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Upload]** custom_upload *특성에 대해*&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Select file]** image_attachment *특성에 대해*&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

두 속성에 대해 파일 탐색기가 열립니다. 저장 시 값이 저장되고 파일이 성공적으로 업로드됩니다.

<u>실제 결과</u>:

버튼이 응답하지 않습니다. 파일 탐색기가 열리지 않거나 데이터가 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
