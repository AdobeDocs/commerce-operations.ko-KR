---
title: 검색 엔진 구성
description: Adobe Commerce 및 Magento Open Source을 사용하여 검색 엔진을 구성합니다.
source-git-commit: 66681f06c15907a5d25e71005c27785f0745ed63
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# 검색 엔진 구성

이 섹션에서는 Adobe Commerce 및 Magento Open Source을 사용하여 Elasticsearch 또는 OpenSearch를 테스트하도록 선택해야 하는 최소 설정을 설명합니다. 버전 2.4.4 및 2.4.3-p2의 경우, 모든 필드에 레이블이 지정됨 **Elasticsearch** OpenSearch에도 적용됩니다.

검색 엔진 구성에 대한 자세한 내용은 [사용 안내서](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 관리자에서 검색 엔진 구성

Elasticsearch 또는 OpenSearch를 사용하도록 시스템을 구성하려면 다음을 수행하십시오.

1. 관리자로 관리자에게 로그인합니다.
1. 클릭 **스토어** > 설정 > **구성** > **카탈로그** > **카탈로그** > **카탈로그 검색**.
1. 에서 **검색 엔진** 검색 엔진의 해당 버전을 선택합니다. OpenSearch를 사용하는 경우에는 Elasticsearch7을 선택해야 합니다.

   다음 표에는 Commerce와의 연결을 구성하고 테스트하는 데 필요한 구성 옵션이 나와 있습니다.
검색 엔진의 서버 설정을 변경하지 않으면 기본값이 작동해야 합니다. 다음 단계로 건너뜁니다.

   | 옵션 | 설명 |
   |--- |--- |
   | **Elasticsearch 서버 호스트 이름** | Elasticsearch 또는 OpenSearch를 실행하는 컴퓨터의 정규화된 호스트 이름 또는 IP 주소를 입력합니다.<br>Adobe Commerce on cloud 인프라: 통합 시스템에서 이 값을 가져옵니다. |
   | **Elasticsearch 서버 포트** | 웹 서버 프록시 포트를 입력합니다. 기본값은 9200입니다<br>Adobe Commerce on cloud 인프라: 통합 시스템에서 이 값을 가져옵니다. |
   | **Elasticsearch 인덱스 접두사** | 검색 엔진 인덱스 접두사를 입력합니다. 둘 이상의 상거래 설치(스테이징 및 프로덕션 환경)에 대해 단일 인스턴스를 사용하는 경우 각 설치에 고유한 접두사를 지정해야 합니다. 그렇지 않으면 기본 접두사 magento2를 사용할 수 있습니다. |
   | **Elasticsearch HTTP 인증 활성화** | 클릭 **예** 검색 엔진 서버에 대해 인증을 사용하도록 설정한 경우에만 해당됩니다. 있는 경우 제공된 필드에 사용자 이름과 암호를 입력합니다. |

1. 클릭 **연결 테스트**.

   샘플 응답:

   ![성공](../../assets/configuration/elastic_test-success.png)

   계속:

   - [검색 엔진에 대한 Apache 구성](../../installation/prerequisites/search-engine/configure-apache.md)
   - [검색 엔진에 대한 ninx 구성](../../installation/prerequisites/search-engine/configure-nginx.md)

   또는 다음을 볼 수 있습니다.

   ![실패](../../assets/configuration/elastic_test-fail.png)

그럴 경우 다음을 시도해 보십시오.

- 검색 엔진 서버가 실행 중인지 확인합니다.
- 서버가 상거래 호스트와 다른 호스트에 있는 경우 상거래 서버에 로그인하고 검색 엔진 호스트를 ping합니다. 네트워크 연결 문제를 해결하고 연결을 다시 테스트합니다.
- Elasticsearch 또는 OpenSearch를 시작한 명령 창에서 스택 추적 및 예외를 검사합니다. 계속하기 전에 이러한 문제를 해결해야 합니다. 특히 을 사용하는 사용자로 검색 엔진을 시작했는지 확인합니다. `root` 권한.
- 확인 [UNIX 방화벽 및 SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 둘 다 비활성화되어 있거나, 검색 엔진과 상거래가 서로 통신할 수 있도록 하는 규칙을 설정하십시오.
- 의 값을 확인합니다 **Elasticsearch 서버 호스트 이름** 필드. 서버가 사용 가능한지 확인하십시오. 대신 서버의 IP 주소를 시도할 수 있습니다.
- 를 사용하십시오 `netstat -an | grep <listen-port>` 명령을 사용하여 **Elasticsearch 서버 포트** 다른 프로세스에서 필드를 사용하고 있지 않습니다.

   예를 들어 검색 엔진이 기본 포트에서 실행 중인지 확인하려면 다음 명령을 사용하십시오.

   ```bash
   netstat -an | grep 9200
   ```

   포트 9200에서 실행 중인 경우 다음과 유사하게 표시됩니다.

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 카탈로그 검색을 다시 인덱싱하고 전체 페이지 캐시를 새로 고치는 중

검색 엔진 구성을 변경한 후 카탈로그 검색 색인을 다시 색인화하고 관리자 또는 명령줄을 사용하여 전체 페이지 캐시를 새로 고쳐야 합니다.

관리자를 사용하여 캐시를 새로 고치려면:

1. 관리자에서 **시스템** > **캐시 관리**.
1. 옆에 있는 확인란을 선택합니다 **페이지 캐시**.
1. 에서 **작업** 오른쪽 상단의 목록을 클릭한 다음 **새로 고침**.

   ![캐시 관리](../../assets/configuration/refresh-cache.png)

명령줄을 사용하여 캐시를 지우려면 [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

명령줄을 사용하여 다시 색인화하려면

1. Commerce 서버에 로그인하거나 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 다음 명령을 입력합니다.

   카탈로그 검색 색인만 다시 색인화하려면 다음 명령을 입력합니다.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   모든 인덱서를 다시 색인화하려면 다음 명령을 입력합니다.

   ```bash
   bin/magento indexer:reindex
   ```

1. 다시 색인화가 완료될 때까지 기다립니다.

   >[!INFO]
   >
   >캐시와 달리 인덱서는 크론 작업에 의해 업데이트됩니다. 확인 [cron이 활성화되어 있습니다.](../cli/configure-cron-jobs.md) 검색 엔진 사용을 시작하기 전에

