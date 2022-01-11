---
title: Current Search Engine Not Supported
description: Troubleshoot your Adobe Commerce or Magento Open Source upgrade after encountering an error about an unsupported search engine.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Current search engine not supported

다음 오류 메시지는 업그레이드할 Magento 버전이 업그레이드 중인 Magento 버전에서 지원되지 않는 카탈로그 검색 엔진을 사용하도록 구성되어 있음을 나타냅니다.

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

This error means one of the following conditions is true on the down-level version of Adobe Commerce or Magento Open Source:

- The search engine is set to MySQL.
- The search engine is set to a version of Elasticsearch that is no longer supported.

Use the following command to check the current search engine:

```bash
bin/magento config:show catalog/search/engine
```

The error occurs if the returned value is `mysql` or `elasticsearch`.

>[!WARNING]
>
>If you have received this error, Magento is in an inconsistent state, and you cannot access the Admin. 이 오류를 해결하는 동안 이전 버전으로 되돌리는 것이 좋습니다. To do this, run one of the following commands:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>위치 `<version>` 실행 중인 Magento 버전입니다. **이전** 업그레이드. 예, `2.3.5`.

Follow the guidelines described in the following sections to recover from an inconsistent state.

## If your search engine is `mysql`

Before 2.4, MySQL was the default catalog search engine, but MySQL is no longer supported in this capacity. 이제 2.4로 업그레이드하기 전에 Elasticsearch을 검색 엔진으로 설치 및 구성해야 합니다.

Use the following resources to help guide you through this process:

- [Elasticsearch 설치 및 구성](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Installing Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configure Elasticsearch to work with [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) or [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Configure Magento to use Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Elasticsearch 및 재색인을 구성한 후 2.4로 업그레이드할 수 있습니다.

## 검색 엔진이 `elasticsearch`

값 `elasticsearch` Adobe Commerce 또는 Magento Open Source의 다운 수준 버전이 Elasticsearch 2.x를 사용하도록 구성되어 있음을 나타냅니다. 이 버전의 Elasticsearch은 더 이상 지원되지 않습니다.

You must perform the following tasks before upgrading to 2.4:

1. Elasticsearch 업데이트. We recommend updating to Elasticsearch 7.x. Refer to [Upgrading Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) for full instructions on backing up your data, detecting potential migration issues, and testing upgrades before deploying to production. 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작할 필요가 있거나 필요하지 않을 수 있습니다.

   >[!NOTE]
   >
   >Elasticsearch을 사용하려면 JDK 1.8 이상이 필요합니다. 자세한 내용은 [JDK(Java Software Development Kit) 설치](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 를 클릭하여 설치된 JDK 버전을 확인합니다.

1. [Elasticsearch을 사용하도록 Magento 구성](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) 색인화

Elasticsearch 및 재색인을 구성한 후 2.4로 업그레이드할 수 있습니다.
