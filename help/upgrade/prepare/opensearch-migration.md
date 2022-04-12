---
title: Elasticsearch에서 OpenSearch로 마이그레이션
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 사용되는 검색 엔진을 교체하는 방법에 대해 알아봅니다.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# OpenSearch로 마이그레이션

OpenSearch는 Elasticsearch의 라이센스 변경 후 생성된 Elasticsearch 7.10.2의 오픈 소스 포크입니다.

2.4.4, 2.4.3-p2 및 2.3.7-p3부터 Adobe Commerce 및 Magento Open Source은 OpenSearch를 지원합니다. 클라우드 인프라에서 Adobe Commerce은 더 이상 지원되지 않지만, 온-프레미스 설치는 Elasticsearch을 계속 지원합니다.

## 마이그레이션 경로

OpenSearch로 마이그레이션하는 단계는 간단하고 대개 Elasticsearch 구성 단계를 따릅니다. 이 단계에서는 검색 엔진을 사용하는 유일한 응용 프로그램으로서 Adobe Commerce을 가정합니다. 여러 애플리케이션이 검색 엔진을 사용하는 경우 공식 마이그레이션 가이드를 따르십시오 [오픈 소스 Elasticsearch에서 OpenSearch로 이동](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. 설치가 [검색 엔진 사전 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. 사이트에 위치 [유지 관리 모드](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. 선택적으로 Elasticsearch 제거.

1. [OpenSearch 설치](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [검색 엔진 구성](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 캐시 플러시 및 카탈로그 검색 색인 재지정 등의 관련 작업을 수행합니다.

더 이상 구성 값을 변경할 필요가 없습니다.
