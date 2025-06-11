---
title: Adobe Managed Services
description: Adobe Managed Services이 Adobe Commerce 구현을 지원하고 유지하는 데 어떻게 도움이 되는지 알아봅니다.
exl-id: b600b0e3-c6fd-4b86-ad2a-a445e599f1bd
feature: Services
source-git-commit: c93dd37d6e196a09c9e7f4b376e421ca5886c7e0
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 0%

---


# Adobe Managed Services

Adobe Commerce은 강력한 기본 기능, 광범위한 사용자 지정 옵션 및 서드파티 통합을 포함하는 전자 상거래 기능을 제공하는 플랫폼입니다.

Adobe Managed Services은 Adobe Commerce on cloud infrastructure Pro 플랜에 호스팅 및 관리되는 애플리케이션 및 인프라를 제공합니다.

## 이점

![Adobe Managed Services의 이점을 보여주는 인포그래픽](../../assets/playbooks/managed-services-benefits.png)

### 구현 옵션 비교

Adobe Managed Services은 온-프레미스 및 관리되지 않는 클라우드 구현에 비해 다음과 같은 주요 이점을 제공합니다.

- **향상된 서비스 수준 대상(SLT)**—표준 Adobe Commerce 지원보다 빠른 응답 시간.
- Adobe Commerce **향상된 SLA(서비스 수준 계약)**—클라우드 인프라 고객이 99.99% 인프라 수준을 능가하는 99.9%의 애플리케이션 수준.
- **지정된 클라우드 전문 지식**—Managed Services은 애플리케이션 및 클라우드 인프라 전문가 역할을 하는 CSE(Designated Customer Success Engineer)를 고객에게 제공합니다. CSE는 고객 및 파트너와 협력하여 다음과 같은 Best Practice와 지침을 제공함으로써 출시 시기를 앞당깁니다.
   - 온보딩 프로세스 안내 및 지원
   - 프로비저닝 및 플랫폼 설정 관리
   - 통합 및 사용자 정의를 위한 아키텍처 원칙에 대한 조언
   - 사고 관리 및 무중단 업무 운영 촉진
   - 계획, 실행 및 모니터링을 통해 이벤트 지원 제공
   - 클라우드 지원 및 전문 지식(사전 최적화, 보고 및 모범 사례)

주요 Managed Services 이점을 보다 자세히 비교하려면 다음 표를 검토하십시오.

| 기능 | Adobe Commerce 온-프레미스 | 클라우드의 Adobe Commerce | Managed Services의 Adobe Commerce |
|---------|---------------------------|-------------------------|-----------------------------------|
| Adobe 엔터프라이즈 소프트웨어 | ✓ | ✓ | ✓ |
| 보안 및 전용 클라우드 인프라 | | ✓ | ✓ |
| 향상된 문제 서비스 수준 타겟 | | P1: 1시간 | P1: 15분 |
| 서지 용량 모니터링 및 응답 | | | ✓ |
| 인프라 보안 | | | ✓ |
| 인프라 수준 99.99% SLA | | | ✓ |
| 애플리케이션 수준 99.9% SLA | | | |
| 지정된 인프라 전문가 리소스(고객 성공 엔지니어) | | | |
| 계획된 이벤트 관리 | | | |
| 맞춤화된 사이트 모니터링 및 맞춤화된 Runbook | | | |
| 업그레이드 및 패치 배포 지원 | | | |
| Go-Live 프로세스 조정 | | | |
| 전담 에스컬레이션 관리 | | | |
| 애플리케이션 모니터링 및 지원 | | | |

엑셀이나 다른 형식으로 내보내기를 원하시는지 알려주세요.

## 역할 및 책임

Adobe은 Managed Services 시스템에서 Adobe Commerce의 프로비저닝, 개발, 스테이징 및 프로덕션과 관련된 일련의 서비스를 제공합니다. 솔루션의 개발 및 배포가 가능한 한 효율적으로 진행되려면 아래에 설명된 대로 고객과 파트너가 자신의 역할을 이해하고 수행하는 것이 중요합니다.

