---
title: PHP 설정
description: 다음 단계에 따라 필요한 PHP 확장 프로그램을 설치하고 Adobe Commerce의 온프레미스 설치에 필요한 PHP 설정을 구성합니다.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP 설정

이 항목에서는 필요한 PHP 옵션을 설정하는 방법에 대해 설명합니다.

>[!NOTE]
>
>최신 버전의 Adobe Commerce은 PHP 8.1 이상이 필요합니다. 지원되는 모든 PHP 버전에 대해서는 [시스템 요구 사항](../system-requirements.md)을 참조하십시오.

클라우드 구성 지침은 _클라우드 인프라의 Commerce_ 안내서에서 [PHP 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html)을 참조하십시오.

## PHP 프로세스 제어

{{php-process-control}}

## PHP가 설치되었는지 확인

PHP는 대부분의 Linux 배포판에 기본적으로 설치됩니다. 이 항목에서는 사용자가 이미 PHP를 설치했다고 가정합니다. PHP가 설치되어 있는지 확인하려면 명령줄에 다음을 입력합니다.

```bash
php -v
```

PHP가 설치되어 있으면 다음과 유사한 메시지가 표시됩니다.

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

PHP가 설치되지 않은 경우(또는 업그레이드가 필요한 경우) Linux 배포판의 지침에 따라 설치합니다.

## 설치된 확장 확인

Adobe Commerce에는 특정 PHP 확장명이 필요합니다. 다음 목록은 각 Commerce 버전에 필요한 확장을 지정합니다. 이 목록은 각 버전의 최신 버전을 실행하는 배포에서 자동으로 생성됩니다.

{{$include /help/_includes/templated/php-extensions.md}}

설치된 확장을 확인하려면:

1. 설치된 모듈을 나열합니다.

   ```bash
   php -m
   ```

1. 필요한 확장이 모두 설치되었는지 확인합니다.
1. PHP 설치에 사용되는 것과 동일한 워크플로를 사용하여 누락된 모듈을 추가합니다.

## PHP 설정 확인

>[!WARNING]
>
>PHP 7.4.20을 사용하는 경우 `php.ini` 파일에서 `pcre.jit=0`을(를) 설정합니다. CSS를 로드할 수 없는 PHP [bug](https://bugs.php.net/bug.php?id=81101)을(를) 알아봅니다.

- PHP에 대한 시스템 시간대를 설정합니다. 그렇지 않으면 설치 중에 다음과 같은 오류가 표시되고 cron과 같은 시간 관련 작업이 작동하지 않을 수 있습니다.

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- PHP 메모리 제한을 설정합니다.

  Adobe은 다음 사항을 권장합니다.

   - 코드 컴파일 또는 정적 자산 배포, `1G`
   - 디버깅, `2G`
   - 테스트 중, `~3-4G`

- PHP `realpath_cache_size` 및 `realpath_cache_ttl`의 값을 권장 설정으로 늘립니다.

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  이러한 설정을 사용하면 PHP 프로세스가 페이지 로드 시 경로를 조회하는 대신 파일에 경로를 캐시할 수 있습니다. PHP 설명서에서 [성능 조정](https://www.php.net/manual/en/ini.core.php)을 참조하십시오.

- Adobe Commerce 2.1 이상에 필요한 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)을(를) 사용하도록 설정합니다.

  Adobe 성능상의 이유로 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php)을(를) 사용하도록 설정하는 것이 좋습니다. OPcache는 많은 PHP 배포에서 사용할 수 있습니다.

  Adobe Commerce 2.1 이상 버전은 코드 생성에 PHP 코드 주석을 사용합니다.

>[!NOTE]
>
>설치 및 업그레이드 중 문제가 발생하지 않도록 하기 위해, Adobe은 PHP 명령줄 구성과 PHP 웹 서버 플러그인 구성 모두에 동일한 PHP 설정을 적용할 것을 강력히 권장합니다. 자세한 내용은 다음 섹션을 참조하십시오.

## PHP 구성 파일 찾기

