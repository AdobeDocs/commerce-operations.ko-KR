---
title: 'ACSD-61805: REST API를 통해 미납 주문 상태를 업데이트한 후 스토어프론트에서 재고 문제를 수정합니다'
description: REST API를 통해 미납 주문 상태를 업데이트한 후 ACSD-61805 패치를 적용하여 제품이 상점 진열대에서 품절 상태로 유지되는 Adobe Commerce 문제를 해결합니다
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805: REST API를 통해 미납 주문 상태를 업데이트한 후 스토어프론트에서 재고 문제를 수정합니다

ACSD-61805 패치는 REST API를 통해 미납 주문 상태를 업데이트한 후 스토어에서 제품이 품절 상태로 유지되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61805입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 통해 미납 주문 상태를 업데이트한 후 상점 진열대에 제품이 품절 상태로 남아 있습니다.

<u>재현 단계</u>:

1. 샘플 데이터를 사용하여 클린 인스턴스를 설치합니다.
1. 새 인벤토리 소스를 만듭니다.
1. 새 재고 재고를 생성하고 새 출처를 지정합니다.
1. 새 소스를 제품 24MB01에 할당합니다.
1. 두 제품 소스에 대해 **[!UICONTROL Source Item Status]**&#x200B;을(를) `In Stock`(으)로 설정합니다.
1. 두 제품 수량에 대해 수량(**[!UICONTROL QTY]**)을 *0*(으)로 설정합니다.
1. 제품을 저장합니다.
1. 이 끝점 URL에서 관리 토큰 가져오기: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. 끝점을 사용하여 제품 업데이트: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. cron 작업을 두 번 실행합니다(한 번은 예약을 만들고 한 번은 예약을 실행).

   ```bash
   bin/magento cron:run
   ```

1. 프론트엔드에 가셔서 제품을 확인해 보세요

<u>예상 결과</u>:

제품은 *재고*&#x200B;여야 합니다.

<u>실제 결과</u>:

제품이 *품절*&#x200B;되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
