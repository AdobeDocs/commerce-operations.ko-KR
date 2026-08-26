---
title: ' [!DNL Adobe Commerce Patching Automation]에 대한 GitHub 통합 설정'
description: GitHub에 연결된 Adobe Commerce Cloud 프로젝트에 대한 패치 작업을 활성화하기 위해  [!DNL Adobe Commerce Patching Automation] GitHub 앱을 설치하는 방법을 알아봅니다.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# [!DNL Patching Automation]에 대한 GitHub 통합 설정

Adobe Commerce Cloud 프로젝트가 GitHub 리포지토리에 연결되어 있는 경우 서비스를 사용하여 패치를 적용하거나 되돌리려면 먼저 [!DNL Patching Automation] GitHub 앱을 설치해야 합니다. 이 앱은 사용자를 대신하여 저장소를 변경하는 데 필요한 액세스 권한을 서비스에 부여합니다.

## 사전 요구 사항

* 활성 Adobe Commerce Cloud 구독
* [GitHub 통합](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)이(가) [`fetch-branches` 옵션을 사용하도록 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)한 상태로 Adobe Commerce Cloud 프로젝트에 대해 이미 구성되었습니다. [!DNL Patching Automation]이(가) 임시 통합 환경 분기를 만들고 푸시하므로 이 옵션을 사용하지 않도록 설정하면 패치 작업에서 환경을 만들지 못합니다.
* [!DNL github.com]에 호스팅된 리포지토리입니다. 사용자 정의 도메인으로 구성된 GitHub 통합은 지원되지 않습니다.
* GitHub 조직 또는 저장소에 대한 소유자 또는 관리자 액세스

## [!DNL Patching Automation] GitHub 앱 설치

UI에서 **[!UICONTROL Install GitHub App]**&#x200B;을(를) 클릭하여 설치 페이지로 리디렉션하거나 설치 페이지로 직접 이동하여 [!DNL Patching Automation]에서 설치를 시작할 수 있습니다.

1. [Patching Automation GitHub App 설치 페이지](https://github.com/apps/adobe-commerce-patching-automation)를 엽니다.
1. **[!UICONTROL Install]**&#x200B;을(를) 클릭합니다.
1. Adobe Commerce 저장소를 소유한 GitHub 조직을 선택합니다.
1. **[!UICONTROL Repository access]**&#x200B;에서 **[!UICONTROL Only select repositories]**&#x200B;을(를) 선택하고 Adobe Commerce 프로젝트에 대한 저장소를 선택합니다.
1. **[!UICONTROL Install]**&#x200B;을(를) 클릭하여 확인합니다.

설치가 완료되면 서비스는 GitHub 연결을 자동으로 감지하고 모든 패치 작업에 앱을 사용합니다. 추가 설정이 필요하지 않습니다.

## 연결 상태 확인 및 관리

[!DNL Patching Automation] UI는 GitHub 연결의 현재 상태를 표시하며 해당 상태에 따라 사용 가능한 작업을 표시합니다.

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** - 변경하지 않고 연결 상태를 다시 확인합니다.
* **[!UICONTROL Reinstall]** - 설치가 더 이상 유효하지 않은 경우(예: 일시 중단되었거나 클라우드 프로젝트에 연결된 저장소가 변경된 경우) 표시됩니다. 위에서 설명한 것과 동일한 설치 흐름을 시작합니다.
* **[!UICONTROL Unlink GitHub App]** - GitHub 앱에 저장된 [!DNL Patching Automation]의 연결을 제거합니다. 이렇게 하면 GitHub 저장소에서 앱을 **제거하지**&#x200B;않습니다. 액세스 권한을 완전히 제거하려면 아래 제거 섹션을 참조하십시오.

## [!DNL Patching Automation] GitHub 앱 제거

서비스가 저장소에 더 이상 액세스하지 않으려는 경우:

1. GitHub에서 설치를 소유하는 계정에 대한 설정을 엽니다.
   * **조직 소유** 저장소의 경우: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * **personal** 리포지토리의 경우: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. `adobe-commerce-patching-automation`을(를) 찾아 **[!UICONTROL Configure]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Uninstall]**&#x200B;을(를) 클릭하고 확인합니다.

>[!WARNING]
>
>GitHub 앱을 제거할 때 적용 또는 되돌리기 작업이 계속 진행 중인 경우 해당 작업이 실패할 수 있습니다. 앱을 제거한 후에는 작업 버튼이 비활성화되므로 새 작업을 시작할 수도 없습니다.

## 관련 항목

* [패치 자동화 소개](intro.md)
* [액세스 방법](access.md)
* [워크플로우 개요](workflow.md)
* [우수 사례](best-practices.md)
* [문제 해결](troubleshooting.md)
