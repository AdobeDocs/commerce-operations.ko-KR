---
title: '[!DNL Adobe Commerce Patching Automation]'
description: ' [!DNL Adobe Commerce Patching Automation], 사용 방법, 액세스 방법 및 자동 패치 모범 사례에 대해 알아봅니다.'
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation]은(는) 클라우드 환경에서 Adobe Commerce에 대한 패치를 적용하고 되돌리는 프로세스를 자동화하는 도구입니다. Commerce 프로젝트 관리자는 패치를 적용하고 되돌릴 수 있는 능률적인 워크플로를 제공합니다. 내장된 유효성 검사 및 상태 검사는 클라우드 환경이 안정적이고 안전하게 유지될 수 있도록 지원합니다.

이 안내서는 패치 작업 프로세스를 간소화하고 패치 관련 문제의 위험을 줄이고 환경의 보안 및 안정성을 개선하며 일상적인 패치 작업을 자동화하려는 Adobe Commerce Cloud 판매자 및 파트너를 위해 설계되었습니다.

## [!DNL Patching Automation]개 주제

* **[액세스 방법](access.md)**
* **[워크플로 개요](workflow.md)**
* **[GitHub 통합](github-integration.md)**
* **[모범 사례](best-practices.md)**
* **[문제 해결](troubleshooting.md)**

## 도구 개요

* **UI 인터페이스**
  * 특정 프로젝트 및 환경 조합에 대한 실시간 패치 가용성 및 상태 표시
  * 진행 상황, 오류 및 기타 관련 메시지를 보여주는 포괄적인 패치 상태 정보
  * 다음에 대한 [!UICONTROL Patch Management Dashboard]:
    * 사용 가능한 패치 보기
    * 한 번의 클릭으로 패치 적용
    * 이전에 적용된 패치 되돌리기
    * 패치 작업 상태 및 결과 모니터링

* **구조화된 워크플로를 사용한 자동 패치 서비스**
  * **사전 확인** - 패치 호환성 및 환경 준비 상태 확인
  * **패치 중** - 통합 환경에서 자동으로 패치를 적용하거나 되돌립니다.
  * **유효성 검사** - 상태 검사를 수행하여 응용 프로그램이 시작되고 해당 데이터베이스와 캐시 연결에 연결할 수 있는지 확인합니다.

* **안전 기능**
  * 응용 프로그램 전에 패치 호환성 확인
  * 임시 통합 환경에서 먼저 패치를 적용하여 성공적으로 배포되었는지 확인하고 상태 검사를 통과한 후 대상 환경으로 병합한 다음 배포 직후 최종 상태 검사를 수행합니다
  * 되돌리는 동안 자동 제거로 `m2-hotfixes` 폴더에 패치를 적용합니다.

## Adobe Commerce Cloud와 통합

[!DNL Patching Automation]은(는) Adobe Commerce 클라우드 인프라와 완전히 통합되었으며 기존 클라우드 환경과 원활하게 연동됩니다. 최적의 성능을 위해 클라우드 기반 기능을 활용하고 상세한 로깅 및 모니터링을 제공하며 Adobe Commerce 클라우드 지원 도구와 통합됩니다.

## 비디오 튜토리얼

[!DNL Adobe Commerce Patching Automation]에 대해 알아보고 이 도구를 사용하여 보안 패치를 빠르게 찾고 적용하는 방법에 대해 알아봅니다. 다음 비디오에서는 SWAT(Site-Wide Analysis Tool) 대시보드를 통해 프로젝트에 액세스하고, 프로젝트 및 환경을 선택하고, 패치를 적용하는 방법을 한 번의 클릭으로 다룹니다.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## 일반적인 사용 사례

* **보안 패치** - 중요한 보안 업데이트를 신속하게 적용합니다.
* **패치 롤백** - 서비스를 통해 적용된 문제 패치를 안전하게 되돌립니다.
* **보안 규정 준수** - 자동 패치로 보안 표준 유지
* **작동 안정성** - 응용 프로그램이 시작되고 각 패치 작업 후에 상태 검사를 통과하는지 확인합니다.
