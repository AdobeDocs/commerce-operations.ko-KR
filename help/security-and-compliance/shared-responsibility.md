---
title: 공동 책임 보안 및 운영 모델
description: Adobe Commerce on cloud infrastructure 프로젝트와 관련된 각 당사자의 보안 책임에 대해 알아봅니다.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: aac78fc95b86951f352a636eef33e0b79b22a183
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 0%

---

# 공동 책임 보안 및 운영 모델

Adobe Commerce on cloud infrastructure는 공유 책임 보안 및 운영 모델을 사용하는 PaaS(platform-as-a-service) 서비스입니다. 이러한 책임은 Adobe, 판매자, 클라우드 서비스 공급자 및 CDN(Content Delivery Network) 공급자 간에 공유됩니다. 각 당사자는 Adobe Commerce 애플리케이션 및 클라우드 인프라에 배포된 판매자별 코드 및 확장에 대한 보안 및 운영에 대해 고유한 책임을 집니다.

이 공유 모델을 통해 상인은 비즈니스 요구 사항을 충족하고 운영 책임과 비용을 최소화하면서 유연하고 사용자 정의가 가능하며 확장 가능한 솔루션을 설계 및 구현할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

일반적으로 Adobe은 다음 사항을 담당합니다.

- 보안 핵심 애플리케이션 코드 개발 및 유지 관리
- 플랫폼 보안 유지
- 플랫폼이 SOC 2 및 PCI를 준수하고 PCI 호환 기술 구성 요소(예: PHP, Redis)와 호환되는지 확인
- 핵심 플랫폼과 관련된 보안 문제에 대응
- 클라우드 서비스 공급자 및 CDN 파트너와 협력하여 발생하는 모든 문제 해결

상인은 다음 사항을 담당합니다.

- 사용자 지정 코드 및 타사 애플리케이션과의 통합을 위한 보안 유지
- 안전한 애플리케이션 개발 보장
- 판매자의 결제 프로세서에서 요청하는 경우 PCI 인증 획득
- 보안 사고 대응 및 대응

## Adobe 책임

Adobe은 클라우드 인프라 환경 및 핵심 솔루션 코드의 Adobe Commerce에 대한 보안 및 가용성을 담당합니다. 또한 Adobe은 다음을 포함하여 클라우드 인프라 솔루션에서 Adobe Commerce의 보안을 유지하는 데 필요한 활동 및 메커니즘을 담당합니다.

- 클라우드 데이터 스토리지 및 검색 기능과 같은 클라우드 인프라에서 Adobe Commerce이 지원하는 애플리케이션에 서버 수준 보안 및 패치 적용
- 클라우드 인프라 코드에서 핵심 Adobe Commerce 침투 테스트 및 스캔 수행
- 공용 클라우드 서비스 공급자의 IAM(Identity and Access Management) 솔루션 및 권한 관리(PCI 규정 준수 요구 사항)에 대한 반기별 검토 및 감사 수행
- Adobe 직원 및 계약자를 포함한 승인된 사용자에 대한 반기별 검토 및 감사 실시(PCI 규정 준수 요구 사항)
- 백업 및 복원 기능에 대한 연간 테스트 및 문서화 수행
- 서버 및 경계 방화벽 구성
- 클라우드 인프라 저장소에서 Adobe Commerce 연결 및 구성
- Adobe의 책임 범위에 속하는 영역에 대한 재해 복구(DR) 계획 정의, 테스트, 구현 및 문서화
- 글로벌 플랫폼 웹 애플리케이션 방화벽(WAF) 규칙 정의
- 운영 체제(OS) 강화
- 클라우드 인프라에서 Adobe Commerce과 CDN(Content Distribution Network) 및 APM(Application Performance Management) 솔루션 통합 구현 및 유지 관리
- 클라우드 인프라 코드에서 핵심 Adobe Commerce에 대한 정기 보안 및 기타 업데이트 발행(패치 적용은 판매자의 책임)
- 판매자 지원 및 지원 액세스 제어 관리(예: Zendesk)
- 클라우드 인프라 플랫폼 인프라의 Adobe Commerce과 관련된 보안 사고 모니터링, 로깅 및 수정
- 클라우드 인프라 판매자의 Adobe Commerce 플랫폼 운영 모니터링 및 연중무휴 지원 제공
- 프로덕션 및 스테이징 환경 프로비저닝
- 플랫폼 운영 및 인프라에 대한 잠재적인 보안 위협 평가
- 머천트와의 SLA(SLA)에 명시된 대로 컴퓨팅, 스토리지, 그리드 및 기타 리소스 확장
- DNS 설정(클라우드 인프라 플랫폼 인프라의 Adobe Commerce만 해당)
- 보안 취약점에 대한 플랫폼 테스트

