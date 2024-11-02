---
title: Adobe Commerce 성능 최적화
description: 일부 기본 설정을 변경하여 Adobe Experience Manager as a CMS을 사용하도록 Adobe Commerce 프로젝트를 준비합니다.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Adobe Commerce 성능 최적화

## AEM 및 Adobe Commerce 인프라의 지리적 위치

페이지를 작성할 때 AEM 게시자와 Adobe Commerce GraphQL 간의 지연 시간을 줄이려면 두 개의 별도 인프라의 초기 프로비저닝이 동일한 AWS(또는 Azure) 지역 내에서 호스팅되어야 합니다. 두 클라우드에 대해 선택한 지리적 위치도 대부분의 고객 기반에 가장 가까워야 클라이언트측 GraphQL 요청이 지리적으로 가까운 위치에서 대부분의 고객에게 제공됩니다.

## Adobe Commerce의 GraphQL 캐싱

사용자의 브라우저 또는 AEM 게시자가 Adobe Commerce의 GraphQL을 호출하면 특정 호출이 캐시됩니다
Fastly에서. 캐시된 쿼리는 일반적으로 개인적이지 않은 데이터를 포함하고 있으며 자주 변경되지 않는 쿼리입니다. 예를 들어 categories, categoryList 및 products가 있습니다. 명시적으로 캐시되지 않는 항목은 정기적으로 변경되며 캐시되는 경우 장바구니 및 customerPaymentTokens와 같은 쿼리와 같은 개인 데이터 및 사이트 운영에 위험을 초래할 수 있는 항목입니다.

GraphQL을 사용하면 한 번의 호출로 여러 쿼리를 만들 수 있습니다. Adobe Commerce이 캐시할 수 없는 다른 많은 쿼리와 함께 캐시하지 않는 한 개의 쿼리라도 지정하는 경우 Adobe Commerce은 호출의 모든 쿼리에 대해 캐시를 무시합니다. 잠재적 캐시 가능한 쿼리가 의도하지 않게 우회되지 않도록 여러 쿼리를 결합할 때 개발자가 이를 고려해야 합니다‡

