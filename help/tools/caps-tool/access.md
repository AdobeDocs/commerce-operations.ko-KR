---
title: 액세스 방법 [!DNL Cloud Automation Patching Service (CAPS)]
description: ' [!DNL Cloud Automation Patching Service (CAPS)]에 액세스하고 사용하는 방법을 알아봅니다.'
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Cloud Automation Patching Service (CAPS)]에 액세스하는 방법

## 사전 요구 사항

[!DNL CAPS]은(는) Adobe Commerce Cloud의 역할 기반 액세스 제어를 사용합니다. 클라우드 콘솔의 액세스 수준에 따라 [!DNL CAPS]&#x200B;(으)로 수행할 수 있는 작업이 결정됩니다.

### [!DNL CAPS] 사용 가능 사용자

* **프로젝트 관리자** - 모든 환경에서 패치를 적용하거나 되돌릴 수 있습니다.
* **참가자** - 할당된 환경에서 패치를 적용하거나 되돌릴 수 있습니다.
* **뷰어** - 프로젝트와 환경만 볼 수 있으며 동작은 허용되지 않습니다.

### 프로젝트에 대한 액세스 권한을 요청하는 방법

[!DNL CAPS] 사용자 인터페이스에 프로젝트가 없는 경우 적절한 사람에게 액세스 권한을 요청해야 합니다.

* 프로젝트의 계정 소유자 또는 프로젝트 관리자에게 문의하십시오
* 클라우드 콘솔을 통해 적절한 역할을 부여합니다.
* 액세스 권한이 부여되면 클라우드 콘솔에 로그인하여 [!DNL CAPS]을(를) 사용할 수 있습니다.

>[!NOTE]
>
>[!DNL CAPS]은(는) Adobe Commerce Cloud와 동일한 권한 모델을 따르므로 Cloud Console의 액세스 수준에 따라 [!DNL CAPS]을(를) 사용하여 수행할 수 있는 작업이 결정됩니다.

## [!DNL CAPS]에 액세스 중

CAPS 도구는 [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/)의 사이트 전체 분석 도구 대시보드에서 사용할 수 있습니다. 패치 자동화 탭에서 프로젝트 및 환경을 선택할 수 있습니다.

1. 사이트 전체 분석 도구([https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/))로 이동합니다.
1. 인터페이스에서 [!UICONTROL Patching Automation] 탭을 클릭합니다.
1. 패치를 적용할 프로젝트 및 환경을 선택합니다.
1. 사용 가능한 패치와 호환 상태를 검토합니다.
1. 적용 또는 되돌릴 패치를 선택합니다.

## 프로덕션 환경 액세스

프로덕션 환경에는 다음과 같은 추가 보호 조치가 적용됩니다.

* **유지 관리 모드** - 사용하도록 설정해야 함
* **크론 작업** - 비활성화해야 함
* **확인 대화 상자** - 계속하려면 완료해야 합니다.

>[!IMPORTANT]
>
>프로덕션 환경을 패치하려면 우발적인 중단을 방지하기 위한 적절한 준비와 안전 장치가 필요합니다.

## 관련 항목

* [CAPS 소개](intro.md)
* [워크플로](workflow.md)
* [우수 사례](best-practices.md)
* [문제 해결](troubleshooting.md)
