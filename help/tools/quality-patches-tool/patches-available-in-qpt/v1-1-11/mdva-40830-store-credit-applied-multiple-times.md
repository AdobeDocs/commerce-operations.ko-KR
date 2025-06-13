---
title: 'MDVA-40830: 주문 중에 저장소 크레딧이 여러 번 적용됨'
description: MDVA-40830 패치는 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40830입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Orders, Returns
role: Admin
exl-id: 4ee952c8-2736-47b2-84f6-a7a0556608dd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-40830: 주문 중에 저장소 크레딧이 여러 번 적용됨

MDVA-40830 패치는 주문 배치 중에 스토어 크레딧이 여러 번 적용되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40830입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

매장 크레딧은 주문 배치 중 여러 번 적용됩니다.

<u>재현 단계</u>:

1. 고객을 생성하고 고객 계정에 스토어 크레딧을 추가합니다.
1. 간단한 제품을 장바구니에 추가합니다.
1. 장바구니에 대한 배송 주소 및 청구 주소를 설정합니다.
1. 장바구니의 grand_total을 확인합니다.
1. 다음 GraphQL 요청을 사용하여 장바구니에 스토어 크레딧을 적용합니다.

<pre>
<code class="language-graphql">
mutation &lbrace;
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) &lbrace;
    cart &lbrace;
      prices &lbrace;
        grand_total &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
      applied_store_credit &lbrace;
        applied_balance &lbrace;
          currency
          value
        &rbrace;
        current_balance &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>예상 결과</u>:

applied_store_credit 의 값이 정확하게 적용되고, 장바구니 합계가 API 응답에 올바르게 반영됩니다.

<u>실제 결과</u>:

applied_store_credit 값이 두 번 적용되어 장바구니와 grand_total에 모두 영향을 줍니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
