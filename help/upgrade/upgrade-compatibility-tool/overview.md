---
title: 개요 [!DNL Upgrade Compatibility Tool]
description: 에 대해 알아보기 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 어떻게 도움을 줄 수 있습니까?
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# 개요 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

다음 [!DNL Upgrade Compatibility Tool] 은 Adobe Commerce 사용자 지정된 인스턴스에 설치된 모든 모듈 및 핵심 코드를 분석하여 특정 버전과 비교하여 확인하는 명령줄 도구입니다. 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 해결해야 하는 중요한 문제, 오류 및 경고 목록을 반환합니다. 또한 최신 버전의 Adobe Commerce으로 업그레이드하기 전에 코드에서 해결해야 하는 잠재적인 문제를 식별합니다.

다음 [!DNL Upgrade Compatibility Tool] 사용자 지정된 기능에 대한 핵심 코드 변경 사항을 적용한 시기를 식별할 수 있습니다. 자세한 내용은 [도구 실행](../upgrade-compatibility-tool/run.md) 주제 를 참조하십시오.

Adobe Commerce 버전을 릴리스할 때마다 작성기 패키지로 배포됩니다. 자세한 내용은 [개발자](../upgrade-compatibility-tool/developer.md) 주제 를 참조하십시오.

자세한 내용은 [설치](../upgrade-compatibility-tool/install.md) 을 사용하여 첫 번째 단계에 대한 주제 [!DNL Upgrade Compatibility Tool].

## 워크플로우

다음 다이어그램은 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 다이어그램](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 다음 [!DNL Upgrade Compatibility Tool] 사용 사례

다음 사용 사례에서는 Adobe Commerce 파트너가 클라이언트의 인스턴스를 업그레이드하는 일반적인 프로세스에 대해 설명합니다.

1. 다운로드 [!DNL Upgrade Compatibility Tool] Adobe Commerce 저장소에서 패키지(`https://repo.magento.com/`). 자세한 내용은 [다운로드 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 주제 를 참조하십시오.
1. 를 실행합니다 [!DNL Upgrade Compatibility Tool] 그 동안 [베타](https://devdocs.magento.com/release/beta-program.html) 최신 단계 [Adobe Commerce 릴리스](https://devdocs.magento.com/release/).
1. 기본 명령은 다음과 같습니다. `upgrade:check`. 이 명령은 인스턴스를 분석하고 인스턴스의 오류, 경고 및 중요 문제를 확인합니다. 결과를 최적화하려면 다음을 수행하십시오.

   - 추가 옵션 `--ignore-current-version-compatibility-issues` 알려진 모든 중요한 문제를 무시하기 위해 현재 Adobe Commerce 버전에 대한 오류 및 경고를 무시합니다. 원하는 버전의 결과만 표시합니다.
   - 사용 옵션 `--min-issue-level` 최소 문제 수준을 설정하려면 다음을 수행하십시오. 업그레이드의 가장 중요한 문제만 우선 순위를 지정하는 데 도움이 됩니다. 특정 공급업체, 모듈 또는 심지어 디렉토리만 분석하려는 경우 경로를 지정할 수도 있습니다. 자세한 내용은 [도구 실행](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) 항목을 참조하십시오.

1. 현재 설치된 특정 버전의 Adobe Commerce에 대해 vanilla 인스턴스를 생성합니다. 자세한 내용은 [기여자 안내서](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 자세한 내용은 `instance` 바닐라 설치를 생성하기 위한 명령

   >[!NOTE]
   >
   >vanilla 인스턴스는 특정 릴리스 버전에 대해 지정된 버전 태그 또는 분기를 깔끔하게 설치하는 것입니다.

1. 다음 [!DNL Upgrade Compatibility Tool] 사용자 지정된 손상 영역을 식별합니다. 소프트웨어 엔지니어는 복잡성을 이해하고 업그레이드의 노력을 예측할 수 있습니다. 이 정보는 이해 관계자와 공유됩니다.
1. 업그레이드에 대한 예산과 타임라인이 정의됩니다.
1. 그런 다음 소프트웨어 엔지니어가 손상된 모듈을 해결하기 위해 필요한 코드 수정 작업을 수행할 수 있습니다.
1. 다음 [!DNL Upgrade Compatibility Tool] 를 실행하여 업그레이드 진행 상황을 추적할 수 있습니다.
1. 이제 모든 것이 확인되고 엔지니어링이 코드를 스테이징 환경에 푸시할 수 있습니다. 여기서 회귀 테스트는 모든 테스트가 녹색임을 확인하므로 Adobe Commerce 사전 릴리스가 있는 당일 최신 Adobe Commerce 버전을 프로덕션에 릴리스할 수 있습니다.

   ![[!DNL Upgrade Compatibility Tool] 대상자](../../assets/upgrade-guide/audience-uct-v3.png)

## 개선 사항 [!DNL Upgrade Compatibility Tool]

에 연결하려면 [!DNL Upgrade Compatibility Tool] 팀, 엔지니어링 Slack 채널에서 문의하십시오. [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). 도구를 개선하는 데 도움이 되는 피드백, 문제 및 제안 사항을 알고 싶습니다.

다음 [!DNL Upgrade Compatibility Tool] adobe에서 정의한 규칙 사용 [코딩 표준](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 프로젝트가 Adobe Commerce 우수 사례를 따르고 있는지 확인하고, 이를 통해 개선 및 확장 작업을 수행할 수 있는지 확인하십시오 [!DNL Upgrade Compatibility Tool].

자세한 내용은 [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  이 프로젝트에 기여하는 방법에 대한 자세한 내용은 항목을 참조하십시오.

## 리소스

Adobe Commerce 업그레이드를 이해하는 데 도움이 되도록 다음 리소스를 개발했습니다.

- [업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [예정된 릴리스](https://devdocs.magento.com/release/)
- [커뮤니티 리소스](https://devdocs.magento.com/community/resources/resources.html) 페이지를 참조하십시오.
