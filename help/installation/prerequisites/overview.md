---
title: 온-프레미스 설치 사전 요구 사항
description: Adobe Commerce 온-프레미스 설치에 필요한 소프트웨어 종속성에 대해 자세히 알아보세요.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# 온-프레미스 설치 사전 요구 사항

Adobe Commerce을 설치하기 전에 다음을 수행해야 합니다.

* *Commerce 온-프레미스* 탭에 나열된 [시스템 요구 사항](../system-requirements.md)을(를) 충족하는 호스트를 하나 이상 설정합니다.
* 부하 분산이 있는 웹 노드를 두 개 이상 설정하는 경우 응용 프로그램을 설치하기 _전에_ 시스템의 해당 부분을 설정하고 테스트합니다.
* 문제가 있는 경우 롤백할 수 있도록 설치하는 동안 여러 지점에서 전체 시스템을 백업할 수 있습니다.

>[!NOTE]
>
>**개발 환경**&#x200B;에 Adobe Commerce을 설치하고, 컴퓨터에 대한 루트 사용자 액세스 권한이 있고, **및** 컴퓨터의 보안이 필요하지 않다고 가정합니다. 보다 안전한 시스템을 설정하는 경우 네트워크 관리자에게 추가 지원을 요청하는 것이 좋습니다.

운영 체제 소프트웨어를 업데이트하고 업그레이드하는 것이 좋습니다. 이러한 업그레이드는 향후 문제를 방지할 수 있는 보안 및 소프트웨어 수정 사항을 제공할 수 있습니다. 이게 무슨 뜻인지 모르세요? [설치 개요 페이지](../overview.md)를 확인하십시오.

`root` 권한이 있는 사용자로 다음 명령을 입력하십시오.

* 우분투

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* 센트OS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## 전제 조건 확인

시스템에서 필수 구성 요소를 확인하려면 다음 명령을 입력합니다.

### Apache

CentOS: `httpd -v`

우분투: `apache2 -v`

Adobe Commerce은 다음 결과에 따라 Apache 버전 2.4를 지원합니다.

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache를 설치하거나 업그레이드하려면 [Apache](web-server/apache.md)를 참조하십시오.

### PHP

지원되는 버전의 PHP는 [시스템 요구 사항](../system-requirements.md)에서 *Commerce 온-프레미스* 탭을 참조하고 PHP 요구 사항은 [PHP](../system-requirements.md#php-settings)를 참조하십시오.

### MySQL

설치 중인 Adobe Commerce 버전과 호환되는 MySQL 버전이 있는지 확인하십시오. 지원되는 버전은 [시스템 요구 사항](../system-requirements.md)에서 *Commerce 온-프레미스* 탭을 참조하십시오.

```bash
mysql -u <database root user or database owner name> -p
```

For example:

```bash
mysql -u magento -p
```

다음 결과는 실행 중인 버전을 나타냅니다.

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

도움말을 보려면 `help` 또는 `\h`을(를) 입력하십시오. 현재 입력 문을 지우려면 `\c`을(를) 입력하십시오.

종료하려면 `mysql>` 프롬프트에 `exit`을(를) 입력하십시오.

MySQL을 설치하거나 업그레이드하려면 [MySQL](database/mysql.md)을 참조하세요.

### 검색 엔진

OpenSearch 설치를 확인하려면:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Elasticsearch 설치를 확인하려면:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

For example:

```bash
curl -XGET 'localhost:9200'
```

```
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
