---
title: 개요 [!DNL Upgrade Compatibility Tool]
description: 에 대해 알아보기 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 어떤 도움을 줄 수 있는지 설명합니다.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 안내서 개요

{{commerce-only}}

이 안내서는 Adobe Commerce의 관리자 및 소프트웨어 엔지니어를 대상으로 합니다. 여기에는 설치에 대한 자세한 정보가 포함되어 있습니다. [!DNL Upgrade Compatibility Tool], 구성 및 관리. 이는 핵심 상거래 구성 및 기능에 대한 기본적인 이해를 전제로 합니다.

## 개요 [!DNL Upgrade Compatibility Tool]

다음 [!DNL Upgrade Compatibility Tool] 는 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

## 사용 [!DNL Upgrade Compatibility Tool]

다음을 사용할 수 있습니다. [!DNL Upgrade Compatibility Tool] 를 통해:

- 독립 실행형으로 [명령줄 인터페이스](../upgrade-compatibility-tool/run.md) 도구. 사용 가능한 명령의 전체 목록은 [`bin/uct` 참조](/help/reference/uct.md).
- 통합 [!DNL Upgrade Compatibility Tool] (으)로 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 내에서 실행 구성 [Magento PHPStorm 플러그인](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## 워크플로

다음 다이어그램은 를 실행할 때 가능한 워크플로를 보여 줍니다. [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 다이어그램](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 데모

다음 비디오에 대해 알아보십시오. [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 개선 지원 [!DNL Upgrade Compatibility Tool]

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

을(를) 연결하려면 [!DNL Upgrade Compatibility Tool] 팀, 엔지니어링 Slack 채널에서 문의하십시오. [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 도구를 개선하는 데 도움이 되는 피드백, 문제 및 제안을 듣고자 합니다.

다음 [!DNL Upgrade Compatibility Tool] 에서 정의한 규칙을 사용합니다. [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/) 프로젝트가 Adobe Commerce 모범 사례를 따르고 있는지 확인하고 의 개선 및 확장을 지원합니다. [!DNL Upgrade Compatibility Tool].

다음을 참조하십시오. [참여](https://developer.adobe.com/commerce/php/coding-standards/contributing/) topic 을 참조하십시오.

## 리소스

Adobe Commerce 업그레이드를 이해하는 데 도움이 되는 다음 리소스를 참조하십시오.

- 다음 [업그레이드 안내서](../overview.md) 일반적인 Adobe Commerce 또는 Magento Open Source 업그레이드 여정과 해당 여정에 따른 모범 사례에 대한 개요를 제공합니다.
- 다음 [예정된 릴리스](https://devdocs.magento.com/release/) 페이지는 예정된 릴리스 및 예정된 릴리스에 대한 날짜를 제공합니다.
- 다음 [커뮤니티 리소스](https://developer.adobe.com/commerce/contributor/community/) 페이지를 열어 토론을 시작하거나 추가 정보를 찾을 수 있습니다.
- 다음 확인: [관련 도구](../upgrade-compatibility-tool/related-tools.md) 일반적인 업그레이드 여정에서 유용한 도구를 보려면 페이지를 참조하십시오.
