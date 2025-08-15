---
title: 'ACSD-65775: 복수 수량에 대한 REST API 주문 상세내역의 ''base_row_total'' 및 ''row_total'' 값이 잘못됨'
description: ACSD-65775 패치를 적용하여 동일한 항목의 여러 수량이 주문되면 REST API 주문 세부 사항이 잘못된 'base_row_total' 및 'row_total' 값을 반환하는 Adobe Commerce 문제를 해결합니다.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: ce5a136dd59c52d5fa5b555b3ee74fe14d7e53a4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-65775: 여러 수량에 대한 REST API 주문 세부 정보에 잘못된 `base_row_total` 및 `row_total` 값이 있습니다.

ACSD-65775 패치는 동일한 항목의 여러 수량을 주문했을 때 REST API 주문 세부 사항이 잘못된 `base_row_total` 및 `row_total` 값을 반환하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-65775입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 세부 사항 REST API 응답의 `base_row_total` 및 `row_total`은(는) 동일한 항목의 여러 수량을 주문하는 경우 총 가격 대신 단가를 표시합니다.

<u>재현 단계</u>:

1. 간단한 두 가지 제품을 만드세요: 10달러 가격의 simple1과 15달러 가격의 simple2입니다.
1. 새 고객 계정을 만듭니다.
1. 수량이 2인 simple1과 수량이 3인 simple2를 장바구니에 추가합니다.
1. 고객 계정을 사용하여 주문합니다.
1. 다음 페이로드를 사용하여 `/rest/V1/integration/admin/token`에 POST 요청을 전송하여 관리 토큰을 얻습니다.

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. `/rest/default/V1/orders/1`에 대한 GET 요청을 사용하여 주문 세부 정보를 검색합니다.

<u>예상 결과</u>:

`base_row_total` 및 `row_total`은(는) 수량에 품목 가격을 곱한 값으로 계산된 총 가격을 반영해야 합니다(예: simple1의 경우 2 × $10 = $20).

<u>실제 결과</u>:

`base_row_total` 및 `row_total`은(는) 단가만 반환합니다(예: simple1의 경우 $20 대신 $10).

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
