---
title: 'ACSD-65195: GraphQL ''createCompany'' 돌연변이가 필수 지역이 없는 국가에 대한 오류를 반환합니다.'
description: ACSD-65195 패치를 적용하여 영역이 필요하지 않은 국가에 GraphQL 'createCompany' 돌연변이로 인해 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%
---
# ACSD-65195: GraphQL `createCompany` 돌연변이가 필요한 지역이 없는 국가에 대해 오류를 반환합니다.

ACSD-65195 패치는 영역이 필요하지 않은 국가에 대해 [!UICONTROL GraphQL] `createCompany` 돌연변이로 인해 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65195입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL GraphQL] `createCompany` 돌연변이는 지역이 필요하지 않은 국가에 대해 지정되면 오류를 반환합니다.

<u>재현 단계</u>:

1. **[!UICONTROL B2B Companies]** 사용
1. 지역 필드가 지정되지 않은 국가에 대해 지정된 필드가 있는 `createCompany` [!UICONTROL GraphQL] 돌연변이를 보냅니다. 예: [!UICONTROL country_id]: *AE* 및 [!UICONTROL region]: *두바이*.
1. GraphQL 응답을 확인합니다.

<u>예상 결과</u>:

필요 없는 국가에 대해 지역을 지정한 경우 오류를 반환하지 않고 회사를 성공적으로 만들어야 합니다.

<u>실제 결과</u>:

회사가 생성되지 않고 다음 오류가 반환됩니다.
`Error: Invalid value of "Dubai" provided for the region field.`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 업그레이드 및 패치 > 패치 적용.

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