Adobe은 Adobe Commerce 솔루션에 사용되는 인프라 및 서비스에 대한 PCI 인증을 유지 관리합니다.  판매자는 사용자 정의 코드, 시스템 및 네트워크 프로세스, 조직의 규정 준수에 대한 책임을 집니다.

또한 Adobe은 해당 SLA에서 합의한 대로 판매자의 인프라를 사용할 수 있도록 보장합니다.

## 판매자 책임

판매자는 클라우드 인프라 솔루션에서 맞춤화된 특정 Adobe Commerce 인스턴스에 대한 다음 보안 모범 사례를 책임집니다.

- 저장소에 클라우드 인프라 구성 파일에 필요한 Adobe Commerce 추가
- Adobe에서 출시한 직후 보안 및 기타 패치를 Adobe Commerce on cloud infrastructure 솔루션에 적용
- 공급업체에서 출시한 직후 모든 사용자 정의 확장 및 코드에 보안 및 기타 패치 적용
- 사용자 정의 Varnish VCL 파일 생성, 배포 및 테스트
- 모든 사용자 지정 확장 및 코드를 포함하여 클라우드 인프라 솔루션에 대한 맞춤형 Adobe Commerce의 디자인, 테마 설정, 설치, 통합 및 보안
- 클라우드 인프라 구성, 애플리케이션 및 플랫폼에서 판매자의 Adobe Commerce 인스턴스에 대한 사용자 액세스 권한 부여 및 취소
- 클라우드 인프라 플랫폼의 Adobe Commerce에 구축된 판매자 내부 네트워크, 서버, 인프라 및 모든 맞춤형 애플리케이션과 관련된 보안 문제 처리
- 클라우드 인프라에 Adobe Commerce 설치 명령줄 통합(CLI) 도구
- PCI-DSS 지침에 정의된 대로 사용자 정의 애플리케이션 및 기타 내부 프로세스에 대한 PCI 규정 준수 수준 유지

  >[!NOTE]
  >
  >검토해야 하는 영역을 최소화하기 위해 판매자를 위한 PCI 규정 준수는 Adobe Commerce 및 클라우드 호스팅 공급자의 PCI 인증을 기반으로 구축됩니다.

- PCI ASV 스캔 실행 및 클라우드 인프라 코드 및 플랫폼에서 핵심 Adobe Commerce의 문제 해결
- 침투 테스트, 취약성 검사 및 로그를 포함하여 잠재적인 보안 위협을 드러낼 수 있는 모든 애플리케이션 작업 모니터링
- 클라우드 인프라 솔루션 및 사용자 계정에 대한 판매자의 Adobe Commerce 관련 포렌식, 수정 및 보고를 포함한 보안 사고 모니터링 및 대응
- DNS 공급자 확보 및 판매자별 DNS 레코드 구성 및 유지 관리
- 사용자 지정된 응용 프로그램에서 성능 테스트 실행
- 플랫폼 계정, 인스턴스 액세스 및 애플리케이션에 대한 액세스 보호
- 사용자 정의 애플리케이션 테스트 및 QA
- 판매자가 클라우드 인프라 애플리케이션에서 Adobe Commerce에 연결하는 모든 시스템 또는 네트워크의 보안 유지

