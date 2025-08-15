---
title: '[!UICONTROL CDN] 탭'
description: '[!UICONTROL CDN]의  [!DNL Observation for Adobe Commerce] 탭에 대해 알아봅니다.'
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# [!UICONTROL CDN] 탭

이 탭에는 [!DNL content delivery network (CDN)]에 초점을 맞춘 정보가 있습니다. Adobe Commerce Cloud의 경우 [!DNL Fastly] 서비스입니다.

## [!UICONTROL HIT rate]

![적중률](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

**[!UICONTROL HIT rate]** 프레임에는 마지막 순간에 [!UICONTROL HITS]을(를) 발생시킨 캐시 가능한 요청 수가 표시됩니다. 캐싱이 성공했음을 나타냅니다. 오른쪽 화살표는 일주일 전 같은 시간에 위 또는 아래의 백분율을 보여줍니다.

## [!UICONTROL HIT Processing]

![히트 처리](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

이 **[!UICONTROL HIT processing]** 상자에는 주중에 [!UICONTROL HITS]을(를) 발생시킨 캐시 가능 요청 수가 표시됩니다.

## [!UICONTROL MISS rate]

![결석 비율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

이 **[!UICONTROL MISS rate]** 상자는 마지막 순간에 캐시 가능한 요청의 누락 수를 표시합니다. miss는 요청이 캐시되지 않고 콘텐츠를 제공하기 위해 요청을 원본 서버에 전달해야 하는 경우를 말합니다. 오른쪽의 값은 1주일 전 분당 분 수 대비 증가/감소를 비교한 것이다.

## [!UICONTROL MISS time]

![부재 중 시간](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![히트 비율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![오류 백분율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

**[!UICONTROL Error Percentage]** 상자에 요청의 ERROR 백분율 값이 표시되고 1주일 전 같은 시간과 비교하여 상대적인 증가/감소가 표시됩니다.

## [!UICONTROL Total Requests]

![총 요청](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![오류율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![선택한 기간(초)에 대한 Fastly 캐시 평균 응답](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

이 프레임에는 캐시 가능한 요청의 기간(초)이 표시됩니다. 즉, `cache_response`이(가) [!UICONTROL MISS]인 경우 선택한 시간 동안 캐시된 누락된 응답의 평균을 표시합니다.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![POP로 대체된 선택한 기간(초)의 평균 응답 빠르게 캐시하기](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

이 컨텍스트의 *POP*&#x200B;은(는) 캐시 저장소에 대한 풀로 작동하도록 구성된 POP(Point of Presence)를 참조합니다. [현재 상태 지점](https://developer.fastly.com/learning/concepts/pop/)을 참조하세요.

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![선택한 기간 동안의 총 대역폭(모든 POP), 1주 전과 비교(% 증가/감소)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![요청 - 선택한 이후 기간이 1주 전과 비교됨](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

이 프레임은 맨 위에 있는 [!UICONTROL Total Requests]의 요약 상자와 비슷하지만 이전 주의 요청 수를 보여 줍니다. 캐시 가능한 요청만 있는 것이 아니라 모든 요청입니다(`is_cacheable`이(가) true인 경우).

## [!UICONTROL Response Count]

![응답 수](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POP별 대역폭](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![상위 5개 URL(5xx 또는 3xx 상태 코드)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

**[!UICONTROL Top 5 URLs]** 보기에는 5xx 또는 3xx 오류 응답이 있는 상위 5개의 URL이 표시됩니다. 공간 제약으로 인해 해당 URL과 연관된 특정 오류 코드를 보려면 URL을 마우스로 가리켜야 합니다. (위 그림의 빨간색 상자).

## [!UICONTROL Top 25 URLs (200 status)]

![상위 25개 URL(200개 상태)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

**[!UICONTROL Top 25 URLs]** 프레임에는 선택한 기간 동안 횟수별로 200 상태를 반환하는 URL이 표시됩니다.

## [!UICONTROL Duration by Response Status]

응답 상태별 ![기간](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

**[!UICONTROL Duration by Response Status]** 그래프는 선택한 기간 동안 오류 상태 코드에 의해 패싯되어 카운트별로 오류 응답을 표시합니다.

## [!UICONTROL Duration by Response Status, top 25 urls]

![응답 상태별 기간, 상위 25개 url](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

**[!UICONTROL Duration by Response Status, top 25 URLs]** 그래프는 응답 기간(초)별로 상위 25개의 URL을 보여 줍니다. 전체 경로를 보려면 마우스를 URL 위로 가져와야 할 수 있습니다. 또한 하나의 URL을 제외한 모든 URL을 제거하려면 해당 URL을 클릭합니다. 그런 다음 다른 URL을 개별적으로 클릭하여 다시 추가할 수 있습니다. 개별 URL을 제거하려면 키를 누른 채로 각 URL을 클릭하여 그래프에서 제거할 수 있습니다.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![응답 상태별 기간, 200개가 아닌 상위 25개 상태](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

**[!UICONTROL Duration by Response Status, top 25 non-200 status]** 그래프는 포커스가 200개가 아닌 상태 코드 또는 오류 상태 코드에 있다는 점을 제외하고 마지막 그래프와 비슷합니다. 오류 코드와 URL이 표시됩니다. 전체 경로를 보려면 마우스를 URL 위로 가져와야 할 수 있습니다. 또한 하나의 URL을 제외한 모든 URL을 제거하려면 해당 URL을 클릭합니다. 그런 다음 다른 URL을 개별적으로 클릭하여 다시 추가할 수 있습니다. 개별 URL을 제거하려면 키를 누른 채로 각 URL을 클릭하여 그래프에서 제거할 수 있습니다.

## [!UICONTROL Error Count by POP timeline]

![POP 타임라인별 오류 개수](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

**[!UICONTROL Error Count by POP timeline]** 그래프는 선택한 일정 타임라인에 오류 코드로 대체된 오류 상태의 수를 표시합니다.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![응답 상태별 기간, 상위 25개 클라이언트 IP, 200개가 아닌 상태](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

**[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** 그래프는 상태 오류 코드가 있는 선택한 일정의 평균 기간별 IP 주소를 표시합니다.

## [!UICONTROL IP Frequency]

![IP 빈도](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

**[!UICONTROL IP Frequency]** 프레임은 [!DNL Fastly] 로그에서 각 IP에 대한 (&#39;MISS&#39; 및 &#39;PASS&#39;) 상태를 계산합니다. 이러한 상태의 웹 요청은 원본 서버에 도달하고 서버에 로드를 추가합니다. 상위 20개 주소를 빈도로 표시합니다. 이 프레임은 웹 사이트에서 IP 공격 또는 과도한 부하를 감지하는 데 사용할 수 있습니다. 이 그래프는 요약 탭에도 있으며 이 탭에 표시된 [!DNL Fastly] 로그 정보에 대한 자세한 내용을 쉽게 비교하기 위해 여기에 배치됩니다.
