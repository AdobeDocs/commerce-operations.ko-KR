---
title: 다음 [!DNL Infra] 탭
description: 다음 [!DNL Infra] 탭은 인프라 문제의 문제 및 원인을 격리합니다.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 다음 [!DNL Infra] 탭

다음 **[!DNL Infra]** 탭은 인프라 문제의 문제 및 원인을 격리합니다. 탭에서 볼 수 있는 프레임에 대해 자세히 설명합니다.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![서비스 경고](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

다음 **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** 그래프는에서 수집한 서비스 경고를 보여 줍니다. [!DNL New Relic] 인프라 에이전트. 많은 서비스가 배포와 연결되어 다시 시작되는 것을 보여 줍니다.

## [!UICONTROL Inode usage by mount]

![마운트별 Inode 사용](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

다음 **[!UICONTROL Inode usage by mount]** 프레임 쇼 [!DNL inode] 선택한 일정 동안의 마운트에 의한 사용. 스토리지 공간이 충분하더라도 노드가 부족한 경우 [!DNL inodes], 사용 가능한 스토리지가 부족한 것으로 표시됩니다. 파일(특히 작은 파일)을 제거하면 두 공간이 모두 확보되어 [!DNL inodes] 사용 가능.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![시간 표시 막대에 따른 vCPU 계층 보기 2주 이상](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

다음 **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** 이 프레임은 선택한 기간(2주 이상)에 대한 vCPU 계층 보기를 표시합니다. 이 프레임은 다음에 할당된 vCPU 수를 확인합니다. [!DNL New Relic] 애플리케이션 이름이 표시됩니다.

## [!UICONTROL vCPU tier view over timeline]

![타임라인에 대한 vCPU 계층 보기](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

다음 **[!UICONTROL vCPU tier view over timeline]** 이 프레임은 24시간 이상 선택한 기간 동안의 vCPU 계층 보기를 보여 줍니다. 이 프레임은 다음에 할당된 vCPU 수를 확인합니다. [!DNL New Relic] 애플리케이션 이름이 표시됩니다. 클러스터 업사이징과 다운사이징을 모두 표시합니다.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![노드별 타임라인에 대한 vCPU 계층 보기](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

다음 **[!UICONTROL vCPU tier view over timeline BY NODE]** 프레임은 선택한 기간 동안의 vCPU 계층 보기를 노드별로 보여 줍니다. 이 프레임은 노드 손실을 감지하거나 노드가 확장 또는 축소될 때 유용합니다. 노드별 타임라인에 대한 vCPU 계층 보기는 타임라인을 24시간 미만으로 확인해야 합니다.

## [!UICONTROL Instance details]

![인스턴스 세부 사항](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

다음 **[!UICONTROL Instance details]** 표에는 각 인스턴스의 인스턴스 세부 정보가 나와 있습니다. [!DNL New Relic] 응용 프로그램.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![비응답형 노드](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

다음 **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** 프레임이 일정 기간 동안 응답하지 않는 노드를 보여 줍니다.
