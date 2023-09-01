---
title: 클라우드 인프라 보안
description: Adobe이 클라우드 인프라에서 Adobe Commerce을 안전하게 유지하는 방법에 대해 알아봅니다.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: afe70569796c056cd0ecab82898f0dec016e7a3f
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 0%

---


# 보안

더 Adobe Commerce [Pro 플랜 아키텍처](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) 는 매우 안전한 환경을 제공하도록 설계되었습니다. 각 고객은 다른 고객과 분리된 고유한 서버 환경에 배포됩니다. 프로덕션 환경의 보안 세부 정보는 아래에 설명되어 있습니다.

## 웹 브라우저

클라우드 환경으로 들어오고 나가는 트래픽의 대부분은 소비자의 웹 브라우저에서 발생합니다. 소비자 트래픽은 웹 사이트의 모든 페이지에 대해 HTTPS를 사용하여 보호할 수 있습니다(추가 요금으로 공유 SSL 인증 또는 고객 고유의 SSL 인증서 사용). 체크아웃 및 계정 페이지는 항상 HTTPS를 사용하여 제공됩니다. 가장 좋은 방법은 HTTPS에서 모든 페이지를 제공하는 것입니다.

## 컨텐츠 전달 네트워크

Fastly는 CDN(Content Delivery Network) 및 DDoS(Distributed Denial of Service) 보호 기능을 제공합니다. Fastly CDN은 원본 서버에 대한 직접 액세스를 격리하는 데 도움이 됩니다. 공용 DNS는 Fastly 네트워크를 가리킬 뿐입니다. Fastly DDoS 솔루션은 시스템 중단을 일으키는 L3 및 L4 공격과 복잡한 L7 공격으로부터 보호합니다. 레이어 7 공격은 전체 HTTP/HTTPS 요청을 기반으로 하고 헤더, 쿠키, 요청 경로, 클라이언트 IP를 포함한 클라이언트 및 요청 기준이나 지리적 위치와 같은 지표를 기반으로 하는 사용자 지정 규칙을 사용하여 차단할 수 있습니다.

다음을 참조하십시오 [Fastly 서비스 개요](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) 다음에서 _Cloud 안내서_.

## 웹 애플리케이션 방화벽

Fastly Web Application Firewall(WAF) 은 추가적인 보호를 제공하는 데 사용됩니다. Fastly의 클라우드 기반 WAF는 OWASP 핵심 규칙 세트와 같은 상용 및 오픈 소스 소스의 타사 규칙을 사용합니다. 또한 Adobe Commerce 관련 규칙이 사용됩니다. 주입 공격과 악의적인 입력, 교차 사이트 스크립팅, 데이터 내보내기, HTTP 프로토콜 위반 및 기타 OWASP 상위 10가지 위협을 포함한 주요 애플리케이션 계층 공격으로부터 고객을 보호합니다.

Adobe Commerce에서 소프트웨어 패치 전에 Managed Services에서 보안 문제를 &quot;가상으로 패치&quot;할 수 있는 새로운 취약점을 감지해야 하는 경우 WAF 규칙이 업데이트됩니다. Fastly WAF는 속도 제한 또는 봇 탐지 서비스를 제공하지 않습니다. 원하는 경우 고객은 Fastly와 호환되는 서드파티 봇 탐지 서비스에 라이선스를 부여할 수 있습니다.

다음을 참조하십시오 [WAF(Web Application Firewall)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service.html) 다음에서 _Cloud 안내서_.

## 가상 사설 클라우드

Adobe Commerce Pro 플랜 프로덕션 환경은 Virtual Private Cloud(VPC)로 구성되므로 프로덕션 서버는 격리되고 클라우드 환경 안팎에 연결하는 기능이 제한됩니다. 클라우드 서버에 대한 보안 연결만 허용됩니다. SFTP 또는 rsync와 같은 보안 프로토콜을 파일 전송에 사용할 수 있습니다.

고객은 SSH 터널을 사용하여 애플리케이션과 안전하게 통신할 수 있습니다. 추가 요금으로 AWS PrivateLink에 액세스할 수 있습니다. 이러한 서버에 대한 모든 연결은 환경에 대한 연결을 제한하는 가상 방화벽인 AWS 보안 그룹을 사용하여 제어됩니다. 고객의 기술 리소스는 SSH를 사용하여 이러한 서버에 액세스할 수 있습니다.

## 암호화

Amazon Elastic Block Store(EBS)는 스토리지에 사용됩니다. 모든 EBS 볼륨은 AES-265 알고리즘을 사용하여 암호화됩니다. 즉, 데이터는 항상 암호화됩니다. 또한 시스템은 CDN과 원본 간, 원본 서버 간에 전송되는 데이터도 암호화합니다. 고객 암호는 해시로 저장됩니다. 결제 게이트웨이 자격 증명을 포함한 중요한 자격 증명은 SHA-256 알고리즘을 사용하여 암호화됩니다.

