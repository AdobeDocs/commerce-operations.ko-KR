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

AEM 디스패처는 역방향 프록시이며 빠르고 동적인 환경을 제공합니다. 정적 리소스 형태로 사이트 컨텐츠를 최대한 저장(또는 &quot;캐싱&quot;)하는 것을 목표로 Apache HTTP Server와 같은 정적 HTML 서버의 일부로 작동합니다. 이 접근 방법은 AEM 페이지 렌더링 기능과 Adobe Commerce GraphQL 서비스에 최대한 액세스해야 하는 필요성을 최소화하기 위한 것입니다. 대부분의 페이지를 정적 HTML, CSS 및 JS로 제공함으로써 사용자에게 성능 이점을 제공하고 환경의 인프라 요구 사항을 줄입니다. 사용자에서 사용자까지 동일하게 반복될 수 있는 모든 페이지 또는 쿼리는 캐싱에 대해 고려되어야 합니다.

다음 섹션에서는 CIF/Adobe Commerce 환경에서 AEM에서 효율적인 캐싱을 활성화하기 위해 검토할 권장 기술 포커스 영역을 높은 수준에서 보여줍니다.

## AEM 디스패처의 TTL 기반 캐싱

모든 AEM 프로젝트에 대해 Dispatcher에 가능한 한 많은 사이트를 캐시하는 것이 가장 좋습니다. 시간 기반 캐시 무효화를 사용하면 지정된 시간 동안 서버 측에서 렌더링된 CIF 페이지를 캐시합니다. 설정 시간이 만료되면 다음 요청은 AEM Publisher 및 Adobe Commerce GraphQL에서 페이지를 다시 빌드하고 다음 무효화까지 디스패처 캐시에 다시 저장합니다.

TTL 캐싱 기능은 ACS AEM Commons 패키지 내에서 &quot;Dispatcher TTL&quot; 구성 요소를 사용하여 AEM에서 구성할 수 있고 dispatcher.any 구성 파일에서 /enableTTL &quot;1&quot;을 설정할 수 있습니다.

활성화된 경우 디스패처는 백엔드의 응답 헤더를 평가하고, 캐시 제어 최대 기간 또는 만료 날짜가 포함된 경우 캐시 파일 옆에 수정 시간이 만료 날짜와 동일한 보조 빈 파일이 만들어집니다. 수정 시간 이후에 캐시된 파일이 요청되면 백엔드에서 자동으로 다시 요청됩니다. 이를 통해 비즈니스 이해 관계자가 제품 업데이트 지연(TTL)을 확인하고 수락하면 수동 개입이나 유지 관리가 필요하지 않은 효과적인 캐싱 메커니즘을 제공합니다.

## 브라우저 캐싱

위의 Dispatcher TTL 접근 방식은 요청을 크게 줄이고 게시자에게 로드되지만 변경할 가능성이 거의 없는 일부 자산이 있으므로 사용자의 브라우저에서 관련 파일을 로컬로 캐시하여 디스패처에 대한 요청도 줄일 수 있습니다. 예를 들어 사이트 템플릿의 사이트의 모든 페이지에 표시되는 사이트의 로고는 디스패처에 매번 요청할 필요가 없습니다. 대신 사용자의 브라우저 캐시에 저장할 수 있습니다. 각 페이지 로드에 대한 대역폭 요구 사항이 감소하면 사이트 응답성 및 페이지 로드 시간에 큰 영향을 줄 수 있습니다.

브라우저 수준에서 캐싱은 일반적으로 &quot;Cache-Control: max-age=&quot; 응답 헤더. maxage 설정은 브라우저에서 &quot;유효성 검사&quot;를 다시 시도하거나 사이트에서 다시 요청하기 전에 파일을 캐시해야 하는 시간(초)을 알려줍니다. 캐시 최대 연령 개념은 일반적으로 &quot;캐시 만료&quot; 또는 TTL(&quot;Time to Live&quot;)이라고 합니다. 규모에 맞게 상거래 경험 제공 - Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

클라이언트의 브라우저에서 캐싱되도록 설정할 수 있는 AEM/CIF/Adobe Commerce 사이트의 일부 영역은 다음과 같습니다.

