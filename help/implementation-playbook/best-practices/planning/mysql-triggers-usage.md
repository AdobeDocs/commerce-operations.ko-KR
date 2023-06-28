---
title: MySQL 트리거 사용
description: Adobe Commerce에서 MySQL 트리거를 효과적으로 사용하는 방법을 알아봅니다.
role: Developer
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# MySQL 트리거 사용 모범 사례

이 문서에서는 MySQL 트리거를 사용할 때 성능 문제를 방지하는 방법에 대해 설명합니다. 트리거는 변경 사항을 감사 테이블에 기록하는 데 사용됩니다.

## 영향을 받는 제품 및 버전

- Adobe Commerce 온-프레미스
- 클라우드 인프라의 Adobe Commerce

>[!WARNING]
>
>클라우드 프로젝트의 Adobe Commerce의 경우 프로덕션 환경에 대한 구성을 변경하기 전에 항상 스테이징 환경에서 구성 변경 사항을 테스트하십시오.

## 성능 영향 이해

트리거는 MySQL이 트리거를 미리 컴파일하지 않는다는 것을 의미하는 코드로 해석됩니다.

쿼리의 트랜잭션 공간에 후킹하는 트리거는 테이블과 함께 수행되는 각 쿼리에 대해 파서 및 인터프리터에 오버헤드를 추가합니다. 트리거는 원래 쿼리와 동일한 트랜잭션 공간을 공유하며, 해당 쿼리가 테이블에서 잠금에 대해 경쟁하는 동안 트리거는 독립적으로 다른 테이블에서 잠금에 대해 경쟁합니다.

이 추가 오버헤드는 많은 트리거를 사용하는 경우 사이트의 사이트 성능에 부정적인 영향을 줄 수 있습니다.

>[!WARNING]
>
>Adobe Commerce은 사용자 지정 트리거로 인해 향후 Adobe Commerce 버전과 호환되지 않을 수 있으므로 Adobe Commerce 데이터베이스에서 모든 사용자 지정 트리거를 지원하지 않습니다. 모범 사례에 대해서는 다음을 참조하십시오. [일반 MySQL 지침](../../../installation/prerequisites/database/mysql.md) Adobe Commerce 설명서에서 확인할 수 있습니다.

## 효과적인 트리거 사용

트리거를 사용할 때 성능 문제를 방지하려면 다음 지침을 따르십시오.

- 트리거가 실행될 때 일부 데이터를 작성하는 사용자 지정 트리거가 있는 경우 이 논리를 이동하여 감사 테이블에 직접 작성합니다. 예를 들어, 트리거를 만들려는 쿼리 뒤에 애플리케이션 코드에 쿼리를 추가하여 추가합니다.
- 기존 사용자 지정 트리거를 검토하고 이를 제거하여 애플리케이션 측에서 테이블에 직접 작성하는 것이 좋습니다. 다음을 사용하여 데이터베이스에서 기존 트리거 확인 [`SHOW TRIGGERS` SQL 문](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 추가 지원, 질문 또는 우려 사항 [Adobe Commerce 지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 추가 정보

- [MySQL 사전 요구 사항](../../../installation/prerequisites/database/mysql.md)
- [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](database-on-cloud.md)