<table>
    <thead>
        <tr>
            <th></th>
            <th>고객</th>
            <th>파트너</th>
            <th>고객 성공 엔지니어</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>프로비저닝</strong></td>
        </tr>
        <tr>
            <td>클라우드 영역 선택</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>인스턴스 프로비저닝</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>내부 네트워크 구성 및 보안</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>Adobe Commerce 애플리케이션 프로비저닝</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>Adobe Commerce Source 코드 액세스</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>CDN 서비스 프로비저닝</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>로컬 개발 환경</td>
            <td>참여자</td>
            <td>소유자</td>
            <td></td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>개발 및 QA</strong></td>
        </tr>
        <tr>
            <td>요구 사항 수집 및 프로젝트 관리</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>애플리케이션 개발</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>애플리케이션 테스트</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>스테이징 및 전환</strong></td>
        </tr>
        <tr>
            <td>개발, 통합 및 스테이징에 코드 배포</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>콘텐츠 배포</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>사용자 수용 테스트 개발</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>사용자 승인 테스트</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>사용자 정의 모니터링 요구 사항</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>고객 제공 SSL 인증서</td>
            <td>소유자</td>
            <td></td>
            <td>참여자</td>
        </tr>
        <tr>
            <td>성능 및 부하 테스트 개발</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>성능 및 로드 테스트</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>사용자 정의 개발 및 QA</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>Runbook 완료</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>참여자</td>
        </tr>
        <tr>
            <td>Runbook 검토</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>시작</strong></td>
        </tr>
        <tr>
            <td>실행 체크리스트</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>라이브 이벤트 회의실</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>프로덕션 코드 배포</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>프로덕션</strong></td>
        </tr>
        <tr>
            <td>프로덕션 인프라 모니터링</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>주요 애플리케이션 모니터링</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>프로덕션 이벤트 응답</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>인프라 및 운영 체제 수준 유지 관리</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>사용자 지정 코드 유지 관리 및 보안 패치</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>Adobe Commerce 제품 업데이트 및 업그레이드에 대한 액세스 제공</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>Adobe Commerce 제품 업데이트 및 업그레이드 적용</td>
            <td>참여자</td>
            <td>소유자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>승인 게시판을 변경하여 프로덕션 배포 승인</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>프로덕션 애플리케이션 관리</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>프로덕션 인프라 조정</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>프로덕션 아키텍처 확장</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>운영 백업 및 복구</td>
            <td></td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>보안 및 규정 준수</strong></td>
        </tr>
        <tr>
            <td>서비스 SOC-2 감사</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>인프라의 PCI 인증</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>맞춤형 애플리케이션의 PCI 인증</td>
            <td>소유자</td>
            <td>참여자</td>
            <td></td>
        </tr>
        <tr>
            <td>핵심 애플리케이션의 보안 감사</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>어드바이저</td>
        </tr>
        <tr>
            <td>맞춤화 및 확장에 대한 보안 감사</td>
            <td>소유자</td>
            <td>참여자</td>
            <td></td>
        </tr>
        <tr>
            <td>고객의 애플리케이션 인스턴스에 대한 침투 테스트</td>
            <td>소유자</td>
            <td>참여자</td>
            <td></td>
        </tr>
        <tr>
            <td>웹 애플리케이션 방화벽 규칙(WAF)</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>침입 탐지 모니터링</td>
            <td></td>
            <td></td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>애플리케이션 및 DB 이벤트 모니터링</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>웹 응용 프로그램 방화벽 이벤트 모니터링</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>사용자 관리 및 SSO 통합</td>
            <td>소유자</td>
            <td>참여자</td>
            <td>참여자</td>
        </tr>
        <tr>
            <td>보안 이벤트 응답</td>
            <td>참여자</td>
            <td>참여자</td>
            <td>소유자</td>
        </tr>
        <tr>
            <td>기업 네트워크 및 리소스에 대한 연결 설정, 보안 및 유지 </td>
            <td>소유자</td>
            <td>어드바이저</td>
            <td>어드바이저</td>
        </tr>
    </tbody>
</table>

## 보안

Managed Services용 Adobe 보안 스택은 자동화 및 일관성을 사용하여 모든 수준에서 보안을 구축하여 사람의 오류를 줄입니다. 개발 및 운영 팀은 서로 다른 스택 수준에서 보안 제어 기능을 자동으로 상속합니다.

