---
title: 'ACSD-64118: 동일한 제품에 대한 동시 제품 저장 요청으로 인해 데이터 불일치 및 중복 항목 발생'
description: ACSD-64118 패치를 적용하여 동일한 제품을 저장하고 업데이트하는 동시 요청으로 인해 데이터 불일치 또는 제품 중복이 발생하는 Adobe Commerce 문제를 해결합니다.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118: 동일한 제품에 대한 동시 제품 저장 요청으로 인해 데이터 불일치 및 중복 항목 발생

ACSD-64118 패치는 동일한 제품을 저장하고 업데이트하라는 동시 요청이 데이터 불일치 또는 제품 중복을 초래하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-64118입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p7

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 제품을 저장하고 업데이트하기 위한 동시 요청으로 인해 데이터가 일치하지 않거나 중복되는 제품이 발생합니다.

<u>재현 단계</u>:

1. `env.php`에서 소비자를 위한 다중 프로세스 설정:

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. 기본 웹 사이트에 추가 스토어와 새 스토뷰를 추가합니다.
1. 제품을 만들기 위해 다음 페이로드와 함께 기본 스토어뷰 끝점 `/rest/default/async/bulk/V1/products`에 일괄 API 요청을 보냅니다.

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. 같은 페이로드를 사용하여 제품을 업데이트하기 위해 새 스토어뷰 끝점 `/rest/store/async/bulk/V1/products`에 일괄 API 요청을 보냅니다.
1. 캐시를 플러시합니다.
1. cron 작업을 실행합니다.
1. `catalog_product_entity` 테이블에서 이전 단계의 제품 항목을 확인합니다.

<u>예상 결과</u>:

* 제품 SKU의 단일 항목이 `catalog_product_entity` 테이블에 있어야 합니다.
* 첫 번째 REST API 요청은 하나의 데이터베이스 항목을 만들어야 하며 모든 후속 요청은 해당 데이터베이스 항목을 업데이트해야 합니다.

<u>실제 결과</u>:

동일한 SKU에 대한 여러 항목이 `catalog_product_entity` 테이블에 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
