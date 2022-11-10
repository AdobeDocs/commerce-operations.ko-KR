---
title: 보안 사고 방지 및 대응
description: 클라우드 인프라 프로젝트에서 Adobe Commerce의 보안 사고를 방지하고 응답하기 위한 모범 사례에 대해 배웁니다.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 보안 문제를 방지하고 이에 응답하는 데 도움이 되는 우수 사례

Adobe Commerce 보안은 [공유 권한](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 모델. Adobe 및 기술 팀이 담당하는 사항을 이해하는 것이 중요합니다. 아래에 요약하면 다음과 같습니다 [보안 모범 사례](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 을 참조하십시오. 프로젝트에 가장 적합한 보안 제어 기능이 있고 보안 문제에 가장 잘 대처할 수 있습니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라

## 사고 대응

보안 문제에 응답할 때 고려해야 할 사항이 많습니다. 클라우드 인프라 프로젝트에서 Adobe Commerce에 대한 최근 보안 사고가 발생한 것으로 의심되는 경우 모든 관리자 사용자 계정 액세스를 감사하고, 고급 MFA(Multi-Factor Authentication) 컨트롤을 사용하도록 설정하고, 중요 로그를 보존하고, Adobe Commerce 버전에 대한 보안 업그레이드를 검토해야 합니다.

추가 권장 사항은 아래에 자세히 설명되어 있습니다. 무단 액세스를 방지하고 추가 사고 분석 프로세스를 시작할 수 있습니다.

## 보안 사고를 방지하는 방법

Adobe Commerce 사이트 및 스토어프런트에 영향을 주는 보안 사고를 사전에 방지하려면 다음 보안 모범 사례를 따르십시오.

- [관리자 액세스를 위해 2FA 활성화](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
2단계 인증은 널리 사용되고 동일한 앱에서 다른 웹 사이트에 대한 액세스 코드를 생성하는 것이 일반적입니다. 이렇게 하면 사용자 계정에만 로그인할 수 있습니다. 암호를 잃어버리거나 봇이 암호를 인식하는 경우 2단계 인증은 보호 레이어를 추가합니다.
- [SSH 액세스에 대한 MFA 활성화](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
프로젝트에서 MFA가 활성화되면 SSH 액세스 권한이 있는 클라우드 인프라 계정의 모든 Adobe Commerce은 환경에 액세스하기 위해 2단계 인증(2FA) 코드 또는 API 토큰 및 SSH 인증서가 필요한 인증 워크플로우를 따라야 합니다.
- Adobe Commerce 최신 릴리스로 업그레이드하십시오.
Adobe은 지원되는 각 릴리스 Adobe Commerce에 대한 보안 및 기능 패치를 릴리스합니다.
- 설정 및 사용 [비기본 관리 URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe은 기본 URL 대신 고유한 사용자 지정 관리 URL을 사용하는 것을 권장합니다 `admin` 또는 다음과 같은 일반적인 용어 *백엔드*. 이 구성 변경으로 인해 결정된 불량 행위자로부터 사이트를 직접 보호하지는 않지만, 무단 액세스를 시도하는 스크립트의 노출을 줄일 수 있습니다.
- 관리자가  [`bin/magento config:set` CLI 명령을 사용하여 `lock env` 구성 옵션](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 이 옵션은 관리자에서 편집할 수 없도록 구성 값을 잠그거나 이미 잠긴 설정을 변경할 수 없습니다. 이 옵션을 사용하면 구성 변경 사항이 `<Commerce base dir>/app/etc/env.php` 파일.
- 설정 및 실행 [Adobe Commerce 보안 검사 도구](https://docs.magento.com/user-guide/magento/security-scan.html).
향상된 보안 검색을 통해 PWA을 포함한 각 Adobe Commerce 사이트를 모니터링하여 알려진 보안 위험 및 맬웨어를 확인하고 패치 업데이트 및 보안 알림을 받을 수 있습니다.
- [관리자 액세스 검토 및 업데이트](https://docs.magento.com/user-guide/system/permissions-users-all.html) 및 [보안 설정](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 오래된 계정, 사용하지 않거나 의심스러운 계정을 제거하고 모든 관리 사용자를 위해 암호를 회전하는 것이 좋습니다.
   - 프로젝트에 대한 고급 보안 설정 을 검토하고 업데이트합니다. 관리자 보안 구성을 사용하면 URL에 암호 키를 추가하고, 대/소문자를 구분해야 하며, 암호 수명 및 관리자 사용자 계정이 잠기기 전에 수행할 수 있는 로그인 시도 횟수를 포함하여 관리자 세션의 길이를 제한할 수 있습니다. 보안을 강화하려면 현재 세션이 만료되기 전에 키보드 비활성화 시간을 구성하고 사용자 이름과 암호를 대/소문자를 구분해야 합니다.
- Adobe Commerce 감사 켜기 [클라우드 프로젝트 사용자](https://devdocs.magento.com/cloud/project/user-admin.html).
오래되거나 사용되지 않거나 의심스러운 계정을 제거하고 사용자에게 암호를 변경하도록 요청하는 것이 좋습니다.
- 감사 [SSH 키](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 클라우드 기반의 Adobe Commerce용
SSH 키를 검토, 삭제 및 회전하는 것이 좋습니다.
- 관리자의 ACL(액세스 제어 목록)을 구현합니다.
사용자 지정 ACL 목록과 함께 기본 Edge ACL 목록을 사용할 수 있습니다 [VCL 코드 조각](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 수신 요청을 필터링하고 IP 주소별로 관리자에게 액세스를 허용하기 위해.

## 사고 분석

사고 분석의 첫 번째 단계는 가능한 한 빨리 많은 사실을 수집하는 것이다. 사고 관련 정보를 수집하면 사고의 잠재적 원인을 파악하는 데 도움이 될 수 있습니다. Adobe Commerce은 사고 분석을 지원하기 위한 아래 도구를 제공합니다.

- [감사 관리 작업 로그](https://docs.magento.com/user-guide/system/action-log-report.html).
작업 로그 보고서에는 로깅에 대해 활성화된 모든 관리 작업의 세부 레코드가 표시됩니다. 각 레코드는 타임스탬프를 지정하고 사용자의 IP 주소와 이름을 등록합니다. 로그 세부 사항에는 관리자 사용자 데이터 및 작업 중에 발생한 관련 변경 사항이 포함됩니다.
- 를 사용하여 이벤트 분석 [Adobe Commerce 도구 관찰](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Adobe Commerce 관찰 도구를 사용하면 복잡한 문제를 분석하여 근본 원인을 식별할 수 있습니다. 서로 다른 데이터를 추적하는 대신 이벤트와 오류에 대해 상관관계를 맺어 성능 병목 현상을 보다 심층적으로 파악할 수 있습니다.
이 도구는 근본 원인을 식별하고 사이트를 최적으로 계속 작동하도록 하기 위해 잠재적 사이트 문제 중 일부를 명확하게 확인하기 위한 것입니다. 위의 Adobe Commerce 도구 설명서에 대한 링크를 클릭하여 도구 설명서에 액세스합니다. 설명서에는 **보안** 탭.
- 을 사용하여 로그 분석 [새 레큐리티 로그](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure pro 프로젝트에는 다음이 포함됩니다 [새 레큐리티 로그](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 서비스. 이 서비스는 스테이징 및 프로덕션 환경에서 모든 로그 데이터를 집계하여 중앙 로그 관리 대시보드에 표시하도록 사전 구성되어 있습니다.
New Relic Logs 서비스를 사용하여 다음 작업을 완료할 수 있습니다.
   - 사용 [새 Relic 쿼리](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 합계된 로그 데이터를 검색하려면 다음을 수행하십시오.
   - New Relic Logs 애플리케이션을 통해 로그 데이터를 시각화합니다.

## 추가 정보

- [근본 원인 분석 프레임워크](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
