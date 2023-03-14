---
title: 플랫폼 도구
description: Adobe Commerce 구현에 대해 권장되는 플랫폼 도구를 선택합니다.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 플랫폼 도구

전자 상거래 사이트를 간섭 없이 계속 운영하기 위해 잘 숙고하고 엄격하게 테스트해야 하는 측면이 부족하지 않습니다. 데이터 스토리지 및 프로그래밍에서 캐싱 및 보안에 이르기까지 사이트의 모든 측면을 처리할 수 있는 적합한 솔루션을 확인해야 할 뿐만 아니라, 원활한 실행을 보장하고 효율적으로 구축 및 최적화할 수 있는 플랫폼을 제공하려면 적합한 프로세스가 필요합니다.

이 섹션에서는 여러 Adobe Commerce 구현에 대해 테스트 및 완료된 도구, 솔루션, 프로세스 및 방법론에 대해 살펴볼 뿐만 아니라 특정 비즈니스 요구 사항 및 목표에 가장 적합한 솔루션에 대한 권장 사항도 제공합니다.

다음 표에는 플랫폼 성능을 향상시키기 위해 Adobe Commerce 내에서 권장되고 사용할 수 있는 솔루션이 포함되어 있습니다.

| 목적 | 도구 |
|------------------------------------------|-------------------------|
| 데이터베이스 | MySQL, MariaDB, Percona |
| 프로그래밍 언어 | PHP, JS, HTML, CSS 줄이기 |
| IDE(통합 개발 환경) | Eclipse, PHPStorm |
| 웹 서버 | Nginx, Apache |
| 캐싱 서비스 | 레디스, 바니시 |
| 서비스 검색 | Elasticsearch |
| 메시지 큐 서비스 | [!DNL RabbitMQ] |
| 보안 검색 도구 | SonarQube, ZAP |

## 데이터베이스

브랜드의 필요에 따라 사용하는 도구가 세 가지가 있습니다. MySQL은 저장소에서 과도한 로드를 처리하지 못할 경우 Adobe Commerce 데이터베이스로서 매우 훌륭한 기본 솔루션입니다.

MariaDB는 커뮤니티 중심적이며 순수한 성능보다 기능에 더 관심이 있는 사용자에게 더 적합합니다. MariaDB는 대규모 데이터베이스 엔진, 디스크 암호화, 복잡한 수평 상호 연결 및 확장 기능을 지원하므로 Adobe Commerce 대형 스토어에 관심을 가질 수 있습니다.

Percona는 성능과 최대 로드 처리를 중심으로 하는 MySQL의 포크입니다. 삶의 질과 DevOps 기능이 더 필요한 경우 MariaDB를 선택하십시오. 대규모 데이터 세트에서 높은 로드 성능을 얻는 것이 목표라면 Percona로 이동하십시오.

## 프로그래밍 언어

Adobe Commerce은 PHP 기반 응용 프로그램이며 최신 릴리스는 항상 안정적인 최신 PHP 버전과 호환됩니다(예: Adobe Commerce 버전 2.4에서는 PHP 7.4를 사용하는 것이 좋습니다). 더 많은 보안과 성능을 얻기 위해, 요청 처리 시 최대 속도와 효율성을 얻기 위해 PHP를 구성할 때 고려해야 할 몇 가지 요소가 있습니다. Adobe Commerce 웹 상점 첫 페이지는 HTML, JavaScript 및 LESS CSS 프리 프로세서로 구축됩니다.

## 웹 서버

Adobe Commerce은 Nginx 및 Apache 웹 서버를 완전히 지원합니다. Adobe Commerce은 다음 두 가지 모두에 대한 샘플 권장 구성 파일을 제공합니다.

- **Ngix**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx 샘플에는 성능 향상을 위한 설정이 포함되어 있으며 재구성이 거의 필요하지 않도록 설계되었습니다.

## 캐싱 서비스

Adobe Commerce은 Redis, Memcache, 파일 시스템 및 데이터베이스를 포함하여 캐시 및 세션 데이터를 저장하는 다양한 옵션을 제공합니다. 여러 웹 노드가 있는 설치의 경우 Redis가 가장 적합한 옵션입니다.

Varnish 를 저장소의 전체 페이지 캐시 서버로 사용하는 것이 좋습니다. Adobe Commerce은 성능에 대한 모든 권장 설정이 포함된 Varnish용 샘플 구성 파일을 배포합니다.

## 서비스 검색

Adobe Commerce 버전 2.4 이상의 경우, 모든 설치는 Elasticsearch 또는 OpenSearch를 카탈로그 검색 솔루션으로 사용하도록 구성해야 합니다. Elasticsearch은 카탈로그의 제품에 대해 빠르고 고급 검색을 제공합니다. 2.4 이전 릴리스의 경우 Elasticsearch은 선택 사항이지만 권장됩니다.

## 메시지 큐 서비스

메시지 큐들은 메시지의 발신자와 수신자가 서로 접촉하지 않는 비동기 통신 메커니즘을 제공한다. [!DNL RabbitMQ] 는 안정적이고 가용성이 높으며 확장 가능하고 휴대성이 뛰어난 메시징 시스템을 제공하는 오픈 소스 메시지 브로커입니다.

## 보안 도구

다음 [Adobe Commerce 보안 검색 도구](https://docs.magento.com/user-guide/magento/security-scan.html) 을 사용하면 스토어 웹 사이트를 정기적으로 모니터링하고 알려진 보안 위험, 맬웨어 및 오래된 소프트웨어에 대한 업데이트를 받을 수 있습니다. 일반적으로 UAT(사용자 승인 테스트)를 시작할 때 이 도구를 사용하기 시작합니다. 무료로 Adobe Commerce의 모든 구현 및 버전에서 사용할 수 있는 Adobe Commerce 보안 검색 도구 외에도 CI/CD 프로세스 중 및 각 릴리스 전에 사용할 수 있는 다른 선택 사항이 있습니다.

SonarQube는 코드의 기술 품질을 분석하고 측정하도록 설계된 오픈 소스 품질 관리 플랫폼입니다. SonarQube는 코드 버그, 구문 오류 및 취약점에 대한 전체 보고서를 제공할 뿐만 아니라 코드 수정에 대한 제안과 예제를 제공합니다. SonarQube는 코드를 배포하기 전에 분석할 수 있는 도구로 CI/CD 환경에서 사용하기에 적합합니다.

ZAP(Zed Attack Proxy)는 전 세계 수천 명의 펜테스터가 사용하는 무료 보안 테스트 도구입니다. ZAP는 OWASP에서 개발되었으며 수동 보안 테스트를 위해 가장 선호되는 도구 중 하나입니다.