- 이미지(AEM 템플릿 자체 내에서, 사이트 로고 및 템플릿 디자인 이미지 등) - 카탈로그 제품 이미지를 Adobe Commerce에서 기본적으로 호출하고 이러한 이미지를 캐싱하는 방법은 나중에 설명합니다.)
- HTML 파일(자주 변경되지 않는 페이지의 경우 - 약관 페이지 등)
- CSS 파일
- 모든 사이트 JavaScript 파일(CIF JavaScript 파일 포함)

## Dispatcher 상태 파일 레벨 및 유예 기간 최적화

기본 Dispatcher 구성은 /statfilelevel &quot;0&quot; 설정을 사용합니다. 즉, 단일 &quot;.stat&quot; 파일이 htdocs 디렉토리(문서 루트 디렉토리)의 루트에 배치됩니다. AEM의 페이지 또는 파일을 변경하면 이 단일 상태 파일의 수정 시간이 변경 시간으로 업데이트됩니다. 시간이 리소스의 수정 시간보다 최신 시간인 경우 디스패처는 모든 리소스가 무효화되는 것으로 간주하며 무효화된 리소스에 대한 후속 요청은 게시 인스턴스에 대한 호출을 트리거합니다. 따라서 기본적으로 이 설정을 사용하면 모든 활성화가 전체 캐시를 무효화합니다.

사이트, 특히 부하가 많은 상거래 사이트의 경우 단일 페이지 업데이트만으로 전체 사이트 구조가 무효화되는 경우 이 작업을 수행하면 전체 사이트 구조에 대해 불필요한 로드 양이 AEM 게시 계층에 배치됩니다.

대신, 상태 파일 레벨 설정을 문서 루트 디렉토리의 htdocs 디렉토리에 있는 하위 디렉토리 깊이에 해당하는 더 높은 값으로 수정하여 특정 수준에 있는 파일이 무효화된 경우 해당 .stat 디렉토리 레벨 및 그 이하의 파일만 업데이트할 수 있습니다.

예: 다음의 제품 페이지 템플릿을 보유하고 있다고 가정해 보겠습니다.

```
content/ecommerce/us/en/products/product-page.html
```

각 폴더 수준에는 위의 표에서 분류된 것처럼 &#39;stat level&#39;이 있습니다.

| 컨텐츠(docroot) | ecommerce | 미국 | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2개 | 3 | 4 | - |

이 경우 statfilelevel 속성을 기본 &quot;0&quot;으로 설정한 상태에서 product-page.html 템플릿이 업데이트되고 무효화를 트리거하는 활성화되면 docroot에서 level 4로 모든 .stat 파일이 터치되고 파일이 무효화되어 해당 단일 변경 사항에서 사이트의 모든 페이지(다른 웹 사이트, 국가 및 언어 포함)에 대한 AEM 게시 인스턴스에서 추가 요청이 발생합니다.

그러나 statfilelevel 속성이 level 4로 설정되어 있고 product-page.html에 변경 사항이 있는 경우 해당 특정 웹 사이트/국가/언어에 대한 products 디렉토리의 .stat 파일만 터치합니다.

.stat 파일 수준은 너무 높은 수준으로 설정해서는 안 됩니다. 20을 초과하면 성능에 영향을 줄 수 있습니다. 성능 테스트를 실행하는 동안 벌크 파일 활성화를 실행하면 시작 레벨을 조정할 수 있는 정확한 수준이 제공됩니다.

상태 파일 수준을 구성할 때 최적화하는 다른 디스패처 설정은 gracePeriod 설정입니다. 마지막 활성화가 발생한 후에도 오래된 자동 무효화된 리소스가 캐시에서 계속 제공될 수 있는 시간(초)을 정의합니다. 자동 무효화된 리소스는 모든 활성화에서 무효화됩니다(해당 경로가 디스패처 /invalidate 섹션 및 statfileslevel 속성에 지정된 수준과 일치하는 경우). gracePeriod 설정을 2초로 설정하면 게시자가 새 페이지를 작성하는 중이지만 계속해서 여러 요청이 게시자에게 전송되는 시나리오를 방지하기 위해 사용할 수 있습니다.

