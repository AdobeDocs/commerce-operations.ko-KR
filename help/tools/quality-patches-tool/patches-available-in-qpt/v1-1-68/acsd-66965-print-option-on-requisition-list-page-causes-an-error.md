---
title: 'ACSD-66965: [!UICONTROL Print] 페이지의 [!UICONTROL Requisition List] 옵션에서 오류가 발생했습니다.'
description: ACSD-66965 패치를 적용하여 Adobe Commerce에서 [!UICONTROL Print] 페이지의 [!UICONTROL Requisition List] 옵션으로 인해 오류가 발생하는 문제를 해결합니다.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: **[!UICONTROL Print]** 페이지의 **[!UICONTROL Requisition List]** 옵션에서 오류가 발생했습니다.

ACSD-66965 패치는 **[!UICONTROL Print]** 페이지의 **[!UICONTROL Requisition List]** 옵션으로 인해 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66965입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Print]** 페이지의 **[!UICONTROL Requisition List]** 옵션에서 `Grid.php`의 null 개체 참조로 인해 오류가 발생합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**(으)로 이동합니다.
1. **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** 및 **[!UICONTROL Enable Requisition List]**&#x200B;을(를) `Yes`(으)로 설정합니다.
1. 두 개의 간단한 제품을 만듭니다.
1. 상점 첫 화면에 로그인하고 **[!UICONTROL My Account]** 페이지를 엽니다.
1. 구매요청 목록을 생성합니다.
1. 두 제품을 모두 구매요청 목록에 지정합니다.
1. 구매요청 목록에 액세스하여 제품을 나열합니다.
1. **[!UICONTROL Print]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

**[!UICONTROL Print]** 페이지의 **[!UICONTROL Requisition List]** 옵션은 오류 없이 인쇄 미리 보기를 표시합니다.

<u>실제 결과</u>:

다음 오류 메시지가 나타납니다. *응용 프로그램을 실행하는 동안 오류가 발생했습니다. 자세한 내용은 예외 로그를 참조하십시오.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
