---
title: "다음 [!UICONTROL bots] tab"
description: 에 대해 알아보기 [!UICONTROL bots] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: 6523372cd5fe3219dc582123471cc85f3c47f37d
workflow-type: tm+mt
source-wordcount: '1649'
ht-degree: 0%

---

# 다음 [!UICONTROL bots] 탭

이 탭에는 ID와 ID를 식별하는 방법과 그 내용을 설명하는 정보가 있습니다 [!DNL bots] 사이트 문제를 일으키고 있습니다.

## 의 개요 [!DNL bots]:

* A [!DNL bot] 는 반복적인 자동화 작업을 실행하는 소프트웨어 부분입니다. 인공 지능과 머신 러닝 진화를 통해 [!DNL bots] 변경 중입니다. 있습니다 *좋은* [!DNL bots] 그것은 인터넷 검색 엔진에 그것들을 크롤링하여 추가함으로써 사이트를 이롭게 합니다. 따라서 검색 엔진 결과를 통해 인터넷 사용자가 사이트로 안내됩니다. A *좋은* [!DNL bot] 일반적으로 경계를 따릅니다 [!DNL bot] 기준 `robots.txt` 검색 엔진 콘솔의 파일 또는 설정. 경계는 사이트 또는 사이트 부분에 대한 액세스를 제한할 수 있습니다.
* 악성 [!DNL bots] 무시 `robots.txt` 파일을 보관하거나 또는 좋은 [!DNL bot] http 요청 데이터의 요청 사용자 에이전트 필드를 통해. 악의적으로 [!DNL bots] 작업:
   * 사이트에 로드를 추가하여 합법적인 사용자가 사이트에 액세스할 수 없도록 합니다.
   * 권한 없이 컨텐츠를 긁고 재사용합니다.
   * 가짜 계정을 등록하여 이메일 서비스 또는 주소를 사용하거나 다른 사이트로 리디렉션합니다([!DNL SPAM bots]).
   * 가짜 보기 만들기([!DNL Viewbots]).
   * 제품 또는 티켓 구입([!DNL Focused bots]).
* 관리 [!DNL bots]
   * [!DNL Observation for Adobe Commerce] 의 [!DNL bot] 트래픽:
      * 총 캐시되지 않은 항목이 표시됩니다 [!DNL bot] 활동: [!DNL bot] 가 사이트에 추가되고, 언제 해당 로드가 발생하고 있는지 확인합니다.
      * 다음 내용이 표시됩니다. [!DNL bots] 오류가 발생합니다. 일반적으로 [!DNL bot] 사이트 문제를 일으키는 로드를 추가하는 중입니다. [!DNL bot] 또는 IP 주소의 오류 빈도는 가장 높습니다.
      * 이건 [!DNL bot] 이름(사용자 에이전트 필드 값 요청) 및 관리할 IP 주소:
         * [!DNL Fastly] (속도 제한 또는 [!DNL VCLs] IP 주소, 범위 또는 [!DNL bots] 이름 값 기준).
         * 추가 기능 [!DNL bot] 에 대한 정보 `robots.txt field` 를 클릭하거나 탭합니다.
         * 관리 [!DNL Bing] 또는 [!DNL Google bots] 검색 엔진 콘솔 사용.

## [!UICONTROL Total Bot traffic by bot name during selected time period]:

