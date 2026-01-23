---
title: '[!DNL Dashboard]'
description: ' [!DNL Dashboard] 의  [!DNL Site-Wide Analysis Tool]탭, 요소, 사용 시기, 이점 및 모범 사례에 대해 알아봅니다.'
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

[!UICONTROL Dashboard] 페이지에는 Adobe Commerce 웹 사이트의 상태 및 현재 상태에 대한 &quot;단일 창 보기&quot;를 제공하는 [!DNL widgets]이(가) 한 눈에 표시됩니다. 각 [!DNL widget]에는 [!DNL widget]에 따라 각 기능의 페이지, 도구 자체 또는 보고서에 대한 액세스 링크가 있습니다.
[!UICONTROL External Resources]Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터) [, &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=ko)Adobe Commerce 개발자 설명서(DevDocs) [, &#x200B;](https://developer.adobe.com/commerce/docs/): 패치 검색[[!DNL Quality Patches Tool], &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}보안 센터[, &#x200B;](https://helpx.adobe.com/kr/security.html)Adobe Commerce 관찰(OAC) [을 포함하여 &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=ko)개의 Adobe Commerce 링크 목록도 있습니다.

## 요소

* **[!UICONTROL Recommendations]**: 사이트에 대한 모범 사례 권장 사항을 표시합니다. 권장 사항(발견된 문제 및 수정할 권장 사항)은 우선 순위(P0(중요) ~ P4(알림)로 정렬됩니다.
권장 사항에는 설명, 권장 사항, 사이트 영향, 근본 원인, 시나리오/사전 조건 및 사용된 도구가 포함됩니다.

* **[!UICONTROL Upgrade Compatibility Tool]**: 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인합니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다. 또한 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 수정해야 하는 잠재적인 문제를 식별합니다.
[!UICONTROL Upgrade Compatibility Tool]을(를) 사용하면 사용자 지정된 기능에 대한 핵심 코드가 변경된 시기를 식별할 수 있습니다.

* **[!UICONTROL Security Center Widget]**: 사이트에 대한 보안 인사이트를 표시합니다.
표시되는 보안 정보에는 [기술 [!DNL Stack] 최상의 보안 권장 사항을 준수하는 버전 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=ko), [Adobe Security Bulletin](https://helpx.adobe.com/kr/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ko), and [[!DNL Site-Wide Analysis Tool] 보안 권장 사항](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=ko)이 포함됩니다.<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ko)은(는) 보안 위험이 있는지 Adobe Commerce 사이트를 모니터링합니다. 가맹점의 악성코드를 선제적이고 효율적으로 탐지해 보안 위험, 악성코드, 위협 등이 있으면 가맹점에 알리고, Adobe Commerce 패치와 업데이트 누락 등을 파악할 수 있다.

* **[!UICONTROL Extensions]**: 현재 Adobe Commerce 인스턴스에 설치된 확장을 표시합니다. [Adobe Commerce 마켓플레이스](https://commercemarketplace.adobe.com//extensions.html) 정보가 제공됩니다(사용 가능한 경우). 여기에 나열된 확장에 대해 사용할 수 있습니다.

* **[!UICONTROL Alerts]**: Adobe Commerce 인스턴스에 대한 최신 [!DNL New Relic Managed Alerts]을(를) 표시합니다. Adobe Commerce 지원 기술 자료에서 [Adobe Commerce에 대한 관리 경고](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html?lang=ko)와 [New Relic 서비스에 액세스](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=ko)하는 방법에 대해 자세히 알아보세요.

* **[!UICONTROL Non-recommended software in use]**: Adobe Commerce 버전에 따라 Adobe Commerce 인스턴스가 현재 사용 중인 권장되지 않는 소프트웨어를 표시합니다. 권장되지 않는 소프트웨어는 [!UICONTROL Name], [!UICONTROL Installed Version] 및 [!UICONTROL Recommended Version]&#x200B;(으)로 나열됩니다.

* **[!UICONTROL Recommended Patches]**: 이미 설치되어 있을 수 있는 패치와 Adobe Commerce 버전을 기준으로 하는 권장 패치의 간단한 목록을 표시합니다. 권장 패치의 전체 목록은 **[!UICONTROL Patches]** 기능 탭과 [!DNL Site-Wide Analysis Tool] 내에 있습니다. 패치는 [[!DNL Quality Patches Tool]에서 제공됩니다. 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}. 나열된 모든 패치는 현재 Adobe Commerce 인스턴스와 호환됩니다.
Adobe Commerce 인스턴스에 대해 표시할 권장 패치가 없으면 이 [!DNL widget]에 **[!UICONTROL No Recommended Patches]**&#x200B;이(가) 표시됩니다.

## 사용 시기

**[!UICONTROL Dashboard]** 페이지는 [!DNL Site-Wide Analysis Tool]의 한눈에 볼 수 있는 명령 센터로서 사이트 전체의 상태에 대한 &quot;주요 상황&quot;을 쉽게 볼 수 있을 뿐만 아니라 각 [!DNL widget]을(를) 통해 Adobe Commerce 웹 사이트에 대한 특정 도구, 권장 사항 및 보고서를 확인하고 액세스할 수 있습니다.

## 이점

* [!DNL widgets], [!UICONTROL Security Center], [!UICONTROL Recommendations] 및 [!UICONTROL Extensions]에 대한 [!UICONTROL Security Scan]은(는) 모두 옆에 그래프 범례가 있는 읽기 쉬운 색상으로 구분된 대화형 순환 그래프를 사용하며 중앙의 합계를 계산하여 각 기능에 포함된 [!UICONTROL Recommendations], [!UICONTROL Extensions] 및 [!UICONTROL Security Scan Tool]개 항목의 수를 나타냅니다. [!UICONTROL Recommendations] 및 [!UICONTROL Security Scan Tool] 그래프는 심각도로 구분됩니다. [!UICONTROL Extensions]은(는) 현재 버전, 이전 버전, 사용 안 함 및 알 수 없음의 네 가지 분류로 구분됩니다.

* [!DNL New Relic Alerts]이(가) 맨 위에 있으며, 여기에는 간단한 설명과 경고가 발생한 기간이 포함됩니다.

* [!UICONTROL Recommendations] 및 [!UICONTROL Extensions] [!DNL widgets]은(는) **[!UICONTROL View All]**&#x200B;을(를) 클릭하여 각 기능의 전체 데이터 페이지에 액세스할 수 있습니다.

* [!UICONTROL Security Scan Tool]의 **[!UICONTROL View Report]** 창에 [!DNL widget] 페이지로 이동하는 [!UICONTROL Recommendations] 링크가 있습니다.

* [!DNL Upgrade Compatibility Tool]의 **[!UICONTROL Run Upgrade Scan]** 창에 [!DNL widget] 단추가 있습니다.

## [!UICONTROL Dashboard] 사용에 대한 모범 사례

* 각 [!DNL widget]을(를) 클릭하면 insight과 웹 사이트의 보안, 상태, 권장 사항 및 모범 사례를 모두 이해하고 이를 개선하기 위해 제공하는 자세한 데이터에 액세스할 수 있습니다.

* 사이트에 대한 [!UICONTROL Security Scan Tool] 보고서를 보려면 [!DNL widget] [!UICONTROL View Report]&#x200B;(으)로 이동하고 [!UICONTROL Recommendations]을(를) 클릭하십시오.

* [!DNL External Resources] 링크를 사용하여 자세한 정보를 알아보거나 보안 패치, 업데이트 및 모범 사례를 최신 상태로 유지하거나 [Adobe Commerce 도움말 센터 지원 기술 자료(도움말 센터)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=ko), [Adobe Commerce 개발자 설명서(DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko){target="_blank"}, [보안 센터](https://helpx.adobe.com/kr/security.html) 및 [OAC(Adobe Commerce에 대한 관찰)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=ko)의 insight을 활용하십시오.
