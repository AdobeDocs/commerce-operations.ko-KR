---
title: AEM 성능 최적화
description: Adobe Commerce에서 높은 로드를 지원하도록 기본 Adobe Experience Manager 구성을 최적화합니다.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM 성능 최적화

AEM Dispatcher는 빠르고 동적인 환경을 제공하는 데 도움이 되는 역방향 프록시입니다. Apache HTTP Server와 같은 정적 HTML 서버의 일부로 작동하며 가능한 한 많은 사이트 콘텐츠를 정적 리소스 형태로 저장(또는 &quot;캐싱&quot;)하는 것을 목적으로 합니다. 이 접근 방식은 AEM 페이지 렌더링 기능과 Adobe Commerce GraphQL 서비스에 최대한 액세스해야 하는 필요성을 최소화하는 데 목적이 있습니다. 많은 페이지를 정적 HTML, CSS 및 JS로 제공하여 사용자에게 성능 이점을 제공하고 환경의 인프라 요구 사항을 줄입니다. 사용자 간에 동일하게 반복될 수 있는 모든 페이지 또는 쿼리는 캐싱을 위해 고려되어야 합니다.

다음 섹션은 CIF/Adobe Commerce 환경에서 AEM에 효과적으로 캐싱을 활성화하기 위해 검토해야 하는 권장 기술 포커스 영역을 개략적으로 보여 줍니다.

## AEM dispatchers를 기반으로 한 TTL 기반 캐싱

디스패처에 가능한 한 많은 사이트를 캐시하는 것은 모든 AEM 프로젝트에 모범 사례입니다. 시간 기반 캐시 무효화를 사용하면 지정된 제한된 시간 동안 서버측에서 렌더링된 CIF 페이지를 캐시합니다. 설정된 시간이 만료되면 다음 요청은 AEM 게시자와 Adobe Commerce GraphQL에서 페이지를 다시 빌드하고 다음 무효화될 때까지 Dispatcher 캐시에 다시 저장합니다.

TTL 캐싱 기능은 ACS AEM Commons 패키지 내에서 &quot;Dispatcher TTL&quot; 구성 요소를 사용하고 dispatcher.any 구성 파일에서 /enableTTL &quot;1&quot;을 설정하여 AEM에서 구성할 수 있습니다.

활성화되면 Dispatcher는 백엔드의 응답 헤더를 평가하고 Cache-Control 최대 기간 또는 만료 날짜가 포함된 경우 캐시 파일 옆에 수정 시간이 만료 날짜와 동일한 보조 빈 파일이 생성됩니다. 캐시된 파일이 수정 시간 이후에 요청되면 백엔드에서 자동으로 다시 요청됩니다. 비즈니스 이해 당사자가 제품 업데이트 지연(TTL)을 승인하고 수락하면 효과적인 캐싱 메커니즘을 제공하여 수동 개입이나 유지 관리가 필요하지 않습니다.

## 브라우저 캐싱

위의 Dispatcher TTL 접근 방식은 요청과 게시자에 대한 로드를 크게 줄여주지만 변경할 가능성이 매우 낮은 일부 자산이 있으므로 사용자의 브라우저에서 로컬로 관련 파일을 캐싱하여 Dispatcher에 대한 요청도 줄일 수 있습니다. 예를 들어 사이트 템플릿의 사이트에 있는 모든 페이지에 표시되는 사이트 로고는 Dispatcher에 매번 요청하지 않아도 됩니다. 대신 사용자의 브라우저 캐시에 저장할 수 있습니다. 각 페이지 로드에 대한 대역폭 요구 사항 감소는 사이트 응답성 및 페이지 로드 시간에 큰 영향을 줍니다.

브라우저 수준에서 캐싱은 일반적으로 &quot;Cache-Control: max-age=&quot; 응답 헤더를 통해 수행됩니다. maxage 설정은 사이트에서 파일 &quot;다시 유효성 검사&quot; 또는 요청을 다시 시도하기 전까지 파일을 캐시해야 하는 시간(초)을 브라우저에 알려줍니다. 이러한 캐시 max-age 개념을 일반적으로 &quot;캐시 만료&quot; 또는 TTL(&quot;Time to Live&quot;)이라고 합니다. 규모에 맞게 상거래 경험 제공 - Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

클라이언트의 브라우저에서 캐시되도록 설정할 수 있는 AEM/CIF/Adobe Commerce 사이트의 일부 영역은 다음과 같습니다.

