---
title: 현재 검색 엔진이 지원되지 않음
description: 지원되지 않는 검색 엔진에 대한 오류가 발생한 후 Adobe Commerce 또는 Magento Open Source 업그레이드 문제를 해결합니다.
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 현재 검색 엔진이 지원되지 않음

다음 오류 메시지는 업그레이드 중인 Adobe Commerce 또는 Magento Open Source 버전이 업그레이드 중인 버전에서 지원되지 않는 카탈로그 검색 엔진을 사용하도록 구성되어 있음을 나타냅니다.

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

이 오류는 Adobe Commerce 또는 Magento Open Source의 하위 수준 버전에서 다음 조건 중 하나가 참임을 의미합니다.

- 검색 엔진이 MySQL로 설정되어 있습니다.
- 검색 엔진이 더 이상 지원되지 않는 Elasticsearch 버전으로 설정되어 있습니다.

다음 명령을 사용하여 현재 검색 엔진을 확인합니다.

```bash
bin/magento config:show catalog/search/engine
```

반환된 값이 다음과 같은 경우 오류가 발생합니다. `mysql`, `elasticsearch`, 또는 `elasticsearch6`.

>[!WARNING]
>
>이 오류가 발생한 경우 설치가 일관되지 않은 상태이며 관리자에 액세스할 수 없습니다. 이 오류를 해결하는 동안 이전 버전으로 되돌리는 것이 좋습니다. 이렇게 하려면 다음 명령 중 하나를 실행합니다.
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
>위치 `<version>` 실행 중인 Magento 버전입니다. **다음 이전** 업그레이드. 예를 들어, `2.3.5`.

다음 섹션에 설명된 지침에 따라 일관되지 않은 상태에서 복구하십시오.

## 검색 엔진이 인 경우 `mysql`

2.4 이전에는 MySQL이 기본 카탈로그 검색 엔진이었지만 이 용량에서는 MySQL이 더 이상 지원되지 않습니다. 이제 2.4로 업그레이드하기 전에 Elasticsearch 또는 OpenSearch를 검색 엔진으로 설치 및 구성해야 합니다.

다음 리소스를 사용하여 이 프로세스를 안내합니다.

- [검색 엔진 설치 및 구성](../../configuration/search/overview-search.md)
- [검색 엔진 구성](../../configuration/search/configure-search-engine.md)

검색 엔진을 구성하고 색인을 재지정하면 2.4로 업그레이드할 준비가 된 것입니다.

## 검색 엔진이 인 경우 `elasticsearch`

Elasticsearch 6 및 이전 버전은 더 이상 지원되지 않습니다.

값 `elasticsearch` 는 Adobe Commerce 또는 Magento Open Source의 하위 수준 버전이 Elasticsearch 2.x를 사용하도록 구성되어 있음을 나타냅니다. 이 버전의 Elasticsearch은 더 이상 지원되지 않습니다.

2.4로 업그레이드하기 전에 다음 작업을 수행해야 합니다.

1. Commerce에서 지원하는 Elasticsearch 버전으로 업데이트합니다. 을(를) 참조하십시오 [업그레이드 Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 프로덕션에 배포하기 전에 데이터 백업, 잠재적인 마이그레이션 문제 감지 및 업그레이드 테스트에 대한 전체 지침 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작해야 할 수도 있고 필요하지 않을 수도 있습니다.

   >[!NOTE]
   >
   >Elasticsearch을 사용하려면 JDK 1.8 이상이 필요합니다. 다음을 참조하십시오 [JDK(Java Software Development Kit) 설치](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 설치된 JDK 버전을 확인하려면 다음을 수행하십시오.

1. [구성 Elasticsearch](../../configuration/search/configure-search-engine.md) 색인 재지정.

검색 엔진을 구성하고 색인을 재지정하면 2.4로 업그레이드할 준비가 된 것입니다.
