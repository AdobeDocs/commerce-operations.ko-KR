---
title: 온-프레미스 설치 사전 요구 사항
description: Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 필요한 소프트웨어 종속성에 대해 자세히 알아보십시오.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---


# 온-프레미스 설치 사전 요구 사항

Adobe Commerce 또는 Magento Open Source을 설치하기 전에 다음을 수행해야 합니다.

* 을(를) 충족하는 호스트를 하나 이상 설정합니다. [시스템 요구 사항](../system-requirements.md).
* 로드 밸런싱을 사용하여 둘 이상의 웹 노드를 설정하는 경우 시스템의 해당 부분을 설정하고 테스트하십시오 _이전_ 응용 프로그램을 설치합니다.
* 설치 중에 여러 지점에서 전체 시스템을 백업할 수 있으므로 문제가 있을 경우 시스템을 롤백할 수 있습니다.

>[!NOTE]
>
>에 Adobe Commerce 또는 Magento Open Source을 설치하고 있다고 가정합니다 **개발 환경**&#x200B;컴퓨터에 대한 루트 사용자 액세스 권한이 있는지 확인합니다. **및** 그 기계는 아주 안전할 필요가 없다. 더 안전한 컴퓨터를 설정하는 경우에는 네트워크 관리자에게 추가 지원을 요청하는 것이 좋습니다.

운영 체제 소프트웨어를 업데이트하고 업그레이드하는 것이 좋습니다. 이러한 업그레이드는 향후 문제를 방지할 수 있는 보안 및 소프트웨어 수정 사항을 제공할 수 있습니다. 이게 무슨 뜻인지 모르니? 저희 회사 [설치 개요 페이지](../overview.md).

다음 명령을 사용자 로 입력합니다. `root` 권한:

* 우분투

   ```bash
   apt-get update
   ```

   ```bash
   apt-get upgrade
   ```

* CentOS

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

Adobe Commerce 및 Magento Open Source은 다음 결과로 Apache 버전 2.4를 지원합니다.

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache를 설치하거나 업그레이드하려면 다음을 참조하십시오 [Apache](web-server/apache.md).

### PHP

자세한 내용은 [시스템 요구 사항](../system-requirements.md) 지원되는 버전의 PHP 및 [PHP] PHP 요구 사항에 대해 설명합니다.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

For example:

```bash
mysql -u magento -p
```

설치하는 Adobe Commerce 또는 Magento Open Source 버전에 대한 올바른 MySQL 버전이 있는지 확인합니다([지원되는 버전을 확인하려면 여기에서 확인하십시오.](../system-requirements.md). 다음 결과는 실행 중인 버전을 나타냅니다.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

유형 `help` 또는 `\h` 도움이 필요합니다. 유형 `\c` 현재 입력 문을 지우려면

Enter 키 `exit` at `mysql>` 종료하라는 메시지를 표시합니다.

MySQL을 설치하거나 업그레이드하려면 다음을 참조하십시오 [MySQL](database/mysql.md).

### Elasticsearch 또는 OpenSearch

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

예:

```bash
curl -XGET 'localhost:9200'
```

```terminal
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
