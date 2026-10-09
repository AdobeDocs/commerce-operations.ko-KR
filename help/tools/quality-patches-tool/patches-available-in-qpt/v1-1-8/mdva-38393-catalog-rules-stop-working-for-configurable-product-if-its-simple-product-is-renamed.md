---
title: 'MDVA-38393: 간단한 제품의 이름이 변경된 경우 구성 가능한 제품에 대한 카탈로그 규칙 작동이 중지됩니다.'
description: MDVA-38393 패치는 구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38393입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
subfeature_v2:
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
source-wordcount: '517'
ht-degree: 0%
---
# MDVA-38393: 간단한 제품의 이름이 변경된 경우 구성 가능한 제품에 대한 카탈로그 규칙 작동이 중지됩니다.

MDVA-38393 패치는 구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38393입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지됩니다.

<u>재현 단계</u>:

1. 연결된 단순 제품을 사용하여 구성 가능한 제품을 만듭니다.
1. 카테고리를 만듭니다.
1. 구성 가능한 제품만 새 범주에 할당합니다.
1. 새 카탈로그 규칙 만들기:
   * 조건 = 범주에 \&lt;새 범주 ID>가 포함됨
   * 조치 = 50% 할인
   * 활성 = 예
1. 색인 재지정을 수행합니다.
1. 구성 가능한 제품은 프론트엔드에서 확인합니다(할인이 적용되어야 함).
1. `catalogrule_product` 표를 확인하십시오. 간단한 제품에 할인이 적용되어야 합니다.
1. 관리자로 이동하여 간단한 제품의 이름을 변경합니다. `catalogrule_product_cl` 테이블에 레코드를 추가합니다.
1. cron 또는 `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` 명령을 실행합니다.
1. `catalogrule_product` 테이블을 확인합니다.

<u>예상 결과</u>:

구성 가능한 제품에는 할인이 적용됩니다.

<u>실제 결과</u>:

* 간단한 제품에 대해 만든 할인 기록이 `catalogrule_product` 표에 없습니다.
* 프론트엔드에서 구성 가능한 제품은 정가 그대로 판매됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
