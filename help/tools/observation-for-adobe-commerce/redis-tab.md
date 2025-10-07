---
title: '[!UICONTROL Redis] 탭'
description: '[!UICONTROL Redis]의  [!DNL Observation for Adobe Commerce] 탭에 대해 알아봅니다.'
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# [!DNL Redis] 탭

## [!UICONTROL Redis Node summary]

![Redis 노드 요약](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]**&#x200B;은(는) 환경의 모든 노드를 포함합니다. 위의 예에는 공유 스테이징을 위한 노드가 포함됩니다. 프로덕션에 1개의 기본 및 2개의 보조 시스템이 있으며 스테이징에도 1개의 기본 및 2개의 보조 시스템이 있습니다.

## [!UICONTROL Redis node detail]

![Redis 서버 성능 메트릭 및 노드 구성 세부 정보](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

**[!UICONTROL Redis node detail]** 프레임은 환경, [!DNL Redis] 역할, 소프트웨어 버전 및 노드 크기를 나타냅니다.

## [!UICONTROL Redis node roles timeline]

![Redis 노드 역할 타임라인](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

**[!UICONTROL Redis node roles timeline]** 프레임은 특정 역할에서 [!DNL Redis] 서비스가 손실되었음을 나타냅니다. 선이 감소하면 해당 선이 나타내는 특정 역할이 노드 또는 노드를 손실했음을 나타냅니다.

## [!UICONTROL Connection to Redis]

![Redis에 연결](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

**[!UICONTROL Connection to Redis]** 프레임에는 [!DNL New Relic Redis] 샘플 데이터의 net.connectedClients 값이 표시됩니다. [!DNL New Relic] 응용 프로그램(환경) 및 노드별 연결 수를 표시합니다.

## [!UICONTROL Commands per second by node]

![노드별 초당 명령](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

**[!UICONTROL Commands per second by node]** 프레임에는 선택한 기간 동안 초당 노드별 [!DNL Redis] 명령이 표시됩니다.

## [!UICONTROL Redis % of memory used]

사용된 메모리 중 ![Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

**[!UICONTROL Redis % of memory used]** 프레임에는 [!DNL Redis] 서버에서 사용하는 최대 메모리 비율이 표시됩니다.

## [!UICONTROL Redis used memory]

![Redis 사용된 메모리](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

**[!UICONTROL Redis used memory]** 프레임은 메모리의 노드 사용량을 GB/MB로 표시합니다.

## [!UICONTROL Redis changes since last db save]

![마지막 DB 저장 이후 변경 내용 수정](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis]은(는) 메모리에 상주하며 정보를 저장소에 저장합니다. **[!UICONTROL Redis changes since last db save]** 프레임은 마지막 데이터베이스가 저장소에 저장된 이후에 발생한 메모리 변경 사항의 수를 나타냅니다. [&#x200B; 지속성에 대한 자세한 내용은 &#x200B;](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)Redis 지속성[!DNL Redis's]을 참조하세요.

## [!UICONTROL Redis synchronization from Log]

![로그에서 Redis 동기화](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

**[!UICONTROL Redis synchronization from Log]** 프레임은 [!DNL Redis] 동기화 중에 발생한 오류 또는 동기화 문제로 인해 발생하는 오류에 중점을 둡니다. [!DNL Redis]에 대한 자세한 내용은 [[!DNL Redis] 설명서](https://redis.io/docs/)를 참조하세요.
