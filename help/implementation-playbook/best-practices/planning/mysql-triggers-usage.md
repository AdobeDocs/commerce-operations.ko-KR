---
title: MySQL 트리거 사용
description: Adobe Commerce에서 MySQL 트리거를 효과적으로 사용하는 방법을 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# MySQL 트리거 사용에 대한 우수 사례

이 문서에서는 MySQL 트리거를 사용할 때 성능 문제를 방지하는 방법을 설명합니다. 트리거는 변경 사항을 감사 테이블에 기록하는 데 사용됩니다.

## 영향을 받는 제품 및 버전

- Adobe Commerce 온-프레미스
- Adobe Commerce on cloud 인프라

>[!WARNING]
>
>클라우드 프로젝트의 Adobe Commerce의 경우 프로덕션 환경에 대한 구성을 변경하기 전에 항상 스테이징 환경에서 구성 변경 사항을 테스트하십시오.

## 성능에 미치는 영향 이해

트리거는 MySQL이 트리거를 미리 컴파일하지 않음을 나타내는 코드로 해석됩니다.

쿼리의 트랜잭션 공간으로 후킹하고, 트리거로 테이블의 각 쿼리에 대해 파서와 인터프리터에 오버헤드를 추가합니다. 트리거는 원래 쿼리와 동일한 트랜잭션 공간을 공유하며, 이러한 쿼리는 테이블의 잠금을 위해 경합하는 반면 트리거는 독립적으로 다른 테이블의 잠금을 위해 경쟁합니다.

많은 트리거를 사용하는 경우 이러한 추가 오버헤드가 사이트의 사이트 성능에 부정적인 영향을 줄 수 있습니다.

>[!WARNING]
>
>Adobe Commerce은 사용자 지정 트리거로 인해 향후 Adobe Commerce 버전과 호환되지 않는 문제가 발생할 수 있으므로 Adobe Commerce 데이터베이스에서 사용자 지정 트리거를 지원하지 않습니다. 모범 사례에 대해서는 [일반 MySQL 지침](../../../installation/prerequisites/database/mysql.md) ( Adobe Commerce 설명서)를 참조하십시오.

## 효과적으로 트리거 사용

트리거를 사용할 때 성능 문제가 발생하지 않도록 하려면 다음 지침을 따르십시오.

- 트리거가 실행될 때 일부 데이터를 쓰는 사용자 지정 트리거가 있는 경우 이 논리를 이동하여 대신 감사 테이블에 직접 작성합니다. 예를 들어 애플리케이션 코드에서 쿼리를 추가하여 트리거를 생성하려는 쿼리 다음에 을 추가합니다.
- 기존 사용자 지정 트리거를 검토하고 이를 제거하고 애플리케이션 측에서 테이블에 직접 기록하는 것이 좋습니다. 를 사용하여 데이터베이스의 기존 트리거를 확인합니다. [`SHOW TRIGGERS` SQL 문](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 추가 지원, 질문 또는 우려 사항은 [Adobe Commerce 지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 추가 정보

- [MySQL 사전 요구 사항](../../../installation/prerequisites/database/mysql.md)
- [클라우드 인프라 기반의 Adobe Commerce을 위한 데이터베이스 우수 사례](database-on-cloud.md)
