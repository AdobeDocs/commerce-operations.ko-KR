---
title: 검색 엔진 구성
description: Adobe Commerce의 온-프레미스 배포에 대한 검색 엔진을 구성합니다.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 검색 엔진 구성

이 섹션에서는 Adobe Commerce의 온-프레미스 배포를 사용하여 Elasticsearch 또는 OpenSearch를 테스트하도록 선택해야 하는 최소 설정에 대해 설명합니다.

>[!TIP]
>
>버전 2.4.4 및 2.4.3-p2에서는 **Elasticsearch** 레이블이 지정된 모든 필드가 OpenSearch에도 적용됩니다.
>&#x200B;>Elasticsearch 8.x에 대한 지원이 버전 2.4.6에 도입되면 Elasticsearch 구성과 OpenSearch 구성을 구별하기 위해 새 레이블이 생성되었습니다.

검색 엔진 구성에 대한 자세한 내용은 [사용 안내서](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html)를 참조하세요.

## 책임자로부터 검색 엔진 구성

>[!TIP]
>
>새 검색 엔진 버전으로 업그레이드하는 방법에 대한 지침은 [업그레이드 필수 구성 요소](../../upgrade/prepare/prerequisites.md)를 참조하십시오.

Elasticsearch 또는 OpenSearch를 사용하도록 시스템을 구성하려면 다음 작업을 수행하십시오.

1. 관리자로 관리자에 로그인합니다.
1. **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Search Engine]** 목록에서 검색 엔진의 해당 버전을 선택합니다.

   다음 표에는 Commerce과의 연결을 구성하고 테스트하는 데 필요한 옵션이 나열되어 있습니다. 검색 엔진의 서버 설정을 변경하지 않은 경우 기본값이 작동합니다. 다음 단계로 건너뜁니다.

   | 옵션 | 설명 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Elasticsearch 또는 OpenSearch를 실행하는 컴퓨터의 정규화된 호스트 이름 또는 IP 주소를 입력합니다.클라우드 인프라의 <br>Adobe Commerce: 통합 시스템에서 이 값을 가져옵니다. |
   | **[!UICONTROL Server Port]** | 웹 서버 프록시 포트를 입력합니다. 기본값은 클라우드 인프라의 9200<br>Adobe Commerce입니다. 통합 시스템에서 이 값을 가져옵니다. |
   | **[!UICONTROL Index Prefix]** | 검색 엔진 색인 접두사를 입력합니다. 둘 이상의 Commerce 설치(스테이징 및 프로덕션 환경)에 단일 인스턴스를 사용하는 경우 각 설치에 대해 고유한 접두사를 지정해야 합니다. 그렇지 않으면 기본 접두사 magento2를 사용할 수 있습니다. |
   | **[!UICONTROL Enable HTTP Auth]** | 검색 엔진 서버에 대한 인증을 사용하도록 설정한 경우에만 **[!UICONTROL Yes]**&#x200B;을(를) 클릭합니다. 그럴 경우 제공된 필드에 사용자 이름과 암호를 입력합니다. |
   | **[!UICONTROL Server Timeout]** | Elasticsearch 또는 OpenSearch 서버에 대한 연결을 설정할 때 대기할 시간(초)을 입력합니다. |

1. **[!UICONTROL Test Connection]**&#x200B;을(를) 클릭합니다.

   샘플 응답:

   ![성공](../../assets/configuration/elastic_test-success.png)

   다음 작업을 사용하여 계속:

   - [검색 엔진에 대한 Apache 구성](../../installation/prerequisites/search-engine/configure-apache.md)
   - [검색 엔진에 대한 nginx 구성](../../installation/prerequisites/search-engine/configure-nginx.md)

   또는 다음을 볼 수 있습니다.

   ![실패](../../assets/configuration/elastic_test-fail.png)

이 경우 다음을 시도해 보십시오.

- 검색 엔진 서버가 실행 중인지 확인하십시오.
- 서버가 Commerce과 다른 호스트에 있는 경우 Commerce 서버에 로그인하고 검색 엔진 호스트에 ping을 실행합니다. 네트워크 연결 문제를 해결하고 연결을 다시 테스트하십시오.
- Elasticsearch 또는 OpenSearch를 시작한 명령 창에서 스택 추적 및 예외를 검사합니다. 계속하려면 이러한 문제를 해결해야 합니다. 특히 `root` 권한을 가진 사용자로 검색 엔진을 시작했는지 확인하십시오.
- [UNIX 방화벽과 SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux)가 모두 사용하지 않도록 설정되어 있는지 확인하거나 검색 엔진과 Commerce이 서로 통신할 수 있도록 규칙을 설정합니다.
- **[!UICONTROL Server Hostname]** 필드의 값을 확인합니다. 서버를 사용할 수 있는지 확인합니다. 대신 서버의 IP 주소를 시도할 수 있습니다.
- `netstat -an | grep <listen-port>` 명령을 사용하여 **[!UICONTROL Server Port]** 필드에 지정된 포트를 다른 프로세스에서 사용하고 있지 않은지 확인하십시오.

  예를 들어 검색 엔진이 기본 포트에서 실행 중인지 확인하려면 다음 명령을 사용합니다.

  ```bash
  netstat -an | grep 9200
  ```

  포트 9200에서 실행 중인 경우 다음과 유사하게 표시됩니다.

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## 카탈로그 검색 색인 재지정 및 전체 페이지 캐시 새로 고침

검색 엔진 구성을 변경한 후에는 카탈로그 검색 색인을 다시 색인화하고 관리 또는 명령줄을 사용하여 전체 페이지 캐시를 새로 고쳐야 합니다.

관리자를 사용하여 캐시를 새로 고침하려면 다음을 수행하십시오.

1. 관리자에서 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Page Cache]** 옆에 있는 확인란을 선택하십시오.
1. 오른쪽 상단의 **[!UICONTROL Actions]** 목록에서 **새로 고침**&#x200B;을 클릭합니다.

   ![캐시 관리](../../assets/configuration/refresh-cache.png)

명령줄을 사용하여 캐시를 정리하려면: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

명령줄을 사용하여 색인 재지정하기

1. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 Commerce 서버에 로그인하거나 (으)로 전환합니다.
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
   >인덱서는 캐시와 달리 cron 작업에 의해 업데이트됩니다. 검색 엔진 사용을 시작하기 전에 [cron이 활성화되었는지](../cli/configure-cron-jobs.md)확인하십시오.
