---
title: Varnish 구성 및 사용
description: Varnish가 파일을 저장하고 HTTP 트래픽을 향상시키는 방법을 이해합니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# 바니쉬 구성

[Varnish 캐시] 은 오픈 소스 웹 응용 프로그램 가속기( _HTTP 가속기_ 또는 _HTTP 역방향 프록시 캐싱_). Varnish는 파일 또는 파일 조각을 메모리에 저장(또는 캐시)하여 Varnish가 나중에 해당하는 요청에 대해 응답 시간 및 네트워크 대역폭 사용을 줄일 수 있도록 합니다. Apache 및 nginx와 같은 웹 서버와는 달리, Varnish는 HTTP 프로토콜에서만 사용하도록 설계되었습니다.

Commerce 2.4.2는 Varnish 6.4에서 테스트됩니다. Commerce 2.4.x는 Varnish 6.x와 호환됩니다

>[!WARNING]
>
>We _강력한 추천_ 프로덕션에서 바르니스를 사용하시면 됩니다 기본 제공 전체 페이지 캐싱 - 파일 시스템 또는 [데이터베이스]- Varnish보다 훨씬 느립니다. Varnish는 HTTP 트래픽을 가속하도록 설계되었습니다.

Varnish에 대한 자세한 내용은 다음을 참조하십시오.

- [큰 바니쉬 그림]
- [변형 시작 옵션]
- [Varnish 및 웹 사이트 성능]

## 니쉬 토폴로지 다이어그램

다음 그림은 상거래 토폴로지의 Varnish에 대한 기본 보기를 보여 줍니다.

![기본 변명 다이어그램](../../assets/configuration/varnish-basic.png)

앞의 그림에서 인터넷을 통한 사용자의 HTTP 요청은 CSS, HTML, JavaScript 및 이미지(집합적으로 라고 함)에 대한 요청이 많습니다 _assets_). Varnish는 웹 서버 앞에 있고 웹 서버에 이러한 요청을 프록시합니다.

웹 서버가 자산을 반환하면 캐시 가능한 자산이 Varnish에 저장됩니다. 이러한 자산에 대한 후속 요청은 Varnish에 의해 이행됩니다(즉, 요청이 웹 서버에 도달하지 않음). Varnish는 캐시된 컨텐츠를 매우 빠르게 반환합니다. 따라서 사용자에게 콘텐츠를 반환하기 위한 응답 시간이 빨라지고 상거래를 통해 충족해야 하는 요청 수가 줄어듭니다.

Varnish로 캐시된 자산은 구성 가능한 간격으로 만료되거나, 동일한 자산의 최신 버전으로 대체됩니다. 또는 [관리](https://glossary.magento.com/magento-admin) 또는 [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) 명령.

## 프로세스 개요

이 항목에서는 최소한의 매개 변수 세트를 사용하여 Varnish를 처음 설치하고 이를 테스트하는 방법을 설명합니다. 그런 다음 상거래 관리자에서 Varnish 구성을 내보내고 다시 테스트합니다.

프로세스는 다음과 같이 요약할 수 있습니다.

1. Varnish를 설치하고 Commerce 페이지에 액세스하여 Varnish가 작동하고 있음을 나타내는 HTTP 응답 헤더를 받고 있는지 테스트합니다.
1. 상거래 소프트웨어를 설치하고 관리자를 사용하여 Varnish 구성 파일을 만듭니다.
1. 기존 Varnish 구성 파일을 관리자가 생성한 파일로 바꿉니다.
1. 모든 것을 다시 테스트합니다.

   네 안에 아무것도 없으면 `<magento_root>/var/page_cache` 디렉터리, Varnish를 Commerce와 구성했습니다!

>[!NOTE]
- 언급된 경우를 제외하고 이 항목에 설명된 모든 명령을 사용자가 사용할 수 있도록 입력해야 합니다 `root` 권한.
- 이 항목은 CentOS와 Apache 2.4의 Varnish에 대해 작성됩니다. 다른 환경에서 Varnish를 설정하는 경우 일부 명령이 다를 수 있습니다. 자세한 내용은 Varnish 설명서 를 참조하십시오.


## 알려진 문제

Varnish와 관련된 다음 문제를 알고 있습니다.

- [Varnish는 SSL을 지원하지 않습니다]

   또는 SSL 종료 또는 SSL 종료 프록시를 사용합니다.

- 수동으로 `<magento_root>/var/cache` 디렉토리, Varnish를 다시 시작해야 합니다.

- 상거래 설치 오류:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   이 오류가 발생하는 경우 다음을 편집합니다. `default.vcl` 시간 초과를 `backend` stanza는 다음과 같습니다.

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Varnish 캐싱 개요

Varnish 캐싱은 다음을 사용하여 Commerce에서 작동합니다.

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) Magento 2 GitHub 저장소에서
- `.htaccess` 상거래와 함께 제공된 Apache용 분산 구성 파일
- `default.vcl` Varnish를 사용하여 생성된 [관리](../cache/config-varnish-magento.md)

