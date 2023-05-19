---
title: 증분 ID 변경
description: 상거래 데이터베이스 엔터티의 증분 ID를 변경합니다.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 증분 ID 변경

이 문서에서는 다음을 사용하여 특정 상거래 저장소의 상거래 데이터베이스(DB) 엔티티(주문, 송장, 대변 메모 등)에 대한 증분 ID를 변경하는 방법에 대해 설명합니다. `ALTER TABLE` SQL 문.

## 영향을 받는 버전

- Adobe Commerce(온-프레미스): 2.x.x
- 클라우드 인프라의 Adobe Commerce: 2.x.x
- 내 SQL: [지원되는 모든 버전](../../installation/prerequisites/database/mysql.md)

## 증분 ID를 언제 변경해야 합니까

다음과 같은 경우 새 DB 엔티티의 증분 ID를 변경해야 할 수 있습니다.

- 라이브 사이트에서 하드 백업 복원 후
- 일부 주문 레코드가 손실되었지만 해당 ID는 현재 판매자 계정의 결제 게이트웨이(예: PayPal)에서 이미 사용되고 있습니다. 이러한 경우 결제 게이트웨이는 동일한 ID를 가진 새 주문 처리를 중지하고 &quot;송장 ID 복제&quot; 오류를 반환합니다

>[!INFO]
>
>또한 PayPal의 지급 입고 환경설정에서 송장 ID당 복수 지급을 허용하여 PayPal에 대한 지급 게이트웨이 문제를 해결할 수 있습니다. 다음을 참조하십시오 [PayPal 게이트웨이 거부 요청 - 중복 송장 문제] 다음에서 _기술 자료_.

## 전제 조건 단계

1. 새 증분 ID를 변경해야 하는 저장소 및 엔티티를 찾습니다.
1. MySQL DB에 연결합니다.
클라우드 인프라의 Adobe Commerce의 경우 먼저 SSH를 사용하여 환경에 연결해야 합니다.
1. 현재 확인 `auto_increment` 다음 쿼리를 사용한 엔티티 시퀀스 테이블 값:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

ID=1인 저장소에서 주문에 대한 자동 증가를 확인하는 경우 테이블 이름은 &#39;sequence_order_1&#39;이 됩니다.

값: `auto_increment` 열은 &#39;1234&#39;로, 스토어에서 `ID=1` 은(는) ID &#39;#100001234&#39;을(를) 갖게 됩니다.

## 증분 ID를 변경하려면 엔티티 업데이트

다음 쿼리를 사용하여 엔티티를 업데이트합니다.

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
중요: 새 증분 값은 현재 증분 값보다 커야 합니다.

다음 쿼리를 실행한 후:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

다음 주문은 상점에서 `ID=1` 은(는) ID &#39;#100002000&#39;을(를) 갖게 됩니다.

## 클라우드 프로덕션 환경에 대한 추가 권장 단계

를 실행하기 전에 `ALTER TABLE` 클라우드 인프라에서 Adobe Commerce의 프로덕션 환경에서 쿼리하려면 다음 단계를 수행하는 것이 좋습니다.

- 스테이징 환경에서 증분 ID를 변경하는 전체 절차를 테스트합니다
- [DB 백업 만들기] 실패 시 프로덕션 DB를 복원하려면

<!-- Link Definitions -->

[PayPal 게이트웨이 거부 요청 - 중복 송장 문제]: https://support.magento.com/hc/en-us/articles/115002457473
[DB 백업 만들기]: https://support.magento.com/hc/en-us/articles/360003254334
[지원되는 모든 버전]
