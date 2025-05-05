---
title: 세션 저장소 위치
description: 세션 파일이 저장되는 위치를 알아봅니다.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 세션 저장소 위치

이 항목에서는 세션 파일이 저장된 위치를 찾는 방법에 대해 설명합니다. 시스템은 다음 논리를 사용하여 세션 파일을 저장합니다.

- memcached를 구성하면 세션이 RAM에 저장됩니다. [세션 저장소에 memcached 사용](memcached.md)을 참조하십시오.
- Redis를 구성한 경우 세션이 Redis 서버에 저장됩니다. [세션 저장소에 Redis 사용](../cache/redis-session.md)을 참조하세요.
- 기본 파일 기반 세션 저장소를 사용하는 경우 표시된 순서대로 다음 위치에 세션을 저장합니다.

   1. [`env.php`](#example-in-envphp)에 정의된 디렉터리
   1. [`php.ini`](#example-in-phpini)에 정의된 디렉터리
   1. `<magento_root>/var/session` 디렉터리

## `env.php`의 예

`<magento_root>/app/etc/env.php`의 샘플 코드 조각:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

앞의 예제에서는 세션 파일을 `/var/www/session`에 저장합니다.

## `php.ini`의 예

`root` 권한이 있는 사용자는 `php.ini` 파일을 열고 `session.save_path`의 값을 검색하십시오. 세션이 저장되는 위치를 식별합니다.

## 세션 크기 관리

_사용 안내서_&#x200B;에서 [세션 관리](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/security-session-management)를 참조하세요.

## 가비지 수집 구성

만료된 세션을 정리하기 위해 시스템은 `gc_probability / gc_divisor` 지시문에 의해 계산되는 확률에 따라 `gc`(_가비지 컬렉션_) 처리기를 임의로 호출합니다. 예를 들어 이러한 지시문을 각각 `1/100`(으)로 설정하면 `1%`의 확률(_100개 요청당 가비지 수집 한 번의 호출 확률_)을 의미합니다.

가비지 수집 처리기는 `gc_maxlifetime` 지시문을 사용합니다. 이 시간(초)이 지나면 세션이 _가비지_(으)로 표시되고 정리될 수 있습니다.

일부 운영 체제(Debian/Ubuntu)에서 기본 `session.gc_probability` 지시문은 `0`이므로 가비지 수집 처리기가 실행되지 않습니다.

`<magento_root>/app/etc/env.php` 파일의 `php.ini` 파일에서 `session.gc_` 지시문을 덮어쓸 수 있습니다.

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

구성은 트래픽 및 판매자 웹 사이트의 특정 요구 사항에 따라 달라집니다.
