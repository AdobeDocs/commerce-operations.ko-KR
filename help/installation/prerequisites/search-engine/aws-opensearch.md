---
title: AWS OpenSearch
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 대한 AWS OpenSearch 웹 서비스를 구성하려면 다음 단계를 따르십시오.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 및 Magento Open Source 2.4.5는 Amazon OpenSearch Service 클러스터 사용을 지원합니다. 이 서비스는 Amazon Elasticsearch 서비스의 후속 서비스입니다. 이 항목에서는 AWS OpenSearch를 사용하도록 Commerce를 구성하는 방법과 로컬 Elasticsearch 또는 OpenSearch 인스턴스에서 AWS OpenSearch 클러스터로 데이터를 마이그레이션하는 방법에 대해 설명합니다.

## AWS OpenSearch 서비스 도메인 만들기

먼저 AWS에서 OpenSearch 인스턴스를 설정해야 합니다.
읽기 [Amazon OpenSearch Service 도메인 만들기 및 관리](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) 자세한 지침은 을 참조하십시오.

## AWS OpenSearch로 데이터 가져오기

AWS에서 모든 것이 준비되면 데이터로 채워야 할 때입니다.

소규모 설치의 경우 다음과 같은 이유로 AWS 인스턴스에서 직접 인덱스를 만드는 것이 좋습니다.

* 인덱스를 다시 만드는 것은 빠른 작업입니다.
* 이전 인스턴스와 AWS 인스턴스 간에 버전 비호환성이 있을 수 있으며, 이러한 비호환성은 AWS 인스턴스에서 직접 빌드하여 방지할 수 있습니다.

대규모 설치에서는 기존 인스턴스에서 AWS으로 데이터 인덱스를 마이그레이션하는 것이 좋습니다. 이렇게 하면 다운타임이 줄어들 수 있지만 이전 Elasticsearch 서버와 AWS 간에 버전이 다르기 때문에 비호환성 문제가 발생할 위험은 여전히 적습니다.

색인은 AWS 인스턴스에서 쉽게 다시 만들 수 있으므로 마이그레이션할 필요가 없습니다.
그러나 데이터 인덱스를 마이그레이션할 때 Elasticsearch/OpenSearch 버전이 호환되는지 확인하십시오.

Amazon 보기 [Amazon OpenSearch Service로 마이그레이션](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 지침 을 참조하십시오.

### OpenSearch용 Commerce 구성

OpenSearch 구성 단계는 [고급 설치](../../advanced.md) 주제.

새 구성이 작동하는지 테스트하려면 OpenSearch 끝점을 직접 테스트합니다.

1. 관리자에서 제품을 만듭니다(예: sku=&quot;testproduct1&quot;).
1. 관리자를 통해 다시 색인화합니다.
1. OpenSearch 엔드포인트 쿼리(AWS UI에 있음):

   인덱스를 가져오려면 다음을 추가합니다. `/_cat/indices/*?v=true` 다음 URL로:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

색인에서 제품을 가져오려면 다음을 추가합니다. `/magento2docker_product_1/_search?q=*` 다음 URL로:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 추가 리소스

자세한 내용은 [OpenSearch AWS 설명서](https://docs.aws.amazon.com/opensearch-service/index.html).
