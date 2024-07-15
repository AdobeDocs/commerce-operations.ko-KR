---
title: MySQL 구성 모범 사례
description: MySQL 트리거 및 슬레이브 연결이 Commerce 사이트 성능에 어떻게 영향을 주는지 그리고 이를 효과적으로 사용하는 방법에 대해 알아봅니다.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# MySQL 구성 모범 사례

>[!NOTE]
>
>이 주제에는 인종 차별주의자, 성차별주의자 또는 억압적인 것으로 인식되며 독자로 하여금 상처받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 포함되어 있습니다. Adobe이 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.

## 트리거

이 문서에서는 MySQL 트리거를 사용할 때 성능 문제를 방지하는 방법에 대해 설명합니다. 트리거는 변경 사항을 감사 테이블에 기록하는 데 사용됩니다.

### 영향을 받는 제품 및 버전

- Adobe Commerce 온-프레미스
- 클라우드 인프라의 Adobe Commerce

>[!WARNING]
>
>클라우드 프로젝트의 Adobe Commerce의 경우 프로덕션 환경에 대한 구성을 변경하기 전에 항상 스테이징 환경에서 구성 변경 사항을 테스트하십시오.

### 성능에 미치는 영향

트리거는 MySQL이 트리거를 미리 컴파일하지 않는다는 것을 의미하는 코드로 해석됩니다.

쿼리의 트랜잭션 공간에 후킹하는 트리거는 테이블과 함께 수행되는 각 쿼리에 대해 파서 및 인터프리터에 오버헤드를 추가합니다. 트리거는 원래 쿼리와 동일한 트랜잭션 공간을 공유하며, 해당 쿼리가 테이블에서 잠금에 대해 경쟁하는 동안 트리거는 독립적으로 다른 테이블에서 잠금에 대해 경쟁합니다.

이 추가 오버헤드는 많은 트리거를 사용하는 경우 사이트의 사이트 성능에 부정적인 영향을 줄 수 있습니다.

>[!WARNING]
>
>Adobe Commerce은 사용자 지정 트리거로 인해 향후 Adobe Commerce 버전과 호환되지 않을 수 있으므로 Adobe Commerce 데이터베이스에서 모든 사용자 지정 트리거를 지원하지 않습니다. 모범 사례는 Adobe Commerce 설명서에서 [일반 MySQL 지침](../../../installation/prerequisites/database/mysql.md)을 참조하십시오.

### 효과적인 사용

트리거를 사용할 때 성능 문제를 방지하려면 다음 지침을 따르십시오.

- 트리거가 실행될 때 일부 데이터를 작성하는 사용자 지정 트리거가 있는 경우 이 논리를 이동하여 감사 테이블에 직접 작성합니다. 예를 들어, 트리거를 만들려는 쿼리 뒤에 애플리케이션 코드에 쿼리를 추가하여 추가합니다.
- 기존 사용자 지정 트리거를 검토하고 이를 제거하여 애플리케이션 측에서 테이블에 직접 작성하는 것이 좋습니다. [`SHOW TRIGGERS` SQL 문](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html)을(를) 사용하여 데이터베이스에서 기존 트리거를 확인합니다.
- 추가 지원, 질문 또는 우려 사항은 [Adobe Commerce 지원 티켓을 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket)하십시오.

## 슬레이브 연결

Adobe Commerce은 여러 데이터베이스를 비동기식으로 읽을 수 있습니다. Cloud Infrastructure Pro 아키텍처에 배포된 Commerce 사이트의 MySQL 데이터베이스에 대한 로드가 높을 것으로 예상되면 Adobe은 MYSQL 슬레이브 연결을 활성화할 것을 권장합니다.

MYSQL 슬레이브 연결을 활성화하면 Adobe Commerce은 데이터베이스에 대한 읽기 전용 연결을 사용하여 마스터가 아닌 노드에서 읽기 전용 트래픽을 수신합니다. 한 노드만 읽기/쓰기 트래픽을 처리할 때 로드 밸런싱을 통해 성능이 향상됩니다.

### 영향을 받는 버전

클라우드 인프라의 Adobe Commerce, Pro 아키텍처 전용

### 구성

클라우드 인프라의 Adobe Commerce에서 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 변수를 설정하여 MYSQL 슬레이브 연결에 대한 기본 구성을 재정의할 수 있습니다. 데이터베이스에 대한 읽기 전용 연결을 자동으로 사용하려면 이 변수를 `true`(으)로 설정하십시오.

**MySQL 슬레이브 연결을 사용하도록 설정하려면**:

1. 로컬 워크스테이션에서 프로젝트 디렉터리로 변경합니다.

1. `.magento.env.yaml` 파일에서 `MYSQL_USE_SLAVE_CONNECTION`을(를) true로 설정합니다.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. `.magento.env.yaml` 파일 변경 내용을 커밋하고 원격 환경에 푸시합니다.

   배포가 성공적으로 완료되면 클라우드 환경에 대해 MySQL 슬레이브 연결이 활성화됩니다.
