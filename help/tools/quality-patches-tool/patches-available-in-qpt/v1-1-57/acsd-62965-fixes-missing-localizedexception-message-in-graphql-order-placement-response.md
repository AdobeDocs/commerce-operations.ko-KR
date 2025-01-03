---
title: 'ACSD-62965: GraphQL 주문 배치 응답에서 누락된 LocalizedException 메시지가 수정되었습니다.'
description: ACSD-62965 패치를 적용하여 'LocalizedException' 메시지가 주문 배치 중 GraphQL 응답에 포함되지 않은 Adobe Commerce 문제를 해결합니다.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: GraphQL 주문 배치 응답에서 누락된 `LocalizedException` 메시지가 수정되었습니다.

ACSD-62965 패치는 주문 배치 중에 `LocalizedException` 메시지가 GraphQL 응답에 포함되지 않은 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57에서 사용할 수 있습니다. 패치 ID는 ACSD-62965입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 배치에 대한 GraphQL 응답에 `LocalizedException` 메시지가 포함되어 있지 않으므로 디버깅을 위한 오류 세부 정보가 부족합니다.

<u>재현 단계</u>:

1. 깔끔한 **[!DNL Adobe Commerce]** 인스턴스를 설치합니다.
1. 장바구니에 제품을 추가하고 주문 배치 단계로 진행합니다.
1. `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`의 `Magento\Framework\Exception\LocalizedException`에 `LocalizedException`을(를) 추가합니다.
1. 다음 줄 뒤에 예외를 삽입합니다.

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   예외를 추가합니다.

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. 주문 GraphQL 요청을 실행합니다.

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. 응답을 확인합니다.
   1. 응답에 `LocalizedException` 메시지가 포함되어 있지 않습니다.
   1. 잘못된 응답의 예:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>예상 결과</u>:

`LocalizedException`이(가) 발생한 경우 오류 처리 개선을 위해 주문 배치 GraphQL 응답에 예외 메시지를 포함해야 합니다.

<u>실제 결과</u>:

`LocalizedException`이(가) 발생하면 주문 배치 GraphQL 응답에 예외 메시지가 포함되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
