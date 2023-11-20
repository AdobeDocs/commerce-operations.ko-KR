---
title: 공동 책임
description: Adobe Commerce on cloud infrastructure 프로젝트와 관련된 각 당사자의 보안 책임에 대해 알아봅니다.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# 공유 책임 보안 모델

Adobe Commerce on cloud infrastructure는 공유 책임 보안 모델을 사용하는 PaaS(platform-as-a-service) 서비스입니다. Adobe, 판매자, 클라우드 서비스 공급자 및 CDN(Content Delivery Network) 공급자는 각각 클라우드 인프라 애플리케이션 및 판매자별 코드 및 확장에서 Adobe Commerce의 보안을 유지해야 하는 고유한 책임을 집니다.

이러한 접근 방식을 통해 판매자는 운영 책임과 비용을 최소화하면서 비즈니스 요구 사항에 가장 적합한 유연하고 사용자 정의 가능하며 확장 가능한 솔루션을 설계하고 구현할 수 있습니다.

일반적으로 Adobe은 보안 핵심 응용 프로그램 코드 개발 및 유지 관리, 플랫폼 보안 유지 관리, 플랫폼의 SOC 2 및 PCI 규정 준수 및 PCI 준수 기술 구성 요소(예: PHP, Redis)와의 호환성 보장, 핵심 플랫폼과 관련된 보안 문제 대응 등을 담당합니다. Adobe은 발생할 수 있는 문제를 해결하기 위해 클라우드 서비스 공급자 및 CDN 파트너와 협력하는 책임도 집니다.

판매자는 안전한 사용자 지정 코드 및 타사 애플리케이션과의 통합을 유지 관리하고, 안전한 애플리케이션 개발을 보장하며, 판매자의 결제 프로세서에서 요청하는 경우 PCI 인증을 획득하고, 보안 사고에 대응하고 대응할 책임이 있습니다.

## Adobe 책임

Adobe은 클라우드 인프라 환경의 Adobe Commerce 및 클라우드 인프라 솔루션 코드의 핵심 Adobe Commerce의 보안 및 가용성을 담당합니다. 또한 Adobe은 다음을 포함하여 클라우드 인프라 솔루션에서 Adobe Commerce의 보안을 유지하는 데 필요한 활동 및 메커니즘을 담당합니다.

- 클라우드 데이터 스토리지 및 검색 기능과 같은 클라우드 인프라에서 Adobe Commerce이 지원하는 애플리케이션에 서버 수준 보안 및 패치 적용
- 클라우드 인프라 코드에서 핵심 Adobe Commerce 침투 테스트 및 스캔 수행
- 공용 클라우드 서비스 공급자의 IAM(Identity and Access Management) 솔루션 및 권한 관리(PCI 규정 준수 요구 사항)에 대한 반기별 검토/감사 수행
- Adobe 직원 및 계약자를 포함한 승인된 사용자에 대한 반기별 검토/감사 실시(PCI 규정 준수 요구 사항)
- 백업 및 복원 기능에 대한 연간 테스트 및 문서화 수행
- 서버 및 경계 방화벽 구성
- 클라우드 인프라 저장소에서 Adobe Commerce 연결 및 구성
- Adobe의 책임 범위 내에 있는 영역에 대한 재해 복구(DR) 계획 정의, 테스트, 구현 및 문서화
- 글로벌 플랫폼 웹 애플리케이션 방화벽(WAF) 규칙 정의
- 운영 체제(OS) 강화
- 클라우드 인프라에서 Adobe Commerce과 CDN(Content Distribution Network) 및 APM(Application Performance Management) 솔루션 통합 구현 및 유지 관리
- 클라우드 인프라 코드에서 핵심 Adobe Commerce에 대한 정기 보안 및 기타 업데이트 발행(패치 적용은 판매자의 책임)
- 판매자 지원 및 지원 액세스 제어 관리(예: Zendesk)
- 클라우드 인프라 플랫폼 인프라의 Adobe Commerce과 관련된 보안 사고 모니터링, 로깅 및 수정
- 클라우드 인프라 판매자의 Adobe Commerce 플랫폼 운영 모니터링 및 연중무휴 지원 제공
- 프로덕션 및 스테이징 환경 프로비저닝
- 플랫폼 운영 및 인프라에 대한 잠재적인 보안 위협 평가
- 머천트와의 SLA(서비스 수준 계약)에 명시된 대로 컴퓨팅, 스토리지, 그리드 및 기타 리소스 확장
- DNS 설정(클라우드 인프라 플랫폼 인프라의 Adobe Commerce만 해당)
- 보안 취약점에 대한 플랫폼 테스트