## Cloud Service 공급자 책임

Adobe은 잘 구축된 클라우드 서비스 제공업체를 통해 클라우드 인프라에서 Adobe Commerce용 클라우드 서버 인프라를 호스팅합니다. 이러한 공급업체는 방화벽 시스템 및 침입 탐지 시스템(ID)을 통해 라우팅, 스위칭 및 경계 네트워크 보안을 포함한 네트워크 보안을 담당합니다. 클라우드 서비스 제공업체는 Adobe Commerce on cloud infrastructure 솔루션을 호스팅하는 데이터 센터의 물리적 보안과 데이터 센터의 환경 보안을 책임집니다.

클라우드 서비스 공급자는 또한 다음 사항에 대한 책임이 있습니다.

- 클라우드 서비스에 대한 PCI DSS, SOC 2 및 ISO 27001 인증 유지
- 하이퍼바이저 보호
- 물리적 액세스와 네트워크 액세스를 모두 포함한 데이터 센터 보안

## CDN 공급자 책임

Adobe Commerce on cloud infrastructure 솔루션은 CDN 공급자를 사용하여 페이지 로드 시간을 단축하고, 콘텐츠를 캐시하며, 오래된 콘텐츠를 즉시 제거합니다. 이러한 공급자는 CDN과 직접 관련되거나 영향을 주는 보안 문제와 CDN WAF 규칙 정의 및 유지 관리에도 책임이 있습니다.

## 보안 권한 요약

>[!BEGINSHADEBOX]

다음 요약 테이블은 RACI 모델을 사용하여 Adobe, 판매자 및 클라우드 서비스 공급자 간에 공유된 보안 책임을 보여 줍니다.

**R** — 담당
**A** — 책임 있음
**C** — 참조됨
**I** — 알림

>[!ENDSHADEBOX]

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
    <td>지원 서비스 <br>에 패치 적용(예: Nginx 또는 MySQL)</td>
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
    <td>Platform WAF 규칙 배포</td>
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
    <td>크기 조절(PaaS 및 그리드)</td>
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
    <td>클라우드 인프라에서 Adobe Commerce에 저장소 연결</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>원본 리포지토리 구성<sup>1</sup></td>
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
    <td>CDN<sup>2</sup> 지원</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APM 및 인프라 애플리케이션 구성</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM 및 인프라 애플리케이션 설치</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM 및 인프라 애플리케이션 지원</td>
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
    <td>DNS 공급자 얻기(Pro만 해당)</td>
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
    <td>Adobe의 보안 연구 지원(소프트웨어)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe의 보안 조사 지원(스캔/감사)</td>
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
    <td>Adobe DR 계획 및 백업 및 복원의 연간 테스트 및 문서화</td>
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
      <p><sup><strong>1</strong></sup> 클라우드 인프라 저장소의 Adobe Commerce이 주 리포지토리로 사용되는 경우에만 해당됩니다. 다른 외부 리포지토리를 사용하는 것은 판매자의 유일한 책임입니다.</p>
      <p><sup><strong>2</strong></sup> Adobe은 CDN 공급자 문제에 대한 레벨 1 지원을 제공합니다.</p>
      <p><sup><strong>3</strong></sup> 판매자는 응용 프로그램에 대해 구성하는 모든 Ngnix 컨트롤을 담당합니다.</p>
      <p><sup><strong>4</strong></sup> PCI의 경우 침투 테스트 요구 사항이 Adobe과 판매자 간에 공유됩니다.</p>
    </td>
  </tr>
</tfoot>
</table>

## 운영 책임 요약

>[!BEGINSHADEBOX]

다음 요약 표는 클라우드 인프라에서 Adobe을 개발, 배포, 유지 관리 및 보호할 때 Adobe Commerce 및 판매자에 대한 운영 책임을 명확하게 설명합니다.

