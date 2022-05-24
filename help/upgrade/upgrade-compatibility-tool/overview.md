---
title: 개요 [!DNL Upgrade Compatibility Tool]
description: 에 대해 알아보기 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 어떻게 도움을 줄 수 있습니까?
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# 안내서 개요

이 안내서는 Adobe Commerce의 관리자 및 소프트웨어 엔지니어를 위한 것입니다. 여기에는 설치 관련 세부 정보가 포함됩니다 [!DNL Upgrade Compatibility Tool]뿐만 아니라 구성 및 관리도 포함되어 있습니다. 이 섹션에서는 코어 상거래 구성 및 기능에 대한 기본적인 이해를 가정합니다.

## 개요 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce 사용자 지정된 인스턴스에 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전과 비교하여 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다.

자세한 내용은 [도구 실행](../upgrade-compatibility-tool/run.md) 추가 정보.

을(를) 참조하십시오. [설치](../upgrade-compatibility-tool/install.md) 을 사용하여 첫 번째 단계에 대해 [!DNL Upgrade Compatibility Tool].

다음 보기 [비디오 튜토리얼](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) 를 참조하십시오 [!DNL Upgrade Compatibility Tool].

### 워크플로우

다음 다이어그램은 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 다이어그램](../../assets/upgrade-guide/uct-diagram-v5.png)

### 다음 [!DNL Upgrade Compatibility Tool] 사용 사례

다음 사용 사례에서는 Adobe Commerce 파트너가 클라이언트의 인스턴스를 업그레이드하는 일반적인 프로세스에 대해 설명합니다.

1. 다운로드 [!DNL Upgrade Compatibility Tool] Adobe Commerce 저장소에서 패키지(`https://repo.magento.com/`). 자세한 내용은 [다운로드 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 주제 를 참조하십시오.
1. 를 실행합니다 [!DNL Upgrade Compatibility Tool] 그 동안 [베타](https://devdocs.magento.com/release/beta-program.html) 최신 단계 [Adobe Commerce 릴리스](https://devdocs.magento.com/release/).
1. 현재 설치된 특정 버전의 Adobe Commerce에 대해 vanilla 인스턴스를 생성합니다. 자세한 내용은 [기여자 안내서](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 자세한 내용은 `instance` 바닐라 설치를 생성하기 위한 명령

   >[!NOTE]
   >
   >vanilla 인스턴스는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 깔끔하게 설치하는 것입니다.

1. 다음 [!DNL Upgrade Compatibility Tool] 소프트웨어 엔지니어가 복잡성을 이해하고 업그레이드의 노력을 예측하는 데 도움이 되는 업그레이드 문제를 식별합니다.
1. 이 정보는 이해 관계자와 공유됩니다.
1. 업그레이드에 대한 예산과 타임라인이 정의됩니다.
1. 그런 다음 소프트웨어 엔지니어가 손상된 모듈을 해결하기 위해 필요한 코드 수정 작업을 수행할 수 있습니다.
1. 다음 [!DNL Upgrade Compatibility Tool] 를 실행하여 업그레이드 진행 상황을 추적할 수 있습니다.
1. 이제 모든 것이 확인되고 엔지니어링이 코드를 스테이징 환경에 푸시할 수 있습니다. 여기서 회귀 테스트는 모든 테스트가 녹색임을 확인하므로 Adobe Commerce 사전 릴리스가 있는 당일 최신 Adobe Commerce 버전을 프로덕션에 릴리스할 수 있습니다.

   ![[!DNL Upgrade Compatibility Tool] 대상자](../../assets/upgrade-guide/audience-uct-v3.png)

### 개선 사항 [!DNL Upgrade Compatibility Tool]

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

에 연결하려면 [!DNL Upgrade Compatibility Tool] 팀, 엔지니어링 Slack 채널에서 문의하십시오. [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 도구를 개선하는 데 도움이 되는 피드백, 문제 및 제안 사항을 알고 싶습니다.

다음 [!DNL Upgrade Compatibility Tool] adobe에서 정의한 규칙 사용 [코딩 표준](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 프로젝트가 Adobe Commerce 우수 사례를 따르고 있는지 확인하고, 이를 통해 개선 및 확장 작업을 수행할 수 있는지 확인하십시오 [!DNL Upgrade Compatibility Tool].

자세한 내용은 [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  코딩 표준에 대한 자세한 정보.

### 리소스

Adobe Commerce 업그레이드를 이해하는 데 도움이 되도록 다음 리소스를 개발했습니다.

- [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [예정된 릴리스](https://devdocs.magento.com/release/)
- [커뮤니티 리소스](https://devdocs.magento.com/community/resources/resources.html) 페이지를 참조하십시오.
- [관련 도구](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