Adobe은 Adobe Commerce on cloud infrastructure 솔루션 운영에 사용되는 인프라 및 서비스에 대한 PCI 인증을 유지 관리하는 반면, 판매자는 사용자 정의 코드, 시스템 및 네트워크 프로세스 및 조직의 준수에 대한 책임을 집니다.

또한 Adobe은 해당 SLA에서 합의한 대로 판매자의 인프라를 사용할 수 있도록 보장합니다.

## 판매자 책임

판매자는 클라우드 인프라 솔루션에서 맞춤화된 특정 Adobe Commerce 인스턴스에 대한 보안 모범 사례 및 를 담당합니다.

- 저장소에 클라우드 인프라 구성 파일에 필요한 Adobe Commerce 추가
- Adobe 출시 후 바로 맞춤형 Adobe Commerce on cloud infrastructure 솔루션에 보안 및 기타 패치 적용
- 공급업체에서 출시한 직후 모든 사용자 정의 확장 및 코드에 보안 및 기타 패치 적용
- 사용자 정의 Varnish VCL 파일 생성, 배포 및 테스트
- 모든 사용자 지정 확장 및 코드를 포함하여 클라우드 인프라 솔루션에 대한 맞춤형 Adobe Commerce의 디자인, 테마 설정, 설치, 통합 및 보안
- 클라우드 인프라 구성, 애플리케이션 및 플랫폼에서 판매자의 Adobe Commerce 인스턴스에 대한 사용자 액세스 권한 부여 및 취소
- 클라우드 인프라 플랫폼의 Adobe Commerce에 구축된 판매자 내부 네트워크, 서버, 인프라 및 모든 맞춤형 애플리케이션과 관련된 보안 문제 처리
- 클라우드 인프라에 Adobe Commerce 설치 명령줄 통합(CLI) 도구
- PCI-DSS 지침에 정의된 대로 사용자 정의 애플리케이션 및 기타 내부 프로세스에 대한 PCI 규정 준수 수준 유지

  >[!NOTE]
  >
  >판매자의 PCI 규정 준수는 클라우드 인프라 및 클라우드 호스팅 제공업체에서 Adobe Commerce의 PCI 인증을 기반으로 하여 검토해야 하는 영역을 최소화합니다.

- PCI ASV 스캔 실행 및 클라우드 인프라 코드 및 플랫폼에서 핵심 Adobe Commerce의 문제 해결
- 침투 테스트, 취약성 검사 및 로그를 포함하여 잠재적인 보안 위협을 드러낼 수 있는 모든 애플리케이션 작업 모니터링
- 클라우드 인프라 솔루션 및 사용자 계정에 대한 판매자의 Adobe Commerce 관련 포렌식, 수정 및 보고를 포함한 보안 사고 모니터링 및 대응
- DNS 공급자 확보 및 판매자별 DNS 레코드 구성 및 유지 관리
- 사용자 지정된 응용 프로그램에서 성능 테스트 실행
- 플랫폼 계정, 인스턴스 액세스 및 애플리케이션에 대한 액세스 보호
- 사용자 정의 애플리케이션 테스트 및 QA
- 판매자가 클라우드 인프라 애플리케이션에서 Adobe Commerce에 연결하는 모든 시스템 또는 네트워크의 보안 유지

## 클라우드 서비스 공급자 책임

Adobe은 잘 구축된 클라우드 서비스 제공업체를 통해 클라우드 인프라에서 Adobe Commerce용 클라우드 서버 인프라를 호스팅합니다. 이러한 공급업체는 방화벽 시스템 및 침입 탐지 시스템(ID)을 통해 라우팅, 스위칭 및 경계 네트워크 보안을 포함한 네트워크 보안을 담당합니다. 클라우드 서비스 제공업체는 Adobe Commerce on cloud infrastructure 솔루션을 호스팅하는 데이터 센터의 물리적 보안과 데이터 센터의 환경 보안을 책임집니다.

클라우드 서비스 공급자는 또한 다음 사항에 대한 책임이 있습니다.

- 클라우드 서비스에 대한 PCI DSS, SOC 2 및 ISO 27001 인증 유지
- 하이퍼바이저 보호
- 물리적 액세스와 네트워크 액세스를 모두 포함한 데이터 센터 보안

## CDN 공급자 책임