>[!ENDSHADEBOX]

### 코딩 및 개발

#### 코어 Adobe Commerce 코드

|     | Adobe | 판매자 |
| --- | --- | --- |
| Adobe Commerce 코어에 업데이트 및 패치 게시 | R |     |
| 파일 시스템 가용성 및 패치 | R |  |
| ECE-Tools에 업데이트 및 패치 게시 | R |     |
| 핵심 Adobe Commerce 애플리케이션 품질 | R |     |

{style="table-layout:auto"}

#### 코드 저장소

|     | Adobe | 판매자 |
| --- | --- | --- |
| repo.magento.com 가용성 | R |     |
| Cloud Git 서버에서 Adobe Commerce 사용 가능 | R |     |
| 기타 판매자가 선택한 코드 저장소(GitHub, Bitbucket, 호스팅된 Git 서버) |     | R |

{style="table-layout:auto"}

#### 클라우드 도커

|     | Adobe | 판매자 |
| --- | --- | --- |
| Cloud Docker 컨테이너를 다운로드할 수 있도록 설정 | R |   |
| Cloud Docker 배포 및 설정(선택 사항) |     | R |
| 기타 모든 로컬 개발 설정 |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | 판매자 |
| --- | --- | --- |
| ECE 도구의 지속적인 품질 및 업데이트 | R |   |
| 최신 ECE Tools 버전 설치 |     | R |

{style="table-layout:auto"}

#### 사용자 정의

|  | Adobe | 판매자 |
| --- | --- | --- |
| 사용자 지정 Adobe Commerce 모듈 및 코드 |     | R |
| 확장 |     | R |
| 사용자 정의 통합 |     | R |

{style="table-layout:auto"}

#### 배포

|     | Adobe | 판매자 |
| --- | --- | --- |
| 코드를 빌드하고 배포할 인프라 가용성 | R |   |
| 인프라 빌드 및 배포 구성 파이프라인의 지속적인 품질 | R |   |
| 빌드 및 정적 콘텐츠 배포 구성 |     | R |
| 배포 거버넌스 프로세스 구축 및 실행: 기준 및 변경 관리 |     | R |
| 스테이징 환경에 배포 |     | R |
| 프로덕션 환경에 배포 |     | R |
| 프로덕션 롤백 |     | R |

{style="table-layout:auto"}

#### 환경 동기화

판매자는 환경 간에 데이터를 동기화할 책임이 있습니다.

#### 패치 중

|     | Adobe | 판매자 |
| --- | --- | --- |
| ECE-Tools에 업데이트 및 패치 설치 |     | R |
| Adobe Commerce 코어에 업데이트 및 패치 설치 |     | R |

#### 웹 사이트 가용성

|  | Adobe | 판매자 |
| --- | --- | --- |
| 사용자 지정된 Adobe Commerce 애플리케이션 및 관련 웹 사이트 |     | R |

#### 성능

|     | Adobe | 판매자 |
| --- | --- | --- |
| 핵심 애플리케이션 튜닝 및 최적화 | R |   |
| 사용자 지정 코드 조정 및 최적화 |     | R |
| 사용자 지정 Adobe Commerce 코드 |     | R |
| 로드 테스트 |     | R |
| 성능 테스트 |     | R |

{style="table-layout:auto"}


#### 로그 및 모니터링

|     | Adobe | 판매자 |
| --- | --- | --- |
| 회전 로그 | R |   |
| 사용자 지정 Adobe Commerce 애플리케이션 | | R |
| New Relic 서비스 가용성:<br>APM 응용 프로그램 및 에이전트 통합, 인프라 응용 프로그램,<br>로깅 및 통합 | R |   |
| New Relic 경고 설정 |     | R |
| PaaS 서버에 New Relic 에이전트 배포 | R |  |

{style="table-layout:auto"}

#### 디버깅 및 문제 격리

