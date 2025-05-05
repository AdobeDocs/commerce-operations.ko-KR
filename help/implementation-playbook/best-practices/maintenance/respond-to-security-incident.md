---
title: 보안 문제에 응답
description: 사이트 가용성 및 성능에 영향을 주는 보안 문제에 대응하고 해결하기 위해 다음과 같은 모범 사례를 통해 보안 인시던트를 처리합니다.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# 보안 사고에 대응하는 우수 사례

다음 문서에서는 보안 문제에 대응하고 Adobe Commerce 사이트의 가용성, 안정성 및 성능에 영향을 주는 문제를 해결하기 위한 모범 사례를 요약합니다.

이러한 모범 사례를 따르면 승인되지 않은 액세스 및 맬웨어 공격을 방지할 수 있습니다. 보안 사고가 발생하면 이러한 모범 사례를 통해 즉각적인 대응을 준비하고 근본 원인을 분석하며 수정 프로세스를 관리하여 정상 작업을 복원할 수 있습니다.

>[!TIP]
>
>Adobe은 위협 행위자가 Commerce 애플리케이션 및 인프라 구성에서 기존의 패치되지 않은 취약성, 낮은 암호, 취약한 소유권 및 권한 설정을 이용할 때 대부분의 보안 사고가 발생한다는 것을 발견했습니다. Adobe Commerce 설치 설정, 구성 및 업데이트 시 Adobe 보안 모범 사례를 검토하고 준수하여 보안 사고의 발생을 최소화합니다. [Commerce 사이트 및 인프라 보호](../launch/security-best-practices.md)를 참조하십시오.


## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 문제에 응답

클라우드 인프라의 Adobe Commerce 프로젝트가 보안 사고의 영향을 받는다고 의심되는 경우 중요한 첫 번째 단계는 다음과 같습니다.

- 모든 관리자 계정 액세스 감사
- 고급 MFA(Multi-Factor Authentication) 컨트롤 사용
- 중요한 로그 유지
- 사용 중인 Adobe Commerce 버전에 대한 보안 업그레이드를 검토하십시오.

자세한 권장 사항은 아래에 자세히 설명되어 있습니다.

## 공격 발생 시 즉각적인 조치 취하기

사이트 손상 시 따라야 할 몇 가지 주요 권장 사항이 있습니다.

- 시스템 통합자 및 적절한 보안 담당자와 협력하여 조사 및 시정 작업을 수행합니다.

- 공격의 범위를 확인합니다.
   - 신용 카드 정보에 액세스했습니까?
   - 어떤 정보가 도난당했나요?
   - 그 타협이 있은 후 시간이 얼마나 지났습니까?
   - 정보가 암호화되었습니까?

- 서버 로그 파일 및 파일 변경 사항을 검토하여 공격 벡터를 찾아 사이트의 손상 시기와 방법을 결정하십시오.

   - 특정 상황에서 모든 것을 지우고 다시 설치하거나 가상 호스팅의 경우 새 인스턴스를 만드는 것이 좋습니다. 맬웨어는 복원하기 위해 대기 중인 의심되지 않은 위치에 숨겨질 수 있습니다.

   - 불필요한 파일을 모두 제거합니다. 그런 다음 알려진 클린 소스에서 필요한 파일을 다시 설치합니다. 예를 들어 버전 제어 시스템이나 Adobe의 원본 배포 파일을 사용하여 다시 설치할 수 있습니다.

   - 데이터베이스, 파일 액세스, 결제 및 배송 통합, 웹 서비스 및 관리자 로그인을 포함하여 모든 자격 증명을 재설정합니다. 또한 시스템을 공격하는 데 사용할 수 있는 모든 통합 및 API 키와 계정을 재설정합니다.

## 문제 분석

사건 분석의 첫 단계는 최대한 많은 사실을 가능한 한 빨리 수집하는 것이다. 인시던트에 대한 정보를 수집하면 인시던트의 잠재적 원인을 파악하는 데 도움이 될 수 있습니다. Adobe Commerce은 사고 분석을 지원하는 아래 도구를 제공합니다.

- [관리 작업 로그 감사](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=ko).

  작업 로그 보고서에는 로깅이 활성화된 모든 관리자 작업에 대한 자세한 레코드가 표시됩니다. 각 레코드는 타임스탬프를 지정하고 사용자의 IP 주소와 이름을 등록합니다. 로그 세부 사항에는 작업 중에 수행된 관리 사용자 데이터 및 관련 변경 사항이 포함됩니다.

- [Adobe Commerce에 대한 관찰 도구](../../../tools/observation-for-adobe-commerce/intro.md)를 사용하여 이벤트를 분석합니다.

  Adobe Commerce 관찰 도구를 사용하면 복잡한 문제를 분석하여 근본 원인을 식별할 수 있습니다. 서로 다른 데이터를 추적하는 대신 이벤트와 오류의 상관 관계를 파악하여 성능 병목 현상의 원인에 대한 심층적인 통찰력을 얻을 수 있습니다.

  도구의 **보안** 탭을 사용하여 잠재적인 보안 문제를 명확하게 확인하여 근본 원인을 파악하고 사이트의 성능을 최적으로 유지할 수 있습니다.