- 이미지(사이트 로고 및 템플릿 디자인 이미지와 같은 AEM 템플릿 자체 내에서 - 카탈로그 제품 이미지는 Fastly를 통해 Adobe Commerce에서 호출되며, 이러한 이미지 캐싱은 나중에 설명합니다.)
- HTML 파일(자주 변경되지 않는 페이지 - 약관 페이지 등의 경우)
- CSS 파일
- 모든 사이트 JavaScript 파일 - CIF JavaScript 파일 포함

## Dispatcher 통계파일레벨 비활성화 유예 기간 최적화

기본 Dispatcher 구성은 /statfilelevel &quot;0&quot; 설정을 사용합니다. 즉, 단일 &quot;.stat&quot; 파일이 htdocs 디렉터리(문서 루트 디렉터리)의 루트에 배치됩니다. AEM의 페이지나 파일이 변경되면 이 단일 통계 파일의 수정 시간이 변경 시간으로 업데이트됩니다. 시간이 리소스의 수정 시간보다 최신인 경우 Dispatcher는 모든 리소스가 무효화된 것으로 간주하고 무효화된 리소스에 대한 후속 요청은 게시 인스턴스에 대한 호출을 트리거합니다. 따라서 기본적으로 이 설정을 사용하면 모든 활성화가 전체 캐시를 무효화합니다.

모든 사이트, 특히 로드가 많은 상거래 사이트의 경우 단일 페이지 업데이트만으로 전체 사이트 구조가 무효화되도록 하려면 AEM 게시 계층에 불필요한 로드를 배치해야 합니다.

대신 문서 루트 디렉터리에서 htdocs 디렉터리의 하위 디렉터리 깊이에 해당하는 더 높은 값으로 통계파일레벨 설정을 수정하여 특정 수준에 있는 파일이 무효화되면 해당 .stat 디렉터리 수준 및 그 아래의 파일만 업데이트됩니다.

예를 들어 다음 위치에 제품 페이지 템플릿이 있다고 가정해 보겠습니다.

```
content/ecommerce/us/en/products/product-page.html
```

각 폴더 수준에는 위 표에 분류된 대로 &#39;통계 수준&#39;이 있습니다.

| content (docroot) | ecommerce | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

이 경우 통계파일레벨 속성을 기본값 &quot;0&quot;으로 설정하고 product-page.html 템플릿을 업데이트하고 활성화하여 무효화를 트리거하면 docroot에서 레벨 4까지의 모든 .stat 파일이 터치되고 파일이 무효화되어 해당 단일 변경으로 인한 사이트(다른 웹 사이트, 국가 및 언어 포함)의 모든 페이지에 대한 AEM 게시 인스턴스의 추가 요청이 발생합니다.

그러나 statfilelevel 속성이 레벨 4로 설정되고 product-page.html이 변경되면 해당 웹 사이트/국가/언어에 대한 products 디렉토리의 .stat 파일만 터치됩니다.

.stat 파일 수준을 너무 높은 수준으로 설정해서는 안 됩니다. 20을 초과하면 성능에 영향을 줄 수 있습니다. 성능 테스트를 실행하는 동안 벌크 파일 활성화를 실행하면 통계 수준을 조정해야 하는 올바른 수준을 얻을 수 있습니다.

통계파일레벨을 구성할 때 최적화하는 또 다른 Dispatcher 설정은 gracePeriod 설정입니다. 마지막 활성화가 발생한 후 캐시에서 오래된 자동 무효화 리소스가 계속 제공될 수 있는 시간(초)을 정의합니다. 자동 무효화된 리소스는 모든 활성화(해당 경로가 dispatcher /invalidate 섹션과 일치하고 statfileslevel 속성에 지정된 수준과 일치하는 경우)에 의해 무효화됩니다. gracePeriod 설정을 2초로 설정하면 게시자가 새 페이지를 만드는 과정 중에 여러 요청이 게시자에게 계속 전송되는 시나리오를 방지할 수 있습니다.

>[!NOTE]
>
> 이 주제에 대한 자세한 내용은 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub 리포지토리.

## CIF - 구성 요소를 통한 GraphQL 캐싱

