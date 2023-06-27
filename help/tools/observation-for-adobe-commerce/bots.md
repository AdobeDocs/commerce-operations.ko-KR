---
title: 다음 [!UICONTROL bots] 탭
description: 에 대해 알아보기 [!UICONTROL bots] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---

# 다음 [!UICONTROL bots] 탭

이 탭에는 해당 여부와 항목을 식별하는 방법을 설명하는 정보가 있습니다 [!DNL bots] 은(는) 사이트 문제를 야기합니다.

## 의 높은 수준 개요 [!DNL bots]:

* A [!DNL bot] 는 반복적인 자동화된 작업을 실행하는 소프트웨어의 일부입니다. 인공 지능과 머신 러닝의 진화, 작업, 방법 및 상호 작용 [!DNL bots] 바뀌고 있어요 다음 항목이 있습니다. *양호* [!DNL bots] 이는 크롤링하여 인터넷 검색 엔진에 추가함으로써 사이트에 도움이 됩니다. 그 결과 인터넷 사용자는 검색 엔진 결과를 통해 사이트로 이동할 수 있습니다. A *양호* [!DNL bot] 일반적으로 다음에 배치된 경계를 준수합니다 [!DNL bot] 작성자: `robots.txt` 검색 엔진 콘솔의 파일 또는 설정. 경계는 사이트 또는 사이트 일부에 대한 액세스를 제한할 수 있습니다.
* 악의적 [!DNL bots] 무시 `robots.txt` 화환이나 또는 상품을 팔기도 한다 [!DNL bot] HTTP 요청 데이터의 요청 사용자 에이전트 필드를 통해 액세스합니다. 악의적인 것들 [!DNL bots] 수행:
   * 사이트에 대한 정당한 사용자 액세스를 거부하기 위해 사이트에 로드를 추가합니다.
   * 권한 없이 콘텐츠를 스크랩하고 재사용할 수 있습니다.
   * 이메일 서비스 또는 주소를 플러드하거나 다른 사이트로 리디렉션할 가짜 계정을 등록합니다([!DNL SPAM bots]).
   * 가짜 보기 만들기([!DNL Viewbots]).
   * 제품 또는 티켓 구매([!DNL Focused bots]).
