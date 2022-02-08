---
title: 플랫폼 도구
description: Adobe Commerce 구현을 위한 권장 플랫폼 도구를 선택합니다.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 플랫폼 도구

간섭 없이 전자 상거래 사이트를 계속 실행할 수 있도록 철저하게 테스트하고 잘 생각해야 하는 측면이 있습니다. 데이터 저장과 프로그래밍에서 캐싱 및 보안에 이르기까지 사이트의 모든 측면을 해결할 수 있는 적합한 솔루션을 선택해야 할 뿐만 아니라, 두 가지 기능이 원활하게 실행되고, 구축되고 효율적으로 최적화할 수 있는 플랫폼을 제공하는 데 적합한 프로세스가 필요합니다.

이 섹션에서는 다양한 Adobe Commerce 구현에 대해 테스트하고 완료된 도구, 솔루션, 프로세스, 방법론 뿐만 아니라 특정 비즈니스 요구 사항과 목표에 가장 적합한 솔루션을 추천합니다.

다음 표에는 권장되는 솔루션 및 Adobe Commerce 내에서 사용하여 플랫폼에서 성능을 향상시킬 수 있습니다.

| 목적 | 도구 |
|------------------------------------------|-------------------------|
| 데이터베이스 | MySQL, MariaDB, Percona |
| 프로그래밍 언어 | PHP, JS, HTML, CSS 감소 |
| IDE(통합 개발 환경) | Eclipse, PHPStorm |
| 웹 서버 | Nginx, Apache |
| 캐싱 서비스 | 레디스, 바니쉬 |
| 검색 서비스 | Elasticsearch |
| 메시지 큐 서비스 | RabbitMQ |
| 보안 검사 도구 | 소나큐, ZAP |

## 데이터베이스

브랜드의 요구 사항에 따라 사용하는 세 가지 다른 도구가 있습니다. MySQL은 저장소가 과도한 로드를 처리하지 못할 것으로 예상하는 경우 Adobe Commerce 데이터베이스로서의 탁월한 기본 솔루션입니다.

MariaDB는 보다 커뮤니티 중심적이고 순수한 성능보다 기능에 대해 더 관심을 갖는 사용자에게 더 잘 작동합니다. MariaDB는 대규모 데이터베이스 엔진, 디스크 암호화, 복잡한 수평 상호 연결 및 확장 기능을 지원하므로 대형 Adobe Commerce 스토어에 유용할 수 있습니다.

Percona는 성능과 최대 로드 처리를 중심으로 하는 MySQL의 포크입니다. 더 많은 삶의 질과 DevOps 기능이 필요한 경우 MariaDB를 선택하십시오. 대규모 데이터 세트에서 높은 로드 성능을 구현하려면 Percona로 이동합니다.

## 프로그래밍 언어

Adobe Commerce은 PHP 기반 응용 프로그램이며 최신 릴리스는 항상 안정적인 최신 PHP 버전과 호환됩니다(예: Adobe Commerce 버전 2.4에서는 PHP 7.4를 사용하는 것이 좋습니다). 보안 및 성능을 향상시키기 위해 PHP를 구성할 때 요청 처리 시 최고 속도와 효율성을 얻을 수 있는 몇 가지 요소를 고려해야 합니다. Adobe Commerce 웹 스토어는 HTML, JavaScript 및 LESS CSS 사전 처리기로 빌드되어 있습니다.

## 웹 서버

Adobe Commerce은 Nginx 및 Apache 웹 서버를 완벽하게 지원합니다. Adobe Commerce은 두 방법 모두에 대한 샘플 권장 구성 파일을 제공합니다.

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx 샘플에는 성능 향상을 위한 설정이 포함되어 있으며, 재구성이 거의 필요하지 않도록 설계되었습니다.

## 캐싱 서비스

Adobe Commerce은 Redis, Memcache, 파일 시스템, 데이터베이스 등 캐시 및 세션 데이터를 저장하는 다양한 옵션을 제공합니다. 여러 웹 노드가 있는 설정의 경우 Redis가 가장 좋습니다.

저장소에 대한 전체 페이지 캐시 서버로 Varnish를 사용하는 것이 좋습니다. Adobe Commerce은 성능에 대한 모든 권장 설정을 포함하는 Varnish용 샘플 구성 파일을 배포합니다.

## 검색 서비스

Adobe Commerce 버전 2.4 이상의 경우 Elasticsearch을 카탈로그 검색 솔루션으로 사용하도록 모든 설치를 구성해야 합니다. Elasticsearch은 카탈로그의 제품에 대한 빠른 및 고급 검색을 제공합니다. Elasticsearch은 2.4 이전 릴리스에 대해 선택 사항이지만 권장됩니다.

## 메시지 큐 서비스

메시지 큐는 메시지의 발신자와 수신자가 서로 연락하지 않는 비동기 통신 메커니즘을 제공합니다. RabbitMQ는 신뢰할 수 있고, 가용성이 높고, 확장 가능하며, 휴대용 메시징 시스템을 제공하는 오픈 소스 메시지 브로커입니다.

## 보안 도구

다음 [Adobe Commerce 보안 검사 도구](https://docs.magento.com/user-guide/magento/security-scan.html) 저장소 웹 사이트를 정기적으로 모니터링하고 알려진 보안 위험, 맬웨어 및 오래된 소프트웨어에 대한 업데이트를 받을 수 있습니다. 일반적으로 UAT(사용자 수락 테스트)를 시작할 때 이 도구를 사용하기 시작합니다. Adobe Commerce의 모든 구현 및 버전에 사용 가능하고 무료 Adobe Commerce 보안 스캔 도구 외에도 CI/CD 프로세스 및 각 릴리스 전에 사용할 수 있는 다른 선택 사항이 있습니다.

SonarQube는 코드의 기술 품질을 분석하고 측정하도록 설계된 오픈 소스 품질 관리 플랫폼입니다. SonarQube는 코드 버그, 구문 오류 및 취약점에 대한 전체 보고서를 제공할 뿐만 아니라 코드 수정에 대한 제안 및 예를 제공합니다. SonarQube는 CI/CD 환경에서 코드를 배포하기 전에 분석할 수 있는 도구로 사용하는 것이 좋습니다.

ZAP(Steed Attack Proxy)는 전 세계 수천 명의 펜 테스터가 사용하는 무료 보안 테스트 도구입니다. ZAP는 OWASP에서 개발되었으며 수동 보안 테스트를 위한 가장 선호하는 도구 중 하나입니다.
