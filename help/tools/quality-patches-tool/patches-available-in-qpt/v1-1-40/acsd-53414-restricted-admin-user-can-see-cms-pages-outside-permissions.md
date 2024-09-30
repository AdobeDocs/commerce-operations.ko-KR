---
title: 'ACSD-53414: 제한된 관리자는 자신의 권한 범위를 벗어난 CMS 페이지를 볼 수 있습니다.'
description: ACSD-53414 패치를 적용하여 제한된 관리 사용자가 권한 범위를 벗어나 CMS 페이지를 볼 수 있는 Adobe Commerce 문제를 해결합니다.
feature: CMS
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: 제한된 관리자는 권한 범위를 벗어난 CMS 페이지를 볼 수 있습니다

ACSD-53414 패치를 사용하면 제한된 관리 사용자가 권한 범위를 벗어난 CMS 페이지를 볼 수 있는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53414입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제한된 관리자는 자신의 권한 범위를 벗어난 CMS 페이지를 볼 수 있습니다.

<u>재현 단계</u>:

1. 새 웹 사이트(sub_website), 스토어(sub_store) 및 스토뷰(sub_storeview)를 만듭니다.
1. sub_expert 역할을 만들어 sub_website 및 sub_store 범위를 허용합니다. [!UICONTROL Dashboard] 및 [!UICONTROL Pages] 권한만 할당하십시오.
1. 새 관리자 사용자를 만들고 sub_expert 역할에 할당합니다.
1. 다음 CSM 페이지를 sub_storeview 및 기본 storeview에 할당합니다.

   * [!UICONTROL 404 Not Found] > 하위 저장소 보기
   * [!UICONTROL 503 Service Unavailable] > 기본 상점 보기

1. 3단계에서 만든 관리자 사용자를 사용하여 관리자에 로그인합니다.
1. CMS 페이지 그리드를 확인합니다.

<u>예상 결과</u>:

*[!UICONTROL 503 Service Unavailable]* 페이지가 웹 관리자에게 표시되지 않습니다.

<u>실제 결과</u>:

*[!UICONTROL 503 Service Unavailable]*&#x200B;이(가) 웹 관리자에게 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.