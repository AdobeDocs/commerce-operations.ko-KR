---
title: 'ACSD-57337: 액세스 제한이 있는 관리자는 *회사* 그리드에서 모든 회사를 볼 수 있습니다.'
description: 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 *회사* 그리드의 모든 웹 사이트에서 회사를 볼 수 있는 Adobe Commerce 문제를 해결하려면 ACSD-57337 패치를 적용합니다.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: 액세스 제한이 있는 관리자는 *회사* 그리드에서 모든 회사를 볼 수 있습니다.

ACSD-57337 패치는 특정 웹 사이트에 대한 액세스 제한이 있는 관리자가 *회사* 그리드의 모든 웹 사이트에서 회사를 볼 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57337입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

특정 웹 사이트에 대한 액세스 제한이 있는 관리자는 *회사* 그리드의 모든 웹 사이트에서 회사를 볼 수 있습니다.

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 다른 웹 사이트에 할당된 몇 개의 회사를 만듭니다.
1. 관리자 사용자 역할을 만들고 역할 범위를 만든 웹 사이트로 설정합니다.
1. 관리자를 만들고 만든 역할에 할당합니다.
1. 새 관리자로 로그인합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;을(를) 열고 회사 목록을 확인합니다.

<u>예상 결과</u>:

추가 웹 사이트에 할당된 회사는 *회사* 그리드에 표시됩니다.

<u>실제 결과</u>:

모든 회사가 *회사* 그리드에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
