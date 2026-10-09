---
title: 'MDVA-44940: 관리자의 범주를 저장하는 동안 SQL 오류 발생'
description: MDVA-44940 패치는 관리자의 범주를 저장하는 동안 SQL 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44940입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 541b5773-5ae1-55f2-8721-511b946fbd7f
    internal-label: Sales Channels
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '468'
ht-degree: 0%
---
# MDVA-44940: 관리자의 범주를 저장하는 동안 SQL 오류 발생

MDVA-44940 패치는 관리자의 범주를 저장하는 동안 SQL 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44940입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자로부터 범주를 저장할 때 SQL 오류가 발생합니다.

<u>재현 단계</u>:

1. 샘플 데이터를 설치합니다.
1. 기본 범주에 할당된 스토어 그룹으로 두 번째 웹 사이트를 만듭니다.

   * 새 저장소 그룹에 할당된 저장소 보기를 만듭니다.

1. 재고 및 이 재고에 지정된 추가 출처와 두 번째 웹 사이트에 지정된 판매 채널을 만듭니다.
1. 두 번째 웹 사이트에 할당된 테스트 제품을 만듭니다.
1. **관리자** > **카탈로그** > **범주**, **범위** = **두 번째 웹 사이트**&#x200B;를 선택하고 **범주의 제품** > **자동 정렬** > 재고 부족 제품을 맨 아래로 이동한 다음 **저장**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

범주가 저장됩니다.

<u>실제 결과</u>:

다음 오류가 발생했습니다. *범주를 저장하는 동안 문제가 발생했습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
