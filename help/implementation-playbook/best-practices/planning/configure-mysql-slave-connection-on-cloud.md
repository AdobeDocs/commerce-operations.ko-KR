---
title: MySQL 슬레이브 연결을 구성하는 우수 사례
description: 클라우드 인프라에 배포된 Adobe Commerce 사이트에 대해 MySQL 슬레이브 연결을 구성하는 방법에 대해 알아봅니다.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# MySQL 슬레이브 연결을 구성하는 우수 사례

>[!NOTE]
>
>이 문서에는 인종 차별주의자, 성차별주의자 또는 억압적인 것으로 인식되며 독자로 하여금 상처 받거나, 트라우마를 받거나, 환영받지 못하게 만들 수 있는 업계 표준 소프트웨어 용어가 포함되어 있습니다. Adobe이 코드, 설명서 및 사용자 경험에서 이러한 용어를 제거하고 있습니다.

Cloud Infrastructure Pro 아키텍처에 배포된 Adobe Commerce Adobe 사이트의 경우 기본적으로 데이터베이스에 대해 MYSQL 슬레이브 연결을 활성화하는 것이 좋습니다.

Adobe Commerce은 여러 데이터베이스를 비동기식으로 읽을 수 있습니다. MYSQL 슬레이브 연결을 활성화하면 Adobe Commerce은 데이터베이스에 대한 읽기 전용 연결을 사용하여 마스터가 아닌 노드에서 읽기 전용 트래픽을 수신합니다. 한 노드만 읽기/쓰기 트래픽을 처리할 때 로드 밸런싱을 통해 성능이 향상됩니다.

## 영향을 받는 버전

클라우드 인프라의 Adobe Commerce, Pro 아키텍처

## MySQL 슬레이브 연결 구성

클라우드 인프라의 Adobe Commerce에서 다음을 설정하여 MYSQL 슬레이브 연결에 대한 기본 구성을 재정의할 수 있습니다. [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 변수를 채우는 방법에 따라 페이지를 순서대로 표시합니다. 데이터베이스에 대한 읽기 전용 연결을 자동으로 사용하려면 이 변수를 true로 설정하십시오.

**MySQL 슬레이브 연결을 활성화하려면**:

1. 로컬 워크스테이션에서 프로젝트 디렉터리로 변경합니다.

1. 다음에서 `.magento.env.yaml` 파일, 설정 `MYSQL_USE_SLAVE_CONNECTION` true로 설정합니다.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 커밋: `.magento.env.yaml` 파일을 변경하고 원격 환경에 푸시합니다.

   배포가 성공적으로 완료되면 클라우드 환경에 대해 MySQL 슬레이브 연결이 활성화됩니다.

를 사용하여 기존 Commerce 구성을 재정의하여 클라우드 환경을 사용자 지정하는 방법에 대해 자세히 알아보십시오. [환경 변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 다음에서 _Adobe Commerce on cloud infrastructure 안내서_.

## 추가 정보

- [클라우드 인프라에서 Adobe Commerce의 MySQL 고부하 병목 현상](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](database-on-cloud.md)