![선택한 기간 동안 보트 이름별 총 보트 트래픽:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

* 다음 **[!UICONTROL Total Bot traffic by bot name during selected time period]:** 변수에는 [!UICONTROL request_user_agent] 필드에 문자열 가 있습니다. [!DNL bots] 참조하십시오. 이름이 지정되었거나 지정되지 않을 수 있습니다. [!DNL bot] 로서의 [!UICONTROL request_user_agent] 필드 값을 스푸핑할 수 있습니다. 다음 아래의 값 [!UICONTROL Count] 열이 가장 중요합니다.

## [!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![선택한 기간 동안 보트 이름/IP 주소별 총 보트 트래픽 실제 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

* 다음 **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 테이블은 이전 테이블과 동일한 데이터를 표시하지만, 지정된 이름을 대신하여 요청을 수행하는 IP 주소를 추가합니다 [!DNL bot]. 악의적으로 [!DNL bots] 좋은 [!DNL bots]또는 IP 주소는 악성 IP 주소를 식별하는 웹 사이트를 통해 또는 *whoo* 서비스 또는 [!DNL DNS lookups]. 예, [!DNL Google] 게시 [[!DNL googlebot] IP 주소](https://developers.google.com/search/apis/ipranges/googlebot.json) 및 [!DNL Microsoft] 에 대한 확인 도구가 있습니다. [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![그래프 - 선택한 기간 동안 HTTP 상태 오류가 발생한 보트 실제 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

* 다음 **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 그래프에 오류가 표시됩니다. [!DNL bots] 요청 사용자 에이전트 필드에 자신을 선언합니다. 이는 반드시 오류가 [!DNL bot] 또는 기타 트래픽. 오류는 [!DNL bot] 가 존재하지 않거나 요청에 다른 문제가 있는 정보를 요청하고 있습니다.
* 사이트 불안정이나 중단 중 IP 주소에 오류가 급증하면 사이트 문제의 용의자일 수 있습니다.

## [!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![테이블 - 선택한 기간 동안 HTTP 상태 오류가 있는 보트로 식별되지 않는 IP 실제 수준에서 보트 트래픽을 차단하거나 로봇을 통해 보트를 관리하는 방법.txt 파일 Adobe Commerce robots.txt에 대한 우수 사례 ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

* 다음 **[!UICONTROL Table - IPs that do not identify as [!DNL bots] with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 표는 자체 식별되지 않는 HTTP 상태 코드가 200개가 아닌 IP 요청을 표시합니다 [!DNL bots] 사용자 에이전트 요청 필드에서 을 클릭합니다. 이러한 IP 주소는 특히 선택한 기간 동안 카운트가 많은 경우 악의적인 IP 주소일 수 있습니다.
* 200개가 아닌 http 상태 코드 카운트가 낮고 IP 주소 범위가 유사하지 않으면 주소가 사이트 문제에 기여하지 않을 수 있습니다.

## [!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![테이블 - 캐시 상태 &#39;ERROR&#39; 세부 정보 테이블(이러한 IP가 수행하는 작업) robots.txt 파일을 통해 실제 수준 OR에서 보트 트래픽을 차단하는 방법 Adobe Commerce robots.txt를 위한 우수 사례](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

* IP 주소가 높은 오류 빈도를 생성하는 경우 IP 주소가 어떻게 작동하는지 묻습니다. 다음 [!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt] 테이블은 캐시 상태가 있는 요청에 대한 HTTP 상태 값과 함께 요청된 URL을 표시합니다 [!UICONTROL ERROR] 값. 빈도는 URL별로 면처리되므로 개수가 적을 수 있습니다. 선택한 기간 동안 IP 주소가 수천 개의 요청을 수행할 수 있습니다. 이는 기간(레코드 표시 제한) 동안 최대 2,000개의 요청에 대한 보기입니다.

## [!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![IP 주소에 대한 5XX 상태 배포 표시(상위 200개 주소) 실제 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

* 다음 **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임은 강력합니다. 선택한 기간 동안 5XX http 상태 코드가 있는 IP 주소가 표시됩니다. IP 주소가 요청을 대량으로 처리하고 사이트가 트래픽을 처리할 수 없는 지점에 영향을 받는 경우 요청 빈도를 가장 많이 하는 IP 주소는 일반적으로 가장 많은 오류 볼륨을 발생시킵니다. 5XX http 상태 코드는 일반적으로 요청에 응답하기 위해 노력하고 있는 사이트를 나타냅니다.
* 막대가 넓을수록 IP 주소가 오류가 발생하는 오류의 비율이 해당 기간 동안 총 5xx 오류 수로 커집니다. 참고: IP 주소에 여러 http 상태 코드(예: 502 및 503 http 상태)가 있는 경우 그래프에 여러 개의 세그먼트가 있을 수 있습니다.
* 일반적인 배포는 IP 주소가 너비가 동일하거나 수가 매우 적은 몇 개의 넓은 막대가 있는 막대의 오른쪽에 표시됩니다.
* 마우스로 막대 세그먼트를 가리키면 선택한 기간 동안 표시된 오류 수가 표시됩니다.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![선택한 기간 동안의 IP 캐시 상태(MISS, PASS, ERROR) 및 http 상태 보트 트래픽을 실제 수준에서 차단하거나 로봇을 통해 보트를 관리하는 방법.txt 파일 Adobe Commerce robots에 대한 우수 사례.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

* 이 **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임은 선택한 기간 동안 IP별로 HTTPS 상태 코드 카운트와 캐시되지 않은 요청을 표시합니다. 이는 각 IP 주소에서 발생하는 비례적 로드와 총 볼륨을 나타냅니다. 요청이 가장 많은 IP 주소를 표시합니다.

## [!UICONTROL Fastly Cache Summary for selected time period]

![선택한 기간에 대한 캐시 요약](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

* 을(를) 클릭하면 [!UICONTROL Error] 아래 그래프에서 아이콘을 사용하여 마지막 두 그래프를 서로 비교할 수 있습니다. 이렇게 하면 로드가 사이트 문제에 기여하는 위치를 나타낼 수 있습니다.

![오류 검사](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![선택한 기간 동안 오류가 없이 보트로 식별되지 않는 IP 실제 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

* 다음 **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임은 요청 사용자 에이전트 필드, IP 주소 및 요청 사용자 에이전트 필드가 [!DNL bot]. 이 프레임은 IP 주소에서 높은 빈도 요청을 표시할 수 있지만 특히 사이트에 문제가 발생할 수 있는 기간 동안 높은 빈도 요청에 유의하십시오.

## [!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]

![선택한 기간 동안 의심스러운 비보트 트래픽](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

* 다음 **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** 그래프는 Go-http-client의 요청 사용자 에이전트 값을 찾지만 다른 의심스러운 요청 사용자 에이전트 값을 보기 위해 확장됩니다. 이 요청 사용자 에이전트 값은 사이트에서 서비스에서 서비스를 연결하는 데 사용되며 유효하지만 악의적인 사용이기도 합니다 [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name during selected time period]

![그래프 - 선택한 기간 동안 보트 이름별 보트 트래픽)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

* 다음 **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** 프레임은 다음의 총 보트 트래픽과 동일한 데이터를 표시합니다 [!DNL Bot] 탭 상단에 있는 선택한 기간 테이블 중 이름 타임라인을 통해 데이터를 표시하므로 [!DNL bots] 생산되고 있으며 분배하고 있습니다.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]

![선택한 기간 동안 상위 250개의 보트 이름 및 IP 주소 실제 수준에서 보트 트래픽을 차단하거나 robots.txt 파일을 통해 보트를 관리하는 방법 Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

* 다음 **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** 프레임에서 합계와 동일한 데이터를 표시합니다. [!DNL Bot] 탭 맨 위에서 선택한 기간 테이블 동안 보트 이름/IP 주소별 트래픽. 타임라인을 통해 데이터를 표시하고 IP 주소별로 처리합니다. 에 의한 요청 시기를 표시합니다 [!DNL bots] 가 수행되고, IP가 요청을 수행하고, 요청의 배포가 이루어집니다.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]

![선택한 기간 동안 차단된 보트 이름/IP 주소(예: ) 이 그래프는 보트 트래픽 및 403 금지된 HTTP 상태 코드에서 반환된 IP를 표시합니다](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

* 다음 **[!UICONTROL IP address in the Graph - Top 250 Bot Names and IP addresses during selected time period]** 그래프가 차단되었습니다. 이 그래프에서 모든 요청이 차단되는 방식을 확인할 수 있습니다 [!DNL Fastly] 앞으로 나아가기.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period. This graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]

![선택한 기간 동안 비보트 이름/IP 주소가 사실상 차단되었습니다. 이 그래프는 보트 이외의 트래픽 및 403 금지된 HTTP 상태 코드에서 반환된 IP를 표시합니다 ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

* 다음 **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** 프레임은 를 [!DNL bot] 그것은 차단되었습니다 [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![이 표는 IP 주소당 사용자 에이전트 수, 성공, 실패 및 차단된 요청 수를 보여줍니다.](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

* 악성 [!DNL bots] 종종 다른 사람을 으스대곤 한다 [!DNL bots] 의 [!UICONTROL Request User Agent] 필드. 이 표는 IP 주소가 해당 필드에 가지는 고유한 값의 수를 보여줍니다. 값이 높을수록 [!UICONTROL Request User Agent] 필드. IP 주소가 의심스러울수록

## [!UICONTROL IP with non-200 status errors – without 403 status]

![200개 이외의 상태 오류가 있는 IP - 403 상태 없음](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

* 다음 **[!UICONTROL IP with non-200 status errors – without 403 status]** 프레임은 200이 아닌 HTTP 상태 코드가 있는 IP 주소의 선택한 기간에 분포를 보여줍니다. 단일 IP 또는 IP 주소 그룹에서 더 높은 값이 표시되면 추가 조사가 필요합니다.

## [!UICONTROL IP with 403 status codes:]

![403 상태 코드가 있는 IP:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

* 다음 **[!UICONTROL IP with 403 status codes]** 프레임은 [!UICONTROL cache_status=ERROR] 에는 403인 HTTP 상태가 있습니다. 원본 서버가 [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes showing cache_status:]

![cache_status를 표시하는 200개가 아닌 상태 코드가 있는 상위 5개:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

* 다음 **[!UICONTROL Top 5 with non-200 status codes showing cache_status:]** 테이블이 IP/상태 수준에서 [!UICONTROL cache_status] 값.

## [!UICONTROL Pageview Latency will show as spikes on this graph:]

![페이지 보기 지연은 이 그래프에 스파이크로 표시됩니다.](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

* 다음 **[!UICONTROL Pageview Latency will show as spikes on this graph:]** 프레임은 페이지 로드/API 응답 지연을 보여주며, [!DNL bot] 트래픽.
