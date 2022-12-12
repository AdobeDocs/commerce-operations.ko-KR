---
title: 품질 관리
description: 구현 프로젝트와 관련된 Adobe Commerce 품질 제어 프로세스에 대해 알아봅니다.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 품질 관리 프로세스 및 도구

![품질 관리 프로세스 다이어그램](../../assets/playbooks/quality-control-diagram.svg)

이전 다이어그램의 품질 관리 프로세스는 다음과 같이 간략하게 설명될 수 있습니다.

<table>
<thead>
  <tr>
    <th>소프트웨어 개발 프로세스</th>
    <th>QC 워크플로우</th>
    <th>QC</th>
    <th>QC 리더</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>개발</td>
    <td>계획</td>
    <td></td>
    <td>테스트 계획 검토 및 기여</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>테스트 사양 만들기(테스트 사례/테스트 시나리오)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>테스트 데이터 준비 및 획득</td>
  </tr>
  <tr>
    <td></td>
    <td>테스트 분석 및 디자인</td>
    <td>테스트 계획 검토 및 기여</td>
    <td>준비, 사양</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>테스트 사양 만들기(테스트 사례/테스트 시나리오)</td>
    <td>프로젝트에 대한 테스트 전략 작성 또는 검토</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>테스트 데이터 준비 및 획득</td>
    <td> 분석, 설계 안내 및 모니터링</td>
  </tr>
  <tr>
    <td>내부 테스트</td>
    <td>테스트 구현 및 실행</td>
    <td>테스트 구현, 실행 및 로그</td>
    <td>테스트 구현 및 실행 모니터링</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>성능 확인 및 검사 보안 - 예상 결과의 결과 및 편차를 평가합니다.</td>
    <td>테스트 기준까지 테스트 추적을 확인하고 버그 추적 시스템에서 버그를 추적합니다</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>버그 추적 시스템에 버그 게시(Jira/Remine/Trello)</td>
    <td>PM으로 정의된 프로젝트 계획에 맞게 테스트를 우선 순위 지정/예약합니다.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>버그 수정 후 재테스트(확인 테스트)</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>평가 및 보고</td>
    <td>QC 리드 및 PM에 테스트 진행 보고</td>
    <td>테스트 결과 및 진행 상태 평가</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>테스트 중에 수집된 정보를 기반으로 테스트 요약 보고서를 작성합니다</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>고객 피드백 또는 변경 요청(CR) 확인</td>
    <td>후속 작업</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>소스 코드를 변경한 후 재테스트 및 회귀 테스트를 수행합니다</td>
    <td>제어</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>테스트 사양 업데이트</td>
    <td></td>
  </tr>
  <tr>
    <td>유지 관리</td>
    <td>유지 관리</td>
    <td>작업 검토 및 기여</td>
    <td>작업 검토 및 예상 시간</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>테스트 사양 만들기/업데이트</td>
    <td>후속 테스트 진행</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>이러한 작업에 대한 테스트 실행</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>회귀 테스트 수행</td>
    <td></td>
  </tr>
</tbody>
</table>

와 비슷합니다 [도구](project-management-tools.md) 개발 프로세스를 위해 식별되었으며 품질 관리 테스트에 자주 사용하는 몇 가지 선택 솔루션과 플랫폼을 선택했습니다.

| 목적 | 도구 |
|---------------------------|---------------------------------------------------|
| 웹 사이트 성능 인덱스 | Google PageSpeed, Webpagetest, JMeter |
| 보안 | Adobe Commerce 보안 검사 도구, SonarQube, ZAP |
| 문제 관리 시스템 | JIRA |
| UI 테스트 | 완벽한 픽셀, 브라우저 스택 |
| API 테스트 | Postman, SoapUI |
| 자동화 테스트 | 셀레늄 |


## 웹 사이트 성능 인덱스

GooglePageSpeed 는 모바일 및 데스크톱 장치 모두에서 페이지 성능을 보고하고 해당 페이지를 개선할 수 있는 방법에 대한 제안을 제공합니다.

WebPageTest 는 실제 브라우저를 사용하여 웹 페이지에 액세스하고 타이밍 지표를 수집하는 웹 성능 도구입니다.

JMeter는 웹 애플리케이션에 중점을 두고 다양한 서비스의 성능을 분석하고 측정하는 로드 테스트 도구로 사용할 수 있는 Apache 프로젝트입니다.

## 보안

SonarQube와 ZAP는 개발 과정에서 도입되었지만, 우리는 또한 그것이 QC 프로세스에 어떻게 관련되었는지에 대한 더 많은 정보를 가지고 그것을 여기에 포함하고 있습니다.

또한 SonarQube는 버그, 코드 냄새 및 보안 취약점을 감지하기 위한 코드의 정적 분석으로 자동 검토를 수행하기 위해 코드 품질의 지속적인 검사에 사용됩니다.

OWASPZAP(Zed Attack Proxy)는 응용 프로그램 보안뿐만 아니라 전문 침투 테스터도 모두 사용하기 위한 것입니다. 내장 기능 중 일부는 가로채기 프록시 서버, 기존 및 AJAX 웹 크롤러, 자동 스캐너, 수동 스캐너, 강제 검색, Fuzzier, WebSocket 지원, 스크립팅 언어 및 Plug-n-Hack 지원 등을 포함합니다.

## UI 테스트

퍼펙트 픽셀을 사용하면 개발자와 마크업 디자이너가 개발한 HTML 위에 반투명 이미지 오버레이를 놓고 픽셀 단위의 완벽한 비교를 수행할 수 있습니다.

BrowserStack은 개발자가 온디맨드 브라우저, 운영 체제 및 실제 모바일 장치에서 웹 사이트 및 모바일 애플리케이션을 테스트할 수 있도록 하는 클라우드 웹 및 모바일 테스트 플랫폼입니다.

## API 테스트

Postman은 API 개발을 위한 공동 작업 플랫폼입니다. Postman은 API를 빌드하는 각 단계를 단순화하고 공동 작업을 간소화하므로 더 나은 API를 만들 수 있습니다.

SoapUI는 SOAP(Simple Object Access Protocol) 및 표현 상태 전송(REST)을 위한 오픈 소스 웹 서비스 테스트 애플리케이션입니다. 웹 서비스 검사 기능을 다룹니다. 호출, 개발, 시뮬레이션, 기능 테스트 로드 및 준수 테스트.

## 자동화 테스트

Selenium은 여러 구성 요소(Selenium 클라이언트 API, Selenium WebDriver)로 구성되며, 각 구성 요소는 웹 애플리케이션 테스트 자동화 개발을 지원하기 위한 특정 역할을 수행합니다.
