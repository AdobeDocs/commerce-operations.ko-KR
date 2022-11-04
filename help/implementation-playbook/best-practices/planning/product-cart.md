---
title: 제품 장바구니 우수 사례
description: 장바구니에 있는 제품 수를 제한하여 Adobe Commerce 성능을 최적화하는 방법을 알아봅니다.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# 제품 장바구니 관리에 대한 우수 사례

최상의 성능을 위해 다음 지침을 사용하여 Adobe Commerce 및 Magento Open Source에 대한 장바구니 제한을 관리합니다.

- 버전 2.3.x - 2.4.2의 경우 장바구니에 최대 100개의 제품을 사용할 수 있습니다.
- 버전 2.4.3 이상의 경우 판매 규칙 기능이 향상되어 장바구니는 최대 750대까지 증가했습니다.


버전 2.3.x - 2.4.2의 경우 장바구니 항목 제한을 기반으로 한 예상 성능은 다음과 같습니다.

- 최대 **100년** 장바구니의 제품—제품이 작동하며 응답 시간에 대한 성능 목표를 충족합니다.
- 최대 **300년** 장바구니의 제품—제품이 작동하지만 응답 시간이 타겟 이상으로 증가합니다.
- 위 **500년** 장바구니의 제품 - 장바구니 및 체크아웃 흐름은 작동하지 않을 수 있습니다

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 장바구니 항목 수 감소

장바구니 항목 수를 관리하려면 다음 전략을 사용하십시오

- 주문을 사용하여 적은 수의 행이 있는 몇 개의 작은 주문으로 분할합니다. [!UICONTROL Add Item by SKU] 기능.
- 항목 목록을 로드하는 데 필요한 사용자 지정 로직 및 장바구니 사용자 지정만 추가합니다.

## 성능에 영향을 줄 수 있음

장바구니에 권장 최대 제품 수를 초과하는 경우 다음과 같은 방법으로 사이트 성능에 영향을 줄 수 있습니다.

- 데이터 검색 작업, 장바구니 항목 유효성 검사, 가격 규칙 적용 확인, 세금 및 총 계산에 대한 응답 시간이 늘어났습니다.
- 장바구니 보기, 체크아웃 흐름 및 실행을 렌더링하는 작업을 포함하여 빠른 렌더링에 대한 응답 시간이 늘어났습니다.
- 미니카트가 있는 모든 사이트 페이지에 대한 로드 시간이 늘어났습니다.

## 추가 정보

- [제품 옵션 구성](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [장바구니 관리](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
