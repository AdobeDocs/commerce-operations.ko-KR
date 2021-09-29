---
title: 성능 최적화 Recommendations
description: 다음 권장 사항을 수행하여 Adobe 상거래 구현의 성능을 최적화합니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---


# 성능 최적화 검토

성능 최적화는 여러 측면에서 가져올 수 있지만 대부분의 시나리오에서 고려해야 하는 몇 가지 일반적인 권장 사항이 있습니다. 여기에는 인프라 요소에 대한 구성 최적화, Adobe 상거래 백엔드 구성 및 아키텍처 확장성 계획이 포함됩니다.

## 인프라

다음 섹션에서는 인프라 최적화에 대한 권장 사항에 대해 설명합니다.

### DNS 조회

DNS 조회는 도메인 이름이 속한 IP 주소를 찾는 프로세스입니다. 브라우저는 DNS 조회가 완료될 때까지 기다려야 각 요청에 대한 모든 것을 다운로드할 수 있습니다. 전체 페이지 로드 시간을 향상하려면 DNS 조회를 줄이는 것이 중요합니다.

### CDN(콘텐츠 전달 네트워크)

CDN을 사용하여 자산 다운로드 성능을 최적화합니다. Adobe 상거래 는 실제 를 사용합니다. Adobe Commerce의 온-프레미스 구현이 있는 경우 CDN 레이어 추가도 고려해야 합니다.

### 웹 지연

데이터 센터의 위치는 프런트 엔드 사용자의 웹 지연에 영향을 줍니다.

### 네트워크 대역폭

Sufficient network bandwidth is one of the key requirements for data exchange between web nodes, databases, caching/session servers, and other services.

Adobe 커머스 가 높은 성능을 위해 캐싱을 효과적으로 활용하므로 시스템은 Redis와 같은 캐싱 서버와 데이터를 적극적으로 교환할 수 있습니다. If Redis is located on a remote server, you must provide a sufficient network channel between web nodes and the caching server to prevent bottlenecks on read/write operations.

### 운영 체제(OS)

운영 체제 구성 및 최적화는 다른 고로드 웹 애플리케이션과 비교하여 Adobe 상거래에 대해 유사합니다. 서버에서 처리하는 동시 연결 수가 증가하면 사용 가능한 소켓 수가 완전히 할당될 수 있습니다.

### 웹 노드의 CPU

하나의 CPU 코어는 효율적으로 캐시 없이 약 2-4개의 Adobe 상거래 요청을 제공할 수 있습니다. 모든 수신 요청을 큐에 넣지 않고 처리하는 데 필요한 웹 노드/코어 수를 결정하려면 다음 공식을 사용하십시오.

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM 설정

이러한 설정을 최적화하는 것은 다른 프로젝트에 대한 성능 테스트 결과에 따라 다릅니다.

- **ByteCode** - PHP 7에서 Adobe Commerce의 최대 속도를 얻으려면 모듈을 활성화하고  `opcache` 제대로 구성해야 합니다.

- **APCU** - PHP APCu 확장을 활성화하고 작성기를 구성하여 최대 성능을 최적화하는 것이 좋습니다. 이 확장은 열린 파일에 대한 파일 위치를 캐시하여 페이지, Ajax 호출 및 종단점을 포함하여 Adobe 상거래 서버 호출에 대한 성능을 높입니다.

- **Realpath_cacheconfiguration** - 최적화를  `realpath_cache` 사용하면 PHP 프로세스가 페이지가 로드될 때마다 경로를 찾는 대신 파일에 대한 경로를 캐싱할 수 있습니다.

### 웹 서버

nginx를 웹 서버로 사용하려면 약간의 재구성만 필요합니다. nginx 웹 서버는 더 나은 성능을 제공하며 Adobe 상거래([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample))의 샘플 구성 파일을 사용하여 쉽게 구성할 수 있습니다.

- Setup PHP-FPM with TCP properly

- Enable HTTP/2 and Gzip

- 작업자 연결 최적화

### 데이터베이스

각 저장소 및 환경이 다르기 때문에 이 문서에서는 심층적인 MySQL 조정 지침을 제공하지 않지만 몇 가지 일반적인 권장 사항을 제공할 수 있습니다.

Adobe 상거래 데이터베이스(다른 데이터베이스 및 기타 데이터베이스)는 데이터 및 인덱스를 저장하는 데 사용할 수 있는 메모리 양에 민감합니다. MySQL 데이터 인덱싱을 효과적으로 활용하려면 사용 가능한 메모리의 양은 최소한 데이터베이스에 저장된 데이터의 절반 크기에 가깝게 입력해야 합니다.

Optimize the `innodb_buffer_pool_instances` setting to avoid issues with multiple threads attempting to access the same instance. The value of the `max_connections` parameter should correlate with the total number of PHP threads configured in the application server. `innodb-thread-concurrency`에 가장 적합한 값을 계산하려면 다음 공식을 사용하십시오.

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Session caching

세션 캐싱은 Redis의 별도 인스턴스에 대해 구성하는 데 적합한 후보입니다. Memory configuration for this cache type should consider the site’s cart abandonment strategy and how long a session should expect to remain in the cache.

레디스는 최적의 성능을 위해 메모리에 다른 모든 캐시를 보관할 충분한 메모리를 할당해야 합니다. 블록 캐시는 구성할 메모리 양을 결정하는 데 중요한 요소가 됩니다. 블록 캐시는 사이트의 페이지 수에 따라 증가합니다(SKU x 저장소 보기 수).

