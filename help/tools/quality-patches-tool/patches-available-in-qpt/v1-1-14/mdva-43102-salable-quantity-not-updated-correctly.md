---
title: 'MDVA-43102: 판매 가능 수량이 올바르게 업데이트되지 않음'
description: MDVA-43102 패치는 REST API를 통해 환불을 수행하면 판매 가능 수량이 올바르게 업데이트되지 않는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43102입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102: 판매 가능 수량이 올바르게 업데이트되지 않음

MDVA-43102 패치는 REST API를 통해 환불을 수행하면 판매 가능 수량이 올바르게 업데이트되지 않는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43102입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 사용하여 환불이 완료되면 판매 가능 수량이 올바르게 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 장바구니에 항목을 추가합니다.
1. 재고 수량 및 판매 가능 수량을 확인합니다.
1. 주문을 만듭니다.
1. 필요한 경우 송장을 생성합니다.
1. 다음 페이로드를 사용하여 송장을 환불하려면 REST 요청을 실행합니다.

   * offline method/order/`<order_id>`/refund
   * 온라인 방법/인보이스/`<invoice_id>`/환불

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. 물건을 배송하지 마십시오.
1. 재고 수량과 판매 가능 수량을 비교합니다. 둘 다 동일한 수량으로 업데이트해야 합니다.

<u>예상 결과</u>:

주문 배송 전 환불이 나오고, 제품이 재고로 반품되면 판매 가능 수량이 올바르게 업데이트 된다.

<u>실제 결과</u>:

주문 배송 전 환불이 가능하고, 제품이 재고로 반품되는 경우 판매 가능 수량이 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