- [New Relic 로그](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=ko)로 로그 분석

  cloud infrastructure Pro 프로젝트의 Adobe Commerce에는 [New Relic 로그](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=ko) 서비스가 포함됩니다. 이 서비스는 스테이징 및 프로덕션 환경에서 모든 로그 데이터를 집계하여 집계된 데이터를 검색하고 시각화할 수 있는 중앙 로그 관리 대시보드에 표시하도록 사전 구성되어 있습니다.

  다른 Commerce 프로젝트의 경우 [New Relic 로그](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) 서비스를 설정하고 사용하여 다음 작업을 완료할 수 있습니다.
   - 집계된 로그 데이터를 검색하려면 [New Relic 쿼리](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs)를 사용하십시오.
   - New Relic 로그 애플리케이션을 통해 로그 데이터를 시각화합니다.

## 계정, 코드 및 데이터베이스 감사

Commerce 관리 및 사용자 계정, 애플리케이션 코드, 데이터베이스 구성 및 로그를 검토하여 의심스러운 코드를 식별 및 정리하고 계정, 사이트 및 데이터베이스 액세스의 보안을 보장합니다. 그런 다음 필요에 따라 재배포합니다.

많은 사이트가 수 시간 내에 다시 손상될 수 있으므로 사고 후 사이트를 계속 면밀히 모니터링합니다. 지속적인 로그 검토 및 파일 무결성 모니터링을 통해 새로운 손상 징후를 신속하게 감지할 수 있습니다.

### 관리자 계정 감사

- [관리자 사용자 액세스 검토](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=ko)—오래되거나 사용하지 않거나 의심스러운 계정을 제거하고 모든 관리자 사용자의 암호를 회전합니다.

- [관리자 보안 설정 검토](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=ko)—관리자 보안 설정이 보안 모범 사례를 따르는지 확인하십시오.

- [클라우드 인프라 프로젝트에서 Adobe Commerce에 대한 사용자 계정 검토](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=ko) - 오래되거나 사용하지 않거나 의심스러운 계정을 제거하고 모든 클라우드 프로젝트 관리자 사용자의 암호를 회전합니다. 계정 보안 설정이 올바르게 구성되었는지 확인하십시오.

- 클라우드 인프라의 Adobe Commerce에 대한 [SSH 키 감사](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko) - SSH 키를 검토, 삭제 및 회전합니다.

### 감사 코드

- 관리자의 `website` 및 `store view`을(를) 포함한 모든 범위 수준에서 [HTML 머리글 및 바닥글 구성](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=ko)을 검토하십시오. 스크립트, 스타일 시트 및 기타 HTML 설정에서 알 수 없는 JavaScript 코드를 제거합니다. 코드 조각 추적과 같이 인식된 코드만 유지합니다.

- 현재 프로덕션 코드 베이스를 버전 제어 시스템(VCS)에 저장된 코드 베이스와 비교합니다.

- 의심스러운 코드를 격리합니다.

- 코드 베이스를 프로덕션 환경에 재배포하여 의심스러운 코드의 나머지 부분이 없는지 확인합니다.

### 데이터베이스 구성 및 로그 감사

- 수정 사항에 대해서는 저장된 절차를 검토하십시오.

- Commerce 인스턴스에서만 데이터베이스에 액세스할 수 있는지 확인합니다.

- 공개적으로 사용 가능한 맬웨어 검색 도구를 사용하여 사이트를 스캔하여 맬웨어가 더 이상 존재하지 않는지 확인합니다.

- 이름을 변경하고 사이트 `app/etc/local.xml` 및 `var` URL에 공개적으로 액세스할 수 없는지 확인하여 관리 패널의 보안을 유지하십시오.

- 많은 사이트가 수 시간 내에 다시 손상될 수 있으므로 사고 후 사이트를 계속 면밀히 모니터링합니다. 지속적인 로그 검토 및 파일 무결성 모니터링을 통해 새로운 손상 징후를 신속하게 감지할 수 있습니다.

## Google 경고 제거

사이트에 악성 코드가 포함되어 있는 것으로 Google에 의해 플래그가 지정된 경우 사이트를 정리한 후 검토를 요청합니다. 맬웨어에 감염된 사이트에 대한 리뷰는 며칠 걸립니다. Google에서 사이트가 깨끗하다고 결정하면 검색 결과와 브라우저의 경고가 72시간 이내에 사라집니다. [검토 요청](https://web.dev/articles/request-a-review)을 참조하세요.

## 맬웨어 결과 검사 목록 검토

공개적으로 사용 가능한 맬웨어 검색 도구가 맬웨어 공격을 확인한 경우 해당 사건을 조사하십시오. 솔루션 통합자와 협력하여 사이트를 정리하고 권장되는 교정 프로세스를 수행합니다.

## 추가 검토 수행

정교한 공격을 처리할 때는 숙련된 개발자, 타사 전문가 또는 솔루션 통합업체와 협력하여 사이트를 완전히 복구하고 보안 사례를 검토하는 것이 모범 사례입니다. 숙련된 보안 전문가와 협력하여 비즈니스와 고객의 안전을 보장하기 위해 종합적이고 고급 조치를 취하도록 보장합니다.

## 추가 정보

- [근본 원인 분석 프레임워크](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
