---
title: 세션 저장소 위치
description: 세션 파일이 저장되는 위치를 알아봅니다.
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 세션 저장소 위치

이 항목에서는 세션 파일이 저장된 위치를 찾는 방법에 대해 설명합니다. 시스템은 다음 논리를 사용하여 세션 파일을 저장합니다.

- memcached를 구성한 경우 세션은 RAM에 저장됩니다. 다음을 참조하십시오. [세션 스토리지에 memcached 사용](memcached.md).
- Redis를 구성한 경우 세션은 Redis 서버에 저장됩니다. 다음을 참조하십시오. [세션 스토리지에 Redis 사용](../cache/redis-session.md).
- 기본 파일 기반 세션 저장소를 사용하는 경우 표시된 순서대로 다음 위치에 세션을 저장합니다.

   1. 에 정의된 디렉터리 [`env.php`](#example-in-envphp)
   1. 에 정의된 디렉터리 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 디렉터리

## 의 예 `env.php`

의 샘플 코드 조각 `<magento_root>/app/etc/env.php` 다음 작업을 수행합니다.

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

앞의 예제에서는 세션 파일을에 저장합니다 `/var/www/session`

## 의 예 `php.ini`

을 사용하는 사용자로서 `root` 권한, 열기 `php.ini` 파일 및 값 검색 `session.save_path`. 세션이 저장되는 위치를 식별합니다.

## 세션 크기 관리

다음을 참조하십시오. [세션 관리](https://docs.magento.com/user-guide/stores/security-session-management.html) 다음에서 _사용 안내서_.

## 가비지 수집 구성

만료된 세션을 정리하려면 시스템은 `gc` (_가비지 수집_) 처리기는 다음에 의해 계산되는 확률에 따라 임의로 `gc_probability / gc_divisor` 지시문입니다. 예를 들어 이러한 지시문을 로 설정한 경우 `1/100` 각각 다음과 같은 확률을 의미합니다. `1%` (_100개 요청당 가비지 수집 호출 1개 확률_).

가비지 수집 처리기는 `gc_maxlifetime` 지시문—세션이 표시된 후 경과되는 시간(초) _가비지_ 그리고 잠재적으로 깨끗해졌죠.

일부 운영 체제(Debian/Ubuntu)에서 기본값 `session.gc_probability` 지시문은 입니다. `0`- 가비지 수집 핸들러가 실행되지 않도록 합니다.

다음을 덮어쓸 수 있습니다. `session.gc_` 에서 지시문 `php.ini` 파일 위치: `<magento_root>/app/etc/env.php` 파일:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

구성은 트래픽 및 판매자 웹 사이트의 특정 요구 사항에 따라 달라집니다.
