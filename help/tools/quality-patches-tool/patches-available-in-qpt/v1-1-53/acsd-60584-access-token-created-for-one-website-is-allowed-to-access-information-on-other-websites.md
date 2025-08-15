---
title: 'ACSD-60584: 한 웹 사이트에 대해 생성된 액세스 토큰은 다른 웹 사이트의 정보에 액세스할 수 있습니다.'
description: ACSD-60584 패치를 적용하여 한 웹 사이트에서 사용자를 위해 생성된 액세스 토큰이 다른 웹 사이트의 고객 정보에 액세스하거나 변경할 수 있는 문제를 해결합니다.
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: 한 웹 사이트에 대해 생성된 액세스 토큰은 다른 웹 사이트의 정보에 액세스할 수 있습니다.

ACSD-60584 패치는 한 웹 사이트에서 사용자를 위해 만든 액세스 토큰이 다른 웹 사이트의 고객 정보에 액세스하거나 변경할 수 있는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-60584입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

한 웹 사이트에서 사용자를 위해 만들어진 API 토큰을 사용하면 고객 정보에 액세스하고, 장바구니를 만들고, 다른 웹 사이트 보기에서 장바구니에 제품을 추가할 수 있습니다.

<u>재현 단계</u>:

1. **[!DNL Share Customer Accounts configuration]**&#x200B;이(가) **[!UICONTROL Per Website]**(으)로 설정되어 있는지 확인하십시오.
1. 추가 *웹 사이트*, *스토어* 및 *스토어뷰*&#x200B;를 만듭니다.
1. 이전 단계의 기본 *웹 사이트*&#x200B;와(과) *웹 사이트*&#x200B;에서 동일한 전자 메일을 사용하는 두 고객을 만드십시오.
1. 기본 웹 사이트에서 [!DNL GraphQL]을(를) 통해 고객 토큰을 생성합니다.
1. 생성된 토큰을 사용하여 헤더의 두 번째 웹 사이트와 함께 고객 **[!DNL GraphQL]** 쿼리를 보내 고객 정보를 검색합니다.
1. 반환된 결과를 확인합니다.

<u>예상 결과</u>:

기본 *웹 사이트*&#x200B;의 토큰이 *쿼리에 사용되므로 기본*&#x200B;웹 사이트[!DNL GraphQL]의 고객 정보가 반환됩니다.

<u>실제 결과</u>:

두 번째 웹 사이트의 고객 정보가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[!UICONTROL Quality Patches Tool]


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [[!DNL Quality Patches Tool] 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): 패치 검색[!DNL Quality Patches Tool]을 참조하세요.
