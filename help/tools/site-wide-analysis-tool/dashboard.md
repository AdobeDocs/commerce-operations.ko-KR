---
title: "[!DNL Dashboard]"
description: 에 대해 알아보기 [!DNL Dashboard] 탭에서 다음을 수행합니다. [!DNL Site-Wide Analysis Tool], 요소, 사용할 시기, 이점 및 우수 사례
source-git-commit: d176b6a82fbea2f3c611be0fbea85814086feed9
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

다음 [!UICONTROL Dashboard] 페이지 표시 개요 [!DNL widgets] Adobe Commerce 웹 사이트의 상태 및 현재 상태에 대한 &quot;단일 창&quot;을 제공합니다. 다음 [!DNL widgets] 각 기능에는 각 기능의 페이지, 각 도구 자체에 대한 액세스 링크 또는 보고서에 대한 액세스 링크가 포함되어 있습니다 [!DNL widget]).
다음 목록도 있습니다 [!UICONTROL External Resources] 다음을 포함한 Adobe Commerce 링크 [Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터)](https://support.magento.com/), [Adobe Commerce 개발자 설명서(DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [보안 센터](https://magento.com/security), 및 [Adobe Commerce(OAC)에 대한 관찰](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## 요소

* **[!UICONTROL Recommendations]**: 사이트에 대한 우수 사례 권장 사항을 표시합니다. Recommendations(발견된 문제 및 수정할 권장 사항)는 우선 순위(P0(중요)에서 P4(알림)별로 정렬됩니다.
Recommendations에는 사용된 설명, 권장 사항, 사이트 영향, 근본 원인, 시나리오/전제 조건 및 도구가 포함되어 있습니다.

* **[!UICONTROL Upgrade Compatibility Tool]**: 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인합니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다. 또한 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 해결해야 하는 잠재적인 문제를 식별합니다.
다음 [!UICONTROL Upgrade Compatibility Tool] 사용자 지정된 기능에 대한 핵심 코드 변경 사항을 적용한 시기를 식별할 수 있습니다.

* **[!UICONTROL Security Scan Tool]**: 보안 위험에 대한 Adobe Commerce 사이트를 모니터링합니다. 또한 가맹점에서 맬웨어를 적극적으로 효율적으로 탐지하고, 보안 위험, 맬웨어 또는 위협이 있는 경우 가맹점에 알릴 수 있으며, 누락된 Adobe Commerce 패치 및 업데이트를 식별할 수 있습니다.

* **[!UICONTROL Extensions]**: Adobe Commerce 인스턴스에 현재 설치된 확장을 표시합니다. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 여기에 나열된 확장에 대한 정보가 제공된 경우 사용할 수 있습니다.

* **[!UICONTROL Alerts]**: 최신 항목을 표시합니다 [!DNL New Relic Managed Alerts] 참조하십시오. 추가 정보 [Adobe Commerce에 대한 관리 경고](https://support.magento.com/hc/en-us/articles/360045806832) 그리고 방법 [New Relic 서비스 액세스](https://support.magento.com/hc/en-us/articles/360039127712) ( Adobe Commerce 지원 기술 자료) 를 참조하십시오.

* **[!UICONTROL Non-recommended software in use]**: Adobe Commerce 버전을 기반으로 Adobe Commerce 인스턴스가 현재 사용하고 있는 비권장 소프트웨어를 표시합니다. 권장되지 않는 소프트웨어는 [!UICONTROL Name], [!UICONTROL Installed Version], 및 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: 이미 설치했을 수 있는 패치와 Adobe Commerce 버전을 모두 기준으로 권장되는 패치에 대한 간단한 목록을 표시합니다. 권장 패치 전체 목록은 **[!UICONTROL Patches]** 기능 탭 - [!DNL Site-Wide Analysis Tool]. 패치는 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}. 나열된 모든 패치는 현재 Adobe Commerce 인스턴스와 호환됩니다.
Adobe Commerce 인스턴스에 표시할 권장 패치가 없는 경우 다음을 수행합니다 [!DNL widget] 표시됩니다. **[!UICONTROL No Recommended Patches]**.

## 사용 시기

다음 **[!UICONTROL Dashboard]** 페이지 는 개요 명령 센터입니다 [!DNL Site-Wide Analysis Tool] 사이트 상태에 대한 &quot;큰 그림&quot;을 전체적으로 쉽게 볼 수 있을 뿐만 아니라 각 페이지를 통해 Adobe Commerce 웹 사이트에 대한 특정 도구, 권장 사항 및 보고서를 보고 액세스할 수도 있습니다 [!DNL widget].

## 이점

* 다음 [!DNL widgets] 대상 [!UICONTROL Recommendations], [!UICONTROL Extensions], 및 [!UICONTROL Security Scan] 모든 사용자는 읽기 쉬운 색상으로 코딩된 대화형 원형 그래프를 사용하는데, 이 그래프는 사이드에 대한 그래프 범례 및 중앙에 있는 계산 합계를 사용하여 몇 개인지를 나타냅니다 [!UICONTROL Recommendations], [!UICONTROL Extensions], 및 [!UICONTROL Security Scan Tool] 각 기능에 있는 항목입니다. [!UICONTROL Recommendations] 및 [!UICONTROL Security Scan Tool] 그래프는 심각도로 구분됩니다. [!UICONTROL Extensions] 는 4개의 분류로 구분됩니다. 현재 버전, 이전 버전, 비활성화 및 알 수 없음.

* [!DNL New Relic Alerts] 짧은 설명 및 경고가 발생한 지 오래 전을 포함하여 맨 위에 있는 가장 최근 경고와 함께 나열됩니다.

* 다음 [!UICONTROL Recommendations] 및 [!UICONTROL Extensions] [!DNL widgets] 를 클릭하여 각 기능에 대한 전체 데이터 페이지에 액세스할 수 있습니다. **[!UICONTROL View All]**.

* 다음 [!UICONTROL Security Scan Tool] 에 **[!UICONTROL View Report]** 링크 위치 [!DNL widget] 창으로 이동 [!UICONTROL Recommendations] 페이지.

* 다음 [!DNL Upgrade Compatibility Tool] 에 **[!UICONTROL Run Upgrade Scan]** 단추 [!DNL widget] 창을 엽니다.

## 사용 우수 사례 [!UICONTROL Dashboard]

* 각 [!DNL widget] 이 라이브러리가 제공하는 세부 데이터에 액세스하려면 웹 사이트의 상태, 권장 사항 및 모범 사례에 대한 통찰력과 이해를 모두 얻을 수 있습니다.

* 로 이동합니다. [!UICONTROL Security Scan Tool] [!DNL widget] 을(를) 클릭합니다. [!UICONTROL View Report] 를 보려면 [!UICONTROL Recommendations] 사이트에 대해 보고합니다.

* 를 사용하십시오 [!DNL External Resources] 추가 정보, 보안 패치, 업데이트 및 모범 사례에 대한 최신 정보를 확인하거나 이러한 통찰력을 활용할 수 있는 링크 [Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터)](https://support.magento.com/), [Adobe Commerce 개발자 설명서(DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [보안 센터](https://helpx.adobe.com/security.html), 및 [Adobe Commerce(OAC)에 대한 관찰](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).
