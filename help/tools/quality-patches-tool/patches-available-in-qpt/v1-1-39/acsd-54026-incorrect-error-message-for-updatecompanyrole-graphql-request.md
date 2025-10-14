---
title: 'ACSD-54026: updateCompanyRole GraphQL 요청에 대한 잘못된 오류 메시지'
description: ACSD-54026 패치를 적용하여 권한이 없는 사용자에 대한 updateCompanyRole GraphQL 요청에 대해 잘못된 오류 메시지가 있는 Adobe Commerce 문제를 수정합니다.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026: `updateCompanyRole` GraphQL 요청에 대해 잘못된 오류 메시지

ACSD-54026 패치는 권한이 없는 사용자에 대한 `updateCompanyRole` GraphQL 요청에 잘못된 오류 메시지가 있는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54026입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

권한이 없는 사용자에 대한 `updateCompanyRole` GraphQL 요청에 대해 잘못된 오류 메시지를 받고 있습니다.

<u>재현 단계</u>:

1. 구성에서 B2B 회사를 활성화합니다.
1. 회사를 만듭니다.
1. 전달자 토큰을 전달하지 않거나 잘못된 전달자 토큰을 사용하여 `updateCompanyRole` GraphQL 요청을 보냅니다.
1. GraphQL 응답에서 오류 메시지를 확인합니다.

<u>예상 결과</u>:

다음 오류 메시지가 표시됩니다. *현재 고객은 권한이 없습니다.*

<u>실제 결과</u>:

다음 오류 메시지가 표시됩니다. *고객이 회사 사용자가 아닙니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [&#x200B; 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