AEM 내의 개별 구성 요소를 캐시되도록 설정할 수 있습니다. 즉, Adobe Commerce에 대한 GraphQL 요청을 한 번 호출한 다음 구성된 시간 제한까지 후속 요청을 AEM 캐시에서 검색하고 Adobe Commerce에 더 이상 로드하지 않습니다. 예제는 모든 페이지에 표시되는 카테고리 트리를 기반으로 하는 사이트 탐색과 패싯된 검색 기능 내의 옵션입니다. 이는 Adobe Commerce에서 리소스를 많이 사용하는 쿼리를 빌드해야 하는 두 가지 영역이지만 정기적으로 변경되지는 않으므로 캐싱에 적합합니다. 이러한 방식으로, 예를 들어 게시자가 PDP 또는 PLP를 다시 작성하는 경우에도 탐색 빌드에 대한 리소스 집약적인 GraphQL 요청이 Adobe Commerce에 도달하지 않고 AEM CIF의 GraphQL 캐시에서 검색할 수 있습니다.

아래 예제는 탐색 구성 요소가 사이트의 모든 페이지에서 동일한 GraphQL 쿼리를 보내기 때문에 캐시되는 것입니다. 아래 요청은 탐색 구조에 대해 10분 동안 지난 100개의 항목을 캐시합니다.

```
venia/components/structure/navigation:true:100:600
```

아래 예제는 검색 페이지에서 1시간 동안 지난 100개의 패싯된 검색 옵션을 캐시합니다.

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

캐시가 &#39;히트&#39;가 되고 Adobe Commerce에 대한 반복 호출이 수행되지 않도록 하려면 모든 사용자 지정 http 헤더와 변수를 포함한 요청이 정확히 일치해야 합니다. 일단 설정되면 이 캐시를 수동으로 무효화하는 쉬운 방법이 없다는 점에 유의해야 합니다. 따라서 Adobe Commerce에 새 카테고리가 추가되면 위의 캐시에 설정된 만료 시간이 만료되고 GraphQL 요청이 새로 고쳐질 때까지 탐색에 표시되지 않을 수 있습니다. 검색 패싯에 대해서도 동일합니다. 그러나 이 캐싱을 통해 얻을 수 있는 성능 이점을 고려한다면 일반적으로 이는 적절한 대안입니다.

위의 캐싱 옵션은 &quot;GraphQL Client Configuration Factory&quot;의 AEM OSGi 구성 콘솔을 사용하여 설정할 수 있습니다. 각 캐시 구성 항목은 다음 형식으로 지정할 수 있습니다.

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 하이브리드 캐싱 - 캐시된 Dispatcher 페이지 내의 클라이언트측 GraphQL 요청

또한 페이지의 캐싱에 대한 하이브리드 접근 방식이 가능합니다. CIF 페이지에는 항상 고객의 브라우저에서 직접 Adobe Commerce의 최신 정보를 요청하는 구성 요소가 포함될 수 있습니다. 이 기능은 예를 들어 PDP 내의 제품 가격과 같은 실시간 정보를 사용하여 최신 상태로 유지해야 하는 템플릿 내의 특정 페이지 영역에 유용합니다. 동적 가격 일치로 인해 가격이 자주 변경되는 경우 해당 정보는 Dispatcher에 캐시되지 않도록 구성할 수 있으며, 오히려 AEM CIF 웹 구성 요소가 있는 GraphQL API를 통해 직접 Adobe Commerce에서 고객의 브라우저에서 클라이언트측에서 가격을 가져올 수 있습니다.

AEM 구성 요소 설정 을 통해 구성할 수 있습니다. 제품 목록 페이지의 가격 정보에 대해 이 구성 요소는 제품 목록 템플릿에서 구성하고 페이지 설정에서 제품 목록 구성 요소를 선택한 다음 &quot;가격 로드&quot; 옵션을 선택할 수 있습니다. 동일한 방식이 재고 수준에 적용됩니다.

상기 방법들은 실시간, 지속적으로 최신 정보를 요구하는 경우에만 사용되어야 한다. 가격 책정 시 위의 예에서 비즈니스 이해 당사자와 협력하여 낮은 트래픽 시간에만 가격을 매일 업데이트하고 캐시 플러시 작업을 수행할 수 있습니다. 이렇게 하면 가격 정보를 표시하는 각 페이지를 작성할 때 실시간 가격 정보 요청과 그에 따른 Adobe Commerce 추가 로드에 대한 필요성이 제거됩니다.

## 캐시 불가능 GraphQL 요청

