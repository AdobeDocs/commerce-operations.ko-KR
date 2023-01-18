---
title: MySQL 슬레이브 연결 구성 우수 사례
description: 클라우드 인프라에 배포된 Adobe Commerce 사이트에 대한 MySQL 슬레이브 연결을 구성하는 방법을 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 0866272e02a7a223d35e14842bfb42a827e0468d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# MySQL 슬레이브 연결 구성 우수 사례

>!![NOTE]
본 문서는 일부 독자가 인종차별적이거나 성차별적이거나 억압적인 상태를 보일 수 있는 업계 표준 소프트웨어 용어를 포함하고 있으며 독자가 상처받거나, 정신적 충격적이거나, 환영받지 못할 수도 있습니다. Adobe은 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하려고 노력하고 있습니다.

클라우드 인프라 Pro 아키텍처에 배포된 Adobe Commerce 사이트의 경우 기본적으로 데이터베이스에 대해 MYSQL 슬레이브 연결을 활성화하는 것이 좋습니다.

Adobe Commerce은 여러 데이터베이스를 비동기식으로 읽을 수 있습니다.  MYSQL 슬레이브 연결을 활성화하면 Adobe Commerce에서 데이터베이스에 대한 읽기 전용 연결을 사용하여 비마스터 노드에서 읽기 전용 트래픽을 받습니다. 이렇게 하면 한 노드만 읽기-쓰기 트래픽을 처리해야 하므로 로드 밸런싱을 통해 성능이 향상됩니다.

## 영향을 받는 버전

Adobe Commerce on cloud infrastructure, Pro 아키텍처

## MySQL 슬레이브 연결 구성

MYSQL 슬레이브 연결에 대한 구성은 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) Adobe Commerce의 클라우드 인프라 환경 구성 파일에 변수 배포, `.magento.env.yaml`. 이 변수를 로 설정 `true` 을 눌러 연결을 활성화합니다.

MySQL 슬레이브 연결을 사용하려면

1. 편집 `.magento.env.yaml` 파일 및 `MYSQL_USE_SLAVE_CONNECTION` 이 활성화되어 있습니다.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 변경 사항을 커밋한 다음 환경 분기에 푸시하여 업데이트를 배포합니다.

   배포가 성공적으로 완료되면 클라우드 인프라에서 MySQL 슬레이브 연결이 활성화됩니다.

## 추가 정보

- [환경 변수](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [클라우드 인프라에서 Adobe Commerce의 MySQL 고로드 병목 현상](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [클라우드 인프라 기반의 Adobe Commerce을 위한 데이터베이스 우수 사례](database-on-cloud.md)
