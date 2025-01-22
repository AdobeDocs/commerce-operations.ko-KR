---
title: '관리 패널의 ACSD-62708: [!DNL TinyMCE] 7 편집기 글꼴 크기에 PT가 표시됩니다.'
description: ACSD-62708 패치를 적용하여 관리자의  [!DNL TinyMCE] 7 편집기 글꼴 크기가 PX가 아닌 PT로 표시되는 Adobe Commerce 문제를 해결합니다. 이제 PT 대신 PX로 글꼴 크기를 설정할 수도 있습니다.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708: 관리 패널의 [!DNL TinyMCE] 7 편집기 글꼴 크기에 PT가 표시됩니다.

ACSD-62708 패치는 관리 패널의 [!DNL TinyMCE] 7 편집기 글꼴 크기가 PX가 아닌 PT로 표시되는 문제를 해결합니다. 이 패치를 사용하면 글꼴 크기를 PX 단위로 설정할 수 있습니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-62708입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리 패널의 [!DNL TinyMCE] 7 편집기는 글꼴 크기를 PX가 아닌 PT로 표시합니다.

<u>재현 단계</u>:

1. 관리 패널에서 제품 편집 페이지를 엽니다.
1. [!UICONTROL Content] 섹션을 확장합니다.
1. [!DNL TinyMCE] 편집기에서 글꼴 컨트롤을 확인합니다.

<u>예상 결과</u>:

글꼴 크기는 픽셀 단위여야 합니다.

<u>실제 결과</u>:

글꼴 크기는 PT 단위입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).