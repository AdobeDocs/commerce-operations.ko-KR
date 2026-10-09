---
title: 'ACP2E-3964: REST API를 통해 나열되지 않은 비디오로 구성 가능한 하위 제품'
description: ACP2E-3964 패치를 적용하여 [!UICONTROL Media Gallery]에 있는 비디오가 있는 구성 가능한 제품의 하위 제품이 REST API를 통해 나열되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 61c5b97c-79aa-4ee7-96b3-70924d2c85a0
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '371'
ht-degree: 0%
---
# ACP2E-3964: REST API를 통해 나열되지 않은 비디오로 구성 가능한 하위 제품

ACP2E-3964 패치는 **[!UICONTROL Media Gallery]**&#x200B;에 있는 비디오가 있는 구성 가능한 제품의 하위 제품이 REST API를 통해 나열되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3964입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Media Gallery]**&#x200B;에서 비디오가 포함된 구성 가능한 제품의 하위 제품은 REST API를 통해 나열할 수 없으므로 오류 응답이 발생합니다.

<u>재현 단계</u>:

1. 구성 가능한 새 제품을 만들고 단일 하위 제품을 추가합니다.
1. 하위 제품을 편집하고 **[!UICONTROL Images and Videos]** 아래에 비디오를 추가하십시오(예: [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. 하위 제품을 저장합니다.
1. 관리자 전달자 토큰을 사용하여 REST API 끝점 `rest/v1/configurable-products/%sku%/children`에 GET 요청을 보냅니다.

<u>예상 결과</u>:

REST API는 **[!UICONTROL Media Gallery]**&#x200B;의 비디오 정보를 포함하여 오류 없이 하위 제품 데이터를 반환해야 합니다.

<u>실제 결과</u>:

REST API가 오류를 반환합니다.

```text
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
