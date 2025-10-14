---
title: 'ACSD-56621: 회사 관리자의 인사말 헤더에 업데이트된 이름이 표시되지 않음'
description: ACSD-56621 패치를 적용하여 회사 관리자 사용자의 업데이트된 이름과 성이 인사말 헤더 섹션에 반영되지 않은 Adobe Commerce 문제를 수정합니다.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621: 회사 관리자의 인사말 헤더에 업데이트된 이름이 표시되지 않음

ACSD-56621 패치는 회사 관리자 사용자의 업데이트된 이름과 성이 인사말 헤더 섹션에 반영되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-56621입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

업데이트된 이름은 회사 관리자의 인사말 헤더에 표시되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** 패널로 이동합니다.
1. **[!UICONTROL Stores]**(으)로 이동하여 **[!UICONTROL Configuration]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL General]** 섹션에서 **[!UICONTROL B2B]**&#x200B;을(를) 선택하여 B2B 회사 기능을 사용하도록 설정합니다.
1. **[!UICONTROL Storefront]**(으)로 이동하여 새 회사를 등록하십시오.
1. 회사 관리자로 로그인합니다.
1. **[!UICONTROL My Account]** > **[!UICONTROL Company Users]**(으)로 이동하여 필요에 따라 이름 및 성 필드를 수정합니다.

<u>예상 결과</u>:

인사말 헤더 섹션의 사용자 이름과 성이 즉시 변경됩니다.

<u>실제 결과</u>:

사용자의 이름과 성은 사용자가 로그아웃했다가 다시 로그인할 때만 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