|     | Adobe | 판매자 |
| --- | --- | --- |
| 디버깅 및 문제 격리 | R | R |
| 디버깅 및 문제 격리 프로세스를 적시에 지원 |     | R |

{style="table-layout:auto"}

### 애플리케이션 및 서비스 구성

#### Commerce 애플리케이션

|     | Adobe | 판매자 |
| --- | --- | --- |
| 애플리케이션 구성 |     | R |
| Adobe Commerce 애플리케이션에 도메인 추가(기본 URL) |     | R |
| 배포된 Adobe Commerce 버전에서 지원하는 서비스 버전을 사용하도록 PaaS 구성<br><br>예를 들어 다른 Commerce 버전이 PHP, Redis 등의 특정 버전과 호환됩니다. |     | R |

{style="table-layout:auto"}

#### cron 작업으로 작업 예약

|     | Adobe | 판매자 |
| --- | --- | --- |
| 기본 cron 작업 가용성 | R | |
| 사용자 정의 크론 작업의 지속적인 품질 |  | R |

{style="table-layout:auto"}

#### 메시지 대기열 프레임워크용 메시지 브로커

|     | Adobe | 판매자 |
| --- | --- | --- |
| RabbitMQ 서비스 가용성 | R |   |
| 기본 RabbitMQ 설정 구성 | R |   |
| RabbitMQ의 지속적인 품질 및 패치 | R |   |
| 설치된 Adobe Commerce 버전과 호환되는 RabbitMQ 버전을 설치하려면 서비스 요청을 제출하십시오. |   | R |

{style="table-layout:auto"}

#### PHP 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| PHP의 가용성 | R |   |
| 기본 PHP 설정 구성 | R |     |
| 사용자 지정 PHP 설정 구성 |     | R |
| 설치된 Adobe Commerce 버전과 호환되는 PHP 버전을 정렬하기 위한 YAML 파일 구성 |    | R |

{style="table-layout:auto"}

#### 데이터베이스 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| Galera 및 MariaDB 서비스 가용성 | R | |
| 기본 데이터베이스 설정 <br><br>의 유지 관리 진행 중(핵심 테이블 인덱싱 및 최적화, 기본 시스템 관리자 설정 최적화) | R |   |
| 판매자 데이터 및 수정된 설정의 지속적인 유지 관리<br><br>(정규화된 테이블과 플랫 테이블 구성, 사용자 지정 및 타사 테이블 인덱싱 및 최적화, 데이터 보관 또는 제거, 시스템 관리 설정 구성) |     | R |
| Galera 및 MySQL의 구성 | R |   |
| Galera 및 MariaDB의 지속적인 품질 및 패치 | R |   |
| 지속적인 인프라 최적화 | R |   |
| 느린 쿼리 식별 및 수정 |     | R |
| 설치된 Adobe Commerce 버전과 호환되는 MariaDB 버전을 설치하려면 서비스 요청을 제출하십시오 |     | R |
| 판매자별 데이터 보존 정책 설정 및 유지 관리(Adobe의 데이터 보존 정책은 판매자 계약에 정의됨) |     | R |

{style="table-layout:auto"}

#### CDN 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| CDN 가용성 및 품질 | R |   |
| Fastly 서비스 구성(확장/API를 통해) |     | R |
| Fastly 확장 품질 | R |   |
| Fastly 통합 VCL 스니펫(Fastly 확장과 함께 번들로 제공) 품질 | R |   |
| 페이지 캐시 최적화 |     | R |
| 서비스, CDN 및 인프라에 도메인 추가 | R |   |
| 사용자 지정 VCL 코드 조각 |     | R |
| WAF 및 WAF 규칙 | R |   |

{style="table-layout:auto"}

#### 캐시 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| Redis 서비스 가용성 | R |   |
| 기본 Redis 설정 구성 | R |   |
| Redis의 지속적인 품질 및 패치 | R |   |
| 설치된 Adobe Commerce 버전과 호환되는 Redis 버전을 설치하려면 서비스 요청을 제출하십시오. |     | R |

