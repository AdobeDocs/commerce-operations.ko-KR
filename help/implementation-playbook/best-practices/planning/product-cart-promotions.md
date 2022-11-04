---
title: 프로모션 구성 우수 사례
description: 상거래 저장소 성능을 최적화하기 위해 판매 규칙 및 쿠폰 코드를 구성하는 모범 사례에 대해 배웁니다.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 프로모션 구성 우수 사례

최상의 성능을 위해 장바구니에 있는 항목에 대한 판매 및 프로모션을 구성하려면 다음 모범 사례를 따릅니다.

- **판매 규칙(장바구니 가격 규칙)**- 모든 웹 사이트에 대해 1,000개 이하의 장바구니 가격 규칙을 구성합니다
   - 사용하지 않는 규칙을 관리하고 제거합니다.
   - 가장 효율적인 일치를 위해 엄격한 규칙 조건(예: 속성 또는 카테고리 필터)을 추가합니다.
- **쿠폰**—
   - 데이터베이스의 총 쿠폰 수가 250,000개 미만인지 확인합니다.
   - 사용하지 않고 만료된 쿠폰을 제거합니다.
   - 캠페인 요구 사항을 충족하는 데 필요한 쿠폰 수만 생성합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 성능에 영향을 줄 수 있음

권장 최대 장바구니 가격 규칙 또는 쿠폰 수를 초과하는 경우 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 장바구니에 제품을 추가할 때 응답 시간이 늘어났습니다.
- 미니카트를 로드하고 렌더링하는 시간이 늘어났습니다.
- 장바구니 페이지를 렌더링하는 데 걸리는 시간이 늘어났습니다.
- 렌더링 시간 증가 **합계** 차단.
- 쿠폰을 적용하는 데 2초 이상 걸릴 수 있습니다.

## 추가 정보

- [마케팅 캠페인 및 프로모션 이해](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [장바구니 가격 규칙](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [자습서: 장바구니 가격 규칙 만들기](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [쿠폰 코드](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce on cloud 인프라: 저장소 구성 우수 사례](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
