---
title: 개요 [!DNL Upgrade Compatibility Tool]
description: 에 [!DNL Upgrade Compatibility Tool] 대해 알아보고 Adobe Systems Commerce 프로젝트에 어떻게 도움을 줄 수 있는지 알아봅니다.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 안내서 개요

{{commerce-only}}

이 안내서 - Adobe Systems Commerce의 관리자와 소프트웨어 엔지니어용입니다. 여기에는 의 [!DNL Upgrade Compatibility Tool]설치와 구성 및 관리에 대한 자세한 정보가 포함되어 있습니다. 핵심 상거래 구성 및 기능에 대한 기본적인 이해가 있다고 가정합니다.

## 개요 [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] 설치된 모든 모듈과 코어 코드를 분석하여 특정 버전에 대해 Adobe Systems Commerce 사용자 지정 인스턴스를 확인하는 도구입니다. 최신 버전의 Adobe Systems Commerce로 업그레이드하기 전에 해결해야 하는 중요 문제, 오류 및 경고 목록을 반환합니다.

## 디스플레이 광고, 오프사이트 대상 등 원격 [!DNL Upgrade Compatibility Tool]

다음을 통해 [!DNL Upgrade Compatibility Tool]을(를) 사용할 수 있습니다.

- 독립 실행형 [명령줄 인터페이스](../upgrade-compatibility-tool/run.md) 도구입니다. 사용 가능한 명령의 전체 목록을 보려면 [`bin/uct` 참조](../../tools/reference/uct.md)를 참조하십시오.
- 를 [!DNL Upgrade Compatibility Tool] [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Magento PHPStorm 플러그인](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md) 내의 [실행 구성입니다.

## 워크플로

다음 다이어그램은 을 실행할 때 가능한 워크플로우를 보여줍니다.[!DNL Upgrade Compatibility Tool]

![[!DNL Upgrade Compatibility Tool] 다이어그램](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 데모

이 비디오를 통해 다음에 대해 알아보십시오.[!DNL Upgrade Compatibility Tool]

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 도움말 개선 [!DNL Upgrade Compatibility Tool]

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

[!DNL Upgrade Compatibility Tool] 팀에 연결하려면 엔지니어링 Slack 채널 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)에서 문의하세요. 도구를 개선하는 데 도움이 되는 피드백, 문제 및 제안을 듣고자 합니다.

코딩 [!DNL Upgrade Compatibility Tool] 표준](https://developer.adobe.com/commerce/php/coding-standards/) 내에 [정의된 규칙을 사용하여 프로젝트가 Adobe Systems Commerce 우수 사례를 [!DNL Upgrade Compatibility Tool]따르도록 하고 .

코딩 표준 기여에 대한 자세한 내용은 Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 항목을 참조하십시오[.

## 리소스

Adobe Systems Commerce 업그레이드를 이해하는 데 도움이 되는 다음 리소스를 참조하십시오.

- [업그레이드 안내서](../overview.md)는 일반적인 Adobe Systems Commerce 업그레이드 여정에 대한 개요와 해당 여정에 팔로우 모범 사례를 제공합니다.
- [예정된 릴리스](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) 페이지 페이지에서는 예약된 릴리스와 예정된 릴리스에 대한 날짜를 제공합니다.
- [커뮤니티 리소스](https://developer.adobe.com/commerce/contributor/community/) 페이지 는 토론을 시작하거나 더 많은 정보를 찾을 수 있는 곳입니다.
- 관련 도구](../upgrade-compatibility-tool/related-tools.md) 페이지에서 [일반적인 업그레이드 경험의 유용한 도구를 확인하십시오.
