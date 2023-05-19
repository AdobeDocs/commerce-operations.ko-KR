---
title: 검색 엔진 구성
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 배포에 대한 검색 엔진을 구성합니다.
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 검색 엔진 구성

이 섹션에서는 Adobe Commerce 및 Magento Open Source의 온-프레미스 배포로 Elasticsearch 또는 OpenSearch를 테스트하도록 선택해야 하는 최소 설정에 대해 설명합니다.

>[!TIP]
>
>버전 2.4.4 및 2.4.3-p2에서 모든 필드에 레이블이 지정됨 **Elasticsearch** OpenSearch에도 적용됩니다.
>버전 2.4.6에서 Elasticsearch 8.x에 대한 지원이 도입되었을 때 Elasticsearch 구성과 OpenSearch 구성을 구별하기 위해 새 레이블이 만들어졌습니다.

검색 엔진 구성에 대한 자세한 내용은 [사용 안내서](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 책임자로부터 검색 엔진 구성

>[!TIP]
>
>새 검색 엔진 버전으로 업그레이드하는 방법에 대한 지침은 [업그레이드 사전 요구 사항](../../upgrade/prepare/prerequisites.md).

Elasticsearch 또는 OpenSearch를 사용하도록 시스템을 구성하려면 다음을 수행합니다.

1. 관리자로 관리자에 로그인합니다.
1. 클릭 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 다음에서 **[!UICONTROL Search Engine]** 목록에서 검색 엔진의 해당 버전을 선택합니다.

   다음 표에는 Commerce와의 연결을 구성하고 테스트하는 데 필요한 옵션이 나열되어 있습니다. 검색 엔진의 서버 설정을 변경하지 않은 경우 기본값이 작동합니다. 다음 단계로 건너뜁니다.

   | 옵션 | 설명 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Elasticsearch 또는 OpenSearch를 실행하는 컴퓨터의 정규화된 호스트 이름 또는 IP 주소를 입력합니다.<br>클라우드 인프라의 Adobe Commerce: 통합 시스템에서 이 가치를 얻으십시오. |
   | **[!UICONTROL Server Port]** | 웹 서버 프록시 포트를 입력합니다. 기본값은 9200입니다.<br>클라우드 인프라의 Adobe Commerce: 통합 시스템에서 이 가치를 얻으십시오. |
   | **[!UICONTROL Index Prefix]** | 검색 엔진 색인 접두사를 입력합니다. 둘 이상의 상거래 설치(스테이징 및 프로덕션 환경)에 단일 인스턴스를 사용하는 경우 각 설치에 대해 고유한 접두사를 지정해야 합니다. 그렇지 않으면 기본 접두사 magento2를 사용할 수 있습니다. |
   | **[!UICONTROL Enable HTTP Auth]** | 클릭 **[!UICONTROL Yes]** 검색 엔진 서버에 대한 인증을 사용하도록 설정한 경우에만 해당합니다. 그럴 경우 제공된 필드에 사용자 이름과 암호를 입력합니다. |
   | **[!UICONTROL Server Timeout]** | Elasticsearch 또는 OpenSearch 서버에 대한 연결을 설정할 때 대기할 시간(초)을 입력합니다. |

1. 클릭 **[!UICONTROL Test Connection]**.

   샘플 응답:

   ![성공](../../assets/configuration/elastic_test-success.png)

   다음 작업을 사용하여 계속:

   - [검색 엔진에 대한 Apache 구성](../../installation/prerequisites/search-engine/configure-apache.md)
   - [검색 엔진에 대한 nginx 구성](../../installation/prerequisites/search-engine/configure-nginx.md)

   또는 다음을 볼 수 있습니다.

   ![실패](../../assets/configuration/elastic_test-fail.png)

이 경우 다음을 시도해 보십시오.

- 검색 엔진 서버가 실행 중인지 확인하십시오.
- 서버가 Commerce와 다른 호스트에 있는 경우 Commerce 서버에 로그인하고 검색 엔진 호스트를 ping합니다. 네트워크 연결 문제를 해결하고 연결을 다시 테스트하십시오.
- Elasticsearch 또는 OpenSearch를 시작한 명령 창에서 스택 추적 및 예외를 검사합니다. 계속하려면 이러한 문제를 해결해야 합니다. 특히 를 사용하여 사용자로 검색 엔진을 시작했는지 확인하십시오. `root` 권한.
- 다음을 확인합니다. [UNIX 방화벽 및 SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 둘 다 비활성화되어 있거나 검색 엔진과 상거래 가 서로 통신할 수 있도록 규칙을 설정합니다.
- 값 확인 **[!UICONTROL Server Hostname]** 필드. 서버를 사용할 수 있는지 확인합니다. 대신 서버의 IP 주소를 시도할 수 있습니다.
- 사용 `netstat -an | grep <listen-port>` 에 지정된 포트를 확인하는 명령 **[!UICONTROL Server Port]** 다른 프로세스에서 필드를 사용하고 있지 않습니다.

   예를 들어 검색 엔진이 기본 포트에서 실행 중인지 확인하려면 다음 명령을 사용합니다.

   ```bash
   netstat -an | grep 9200
   ```

   포트 9200에서 실행 중인 경우 다음과 유사하게 표시됩니다.

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 카탈로그 검색 색인 재지정 및 전체 페이지 캐시 새로 고침

검색 엔진 구성을 변경한 후에는 카탈로그 검색 색인을 다시 색인화하고 관리 또는 명령줄을 사용하여 전체 페이지 캐시를 새로 고쳐야 합니다.

관리자를 사용하여 캐시를 새로 고침하려면 다음을 수행하십시오.

1. 관리에서 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 옆에 있는 확인란을 선택합니다. **[!UICONTROL Page Cache]**.
1. 다음에서 **[!UICONTROL Actions]** 오른쪽 상단에 있는 을(를) 클릭하여 **새로 고침**.

   ![캐시 관리](../../assets/configuration/refresh-cache.png)

명령줄을 사용하여 캐시를 정리하려면 다음을 수행하십시오. [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

명령줄을 사용하여 색인 재지정하기

1. Commerce 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 다음 명령 중 하나를 입력합니다.

   다음 명령을 입력하여 카탈로그 검색 색인만 다시 색인화합니다.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   모든 인덱서를 다시 인덱싱하려면 다음 명령을 입력합니다.

   ```bash
   bin/magento indexer:reindex
   ```

1. 리인덱싱이 완료될 때까지 기다립니다.

   >[!INFO]
   >
   >인덱서는 캐시와 달리 cron 작업에 의해 업데이트됩니다. 다음을 확인하십시오. [cron이 활성화되었습니다.](../cli/configure-cron-jobs.md) 검색 엔진 사용을 시작하기 전에