>[!INFO]
이 주제에서는 이전 목록의 기본 옵션만 다룹니다. 복잡한 시나리오에서 캐싱을 구성하는 다른 여러 가지 방법이 있습니다(예: 콘텐츠 전달 네트워크 사용). 이러한 메서드는 이 안내서의 범위를 벗어납니다.

첫 번째 브라우저 요청에서 캐시 가능한 자산은 Varnish에서 클라이언트 브라우저에 전달되고 브라우저에서 캐시됩니다.

또한 Varnish는 [엔티티](https://glossary.magento.com/entity) 정적 자산에 대한 태그(ETag)입니다. ETag는 [정적 파일](https://glossary.magento.com/static-files) 서버에서 변경합니다. 따라서 정적 자산은 서버에서 변경될 때 클라이언트로 전송됩니다. 새로운 브라우저에서 요청하거나 클라이언트가 브라우저 캐시를 새로 고칠 때, 일반적으로 F5 또는 Control+F5를 눌러 전송합니다.

자세한 내용은 다음에 나오는 섹션에서 제공됩니다.

## 브라우저 요청별 캐싱

이 섹션에서는 브라우저 검사기를 사용하여 첫 번째 요청에서 그리고 나중에 로컬 브라우저 캐시에서 로드되는 방식으로 자산이 브라우저에 전달되는 방식을 표시합니다.

### 첫 번째 브라우저 요청

`nginx.conf.sample` 및 `.htaccess` 클라이언트 캐싱에 대한 옵션을 제공합니다. 브라우저에서 캐시 가능한 개체에 대해 첫 번째 요청을 수행하면 Varnish가 이를 클라이언트에 전달합니다.

다음 그림은 브라우저 관리자를 사용하는 예를 보여줍니다.

![캐시 가능한 개체에 대해 처음으로 요청이 수행된 경우, Varnish는 이를 브라우저로 전달합니다](../../assets/configuration/varnish-apache-first-visit.png)

앞의 예는 storfront 주 페이지에 대한 요청을 보여줍니다(`m2_ce_my`). CSS 및 JavaScript 자산은 클라이언트 브라우저에서 캐시됩니다.

>[!NOTE]
대부분의 정적 자산에는 서버에서 자산이 검색되었음을 나타내는 HTTP 200(OK) 상태 코드가 있습니다.

### 두 번째 브라우저 요청

동일한 브라우저가 동일한 페이지를 다시 요청하는 경우 다음 그림과 같이 이러한 자산은 로컬 브라우저 캐시에서 전달됩니다.

![다음에 동일한 개체가 요청되면 로컬 브라우저 캐시에서 자산이 로드됩니다](../../assets/configuration/varnish-apache-second-visit.png)

첫 번째 요청과 두 번째 요청 간의 응답 시간의 차이를 확인합니다. 다시 말하지만, 정적 자산에는 로컬 캐시에서 처음 전달되므로 200(OK) 응답 코드가 있습니다.

## Commerce에서 Tag를 사용하는 방법

다음 예는 특정 정적 자산에 대한 응답 헤더를 보여줍니다.

![ETag를 사용하면 정적 자산이 변경되었는지 여부를 쉽게 확인할 수 있습니다](../../assets/configuration/varnish-etag.png)

`calendar.css` 에는 클라이언트 브라우저의 CSS 파일을 서버의 CSS와 비교할 수 있는 ETag 응답 헤더가 있습니다.

또한 다음 그림과 같이 정적 자산이 304(수정되지 않음) HTTP 상태 코드와 함께 반환됩니다.

![HTTP 304(수정되지 않음) 응답 코드는 로컬 캐시의 정적 자산이 서버의 정적 자산과 동일함을 나타냅니다](../../assets/configuration/varnish-304.png)

사용자가 로컬 캐시를 무효화하고 서버의 콘텐츠가 변경되지 않았기 때문에 304 상태 코드가 발생합니다. 304 상태 코드 때문에 정적 자산 _콘텐츠_ 는 전송되지 않습니다. HTTP 헤더만 브라우저에 다운로드됩니다.

서버에서 컨텐츠가 변경되면 클라이언트는 HTTP 200 (OK) 상태 코드와 새 ETag를 사용하여 정적 자산을 다운로드합니다.

<!-- Link Definitions -->

[데이터베이스]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/cache/partial-caching/database-caching.html
[큰 바니쉬 그림]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Varnish 캐시]: https://varnish-cache.org
[변형 시작 옵션]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Varnish 및 웹 사이트 성능]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish는 SSL을 지원하지 않습니다]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