{style="table-layout:auto"}

#### 검색 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| Elasticsearch 또는 OpenSearch 가용성 | R |   |
| 기본 Elasticsearch 또는 OpenSearch 설정 구성 | R |   |
| 설치된 Adobe Commerce 버전과 호환되는 Elasticsearch 또는 OpenSearch 버전을 설치하려면 서비스 요청을 제출하십시오. |  | R |

{style="table-layout:auto"}

#### 이메일 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| SendGrid 이메일 서비스 및 통합 가용성 | R |   |
| 판매자의 SendGrid 사용 제한 모니터링 | R |   |
| 판매자는 보내는 트랜잭션 전자 메일에 대해서만 서비스를 사용할 책임이 있습니다<br>이 서비스는 마케팅 전자 메일 전송을 지원하지 않습니다. |     | R |
| 선택적 서드파티 이메일 서비스 구성 |     | R |

{style="table-layout:auto"}

#### 타사 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| 타사 서비스의 가용성 및 품질 |     | R |

{style="table-layout:auto"}

### Commerce 서비스 확장

#### 고급 보고 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| Advanced Reporting Service 가용성 | R |   |
| 고급 보고 구성은 고급 보고 약관을 준수합니다 |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | 판매자 |
| --- | --- | --- |
| Adobe Commerce Business Intelligence 서비스 가용성 | R |   |
| MBI 데이터 동기화 프로세스 | R |   |
| MBI 동기화 문제 감지 | R |   |
| Adobe Commerce Cloud Pro, Starter, On-Premise 또는 비 Adobe Commerce에 MBI 데이터 동기화 구성<br>(데이터 임계값을 통해 API, 데이터 품질 및 형식 지정, 판매자 네트워크,<br>Adobe Commerce Cloud DB 내부 및 외부 모두 연결) |     | R |
| Adobe Commerce Cloud Pro<br>에 대한 MBI 데이터 동기화 구성(Adobe Commerce Cloud 데이터베이스 구성) | R |   |

{style="table-layout:auto"}