이 섹션에서는 필요한 설정을 업데이트하는 데 필요한 구성 파일을 찾는 방법에 대해 설명합니다.

### `php.ini` 구성 파일 찾기

웹 서버 구성을 찾으려면 웹 브라우저에서 [`phpinfo.php` 파일](optional-software.md#create-phpinfophp)을 실행하고 다음과 같이 `Loaded Configuration File`을(를) 찾으십시오.

![PHP 정보 페이지](../../assets/installation/config_phpini-webserver.png)

PHP 명령줄 구성을 찾으려면 다음을 입력합니다

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>`php.ini` 파일이 하나만 있는 경우 해당 파일을 변경하십시오. `php.ini`개 파일이 두 개 있는 경우 *둘 다*&#x200B;개 파일을 변경하십시오. 이렇게 하지 않으면 예기치 않은 성능이 발생할 수 있습니다.

### OPcache 구성 설정 찾기

PHP OPcache 설정은 일반적으로 `php.ini` 또는 `opcache.ini`에 있습니다. 위치는 운영 체제와 PHP 버전에 따라 달라질 수 있습니다. OPcache 구성 파일에 `opcache` 섹션이나 `opcache.enable` 같은 설정이 있을 수 있습니다.

다음 지침을 사용하여 찾습니다.

- Apache 웹 서버:

  Apache가 있는 Ubuntu의 경우, OPcache 설정은 일반적으로 `php.ini` 파일에 있습니다.

  Apache 또는 nginx가 있는 CentOS의 경우 OPcache 설정은 일반적으로 `/etc/php.d/opcache.ini`에 있습니다.

  그렇지 않은 경우 다음 명령을 사용하여 찾습니다.

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx 웹 서버(PHP-FPM 포함): `/etc/php/8.1/fpm/php.ini`

`opcache.ini`이(가) 두 개 이상인 경우 모두 수정하십시오.

## PHP 옵션을 설정하는 방법

PHP 옵션을 설정하려면 다음을 수행합니다.

1. 텍스트 편집기에서 `php.ini`을(를) 엽니다.
1. 사용 가능한 [표준 시간대 설정](https://www.php.net/manual/en/timezones.php)에서 서버의 표준 시간대를 찾습니다
1. 다음 설정을 찾아 필요한 경우 주석 처리를 제거합니다.

   ```conf
   date.timezone =
   ```

1. 2단계에서 찾은 시간대 설정을 추가합니다.

1. `memory_limit`의 값을 이 섹션의 시작 부분에서 권장되는 값 중 하나로 변경합니다.

   For example,

   ```conf
   memory_limit=2G
   ```

1. 다음 값과 일치하도록 `realpath_cache` 구성을 추가하거나 업데이트하십시오.

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.

1. 다른 `php.ini`을(를) 열고 같은 변경 내용을 적용합니다.

## OPcache 옵션 설정

`opcache.ini` 옵션을 설정하려면:

1. 텍스트 편집기에서 OPcache 구성 파일을 엽니다.

   - `opcache.ini`(CentOS)
   - `php.ini`(Ubuntu)
   - `/etc/php/8.1/fpm/php.ini`(nginx 웹 서버(CentOS 또는 Ubuntu))

1. `opcache.save_comments`을(를) 찾아 필요한 경우 주석 처리를 제거합니다.
1. 해당 값이 `1`(으)로 설정되어 있는지 확인하십시오.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 웹 서버를 다시 시작합니다.

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu 및 CentOS: `service nginx restart`

## 문제 해결

PHP 문제 해결에 대한 도움말은 다음 Adobe Commerce 지원 문서를 참조하십시오.

- 브라우저에서 Adobe Commerce에 액세스할 때 [PHP 버전 오류 또는 404 오류 발생](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP 설정 오류](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP mcrypt 확장이 제대로 설치되지 않았습니다](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP 버전 준비 확인 문제](https://support.magento.com/hc/en-us/articles/360033546411)
- [일반적인 PHP 치명적인 오류 및 해결 방법](https://support.magento.com/hc/en-us/articles/360030568432)
