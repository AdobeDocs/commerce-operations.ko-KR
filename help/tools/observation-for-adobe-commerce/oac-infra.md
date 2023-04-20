---
title: "다음 [!DNL Infra] tab"
description: 다음 [!DNL Infra] 탭에서는 인프라 문제의 문제와 원인을 파악합니다.
source-git-commit: 5e4ab9e62f395b0967c3a632659c70a22770e9db
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 다음 [!DNL Infra] 탭

다음 **[!DNL Infra]** 탭에서는 인프라 문제의 문제와 원인을 파악합니다. 또한 탭에서 볼 수 있는 프레임에 대해 설명합니다.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![서비스 경고](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

다음 **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** 그래프는 다음을 통해 수집된 서비스 경고를 표시합니다 [!DNL New Relic] 인프라 에이전트 이렇게 하면 서비스 재시작을 보여주며 대부분 배포와 관련되어 있습니다.

## [!UICONTROL Inode usage by mount]

![마운트별 Inode 사용](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

다음 **[!UICONTROL Inode usage by mount]** 프레임 표시 [!DNL inode] 선택한 기간에 대해 마운트별 사용. 노드가 부족하면 사용 가능한 스토리지가 많아도 [!DNL inodes]로 설정되면 사용 가능한 스토리지가 부족하게 됩니다. 파일(특히 작은 파일)을 제거하면 공간이 모두 확보되어 [!DNL inodes] 사용할 수 있습니다.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![타임라인에 대한 vCPU 계층 보기 2주 이상](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

다음 **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** 프레임은 선택한 기간(2주 이상)의 vCPU 계층 보기를 표시합니다. 이 프레임은 에 할당된 vCPU 수를 확인합니다. [!DNL New Relic] 애플리케이션 이름이 표시됩니다.

## [!UICONTROL vCPU tier view over timeline]

![타임라인을 통한 vCPU 계층 보기](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

다음 **[!UICONTROL vCPU tier view over timeline]** 프레임은 선택한 시간대의 vCPU 계층 보기를 24시간 이상 표시합니다. 이 프레임은 에 할당된 vCPU 수를 확인합니다. [!DNL New Relic] 애플리케이션 이름이 표시됩니다. 클러스터 업사이즈와 다운사이즈가 모두 표시됩니다.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![노드별로 타임라인을 통한 vCPU 계층 보기](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

다음 **[!UICONTROL vCPU tier view over timeline BY NODE]** 프레임은 노드별로 선택한 일정의 vCPU 계층 보기를 표시합니다. 이 프레임은 노드의 손실을 감지하거나 노드가 업사이드나 다운사이즈인 경우에 유용합니다. NODE별 타임라인을 통한 vCPU 계층 보기는 24시간 미만의 타임라인을 확인해야 합니다.

## [!UICONTROL Instance details]

![인스턴스 세부 사항](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

다음 **[!UICONTROL Instance details]** 표는 각 인스턴스에 대한 세부 정보를 보여줍니다. [!DNL New Relic] 응용 프로그램.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![비응답형 노드](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

다음 **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** 프레임은 일정 기간 동안 응답하지 않는 노드를 표시합니다.
