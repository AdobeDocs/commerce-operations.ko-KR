---
title: 검색 엔진 사전 요구 사항
description: Adobe Commerce의 온프레미스 설치에 지원되는 검색 엔진 소프트웨어를 설치하고 구성하려면 다음 단계를 따르십시오.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 검색 엔진 사전 요구 사항

Adobe Commerce 2.4부터는 카탈로그 검색 솔루션으로 [Elasticsearch](https://www.elastic.co) 또는 [OpenSearch](https://opensearch.org/)을(를) 사용하도록 모든 설치를 구성해야 합니다.

>[!NOTE]
>
>2.4.4에 OpenSearch 지원이 추가되었습니다. OpenSearch는 Elasticsearch의 호환 가능한 포크입니다. Elasticsearch 7을 구성하는 모든 지침은 OpenSearch에 적용됩니다. [Elasticsearch에서 OpenSearch로 마이그레이션](../../../upgrade/prepare/opensearch-migration.md)에서 OpenSearch로 전환하는 방법에 대한 지침을 제공합니다.

## 지원되는 버전

Adobe Commerce 2.4.4 이상을 설치하기 전에 Elasticsearch 또는 OpenSearch를 설치하고 구성해야 합니다.

특정 버전 정보는 [시스템 요구 사항](../../system-requirements.md)을 참조하세요.

## 권장 구성

다음 사항을 권장합니다.

* [검색 엔진에 대한 nginx 구성](configure-nginx.md)
* [검색 엔진에 대한 Apache 구성](configure-apache.md)

## 설치 위치

다음 작업에서는 다음 다이어그램에 따라 시스템을 구성했다고 가정합니다.

![검색 엔진 다이어그램](../../../assets/installation/search-engine-config.svg)

앞의 다이어그램은 다음과 같습니다.

* Commerce 애플리케이션과 검색 엔진은 다른 호스트에 설치됩니다.

  별도의 호스트에서 실행하려면 프록시가 필요합니다. (검색 엔진 클러스터링은 이 안내서의 범위를 벗어나지만 [Elasticsearch 클러스터링 설명서](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html)에서 자세한 정보를 찾을 수 있습니다.)

* 각 호스트에는 자체 웹 서버가 있습니다. 웹 서버는 동일하지 않아도 됩니다.

  예를 들어 Commerce 애플리케이션은 Apache를 실행할 수 있으며 검색 엔진은 nginx를 실행할 수 있습니다.

* 두 웹 서버 모두 전송 계층 보안(TLS)을 사용합니다.

  TLS를 설정하는 것은 설명서에서 다루지 않습니다.

검색 요청은 다음과 같이 처리됩니다.

1. 사용자로부터 검색 요청을 Commerce 웹 서버가 수신하고 이를 검색 엔진 서버에 전달합니다.

   프록시의 호스트 및 포트에 연결하도록 검색 엔진을 구성합니다. 웹 서버의 SSL 포트(기본적으로 443)가 권장됩니다.

1. 검색 엔진 웹 서버(포트 443에서 수신)는 검색 엔진 서버로 요청을 프록시합니다(기본적으로 포트 9200에서 수신).

1. 검색 엔진에 대한 액세스는 HTTP 기본 인증을 통해 추가로 보호됩니다. 검색 엔진에 연결하려면 SSL *및*&#x200B;을 통해 올바른 사용자 이름과 암호를 제공해야 합니다.

1. 검색 엔진은 요청을 처리합니다.

1. 통신은 Elasticsearch 웹 서버가 보안 역방향 프록시 역할을 하는 동일한 경로를 따라 반환됩니다.

## 사전 요구 사항

이 섹션에서 설명하는 작업은 다음 조건을 충족해야 합니다.

* [방화벽 및 SELinux](#firewall-and-selinux)
* [JDK(Java Software Development Kit) 설치](#install-the-java-software-development-kit)
* [검색 엔진 설치](#install-the-search-engine)
* [Elasticsearch 업그레이드](#upgrading-elasticsearch)

### 방화벽 및 SELinux

보안 관련 소프트웨어(iptables, SELinux, AppArmor)는 서브시스템들 간의 통신을 차단하도록 기본적으로 구성될 수 있다. 문제가 있는지 확인하는 것이 좋을 것 같습니다.

#### iptables 및 SELinux에 대한 규칙 설정

방화벽 또는 SELinux와의 통신을 허용하는 규칙을 설정하려면 다음 리소스를 참조하십시오.

* [입력 방법](https://help.ubuntu.com/community/IptablesHowTo)
* [테이블 규칙을 편집하는 방법(fedora 프로젝트)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux 소개(CentOS.org)](https://www.centos.org)
* [SELinux 사용 방법 Wiki(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Java Software Development Kit 설치

Java가 이미 설치되어 있는지 확인하려면 다음 명령을 입력합니다.

```bash
java -version
```

`java: command not found` 메시지가 표시되면 다음 섹션에서 설명한 대로 Java SDK을 설치해야 합니다.

다음 섹션 중 하나를 참조하십시오.

* [CentOS에 최신 JDK 설치](#install-the-jdk-on-centos)
* [Ubuntu에 최신 JDK 설치](#install-the-jdk-on-ubuntu)

#### CentOS에 JDK 설치

이 [Digital Ocean 튜토리얼](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8)을 참조하세요.

JDK를 설치하고 JRE를 *하지*&#x200B;하십시오.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>일부 운영 체제에서는 Java 버전 8을 사용할 수 없습니다. 예를 들어 [Ubuntu에서 사용 가능한 패키지 목록을 검색](https://packages.ubuntu.com/)할 수 있습니다.

#### Ubuntu에 JDK 설치

Ubuntu에 JDK 1.8을 설치하려면 `root` 권한을 가진 사용자로 다음 명령을 입력하십시오.

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

기타 옵션은 [Oracle 설명서](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html)를 참조하세요.

### 검색 엔진 설치

플랫폼별 단계는 [Elasticsearch 설치](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 또는 [OpenSearch 설치 및 구성](https://opensearch.org/docs/latest/opensearch/install/index/)을 따르십시오.

Elasticsearch이 작동하는지 확인하려면 실행 중인 서버에서 다음 명령을 입력합니다.

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

다음과 유사한 메시지가 표시됩니다.

```
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

## Elasticsearch 업그레이드

프로덕션에 배포하기 전에 데이터 백업, 잠재적인 마이그레이션 문제 감지 및 업그레이드 테스트에 대한 전체 지침은 [Elasticsearch 업그레이드](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)를 참조하십시오. 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작해야 할 수도 있고 필요하지 않을 수도 있습니다.

Elasticsearch을 사용하려면 JDK 1.8 이상이 필요합니다. 설치된 JDK 버전을 확인하려면 [Java Software Development Kit 설치](#install-the-java-software-development-kit)를 참조하십시오.

## 추가 리소스

[Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 또는 [OpenSearch](https://opensearch.org/docs/latest/) 설명서를 참조하십시오.
