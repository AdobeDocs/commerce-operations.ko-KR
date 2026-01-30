---
title: '[!DNL Site-Wide Analysis Tool]'
description: ' [!DNL Site-Wide Analysis] 도구, 사용 방법, 설치 프로세스 및 액세스 방법에 대해 알아봅니다.'
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>2024년 4월 23일부터 모든 Adobe Commerce 온-프레미스 고객에 대한 [!DNL Site-Wide Analysis Tool]의 서비스가 중단됩니다.

이 안내서에서는 [!DNL Site-Wide Analysis Tool]에 대한 전체적인 개요를 제공합니다. 사용, 설치 단계별 지침 및 도구에 액세스하는 방법에 대해 설명합니다.

## [!DNL Site-Wide Analysis Tool]은(는) 무엇입니까?

[!DNL Site-Wide Analysis Tool]은(는) Adobe Commerce 설치의 보안 및 운영을 보장하기 위한 자세한 시스템 통찰력과 권장 사항이 포함된 사전 예방적 셀프서비스 도구이자 중앙 저장소입니다. 24시간 연중무휴 실시간 성능 모니터링, 보고서 및 조언을 제공하여 잠재적인 문제를 식별하고 사이트 상태, 안전 및 애플리케이션 구성에 대한 가시성을 향상시킵니다. 이는 해결 시간을 줄이고 사이트 안정성과 성능을 개선하는 데 도움이 됩니다.

>[!NOTE]
>
>권장 사항을 적용한 후 사이트 전체 분석 도구 대시보드 또는 생성된 보고서에서 업데이트되기까지 며칠이 걸릴 수 있습니다.
>
>[!DNL Site-Wide Analysis Tool]이(가) 시스템 수준 데이터에 대해 보고합니다. Adobe Commerce 제품, 판매, 마케팅 및 기타 상거래 응용 프로그램 데이터에 대한 보고서는 [Adobe Commerce 보고서](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)를 참조하십시오.

![사이트 전체 분석 도구 대시보드](../../assets/tools/swat-dashboard.png){zoomable="yes"}

자세한 내용은 이 [소개 비디오](https://www.youtube.com/watch?v=KW2R8ki_RG4)를 참조하세요.

## 도구 개요

- **대시보드**
   - 감지된 문제에 대한 알림 및 우선 순위별 특정 권장 사항과 함께 시스템의 전체 상태를 표시합니다.<br>
또한 웹 사이트의 상태가 시간에 따라 어떻게 변하는지를 추적하는 기록 차트가 포함되어 있습니다.
   - 다음 리소스에 대한 링크를 제공하는 **[!UICONTROL Security Center Widget]**&#x200B;을(를) 표시합니다.
      - [기술 [!DNL Stack] 버전 준수  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Adobe 보안 게시판](https://helpx.adobe.com/security/security-bulletin.html)
      - [추천 항목 [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool] 모범 사례 보안 권장 사항](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **정보** - 설치된 각 Adobe Commerce 제품에 대한 자세한 정보를 포함하여 고객 연락처 정보와 현재 티켓의 요약을 제공합니다.

- **권장 사항** - 사이트 상태를 추적하기 위해 [SWAT 상태 인덱스 점수를 제공](#swat-health-index.md)하고, 사이트에서 발견된 문제를 해결하기 위해 모범 사례를 기반으로 권장 사항을 나열합니다.
   - 인프라 업데이트가 필요한 변경 사항에 대해서는 지원 요청을 제출합니다.
   - 응용 프로그램을 업데이트해야 하는 변경 사항의 경우 직접 변경합니다.
   - [코드 배포](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow)와 같이 수동 개입이 필요한 변경 사항에 대해서는 시스템 관리자 또는 개발자에게 도움을 요청하십시오.

- **예외** - 오류 처리기 없이 비정상 조건으로 인해 응용 프로그램에서 발생하는 오류를 나열합니다.

- **확장** - 모든 타사 확장 및 타사 라이브러리를 나열합니다.

- **패치** - [!DNL Quality Patches Tool]과(와) 통합되었으며 Adobe Commerce 인스턴스에 대해 사용 가능한 모든 패치 목록을 제공합니다.

## 다른 Adobe Commerce 지원 도구와의 통합

사이트에 대한 중요한 통찰력을 한 곳에서 볼 수 있습니다. [!DNL Site-Wide Analysis Tool]을(를) 사용하면 [!UICONTROL Security Center Widget], [!DNL Upgrade Compatibility Tool] 및 [!DNL Managed Alerts]에서 및 정보에 직접 액세스할 수 있습니다.

- **[!UICONTROL Security Center Widget]** - 사이트에 대한 보안 인사이트를 표시합니다.<br>
보안 정보에는 [기술 [!DNL Stack] 보안 권장 사항 모범 사례 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool] 를 통한 버전 준수](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)가 포함되어 있습니다.

  [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)은(는) 맬웨어를 사전에 감지하고 스토어가 손상된 경우 경고하여 Adobe Commerce 및 Magento Open-Source 고객에게 스토어의 보안 상태에 대한 실시간 통찰력을 제공합니다.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - 업그레이드 버전에 대해 Adobe Commerce 인스턴스를 확인하고 업그레이드하기 전에 수정해야 할 중요한 문제, 오류 및 경고에 플래그를 지정합니다. 이러한 문제를 해결하면 업그레이드 프로세스를 간소화할 수 있습니다.&quot;

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - 주요 지표(CPU, 응용 프로그램 성능, 디스크, 메모리 및 데이터베이스 상태)를 모니터링하고 판매자가 문제를 미리 방지하고 가동 중단을 피할 수 있도록 명확한 문제 해결 단계를 제공합니다.

## 이 가이드는 누구의 것인가요?

Adobe Commerce 웹 사이트에 대한 가시성을 높이기를 원하는 판매자와 파트너입니다. 이를 통해 상인은 고객의 경험을 개선하고 모범 사례 권장 사항 및 기본 문제에 보다 가깝게 조정할 수 있습니다.

## [!DNL Site-Wide Analysis Tool] 데모

[!DNL Site-Wide Analysis Tool]에 대해 알아보려면 이 비디오를 시청하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
