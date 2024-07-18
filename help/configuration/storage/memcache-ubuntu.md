---
title: Ubuntu에서 memcached 설정
description: Ubuntu에서 memcached를 설치하고 구성합니다.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Ubuntu에서 memcached 설정

이 섹션에서는 Ubuntu에 memcached를 설치하는 지침을 제공합니다.

>[!INFO]
>
>Adobe은 memcached 버전 3.0.5 이상을 사용할 것을 권장합니다.

PHP에는 memcache에 대한 기본 지원이 없으므로 이를 사용하려면 PHP용 확장을 설치해야 합니다. 사용 가능한 두 개의 PHP 확장명이 있으며, 어떤 것을 사용할지 디코딩하는 것이 중요합니다.

- `memcache`(_no d_)—정기적으로 유지되지 않는 오래되었지만 인기 있는 확장입니다.
`memcache` 확장 프로그램은 현재 _PHP 7에서 작동하지 않습니다_. memcache에 대한 [PHP 설명서](https://www.php.net/manual/en/book.memcache.php)를 참조하십시오.

  Ubuntu의 정확한 이름은 `php5-memcache`입니다.

- `memcached`(_(`d`_&#x200B;을(를) 사용하는 경우)—PHP 7과 호환되는 최신 버전 및 유지 관리된 확장입니다. memcached에 대한 [PHP 설명서](https://www.php.net/manual/en/book.memcached.php)를 참조하세요.

  Ubuntu의 정확한 이름은 `php5-memcached`입니다.

## Ubuntu에서 memcached 설치 및 구성

**Ubuntu에 memcached를 설치하고 구성하려면**:

1. `root` 권한이 있는 사용자는 다음 명령을 입력하십시오.

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. `CACHESIZE` 및 `-l`에 대한 memcached 구성 설정 변경:

   1. 텍스트 편집기에서 `/etc/memcached.conf` 열기
   1. `-m` 매개 변수를 찾습니다.
   1. 값을 `1GB` 이상으로 변경합니다.
   1. `-l` 매개 변수를 찾습니다.
   1. 값을 `127.0.0.1` 또는 `localhost`(으)로 변경
   1. 변경 내용을 `memcached.conf`에 저장하고 텍스트 편집기를 종료합니다.
   1. memcached를 다시 시작합니다.

      ```bash
      service memcached restart
      ```

1. 웹 서버를 다시 시작합니다.

   Apache의 경우 `service apache2 restart`

1. 다음 섹션을 계속합니다.

## Magento 설치 전 memcached 작업 확인

Adobe은 Commerce을 설치하기 전에 memcached를 테스트하여 작동하는지 확인할 것을 권장합니다. 이렇게 하면 몇 분 밖에 걸리지 않으며 나중에 문제 해결을 단순화할 수 있습니다.

### 웹 서버에서 memcached를 인식하는지 확인

웹 서버에서 memcached를 인식하는지 확인하려면:

1. 웹 서버의 docroot에 `phpinfo.php` 파일을 만듭니다.

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 웹 브라우저의 해당 페이지로 이동합니다. For example:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. memcached 가 다음과 같이 표시되는지 확인합니다.

   ![웹 서버에서 memcached를 인식하는지 확인](../../assets/configuration/memcache.png)

   memcached 버전 3.0.5 이상을 사용 중인지 확인하십시오.

   memcached가 표시되지 않으면 웹 서버를 다시 시작하고 브라우저 페이지를 새로 고칩니다. 그래도 표시되지 않으면 `php-pecl-memcached` 확장을 설치했는지 확인하십시오.

### memcached가 데이터를 캐시할 수 있는지 확인

이 테스트에서는 PHP 스크립트를 사용하여 memcached가 캐시 데이터를 저장하고 검색할 수 있는지 확인합니다.

이 테스트에 대한 자세한 내용은 [Ubuntu에서 Memcache를 설치하고 사용하는 방법](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04)을 참조하십시오.

다음 내용으로 웹 서버의 docroot에 `cache-test.php`을(를) 만듭니다.

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

여기서 `<memcached hostname or ip>`은(는) `localhost`, `127.0.0.1`이거나 memcache 호스트 이름 또는 IP 주소입니다. `<memcached port>`은(는) 수신 포트입니다. 기본적으로 `11211`입니다.

웹 브라우저의 해당 페이지로 이동합니다. 예

```http
http://192.0.2.1/cache-test.php
```

페이지로 처음 이동하면 다음과 같이 표시됩니다. `No matching key found. Refresh the browser to add it!`

브라우저를 새로 고칩니다. 메시지가 `Successfully retrieved the data!`(으)로 변경됩니다.

마지막으로 텔넷을 사용하여 memcache 키를 볼 수 있습니다.

```bash
telnet localhost <memcache port>
```

프롬프트에서 다음을 입력합니다.

```shell
stats items
```

그 결과는 다음과 비슷합니다.

```
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

memcached 스토리지를 플러시하고 텔넷을 종료합니다.

```shell
flush_all
```

```shell
quit
```

[Telnet 테스트에 대한 추가 정보](https://darkcoding.net/software/memcached-list-all-keys/)
