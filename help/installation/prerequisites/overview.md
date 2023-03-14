---
title: 온-프레미스 설치 사전 요구 사항
description: Adobe Commerce 및 Magento Open Source의 온프레미스 설치에 필요한 소프트웨어 종속성에 대해 자세히 알아봅니다.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# 온-프레미스 설치 사전 요구 사항

Adobe Commerce 또는 Magento Open Source을 설치하기 전에 다음을 수행해야 합니다.

* 다음을 충족하는 호스트 하나 이상 설정 [시스템 요구 사항](../system-requirements.md).
* 로드 밸런싱이 있는 웹 노드를 두 개 이상 설정하는 경우 시스템의 해당 부분을 설정하고 테스트합니다 _다음 이전_ 응용 프로그램을 설치합니다.
* 문제가 있는 경우 롤백할 수 있도록 설치하는 동안 여러 지점에서 전체 시스템을 백업할 수 있습니다.

>[!NOTE]
>
>에 Adobe Commerce 또는 Magento Open Source을 설치한다고 가정합니다. **개발 환경**, 루트 사용자에게 컴퓨터에 대한 액세스 권한 부여, **및** 즉, 이 시스템은 높은 수준의 보안이 필요하지 않습니다. 보다 안전한 시스템을 설정하는 경우 네트워크 관리자에게 추가 지원을 요청하는 것이 좋습니다.

운영 체제 소프트웨어를 업데이트하고 업그레이드하는 것이 좋습니다. 이러한 업그레이드는 향후 문제를 방지할 수 있는 보안 및 소프트웨어 수정 사항을 제공할 수 있습니다. 이게 무슨 뜻인지 모르세요? 다음을 확인하십시오. [설치 개요 페이지](../overview.md).

사용자로 다음 명령을 입력합니다. `root` 권한:

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

Adobe Commerce 및 Magento Open Source은 다음 결과에 따라 Apache 버전 2.4를 지원합니다.

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache를 설치 또는 업그레이드하려면 다음을 참조하십시오. [Apache](web-server/apache.md).

### PHP

다음을 참조하십시오 [시스템 요구 사항](../system-requirements.md) 지원되는 버전의 PHP 및 [PHP] PHP 요구 사항

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

예:

```bash
mysql -u magento -p
```

설치 중인 Adobe Commerce 또는 Magento Open Source 버전에 맞는 MySQL 버전이 있는지 확인합니다([지원되는 버전을 보려면 여기를 클릭하십시오.](../system-requirements.md). 다음 결과는 실행 중인 버전을 나타냅니다.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

유형 `help` 또는 `\h` 도와주세요. 유형 `\c` 현재 입력 문을 지웁니다.

입력 `exit` 위치: `mysql>` 끝내라는 메시지가 표시됩니다.

MySQL을 설치하거나 업그레이드하려면 [MySQL](database/mysql.md).

### 검색 엔진

OpenSearch 설치를 확인하려면:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Elasticsearch 설치를 확인하려면:

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
