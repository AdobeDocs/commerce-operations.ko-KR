---
title: Elasticsearch에서 OpenSearch로 마이그레이션
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 사용되는 검색 엔진 교체에 대해 알아봅니다.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# OpenSearch로 마이그레이션

OpenSearch는 Elasticsearch의 라이센스 변경 후에 생성된 Elasticsearch 7.10.2의 오픈 소스 포크입니다.

2.4.4, 2.4.3-p2 및 2.3.7-p3부터 Adobe Commerce 및 Magento Open Source은 OpenSearch를 지원합니다. 클라우드 인프라의 Adobe Commerce에 대해 더 이상 지원되지 않지만 온프레미스 설치는 Elasticsearch을 계속 지원합니다. 버전 2.4.6부터 OpenSearch에는 관리 구성 설정에 고유한 모듈과 필드가 있습니다.

## 마이그레이션 경로

OpenSearch로 마이그레이션하는 단계는 간단하며 대부분 Elasticsearch 구성 단계를 따릅니다. 이 절차에서는 Adobe Commerce이 검색 엔진을 사용하는 유일한 애플리케이션이라고 가정합니다. 여러 애플리케이션이 검색 엔진을 사용하는 경우 공식 마이그레이션 안내서를 따르십시오 [오픈 소스 Elasticsearch에서 OpenSearch로 이동](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. 설치가 다음을 충족하는지 확인합니다. [검색 엔진 사전 요구 사항](../../installation/prerequisites/search-engine/overview.md).

1. 사이트 배치 위치 [유지 관리 모드](../../installation/tutorials/maintenance-mode.md).

1. 필요한 경우 Elasticsearch을 제거합니다.

1. [OpenSearch 설치](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [검색 엔진 구성](../../configuration/search/configure-search-engine.md) 및 를 사용하여 캐시를 플러시하고 카탈로그 검색 인덱스를 다시 인덱싱하는 등 관련 작업을 수행할 수 있습니다.

구성 값을 더 이상 변경할 필요가 없습니다.
