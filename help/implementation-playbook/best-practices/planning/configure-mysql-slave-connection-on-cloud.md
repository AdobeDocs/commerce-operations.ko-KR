---
title: MySQL 슬레이브 연결 구성 우수 사례
description: 클라우드 인프라에 배포된 Adobe Commerce 사이트에 대한 MySQL 슬레이브 연결을 구성하는 방법을 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# MySQL 슬레이브 연결 구성 우수 사례

>[!NOTE]
>
>이 문서에는 산업 표준 소프트웨어 용어들이 포함되어 있으며, 일부는 인종차별적이거나 성차별적이거나 억압적일 수 있으며 독자가 상처 받거나, 외상을 입거나, 환영받지 못할 수도 있습니다. Adobe은 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하려고 노력하고 있습니다.

클라우드 인프라 Pro 아키텍처에 배포된 Adobe Commerce 사이트의 경우 기본적으로 데이터베이스에 대해 MYSQL 슬레이브 연결을 활성화하는 것이 좋습니다.

Adobe Commerce은 여러 데이터베이스를 비동기식으로 읽을 수 있습니다. MYSQL 슬레이브 연결을 활성화하면 Adobe Commerce에서 데이터베이스에 대한 읽기 전용 연결을 사용하여 비마스터 노드에서 읽기 전용 트래픽을 받습니다. 읽기-쓰기 트래픽을 처리하는 노드가 한 개만 있을 때 로드 밸런싱을 통해 성능이 향상됩니다.

## 영향을 받는 버전

Adobe Commerce on cloud infrastructure, Pro 아키텍처

## MySQL 슬레이브 연결 구성

클라우드 기반의 Adobe Commerce에서 다음을 설정하여 MYSQL 슬레이브 연결에 대한 기본 구성을 무시할 수 있습니다 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 변수를 채우는 방법을 설명합니다. 데이터베이스에 대한 읽기 전용 연결을 자동으로 사용하려면 이 변수를 true로 설정합니다.

**MySQL 슬레이브 연결을 사용하려면**:

1. 로컬 워크스테이션에서 프로젝트 디렉토리로 변경합니다.

1. 에서 `.magento.env.yaml` 파일에서 `MYSQL_USE_SLAVE_CONNECTION` true로 설정합니다.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 커밋 `.magento.env.yaml` 파일이 변경되고 원격 환경에 푸시됩니다.

   배포가 성공적으로 완료되면 클라우드 환경에 대해 MySQL 슬레이브 연결이 활성화됩니다.

기존 상거래 구성을 재정의하여 클라우드 환경 사용자 지정에 대해 자세히 알아봅니다. [환경 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 에서 _Adobe Commerce on cloud 인프라 안내서_.

## 추가 정보

- [클라우드 인프라에서 Adobe Commerce의 MySQL 고로드 병목 현상](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [클라우드 인프라 기반의 Adobe Commerce을 위한 데이터베이스 우수 사례](database-on-cloud.md)
