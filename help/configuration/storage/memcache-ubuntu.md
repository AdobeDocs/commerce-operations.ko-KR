---
title: Ubuntu에 캐시된 구성원 설정
description: Ubuntu에 캐시된 멤버를 설치 및 구성합니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Ubuntu에 캐시된 구성원 설정

이 섹션에서는 Ubuntu에 cached를 설치하는 지침을 제공합니다.

>[!INFO]
>
>memcached 버전 3.0.5 이상을 사용하는 것이 좋습니다.

PHP에는 memcache에 대한 기본 지원이 없으므로 사용하려면 PHP용 확장을 설치해야 합니다. 사용할 수 있는 PHP 확장에는 두 가지가 있으며 사용할 PHP를 디코딩하는 것이 중요합니다.

- `memcache` (_no d_) - 정기적으로 유지 관리되지 않는 오래되었지만 인기 있는 확장.
다음 `memcache` 현재 확장 _포함하지 않음_ PHP 7을 사용하여 작업 자세한 내용은 [memcache용 PHP 설명서](https://www.php.net/manual/en/book.memcache.php).

   정확한 이름은 `php5-memcache` 우분투.

- `memcached` (_사용`d`_)—PHP 7과 호환되는 최신 유지 관리 확장입니다. 자세한 내용은 [memcached용 PHP 설명서](https://www.php.net/manual/en/book.memcached.php).

   정확한 이름은 `php5-memcached` 우분투.

## Ubuntu에 캐시된 구성원 설치 및 구성

**Ubuntu에 캐시된 멤버를 설치 및 구성하려면**:

1. 을 사용하는 사용자 `root` 권한, 다음 명령을 입력합니다.

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 다음에 대한 memcached 구성 설정 변경 `CACHESIZE` 및 `-l`:

   1. 열기 `/etc/memcached.conf` 텍스트 편집기에서 을 참조하십시오.
   1. 을(를) 찾습니다 `-m` 매개 변수.
   1. 값을 최소 로 변경 `1GB`
   1. 을(를) 찾습니다 `-l` 매개 변수.
   1. 값을 다음으로 변경 `127.0.0.1` 또는 `localhost`
   1. 변경 내용을 `memcached.conf` 텍스트 편집기를 종료합니다.
   1. memcached를 다시 시작합니다.

      ```bash
      service memcached restart
      ```

1. 웹 서버를 다시 시작합니다.

   Apache의 경우, `service apache2 restart`

1. 다음 섹션을 계속 진행합니다.

## Magento 설치 전 memcached 작업 확인

Adobe은 Commerce를 설치하기 전에 memcached를 테스트하여 작동하는지 확인하는 것을 권장합니다. 이렇게 하면 몇 분 정도 걸리며 나중에 문제를 간단히 해결할 수 있습니다.

### 웹 서버에서 memcached가 인식되는지 확인

웹 서버에서 메모리를 인식하는지 확인하려면:

1. 만들기 `phpinfo.php` 웹 서버의 docroot 파일:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 웹 브라우저에서 해당 페이지로 이동합니다. For example:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. memcached가 다음과 같이 표시되는지 확인하십시오.

   ![웹 서버에서 memcached를 인식하는지 확인](../../assets/configuration/memcache.png)

   memcached 버전 3.0.5 이상을 사용 중인지 확인하십시오.

   memcached가 표시되지 않으면 웹 서버를 다시 시작하고 브라우저 페이지를 새로 고칩니다. 표시되지 않는 경우 `php-pecl-memcached` 확장.

### memcached에서 데이터를 캐시할 수 있는지 확인

이 테스트에서는 PHP 스크립트를 사용하여 memcached가 저장 및 검색할 수 있는지 확인합니다 [캐시](https://glossary.magento.com/cache) 데이터.

이 테스트에 대한 자세한 내용은 [Ubuntu에서 Memcache 설치 및 사용 방법 자습서](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

만들기 `cache-test.php` 웹 서버의 docroot에서 다음 내용을 참조하십시오.

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

위치 `<memcached hostname or ip>` 다음 중 하나입니다. `localhost`, `127.0.0.1`또는 memcache 호스트 이름 또는 IP 주소입니다. 다음 `<memcached port>` 은 수신 포트입니다. 기본적으로 `11211`.

웹 브라우저에서 해당 페이지로 이동합니다. For example

```http
http://192.0.2.1/cache-test.php
```

처음으로 페이지로 이동하면 다음과 같은 내용이 표시됩니다. `No matching key found. Refresh the browser to add it!`

브라우저를 새로 고칩니다. 메시지가 `Successfully retrieved the data!`

마지막으로 Telnet 을 사용하여 메모리 캐시 키를 볼 수 있습니다.

```bash
telnet localhost <memcache port>
```

프롬프트에서 다음을 입력합니다.

```shell
stats items
```

결과는 다음과 비슷합니다.

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

메모리 캐시 스토리지를 플러시하고 텔넷 종료:

```shell
flush_all
```

```shell
quit
```

[텔넷 테스트에 대한 추가 정보](https://darkcoding.net/software/memcached-list-all-keys/)
