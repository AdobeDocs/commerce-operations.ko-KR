---
title: '"통합 [!DNL Site-Wide Analysis Tool]"'
description: 다음 단계에 따라 을 검색합니다. [!DNL Upgrade Compatibility Tool] 보고서 출처 [!DNL Site-Wide Analysis Tool] 대시보드 를 사용하십시오.
source-git-commit: 1fc12289125a5954243e177a0c21505234eb2e81
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 통합 [!DNL Site-Wide Analysis Tool]

다음 [!DNL Site-Wide Analysis Tool] Adobe Commerce 인스턴스의 보안 및 작동을 보장하는 24/7의 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다.

다음 [!DNL Upgrade Compatibility Tool] 는 이제 [!DNL Site-Wide Analysis Tool] 기술 전문가가 아닌 사람이 [!DNL Upgrade Compatibility Tool] 그리고 [보고서](../upgrade-compatibility-tool/reports.md) 각 파일에 대한 문제 목록을 포함합니다.

자세한 내용은 [[!DNL Site-Wide Analysis Tool] 사용 안내서](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 추가 정보.

## 를 실행합니다. [!DNL Upgrade Compatibility Tool] 에서 [!DNL Site-Wide Analysis Tool]

로 이동합니다 [!DNL Site-Wide Analysis Tool] 프로젝트에 대한 대시보드 를 찾아 [!DNL Upgrade Compatibility Tool] 위젯.

![UCT SWAT 위젯 - 초기](../../assets/upgrade-guide/uct-swat-initial.png)

클릭 **[!UICONTROL Run Upgrade Scan]**. 검사는 프로젝트 크기에 따라 시간이 좀 걸릴 수 있습니다. spinner는 검사가 진행 중임을 나타냅니다.

![UCT SWAT 위젯 - 진행 중](../../assets/upgrade-guide/uct-swat-progress.png)

스캔이 완료되면 높은 수준의 결과가 위젯에 표시됩니다.

![UCT SWAT 위젯 - 결과](../../assets/upgrade-guide/uct-swat-results.png)

클릭 **[!UICONTROL Download Report]** 읽어들이기 [!DNL Upgrade Compatibility Tool] [HTML 보고서](../upgrade-compatibility-tool/reports.md#html-report) 세부 사항을 검토합니다.


>[!NOTE]
>
> 실행 [!DNL Upgrade Compatibility Tool] 사용 [!DNL Site-Wide Analysis Tool] 은 결과를 최적화하고 target 업그레이드를 위해 새롭고 중요한 문제에 집중할 수 있도록 도와줍니다. 이 템플릿은 를 사용합니다 [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 옵션 및 은 항상 프로젝트 버전과 최신 릴리스 버전을 비교하는 결과를 표시합니다.