페이지 내의 특정 동적 데이터 구성 요소는 캐시해서는 안 되며, 장바구니 및 체크아웃 페이지 전체의 호출과 같이 항상 Adobe Commerce에 대한 GraphQL 호출이 필요합니다. 이 정보는 사용자별로 다르며, 장바구니에 제품을 추가하는 등의 사이트 고객 활동으로 인해 지속적으로 변경됩니다.

사이트 디자인이 사용자의 역할에 따라 다른 응답을 제공하는 경우 로그인한 고객에 대해 GraphQL 쿼리 결과를 캐시해서는 안 됩니다. 예를 들어 여러 고객 그룹을 만들고 각 그룹에 대해 다른 제품 가격 또는 다른 제품 범주 가시성을 설정할 수 있습니다. 이러한 결과를 캐시하면 고객이 다른 고객 그룹의 가격을 보거나 잘못된 카테고리가 표시될 수 있습니다.

## AEM Dispatcher 캐시의 추적 매개 변수 무시

전자 상거래 사이트는 PPC 검색 광고 또는 소셜 미디어 캠페인을 사용하여 사이트 트래픽을 유도할 수 있습니다.

이러한 미디어를 사용하면 추적 ID가 해당 플랫폼의 아웃바운드 링크에 추가됩니다. 예를 들어, Facebook은 URL에 Facebook 클릭 ID(fbclid)를 추가하고, Google Advertises는 Google 클릭 ID(gclid)를 추가합니다. 예를 들어, AEM 프론트엔드에 대한 수신 링크가 아래와 같이 표시됩니다.

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

gclid 및 fbclid는 광고를 클릭하는 모든 사용자에 대해 변경되며, 이는 추적용으로 사용되지만 기본 설정으로 AEM은 모든 요청을 고유한 페이지로 간주하여 Dispatcher를 무시하고 게시자 및 Adobe Commerce에 불필요한 추가 로드를 생성합니다.

서지 이벤트 동안 이로 인해 AEM 게시자가 오버로드되고 응답하지 않을 수 있습니다. 페이지에 대한 매개 변수를 무시하도록 설정하면 페이지가 처음 요청될 때 페이지가 캐시됩니다. 페이지에 대한 후속 요청은 요청의 매개 변수 값에 관계없이 캐시된 페이지에 제공됩니다.

>[!NOTE]
>
>설정의 중요성에 대한 추가 읽기 `ignoreUrlParams` 다음에서 사용할 수 있습니다. [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub 리포지토리.

따라서 페이지의 HTML 구조를 변경하는 GET 매개 변수가 사용되는 경우를 제외하고 &quot;ignoreUrlParams&quot;에서 기본적으로 모든 매개 변수를 무시하도록 구성해야 합니다. 예를 들어 검색어가 URL에 GET 매개 변수로 포함되어 있는 검색 페이지를 사용하면 됩니다. 이 경우 gclid, fbclid 및 광고 채널에서 사용 중인 기타 추적 매개 변수와 같은 매개 변수를 무시하도록 ignoreUrlParams를 수동으로 구성해야 일반 사이트 작업에 필요한 GET 매개 변수는 영향을 받지 않습니다.

## MPM 작업자 디스패처 제한

MPM 작업자 설정은 Dispatcher의 사용 가능한 CPU 및 RAM을 기반으로 최적화하기 위해 철저한 테스트가 필요한 고급 Apache HTTP 서버 구성입니다. 그러나 이 백서의 범위에서는 ServerLimit 및 MaxRequestWorkers를 서버의 사용 가능한 CPU 및 RAM이 지원하는 수준으로 늘린 다음 MinSpareThreads 및 MaxSpareThreads를 모두 MaxRequestWorkers와 일치하는 수준으로 늘려야 한다고 제안합니다.

이 구성을 사용하면 Apache HTTP가 &quot;전체 준비 설정&quot;에 남게 됩니다. 이는 상당한 RAM 및 여러 CPU 코어를 가진 서버의 고성능 구성입니다. 이 구성은 요청을 처리할 준비가 된 지속적인 오픈 연결을 유지함으로써 Apache HTTP에서 가능한 최상의 응답 시간을 생성하고 플래시 판매 중과 같은 갑작스러운 트래픽 급증에 대한 응답으로 새 프로세스를 생성하는 데 있어 지연을 제거합니다.
