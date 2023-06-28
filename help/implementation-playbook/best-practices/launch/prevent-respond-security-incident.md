---
title: 보안 사고 예방 및 대응
description: Adobe Commerce on cloud infrastructure 프로젝트의 보안 사고를 방지하고 대응하기 위한 모범 사례에 대해 알아봅니다.
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# 보안 사고를 예방하고 대응하는 데 도움이 되는 모범 사례

Adobe Commerce 보안은 [공동 책임](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 모델. Adobe 및 기술 팀의 책임을 파악하는 것이 중요합니다. 아래에서는 다음을 요약합니다 [보안 모범 사례](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 프로젝트에 최상의 보안 제어 기능이 적용되어 있고 보안 문제에 대한 최적의 대응 방법을 보장하기 위해

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce

## 문제에 응답

보안 사고에 대처할 때 고려해야 할 사항이 많습니다. Adobe Commerce on cloud infrastructure 프로젝트에서 최근 보안 문제가 발생했다고 의심되는 경우 모든 관리자 사용자 계정 액세스를 감사하고 고급 MFA(Multi-Factor Authentication) 컨트롤을 활성화하고, 중요한 로그를 보존하고, Adobe Commerce 버전에 대한 보안 업그레이드를 검토하는 것이 중요합니다.

자세한 권장 사항은 아래에 자세히 설명되어 있습니다. 이를 통해 무단 액세스를 방지하고 추가 사고 분석을 위한 프로세스를 시작할 수 있습니다.

## 보안 사고를 방지하는 방법

다음 보안 모범 사례를 따라 Adobe Commerce 사이트 및 상점에 영향을 주는 보안 사고를 사전에 방지하십시오.

- [관리자 액세스에 2FA 활성화](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
2단계 인증이 널리 사용되고 있으며 동일한 앱에서 서로 다른 웹 사이트에 대한 액세스 코드를 생성하는 것이 일반적입니다. 이렇게 하면 사용자만 사용자 계정에 로그인할 수 있습니다. 암호를 분실하거나 봇이 추측하는 경우 2단계 인증을 통해 보호 계층이 추가됩니다.
- [SSH 액세스용 MFA 활성화](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
프로젝트에서 MFA가 활성화되면 SSH 액세스가 가능한 모든 클라우드 인프라 계정의 Adobe Commerce은 2단계 인증(2FA) 코드 또는 환경에 액세스하기 위한 API 토큰과 SSH 인증서가 필요한 인증 워크플로를 따라야 합니다.
- Adobe Commerce의 최신 릴리스로 업그레이드하십시오.
Adobe은 지원되는 각 릴리스 Adobe Commerce에 대한 보안 및 기능 패치를 릴리스합니다.
- 설정 및 사용 [기본값이 아닌 관리자 URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe은 기본값 대신 고유한 사용자 지정 관리자 URL을 사용할 것을 권장합니다 `admin` 또는 다음과 같은 일반적인 용어 *백엔드*. 이러한 구성 변경으로 인해 결정된 불량 액터로부터 사이트를 직접 보호하지는 못하지만, 무단 액세스를 시도하는 스크립트에 대한 노출을 줄일 수 있습니다.
- 관리자를 사용하여 구성 값이 편집되거나 업데이트되지 않도록 합니다.  [`bin/magento config:set` CLI 명령 `lock env` 구성 옵션](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 이 옵션은 관리자에서 편집할 수 없도록 구성 값을 잠그거나 이미 잠긴 설정을 변경하지 못하도록 합니다. 이 옵션을 사용하면 구성 변경 사항이 `<Commerce base dir>/app/etc/env.php` 파일.
- 설정 및 실행 [Adobe Commerce 보안 검색 도구](https://docs.magento.com/user-guide/magento/security-scan.html).
향상된 보안 검사를 통해 PWA을 포함한 각 Adobe Commerce 사이트를 모니터링하여 알려진 보안 위험 및 맬웨어를 확인하고 패치 업데이트 및 보안 알림을 받을 수 있습니다.
- [관리자 액세스 검토 및 업데이트](https://docs.magento.com/user-guide/system/permissions-users-all.html) 및 [보안 설정](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 오래되거나 사용하지 않거나 의심스러운 계정을 제거하고 모든 관리자의 암호를 순환하는 것이 좋습니다.
   - 프로젝트에 대한 고급 보안 설정 을 검토하고 업데이트합니다. 관리자 보안 구성을 사용하면 URL에 비밀 키를 추가하고, 암호는 대/소문자를 구분해야 하며, 관리자 사용자 계정이 잠기기 전에 시도할 수 있는 로그인 시도 횟수 및 암호 수명을 포함하여 관리자 세션 길이를 제한할 수 있습니다. 보안을 강화하기 위해 현재 세션이 만료되기 전에 키보드 비활성화 시간을 구성하고 사용자 이름과 암호를 대소문자를 구분해야 합니다.
- Adobe Commerce 감사 [클라우드 프로젝트 사용자](https://devdocs.magento.com/cloud/project/user-admin.html).
오래되거나 사용하지 않거나 의심스러운 계정을 제거하고 사용자에게 암호 변경을 요청하는 것이 좋습니다.
- 감사 [SSH 키](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 클라우드 인프라의 Adobe Commerce용
SSH 키를 검토, 삭제 및 회전시키는 것이 좋습니다.
- 관리자용 ACL(액세스 제어 목록)을 구현합니다.
Fastly Edge ACL 목록을 사용자 정의와 함께 사용할 수 있습니다 [VCL 코드 조각](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 수신 요청을 필터링하고 IP 주소별 관리자 액세스를 허용합니다.

## 문제 분석

사건 분석의 첫 단계는 최대한 많은 사실을 가능한 한 빨리 수집하는 것이다. 인시던트에 대한 정보를 수집하면 인시던트의 잠재적 원인을 파악하는 데 도움이 될 수 있습니다. Adobe Commerce은 사고 분석을 지원하는 아래 도구를 제공합니다.

- [감사 관리자 작업 로그](https://docs.magento.com/user-guide/system/action-log-report.html).
작업 로그 보고서에는 로깅이 활성화된 모든 관리자 작업에 대한 자세한 레코드가 표시됩니다. 각 레코드는 타임스탬프를 지정하고 사용자의 IP 주소와 이름을 등록합니다. 로그 세부 사항에는 작업 중에 수행된 관리 사용자 데이터 및 관련 변경 사항이 포함됩니다.
- 를 사용하여 이벤트 분석 [Adobe Commerce 도구에 대한 관찰](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Adobe Commerce 관찰 도구를 사용하면 복잡한 문제를 분석하여 근본 원인을 식별할 수 있습니다. 서로 다른 데이터를 추적하는 대신 이벤트와 오류의 상관 관계를 파악하여 성능 병목 현상의 원인에 대한 심층적인 통찰력을 얻을 수 있습니다.
이 도구는 잠재적 사이트 문제 중 일부를 명확하게 확인하여 근본 원인을 식별하고 사이트의 성능을 최적으로 유지하는 데 도움을 주기 위한 것입니다. 위의 Adobe Commerce 관찰 도구 설명서에 대한 링크를 클릭하여 도구 설명서에 액세스합니다. 설명서에는 에서 찾을 수 있는 모든 정보를 자세히 설명하는 섹션이 있습니다. **보안** 탭.
- 로그 분석 [New Relic 로그](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure Pro 프로젝트에는 [New Relic 로그](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 서비스. 이 서비스는 스테이징 및 프로덕션 환경에서 모든 로그 데이터를 집계하여 중앙 로그 관리 대시보드에 표시하도록 사전 구성되어 있습니다.
New Relic 로그 서비스를 사용하여 다음 작업을 완료할 수 있습니다.
   - 사용 [New Relic 쿼리](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 집계된 로그 데이터를 검색합니다.
   - New Relic 로그 애플리케이션을 통해 로그 데이터를 시각화합니다.

## 추가 정보

- [근본 원인 분석 프레임워크](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