* 관리 [!DNL bots]
   * [!DNL Observation for Adobe Commerce] 의 조회수 있음 [!DNL bot] 트래픽:
      * 캐시되지 않은 총 수가 표시됩니다. [!DNL bot] 에 대한 로드를 표시하는 활동 [!DNL bot] 가 사이트에 추가되고 해당 로드가 발생하는 경우입니다.
      * 다음을 표시합니다. [!DNL bots] 오류를 생성하고 있습니다. 일반적으로 [!DNL bot] 은(는) 사이트 문제를 일으키는 로드를 추가하고 있습니다. [!DNL bot] 또는 IP 주소가 오류 빈도가 가장 높습니다.
      * 다음을 표시합니다. [!DNL bot] 다음을 통해 관리할 이름(사용자 에이전트 필드 값 요청) 및 IP 주소:
         * [!DNL Fastly] (속도 제한 또는 [!DNL VCLs] IP 주소, 범위 또는 [!DNL bots] 이름 값 기준).
         * 양호 추가 [!DNL bot] 에 대한 정보 `robots.txt field` 사이트 액세스 속도를 제한하거나 제한합니다.
         * 관리 [!DNL Bing] 또는 [!DNL Google bots] 검색 엔진 콘솔을 통해.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![실험적 잠재적 악성 보트 프레임](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

다음 **[!UICONTROL Experimental Potential Malicious Bots frame]** 프레임은 12개 이상의 복잡한 별도 쿼리를 실행합니다. 악의적인 IP 요청 서명을 감지한 다음, 결과를 집계하여 내림차순으로 집계하여 정렬합니다. 쿼리에는 CVE 악용 및 기타 악의적인 요청의 많은 데이터 서명이 포함되어 있습니다. 보안 수정/패치에 의해 악용이 차단되고 사이트에 위협이 되지 않는 경우에도, 요청은 여전히 웹 사이트에서 처리해야 합니다. 짧은 기간 내에 요청의 양이 상당히 커질 수 있습니다. 이 프레임에는 IP 주소의 총 요청이 표시되지 않고, 요청에 의심스러운 의도가 있음을 나타내는 신호가 있는 요청이 표시됩니다.

트래픽이 의심스러우며 다음에서 발생하지 않는지 확인하십시오. [!DNL Content Distributed Network] (CDN) 유효한 요청을 전달할 수도 있는 주소입니다. 요청이 CDN IP 주소에서 발송된 것으로 확인되면 해당 서비스 공급업체에 연락하여 네트워크를 통한 의심스러운 트래픽 차단을 도와주십시오. 주소 또는 요청 URL을 차단해야 하는 경우 다음을 참조하십시오. [에서 Adobe Commerce에 대한 악성 트래픽 차단 [!DNL Fastly] 수준](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) Adobe Commerce 지원 기술 자료에서 참조할 수 있습니다.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![요청된 기간 동안의 초당 HTTP 요청 비율(상위 25개)](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

다음 **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** 프레임은 선택한 기간 동안 초당 가장 높은 IP 주소 요청을 표시합니다. 이러한 주소도 위 표에 있으면 CDN 주소 및 악의적인 주소가 아닌지 확인하고 를 통해 차단합니다. [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![선택한 기간 동안의 보트 이름별 총 보트 트래픽:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

다음 **[!UICONTROL Total Bot traffic by bot name during selected time period]** 테이블에는 캐시되지 않은 요청의 집계된 수가 들어 있습니다. 여기서 [!UICONTROL request_user_agent] 필드에는 다음 문자열이 있습니다. [!DNL bots] 을 입력합니다. 이는 이라는 이름일 수도 있고 아닐 수도 있습니다. [!DNL bot] (으)로 [!UICONTROL request_user_agent] 필드 값은 스푸핑될 수 있습니다. 아래 값 [!UICONTROL Count] 열이 가장 중요합니다.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![선택한 기간 동안 보트 이름/IP 주소별 총 보트 트래픽 Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

다음 **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 이 표에서는 이전 테이블과 동일한 데이터를 보여주지만, 이름이 인 을 대신하여 요청을 수행하는 IP 주소를 추가합니다 [!DNL bot]. 악의적으로 [!DNL bots] 좋은 것 [!DNL bots], IP 주소는 모욕적인 IP 주소를 식별하는 웹 사이트 또는 를 통해 확인해야 합니다. *후이스* 서비스 또는 [!DNL DNS lookups]. 예를 들어, [!DNL Google] 게시 [[!DNL googlebot] IP 주소](https://developers.google.com/search/apis/ipranges/googlebot.json) 및 [!DNL Microsoft] 다음 항목에 대한 확인 도구가 있습니다. [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![그래프 - 선택한 기간 동안 HTTP 상태 오류가 발생한 보트 Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

다음 **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 그래프는에 오류를 표시합니다. [!DNL bots] 요청 사용자 에이전트 필드에 자신을 선언합니다. 이것은 오차가 반드시 의 부피에 의해 발생한다는 것을 의미하지는 않는다. [!DNL bot] 또는 기타 트래픽. 오류는 다음과 같습니다. [!DNL bot] 은(는) 존재하지 않는 정보를 요청하거나 요청에 다른 문제가 있습니다.

사이트 불안정 또는 중단 중에 IP 주소에 오류가 급증하는 경우 사이트 문제가 의심될 수 있습니다.

## [!UICONTROL Table - IPs that do not identify as bots]

![표 - 선택한 기간 동안 HTTP 상태 오류가 있는 보트로 식별되지 않는 IP Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례 ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

다음 **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 표에는 자체 식별되지 않는 200개가 아닌 http 상태 코드가 있는 IP 요청이 다음과 같이 표시됩니다. [!DNL bots] 사용자 에이전트 요청 필드에서 다음을 수행합니다. 이러한 IP 주소는 특히 선택한 기간 동안 횟수가 많은 경우 악의적인 IP 주소일 수 있습니다.

200개가 아닌 http 상태 코드 수가 적고 IP 주소 범위가 유사하지 않으면 주소가 사이트 문제에 기여하지 않을 수 있습니다.

## [!UICONTROL Table – Cache Status 'ERROR']

![표 - 캐시 상태 &#39;오류&#39; 세부 정보 표(이들 IP가 수행하는 작업) Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt 모범 사례](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

IP 주소에서 오류가 자주 발생하는 경우 어떻게 하는지 묻습니다. 다음 **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 이 표에서는 캐시 상태가 있는 요청에 대해 요청된 URL과 HTTP 상태 값을 보여 줍니다 [!UICONTROL ERROR] 값. 빈도는 URL로 대체되므로 카운트가 낮을 수 있습니다. IP 주소는 선택한 기간 동안 수천 개의 요청을 수행할 수 있습니다. 일정 기간(레코드 표시 제한) 동안 최대 2000개의 요청에 대한 보기입니다.

## [!UICONTROL Show 5XX status distribution]

![IP 주소(상위 200개 주소) 전반에 걸친 5XX 상태 배포 표시 Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례 ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

다음 **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임은 강력합니다. 선택한 기간 동안 5XX http 상태 코드가 있는 IP 주소를 표시합니다. IP 주소가 많은 양의 요청을 하고 사이트가 트래픽을 처리할 수 없는 지점까지 영향을 받는 경우 요청 빈도가 가장 높은 IP 주소는 일반적으로 가장 높은 오류 볼륨을 갖게 됩니다. 5XX http 상태 코드는 일반적으로 요청에 응답하기 어려운 사이트를 나타냅니다.

막대가 넓을수록 해당 기간 동안의 총 5xx 오류 수에서 IP 주소에 있는 오류의 %가 커집니다. 참고: IP 주소에 HTTP 상태 코드가 여러 개 있는 경우(예: 502 및 503 HTTP 상태) 그래프에 여러 세그먼트가 있을 수 있습니다.

일반적인 분포는 IP 주소의 너비가 동일하거나 개수가 매우 적은 넓은 막대가 몇 개 있는 막대의 오른쪽에 표시됩니다.

바 세그먼트 위로 마우스를 가져가면 선택한 기간 동안 표시된 오류 수가 표시됩니다.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![선택한 기간 동안 IP 캐시 상태(MISS, PASS, ERROR) 및 HTTP 상태 Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 우수 사례](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

이 **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame은 선택한 기간 동안 IP별로 HTTPS 상태 코드 카운트 및 캐시되지 않은 요청을 표시합니다. 이는 각 IP 주소와 총 볼륨의 비례 로드를 나타냅니다. 요청이 가장 많은 IP 주소를 표시합니다.

## [!UICONTROL Fastly Cache Summary for selected time period]

![선택한 기간에 대한 Fastly 캐시 요약](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

다음을 클릭하면 [!UICONTROL Error] 아이콘 아래 그래프에서 마지막 두 그래프를 서로 비교할 수 있습니다. 이렇게 하면 로드가 사이트 문제에 기여하는 위치를 표시하는 데 도움이 될 수 있습니다.

![Fastly 오류 검사](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![선택한 기간 동안 오류 없이 보트로 식별되지 않는 IP Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

다음 **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임에는 요청 사용자 에이전트 필드, IP 주소 및 요청 사용자 에이전트 필드가 을 표시하지 않는 요청에 대한 상태 코드가 표시됩니다. [!DNL bot]. 이 프레임은 모든 IP 주소에서 고주파 요청을 표시할 수 있지만 특히 사이트에 문제가 있을 수 있는 기간 동안 고주파 요청에 주의를 기울입니다.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![선택한 기간 동안 의심스러운 비봇 트래픽](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

다음 **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** graph에서 Go-http-client의 요청 사용자 에이전트 값을 검색하지만 다른 의심되는 요청 사용자 에이전트 값을 확인하기 위해 확장됩니다. 이 요청 사용자 에이전트 값은 서비스에서 연결하기 위해 사이트에서 사용되며 유효할 수 있지만 악의적으로도 사용됩니다 [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![그래프 - 선택한 기간 동안의 보트 이름별 보트 트래픽)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

다음 **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** 프레임은 의 총 보트 트래픽과 동일한 데이터를 보여 줍니다. [!DNL Bot] 탭 상단의 선택된 기간 테이블 이름. 은(는) 타임라인을 통해 데이터를 표시하므로 을(를) 통한 요청 시점을 확인할 수 있습니다. [!DNL bots] 제작 및 배포가 진행 중입니다.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![선택한 기간 동안 상위 250개 보트 이름 및 IP 주소 Fastly 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt에 대한 모범 사례](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

다음 **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임이 합계와 동일한 데이터를 표시합니다. [!DNL Bot] 탭 상단의 선택한 기간 테이블 동안 보트 이름/IP 주소별 트래픽. 해당 데이터는 타임라인을 통해 표시되며 IP 주소별로 표시됩니다. 에 의한 요청 시간을 표시합니다. [!DNL bots] 만들어짐, 요청을 하는 IP 및 요청 배포.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![선택한 기간 동안 차단된 보트 이름/IP 주소(Fastly)입니다. 이 그래프는 403 금지된 HTTP 상태 코드가 반환되는 봇 트래픽 및 IP를 표시합니다](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

다음 **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** 프레임은 차단된 보트 이름과 IP 주소를 보여 줍니다. 이 그래프에서 모든 요청이 차단된 방식을 확인할 수 있습니다. [!DNL Fastly] 앞으로 나아갑니다.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![선택한 기간 동안 봇이 아닌 이름/IP 주소(Fastly)를 차단했습니다. 이 그래프는 403 금지 HTTP 상태 코드가 반환된 비봇 트래픽 및 IP를 표시합니다 ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

다음 **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** 프레임에는 로 식별되지 않는 IP 주소가 표시됩니다. [!DNL bot] 다음을 통해 차단됨: [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![이 표에서는 IP 주소당 사용자 에이전트 수, 성공, 실패 및 차단된 요청 수를 보여 줍니다.](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

악의적 [!DNL bots] 기타 스푸핑 [!DNL bots] 을 통해 [!UICONTROL Request User Agent] 필드. 이 표에서는 해당 필드에 IP 주소가 갖는 고유 값 수를 보여 줍니다. 의 값이 높을수록 [!UICONTROL Request User Agent] 필드에서는 IP 주소가 더 의심스럽습니다.

## [!UICONTROL IP with non-200 status errors]

![200개 이외의 상태 오류가 있는 IP - 403 상태 제외](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

다음 **[!UICONTROL IP with non-200 status errors – without 403 status]** 프레임은 200개가 아닌 HTTP 상태 코드와 함께 선택한 IP 주소 일정에 따른 분포를 보여 줍니다. 단일 IP 또는 IP 주소 그룹에서 더 높은 값이 표시되면 추가 조사가 필요합니다.

## [!UICONTROL IP with 403 status codes:]

![403 상태 코드가 있는 IP:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

다음 **[!UICONTROL IP with 403 status codes]** 프레임에 캐시되지 않은 요청이 [!UICONTROL cache_status=ERROR] 에 403 HTTP 상태가 있습니다. 이는 원본 서버가 의 블록이 아닌 403(인증되지 않음)의 소스임을 보여줄 수 있습니다. [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![cache_status를 표시하는 200개 이외의 상태 코드가 있는 상위 5개:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

다음 **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** 이 테이블은 IP/상태 수준에서 를 사용하는 각 의 수를 보여 줍니다. [!UICONTROL cache_status] 값.

## [!UICONTROL Pageview Latency will show as spikes]

![페이지 보기 대기 시간은 이 그래프에서 스파이크로 표시됩니다.](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

다음 **[!UICONTROL Pageview Latency will show as spikes on this graph:]** 프레임은 과 일치할 수 있는 페이지 로드/API 응답 지연을 보여 줍니다. [!DNL bot] 트래픽.
