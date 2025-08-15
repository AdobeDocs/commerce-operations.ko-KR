---
title: 'ACSD-63329: REST API를 사용하여 제품을 만들 때 날짜 및 시간 특성이 설정되지 않음'
description: REST API를 사용하여 제품을 만들 때 날짜 및 시간 필드에 기본값이 설정되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-63329 패치를 적용합니다.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: REST API를 사용하여 제품을 만들 때 날짜 및 시간 필드의 기본값이 설정되지 않음

ACSD-63329 패치는 REST API를 사용하여 새 제품을 만들 때 날짜 및 시간 필드에 기본값이 설정되지 않은 문제를 해결합니다. `/rest/default/V1/products`. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63329입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 사용하여 제품을 만들 때 날짜 및 시간 필드에 기본값이 설정되지 않았습니다. `/rest/default/V1/products`

<u>재현 단계</u>:

1. **[!UICONTROL Product]** 특성을 만들고, 기본값을 `12/31/2020`(으)로 설정하고, **[!UICONTROL Catalog Input Type for Store Owner]**&#x200B;을(를) ***[!UICONTROL Date]*** 또는 [!UICONTROL Date and Time]&#x200B;***(으)로 &#x200B;***.
1. 다른 텍스트 형식 특성을 만들고 기본값을 ***테스트 값***(으)로 설정합니다.
1. `/rest/all/V1/products/`에 대한 REST API POST 요청을 사용하여 새 제품을 만드십시오.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. 위에서 언급한 속성에 대해 저장된 값을 확인합니다.

<u>예상 결과</u>:

API를 사용하여 제품을 만들 때 **[!UICONTROL Date/Datetime]** 형식 특성에 기본값을 저장해야 합니다.

<u>실제 결과</u>:

기본값은 **[!UICONTROL Text]** 특성에 대해 저장되지만 **[!UICONTROL Date type]** 특성에 대해서는 저장되지 않습니다. **[!UICONTROL Date]** 특성 값이 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
