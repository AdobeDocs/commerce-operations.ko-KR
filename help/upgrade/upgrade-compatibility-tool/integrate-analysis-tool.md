---
title: ' [!DNL Site-Wide Analysis Tool] 통합'
description: Adobe Commerce 프로젝트의  [!DNL Site-Wide Analysis Tool] 대시보드에서  [!DNL Upgrade Compatibility Tool] 보고서를 검색하려면 다음 단계를 따르십시오.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool] 통합

[!DNL Site-Wide Analysis Tool]은(는) Adobe Commerce 인스턴스의 보안과 운영을 보장하기 위해 연중무휴 실시간 성능 모니터링, 보고서 및 권장 사항을 제공합니다.

이제 [!DNL Upgrade Compatibility Tool]이(가) [!DNL Site-Wide Analysis Tool]과(와) 통합되어 기술 전문가가 아닌 사용자도 [!DNL Upgrade Compatibility Tool]을(를) 실행하고 각 파일에 대한 문제 목록이 포함된 [보고서](../upgrade-compatibility-tool/reports.md)를 가져올 수 있습니다.

자세한 내용은 [[!DNL Site-Wide Analysis Tool] 사용 안내서](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html)를 참조하세요.

## [!DNL Site-Wide Analysis Tool]에서 [!DNL Upgrade Compatibility Tool] 실행

프로젝트의 [!DNL Site-Wide Analysis Tool] 대시보드로 이동하여 [!DNL Upgrade Compatibility Tool] 위젯을 찾습니다.

![UCT SWAT 위젯 - 초기](../../assets/upgrade-guide/uct-swat-initial.png)

**[!UICONTROL Run Upgrade Scan]**&#x200B;을(를) 클릭합니다. 프로젝트 크기에 따라 스캔이 다소 시간이 걸릴 수 있습니다. 회전자는 스캔이 진행 중임을 나타냅니다.

![UCT SWAT 위젯 - 진행 중](../../assets/upgrade-guide/uct-swat-progress.png)

검사가 완료되면 높은 수준의 결과가 위젯에 표시됩니다.

![UCT SWAT 위젯 - 결과](../../assets/upgrade-guide/uct-swat-results.png)

[!DNL Upgrade Compatibility Tool] [HTML 보고서](../upgrade-compatibility-tool/reports.md#html-report)를 검색하고 세부 정보를 검토하려면 **[!UICONTROL Download Report]**&#x200B;을(를) 클릭하십시오.


>[!NOTE]
>
> [!DNL Site-Wide Analysis Tool]을(를) 통해 [!DNL Upgrade Compatibility Tool]을(를) 실행하면 결과가 최적화되고 대상 업그레이드에 새롭고 중요한 문제에 집중할 수 있습니다. [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 옵션을 사용하며 항상 프로젝트 버전과 최신 릴리스 버전을 비교한 결과를 표시합니다.
