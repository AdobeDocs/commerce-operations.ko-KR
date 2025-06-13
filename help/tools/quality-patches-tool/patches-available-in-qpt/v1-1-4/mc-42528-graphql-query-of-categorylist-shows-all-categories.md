---
title: 'MC-42528: categoryList의 GraphQL 쿼리에 모든 범주가 표시됩니다.'
description: MC-42528 패치는 특정 범주의 검색 범주가 "거부"로 설정되면 'categoryList'의 GraphQL 쿼리가 할당된 범주와 할당되지 않은 범주 모두를 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MC-42528입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528: categoryList의 GraphQL 쿼리에 모든 범주가 표시됩니다.

MC-42528 패치는 특정 범주의 검색 범주가 &quot;거부&quot;로 설정되어 있을 때 `categoryList`의 GraphQL 쿼리가 할당된 범주와 할당되지 않은 범주를 모두 반환하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MC-42528입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`categoryList`의 GraphQL 쿼리가 할당된 범주와 할당되지 않은 범주를 모두 반환합니다.

<u>재현 단계</u>:

1. CAT1과 CAT2라는 두 가지 카테고리를 만들고 각 카테고리에 몇 가지 제품을 할당합니다.
1. 비공개 공유 카탈로그를 만듭니다.
1. 회사 사용자를 만들고 생성된 공유 카탈로그에 할당합니다.
1. CAT1을 사용자 지정 카탈로그에 할당하고 범주 권한을 개인 카탈로그의 고객 그룹에 대한 검색 범주를 &quot;허용&quot;으로 설정합니다.
1. CAT2에 대한 범주 권한을 개인 카탈로그의 고객 그룹에 대한 검색 범주를 &quot;거부&quot;로 설정합니다.
1. 회사 사용자로 `categoryList` 또는 `categories` GraphQL 쿼리를 실행합니다.

<u>예상 결과</u>:

CAT1만 응답에 표시됩니다.

<u>실제 결과</u>:

범주의 검색 권한에 관계없이 모든 범주가 응답에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
