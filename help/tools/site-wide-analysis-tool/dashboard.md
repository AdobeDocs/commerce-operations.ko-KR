---
title: '[!DNL Dashboard]'
description: 에 대해 알아보기 [!DNL Dashboard] 의 탭 [!DNL Site-Wide Analysis Tool], 요소, 사용 시기, 이점 및 모범 사례입니다.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

다음 [!UICONTROL Dashboard] 한 눈에 페이지 표시 [!DNL widgets] 이를 통해 Adobe Commerce 웹 사이트의 상태 및 현재 상태에 대한 &quot;단일 창 보기&quot;를 제공합니다. 각 [!DNL widget] 에는 각 기능의 페이지, 각 도구 자체 또는 보고서(다음에 따라 다름)에 대한 액세스 링크가 포함되어 있습니다. [!DNL widget]).
다음 목록도 있습니다. [!UICONTROL External Resources] 다음을 포함한 Adobe Commerce 링크 [Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce 개발자 설명서(DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [보안 센터](https://helpx.adobe.com/security.html), 및 [Adobe Commerce(OAC)에 대한 관찰](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 요소

* **[!UICONTROL Recommendations]**: 사이트에 대한 모범 사례 권장 사항을 표시합니다. Recommendations(발견된 문제 및 해결할 권장 사항)는 우선 순위(P0(중요) ~ P4(알림)로 정렬됩니다.
Recommendations에는 설명, 권장 사항, 사이트 영향, 근본 원인, 시나리오/사전 조건 및 사용된 도구가 포함되어 있습니다.

* **[!UICONTROL Upgrade Compatibility Tool]**: 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인합니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다. 또한 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 수정해야 하는 잠재적인 문제를 식별합니다.
다음 [!UICONTROL Upgrade Compatibility Tool] 사용자 지정된 기능에 대한 핵심 코드가 변경된 시기를 식별할 수 있습니다.

* **[!UICONTROL Security Center Widget]**: 사이트에 대한 보안 인사이트를 표시합니다.
표시되는 보안 정보에는 다음이 포함됩니다 [기술 [!DNL Stack] 버전 준수 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 우수 사례 보안 Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
다음 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) Adobe Commerce 사이트를 모니터링하여 보안 위험을 방지합니다. 가맹점의 악성코드를 선제적이고 효율적으로 탐지해 보안 위험, 악성코드, 위협 등이 있으면 가맹점에 알리고, Adobe Commerce 패치와 업데이트 누락 등을 파악할 수 있다.

* **[!UICONTROL Extensions]**: 현재 Adobe Commerce 인스턴스에 설치된 확장을 표시합니다. [Adobe Commerce 마켓플레이스](https://marketplace.magento.com/extensions.html) 목록에 있는 확장에 대한 정보가 제공됩니다(사용 가능한 경우).

* **[!UICONTROL Alerts]**: 최신 버전을 표시합니다. [!DNL New Relic Managed Alerts] Adobe Commerce 인스턴스용 자세히 알아보기 [Adobe Commerce에 대한 관리 경고](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) 및 방법 [New Relic 서비스 액세스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) Adobe Commerce 지원 기술 자료

* **[!UICONTROL Non-recommended software in use]**: Adobe Commerce 버전에 따라 Adobe Commerce 인스턴스가 현재 사용 중인 권장되지 않는 소프트웨어를 표시합니다. 권장되지 않는 소프트웨어는 [!UICONTROL Name], [!UICONTROL Installed Version], 및 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: 이미 설치했을 수 있는 패치와 Adobe Commerce 버전을 기준으로 하여 권장되는 패치의 간단한 목록을 표시합니다. 권장되는 패치의 전체 목록은 **[!UICONTROL Patches]** 기능 탭(다음 내에 있음) [!DNL Site-Wide Analysis Tool]. 패치는 다음을 통해 제공됩니다. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 나열된 모든 패치는 현재 Adobe Commerce 인스턴스와 호환됩니다.
Adobe Commerce 인스턴스에 대해 표시할 권장 패치가 없는 경우 [!DNL widget] 이(가) 표시됩니다. **[!UICONTROL No Recommended Patches]**.

## 사용 시기

다음 **[!UICONTROL Dashboard]** 페이지는 의 개요 명령 센터입니다. [!DNL Site-Wide Analysis Tool] 를 통해 사이트 전체의 상태에 대한 &quot;전체적인 그림&quot;을 쉽게 볼 수 있을 뿐만 아니라 Adobe Commerce 웹 사이트에 대한 특정 도구, 권장 사항 및 보고서를 확인하고 액세스할 수 있습니다. [!DNL widget].

## 이점

* 다음 [!DNL widgets] 대상 [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], 및 [!UICONTROL Security Scan] 모두 옆에 그래프 범례가 있고 중앙에 총계가 있는 읽기 쉬운 색상으로 구분된 대화형 원형 그래프를 사용하여 몇 개인지 표시합니다 [!UICONTROL Recommendations], [!UICONTROL Extensions], 및 [!UICONTROL Security Scan Tool] 각 기능에 있는 항목입니다. [!UICONTROL Recommendations] 및 [!UICONTROL Security Scan Tool] 그래프는 심각도로 구분됩니다. [!UICONTROL Extensions] 는 현재 버전, 이전 버전, 비활성화 및 알 수 없음의 4가지 분류로 구분됩니다.

* [!DNL New Relic Alerts] 짧은 설명 및 경고가 발생한 시간 전을 포함하여 가장 최근 경고가 맨 위에 나열됩니다.

* 다음 [!UICONTROL Recommendations] 및 [!UICONTROL Extensions] [!DNL widgets] 을 클릭하여 각 기능의 전체 데이터 페이지에 액세스할 수 있습니다. **[!UICONTROL View All]**.

* 다음 [!UICONTROL Security Scan Tool] 다음 포함 **[!UICONTROL View Report]** 링크 [!DNL widget] 다음 창으로 이동합니다. [!UICONTROL Recommendations] 페이지를 가리키도록 업데이트하는 중입니다.

* 다음 [!DNL Upgrade Compatibility Tool] 다음 포함 **[!UICONTROL Run Upgrade Scan]** 의 단추 [!DNL widget] 창.

## 사용 모범 사례 [!UICONTROL Dashboard]

* 각각 클릭 [!DNL widget] 를 통해 제공되는 세부 데이터에 액세스하여 웹 사이트의 보안, 상태, 권장 사항 및 모범 사례에 대한 통찰력과 이해를 모두 얻어 이를 개선할 수 있습니다.

* 로 이동 [!UICONTROL Security Scan Tool] [!DNL widget] 및 클릭 [!UICONTROL View Report] 을(를) 보려면 [!UICONTROL Recommendations] 사이트에 대해 보고합니다.

* 사용 [!DNL External Resources] 를 통해 추가 정보를 확인하거나 보안 패치, 업데이트 및 모범 사례를 최신 상태로 유지하거나 의 통찰력을 활용할 수 있습니다. [Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce 개발자 설명서(DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [보안 센터](https://helpx.adobe.com/security.html), 및 [Adobe Commerce(OAC)에 대한 관찰](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
