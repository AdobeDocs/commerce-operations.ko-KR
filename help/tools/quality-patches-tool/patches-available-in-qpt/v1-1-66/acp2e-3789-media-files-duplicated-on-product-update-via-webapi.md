---
title: 'ACP2E-3789: WebAPI를 통해 제품 업데이트에 중복되는 미디어 파일'
description: ACP2E-3789 패치를 적용하여 미디어 ID가 제공될 때 WebAPI를 통해 제품이 미디어 파일을 복제하는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789: WebAPI를 통해 제품 업데이트에 중복되는 미디어 파일

ACP2E-3789 패치는 미디어 ID가 제공될 때 WebAPI를 통해 제품 업데이트가 미디어 파일을 복제하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACP2E-3789입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

WebAPI를 통해 제품을 미디어 ID로 업데이트하면 시스템이 미디어 파일을 바꾸는 대신 미디어 파일을 복제하고, 각 API 호출로 새 파일을 만들고, `/pub/media/catalog/products/cache/` 디렉터리를 오버로드한 이미지를 빌드합니다.

<u>재현 단계</u>:

1. 제품을 만들고 이미지를 추가합니다.
1. `base_url/rest/V1/products/<sku>`에서 REST API를 사용하여 제품 세부 정보를 가져옵니다.
1. `media_gallery_entrie`을(를) 변경되지 않은 상태로 유지하면서 제품을 업데이트하려면 PUT 요청을 수행합니다(동일한 이미지 이름 및 파일).
1. 업데이트 전후에 `pub/media/catalog/product/xx/yy` 디렉터리를 확인하십시오.

<u>예상 결과</u>:

미디어 ID가 요청에 포함되면 이미지 파일이 바뀝니다.

<u>실제 결과</u>:

이미지가 새 이름(예: wb04-blue-1.jpg)으로 복제되어 불필요한 파일이 누적됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
