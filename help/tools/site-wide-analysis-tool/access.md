---
title: 액세스 방법 [!DNL Site-Wide Analysis Tool]
description: Adobe Commerce 관리 패널에서 사이트 전체 분석 도구 대시보드에 액세스하는 방법을 알아봅니다. 사용자 권한 및 역할 요구 사항을 알아봅니다.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]에 액세스하는 방법

스토어의 [!DNL Site-Wide Analysis Tool]에서 [!UICONTROL Admin Panel] 대시보드에 액세스할 수 있습니다.

[!DNL Site-Wide Analysis Tool] 서비스는 [역할 리소스](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes)에 액세스할 수 있는 권한이 있는 [!UICONTROL Admin] 사용자에 대해 [프로덕션 모드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)에서 사용할 수 있습니다.

>[!NOTE]
>
>2024년 4월 23일부터 [!DNL Site-Wide Analysis Tool]이(가) 서비스 해제되어 Adobe Commerce 온-프레미스 고객이 더 이상 사용할 수 없습니다.


![사이트 전체 분석 대시보드](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]대시보드*

>[!NOTE]
>
>**[!DNL Support Permissions]**&#x200B;에 액세스하려면 계정에 [!DNL Site-Wide Analysis Tool Dashboard] 권한이 있어야 합니다.
>>자세한 내용은 사용 안내서의 [계정 공유 [!DNL Commerce] 에서 확인하세요](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html).

## 스토어의 [!DNL Site-Wide Analysis Tool Dashboard]에서 [!UICONTROL Admin Panel]에 로그인

### 1단계: 권한 확인

[!UICONTROL Admin] 사용자 계정에 [!DNL Site-Wide Analysis Tool]할당된 사용자 역할[을(를) 통해 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)에 액세스할 수 있는 권한이 있는지 확인하십시오.

>[!IMPORTANT]
>
>[!DNL Site-Wide Analysis Tool] 역할 리소스(권한)가 **자동 할당되지 않음**. [!UICONTROL Admin]의 각 사용자 계정에 개별적으로 할당된 사용자 역할 및 역할에 대해 활성화해야 합니다.

[!DNL Site-Wide Analysis Tool] 액세스 권한이 필요한 사용자 지정 역할에 대해 다음을 수행하십시오.

1. **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** 역할 리소스를 선택합니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]역할에 대해* 권한이 선택됨

1. **[!UICONTROL Save Role]**&#x200B;을(를) 클릭합니다.

1. 해당 역할이 할당된 사용자에게 [!DNL Admin]에서 로그아웃하도록 알리고 다시 로그인하세요.

>[!NOTE]
>
>사용자 계정에 [!DNL Site-Wide Analysis Tool]에 액세스할 수 있는 권한이 있고 사용자가 [!UICONTROL Admin]에서 도구에 액세스하려고 할 때 403 오류가 발생하는 경우 클라우드 인프라의 Adobe Commerce 인스턴스에서 HTTP 액세스 제어를 사용하도록 설정할 수 있습니다. HTTP 인증을 사용하도록 설정한 경우 [!DNL Site-Wide Analysis Tool] 대시보드가 지원되지 않습니다. 이 문제를 해결하는 방법에 대한 자세한 내용은 [지원 문서](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento)를 참조하세요.

### 2단계: [!DNL Site-Wide Analysis Tool]에 액세스

1. *[!UICONTROL Admin]* 사이드바에서 **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**(으)로 이동합니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/ac-admin-panel-marked.jpg)
   Adobe Commerce에서 *[!DNL Site-Wide Analysis Tool]의 [!UICONTROL Admin Panel] 위치*

1. *의*&#x200B;사용 약관[!DNL Site-Wide Analysis Tool]을 읽고 계속하려면 **[!UICONTROL Accept]**&#x200B;을(를) 클릭하십시오.

   각 사용자는 세션에 대한 사용 약관에 동의해야 합니다. 이 단계는 로그인한 각 세션에 대해 반복됩니다.


1. 대시보드 맨 위에서 보려는 탭을 클릭합니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]정보*

## [!DNL Site-Wide Analysis Tool Dashboard]에서 보고서 생성

1. 대시보드의 오른쪽 위 모서리에서 **[!UICONTROL Generate Report]**&#x200B;을(를) 클릭합니다.

1. 보고서에 포함할 각 **[!UICONTROL Type]** 및 **[!UICONTROL Priority]** 설정에 대한 확인란을 선택하십시오.

1. **[!UICONTROL Generate Report]**&#x200B;을(를) 클릭합니다.

   ![사이트 전체 분석 대시보드](../../assets/tools/swat-report-settings.png)
   *보고서 설정*

| 탭 | 설명 |
| --- | --- |
| 대시보드 | 우선 순위별 현재 알림 및 권장 사항과 함께 시스템 상태를 표시합니다. |
| 정보 | 설치된 각 Adobe Commerce 제품에 대한 자세한 정보와 함께 고객 연락처 정보 및 현재 티켓의 요약을 제공합니다. |
| 권장 사항 | 사이트에서 감지된 문제를 해결하기 위한 모범 사례를 기반으로 권장 사항을 나열합니다. |
| 예외 | 오류 처리기 없이 비정상 조건으로 인해 응용 프로그램에서 발생하는 오류를 나열합니다. |
| 확장 | 모든 타사 확장 및 타사 라이브러리를 나열합니다. |

>[!NOTE]
>
>권장 사항을 적용한 후 [!DNL Site-Wide Analysis Tool Dashboard] 또는 생성된 보고서에서 업데이트되는 데 며칠이 걸릴 수 있습니다.
