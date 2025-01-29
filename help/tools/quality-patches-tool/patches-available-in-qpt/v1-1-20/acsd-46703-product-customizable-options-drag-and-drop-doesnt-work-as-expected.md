---
title: 'ACSD-46703: 제품 사용자 지정 드래그 앤 드롭이 작동하지 않음'
description: 이 문서에서는 제품 사용자 지정 가능 옵션 끌어서 놓기가 예상대로 작동하지 않는 문제에 대한 해결 방법을 제공합니다.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-46703: 제품 사용자 지정 드래그 앤 드롭이 작동하지 않음

ACSD-46703 패치는 제품 사용자 지정 가능 옵션(드래그 앤 드롭)이 예상대로 작동하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46703입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5

>[!NOTE]
>
>이 패치는 새로운 [품질 패치 도구] 릴리스를 사용하는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자는 사용자 지정 가능한 옵션을 한 페이지에서 다른 페이지로 드래그하여 놓을 수 없습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 간단한 제품에 사용자 정의 가능한 옵션을 추가하고 20개 이상의 옵션을 추가하여 페이지 매김 을 수행했는지 확인하십시오.
1. 사용자 지정 가능한 옵션을 동일한 페이지 내에서 이동(드래그 앤 드롭)해 보십시오.
1. 이제 사용자 지정 가능한 옵션을 2페이지에서 1페이지로 이동해 보십시오.

<u>예상 결과</u>:

* 한 페이지에서 다른 페이지로 사용자 지정 가능한 옵션을 끌어다 놓을 수 있습니다.
* 끌어서 놓기 기능을 사용하여 여러 페이지에 대해서도 값을 정렬할 수 있습니다.

<u>실제 결과</u>:

드래그 앤 드롭 기능을 사용하여 다른 페이지로 값을 이동할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 품질 패치 도구 안내서의 [품질 패치 도구 > 사용량](/help/tools/quality-patches-tool/usage.md).
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 품질 패치 도구 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하십시오.
