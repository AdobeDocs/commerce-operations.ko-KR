---
title: 'MDVA-37592: 가격이 0인 제품에 대해 가격별 정렬이 작동하지 않음'
description: MDVA-37592 Adobe Commerce 패치는 공유 카탈로그에 가격 0이 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37592입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%
---
# MDVA-37592: 가격이 0인 제품에 대해 가격별 정렬이 작동하지 않음

MDVA-37592 Adobe Commerce 패치는 공유 카탈로그에 가격 0이 할당된 제품에 대해 가격별 정렬이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37592입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce on our cloud architecture 2.4.0-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 유형) 2.3.6-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가격 기준 정렬이 공유 카탈로그에 가격 0이 지정된 제품에 대해 제대로 작동하지 않습니다.

<u>필수 구성 요소</u>:

B2B가 설치되었습니다.

<u>재현 단계</u>:

1. 공유 카탈로그를 활성화합니다.
1. $50, $60, $70, $80와 같은 가격으로 4개의 제품을 만들어 카테고리에 할당합니다.
1. 위의 제품으로 공유 카탈로그를 만듭니다.
1. 가격이 $70인 제품에 대한 사용자 지정 가격을 0으로 설정합니다.
1. 이제 회사 사용자를 만들고 방금 만든 공유 카탈로그에 할당합니다.
1. 회사 계정을 사용하여 로그인하고 제품이 할당된 범주를 찾습니다.
1. 가격을 기준으로 정렬해 보세요.

<u>예상 결과</u>:

가격이 0인 제품은 정확하게 정렬되어 있습니다.

<u>실제 결과</u>:

가격이 0인 제품이 제대로 정렬되지 않았습니다. 대신 원래 가격에 따라 정렬됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!DNL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
