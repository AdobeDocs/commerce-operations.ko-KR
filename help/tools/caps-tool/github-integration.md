---
title: ' [!DNL CAPS]에 대한 GitHub 통합 설정'
description: GitHub에 연결된 Adobe Commerce Cloud 프로젝트에 대한 패치 작업을 활성화하기 위해  [!DNL Cloud Automation Patching Service (CAPS)] GitHub 앱을 설치하는 방법을 알아봅니다.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# [!DNL CAPS]에 대한 GitHub 통합 설정

Adobe Commerce Cloud 프로젝트가 GitHub 저장소에 연결된 경우 [!DNL Cloud Automation Patching Service]&#x200B;([!DNL CAPS])을(를) 사용하여 패치를 적용하거나 되돌리려면 먼저 [!DNL CAPS] GitHub 앱을 설치해야 합니다. 이 앱은 사용자를 대신하여 리포지토리를 변경하는 데 필요한 액세스 권한을 [!DNL CAPS]에게 부여합니다.

## 사전 요구 사항

* 활성 Adobe Commerce Cloud 구독
* [GitHub 통합](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)이(가) [`fetch-branches` 옵션을 사용하도록 설정](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)한 상태로 Adobe Commerce Cloud 프로젝트에 대해 이미 구성되었습니다. [!DNL CAPS]이(가) 임시 통합 환경 분기를 만들고 푸시하므로 이 옵션을 사용하지 않도록 설정하면 패치 작업에서 환경을 만들지 못합니다.
* [!DNL github.com]에 호스팅된 리포지토리입니다. 사용자 정의 도메인으로 구성된 GitHub 통합은 지원되지 않습니다.
* GitHub 조직 또는 저장소에 대한 소유자 또는 관리자 액세스

## [!DNL CAPS] GitHub 앱 설치

1. [CAPS GitHub 앱 설치 페이지를 엽니다](https://github.com/apps/adobe-commerce-patching-automation).
1. **[!UICONTROL Install]**&#x200B;을(를) 클릭합니다.
1. Adobe Commerce 저장소를 소유한 GitHub 조직을 선택합니다.
1. **[!UICONTROL Repository access]**&#x200B;에서 **[!UICONTROL Only select repositories]**&#x200B;을(를) 선택하고 Adobe Commerce 프로젝트에 대한 저장소를 선택합니다.
1. **[!UICONTROL Install]**&#x200B;을(를) 클릭하여 확인합니다.

[!DNL CAPS]이(가) 설치되면 GitHub 연결을 자동으로 감지하여 모든 패치 작업에 앱을 사용합니다. 추가 설정이 필요하지 않습니다.

## [!DNL CAPS] GitHub 앱 제거

[!DNL CAPS]이(가) 저장소에 더 이상 액세스하지 않도록 하려면 다음을 수행하십시오.

1. GitHub에서 설치를 소유하는 계정에 대한 설정을 엽니다.
   * **조직 소유** 저장소의 경우: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * **personal** 리포지토리의 경우: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. `adobe-commerce-patching-automation`을(를) 찾아 **[!UICONTROL Configure]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Uninstall]**&#x200B;을(를) 클릭하고 확인합니다.

>[!WARNING]
>
>GitHub 앱을 제거할 때 CAPS 적용 또는 되돌리기 작업이 계속 진행 중인 경우 해당 작업이 실패할 수 있습니다. 앱을 제거한 후에는 작업 버튼이 비활성화되므로 새 작업을 시작할 수도 없습니다.

## 관련 항목

* [CAPS 소개](intro.md)
* [액세스 방법](access.md)
* [워크플로우 개요](workflow.md)
* [우수 사례](best-practices.md)
* [문제 해결](troubleshooting.md)
