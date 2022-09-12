---
title: 원격 MySQL 데이터베이스 연결 설정
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 대한 원격 데이터베이스 연결을 구성하십시오.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# 원격 MySQL 데이터베이스 연결 설정

데이터베이스 서버와 웹 서버를 같은 컴퓨터에서 실행하는 대신 별도의 서버에서 데이터베이스를 호스팅하려는 경우가 있습니다.

Adobe에서 다른 컴퓨터의 MySQL 서버에 연결하는 방법을 제공했습니다. Adobe Commerce 및 Magento Open Source 2.4.3부터는 코드를 변경하지 않고 Amazon Web Services(AWS) Aurora 데이터베이스를 사용하도록 애플리케이션을 구성할 수도 있습니다.

Aurora는 AWS에서 호스팅되는 고성능, 완벽하게 호환되는 MySQL 서버입니다.

## AWS Aurora 데이터베이스에 연결

Aurora를 데이터베이스로 사용하는 것은 기본 데이터베이스 커넥터를 사용하여 일반 Adobe Commerce 및 Magento Open Source 설정 구성에서 데이터베이스를 지정하는 것만큼 쉽습니다.

실행 시 `bin/magento setup:install`에서 Aurora 정보를 사용하십시오. `db-` 필드:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

다음 `db-host` 값은 `https://` 및 후행 `:portnumber`  제거됨.

## 원격 데이터베이스 연결 설정

>[!NOTE]
>
>이 항목은 숙련된 네트워크 관리자 또는 데이터베이스 관리자만 사용해야 하는 고급 항목입니다. 다음을 수행해야 합니다. `root` 파일 시스템에 액세스할 수 있어야 하며 MySQL에 `root`.

### 전제 조건

시작하기 전에 다음을 수행해야 합니다.

* [MySQL Server 설치](mysql.md) 데이터베이스 서버에 있어야 합니다.
* [데이터베이스 인스턴스 만들기](mysql.md#configuring-the-database-instance) 데이터베이스 서버에 있어야 합니다.
* Adobe Commerce 또는 Magento Open Source 웹 노드에 MySQL 클라이언트를 설치합니다. 자세한 내용은 MySQL 설명서를 참조하십시오.

### 고가용성

웹 서버나 데이터베이스 서버가 클러스터링된 경우 다음 지침을 사용하여 원격 데이터베이스 연결을 구성하십시오.

* 각 웹 서버 노드에 대한 연결을 구성해야 합니다.
* 일반적으로 데이터베이스 로드 밸런서에 대한 데이터베이스 연결을 구성합니다. 그러나 데이터베이스 클러스터링은 복잡할 수 있으며 사용자가 직접 구성할 수 있습니다. Adobe은 데이터베이스 클러스터링에 대한 특정 권장 사항을 만들지 않습니다.

   자세한 내용은 [MySQL 설명서](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 연결 문제 해결

두 호스트에 연결하는 데 문제가 있는 경우 먼저 다른 호스트를 ping하여 연결할 수 있는지 확인합니다. 방화벽 및 SELinux 규칙을 수정하여 한 호스트에서 다른 호스트로 연결을 허용해야 할 수 있습니다(SELinux를 사용하는 경우).

## 원격 연결 만들기

원격 연결을 만들려면

1. 데이터베이스 서버에서 `root` MySQL 구성 파일을 엽니다.

   해당 위치를 찾으려면 다음 명령을 입력합니다.

   ```bash
   mysql --help
   ```

   위치는 다음과 유사하게 표시됩니다.

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Ubuntu 16에서는 일반적으로 경로가 사용됩니다 `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 구성 파일에서 `bind-address`.

   있을 경우 다음과 같이 값을 변경합니다.

   존재하지 않는 경우 `[mysqld]` 섹션을 참조하십시오.

   ```conf
   bind-address = <ip address of your web node>
   ```

   자세한 내용은 [MySQL 설명서](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)특히 클러스터된 웹 서버가 있는 경우

1. 구성 파일에 대한 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. MySQL 서비스를 다시 시작합니다.

   * CentOS: `service mysqld restart`

   * 우분투: `service mysql restart`
   >[!NOTE]
   >
   >MySQL을 시작하지 못하면 syslog에서 문제의 소스를 찾습니다. 다음 방법으로 문제 해결 [MySQL 설명서](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) 또는 다른 권위 있는 소스.

## 데이터베이스 사용자에게 액세스 권한 부여

웹 노드가 데이터베이스 서버에 연결할 수 있도록 하려면 원격 서버의 데이터베이스에 대한 웹 노드 데이터베이스 사용자 액세스 권한을 부여해야 합니다.

이 예는 를 부여합니다 `root` 데이터베이스 사용자가 원격 호스트의 데이터베이스에 대한 전체 액세스 권한을 갖습니다.

데이터베이스 사용자에게 액세스 권한을 부여하려면

1. 데이터베이스 서버에 로그인합니다.
1. MySQL 데이터베이스에 을(를) `root` 사용자.
1. 다음 명령을 입력합니다.

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   For example,

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >웹 서버가 클러스터링된 경우 모든 웹 서버에 동일한 명령을 입력합니다. 모든 웹 서버에 대해 동일한 사용자 이름을 사용해야 합니다.

## 데이터베이스 액세스 확인

웹 노드 호스트에서 다음 명령을 입력하여 연결이 작동하는지 확인합니다.

```bash
mysql -u <local database username> -h <database server ip address> -p
```

MySQL 모니터가 다음과 같이 표시되면 데이터베이스가 Adobe Commerce 또는 Magento Open Source 준비가 된 것입니다.

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

웹 서버가 클러스터링된 경우 각 웹 서버 호스트에 명령을 입력합니다.

## Adobe Commerce 또는 Magento Open Source 설치

Adobe Commerce 또는 Magento Open Source을 설치할 때 다음을 지정해야 합니다.

* 기본 [URL](https://glossary.magento.com/url) (이하 *스토어 주소*) 의 호스트 이름 또는 IP 주소를 지정합니다 *웹 노드*
* 데이터베이스 호스트는 *원격 데이터베이스 서버* IP 주소(또는 데이터베이스 서버가 클러스터링된 경우 로드 밸런서)
* 데이터베이스 사용자 이름은 *로컬 웹 노드* 액세스 권한을 제공한 데이터베이스 사용자
* 데이터베이스 암호는 로컬 웹 노드 사용자의 암호입니다
* 데이터베이스 이름은 원격 서버의 데이터베이스 이름입니다
