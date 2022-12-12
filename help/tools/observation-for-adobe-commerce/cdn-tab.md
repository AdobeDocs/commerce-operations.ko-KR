---
title: "다음 [!UICONTROL CDN] tab"
description: 에 대해 알아보기 [!UICONTROL CDN] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 다음 [!UICONTROL CDN] 탭

이 탭에는 [!DNL content delivery network (CDN)]. Adobe Commerce Cloud의 경우 다음과 같습니다 [!DNL Fastly] 서비스.

## [!UICONTROL HIT rate]

![적중률](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

다음 **[!UICONTROL HIT rate]** 프레임은 다음을 발생시킨 캐시 가능 요청 수를 보여줍니다. [!UICONTROL HITS] 마지막 순간에 캐싱이 성공했음을 나타냅니다. 오른쪽 화살표는 1주일 전에 같은 시간 위 또는 아래에 백분율이 표시됩니다.

## [!UICONTROL HIT Processing]

![히트 처리](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

이 **[!UICONTROL HIT processing]** 상자에 결과를 가져오는 캐시 가능한 요청 수가 표시됩니다 [!UICONTROL HITS] 한 주 동안.

## [!UICONTROL MISS rate]

![MISS 비율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

이 **[!UICONTROL MISS rate]** 상자에 마지막 순간에 캐시 가능한 요청의 누락 수가 표시됩니다. 누락은 요청이 캐시되지 않고 컨텐츠를 제공하기 위해 요청을 원본 서버에 전달해야 하는 경우입니다. 오른쪽의 값은 1주 전에 분당 시간(분)과 증가/감소를 비교하는 값입니다.

## [!UICONTROL MISS time]

![누락된 시간](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![적중률](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![오류 비율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

다음 **[!UICONTROL Error Percentage]** 상자는 요청의 오류 백분율에 값을 표시하며, 1주 전에 동일한 시간과 비교하여 상대적 증가/감소를 표시합니다.

## [!UICONTROL Total Requests]

![총 요청 수](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![오류율](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![선택한 기간(초)에 대한 실제 캐시 평균 응답](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

이 프레임은 캐시 가능한 요청의 기간(초)을 보여줍니다. 즉, `cache_response` is [!UICONTROL MISS]에 지정된 경우 선택한 시간에 대해 캐시된 누락된 응답의 평균을 표시합니다.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![POP에 의해 선택한 기간(초)에 대한 캐시 평균 응답](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![선택한 기간 동안 총 대역폭(모든 POP)이 1주 전(증가율/감소율) 대비](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![요청 - 선택한 기간 이후(1주 전과 비교)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

이 프레임은 [!UICONTROL Total Requests] 맨 위에 있지만 은 이전 주의 요청 수를 표시합니다. 이는 캐시 가능한 요청뿐만 아니라 모든 요청입니다(여기서 `is_cacheable` 가 true입니다.)

## [!UICONTROL Response Count]

![응답 수](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POP별 대역폭](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![상위 5개의 URL(5xx 또는 3xx 상태 코드)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

다음 **[!UICONTROL Top 5 URLs]** 보기는 5xx 또는 3xx 오류 응답을 경험하는 상위 5개 URL을 보여줍니다. space 제약 조건 때문에 URL 위로 마우스를 가져와야 해당 URL과 관련된 특정 오류 코드를 볼 수 있습니다. (위 그림의 빨간색 상자에 있는 예)

## [!UICONTROL Top 25 URLs (200 status)]

![상위 25개의 URL(200 상태)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

다음 **[!UICONTROL Top 25 URLs]** 프레임은 선택한 기간 동안 카운트별로 200 상태를 반환하는 URL을 보여줍니다.

## [!UICONTROL Duration by Response Status]

![응답별 기간 상태](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

다음 **[!UICONTROL Duration by Response Status]** 그래프는 선택한 시간 동안의 카운트별 오류 응답을 오류 상태 코드에 따라 면처리된 오류 응답을 표시합니다.

## [!UICONTROL Duration by Response Status, top 25 urls]

![응답 상태별 기간, 상위 25개의 url](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

다음 **[!UICONTROL Duration by Response Status, top 25 URLs]** 그래프는 응답 시간별 상위 25개의 URL을 초 단위로 보여줍니다. 전체 경로를 보려면 마우스를 URL 위로 가져와야 할 수 있습니다. 또한 URL을 제외한 모든 URL을 제거하려면 해당 URL을 클릭합니다. 그런 다음 다른 URL을 개별적으로 클릭하여 다시 추가할 수 있습니다. 개별 URL을 제거하려면 키를 누른 채로 각 URL을 클릭하여 그래프에서 제거할 수 있습니다.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![응답 상태별 기간, 상위 25개 비200개 상태](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

다음 **[!UICONTROL Duration by Response Status, top 25 non-200 status]** 그래프는 200이 아닌 상태 코드 또는 오류 상태 코드에 중점을 두었다는 점을 제외하고 마지막 그래프와 유사합니다. 오류 코드와 URL이 표시됩니다. 전체 경로를 보려면 마우스를 URL 위로 가져와야 할 수 있습니다. 또한 URL을 제외한 모든 URL을 제거하려면 해당 URL을 클릭합니다. 그런 다음 다른 URL을 개별적으로 클릭하여 다시 추가할 수 있습니다. 개별 URL을 제거하려면 키를 누른 채로 각 URL을 클릭하여 그래프에서 제거할 수 있습니다.

## [!UICONTROL Error Count by POP timeline]

![POP 타임라인별 오류 수](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

다음 **[!UICONTROL Error Count by POP timeline]** 그래프에는 오류 코드에 따라 면처리된 선택한 시간 표시 막대 및 오류 상태의 수가 표시됩니다.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![응답별 기간 상태, 상위 25개 클라이언트 IP, 200개 제외 상태](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

다음 **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** 그래프는 상태 오류 코드가 있는 선택한 기간의 평균 기간별로 IP 주소를 보여줍니다.

## [!UICONTROL IP Frequency]

![IP 빈도](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

다음 **[!UICONTROL IP Frequency]** 프레임은 IP에서 각 IP의 (&#39;MISS&#39; 및 &#39;PASS&#39;) 상태를 계산합니다 [!DNL Fastly] 로그. 이러한 상태의 웹 요청은 원본 서버에 도달하고 서버에 로드를 추가합니다. 빈도로 상위 20개의 주소를 보여 줍니다. 이 프레임은 웹 사이트에서 IP 공격 또는 부하의 소스를 감지하는 데 사용할 수 있습니다. 이 그래프는 요약 탭에도 있으며 의 세부 사항과 쉽게 비교할 수 있도록 여기에 배치됩니다. [!DNL Fastly] 이 탭에 표시되는 로그 정보입니다.