### 페이지 캐싱

Adobe 상거래 저장소에서 전체 페이지 캐시에 Varnish를 사용하는 것이 좋습니다. `PageCache` 모듈은 여전히 코드 베이스에 있지만 개발 목적으로만 사용해야 합니다.

웹 계층 앞의 별도의 서버에 Varnish를 설치합니다. 모든 수신 요청을 수락하고 캐시된 페이지 사본을 제공해야 합니다. Varnish가 보안 페이지를 사용하여 효과적으로 작업할 수 있도록 하기 위해 Varnish 앞에 SSL 종료 프록시를 배치할 수 있습니다. Nginx는 이러한 용도로 사용할 수 있습니다.

Varnish 전체 페이지 캐시 메모리 무효화는 유효하지만, 가장 인기 있는 페이지를 메모리에 저장하기 위해 Varnish에 충분한 메모리를 할당하는 것이 좋습니다.

### 메시지 큐

MQF(메시지 큐 프레임워크)는 모듈이 메시지를 큐에 게시할 수 있도록 하는 시스템입니다. 또한 비동기식으로 메시지를 받는 소비자를 정의합니다. Adobe Commerce는 메시지 송수신을 위한 확장 가능한 플랫폼을 제공하는 메시징 브로커로서 RabbitMQ를 지원합니다.

### 성능 테스트 및 모니터링

각 프로덕션 릴리스보다 먼저 성능 테스트를 수행하면 전자 상거래 플랫폼의 기능을 예상할 수 있습니다. Keep monitoring after launch and have a scalability and backup plan for handling peak times.

>[!NOTE]
>
> 클라우드 인프라에서 Adobe 커머스 는 범위를 벗어나므로 DNS 조회를 제외하고 위의 모든 인프라 및 아키텍처 최적화를 이미 적용합니다.

### Search

Adobe Commerce 버전 2.4부터 Elasticsearch이 필요하지만, 2.4 이전 버전에서 활성화하는 것이 가장 좋습니다.

## 운영 모델

이전의 일반적인 인프라 최적화 권장 사항 외에도 특정 비즈니스 모드 및 규모에 대한 성능을 향상시키는 접근 방식이 있습니다. 각 시나리오가 다르기 때문에 이 문서에서는 모든 구성 요소에 대해 심층적인 조정 지침을 제공하지 않지만, Adobe에서는 사용자 참조에 대해 몇 가지 고급 옵션을 제공할 수 있습니다.

### 헤드리스 아키텍처

[헤드리스](../../architecture/headless/adobe-commerce.md)가 무엇이고 다른 옵션을 자세히 설명하는 별도의 섹션이 있습니다. 요약하면 점두 레이어를 플랫폼 자체와 분리합니다. 여전히 동일한 백엔드이지만, Adobe 상거래에 의해 더 이상 요청을 직접 처리하지 않고 대신 GraphQL API를 통해 사용자 지정 스토어프런트만 지원합니다.

### Adobe 상거래 업데이트 유지

Adobe Commerce는 최신 버전을 실행할 때 항상 성능이 향상됩니다. 각 새 버전이 릴리스된 후에도 Adobe Commerce를 최신 상태로 유지할 수 없는 경우에도 Adobe Commerce에서 상당한 성능 최적화를 구현할 때 계속 업그레이드하는 것이 좋습니다.

예를 들어, 2020년에 Adobe은 Redis 계층에 대한 최적화를 발표하여 비효율성, 연결 문제 및 Redis와 Adobe Commerce 간에 불필요한 데이터 전송을 해결했습니다. 2.3에서 2.4 사이의 전반적인 성능은 밤낮으로 향상되었으며 Redis 최적화 때문에 장바구니, 체크아웃, 동시 사용자가 크게 향상되었습니다.

### 데이터 모델 최적화

잘못된 데이터 모델, 제대로 구조화되지 않은 데이터, 색인이 누락된 데이터 등 많은 문제가 데이터에서 발생합니다.

몇 가지 연결을 테스트한다면 괜찮지만 실제 트래픽이 적중하면 프로덕션에서 보이고 이것이 느림이 발생하는 곳입니다. 시스템 통합자는 데이터 모델(특히 제품 속성의 경우)을 디자인하고 불필요한 속성을 추가하지 않고 비즈니스 로직(예: 가격 책정, 재고 가용성 및 검색)에 영향을 주는 필수 속성을 유지하는 방법을 알고 있어야 합니다.

비즈니스 로직에는 영향을 주지 않지만 여전히 상점 앞에 있어야 하는 이러한 속성의 경우 를 일부 속성(예: JSON 형식)에 결합하십시오.

플랫폼 성능을 최적화하기 위해 PIM 또는 ERP에서 가져온 데이터나 속성에서 비즈니스 로직이 저장소에 필요하지 않으면 Adobe 상거래에 해당 속성을 추가할 필요가 없습니다.

### 확장성을 위한 설계

이것은 캠페인을 실행하는 기업에게 중요하며 종종 피크 타임에 직면해 있습니다. 아키텍처 및 애플리케이션 설계를 손쉽게 확장할 수 있도록 하기 위해 피크 시간 동안 리소스를 늘리고 이후 리소스를 줄일 수 있습니다.
