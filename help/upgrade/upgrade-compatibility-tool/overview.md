---
title: ' [!DNL Upgrade Compatibility Tool] 개요'
description: ' [!DNL Upgrade Compatibility Tool] 과(와) Adobe Commerce 프로젝트에 도움이 되는 방법에 대해 알아봅니다.'
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 안내서 개요

{{commerce-only}}

이 안내서는 Adobe Commerce의 관리자 및 소프트웨어 엔지니어를 대상으로 합니다. [!DNL Upgrade Compatibility Tool] 설치와 구성 및 관리에 대한 자세한 정보가 포함되어 있습니다. 핵심 Commerce 구성 및 기능에 대한 기본적인 이해를 전제로 합니다.

## [!DNL Upgrade Compatibility Tool] 개요

[!DNL Upgrade Compatibility Tool]은(는) 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전에 대해 Adobe Commerce 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

## [!DNL Upgrade Compatibility Tool] 사용

다음을 통해 [!DNL Upgrade Compatibility Tool]을(를) 사용할 수 있습니다.

- 독립 실행형 [명령줄 인터페이스](../upgrade-compatibility-tool/run.md) 도구입니다. 사용 가능한 명령의 전체 목록을 보려면 [`bin/uct` 참조](../../tools/reference/uct.md)를 참조하십시오.
- [!DNL Upgrade Compatibility Tool]을(를) [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)과(와) 통합하는 중입니다.
- [Magento PHPStorm 플러그인](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md) 내의 실행 구성입니다.

## 워크플로

다음 다이어그램은 [!DNL Upgrade Compatibility Tool]을(를) 실행할 때 가능한 워크플로를 보여 줍니다.

![[!DNL Upgrade Compatibility Tool] 다이어그램](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 데모

[!DNL Upgrade Compatibility Tool]에 대해 알아보려면 이 비디오를 시청하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## [!DNL Upgrade Compatibility Tool]을(를) 개선하는 데 도움

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

[!DNL Upgrade Compatibility Tool] 팀에 연결하려면 엔지니어링 Slack 채널 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)에서 문의하세요. 도구를 개선하는 데 도움이 되는 피드백, 문제 및 제안을 듣고자 합니다.

[!DNL Upgrade Compatibility Tool]은(는) [코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/)에 정의된 규칙을 사용하여 프로젝트가 Adobe Commerce 모범 사례를 따르고 있는지 확인하고 [!DNL Upgrade Compatibility Tool]을(를) 개선하고 확장하는 데 도움을 줍니다.

코딩 표준을 제공하는 방법에 대한 자세한 내용은 [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 항목을 참조하십시오.

## 리소스

Adobe Commerce 업그레이드를 이해하는 데 도움이 되는 다음 리소스를 참조하십시오.

- [업그레이드 안내서](../overview.md)에서는 일반적인 Adobe Commerce 업그레이드 여정과 해당 여정에 따른 모범 사례에 대한 개요를 제공합니다.
- [예정된 릴리스](https://devdocs.magento.com/release/) 페이지에서는 예정된 릴리스 및 예정된 릴리스의 날짜를 제공합니다.
- [커뮤니티 리소스](https://developer.adobe.com/commerce/contributor/community/) 페이지에서 토론을 시작하거나 추가 정보를 찾을 수 있습니다.
- 일반적인 업그레이드 여정에서 유용한 도구를 보려면 [관련 도구](../upgrade-compatibility-tool/related-tools.md) 페이지를 확인하십시오.
