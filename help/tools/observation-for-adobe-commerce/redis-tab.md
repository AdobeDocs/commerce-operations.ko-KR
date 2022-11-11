---
title: "다음 [!UICONTROL Redis] tab"
description: 에 대해 알아보기 [!UICONTROL Redis] 탭 [!DNL Observation for Adobe Commerce].
source-git-commit: f4379d0b89a6ea6d2f2a5a02c505581d4d54708f
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 다음 [!DNL Redis] 탭

## [!UICONTROL Redis Node summary]

![Redis 노드 요약](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

다음 **[!UICONTROL Redis Node summary]** 는 환경에 있는 모든 노드를 포함합니다. 위의 예에는 공유 스테이징을 위한 노드가 포함되어 있습니다. 프로덕션에 운영 및 보조 노드 1개와 스테이징에 대한 보조 노드 2개가 있습니다.

## [!UICONTROL Redis node detail]

![Redis 노드 세부 정보](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

다음 **[!UICONTROL Redis node detail]** 프레임은 환경을 나타내고 [!DNL Redis] 역할, 소프트웨어 버전 및 노드 크기

## [!UICONTROL Redis node roles timeline]

![Redis 노드 역할 타임라인](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

다음 **[!UICONTROL Redis node roles timeline]** 프레임은 [!DNL Redis] 특정 역할의 서비스입니다. 한 줄이 늘어나면 해당 선이 나타내는 특정 역할이 노드나 노드를 잃었다는 것을 나타냅니다.

## [!UICONTROL Connection to Redis]

![레디스에 연결](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

다음 **[!UICONTROL Connection to Redis]** frame은 다음에서 net.connectedClients 값을 표시합니다 [!DNL New Relic Redis] 샘플 데이터. 연결 수를 표시합니다. [!DNL New Relic] 응용 프로그램(환경) 및 노드입니다.

## [!UICONTROL Commands per second by node]

![노드별 초당 명령 수](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

다음 **[!UICONTROL Commands per second by node]** 프레임이 [!DNL Redis] 선택한 기간에 대한 노드별 명령(초당 노드 수)

## [!UICONTROL Redis % of memory used]

![사용된 메모리의 Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

다음 **[!UICONTROL Redis % of memory used]** 프레임은 [!DNL Redis] 서버.

## [!UICONTROL Redis used memory]

![레디스가 사용한 메모리](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

다음 **[!UICONTROL Redis used memory]** 프레임은 메모리 노드 사용을 GB/MB로 보여 줍니다.

## [!UICONTROL Redis changes since last db save]

![마지막 db 저장 이후 변경 내용 수정](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] 는 메모리 거주자이며 정보를 저장소에 저장합니다. 다음 **[!UICONTROL Redis changes since last db save]** 프레임은 마지막 데이터베이스를 저장소에 저장한 후 발생한 메모리 변경 횟수를 나타냅니다. 을(를) 참조하십시오. [Redis 지속성](https://redis.io/docs/manual/persistence/) 추가 설명 [!DNL Redis's] 지속성.

## [!UICONTROL Redis synchronization from Log]

![로그에서 Redis 동기화](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

다음 **[!UICONTROL Redis synchronization from Log]** 프레임은 [!DNL Redis] 동기화 문제로 인해 발생하는 동기화 또는 오류 자세한 내용은 [!DNL Redis]를 참조하려면 [[!DNL Redis] 설명서](https://redis.io/docs/).
