---
title: CentOS에서 캐시 설정
description: CentOS에서 캐시된 멤버를 설치 및 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# CentOS에서 캐시 설정

이 섹션에서는 CentOS에 캐시된 메모리를 설치하는 지침을 제공합니다. 자세한 내용은 [캐시된 wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe은 최신 안정적인 memcached 버전(memcached의 경우 현재 3.1.3)을 사용할 것을 권장합니다.

PHP에는 memcache에 대한 기본 지원이 없으므로 사용하려면 PHP용 확장을 설치해야 합니다. 사용할 수 있는 PHP 확장에는 두 가지가 있으며 사용할 PHP를 디코딩하는 것이 중요합니다.

- `memcache` (_no d_) - 정기적으로 유지 관리되지 않는 오래되었지만 인기 있는 확장.
다음 `memcache` 현재 확장 _포함하지 않음_ PHP 7을 사용하여 작업 자세한 내용은 [memcache용 PHP 설명서](https://www.php.net/manual/en/book.memcache.php).

   정확한 이름은 `php-pecl-memcache` CentOS용.

- `memcached` (_사용`d`_)—PHP 7과 호환되는 최신 유지 관리 확장입니다. 자세한 내용은 [memcached용 PHP 설명서](https://www.php.net/manual/en/book.memcached.php).

   정확한 이름은 `php-pecl-memcached` CentOS용.

## CentOS에서 캐시된 구성원 설치 및 구성

CentOS에 캐시된 멤버를 설치하려면 다음 작업을 사용자로 수행합니다. `root` 권한:

1. memcached 및 해당 종속성을 설치합니다.

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >이전 명령의 구문은 사용하는 패키지 저장소에 따라 달라질 수 있습니다. 예를 들어, 웹 코드와 PHP 5.6을 사용하는 경우 을 입력합니다 `yum install -y php56w-pecl-memcache`. 사용 `yum search memcache|grep php` 를 클릭하여 적절한 패키지 이름을 찾습니다.


1. 다음에 대한 memcached 구성 설정 변경 `CACHESIZE` 및 `OPTIONS`:

   1. 열기 `/etc/sysconfig/memcached` 텍스트 편집기에서 을 참조하십시오.
   1. 에 대한 값을 찾습니다. `CACHESIZE` 1GB 이상으로 변경합니다. 예:

      ```config
      CACHESIZE="1GB"
      ```

   1. 에 대한 값을 찾습니다. `OPTIONS` 그리고 `localhost` 또는 `127.0.0.1`

1. 변경 내용을 `memcached` 텍스트 편집기를 종료합니다.
1. memcached를 다시 시작합니다.

   ```bash
   service memcached restart
   ```

1. 웹 서버를 다시 시작합니다.

   Apache의 경우:

   ```bash
   service httpd restart
   ```

1. 다음 섹션을 계속 진행합니다.

## Commerce를 설치하기 전에 Memcached 작동 여부를 확인하십시오

Adobe은 Commerce를 설치하기 전에 memcached를 테스트하여 작동하는지 확인하는 것을 권장합니다. 이렇게 하면 몇 분 정도 걸리며 나중에 문제를 간단히 해결할 수 있습니다.

### 웹 서버에서 memcached가 인식되는지 확인

웹 서버에서 memcached를 인식하는지 확인하려면 다음을 수행하십시오.

1. 만들기 `phpinfo.php` 웹 서버의 docroot 파일:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 웹 브라우저에서 해당 페이지로 이동합니다.

   예, `http://192.0.2.1/phpinfo.php`

1. memcache가 다음과 같이 표시되는지 확인하십시오.

![웹 서버에서 메모리 캐시를 인식했는지 확인](../../assets/configuration/memcache.png)

memcached 버전 3.0.5 이상을 사용 중인지 확인하십시오.

memcache가 표시되지 않으면 웹 서버를 다시 시작하고 브라우저 페이지를 새로 고칩니다. 표시되지 않는 경우 `php-pecl-memcache` 확장.

### MySQL 데이터베이스 및 PHP 스크립트로 구성된 멤버 캐시 테스트 만들기

테스트는 MySQL 데이터베이스, 테이블 및 데이터를 사용하여 데이터베이스 데이터를 검색하고 memcache에 저장할 수 있는지 확인합니다. PHP 스크립트는 먼저 캐시를 검색합니다. 결과가 없으면 스크립트는 데이터베이스를 쿼리합니다. 원래 데이터베이스에 의해 쿼리가 이행되면 스크립트는 다음을 사용하여 memcache에 결과를 저장합니다 `set` 명령.

[이 테스트에 대한 자세한 내용](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL 데이터베이스를 만듭니다.

```bash
mysql -u root -p
```

에서 `mysql` 프롬프트에 다음 명령을 입력합니다.

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

만들기 `cache-test.php` 웹 서버의 docroot에서 다음을 수행합니다.

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

위치 `<memcached hostname or ip>` 다음 중 하나입니다. `localhost`, `127.0.0.1`또는 memcache 호스트 이름 또는 IP 주소입니다. 다음 `<memcached port>` 은 수신 포트입니다. 기본적으로 `11211`.

명령줄에서 스크립트를 실행합니다.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

첫 번째 결과는 다음과 같습니다 `got result from mysql`. 즉, 키가 memcached에 없지만 MySQL에서 검색되었음을 의미합니다.

두 번째 결과는 다음과 같습니다 `got result from memcached`: 값이 memcached에 성공적으로 저장되었는지 확인합니다.

마지막으로 Telnet 을 사용하여 메모리 캐시 키를 볼 수 있습니다.

```bash
telnet localhost <memcache port>
```

프롬프트에서 다음을 입력합니다.

```bash
stats items
```

결과는 다음과 비슷합니다.

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

memcache 스토리지를 플러시하고 텔넷을 종료합니다.

```bash
flush_all
```

```bash
quit
```

[텔넷 테스트에 대한 추가 정보](https://darkcoding.net/software/memcached-list-all-keys/)
