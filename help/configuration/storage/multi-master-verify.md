---
title: 분할 데이터베이스 확인
description: Commerce 분할 데이터베이스 구성이 제대로 작동하는지 확인하는 방법을 알아봅니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 분할 데이터베이스 확인

{{ee-only}}

{{deprecate-split-db}}

구성 후 마스터 데이터베이스는 다음과 같이 구성됩니다.

- 기본 상거래 데이터베이스: 369표
- 전자 상거래 견적 데이터베이스: 11개 테이블
- 상거래 영업 데이터베이스: 55개 표

분할된 데이터베이스가 제대로 작동하는지 확인하려면 다음 작업을 수행하고 다음과 같은 데이터베이스 도구를 사용하여 데이터가 데이터베이스 테이블에 추가되었는지 확인합니다 [pmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| 확인할 사항 | 확인 방법 |
| -------------- | ------------- |
| 견적 데이터베이스가 작동합니다. | 장바구니에 항목을 추가합니다. 행이 견적 데이터베이스에 추가되었는지 확인합니다. `quote`, `quote_address`, 및 `quote_item` 표. |
| 영업 데이터베이스가 작동 중입니다. | 주문(수표/통화 주문을 포함한 모든 지급 방법)을 완료합니다. 행이 판매 데이터베이스에 추가되었는지 확인합니다. `sales_order_address`, `sales_order_item`, 및 `sales_order_payment` 표. |

>[!WARNING]
>
>두 개의 추가 데이터베이스 인스턴스를 수동으로 백업해야 합니다. 상거래(Commerce)는 기본 데이터베이스 인스턴스만 백업합니다. 다음 [`magento setup:backup --db`](../../installation/tutorials/backup.md) 명령 및 관리 옵션은 추가 테이블을 백업하지 않습니다.
