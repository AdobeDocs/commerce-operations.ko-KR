---
title: 프로모션 구성에 대한 우수 사례
description: Commerce 스토어 성과를 최적화하기 위해 판매 규칙 및 쿠폰 코드를 구성하는 모범 사례에 대해 알아봅니다.
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 프로모션 구성에 대한 우수 사례

최상의 성능을 얻으려면 다음 모범 사례에 따라 장바구니에 있는 항목에 대한 판매 및 프로모션을 구성하십시오.

- **판매 규칙(장바구니 가격 규칙)**-모든 웹 사이트에 대해 1000개 이하의 장바구니 가격 규칙 구성
   - 사용하지 않는 규칙을 관리하고 제거합니다.
   - 가장 효율적인 일치를 위해 엄격한 규칙 조건(예: 속성 또는 범주 필터)을 추가합니다.
- **쿠폰**—
   - 데이터베이스의 총 쿠폰 수가 250,000개 미만인지 확인합니다.
   - 사용하지 않거나 만료된 쿠폰을 제거합니다.
   - 캠페인 요구 사항을 충족하는 데 필요한 쿠폰 수만 생성합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 성능에 영향을 미칠 수 있음

장바구니 가격 규칙 또는 쿠폰이 권장되는 최대 수보다 많으면 다음 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 장바구니에 제품이 추가될 때 응답 시간이 늘어났습니다.
- 미니 마트를 로드하고 렌더링하는 데 시간이 늘어났습니다.
- 장바구니 페이지를 렌더링하는 데 시간이 늘어났습니다.
- 렌더링 시간 증가 **총계** 체크아웃 페이지에서 을(를) 차단합니다.
- 쿠폰 적용은 2초 이상 소요될 수 있습니다.

## 추가 정보

- [마케팅 캠페인 및 프로모션 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [장바구니 가격 규칙](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [자습서: 장바구니 가격 규칙 만들기](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [쿠폰 코드](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [클라우드 인프라의 Adobe Commerce: 스토어 구성 모범 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
