---
title: 데이터베이스 복제
description: 데이터베이스 복제 구성의 이점을 참조하십시오.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# 데이터베이스 복제

{{ee-only}}

{{deprecate-split-db}}

데이터베이스 복제를 설정하면 다음과 같은 이점이 있습니다.

- 데이터 백업 제공
- 마스터 데이터베이스에 영향을 주지 않고 데이터 분석 사용
- 확장성

MySQL 데이터베이스는 비동기적으로 복제되므로 마스터에서 업데이트를 받기 위해 슬레이브를 영구적으로 연결할 필요가 없습니다.

## 데이터베이스 복제 구성

데이터베이스 복제에 대한 심층적인 논의는 이 가이드의 범위를 벗어납니다. 이를 설정하려면 다음과 같은 리소스를 참조할 수 있습니다.

- [MySQL 설명서](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [MySQL에서 기본 슬레이브 복제 설정 방법(digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce에서는 슬레이브 데이터베이스에 대한 샘플 MySQL 구성을 제공합니다. 간단한 구성에는 `ResourceConnections` 클래스 `README.md`.

다음은 보다 고급 기능이며, 귀하의 정보에만 제공됩니다.

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## 성능 개선

마스터 슬레이브 복제 성능을 향상시키기 위해 슬레이브 인스턴스에 일부 테이블을 필터링할 수 있습니다. 이름 패턴으로 모든 임시 테이블을 필터링하는 것이 좋습니다 `search\_tmp\_%` 에 사용됩니다 [카탈로그](https://glossary.magento.com/catalog) 검색.

이렇게 하려면 다음 줄을 `my.cnf` 파일을 슬레이브 인스턴스에 저장합니다.

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
