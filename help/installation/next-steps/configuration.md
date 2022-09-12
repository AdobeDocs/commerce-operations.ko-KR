---
title: 애플리케이션 구성
description: Adobe Commerce 및 Magento Open Source 온프레미스 배포에 필요한 설치 후 구성에 대해 알아봅니다.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# 애플리케이션 구성

이제 Adobe Commerce 또는 Magento Open Source 설치를 완료했으므로 구성해야 합니다. 이 항목에서는 몇 가지 권장 구성 설정을 제공합니다.

## 크론 설정

UNIX 작업 스케줄러인 cron은 애플리케이션의 일상적인 작업에 매우 중요합니다. 색인 재지정, 뉴스레터, 이메일 및 사이트 맵과 같은 일정을 잡습니다. A *crontab* 는 cron 구성입니다.

에서 Adobe Commerce 및 Magento Open Source 서비스를 설치해야 합니다 *crontab*&#x200B;또는 일부 핵심 기능(및 일부 타사 확장)이 제대로 작동하지 않습니다.

cronon에 대한 자세한 내용은 crontab을 제거하고 명령줄에서 cron을 실행하는 방법을 참조하십시오. [크론 구성 및 실행](../../configuration/cli/configure-cron-jobs.md).

## 보안 설정 및 권장 사항

설치 후에는 다음 사항을 권장합니다.

* 파일 소유권 및 권한이 제대로 설정되어 있는지 확인하십시오
* 적극 권장합니다 [기본 관리 URI 변경](../tutorials/admin-uri.md) 변환 전: `admin` 다른 것
* 다음을 확인합니다. [`X-Frame-Option` HTTP 헤더](../../configuration/security/xframe-options.md) 가 제대로 설정되어 있습니다.
* 다음 작업을 수행하여 XSS(교차 사이트 스크립팅)에 예방합니다. [템플릿 보안](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

다음을 통해 설치한 경우 [GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)를 설정하는 경우 응용 프로그램을 배포할 때 프로덕션 환경에 필요한 파일과 폴더만 포함해야 합니다. 필요하지 않은 파일 및 폴더는 잠재적으로 보안 위험을 노출할 수 있습니다.

## Apache 서버 재작성 활성화

Apache 웹 서버를 사용하는 경우 페이지가 제대로 표시되려면 서버 다시 쓰기를 활성화해야 합니다. 그렇지 않으면 스타일과 기타 문제가 없는 페이지가 표시됩니다.

[Apache 서버 rewrites에 대한 섹션](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 다중 웹 노드 환경에서 캐싱

여러 웹 노드가 있는 경우 *사용할 수 없음* 웹 노드 간에 동기화가 없으므로 응용 프로그램의 기본 파일 캐싱을 사용합니다. 즉, 한 웹 노드의 활동이 해당 웹 노드의 파일 시스템에만 기록됩니다. 후속 활동을 수행하면 다른 웹 노드에서 수행되는 경우 불필요한 파일이 작성되거나 오류가 발생할 수 있습니다.

대신, [레디스](../../configuration/cache/config-redis.md) 두 기본값 모두에 대해 [캐시](https://glossary.magento.com/cache) 그리고 페이지 캐시를 구성합니다.

## 서버 설정

이 섹션에서는 응용 프로그램이 실행되는 서버에 대해 고려할 것을 권장하는 설정을 간략하게 설명합니다. 이러한 설정 중 일부는 애플리케이션과 직접 관련이 없습니다. 제안으로만 제공됩니다.

### 로그 순환

UNIX `logrotate` 유틸리티를 사용하면 많은 수의 로그 파일을 생성하는 시스템을 관리할 수 있습니다. 로그 파일의 자동 순환, 압축, 제거 및 메일링을 수행할 수 있습니다. 각 로그 파일은 일별, 주별, 월별 또는 로그 파일이 지정된 크기를 초과하는 경우 처리할 수 있습니다.

자세한 내용은 다음 중 하나를 참조하십시오.

* [방법: 10가지 예와 함께 최종 로그 회전 명령 자습서](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [스택 교환](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 페이지](https://linuxconfig.org/logrotate-8-manual-page)

### 다양한 서비스가 통신할 수 있도록 iptable 규칙을 설정합니다

서버 하나 또는 많은 서버가 있는 경우 서비스를 통신하려면 방화벽에서 포트를 열어야 합니다. 예를 들어 Adobe Commerce과 함께 Solr 검색 엔진을 사용하는 경우 웹 서버와 통신하도록 하려면 Solr 검색 엔진을 활성화해야 합니다. 여러 웹 노드가 있는 경우 두 노드가 서로 통신할 수 있도록 해야 합니다.

추가 정보:

* 우분투: [Ubuntu 설명서 페이지](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS 방법](https://wiki.centos.org/HowTos/Network/IPTables).

### 보안 Enhanced Linux(SELinux) 규칙

SELinux 사용 여부에 대한 권장 사항이 없습니다. 그러나 사용하는 경우 iptables 구성과 유사하게 서로 통신하도록 서비스를 구성해야 합니다.

추가 정보:

* 우분투: [디비안 핸드북](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux)

### 전자 메일 서버 설정

Adobe Commerce 및 Magento Open Source을 사용하려면 이메일 서버가 필요합니다. 특정 서버를 권장하지 않지만 다음 중 하나를 시도할 수 있습니다.

* CentOS용 포스트픽스([Digital Ocean 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS 설명서](https://www.centos.org))
* Ubuntu용 포스트픽스([Digital Ocean 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu 설명서](https://help.ubuntu.com/community/MailServer))

### 향상된 성능을 위해 검색 엔진을 세분화합니다.

2.4.0부터 모든 설치에 Elasticsearch 또는 OpenSearch가 필요합니다.

* [검색 엔진 설치 및 구성](../../configuration/search/overview-search.md)

### 메시지 큐 설정

버전 2.3.0부터 Adobe Commerce 및 Magento Open Source에 메시지 큐 기능이 포함됩니다. 이전 버전에서는 Adobe Commerce에서만 사용할 수 있습니다.

* [RabbitMQ](../../configuration/queues/message-queue-framework.md)

## Adobe Commerce 전용 설정

Adobe Commerce을 사용하는 경우에만 다음을 구성할 수 있습니다.

* [체크 아웃, 주문 관리 및 기타 데이터베이스 테이블을 위해 데이터베이스 분할](../../configuration/storage/multi-master.md)