Adobe Commerce on cloud infrastructure 솔루션은 CDN 공급자를 사용하여 페이지 로드 시간을 단축하고, 콘텐츠를 캐시하며, 오래된 콘텐츠를 즉시 제거합니다. 이러한 공급자는 CDN과 직접 관련되거나 영향을 주는 보안 문제와 CDN WAF 규칙 정의 및 유지 관리에도 책임이 있습니다.

## 보안 권한 차트

다음 차트는 RACI 모델(R — 책임, A — 책임, C — 상담, I — 정보)을 사용하여 클라우드 인프라의 Adobe Commerce 공유 책임 모델과 관련된 에코시스템의 보안 책임에 있는 각 당사자를 시각적으로 표시합니다.

<table>
<thead>
  <tr>
    <th>작업</th>
    <th>Adobe</th>
    <th>판매자</th>
    <th>클라우드 서비스 공급자</th>
    <th>CDN 공급자</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>클라우드 인프라 패치에 Adobe Commerce 적용</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>지원 서비스에 패치 적용<br>(예: Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>원본 WAF 규칙 정의</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF 규칙 정의</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>플랫폼 WAF 규칙 배포</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF 규칙 배포</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>클라우드 인프라 코드에서 Adobe Commerce의 핵심 버그 수정</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라 패치에 대한 Adobe Commerce 출시</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>크기 조절(컴퓨팅 및 스토리지)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>크기 조절(PaaS/grid)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>repo.magento.com을 포함한 소스 코드에 대한 액세스 보장</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라 CLI 도구에 Adobe Commerce 설치</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>저장소에 클라우드 인프라 구성 파일의 Adobe Commerce 추가</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>판매자를 위한 프로젝트 만들기(온보딩 UI)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라에서 Adobe Commerce에 저장소/인스턴스 연결</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>소스 리포지토리 구성<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>릴리스 관리자용 사용자 만들기(온보딩 UI)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>프로덕션에 코드 배포</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>스테이징에 코드 배포</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>외부 애플리케이션 및 확장 통합</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>확장 설치</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라에서 Adobe Commerce 맞춤화</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라에서 맞춤화된 Adobe Commerce의 성능 테스트</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>사용자 지정된 애플리케이션 테스트</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>사용자 정의 응용 프로그램의 테마 설정 및 디자인</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>사용자 정의 Varnish VCL 생성, 배포 및 테스트</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS 구성(플랫폼 인프라만)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN 확장 개발 및 버그 수정</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>CDN 온보딩</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN 지원<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APM/인프라 구성</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM/인프라 설치</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM/인프라 지원</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Nginx 구성<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS 공급자 가져오기(Pro만 해당)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OS 강화</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>프로덕션 및 스테이징 환경 프로비저닝</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라의 Adobe Commerce Zendesk 액세스</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>판매자 보안 문제 해결</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>클라우드 인프라 보안 문제에 대한 Adobe Commerce 해결</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN 보안 문제 해결</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>APM 보안 문제 해결</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>보안 조사(소프트웨어) Adobe 지원</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>보안 조사(스캔/감사) Adobe 지원</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PCI ASV 스캔 수행</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라 PCI 스캔에서 Adobe Commerce 수정<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PaaS PCI 스캔 수정</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OS 및 플랫폼 비밀 관리</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라 암호화 키에서 Adobe Commerce 관리</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라 인스턴스에서 사용자 지정된 Adobe Commerce 검색</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>보안 로그 모니터링</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>클라우드 인프라에서 Adobe Commerce에 대한 IAM 및 권한 관리</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>지원 액세스 제어 관리(텔레포트)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>판매자 지원 및 액세스 제어</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe DR 계획 및 백업 및 복원에 대한 연간 테스트 및 문서</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>연간 재해 복구 계획 테스트 및 문서화</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> 클라우드 인프라 저장소의 Adobe Commerce이 주 리포지토리로 사용되는 경우에만 해당합니다. 다른 외부 리포지토리를 사용하는 것은 판매자의 유일한 책임입니다.</p>
      <p><sup><strong>2</strong></sup> Adobe은 CDN 공급자 문제에 대한 레벨 1 지원을 제공합니다.</p>
      <p><sup><strong>3</strong></sup> 일부 Ngnix 컨트롤은 해당 애플리케이션에 대해 판매자가 구성하며, 이는 판매자의 책임입니다.</p>
      <p><sup><strong>4</strong></sup> PCI의 경우 침투 테스트 요구 사항이 Adobe과 판매자 간에 공유됩니다.</p>
    </td>
  </tr>
</tfoot>
</table>
