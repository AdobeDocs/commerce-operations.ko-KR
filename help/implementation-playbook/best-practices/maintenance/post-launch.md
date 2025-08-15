---
title: 출시 후 지원 및 유지 관리
description: 포괄적인 출시 후 지원 및 유지 관리 모범 사례를 통해 Adobe Commerce 스토어의 최적의 성능과 보안을 보장합니다.
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Adobe Commerce에 대한 출시 후 지원 및 유지 관리

출시 후 지원 및 유지 관리는 Adobe Commerce 스토어가 원활하게 실행되고, 성능이 우수하며, 안전하게 유지되고, 비즈니스 목표를 지속적으로 충족하도록 하는 데 중요합니다. 이 단계에는 지속적인 모니터링, 최적화, 버그 수정, 업데이트 및 사용자 지원이 포함됩니다. 다음 섹션에서는 **출시 후 지원**&#x200B;을 주요 범주로 분류합니다.

## 정기적인 사이트 모니터링 및 성능 최적화

### 성능 모니터링

- **사이트 속도 및 부하 테스트**: Adobe Commerce은 리소스를 많이 사용할 수 있으므로 정기적인 성능 모니터링이 중요합니다.

   - **사용할 도구**: 클라우드 인프라 프로젝트의 모든 Adobe Commerce에 New Relic에 대한 액세스가 포함되어 있어 Commerce 애플리케이션 및 클라우드 인프라 내에서 성능을 모니터링하고 이벤트를 조사하는 데 도움이 됩니다. 추가 도구로는 Google PageSpeed Insights 및 GTMetrix가 있습니다.

   - **모니터링할 항목**: 다음은 클라우드 인프라에서 Adobe Commerce을 모니터링하는 기본 항목입니다.

      - **상태 알림**: 디스크 공간 및 환경 상태에 대한 경고입니다.

      - **관찰**: 효과적인 사이트 관리를 위해 여러 소스의 로그 데이터를 결합한 포괄적인 모니터링

      - **New Relic 서비스**: 주요 지표를 중심으로 스테이징 및 프로덕션의 성능을 모니터링합니다.

      - **관리 경고 정책**: 사전 정의된 임계값이 있는 지표를 추적하여 성능에 영향을 주는 인프라 또는 응용 프로그램 문제에 대한 알림을 트리거합니다.

  >[!TIP]
  >
  >[Cloud Guide](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/monitor/performance)에서 _성능 모니터링_&#x200B;을 참조하십시오.


- **데이터베이스 성능 최적화**: Adobe Commerce Cloud에서 데이터베이스 성능을 최적화하려면 다음을 구현합니다.

   - **MySQL 쿼리 모니터링 및 최적화**: MySQL의 SHOW FULL PROCESSLIST 및 EXPLAIN 명령을 사용하여 수행할 수 있는 느리게 실행되는 쿼리를 식별하고 해결합니다. 보다 복잡한 설정의 경우 Pro 아키텍처 사용자는 Percona Toolkit을 사용하여 성능 문제에 대한 쿼리 로그를 분석할 수 있습니다.

   - **인덱스 관리**: 모든 테이블에 기본 키가 있는지 확인하고 중복된 인덱스를 제거하십시오. 이렇게 하면 동시 쓰기 중에 효율성이 떨어지고 충돌이 발생할 수 있습니다.

   - **Cron 작업 최적화**: 성능에 미치는 영향을 최소화하려면 특히 색인화와 같은 백그라운드 작업이 잦은 경우 사용량이 적은 시간 동안 Cron 작업을 예약해야 합니다.

  >[!TIP]
  >
  >데이터베이스 성능 문제를 해결하기 위한 [모범 사례](resolve-database-performance-issues.md)를 참조하세요.

