---
title: 세션 저장소 위치
description: 세션 파일이 저장되는 위치를 알아봅니다.
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# 세션 저장소 위치

이 항목에서는 세션 파일이 저장되는 위치를 찾는 방법을 설명합니다. 시스템은 다음 논리를 사용하여 세션 파일을 저장합니다.

- memcached를 구성한 경우 세션이 RAM에 저장됩니다. 참조 [세션 저장소에 memcached 사용](memcached.md).
- Redis를 구성한 경우 세션은 Redis 서버에 저장됩니다. 참조 [세션 저장소에 Redis 사용](../cache/redis-session.md).
- 기본 파일 기반 세션 저장소를 사용하는 경우 다음 위치에 표시된 순서대로 세션을 저장합니다.

   1. 에 정의된 디렉토리 [`env.php`](#example-in-envphp)
   1. 에 정의된 디렉토리 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## 예: `env.php`

의 샘플 코드 조각 `<magento_root>/app/etc/env.php` 다음과 같습니다.

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

앞의 예제에서는 세션 파일을 `/var/www/session`

## 예: `php.ini`

을 사용하는 사용자 `root` 권한, 열기 `php.ini` 파일 및 의 값 검색 `session.save_path`. 세션이 저장되는 위치를 식별합니다.

## 세션 크기 관리

자세한 내용은 [세션 관리](https://docs.magento.com/user-guide/stores/security-session-management.html) 에서 _사용 안내서_.

## 가비지 수집 구성

만료된 세션을 정리하려면 시스템에서 `gc` (_쓰레기 수거_) 처리기는 `gc_probability / gc_divisor` 지시문 예를 들어 이러한 지시어를 `1/100` 각각 `1%` (_100개 요청당 한 번의 가비지 수집 호출 가능성_).

가비지 수집 처리기는 `gc_maxlifetime` 지시어 - 세션이 표시된 후 시간(초) _쓰레기통_ 그리고 잠재적으로 청소할 수 있어요

일부 운영 체제(Debian/Ubuntu)에서 기본값은 다음과 같습니다 `session.gc_probability` 지시문 `0`: 가비지 수집 처리기가 실행되지 않도록 합니다.

을 덮어쓸 수 있습니다 `session.gc_` 지시문 `php.ini` 파일의 `<magento_root>/app/etc/env.php` 파일:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

구성은 상인의 웹 사이트의 트래픽 및 특정 요구 사항에 따라 달라집니다.