>[!NOTE]
>
> 이 항목에 대한 자세한 내용은 [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub 리포지토리.

## CIF - 구성 요소를 통한 GraphQL 캐싱

AEM 내의 개별 구성 요소를 캐시하도록 설정할 수 있습니다. 즉, Adobe Commerce에 대한 GraphQL 요청이 한 번 호출된 다음 구성된 시간 제한까지 후속 요청이 AEM 캐시에서 검색되고 더 이상 Adobe Commerce에 로드되지 않습니다. 예를 들면 모든 페이지에 표시된 카테고리 트리를 기반으로 하는 사이트 탐색과 패싯된 검색 기능 내의 옵션을 선택할 수 있습니다. 이 두 영역은 Adobe Commerce에 리소스 집약적인 쿼리를 빌드해야 하지만 정기적으로 변경되지는 않으므로 캐싱에 적합한 선택 사항이 될 수 있습니다. 예를 들어 게시자가 PDP 또는 PLP를 다시 빌드하는 경우에도 탐색 빌드에 대한 리소스 집약적인 GraphQL 요청은 Adobe Commerce을 히트하지 않고 AEM CIF의 GraphQL 캐시에서 검색할 수 있습니다.

아래 예제는 사이트의 모든 페이지에서 동일한 GraphQL 쿼리를 전송하므로 탐색 구성 요소를 캐시하는 것입니다. 아래 요청은 탐색 구조에 대해 지난 100개의 항목을 10분 동안 캐시합니다.

```
venia/components/structure/navigation:true:100:600
```

아래 예제는 검색 페이지에서 1시간 동안 지난 100개의 면처리 검색 옵션을 캐시합니다.

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

모든 사용자 지정 http 헤더 및 변수를 포함하는 요청은 캐시가 &#39;히트&#39;이고 Adobe Commerce에 대한 반복 호출을 방지하기 위해 정확히 일치해야 합니다. 이 캐시를 수동으로 무효화하는 쉬운 방법은 한 번 설정되어 있으면 주의해야 합니다. 즉, 새 카테고리가 Adobe Commerce에 추가되는 경우 위의 캐시에서 설정된 만료 시간이 만료되고 GraphQL 요청이 새로 고쳐질 때까지 탐색에 나타나지 않습니다. 검색 패싯에도 마찬가지입니다. 그러나 이 캐싱으로 얻을 수 있는 성능 이점이 있다면 일반적으로 허용되는 타협입니다.

위의 캐싱 옵션은 &quot;GraphQL 클라이언트 구성 팩토리&quot;에서 AEM OSGi 구성 콘솔을 사용하여 설정할 수 있습니다. 각 캐시 구성 항목은 다음 형식으로 지정할 수 있습니다.

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## 하이브리드 캐싱 - 캐시된 디스패처 페이지 내의 클라이언트측 GraphQL 요청

또한 페이지의 캐싱에 대한 하이브리드 접근 방식이 가능합니다. CIF 페이지에는 항상 고객의 브라우저에서 직접 Adobe Commerce에서 최신 정보를 요청하는 구성 요소가 포함될 수 있습니다. 이 기능은 실시간 정보로 업데이트해야 하는 템플릿 내에서 페이지의 특정 영역에 유용할 수 있습니다. 예를 들어 PDP 내의 제품 가격. 동적 가격 일치로 인해 가격이 자주 변경되는 경우 디스패처에 캐시되지 않도록 해당 정보를 구성할 수 있습니다. 대신 AEM CIF 웹 구성 요소를 사용하여 GraphQL API를 통해 직접 Adobe Commerce에서 고객 브라우저에서 클라이언트 측에서 가격을 가져올 수 있습니다.

이 구성 요소는 AEM 구성 요소 설정 을 통해 구성할 수 있습니다. 제품 목록 페이지의 가격 정보에 대해서는 제품 목록 템플릿에서 구성하고, 페이지 설정에서 제품 목록 구성 요소를 선택하고 &quot;로드 가격&quot; 옵션을 선택합니다. 같은 접근 방식은 재고 수준에도 작용할 것이다.

위의 방법은 실시간, 지속적으로 최신 정보가 요구 사항인 경우에만 사용해야 합니다. 위의 가격 책정 예에서, 낮은 트래픽 시간에 매일 가격을 업데이트하고 캐시 플러시 작업을 수행하도록 비즈니스 이해 관계자와 동의를 받을 수 있습니다. 이렇게 하면 가격 정보를 표시하는 각 페이지를 작성할 때 실시간 가격 정보 요청과 Adobe Commerce에 대한 후속 추가 로드가 필요 없습니다.

## 실행 취소할 수 없는 GraphQL 요청

페이지 내의 특정 동적 데이터 구성 요소는 캐시하지 말아야 하며, 장바구니와 체크아웃 페이지 전반에 대한 호출과 같이 항상 Adobe Commerce에 GraphQL 호출이 필요합니다. 이 정보는 사용자에게만 해당되며 사이트에서의 고객 활동(예: 장바구니에 제품 추가)으로 인해 지속적으로 변경됩니다.

사이트의 디자인에서 사용자의 역할에 따라 다른 응답을 제공하는 경우 로그인한 고객에 대해 GraphQL 쿼리 결과를 캐시하지 않아야 합니다. 예를 들어, 여러 고객 그룹을 만들고, 각 그룹에 대해 서로 다른 제품 가격이나 다른 제품 카테고리 가시성을 설정할 수 있습니다. 이러한 결과를 캐시하면 고객이 다른 고객 그룹의 가격을 보거나 잘못된 카테고리가 표시될 수 있습니다.

## AEM Dispatcher 캐시에서 추적 매개 변수 무시

전자 상거래 사이트는 PPC 검색 광고 또는 소셜 미디어 캠페인을 사용하여 사이트 트래픽을 유도할 수 있습니다.

이러한 매체를 사용하면 추적 ID가 해당 플랫폼의 아웃바운드 링크에 추가되는 것을 의미합니다. 예를 들어 Facebook은 URL에 Facebook 클릭 ID(fbclid)를 추가하고, Google Advertisers는 Google 클릭 ID(gclid)를 추가하며, 이렇게 하면 AEM 프론트먼트에 대한 수신 링크가 다음과 같이 표시됩니다.

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

광고 및 클립은 광고를 클릭하는 모든 사용자에 따라 변경되며, 이것은 추적 목적으로 작성되지만, 기본 설정을 사용하면 AEM에서 모든 요청을 고유한 페이지로 볼 수 있으므로 디스패처를 무시하고 게시자 및 Adobe Commerce에 불필요한 추가 로드를 생성합니다.

서지 이벤트 중에 이로 인해 AEM 게시자가 오버로드되고 응답하지 않을 수도 있습니다. 페이지에 대해 매개 변수를 무시하도록 설정하면 페이지가 처음 요청될 때 페이지가 캐시됩니다. 페이지에 대한 후속 요청은 요청에 있는 매개 변수의 값에 관계없이 캐시된 페이지에 제공됩니다.

>[!NOTE]
>
>설정의 중요도에 대한 추가 읽기 `ignoreUrlParams` 다음에서 사용 가능합니다. [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub 리포지토리.

따라서 페이지의 HTML 구조를 변경하는 GET 매개 변수를 사용하는 경우를 제외하고 &quot;ignoreUrlParams&quot;에서 기본적으로 모든 매개 변수를 무시하도록 구성해야 합니다. 예로는 검색어가 URL을 GET 매개 변수로 하는 검색 페이지가 있습니다. 이 경우 gclid, fbclid 및 광고 채널이 사용하는 기타 모든 추적 매개 변수와 같은 매개 변수를 무시하도록 ignoreUrlParams 를 수동으로 구성하여 일반적인 사이트 작업에 필요한 GET 매개 변수는 영향을 받지 않습니다.

## MPM 작업자는 디스패처에 대해 제한

MPM 작업자 설정은 Dispatcher의 사용 가능한 CPU와 RAM을 기반으로 최적화하기 위해 철저한 테스트가 필요한 고급 Apache HTTP 서버 구성입니다. 그러나 이 백서의 범위에서는 ServerLimit 및 MaxRequestWorkers를 서버의 사용 가능한 CPU 및 RAM이 지원하는 수준으로 늘린 다음 MinSpareThreads 및 MaxSpareThreads를 MaxRequestWorkers와 일치하는 수준으로 늘리는 것이 좋습니다.

이 구성에서는 Apache HTTP를 &quot;전체 준비 설정&quot;에 둡니다. 이 설정은 상당한 RAM과 여러 CPU 코어를 사용하는 서버에 대한 고성능 구성입니다. 이 구성은 요청을 처리할 수 있는 영구 열린 연결을 유지하여 Apache HTTP에서 가능한 최상의 응답 시간을 생성하며, 플래시 판매 중과 같이 갑작스런 트래픽 정지에 응답하여 새로운 프로세스를 생성하는 데 지연을 제거하게 됩니다.