Amazon Web Services 및 Microsoft Azure와 같은 플랫폼 파트너는 플랫폼 사용자 정의를 적용할 때 최대 보안 범위를 보장하며 Adobe의 Managed Services 팀은 규정 준수, 로깅, 인증, 스캔 및 모니터링과 같은 핵심 보안 서비스, 서버 보안 및 보안 애플리케이션 구성을 제공합니다. 자세한 내용은 [Adobe Commerce 보안](https://business.adobe.com/products/magento/secure-ecommerce.html)을 참조하십시오.

다음 다이어그램은 Adobe Managed Services 보안 기술 스택을 보여 줍니다.

![Adobe Managed Services 보안 스택을 보여 주는 다이어그램](../../assets/playbooks/managed-services-security-stack.svg)

## 업그레이드 지원

Managed Services 팀은 업그레이드 프로세스를 계획하고 지원하는 데 적극적인 역할을 수행합니다. 고객 성공 엔지니어(CSE)는 프로젝트 관리자 및 개발자(내부 주제 전문가, Adobe 인증 파트너 또는 Adobe Consulting의 전문가)를 포함한 업그레이드 프로젝트 팀과 협력하여 팀이 업그레이드 중에 적절한 계획을 수립하고 모범 사례를 준수할 수 있도록 지원합니다.

Managed Services CSE는 Adobe Commerce 고객과 협력하여 대규모 환경에서 업그레이드를 실행했습니다. CSE는 전문 지식을 활용하여 업그레이드 성공을 극대화하는 동시에 다운타임을 최소화하고 전반적인 위험을 줄이는 데 도움이 될 수 있습니다. 또한 Managed Services CSE는 업그레이드를 위해 전용 스테이징 환경과 작동하므로 업그레이드의 유효성을 검사하는 동안 기존 프로덕션 프로세스에 영향을 주지 않습니다.

Adobe은 Managed Services 시스템의 프로비저닝, 개발, 스테이징 및 프로덕션과 관련된 일련의 서비스를 제공합니다. 다음 표에서는 업그레이드 프로세스에서 각 참여자가 수행하는 역할에 대한 개요를 제공합니다.

<table>
<thead>
  <tr>
    <th>단계</th>
    <th>작업</th>
    <th>고객</th>
    <th>개발 파트너*</th>
    <th>Managed Services</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="3">플랜 업그레이드</td>
    <td>업그레이드 프로젝트 계획 만들기</td>
    <td>소유자</td>
    <td>참여자</td>
    <td>Contributor<br />CSE는 업그레이드 템플릿 및 업그레이드 계획 샘플을 제공하고, 조언 및 모범 사례 팁을 제공합니다.</td>
  </tr>
  <tr>
    <td>필요한 인프라 변경 결정</td>
    <td></td>
    <td>참여자</td>
    <td>Owner<br />CSE는 적절한 크기 조정을 위해 스테이징 및 프로덕션 인프라를 검토합니다.</td>
  </tr>
  <tr>
    <td>업그레이드 복잡성 평가<br />패키지, 문제 및 수정 사항, 서드파티 및 사용자 정의 모듈을 식별하고 문서화합니다.</td>
    <td>참여자</td>
    <td>소유자</td>
    <td>Contributor<br />CSE는 업그레이드 호환성 도구 보고서와 권장 사항을 제공합니다.</td>
  </tr>
  <tr>
    <td rowspan="3">업그레이드 실행</td>
    <td>인프라 서비스 업그레이드<br />[MariaDB, Redis, Open Search, Rabbit MQ] (스테이징 및 프로덕션)</td>
    <td></td>
    <td></td>
    <td>Owner<br />CSE가 인프라 서비스 업그레이드를 조정합니다.<br />CSE에서 업그레이드를 위해 전화 회의 이벤트를 예약합니다.<br />CSE는 프로덕션에서 스테이징으로 데이터 마이그레이션을 지원합니다.</td>
  </tr>
  <tr>
    <td>Commerce 코드 베이스 및 사용자 지정 업데이트, 코드 리컴파일 및 코드 리팩터링</td>
    <td>참여자</td>
    <td>소유자</td>
    <td></td>
  </tr>
  <tr>
    <td>업그레이드 후 확인 및 문제 해결 수행</td>
    <td></td>
    <td>소유자</td>
    <td>Contributor<br />CSE는 업그레이드 후 Runbook을 실행하여 업그레이드와 관련된 문제를 감지하고 수정합니다.</td>
  </tr>
  <tr>
    <td rowspan="3">UAT 및 Launch</td>
    <td>성능 및 보안 테스트 실행</td>
    <td>참여자</td>
    <td>소유자</td>
    <td>Contributor<br />CSE는 응용 프로그램 및 인프라의 성능을 모니터링하여 부하 테스트를 지원합니다.<br />CSE는 Commerce 보안 검색 도구 구성을 지원합니다.</td>
  </tr>
  <tr>
    <td>스테이징에서 사용자 수락 테스트</td>
    <td>소유자</td>
    <td>참여자</td>
    <td>Contributor<br />CSE는 응용 프로그램 및 인프라가 업그레이드 후 올바르게 작동하는지 확인합니다.</td>
  </tr>
  <tr>
    <td>프로덕션에 실행</td>
    <td>참여자</td>
    <td>소유자</td>
    <td>Contributor<br />CSE가 전화 회의 시작 이벤트를 예약합니다.</td>
  </tr>
  <tr>
    <td>출시 후</td>
    <td></td>
    <td>참여자</td>
    <td>참여자</td>
    <td>소유자<br />CSE는 응용 프로그램 및 인프라의 성능을 모니터링합니다.</td>
  </tr>
</tbody>
</table>
