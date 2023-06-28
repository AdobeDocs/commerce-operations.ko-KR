---
title: 품질 관리
description: 구현 프로젝트와 관련된 Adobe Commerce 품질 관리 프로세스에 대해 알아봅니다.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 품질 관리 프로세스 및 도구

![품질 관리 프로세스 다이어그램](../../assets/playbooks/quality-control-diagram.svg)

이전 다이어그램에서의 품질관리 과정은 다음과 같이 간략하게 설명할 수 있다.

<table>
<thead>
  <tr>
    <th>소프트웨어 개발 프로세스</th>
    <th>QC 작업 과정</th>
    <th>QC</th>
    <th>QC 리더</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>개발</td>
    <td>계획 수립</td>
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
    <td>테스트 데이터 준비 및 가져오기</td>
  </tr>
  <tr>
    <td></td>
    <td>테스트 분석 및 디자인</td>
    <td>테스트 계획 검토 및 기여</td>
    <td>준비, 사양 시작</td>
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
    <td>테스트 데이터 준비 및 가져오기</td>
    <td> 분석, 설계의 선도, 안내 및 모니터링</td>
  </tr>
  <tr>
    <td>내부 테스트</td>
    <td>구현 및 실행 테스트</td>
    <td>테스트 구현, 테스트 실행 및 로그</td>
    <td>테스트 구현 및 실행 모니터링</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>성능 확인 및 스캔 보안 - 결과 및 예상 결과의 편차를 평가합니다.</td>
    <td>테스트 기준에 대한 테스트의 추적 가능성을 확인하고 버그 추적 시스템에서 버그를 추적합니다.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>버그 추적 시스템에 게시 (Jira/Redmine/Trello)</td>
    <td>PM이 정의한 프로젝트 계획에 부합하도록 테스트 우선 순위 지정/예약</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>버그 수정 후 다시 테스트(확인 테스트)</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>평가 및 보고</td>
    <td>테스트 진행 상황을 QC 리드 및 PM에 보고</td>
    <td>테스트 결과 및 진행률 평가</td>
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
    <td>추가 작업</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>소스 코드를 변경한 후 재테스트 및 회귀 테스트 수행</td>
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
    <td>후속 테스트 진행 상황</td>
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

와 유사 [도구](project-management-tools.md) 개발 프로세스를 위해 품질 관리 테스트를 위해 종종 활용하는 솔루션 및 플랫폼을 몇 가지 선택했습니다.

| 목적 | 도구 |
|---------------------------|---------------------------------------------------|
| 웹 사이트 성과 지수 | Google PageSpeed, Webpagetest, JMeter |
| 보안 | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| 문제 관리 시스템 | JRA |
| UI 테스트 | 완벽한 픽셀, 브라우저 스택 |
| API 테스트 | Postman, SoapUI |
| 자동화 테스트 | Selenium |


## 웹 사이트 성과 지수

GooglePageSpeed는 모바일 장치와 데스크탑 장치 모두에서 페이지 성능을 보고하고 페이지 개선 방법에 대한 제안을 제공합니다.

WebPageTest는 실제 브라우저를 사용하여 웹 페이지에 액세스하고 타이밍 지표를 수집하는 웹 성능 도구입니다.

JMeter는 웹 애플리케이션에 초점을 두고 다양한 서비스의 성능을 분석 및 측정하는 로드 테스트 도구로 사용할 수 있는 Apache 프로젝트입니다.

## 보안

개발 과정에서 SonarQube와 ZAP가 도입되었지만, QC 과정에서 어떻게 관여하는지에 대한 자세한 정보와 함께 여기에 포함하고 있습니다.

SonarQube는 버그, 코드 스멜 및 보안 취약점을 감지하기 위해 코드의 정적 분석과 함께 자동 검토를 수행하는 코드 품질의 지속적인 검사에 사용됩니다.

OWASPZAP(Zed Attack Proxy)는 애플리케이션 보안을 처음 시작하는 사용자와 전문 침투 테스터 모두에서 사용할 수 있도록 설계되었습니다. 내장된 기능 중 일부는 가로채기 프록시 서버, 기존 및 AJAX 웹 크롤러, 자동 스캐너, 수동 스캐너, 강제 브라우징, Fuzzier, WebSocket 지원, 스크립팅 언어 및 Plug-n-Hack 지원을 포함합니다.

## UI 테스트

Perfect Pixel을 사용하면 개발자와 마크업 디자이너가 개발된 HTML 위에 반투명 이미지 오버레이를 놓고 픽셀 간의 완벽한 비교를 수행할 수 있습니다.

BrowserStack은 개발자가 온디맨드 브라우저, 운영 체제 및 실제 모바일 디바이스에서 웹 사이트 및 모바일 애플리케이션을 테스트할 수 있는 클라우드 웹 및 모바일 테스트 플랫폼입니다.

## API 테스트

Postman은 API 개발을 위한 공동 작업 플랫폼입니다. Postman은 API를 빌드하는 각 단계를 단순화하고 공동 작업을 간소화하므로 더 나은 API를 만들 수 있습니다.

SoapUI는 SOAP(Simple Object Access Protocol) 및 REST(표현 상태 전송)를 위한 오픈 소스 웹 서비스 테스트 응용 프로그램입니다. 이 기능은 웹 서비스 검사, 호출, 개발, 시뮬레이션 및 조롱, 기능 테스트, 로드 및 규정 준수 테스트를 포함합니다.

## 자동화 테스트

Selenium은 여러 구성 요소(Selenium 클라이언트 API, Selenium WebDriver)로 구성되며, 각 구성 요소는 웹 애플리케이션 테스트 자동화 개발에 도움이 되는 특정 역할을 수행합니다.