Adobe Commerce 애플리케이션은 데이터가 유휴 상태이거나 서버 간에 전송되지 않을 때 열 또는 행 수준 암호화 또는 암호화를 지원하지 않습니다. 고객은 애플리케이션 내에서 암호화 키를 관리할 수 있습니다. 시스템에서 사용하는 키는 AWS 키 관리 시스템에 저장되며, 서비스의 일부를 제공하기 위해 Managed Services에서 관리해야 합니다.

## 엔드포인트 감지 및 응답

[!DNL CrowdStrike Falcon], 경량의 차세대 EDR(Endpoint Detection and Response) 에이전트가 Adobe 내의 모든 엔드포인트(서버 포함)에 설치됩니다. EDR 에이전트는 실시간 연속 모니터링 및 수집을 통해 Adobe 데이터와 시스템을 보호하므로 신속한 위협 식별 및 대처가 가능합니다.

## 침투 테스트

Managed Services은 기본 제공 애플리케이션을 사용하여 Adobe Commerce 클라우드 시스템의 정기 침투 테스트를 수행합니다. 고객은 사용자 지정된 애플리케이션의 침투 테스트를 담당합니다.

## 결제 게이트웨이

Adobe Commerce에는 신용 카드 데이터가 소비자의 브라우저에서 결제 게이트웨이로 직접 전달되는 결제 게이트웨이 통합이 필요합니다. Adobe Commerce Pro 플랜 Managed Services 환경에서는 카드 데이터를 사용할 수 없습니다. 전자 상거래 애플리케이션에 의한 트랜잭션에 대한 작업은 게이트웨이의 트랜잭션에 대한 참조를 사용하여 완료됩니다.

## Adobe Commerce 애플리케이션

Adobe은 핵심 애플리케이션 코드에서 보안 취약점을 정기적으로 테스트합니다. 결함 및 보안 문제에 대한 패치가 고객에게 제공됩니다. 제품 보안 팀은 OWASP 애플리케이션 보안 지침에 따라 Adobe Commerce 제품을 확인합니다. 여러 보안 취약성 평가 도구와 외부 공급업체를 사용하여 규정 준수를 테스트하고 검증합니다. 보안 도구에는 다음이 포함됩니다.

- Veracode 정적 및 동적 스캔
- RIPS 소스 코드 스캔
- Trustwave 및 Alert Logic의 취약성 검색 서비스
- Burp Suite Pro
- 오와십자프
- andSqlMap