- **CDN 모니터링**: Adobe Commerce Cloud에서 Fastly CDN 성능을 모니터링하려면 다음 작업을 수행할 수 있습니다.

   - **모니터링을 위해 New Relic 활용**: Adobe Commerce은 New Relic을 제공하여 스테이징 및 프로덕션 환경에서 Fastly 성능 및 기타 지표를 모니터링합니다. 이 도구는 시간 경과에 따른 서버 상태, CDN 캐싱 및 네트워크 요청에 대한 통찰력을 제공하여 패턴을 식별하고 CDN 설정을 최적화하는 데 도움이 됩니다.

   - **Fastly 로그 분석**: Adobe Commerce Cloud Pro 프로젝트의 경우 New Relic 로그를 사용하여 Fastly CDN 및 WAF 로그 데이터를 검토하고 분석하여 성능 트렌드, 보안 이벤트를 추적하고 오류 또는 지연 문제를 진단할 수 있습니다.

   - **cURL 명령 사용**: Fastly 관련 헤더로 cURL 명령을 실행하여 사이트의 캐시 상태를 검사합니다. 주요 응답 헤더에는 캐싱 및 모듈 상태를 확인하기 위한 `X-Cache`(HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` 및 `Cache-Control`이(가) 포함됩니다. Adobe은 스테이징 및 프로덕션 환경 모두에 대한 샘플 cURL 명령을 제공합니다.

   - **헤더 정보 확인**: `Cache-Control`, `Pragma`, `X-Magento-Tags` 등의 헤더를 검사하여 캐시된 콘텐츠에 대한 적절한 캐싱 동작과 태그 처리를 확인합니다. 적절한 헤더 값은 캐싱 구성이 CDN에서 효과적으로 적용되는지 여부를 나타냅니다.

   - **빠른 디버깅 및 테스트**: Fastly의 디버깅 기능을 사용하여 캐시 적중률 및 실패율, 캐싱 논리 또는 잘못된 헤더 응답 관련 문제를 식별하고 해결합니다. 이는 구성 문제 또는 예상 캐싱 규칙과의 오정렬을 가리킬 수 있습니다.

이러한 모니터링 단계는 최적의 CDN 성능을 유지하고 사이트 속도 및 안정성에 영향을 주는 문제를 해결하는 데 도움이 됩니다.

>[!TIP]
>
>[Cloud Guide](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly)에서 _Fastly 서비스 개요_&#x200B;를 참조하십시오.

#### 정기 보안 모니터링

Adobe Commerce Cloud에서 정기적인 보안 모니터링을 유지하기 위해 Adobe에서는 지속적인 스캔, 로깅 및 사전 보안 작업과 관련된 다각적인 접근 방식을 권장합니다. 다음은 지속적인 보안을 보장하기 위한 몇 가지 핵심 작업입니다.

- **보안 검색**: Adobe의 보안 검색 도구를 사용하여 Commerce 사이트에서 알려진 취약점 및 맬웨어를 모니터링합니다. 이 도구는 잠재적인 보안 위험 및 규정 준수 문제에 대한 경고를 제공합니다.

- **일반 패치 및 업데이트 유지 관리**: Adobe의 보안 패치 및 업데이트를 사용할 수 있게 되면 적용합니다. 최신 Adobe Commerce 버전으로 업그레이드하면 위협에 대한 최신 방어 수단이 제공됩니다.

- **감사 및 로그 모니터링**: New Relic 로그(Pro 프로젝트에 사용 가능)와 같은 도구를 사용하여 스테이징 및 프로덕션 환경에서 보안 로그를 중앙 집중화하고 분석함으로써 잠재적인 보안 문제와 위반 가능성을 높일 수 있습니다.

- **계정 및 액세스 관리**: 인증되지 않았거나 오래된 계정을 제거하기 위해 정기적으로 사용자 및 관리자 계정을 감사합니다. 관리자 사용자를 위한 MFA(다단계 인증)를 통해 액세스 제어를 강화합니다.

- **웹 응용 프로그램 방화벽(WAF)**: 통합된 Fastly WAF을 사용하여 승인되지 않은 데이터 추출 시도와 같은 악의적인 트래픽 패턴의 위협을 감지하고 완화합니다.

- **사용자 지정 코드 및 확장 보안**: 일반 코드 감사를 수행하고 확장을 Adobe에서 검사하는 것으로 제한하여 사용자 지정 코드 또는 타사 확장을 보호합니다.

>[!TIP]
>
>[관리 시스템 안내서](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/security)에서 _보안_&#x200B;을 참조하십시오.

#### 오류 로깅 및 모니터링

Adobe Commerce Cloud에서 오류 로깅을 모니터링하기 위해 Adobe에서는 효과적인 문제 해결 및 성능 관리를 위한 몇 가지 도구와 사례를 제공합니다.

- **New Relic을 사용한 로그 집계**: New Relic은 인프라, CDN 및 WAF과 관련된 로그를 포함하여 Adobe Commerce 애플리케이션에서 로그를 수집하고 중앙 집중화합니다. 이 설정을 사용하면 능률적인 오류 추적, 대시보드 만들기 및 로그 쿼리를 통해 애플리케이션 성능 및 문제에 대한 심층적인 통찰력을 얻을 수 있습니다. New Relic 로그에 액세스하면 다양한 특성으로 로그를 검색하고 필터링하여 문제를 신속하게 진단할 수 있습니다.

- **오류 로그 유형**: Adobe Commerce Cloud의 주요 오류 로그에는 배포 피드백이 포함된 `cloud.log`과(와) 배포 경고 및 오류를 기록하는 `cloud.error.log`이(가) 포함됩니다. 디버깅을 위한 다른 특정 로그에는 `debug.log`, `system.log` 및 `exception.log`이(가) 있으며, 각 로그는 Commerce 플랫폼 전반에서 오류 및 이벤트 추적에 고유한 역할을 제공합니다.

- **Monolog를 사용한 사용자 지정 로깅**: Adobe Commerce은 개발자가 파일, 데이터베이스 및 경고와 같은 다양한 대상에 로그 메시지를 보낼 수 있는 Monolog를 통한 사용자 지정 로깅을 지원합니다. 이러한 유연성은 개발 및 프로덕션 환경의 다양한 모니터링 요구 사항에 맞는 고급 로깅 전략을 구축하는 데 유용합니다.

- **사이트 전체 분석 도구를 사용한 예외 모니터링**: 사이트 전체 분석 도구는 예외 로그를 모니터링하고 관리하여 배포 및 응용 프로그램 이벤트에서 반복되는 문제를 식별하는 데 도움이 됩니다. 이 도구는 자주 발생하는 문제를 강조하여 성능에 영향을 주는 중요한 문제를 보다 쉽게 우선 순위를 지정하고 해결할 수 있도록 합니다.

>[!TIP]
>
>Adobe Commerce Cloud의 로깅 및 오류 추적 사례에 대한 자세한 내용은 [New Relic 로그 관리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) 및 [예외 모니터링](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions)을 참조하십시오.

### 보안 및 업데이트

#### 보안 패치 및 업데이트

다음은 Adobe Commerce Cloud 시스템의 보안을 유지하고 업데이트하기 위한 보안 패치 및 업데이트 모니터링의 주요 사례입니다.

- **Adobe Commerce 보안 경고에 가입**: [Adobe의 알림을 등록](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/security)하여 보안 취약점에 대한 정보를 지속적으로 받아 보십시오.

- **릴리스 정보 확인**: 버전(예: 2.3.5-p1)에 대해 &quot;-pN&quot; 태그가 지정된 [보안 패치 릴리스 정보](https://experienceleague.adobe.com/ko/docs/commerce-operations/release/notes/security-patches/overview)을 정기적으로 검토하고 중요한 수정 사항 및 개선 사항을 포함합니다.

- **보안 패치를 즉시 적용**: 가능한 즉시 보안 패치를 적용합니다. 여기에는 최신 버전으로 업데이트하거나 특정 패치 파일을 적용하는 것이 포함됩니다.

- **클라우드 패치 사용**: Adobe Commerce Cloud의 경우 보안 패치가 클라우드 도구 세트 내에 번들로 제공될 수 있습니다. 이러한 수정 사항을 받으려면 세트 또는 Commerce 버전을 업그레이드해야 합니다.

- **자동 패치 관리**: 중앙 패처 같은 도구를 사용하여 [여러 저장소에 패치를 자동으로 관리하고 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)하는 것이 좋습니다.

>[!TIP]
>
>패치 적용 및 보안 유지에 대한 자세한 내용과 단계별 지침은 [보안 패치 릴리스 노트](../../../release/release-notes/security/overview.md) 및 [보안 패치를 적용하는 방법](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)을 참조하십시오. [사이트 전체 분석 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/site-wide-analysis-tool/access) 보고서도 검토해야 합니다.

#### PCI 준수

Adobe Commerce Cloud에서 PCI 규정을 준수하려면 다음 주요 사례를 따르십시오.

- **카드 소지자 데이터 보호**: 카드 소지자 데이터를 Adobe Commerce 내에 저장하지 마십시오. 스토리지가 필요한 경우 암호화 및 토큰화된 방법을 사용하여 보호하십시오.

- **보안 전송 프로토콜 사용**: 암호화 및 적절한 키 관리를 사용하여 항상 TLS와 같은 보안 프로토콜을 통해 결제 데이터를 전송합니다.

- **웹 응용 프로그램 방화벽(WAF) 활용**: Fastly를 기반으로 하는 WAF 서비스는 PCI DSS 6.6 요구 사항을 충족하고 사이트에 도달하기 전에 악성 트래픽을 차단하여 일반적인 취약점으로부터 보호합니다. 자세한 내용은 [여기](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) 및 [여기](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)를 참조하세요.

- **액세스 제한**: 권한이 있는 직원만 중요한 결제 데이터에 액세스할 수 있는지 확인하고 [액세스 제어를 적용하여 노출 위험을 줄이십시오](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **정기적인 보안 검색**: 정기적인 PCI ASV 검색을 수행하고 [환경을 모니터링](https://experienceleague.adobe.com/ko/docs/commerce-operations/security-and-compliance/shared-responsibility)하여 잠재적인 취약점을 해결합니다.

>[!TIP]
>
>Adobe Commerce을 통한 PCI 규정 준수에 대한 자세한 지침은 [결제 처리 및 저장 모범 사례](../planning/payment-processing-storage.md)를 참조하세요.

### 사용자 및 고객 지원

#### 설정

- **지원 채널**: 다음과 같은 고객 지원 채널을 구현합니다.

   - **실시간 채팅**: 즉각적인 지원을 위해 실시간 채팅 지원을 제공합니다. 인기 있는 솔루션으로는 Zendesk, Intercom, Tidio 등이 있다.

   - **이메일 지원**: Freshdesk 또는 Zoho Desk와 같은 지원 티켓 시스템을 사용하여 고객 문의 사항을 효과적으로 관리합니다.

   - **전화 지원**: 고객 기반이 많은 경우 업무 시간 동안 전화 지원을 제공하는 것이 좋습니다.

#### 관리자 교육

- **내부 교육**: 직원에게 Adobe Commerce 관리자 사용 방법, 주문 처리 방법, 제품 관리 방법 및 고객 서비스 문제 처리 방법을 교육합니다.

- **설명서**: FAQ, 문제 해결 및 일반적인 작업에 대한 내부 기술 자료 또는 사용 설명서를 유지 관리합니다.

#### 고객 경험 최적화

- **설문 조사 및 피드백**: 설문 조사를 사용하여 고객의 피드백을 수집하고 고객 경험을 최적화합니다. Adobe Commerce은 SurveyMonkey 또는 Google Forms과 같은 도구와의 통합을 지원합니다.

- **리뷰 관리**: 제품에 대한 고객 리뷰 및 등급을 관리합니다. 행복한 고객이 부정적인 리뷰를 적절하게 응답하면서 리뷰를 남길 수 있도록 장려합니다.

- **Personalization**: 개인화된 제품 권장 사항이나 타깃팅된 프로모션과 같은 개인화 기능을 구현합니다.

### 지속적인 저장소 유지 관리 및 최적화

#### SEO(검색 엔진 최적화)

- **콘텐츠 최적화**: 검색 엔진과 관련된 콘텐츠를 최신 상태로 유지하기 위해 제품 설명, 블로그 게시물 및 카테고리 페이지를 정기적으로 업데이트합니다.

- **SEO 감사**: Google 검색 콘솔 또는 Screaming Frog와 같은 도구를 사용하여 정기적으로 SEO 감사를 수행하여 SEO 문제(예: 끊어진 링크, 누락된 메타데이터, 중복 콘텐츠)를 식별합니다.

- **URL 구조**: 깔끔하고 논리적인 URL 구조를 유지하고 끊어진 링크 또는 리디렉션이 없는지 확인합니다.

#### 전환율 최적화(CRO)

- **A/B 테스트**: 제품 페이지나 체크아웃 프로세스와 같은 다른 페이지 요소에서 A/B 테스트를 실행하여 전환율을 개선합니다.

- **장바구니 포기**: 장바구니 포기 이메일 캠페인이나 종료 목적 팝업을 구현하여 손실된 판매를 복구합니다.

- **체크아웃 최적화**: 단계 수를 줄이고 게스트 체크아웃을 제공하여 체크아웃 프로세스를 단순화하여 전환을 개선합니다.

#### 마케팅 통합

- **이메일 캠페인**: 환영 이메일, 포기한 장바구니 이메일 및 구매 후 후속 작업에 대해 자동화된 이메일 마케팅 흐름을 설정합니다. Adobe Marketo, Mailchimp 또는 Klaviyo와 같은 플랫폼은 Adobe Commerce과 잘 통합됩니다.

- **소셜 미디어 및 광고 통합**: Facebook, Instagram 및 Google 광고와 같은 플랫폼과 통합하여 타깃팅된 캠페인을 실행하고 성과를 추적하세요.

#### 모바일 최적화

- **모바일 응답성**: 사이트의 모바일 응답성과 사용성을 정기적으로 테스트합니다. 모바일 커머스가 성장하고 있다는 점에서 지속적인 성공을 위해서는 모바일 우선적 접근이 필수적이다.

- **모바일 성능**: Google의 모바일 친화적 테스트 및 성능 도구를 사용하여 모바일 스토어 환경을 최적화합니다.

### 확장 및 새로운 기능 개발

- **트래픽 처리를 위한 자동 크기 조정**:

   - Adobe Commerce Cloud는 실시간 트래픽 요구에 따라 서버 리소스(예: 웹 노드)를 동적으로 조정하기 위한 자동 크기 조절을 지원하여 스토어에서 수동 개입 없이 높은 방문자 볼륨을 처리할 수 있도록 합니다. [클라우드 가이드](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/autoscaling)에서 _자동 크기 조정_&#x200B;을 참조하십시오.

   - 웹 계층과 서비스 계층은 독립적으로 확장할 수 있으며, 트래픽을 늘리기 위해 웹 노드를 추가하고 피크 기간 동안 백엔드 성능을 높이기 위해 데이터베이스 또는 서비스 노드를 확장할 수 있습니다. [클라우드 가이드](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)에서 _조정된 아키텍처_&#x200B;을(를) 참조하십시오.

- **성능 모니터링**:

   - **New Relic**&#x200B;을(를) 사용하여 실시간 성능 지표(예: CPU 사용, 트래픽 수준)를 모니터링하고 필요에 따라 조정합니다.

   - 프로덕션 문제를 방지하기 위해 크기 조정 전에 스테이징 환경에서 성능을 테스트합니다.

- **새로운 기능 개발**:

   - **AI 기반 개인화**, **구독 관리** 및 사용자 지정 솔루션과 같은 고급 기능을 통합합니다.

   - 프로덕션 환경에 배포하기 전에 스테이징 환경에서 기능을 지속적으로 테스트하고 세분화하여 가동 중지 시간을 최소화합니다.

- **사이트 유지 관리 진행 중**:

   - 정기적으로 시스템 로그 및 성능 지표를 검토하여 개선할 영역을 파악합니다.

   - 새로운 비즈니스 요구 사항과 성장에 맞게 인프라스트럭처를 확장 및 조정할 수 있습니다.

>[!TIP]
>
>자세한 지침은 [유지 관리 모범 사례](overview.md), [개인화](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) 및 [기능 개발](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)을 참조하세요.

### 보고 및 분석

- Adobe Commerce의 핵심 기능인 **Adobe Commerce Intelligence:** Commerce Intelligence은 여러 데이터 소스에 대한 모범 사례 인사이트를 제공하여 판매자가 과학적 데이터 기반 결정을 내리고 명확하고 정보에 입각한 조치를 취할 수 있도록 합니다. [_Commerce Intelligence 사용 안내서_](https://experienceleague.adobe.com/ko/docs/commerce-business-intelligence/mbi/getting-started)를 참조하세요.

- **Adobe Analytics:** Adobe Analytics은 온라인 스토어의 성능을 추적, 분석 및 최적화할 수 있는 강력한 솔루션을 제공합니다. Adobe Analytics은 전자 상거래 비즈니스가 고객 행동, 제품 성능, 전환율 및 기타 주요 지표에 대한 심층적인 통찰력을 확보하여 데이터 중심의 의사 결정을 가능하게 합니다.

- **Google Analytics:** Google Analytics을 사용하여 고객 동작, 트래픽 소스 및 전환율을 추적합니다.

- **추가 Commerce Intelligence 도구:** Adobe Commerce에 고급 보고가 포함되어 있습니다. 이 기능을 사용하면 제품, 주문 및 고객 데이터를 기반으로 하는 동적 보고서 세트에 액세스할 수 있으며, 비즈니스 요구 사항에 맞게 개인화된 대시보드를 사용할 수 있습니다. 자세한 내용은 [관리 사용 안내서](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting)의 _고급 보고_&#x200B;를 참조하십시오.

### 결론

출시 후 지원 및 유지 관리는 Adobe Commerce 스토어가 계속 우수한 성과를 유지하고 안전하게 유지하며 비즈니스 요구에 적응할 수 있도록 정기적으로 관리해야 하는 지속적인 노력입니다. 사이트 모니터링, 고객 지원, 최적화 및 업데이트에 대한 구조화된 접근 방식을 구현하는 것은 장기적인 성공에 중요합니다.
