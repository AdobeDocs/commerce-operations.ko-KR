---
title: 플랫폼 도구
description: Adobe 상거래 구현을 위한 권장 플랫폼 도구를 선택합니다.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Platform tools

간섭 없이 전자 상거래 사이트를 계속 실행할 수 있도록 철저하게 테스트하고 잘 생각해야 하는 측면이 있습니다. 데이터 저장과 프로그래밍에서 캐싱 및 보안에 이르기까지 사이트의 모든 측면을 해결할 수 있는 적합한 솔루션을 선택해야 할 뿐만 아니라, 두 가지 기능이 원활하게 실행되고, 구축되고 효율적으로 최적화할 수 있는 플랫폼을 제공하는 데 적합한 프로세스가 필요합니다.

이 섹션에서는 다양한 Adobe Commerce 구현에서 테스트하고 완성된 도구, 솔루션, 프로세스 및 방법론을 살펴볼 뿐만 아니라 특정 비즈니스 요구 사항과 목표에 가장 적합한 솔루션을 추천합니다.

다음 표에는 추천하고 Adobe 상거래 내에서 사용하여 플랫폼에서 성능을 높일 수 있는 솔루션이 포함되어 있습니다.

| Purpose | 도구 |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| 프로그래밍 언어 | PHP, JS, HTML, LESS CSS |
| IDE(통합 개발 환경) | Eclipse, PHPStorm |
| 웹 서버 | Nginx, Apache |
| 캐싱 서비스 | 레디스, 바니쉬 |
| Search services | Elasticsearch |
| Message queue services | RabbitMQ |
| 보안 검사 도구 | 소나큐, ZAP |

## Datbase

브랜드의 요구 사항에 따라 사용하는 세 가지 다른 도구가 있습니다. MySQL은 저장소가 극심한 로드를 처리하지 못할 것으로 예상하는 경우 Analysis Workspace 데이터베이스로서 탁월한 기본 솔루션입니다.

MariaDB is more community-focused and works better for users who care more about features than pure performance. MariaDB supports a large array of database engines, disk encryption, complex horizontal interconnectivity, and scaling features, which could be interesting for large Adobe Commerce stores.

Percona는 성능과 최대 로드 처리를 중심으로 하는 MySQL의 포크입니다. Choose MariaDB if you need more quality of life and DevOps features. 대규모 데이터 세트에서 높은 로드 성능을 구현하려면 Percona로 이동합니다.

## 프로그래밍 언어

Adobe Commerce is a PHP-based application and the newest releases are always compatible with the latest stable PHP version (for example, Adobe Commerce version 2.4 recommends using PHP 7.4). 보안 및 성능을 향상시키기 위해 PHP를 구성할 때 요청 처리 시 최고 속도와 효율성을 얻을 수 있는 몇 가지 요소를 고려해야 합니다. Adobe Commerce 웹 저장소는 HTML, JavaScript 및 LESS CSS 사전 처리기로 빌드되어 있습니다.

## 웹 서버

Adobe 상거래 는 Nginx 및 Apache 웹 서버를 완전히 지원합니다. Adobe 상거래 는 두 가지 모두에 대한 샘플 권장 구성 파일을 제공합니다.

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## 캐싱 서비스

Redis, Memcache, 파일 시스템 및 데이터베이스를 포함하여 캐시 및 세션 데이터를 저장하는 다양한 옵션을 제공합니다. 여러 웹 노드가 있는 설정의 경우 Redis가 가장 좋습니다.

저장소에 대한 전체 페이지 캐시 서버로 Varnish를 사용하는 것이 좋습니다. Adobe 상거래 에서는 성능에 대한 모든 권장 설정을 포함하는 Varnish용 샘플 구성 파일을 배포합니다.

## 검색 서비스

For Adobe Commerce version 2.4 and later, all installations must be configured to use Elasticsearch as the catalog search solution. Elasticsearch provides quick and advanced searches on products in the catalog. Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## Message queue services

메시지 큐는 메시지의 발신자와 수신자가 서로 연락하지 않는 비동기 통신 메커니즘을 제공합니다. RabbitMQ is an open-source message broker that offers a reliable, highly available, scalable, and portable messaging system.

## Security tools

The [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) enables you to regularly monitor your store websites and receive updates for known security risks, malware, and out-of-date software. Typically, you start using this tool when you begin user-acceptance testing (UAT). Besides the Adobe Commerce Security Scan tool, which is free and available for all implementations and versions of Adobe Commerce, there are other choices that can be used during the CI/CD process and before each release.

SonarQube is an open-source quality management platform, designed to analyze and measure your code’s technical quality. SonarQube는 코드 버그, 구문 오류 및 취약점에 대한 전체 보고서를 제공할 뿐만 아니라 코드 수정에 대한 제안 및 예를 제공합니다. SonarQube는 CI/CD 환경에서 코드를 배포하기 전에 분석할 수 있는 도구로 사용하는 것이 좋습니다.

ZAP(Steed Attack Proxy)는 전 세계 수천 명의 펜 테스터가 사용하는 무료 보안 테스트 도구입니다. ZAP는 OWASP에서 개발되었으며 수동 보안 테스트를 위한 가장 선호하는 도구 중 하나입니다.
