---
title: 애플리케이션 구성
description: Adobe Commerce 온-프레미스 배포에 필요한 사후 설치 구성에 대해 알아봅니다.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 35664c30e438305036d3cfdd1dd1924966f6ced6
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# 애플리케이션 구성

이제 Adobe Commerce 또는 Magento Open Source 설치를 완료했으므로 구성해야 합니다. 이 항목에서는 몇 가지 권장 구성 설정을 제공합니다.

## cron 설정

UNIX 작업 스케줄러 cron 은 애플리케이션의 일상적인 작업에 매우 중요합니다. 리인덱싱, 뉴스레터, 이메일, 사이트 맵 등의 일정을 수립합니다. A *crontab* 는 cron 구성입니다.

에서 Adobe Commerce 서비스를 설치해야 합니다. *crontab*&#x200B;또는 일부 핵심 기능(및 일부 타사 확장)이 제대로 작동하지 않습니다.

crontab을 제거하고 명령줄에서 cron을 실행하는 방법을 포함하여 cron에 대한 자세한 내용은 [cron 구성 및 실행](../../configuration/cli/configure-cron-jobs.md).

## 보안 설정 및 권장 사항

설치 후 다음 사항을 권장합니다.

* 파일 소유권 및 권한이 제대로 설정되어 있는지 확인하십시오.
* 다음을 강력히 권장합니다. [기본 관리자 URI 변경](../tutorials/admin-uri.md) 출처: `admin` 다른 이름으로
* 다음을 확인합니다. [`X-Frame-Option` HTTP 헤더](../../configuration/security/xframe-options.md) 가 제대로 설정되었습니다.
* 다음의 방법으로 크로스 사이트 스크립팅(XSS)에 대한 예방 조치를 취합니다. [템플릿 보호](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

다음을 설치한 경우 [gitHub 저장소 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)를 사용하여 애플리케이션을 배포할 때에는 프로덕션 환경에 필요한 파일과 폴더만 포함해야 합니다. 필요하지 않은 파일 및 폴더는 보안 위험을 초래할 수 있습니다.

## Apache 서버 재작성 사용

Apache 웹 서버를 사용하는 경우 페이지가 제대로 표시되도록 서버 재작성을 활성화해야 합니다. 그렇지 않으면 스타일 및 기타 문제가 없는 페이지가 표시됩니다.

[Apache 서버 재작성에 대한 섹션](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 다중 웹 노드 환경에서 캐싱

웹 노드가 여러 개 있는 경우 *할 수 없음* 웹 노드 간에 동기화가 없으므로 애플리케이션의 기본 파일 캐싱을 사용합니다. 즉, 한 웹 노드의 활동은 해당 웹 노드의 파일 시스템에만 기록됩니다. 후속 활동이 다른 웹 노드에서 수행되는 경우 불필요한 파일이 작성되거나 오류가 발생할 수 있습니다.

대신, [레디스](../../configuration/cache/config-redis.md) 기본 캐시와 페이지 캐시 둘 다에 사용됩니다.

## 서버 설정

이 섹션에서는 응용 프로그램이 실행되는 서버에 대해 고려해야 할 설정에 대해 간략하게 설명합니다. 이러한 설정 중 일부는 응용 프로그램과 직접 관련이 없습니다. 이는 제안으로만 제공됩니다.

### 로그 회전

UNIX `logrotate` 유틸리티를 사용하면 대량의 로그 파일을 생성하는 시스템을 관리할 수 있습니다. 로그 파일의 자동 회전, 압축, 제거 및 메일링을 허용합니다. 각 로그 파일은 매일, 매주, 매월 또는 로그 파일이 지정된 크기를 초과할 때 처리할 수 있습니다.

자세한 내용은 다음 중 하나를 참조하십시오.

* [방법: 10가지 예를 포함하는 최종 로그 회전 명령 자습서](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [스택 교환](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 매뉴얼 페이지](https://linuxconfig.org/logrotate-8-manual-page)

### 다양한 서비스가 통신할 수 있도록 iptables 규칙 설정

서버가 하나이든 많든 간에 서비스가 통신할 수 있도록 하려면 방화벽에서 포트를 열어야 합니다. 예를 들어 Adobe Commerce에서 Solr 검색 엔진을 사용하는 경우 웹 서버와 통신하도록 설정해야 합니다. 여러 웹 노드가 있는 경우 서로 통신할 수 있도록 활성화해야 합니다.

추가 정보:

* 우분투: [Ubuntu 설명서 페이지](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS 방법](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### 보안 강화 Linux(SELinux) 규칙

SELinux 사용 여부에 대한 권장 사항은 없습니다. 그러나 SELinux를 사용하는 경우 iptable 구성과 유사하게 서로 통신하도록 서비스를 구성해야 합니다.

추가 정보:

* 우분투: [데비안 핸드북](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS 위키](https://wiki.centos.org/HowTos/SELinux)

### 전자 메일 서버 설정

Adobe Commerce에는 이메일 서버가 필요합니다. 특정 서버는 권장하지 않지만 다음 중 하나를 시도할 수 있습니다.

* CentOS용 후위([Digital Ocean 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS 설명서](https://www.centos.org))
* Ubuntu용 후위([Digital Ocean 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu 설명서](https://help.ubuntu.com/community/MailServer))

### 향상된 성능을 위해 검색 엔진 세분화:

2.4.0부터 모든 설치에 Elasticsearch 또는 OpenSearch가 필요합니다.

* [검색 엔진 설치 및 구성](../../configuration/search/overview-search.md)

### 메시지 대기열 설정

버전 2.3.0 이후 Adobe Commerce에는 메시지 대기열 기능이 포함되었습니다. 이전 버전에서는 Adobe Commerce에서만 사용할 수 있었습니다.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Adobe Commerce 전용 설정

Adobe Commerce을 사용하는 경우에만 다음을 구성할 수 있습니다.

* [체크아웃, 주문 관리 및 기타 데이터베이스 테이블을 위한 분할 데이터베이스](../../configuration/storage/multi-master.md)
