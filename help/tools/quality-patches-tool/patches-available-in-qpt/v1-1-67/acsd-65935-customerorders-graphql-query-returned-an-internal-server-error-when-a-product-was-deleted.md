---
title: 'ACSD-65935: ''customerOrders'' GraphQL 쿼리에서 제품 삭제 시 내부 서버 오류가 반환됨'
description: ACSD-65935 패치를 적용하여 제품 삭제 시 'customerOrders' GraphQL 쿼리가 내부 서버 오류를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: fd0b7043770bbbd12fbb9aad8cddaa2434d2ea5b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# ACSD-65935: 제품을 삭제할 때 `customerOrders` GraphQL 쿼리에서 내부 서버 오류를 반환했습니다.

ACSD-65935 패치는 제품이 삭제될 때 `customerOrders` GraphQL 쿼리에서 내부 서버 오류를 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-65935입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.7-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 삭제되면 `customerOrders` GraphQL 쿼리에서 내부 서버 오류를 반환합니다.

<u>재현 단계</u>:

1. 두 개의 간단한 제품 만들기
1. 고객을 만들고 프론트엔드의 두 제품을 주문합니다.
1. 백엔드로 이동하여 제품 하나를 삭제합니다.
1. 고객 토큰 만들기:

```
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. `eligible_for_return` 필터(PWA에서 고객 주문을 가져오는 데 사용됨)를 사용하여 주문 목록을 검색합니다.

```
https://localhost/pub/graphql
{
  customerOrders {
    items {
      order_number
      id
      created_at
      grand_total
      status
			items{
				eligible_for_return
			}
    }
  }
}
```

<u>예상 결과</u>:

주문 목록은 오류 없이 수집됩니다.

<u>실제 결과</u>:

예외: *내부 서버 오류*

```
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 &#x200B;](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
