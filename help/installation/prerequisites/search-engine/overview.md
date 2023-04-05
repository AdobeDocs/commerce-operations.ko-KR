---
title: 검색 엔진 사전 요구 사항
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 대해 지원되는 검색 엔진 소프트웨어를 설치하고 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# 검색 엔진 사전 요구 사항

Adobe Commerce 및 Magento Open Source 2.4부터는 모든 설치를 사용하도록 구성해야 합니다 [Elasticsearch](https://www.elastic.co) 또는 [OpenSearch](https://opensearch.org/) 카탈로그 검색 솔루션으로 사용할 수 있습니다.

>[!NOTE]
>
>OpenSearch 지원이 2.4.4에 추가되었습니다. OpenSearch는 Elasticsearch의 호환 가능한 포크입니다. Elasticsearch 7을 구성하는 모든 지침은 OpenSearch에 적용됩니다. [Elasticsearch에서 OpenSearch로 마이그레이션](../../../upgrade/prepare/opensearch-migration.md) OpenSearch로 전환하는 방법에 대한 지침을 제공합니다.

## 지원되는 버전

Adobe Commerce 2.4.4 이상을 설치하기 전에 OpenSearch 또는 Elasticsearch을 설치하고 구성해야 합니다.

자세한 내용은 [시스템 요구 사항](../../system-requirements.md) 를 참조하십시오.

## 권장 구성

다음 사항을 권장합니다.

* [검색 엔진에 대한 ninx 구성](configure-nginx.md)
* [검색 엔진에 대한 Apache 구성](configure-apache.md)

## 설치 위치

다음 작업은 다음 다이어그램에 따라 시스템을 구성했다고 가정합니다.

![검색 엔진 다이어그램](../../../assets/installation/search-engine-config.svg)

앞의 다이어그램은 다음과 같습니다.

* 상거래 애플리케이션과 검색 엔진은 서로 다른 호스트에 설치됩니다.

   별도의 호스트에서 실행하려면 프록시가 작동해야 합니다. (검색 엔진 클러스터링은 이 안내서의 범위를 벗어나지만, [Elasticsearch 클러스터링 설명서](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html))

* 각 호스트에는 자체 웹 서버가 있습니다. 웹 서버가 동일할 필요는 없습니다.

   예를 들어 상거래 애플리케이션은 Apache를 실행할 수 있고 검색 엔진은 nginx를 실행할 수 있습니다.

* 두 웹 서버 모두 TLS(전송 계층 보안)를 사용합니다.

   TLS를 설정하는 것은 설명서의 범위를 벗어납니다.

검색 요청은 다음과 같이 처리됩니다.

1. 사용자로부터 검색 요청을 상거래 웹 서버에서 수신하여 검색 엔진 서버로 전달합니다.

   프록시의 호스트 및 포트에 연결하도록 검색 엔진을 구성합니다. 웹 서버의 SSL 포트(기본적으로 443)를 사용하는 것이 좋습니다.

1. 검색 엔진 웹 서버(포트 443에서 수신 중)는 검색 엔진 서버에 대한 요청을 프록시합니다(기본적으로 포트 9200에서 수신).

1. 검색 엔진에 대한 액세스는 HTTP 기본 인증에 의해 추가로 보호됩니다. 검색 엔진에 도달하도록 요청하려면, SSL을 통해 이동해야 합니다 *및* 올바른 사용자 이름과 암호를 입력하십시오.

1. 검색 엔진이 요청을 처리합니다.

1. 통신은 보안 역방향 프록시로 작동하는 Elasticsearch 웹 서버와 동일한 경로를 따라 반환됩니다.

## 전제 조건

이 섹션에서 설명하는 작업은 다음과 같습니다.

* [방화벽 및 SELinux](#firewall-and-selinux)
* [JDK(Java Software Development Kit) 설치](#install-the-java-software-development-kit)
* [검색 엔진 설치](#install-the-search-engine)
* [업그레이드 Elasticsearch](#upgrading-elasticsearch)

### 방화벽 및 SELinux

보안 관련 소프트웨어(iptables, SELinux, AppArmor)는 기본적으로 하위 시스템 간의 통신을 차단하도록 구성할 수 있습니다. 문제가 있는지 확인하는 것이 좋을 것 같습니다

#### iptables 및 SELinux에 대한 규칙 설정

방화벽 또는 SELinux와 통신할 수 있도록 규칙을 설정하려면 다음 리소스를 참조하십시오.

* [iptables 방법](https://help.ubuntu.com/community/IptablesHowTo)
* [iptables 규칙을 편집하는 방법(fedora 프로젝트)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux(CentOS.org) 소개](https://www.centos.org)
* [SELinux 방법 Wiki(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Java 소프트웨어 개발 키트 설치

Java가 이미 설치되어 있는지 확인하려면 다음 명령을 입력합니다.

```bash
java -version
```

메시지가 `java: command not found` 가 표시되면 다음 섹션에 설명된 대로 Java SDK를 설치해야 합니다.

다음 섹션 중 하나를 참조하십시오.

* [CentOS에 최신 JDK를 설치합니다](#install-the-jdk-on-centos)
* [Ubuntu에 최신 JDK 설치](#install-the-jdk-on-ubuntu)

#### CentOS에 JDK 설치

다음 보기 [Digital Ocean 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

JDK를 설치하고 *not* JRE입니다.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>일부 운영 체제에서는 Java 버전 8을 사용할 수 없을 수 있습니다. 예를 들어 다음 작업을 수행할 수 있습니다. [ubuntu에 사용할 수 있는 패키지 목록 검색](https://packages.ubuntu.com/).

#### Ubuntu에 JDK 설치

Ubuntu에 JDK 1.8을 설치하려면 다음과 같은 명령을 사용할 사용자로 입력합니다 `root` 권한:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

기타 옵션에 대해서는 [Oracle 설명서](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 검색 엔진 설치

팔로우 [Elasticsearch 설치](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 또는 [OpenSearch 설치 및 구성](https://opensearch.org/docs/latest/opensearch/install/index/) 을 참조하십시오.

Elasticsearch이 작동하는지 확인하려면 실행 중인 서버에 다음 명령을 입력합니다.

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

다음과 유사한 메시지가 표시됩니다.

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

OpenSearch가 작동하는지 확인하려면 다음 명령을 입력합니다.

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## 업그레이드 Elasticsearch

을(를) 참조하십시오. [업그레이드 Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 프로덕션에 배포하기 전에 데이터 백업, 잠재적 마이그레이션 문제 감지, 업그레이드 테스트 등에 대한 전체 지침을 살펴보십시오. 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작할 필요가 있거나 필요하지 않을 수 있습니다.

Elasticsearch을 사용하려면 JDK 1.8 이상이 필요합니다. 자세한 내용은 [Java 소프트웨어 개발 키트 설치](#install-the-java-software-development-kit) 를 클릭하여 설치된 JDK 버전을 확인합니다.

## 추가 리소스

자세한 내용은 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 또는 [OpenSearch](https://opensearch.org/docs/latest/) 설명서.