>[!NOTE]
>
> 캐시 가능 쿼리와 캐시 불가능 쿼리에 대한 자세한 내용은 Adobe Commerce [개발자 설명서](https://developer.adobe.com/commerce/webapi/graphql/caching.html)를 참조하세요.

## 카탈로그 플랫 테이블

제품 및 범주에 플랫 테이블을 사용하지 않는 것이 좋습니다. 더 이상 사용되지 않는 이 기능을 사용하면 성능이 저하되고 색인화 문제가 발생할 수 있으므로 상점 첫 번째 섹션에서 Adobe Commerce 관리자를 통해 플랫 카탈로그를 비활성화해야 합니다. 일부 타사 모듈 및 사용자 지정에서는 플랫 테이블이 올바르게 작동해야 하므로 이러한 확장 또는 사용자 지정을 사용할 때 플랫 테이블을 사용해야 하는 것과 관련된 영향 및 위험을 파악하기 위해 평가를 수행하는 것이 좋습니다.

## Fastly 원점 차폐

기본적으로 Fastly 원본 차폐는 활성화되지 않습니다. Fastly의 원본 차폐의 목적은 Adobe Commerce 원본으로 직접 트래픽을 줄이는 것입니다. 요청이 수신되면 Fastly 에지 위치(또는 &quot;존재 지점&quot; / POP)가 캐시된 콘텐츠를 확인하고 제공합니다. 캐시되지 않은 경우 Shield POP로 계속 진행하여 해당 콘텐츠가 캐시되는지 확인합니다(이전에 다른 글로벌 POP에서도 콘텐츠를 요청한 경우 캐시됨). 마지막으로 Shield POP에 캐시되지 않은 경우 원본 서버로만 진행됩니다.

Fastly 원본 차폐는 Adobe Commerce 관리 Fastly 구성 백엔드 설정에서 활성화할 수 있습니다. 최상의 성능을 얻으려면 Adobe Commerce 원본 데이터 센터와 가장 가까운 실드 위치를 선택해야 합니다.

## Fastly 이미지 최적화

Fastly 원본 차폐가 활성화되면 Fastly Image Optimizer를 활성화할 수도 있습니다. 제품 카탈로그 이미지가 Adobe Commerce에 저장되는 경우, 이 서비스를 통해 리소스 집약적인 제품 카탈로그 이미지 변환 처리를 Adobe Commerce 오리진에서 Fastly로 오프로드할 수 있습니다. 이미지가 에지 위치에서 변환되므로 Adobe Commerce 오리진으로의 요청 수가 감소하여 지연 시간이 제거되므로 페이지 로드 시간에 대한 최종 사용자 응답 시간이 향상됩니다.

Fastly 이미지 최적화는 원본 실드가 활성화된 후에만 관리자의 Fastly 구성에서 &quot;딥 이미지 최적화 활성화&quot;를 통해 활성화할 수 있습니다. Fastly 이미지 최적화를 위한 구성에 대한 자세한 내용은 Adobe Commerce [개발자 설명서](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization)를 참조하세요.

![Adobe Commerce 관리자의 Fastly 이미지 최적화 설정 스크린샷](../assets/commerce-at-scale/image-optimization.svg)

## 사용하지 않는 모듈 비활성화

Adobe Commerce Headless를 실행하고 GraphQL 끝점을 통해 요청만 제공하고 Adobe Commerce에서 직접 프론트엔드 스토어 페이지를 제공하지 않는 경우, 많은 모듈이 중복되고 사용되지 않습니다. 사용하지 않는 모듈을 비활성화하면 Adobe Commerce 코드 베이스가 작아지고 복잡해지지 않으므로 성능이 향상될 수 있습니다. Adobe Commerce에서 비활성화된 모듈은 작성기를 사용하여 관리할 수 있습니다. 비활성화할 수 있는 모듈은 사이트의 요구 사항에 따라 다르므로 권장되는 목록은 각 고객의 Adobe Commerce 구현에 따라 달라지므로 제공되지 않습니다.

## MySQL 및 Redis 연결 활성화

기본적으로 MySQL 및 Redis 슬레이브 연결은 클라우드의 Adobe Commerce에서 활성화되지 않습니다. 이러한 설정은 매우 높은 부하가 예상되는 고객에게만 적합하기 때문입니다. AZ 간(Cross-Availability Zones) 지연은 슬레이브 연결이 활성화될수록 더 높으므로 이 설정은 인스턴스가 일반 로드 수준만 수신하는 경우 클라우드 인스턴스에서 Adobe Commerce의 성능을 실제로 감소시킵니다.

Adobe Commerce 인스턴스에서 로드가 많이 발생할 것으로 예상되면 MySQL 및 Redis용 마스터 슬레이브를 활성화하면 MySQL 데이터베이스 또는 Redis의 로드를 다른 노드에 분산시켜 성능을 향상시키는 데 도움이 됩니다.

정상 부하가 있는 환경에서 슬레이브 연결을 활성화하면 성능이 10~15% 느려집니다. 그러나 부하가 많고 트래픽이 많은 클러스터에서는 약 10~15%의 성능 향상이 이루어집니다. 따라서 이 설정이 로드 중 성능 시간에 도움이 되는지 평가하기 위해 예상 트래픽 수준으로 환경을 부하 테스트하는 것이 중요합니다.

mysql 및 redis에 대한 슬레이브 연결을 활성화/비활성화하려면 다음을 포함하도록 `.magento.env.yaml` 파일을 편집해야 합니다.

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

크기 조정된 아키텍처(분할 아키텍처 - 아래 참조)의 경우 Redis 슬레이브 연결을 활성화하면 오류가 발생하므로 활성화해서는 안 됩니다. 분할 아키텍처의 경우 대신 Redis용 L2 캐싱을 구현하는 것이 좋습니다.

## Adobe Commerce on cloud scale (split) 아키텍처로 이동

위의 모든 구성 후에도 로드 테스트 결과 또는 라이브 인프라 성능 분석이 Adobe Commerce에 대한 로드 수준이 일관되게 CPU 및 기타 시스템 리소스를 최대화하는 수준임을 나타내는 경우 크기 조정(분할) 아키텍처로의 이동을 고려해야 합니다.

표준 Pro 아키텍처에는 3개의 노드가 있으며, 각 노드에는 전체 기술 스택이 포함되어 있습니다. 분할 계층 아키텍처로 전환하면 최소 6개의 노드로 변경됩니다. 그 중 3개는 Elasticsearch, MariaDB, Redis 및 기타 핵심 서비스를 포함하며 나머지 3개는 웹 트래픽을 처리하기 위해 phpfpm 및 NGIX를 포함합니다. 분할 계층에는 더 큰 확장이 가능합니다. 데이터베이스가 포함된 코어 노드를 수직으로 확장할 수 있고, 웹 노드를 수평 및 수직으로 확장할 수 있으므로 고부하 작업의 설정 기간 및 추가 리소스가 필요한 노드에 대해 필요에 따라 인프라를 확장할 수 있는 많은 유연성을 제공합니다.

사이트에 대한 과중한 로드 예상으로 인해 분할 계층 아키텍처로 전환하기로 결정한 경우, 이를 활성화하는 단계에서 Adobe 계정 팀과 논의해야 합니다.
