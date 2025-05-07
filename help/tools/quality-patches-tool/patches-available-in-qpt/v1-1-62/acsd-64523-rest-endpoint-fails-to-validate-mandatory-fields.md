---
title: 'ACSD-64523: REST 끝점이 필수 필드의 유효성을 검사하지 못했습니다.'
description: REST 끝점 "[V1/import/csv]"이 필수 필드의 유효성을 검사하지 못하여 필수 필수 필드를 제공하지 않고 제품을 만들 수 있는 문제를 해결하려면 ACSD-64523 패치를 적용하십시오.
feature: REST, Products, Admin Workspace
role: Admin, Developer
source-git-commit: 4bf9a5eb2e423f5981ee9234be57230a6dff3913
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# ACSD-64523: REST 끝점이 필수 필드의 유효성을 검사하지 못했습니다.

ACSD-64523 패치는 REST 끝점 [V1/import/csv]이 필수 필드의 유효성을 검사하지 못하여 필수 데이터 없이 제품을 만들 수 있는 문제를 해결합니다. 이 문제를 해결하려면 인증 헤더를 업데이트하십시오. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST 끝점 `[V1/import/csv]`이(가) 필수 필드를 확인하지 못해 이러한 필수 필드를 제공하지 않고 제품을 만들 수 있습니다.

<u>재현 단계</u>:

1. 다음 페이로드를 실행합니다(인증 헤더 업데이트).

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>예상 결과</u>:

필수 필드 없이 제품을 저장할 수 없습니다.

<u>실제 결과</u>:

필수 속성인 제품 이름을 지정하지 않고 제품이 저장되었습니다. 따라서 백엔드 제품 그리드에 액세스할 수 없으며, 다음과 같은 오류가 발생합니다.

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