전체 코드 베이스는 이러한 도구를 사용하여 격주로 검사됩니다. 고객은 직접 이메일, 애플리케이션 및 을 통해 보안 패치에 대한 알림을 받게 됩니다. [보안 센터](https://helpx.adobe.com/security.html).

고객은 PCI 지침에 따라 릴리스 후 30일 이내에 이러한 패치가 사용자 정의 애플리케이션에 적용되었는지 확인해야 합니다. Adobe은 [보안 검색 도구](https://docs.magento.com/user-guide/magento/security-scan.html) 이를 통해 판매자는 정기적으로 사이트를 모니터링하고 알려진 보안 위험, 맬웨어 및 무단 액세스에 대한 업데이트를 받을 수 있습니다. 보안 검색 도구는 무료 서비스이며 모든 버전의 Adobe Commerce에서 실행할 수 있습니다.

보안 연구원이 취약점을 식별하고 보고하도록 장려하기 위해 Adobe Commerce에는 [버그 보상 프로그램](https://hackerone.com/magento) 내부 테스트 외에. 또한 고객은 원하는 경우 자체 검토를 위해 애플리케이션의 전체 소스 코드를 제공받습니다.

## 읽기 전용 파일 시스템

모든 실행 코드는 읽기 전용 파일 시스템 이미지에 배포되므로 공격에 사용할 수 있는 표면이 크게 줄어듭니다. 배포 프로세스는 Squash-FS 이미지를 만들어 시스템에 PHP 또는 JavaScript 코드를 삽입하거나 Adobe Commerce 애플리케이션 파일을 수정할 수 있는 기회를 줄입니다.

## 원격 배포

Managed Services 프로덕션 환경으로 실행 코드를 가져오는 유일한 방법은 프로비저닝 프로세스를 통해 실행하는 것입니다. 프로비저닝에는 소스 저장소의 소스 코드를 배포 프로세스를 시작하는 원격 저장소로 푸시하는 작업이 포함됩니다. 해당 배포 대상에 대한 액세스가 제어되므로 배포 대상에 액세스할 수 있는 사용자를 완벽하게 제어할 수 있습니다. 비프로덕션 환경에 대한 모든 애플리케이션 코드 배포는 고객이 제어합니다.

## 로깅

모든 AWS 활동이 AWS CloudTrail에 기록됩니다. 운영 체제, 애플리케이션 서버 및 데이터베이스 로그는 운영 서버에 저장되고 백업에 저장됩니다. 모든 소스 코드 변경 사항은 Git 저장소에 기록됩니다. 배포 기록은 Adobe Commerce에서 사용할 수 있습니다. [프로젝트 웹 인터페이스](https://devdocs.magento.com/cloud/project/projects.html#login). 모든 지원 액세스가 기록되고 지원 세션이 기록됩니다.

다음을 참조하십시오 [로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) 다음에서 _Cloud 안내서_.

## 중요 데이터

중요한 데이터는 소비자의 개인 정보나 Managed Services 고객의 기밀 데이터를 포괄할 수 있습니다. 민감한 고객 및 소비자 데이터를 보호하는 것은 Adobe Commerce Managed Services에 있어 중요한 의무입니다. Managed Services 및 Adobe 고객 모두 개인 식별 정보에 대한 법적 의무가 있습니다. 아키텍처의 보안 기능 외에도 중요한 데이터에 대한 배포 및 액세스를 제한하는 다른 제어 기능이 있습니다.

고객은 자신의 데이터를 소유하고 해당 데이터가 있는 위치를 제어합니다. 고객은 프로덕션 및 개발 인스턴스가 상주하는 위치를 지정합니다. 또한 Commerce가 있는 Adobe Commerce 보고 환경에 사용되는 위치와 해당 Adobe Commerce 보고 애플리케이션이 개인 식별 정보에 액세스할 수 있는지 여부도 지정합니다. 프로덕션 인스턴스는 대부분의 AWS 지역에 있을 수 있지만 개발 및 Adobe Commerce 보고 환경은 현재 미국 또는 유럽 연합에서 찾을 수 있습니다.

중요한 데이터는 Fastly CDN 서버 네트워크를 통과할 수 있지만 Fastly 네트워크에 저장되지 않습니다. Managed Services에 포함된 모든 파트너는 민감한 데이터를 보호하기 위한 계약상의 의무를 지닙니다. Managed Services은 고객이 지정한 위치에서 중요한 고객 또는 소비자 데이터를 이동하지 않습니다.

Managed Services 제품에 포함된 서비스를 제공하는 과정에서 Managed Services 직원은 중요한 데이터가 포함된 프로덕션 시스템에 액세스해야 합니다. 이러한 직원들은 민감한 고객 및 소비자 데이터를 보호하기 위한 의무에 대해 교육을 받습니다. 이러한 시스템에 대한 액세스는 액세스가 필요한 직원으로 제한됩니다. 이러한 직원은 이러한 서비스를 제공하는 데 필요한 시간 동안만 액세스할 수 있습니다.

## 일반 데이터 보호 규정

개인정보보호법(GDPR)은 유럽연합(EU)에서 개인에 대한 개인정보 수집 및 처리에 대한 가이드라인을 설정하는 법적 프레임워크입니다. 이러한 규정은 사이트의 기반이 되는 위치에 관계없이 적용되며 EU 방문자는 해당 사이트에 액세스할 수 있습니다.

방문자는 사이트에서 수집하는 데이터에 대한 알림을 받고 정보 수집에 명시적으로 동의해야 합니다. 사이트는 사이트에서 보유하고 있는 개인 데이터가 침해된 경우 방문자에게 알려야 합니다.

사이트를 운영하는 판매자 또는 회사에는 사이트의 데이터 보안을 감독하는 데이터 보호 전담 책임자가 있어야 합니다. 방문자가 데이터 삭제를 요청하는 경우 데이터 개인정보 보호 관리자(또는 웹 사이트 관리 팀)에 연락할 수 있어야 합니다.

GDPR은 수집된 개인 식별 정보(이름, 인종, 생년월일 등)가 익명 처리되거나 가명 처리되도록 요구합니다.

>[!NOTE]
>
>이 페이지에서는 GDPR에 대해 고려해야 할 사항에 대한 일반적인 개요를 제공합니다. 다음을 참조하십시오. _[보안 및 규정 준수 안내서](../../../security-and-compliance/privacy/gdpr.md)_ Adobe Commerce이 개인 정보를 저장하는 방법에 대한 자세한 내용. 비즈니스가 법적 의무를 준수하는 방법을 결정하려면 법률 고문과 상담하거나 다음을 참조하십시오. [공식 텍스트](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## 백업

백업은 지난 24시간 동안 매 시간마다 수행됩니다. 24시간 이후에는 AWS EBS 스냅샷 서비스를 사용하여 일정에 따라 백업이 유지됩니다. 다음을 참조하십시오 [보존 정책](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#retention-policy) 다음에서 _Cloud 안내서_.

이 서비스는 중복 스토리지에 독립적인 백업을 만듭니다. EBS 볼륨은 암호화되므로 백업도 암호화됩니다. 또한 Managed Services은 고객 요청에 따라 온디맨드 백업을 수행합니다.

Managed Services 백업 및 복구 방식에서는 전체 시스템 백업과 함께 고가용성 아키텍처를 사용합니다. 각 프로젝트는 세 개의 별도 AWS 가용 영역(각 영역은 별도의 데이터 센터)에 걸쳐 모든 데이터, 코드 및 에셋으로 복제됩니다.

다음을 참조하십시오 [스냅샷 및 백업 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) 다음에서 _Cloud 안내서_.
