---
title: 액세스 방법 [!DNL Adobe Commerce Patching Automation]
description: ' [!DNL Adobe Commerce Patching Automation]에 액세스하고 사용하는 방법을 알아봅니다.'
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# [!DNL Adobe Commerce Patching Automation]에 액세스하는 방법

## 사전 요구 사항

[!DNL Patching Automation]은(는) Adobe Commerce Cloud의 역할 기반 액세스 제어를 사용합니다. 클라우드 콘솔의 액세스 수준에 따라 서비스로 수행할 수 있는 작업이 결정됩니다.

### [!DNL Patching Automation] 사용 가능 사용자

* **프로젝트 관리자** - 모든 환경에서 패치를 적용하거나 되돌릴 수 있습니다.
* **참가자** - 할당된 환경에서 패치를 적용하거나 되돌릴 수 있습니다.
* **뷰어** - 프로젝트와 환경만 볼 수 있으며 동작은 허용되지 않습니다.

### 프로젝트에 대한 액세스 권한을 요청하는 방법

[!DNL Patching Automation] 사용자 인터페이스에 프로젝트가 없는 경우 적절한 사람에게 액세스 권한을 요청하십시오.

* 프로젝트의 계정 소유자 또는 프로젝트 관리자에게 문의하십시오
* 클라우드 콘솔을 통해 적절한 역할을 부여합니다.
* 액세스 권한이 부여되면 클라우드 콘솔에 로그인하여 서비스를 사용할 수 있습니다

>[!NOTE]
>
>[!DNL Patching Automation]은(는) Adobe Commerce Cloud와 동일한 권한 모델을 따르므로 Cloud Console의 액세스 수준에 따라 서비스로 수행할 수 있는 작업이 결정됩니다.

## [!DNL Patching Automation]에 액세스 중

[!DNL Patching Automation]은(는) [!DNL Site-Wide Analysis Tool] 대시보드에서 탭으로 사용할 수 있습니다. 관리 사이드바에서 **보고서** > **시스템 인사이트** > **사이트 전체 분석 도구**&#x200B;로 이동하여 관리 패널에서 액세스할 수 있습니다. 필수 구성 요소 및 권한 설정에 대해서는 [사이트 전체 분석 도구에 액세스하는 방법](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/site-wide-analysis-tool/access)을 참조하십시오.

대시보드에 들어가면 다음 작업을 수행합니다.

1. 인터페이스에서 [!UICONTROL Patching Automation] 탭을 클릭합니다.
1. 패치를 적용할 프로젝트 및 환경을 선택합니다.
1. 사용 가능한 패치와 호환 상태를 검토합니다.
1. 적용 또는 되돌릴 패치를 선택합니다.

## 프로덕션 환경 액세스

프로덕션 환경에는 기본적으로 다음과 같은 추가 보호 기능이 적용됩니다.

* **유지 관리 모드** - 사용하도록 설정해야 함
* **크론 작업** - 비활성화해야 함
* **확인 대화 상자** - 계속하려면 완료해야 합니다.

>[!IMPORTANT]
>
>프로덕션 환경을 패치하려면 우발적인 중단을 방지하기 위한 적절한 준비와 안전 장치가 필요합니다.

>[!NOTE]
>
>UI(*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*)에서 재정의 확인란을 선택하여 유지 관리 모드 및 cron-job 검사를 건너뛸 수 있습니다. 이러한 안전 장치를 사용하지 않고 프로덕션 패치할 위험을 알고 있는 경우에만 사용하십시오.

## 관련 항목

* [패치 자동화 소개](intro.md)
* [워크플로우 개요](workflow.md)
* [GitHub 통합](github-integration.md)
* [우수 사례](best-practices.md)
* [문제 해결](troubleshooting.md)
