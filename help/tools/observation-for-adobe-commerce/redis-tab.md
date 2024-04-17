---
title: 다음 [!UICONTROL Redis] 탭
description: 에 대해 알아보기 [!UICONTROL Redis] 탭 / [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 다음 [!DNL Redis] 탭

## [!UICONTROL Redis Node summary]

![Redis 노드 요약](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

다음 **[!UICONTROL Redis Node summary]** 는 환경의 모든 노드를 포함합니다. 위의 예에는 공유 스테이징을 위한 노드가 포함됩니다. 프로덕션에 1개의 기본 및 2개의 보조 시스템이 있으며 스테이징에도 1개의 기본 및 2개의 보조 시스템이 있습니다.

## [!UICONTROL Redis node detail]

![Redis 노드 세부 정보](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

다음 **[!UICONTROL Redis node detail]** 프레임은 환경을 나타냅니다. [!DNL Redis] 역할, 소프트웨어 버전 및 노드 크기.

## [!UICONTROL Redis node roles timeline]

![Redis 노드 역할 타임라인](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

다음 **[!UICONTROL Redis node roles timeline]** 프레임은 다음의 손실을 나타냅니다. [!DNL Redis] 특정 역할의 서비스. 선이 감소하면 해당 선이 나타내는 특정 역할이 노드 또는 노드를 손실했음을 나타냅니다.

## [!UICONTROL Connection to Redis]

![Redis에 연결](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

다음 **[!UICONTROL Connection to Redis]** 프레임은 다음에서 net.connectedClients 값을 표시합니다. [!DNL New Relic Redis] 샘플 데이터입니다. 다음의 연결 수를 표시합니다. [!DNL New Relic] 애플리케이션(환경) 및 노드

## [!UICONTROL Commands per second by node]

![노드별 초당 명령](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

다음 **[!UICONTROL Commands per second by node]** 프레임은 [!DNL Redis] 선택한 일정 동안의 초당 노드 명령 수입니다.

## [!UICONTROL Redis % of memory used]

![사용된 메모리 중 레디스 %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

다음 **[!UICONTROL Redis % of memory used]** frame은 다음에서 사용하는 최대 메모리 비율을 보여 줍니다. [!DNL Redis] 서버.

## [!UICONTROL Redis used memory]

![Redis 사용된 메모리](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

다음 **[!UICONTROL Redis used memory]** frame은 메모리의 노드 사용을 GB/MB로 보여 줍니다.

## [!UICONTROL Redis changes since last db save]

![마지막 DB 저장 이후 변경 내용 수정](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] 는 상주하고 정보를 스토리지에 저장하는 메모리입니다. 다음 **[!UICONTROL Redis changes since last db save]** frame은 마지막 데이터베이스가 저장소에 저장된 이후 발생한 메모리 변경 횟수를 나타냅니다. 을(를) 참조하십시오 [Redis 지속성](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) 에 대한 자세한 내용은 [!DNL Redis's] 지속성.

## [!UICONTROL Redis synchronization from Log]

![로그에서 Redis 동기화](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

다음 **[!UICONTROL Redis synchronization from Log]** 프레임은 다음에 발생하는 오류에 중점을 둡니다. [!DNL Redis] 동기화 또는 동기화 문제로 인해 발생하는 오류. 에 대한 자세한 내용 [!DNL Redis], 참조 [[!DNL Redis] 설명서](https://redis.io/docs/).