>
>가맹점은 가장 최신 버전의 라이브 검색, 제품 추천 및 결제 서비스를 사용하여 가장 높은 안정성, 기능 및 지원 자격을 보장해야 합니다.
>Adobe은 오래된 버전을 지원하지 않으며, 업그레이드를 통해 최신 개선 사항 및 버그 수정 사항을 활용할 수 있습니다.
>지원되는 버전에 대한 자세한 내용은 [Commerce 서비스용 제품 가용성 매트릭스](https://experienceleague.adobe.com/ko/docs/commerce-operations/release/product-availability#commerce-services)를 참조하십시오.

#### 제품 추천

|     | Adobe | 판매자 |
| --- | --- | --- |
| 제품 추천 서비스 가용성 | R |   |
| 제품 추천 모듈 업그레이드 |   | R |

{style="table-layout:auto"}

#### 라이브 검색

|     | Adobe | 판매자 |
| --- | --- | --- |
| Live Search 서비스 가용성 | R |   |
| 라이브 검색 모듈 업그레이드 |   | R |

{style="table-layout:auto"}

#### Quality of storefront events(데이터 수집) - 제품 추천 및 라이브 검색 출력 강화

|     | Adobe | 판매자 |
| --- | --- | --- |
| 코어 테마(Luma) | R |   |
| 사용자 정의 테마 |  | R |
| 핵심 PWA 구현 | R |   |
| 사용자 지정 PWA 구현 |  | R |
| 핵심 AEM EDS 구현(Commerce Boilerplate) | R |   |
| 사용자 지정 AEM EDS 구현 |  | R |
| 기타 모든 사용자 지정 Storefront 구현 |  | R |

{style="table-layout:auto"}

#### 결제 서비스

|     | Adobe | 판매자 |
| --- | --- | --- |
| 결제 서비스 가용성 | R |   |
| 결제 모듈 업그레이드 |   | R |

{style="table-layout:auto"}

### 네트워크 서비스

#### 이미지 최적화

|     | Adobe | 판매자 |
| --- | --- | --- |
| 이미지 최적화의 가용성 및 품질 | R |  |
| 이미지 최적화 구성 |     | R |

{style="table-layout:auto"}

#### SSL 인증서

|     | Adobe | 판매자 |
| --- | --- | --- |
| SSL 전용 인증서 - 만료 | R |  |
| SSL 인증서 프로비저닝 | R |  |
| EV/특정 SSL 인증서 구매 및 유지 관리(제공된 기본값 제외) 및 Adobe 제공 |     | R |

{style="table-layout:auto"}

#### 웹 애플리케이션 방화벽(WAF)

|     | Adobe | 판매자 |
| --- | --- | --- |
| WAF의 가용성 및 구성 | R |  |
| WAF 규칙 긍정 오류 해결 | R | |
| WAF 규칙 긍정 오류 보고 |     | R |
| WAF 규칙 조정(지원되지 않음) |     |     |
| WAF/CDN 로그 |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | 판매자 |
| --- | --- | --- |
| 사전 예방적 IP 차단 |     | R |
| 보트 보호 |     | R |
| DDOS 감지 - 레이어 3-4 | R |   |
| DDOS 감지 - 레이어 7 |     | R |
| DDOS 응답 | R |   |

{style="table-layout:auto"}

#### 비공개 링크

|     | Adobe | 판매자 |
| --- | --- | --- |
| Adobe 소유 VPC을 사용한 PrivateLink 연결 구성 및 유지 관리(사용 시) | R |   |
| 판매자 소유 VPC을 사용한 PrivateLink 연결 구성 및 유지 관리 |     | R |
| SSH 사용 가능(비공개 링크 아님) | R |   |
| Adobe Commerce Cloud Service 끝점에 대한 PrivateLink 인바운드 구성 | R |   |
| Adobe Commerce Cloud Service 끝점에 대한 PrivateLink 인바운드 수락 |     | R |
| 판매자의 VPC 서비스 끝점에 대한 PrivateLink 인바운드 구성 |     | R |
| 판매자의 VPC 서비스 끝점에 대한 PrivateLink 인바운드 수락 | R |   |
| PrivateLink 통합 구성(엔드포인트-계정) |     | R |
| PrivateLink 끝점<br><br>에 대한 판매자 소유 VPC 구성(VPN 연결 포함) |     | R |

{style="table-layout:auto"}

### 시스템 및 인프라

#### 앱 서버

|     | Adobe | 판매자 |
| --- | --- | --- |
| Nginx 가용성 | R |   |
| Nginx 구성 | R |   |
| Nginx의 지속적인 품질 및 패치 | R |   |

{style="table-layout:auto"}

#### 운영 체제

|     | Adobe | 판매자 |
| --- | --- | --- |
| 운영 체제 가용성 | R |   |
| 운영 체제의 지속적인 품질 및 패치 | R |   |

{style="table-layout:auto"}

#### 백업, 고가용성 및 페일오버

|     | Adobe | 판매자 |
| --- | --- | --- |
| 스냅샷 및 백업 프로세스 가용성 | R |   |
| Cloud Pro 스테이징 및 프로덕션 환경에 대한 백업 예약 | R |   |
| Cloud Starter 및 Pro 통합 환경에 대한 백업 예약 |     | R |
| HA/페일오버 가용성 | R |   |

{style="table-layout:auto"}

#### 클라우드 서버 및 확장

|     | Adobe | 판매자 |
| --- | --- | --- |
| CPU 리소스, 데이터 센터, 디스크 공간 가용성 | R |   |
| 급증 용량 또는 긴급 업사이징의 가용성 및 실행 | R |   |
| 서지 용량 요청 중 |     | R |
| 제한에 대한 vCPU 사용량 모니터링 | R |   |

{style="table-layout:auto"}
