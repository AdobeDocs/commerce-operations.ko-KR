---
title: 증분 ID 변경
description: 상거래 데이터베이스 엔터티의 증분 ID를 변경합니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# 증분 ID 변경

이 문서에서는 `ALTER TABLE` SQL 문입니다.

## 영향을 받는 버전

- Adobe Commerce (온-프레미스): 2.x.x
- Adobe Commerce on cloud 인프라: 2.x.x
- MySQL: [지원되는 버전](../../installation/prerequisites/database/mysql.md)

## 증가 ID는 언제 변경해야 합니까?

다음과 같은 경우 새 DB 엔티티에 대한 증분 ID를 변경해야 할 수 있습니다.

- 라이브 사이트에서 하드 백업 복원 후
- 일부 주문 레코드가 손실되었지만 해당 ID가 현재 Merchant 계정에 대한 결제 게이트웨이(예: PayPal)에서 이미 사용되고 있습니다. 예를 들어, 결제 게이트웨이는 동일한 ID가 있는 새 주문 처리를 중지하여 &quot;중복된 송장 ID&quot; 오류를 반환합니다

>[!INFO]
>
>또한 PayPal의 결제 수신 환경설정에서 송장 ID당 여러 지급을 허용하여 PayPal에 대한 결제 게이트웨이 문제를 수정할 수 있습니다. 자세한 내용은 [PayPal 게이트웨이가 요청을 거부했습니다. 송장 문제가 중복되었습니다.] 에서 _기술 자료_.

## 전제 조건 단계

1. 새로운 증분 ID를 변경해야 하는 저장소 및 엔티티를 찾습니다.
1. MySQL DB에 연결합니다.
클라우드 기반의 Adobe Commerce의 경우 먼저 SSH를 사용하여 환경에 연결해야 합니다.
1. 현재 항목 확인 `auto_increment` 다음 쿼리를 사용하는 엔티티 시퀀스 테이블의 값:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

ID=1인 저장소에서 주문에 대한 자동 증분을 확인하는 경우 테이블 이름은 &#39;sequence_order_1&#39;입니다.

의 값이 `auto_increment` 열은 &#39;1234&#39;이며 다음 순서는 `ID=1` 에는 &#39;#100001234&#39; ID가 있습니다.

## 증분 ID를 변경하려면 엔터티를 업데이트하십시오

다음 쿼리를 사용하여 엔티티를 업데이트합니다.

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
중요 사항: 새 증분 값은 현재 값보다 커야 합니다.

다음 쿼리를 실행한 후:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

다음 주문은 `ID=1` 에는 &#39;#100002000&#39; ID가 있습니다.

## 클라우드 프로덕션 환경에 대한 추가적인 권장 단계

를 실행하기 전에 `ALTER TABLE` 클라우드 인프라에서 Adobe Commerce의 프로덕션 환경에 대해 쿼리하려면 다음 단계를 수행하는 것이 좋습니다.

- 스테이징 환경에서 증분 ID를 변경하는 전체 절차를 테스트합니다
- [DB 백업 만들기] 오류가 발생한 경우 프로덕션 DB를 복원하기 위해

<!-- Link Definitions -->

[PayPal 게이트웨이가 요청을 거부했습니다. 송장 문제가 중복되었습니다.]: https://support.magento.com/hc/en-us/articles/115002457473
[DB 백업 만들기]: https://support.magento.com/hc/en-us/articles/360003254334
[지원되는 버전]
