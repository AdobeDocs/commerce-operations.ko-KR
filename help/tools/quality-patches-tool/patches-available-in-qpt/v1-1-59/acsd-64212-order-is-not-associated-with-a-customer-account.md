---
title: 'ACSD-64212: 주문을 한 후  [!DNL GraphQL] 을(를) 통해 만든 고객 계정에 주문이 연결되지 않음'
description: ACSD-64212 패치를 적용하여 주문을 한 후  [!DNL GraphQL] 을(를) 통해 만든 고객 계정에 주문이 연결되지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Checkout, Customers
role: Admin, Developer
exl-id: be62e635-2a61-41ed-9c1d-b2c54ee01024
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212: 주문 후 [!DNL GraphQL]을(를) 통해 만든 고객 계정에 주문이 연결되지 않음

ACSD-64212 패치는 주문을 수행한 후 [!DNL GraphQL]을(를) 통해 만든 고객 계정에 주문이 연결되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-64212입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p3

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문을 한 후 [!DNL GraphQL]을(를) 통해 계정을 만들 때 주문이 고객 계정에 연결되어 있지 않습니다.

<u>재현 단계</u>:

1. 프론트 엔드에 손님 주문을 하세요.
1. 계정을 만들려면 다음 요청을 보냅니다.

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>예상 결과</u>:

고객 주문은 고객 계정이 만들어진 후에 고객과 연결됩니다.

<u>실제 결과</u>:

고객 계정이 생성되었지만 게스트 주문이 고객과 연결되어 있지 않습니다.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).


## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
