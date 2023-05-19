---
title: 통합 [!DNL Site-Wide Analysis Tool]
description: '다음 단계에 따라 를 검색합니다. [!DNL Upgrade Compatibility Tool] 다음에서 보고서: [!DNL Site-Wide Analysis Tool] Adobe Commerce 프로젝트에 대한 대시보드.'
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 통합 [!DNL Site-Wide Analysis Tool]

다음 [!DNL Site-Wide Analysis Tool] 는 Adobe Commerce 인스턴스의 보안과 운영을 보장하기 위해 연중무휴 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다.

다음 [!DNL Upgrade Compatibility Tool] 은(는) 이제 와(과) 통합되었습니다. [!DNL Site-Wide Analysis Tool] 기술 전문가가 아닌 사용자도 [!DNL Upgrade Compatibility Tool] 및 받기 [보고서](../upgrade-compatibility-tool/reports.md) 각 파일의 문제 목록을 포함합니다.

다음을 참조하십시오. [[!DNL Site-Wide Analysis Tool] 사용 안내서](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 추가 정보.

## 실행 [!DNL Upgrade Compatibility Tool] 다음에서 [!DNL Site-Wide Analysis Tool]

다음 위치로 이동 [!DNL Site-Wide Analysis Tool] 프로젝트용 대시보드 및 [!DNL Upgrade Compatibility Tool] 위젯.

![UCT SWAT 위젯 - 초기](../../assets/upgrade-guide/uct-swat-initial.png)

클릭 **[!UICONTROL Run Upgrade Scan]**. 프로젝트 크기에 따라 스캔이 다소 시간이 걸릴 수 있습니다. 회전자는 스캔이 진행 중임을 나타냅니다.

![UCT SWAT 위젯 - 진행 중](../../assets/upgrade-guide/uct-swat-progress.png)

검사가 완료되면 높은 수준의 결과가 위젯에 표시됩니다.

![UCT SWAT 위젯 - 결과](../../assets/upgrade-guide/uct-swat-results.png)

클릭 **[!UICONTROL Download Report]** 을(를) 검색하려면 [!DNL Upgrade Compatibility Tool] [HTML 보고서](../upgrade-compatibility-tool/reports.md#html-report) 세부 사항을 검토합니다.


>[!NOTE]
>
> 실행 [!DNL Upgrade Compatibility Tool] 다음을 통해 [!DNL Site-Wide Analysis Tool] 는 결과를 최적화하고 타겟 업그레이드에 새롭고 중요한 문제에 집중할 수 있도록 지원합니다. 다음을 사용합니다. [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 옵션 및 은 항상 프로젝트 버전과 최신 릴리스 버전을 비교하는 결과를 표시합니다.
