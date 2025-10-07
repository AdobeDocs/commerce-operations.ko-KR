---
title: '[!DNL Site-Wide Analysis Tool]'
description: ' [!DNL Site-Wide Analysis] 도구, 사용 방법, 설치 프로세스 및 액세스 방법에 대해 알아봅니다.'
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 23c5da67003ecd1939ea168a843e974b65977063
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>2024년 4월 23일부터 모든 Adobe Commerce 온-프레미스 고객에 대한 [!DNL Site-Wide Analysis Tool]의 서비스가 중단됩니다.

이 안내서에서는 [!DNL Site-Wide Analysis Tool]에 대한 전체적인 개요를 제공합니다. 사용, 설치 단계별 지침 및 도구에 액세스하는 방법에 대해 설명합니다.

## [!DNL Site-Wide Analysis Tool]이란?

[!DNL Site-Wide Analysis Tool]은(는) Adobe Commerce 설치의 보안 및 운영을 보장하기 위한 자세한 시스템 통찰력과 권장 사항이 포함된 사전 예방적 셀프서비스 도구이자 중앙 저장소입니다. 24시간 연중무휴 실시간 성능 모니터링, 보고서 및 조언을 제공하여 잠재적인 문제를 식별하고 사이트 상태, 안전 및 애플리케이션 구성에 대한 가시성을 향상시킵니다. 이는 해결 시간을 줄이고 사이트 안정성과 성능을 개선하는 데 도움이 됩니다.

>[!NOTE]
>
>[!DNL Site-Wide Analysis Tool]이(가) 시스템 수준 데이터에 대해 보고합니다. Adobe Commerce 제품, 판매, 마케팅 및 기타 상거래 응용 프로그램 데이터에 대한 보고서는 [Adobe Commerce 보고서](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/reporting/reports-menu)를 참조하십시오.

![사이트 전체 분석 도구 대시보드](../../assets/tools/swat-dashboard.png){zoomable="yes"}

자세한 내용은 이 [소개 비디오](https://www.youtube.com/watch?v=KW2R8ki_RG4)를 참조하세요.

## 도구 개요

- **대시보드**
   - 감지된 문제에 대한 알림 및 우선 순위별 특정 권장 사항과 함께 시스템의 전체 상태를 표시합니다.<br>
또한 웹 사이트의 상태가 시간에 따라 어떻게 변하는지를 추적하는 기록 차트가 포함되어 있습니다.
   - 다음에 액세스할 수 있는 **[!UICONTROL Security Center Widget]**&#x200B;을(를) 표시합니다.
      - [기술 [!DNL Stack] 버전 준수  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=ko)
      - [Adobe 보안 게시판](https://helpx.adobe.com/kr/security/security-bulletin.html)
      - [추천 항목 [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ko)
      - [[!DNL Site-Wide Analysis Tool] 모범 사례 보안 권장 사항](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=ko)

- **정보** - 설치된 각 Adobe Commerce 제품에 대한 자세한 정보를 포함하여 고객 연락처 정보와 현재 티켓의 요약을 제공합니다.

- **권장 사항** - 사이트 상태를 추적하기 위해 [SWAT 상태 인덱스 점수를 제공](#swat-health-index.md)하고, 사이트에서 발견된 문제를 해결하기 위해 모범 사례를 기반으로 권장 사항을 나열합니다.
   - 인프라 업데이트가 필요한 변경 사항에 대해서는 지원 요청을 제출합니다.
   - 응용 프로그램을 업데이트해야 하는 변경 사항의 경우 직접 변경합니다.
   - [코드 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=ko#deployment-workflow)와 같이 수동 개입이 필요한 변경 사항에 대해서는 시스템 관리자 또는 개발자에게 도움을 요청하십시오.

- **예외** - 오류 처리기 없이 비정상 조건으로 인해 응용 프로그램에서 발생하는 오류를 나열합니다.

- **확장** - 모든 타사 확장 및 타사 라이브러리를 나열합니다.

- **패치** - [!DNL Quality Patches Tool]과(와) 통합되었으며 Adobe Commerce 인스턴스에 대해 사용 가능한 모든 패치 목록을 제공합니다.

## 다른 Adobe Commerce 지원 도구와의 통합

사이트에 대한 모든 중요한 통찰력을 한 곳에서 볼 수 있습니다. [!DNL Site-Wide Analysis Tool]을(를) 사용하면 [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] 및 [!DNL Managed Alerts]에서 및 정보에 직접 액세스할 수 있습니다.

- **[!UICONTROL Security Center Widget]** - 사이트에 대한 보안 인사이트를 표시합니다.<br>
표시되는 보안 정보에는 [기술 [!DNL Stack] 보안 권장 사항 모범 사례 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=ko), [Adobe Security Bulletin](https://helpx.adobe.com/kr/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ko), and [[!DNL Site-Wide Analysis Tool] 를 준수하는 버전](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=ko)이 포함됩니다.<br>
[[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ko)은(는) 맬웨어를 사전에 감지하고 스토어가 손상된 경우 알림으로써 Adobe Commerce 및 Magento Open-Source 고객에게 스토어의 보안 상태에 대한 실시간 통찰력을 제공합니다.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - 대상 업그레이드 버전에 대해 Adobe Commerce의 사용자 지정 인스턴스를 실행하고 해결해야 하는 중요한 문제, 오류 및 경고에 대한 요약을 반환하여 업그레이드 분석 프로세스를 보다 쉽고 빠르고 저렴하게 만듭니다.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - 여러 지표를 모니터링하여 플랫폼의 성능을 미리 추적하고 문제를 해결하는 방법에 대한 특정 지침을 제공하므로 판매자가 중요한 다운타임을 방지하고 CPU, 애플리케이션 성능, 디스크, 메모리 및 데이터베이스에 대한 정보를 계속 얻을 수 있습니다.

## 이 가이드는 누구의 것인가요?

Adobe Commerce 웹 사이트에 대한 가시성을 높이기를 원하는 판매자와 파트너입니다. 이를 통해 상인은 고객의 경험을 개선하고 모범 사례 권장 사항 및 기본 문제에 대해 보다 세밀하게 조정할 수 있습니다.

## [!DNL Site-Wide Analysis Tool] 데모

[!DNL Site-Wide Analysis Tool]에 대해 알아보려면 이 비디오를 시청하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3410780?quality=12&captions=kor)
