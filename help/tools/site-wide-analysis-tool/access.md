---
title: 액세스 방법 [!DNL Site-Wide Analysis Tool]
description: 에 액세스하는 방법 알아보기 [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 액세스 방법 [!DNL Site-Wide Analysis Tool]

다음 [!DNL Site-Wide Analysis Tool] 다음에서 서비스를 사용할 수 있습니다. [프로덕션 모드](https://docs.magento.com/user-guide/magento/installation-modes.html) 대상 [!DNL Admin] 사용자 액세스 권한이 있는 사용자 [역할 리소스](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Adobe Commerce을 온-프레미스에 설치한 경우 [에이전트](../site-wide-analysis-tool/installation.md) 을 참조하십시오.

![사이트 전체 분석 대시보드](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]대시보드*

## 1단계: 권한 확인

다음을 확인합니다 [!DNL Admin] 사용자 계정에는 액세스 권한이 있습니다. [!DNL Site-Wide Analysis Tool] 을 통해 [할당된 사용자 역할](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>다음 [!DNL Site-Wide Analysis Tool] 역할 리소스(권한)는 **아님** 자동 할당됨. 사용자 역할 및 의 각 사용자 계정에 개별적으로 할당된 역할에 대해 활성화해야 합니다. [!UICONTROL Admin].

필요한 사용자 정의 역할에 대해 [!DNL Site-Wide Analysis Tool] 액세스, 다음을 수행합니다.

1. 다음 항목 선택 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 역할 리소스.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]역할에 대해 선택된 권한*

1. 클릭 **[!UICONTROL Save Role]**.

1. 해당 역할이 할당된 모든 사용자에게 로그아웃하도록 알림 [!DNL Admin]을 클릭하고 다시 로그인합니다.

>[!NOTE]
>
>사용자 계정에 액세스할 수 있는 권한이 있는지 확인한 경우 [!DNL Site-Wide Analysis Tool] 및에서 도구에 액세스하려고 하면 403 오류가 표시됩니다. [!DNL Admin]: 클라우드 인프라의 Adobe Commerce 인스턴스에서 HTTP 액세스 제어를 활성화할 수 있습니다. 다음 [!DNL Site-Wide Analysis Tool] HTTP 인증이 활성화된 경우 대시보드가 지원되지 않습니다. 이 문제 해결에 대한 자세한 내용은 [지원 문서](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## 2단계: 액세스 [!DNL Site-Wide Analysis Tool]

1. 다음에서 *[!UICONTROL Admin]* 사이드바, 이동 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. 읽기 *사용 약관* 대상: [!DNL Site-Wide Analysis Tool] 및 클릭 **[!UICONTROL Accept]** 계속합니다.

   각 사용자는 세션에 대한 사용 약관에 동의해야 합니다. 이 단계는 로그인한 각 세션에 대해 반복됩니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-tos.png)
   *사용 약관*

1. 대시보드 맨 위에서 보려는 탭을 클릭합니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]정보*

## 3단계: 보고서 생성

1. 대시보드의 오른쪽 위 모서리에서 을(를) 클릭합니다. **[!UICONTROL Generate Report]**.

1. 각각에 대한 확인란을 선택합니다. **[!UICONTROL Type]** 및 **[!UICONTROL Priority]** 보고서에 포함할 설정입니다.

1. 클릭 **[!UICONTROL Generate Report]**.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-report-settings.png)
   *보고서 설정*

| 탭 | 설명 |
| --- | --- |
| 대시보드 | 우선 순위별 현재 알림 및 권장 사항과 함께 시스템 상태를 표시합니다. |
| 정보 | 설치된 각 Adobe Commerce 제품에 대한 자세한 정보와 함께 고객 연락처 정보 및 현재 티켓의 요약을 제공합니다. |
| Recommendations | 사이트에서 감지된 문제를 해결하기 위한 모범 사례를 기반으로 권장 사항을 나열합니다. |
| 예외 | 오류 처리기 없이 비정상 조건으로 인해 응용 프로그램에서 발생하는 오류를 나열합니다. |
| 확장 | 모든 타사 확장 및 타사 라이브러리를 나열합니다. |

>[!NOTE]
>
>권장 사항을 적용한 후에서 업데이트되기까지 며칠이 걸릴 수 있습니다. [!DNL Site-Wide Analysis Tool] 대시보드 또는 생성된 보고서입니다.
