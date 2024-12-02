---
title: 'ACSD-44938: 게스트 사용자에 대한  [!DNL GraphQL] 요청에서 VAT_ID를 적용할 수 없습니다.'
description: ACSD-44938 패치는 게스트 사용자에 대한  [!DNL GraphQL] 요청에서 'VAT_ID'를 적용할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-44938입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 3fdefc6201714c441d63574d293863e83205894b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938: 게스트 사용자에 대한 [!DNL GraphQL] 요청에서 VAT_ID를 적용할 수 없습니다.

ACSD-44938 패치는 게스트 사용자에 대한 [!DNL GraphQL] 요청에서 `VAT_ID`을(를) 적용할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-44938입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

게스트 사용자에 대한 [!DNL GraphQL] 요청에서 `VAT_ID`을(를) 적용할 수 없습니다.

<u>재현 단계</u>:

1. 개발자 설명서에서 [[!DNL GraphQL] 자습서](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)에 언급된 단계에 따라 장바구니를 만듭니다.
1. [!DNL GraphQL]을(를) 사용하는 게스트 사용자에 대해 `VAT_ID`을(를) 적용해 보십시오.

<u>예상 결과</u>:

`VAT_ID`은(는) 등록된 고객의 경우와 동일한 방식으로 적용할 수 있습니다. 개발자 설명서에서 [`createCustomerAddress` 돌연변이](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) 문서를 참조하십시오.

<u>실제 결과</u>:

[!DNL GraphQL]을(를) 사용하는 게스트 사용자에 대해 `VAT_ID`을(를) 적용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
