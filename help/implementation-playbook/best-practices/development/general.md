---
title: 일반 개발 우수 사례
description: Adobe Commerce 프로젝트를 개발하는 일반적인 모범 사례에 대해 알아봅니다.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Adobe Commerce에 대한 일반 개발 모범 사례

이 항목에서는 정상적인 Adobe Commerce 개발 프로세스의 기준선에 대해 설명합니다. 개발자를 안내하는 기본 프로세스, 코딩 원리, 애플리케이션 설계 원리에 대해 설명한다.

>[!NOTE]
>
>Adobe 기술 설계자는 이러한 모범 사례를 개발과 관련된 참여 중 참조로 사용합니다.

이러한 우수 사례는 Commerce 프로젝트를 개발 및 게재한 수년간의 경험을 기반으로 개발되었습니다. Adobe은 기술 이니셔티브가 이러한 모범 사례를 따르고 기존 프로세스와 코드를 이에 맞게 개선할 것을 권장합니다.

## 텍스트 규칙

이 주제의 핵심 단어 &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;RECOMMENDED&quot;, &quot;MAY&quot; 및 &quot;OPTIONAL&quot;은 다음과 같이 해석됩니다. [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## 프로세스

1. 프로젝트 활동을 시작하기 전에 정의된 프로젝트 방법론에 동의해야 합니다. 이는 스크럼, Waterfall, 또는 임의의 다른 방법론 또는 방법론의 조합이 정의될 수 있는 한 될 수 있다.
1. 개발 팀은 버전 제어 시스템의 분기 전략을 사용할 수 있을 때까지 개발을 시작하지 않아야 합니다.
1. 기술 사양, 사용자 스토리 및 사용 사례에 대한 승인 및 테스트 사례에 대한 승인 이후에 개발을 시작하지 않아야 하며, 개발 팀이 테스트 사례에 대한 승인을 사용할 수 있습니다.
1. 적어도 개발 및 QA 환경을 사용할 수 있을 때까지는 개발을 시작하지 않아야 합니다.
1. 개발을 시작하기 위해 반드시 필요한 프로젝트별 요구 사항은 _준비 정의_.
1. 승인 작업은 프로젝트 결과물에 대한 승인을 받은 고객 담당자가 수행해야 합니다.
1. 애자일 프로젝트 방법론에서 승인을 받으면 추가 요구 사항이 따를 수 있습니다. 이러한 요구 사항은 새로운 요구 사항으로 취급되어야 하며 그에 따라 캡처, 설계 및 계획되어야 합니다.
1. 모든 개발은 제출하기 전에 개발자가 기능적으로 테스트해야 합니다.
1. 모든 개발은 코드 검토를 위해 제출되기 전에 자동화된 테스트를 통과해야 합니다. 이는 끌어오기 요청 생성 후 자동화된 프로세스로 구성될 수 있습니다.
1. 모든 개발은 품질 보증을 위해 제출되기 전에 기술 설계자 또는 수석 개발자의 수동 코드 검토를 통과해야 합니다.
1. 모든 개발은 고객에게 전달하기 전에 품질 보증을 통과해야 합니다.
1. 게재에 필수인 프로젝트별 요구 사항은 &quot;완료의 정의&quot;에 문서화될 수 있습니다.

## 환경

1. 모든 개발자는 동일한 IDE를 사용해야 합니다. PhpStorm은 Adobe Commerce 개발에 권장되는 IDE입니다.
1. 모든 개발자는 (향후) 프로덕션 서버에서 사용되는 것과 동일한 기술 스택을 사용하여 개발 및 테스트해야 합니다. 이 기술 스택에 있는 소프트웨어 버전은 프로덕션 서버에 설치된 소프트웨어의 주 버전 및 부 버전과 일치해야 합니다. 다음을 참조하십시오 [시스템 요구 사항](../../../installation/system-requirements.md) Adobe Commerce의 일반적인 기술 스택에 대한 자세한 내용입니다.
1. 시스템 관리자 또는 기술 설계자는 팀에게 중앙 집중식으로 관리되는 로컬 개발 환경을 제공하여 동등하고 최신 로컬 환경을 보장하고 홍보할 수 있습니다.
1. 개발자와 QA 엔지니어는 QA 환경의 명령줄, 데이터베이스 및 로그 파일에 액세스할 수 있어야 합니다. 이 경우 VPN 연결이 필요할 수 있습니다.

## 코딩 표준

1. 모든 코드는 아키텍처, 방법론 및 코딩 표준의 규칙을 따라야 합니다. 창의성은 형식이 아닌 기능에서 요구되는 것이다.
1. 모든 코드는 [Adobe Commerce 아키텍처 안내서](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. 모든 코드는 [Adobe Commerce 코딩 표준](https://developer.adobe.com/commerce/php/coding-standards/).
1. 모든 코드는 [Adobe Commerce 기술 지침](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. 모든 코드가 다음을 구현해야 함 [Adobe Commerce 우수 사례](../phases.md), 해당하는 경우.
1. 모든 코드는 [PHP-Framework Interoperability Group(FIG) 표준](https://www.php-fig.org/).
1. 가능하면 다음을 수행하는 것이 좋습니다. [Adobe Commerce 기술 비전](https://developer.adobe.com/commerce/php/architecture/technical-vision/) 고려하십시오.
1. 외부 시스템과의 모든 통합에는 비즈니스 프로세스를 검증하는 통합 테스트가 있어야 합니다.
1. 모든 모듈은 테스트 범위를 가져야 합니다. 정확히 무엇을 테스트할지 개발 팀이 기술 설계자 또는 수석 개발자와 협력하여 결정해야 합니다. 이 결정은 정량적 조치가 아닌 정성적 조치에 기초해야 합니다. 높은 코드 적용률은 성공의 지표가 아니며 높은 코드 품질을 의미하지도 않습니다. 오히려, 프로그램의 해당 부분에서 회귀의 확률과 심각도를 평가하여 코드의 일부를 다루지 않을 위험을 판단하십시오.

## 버전 관리

모듈 버전은 [시맨틱 버전 관리 2.0.0 표준](https://semver.org/).
Adobe Commerce 코드베이스에 대한 종속성은 다음을 따라야 합니다. [모듈 버전 종속성 지침](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## 개정 관리

커밋에는 의미 있는 커밋 메시지가 포함되어야 합니다.

## 보안

1. [비보안 기능](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) 를 사용하면 안 됩니다.
1. [XSS 방지 전략](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) 를 적용해야 합니다.
1. [컨텐츠 보안 정책](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 를 적용해야 합니다.
1. 새 Adobe Commerce 인스턴스는 아직 &quot;보안 수정 종료&quot; 날짜에 도달하지 않은 버전의 최신 보안 릴리스에 제공되어야 합니다. 다음을 참조하십시오 [Adobe Commerce 소프트웨어 수명 주기 정책](../../../release/lifecycle-policy.md).
