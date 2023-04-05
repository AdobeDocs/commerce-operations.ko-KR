---
title: PHP 설정
description: 다음 단계에 따라 필요한 PHP 확장을 설치하고 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 필요한 PHP 설정을 구성합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---


# PHP 설정

이 항목에서는 필요한 PHP 옵션을 설정하는 방법을 설명합니다.

>[!NOTE]
>
>자세한 내용은 [시스템 요구 사항](../system-requirements.md) 지원되는 버전의 PHP에 대해 설명합니다.

## PHP가 설치되어 있는지 확인

대부분의 Linux 버전에는 기본적으로 PHP가 설치되어 있습니다. 이 항목에서는 이미 PHP를 설치했다고 가정합니다. PHP가 이미 설치되어 있는지 확인하려면 명령줄에서 다음을 입력합니다.

```bash
php -v
```

PHP가 설치되어 있으면 다음과 유사한 메시지가 표시됩니다.

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce 및 Magento Open Source 2.4는 PHP 7.3과 호환되지만 PHP 7.4를 사용하여 테스트하고 사용하는 것이 좋습니다.

PHP가 설치되어 있지 않거나 버전 업그레이드가 필요한 경우 특정 Linux 버전에 대한 지침에 따라 설치하십시오.
CentOS에서 [추가적인 단계가 필요할 수 있습니다](https://wiki.centos.org/HowTos/php7).

## 설치된 확장 확인

Adobe Commerce 및 Magento Open Source을 사용하려면 확장 세트를 설치해야 합니다.

{{$include /help/_includes/templated/php-extensions.md}}

설치된 확장을 확인하려면:

1. 설치된 모듈을 나열합니다.

   ```bash
   php -m
   ```

1. 필요한 모든 확장이 설치되어 있는지 확인합니다.
1. PHP를 설치하는 데 사용되는 것과 동일한 워크플로우를 사용하여 누락된 모듈을 추가합니다. 예를 들어 `yum` PHP를 설치하기 위해 PHP 7.4 모듈을 다음과 같이 추가할 수 있습니다.

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## PHP 설정 확인

>[!WARNING]
>
>PHP 7.4.20을 사용하는 경우 `pcre.jit=0` 다음 위치에서 `php.ini` 파일. PHP에 영향을 줍니다 [버그](https://bugs.php.net/bug.php?id=81101) CSS가 로드되지 않도록 합니다.

- PHP에 대한 시스템 시간대를 설정합니다. 그렇지 않으면 설치 중에 다음 표시와 같은 오류와 크론과 같은 시간 관련 작업이 작동하지 않을 수 있습니다.

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- PHP 메모리 제한을 설정합니다.

   자세한 권장 사항은 다음과 같습니다.

   - 코드를 컴파일하거나 정적 자산을 배포합니다. `1G`
   - 디버깅, `2G`
   - 테스트, `~3-4G`

- PHP 값을 늘립니다 `realpath_cache_size` 및 `realpath_cache_ttl` 권장 설정을 사용하려면 다음을 수행하십시오.

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   이러한 설정을 사용하면 PHP 프로세스가 페이지가 로드될 때마다 경로를 찾는 대신 파일에 대한 경로를 캐싱할 수 있습니다. 자세한 내용은 [성능 조정](https://www.php.net/manual/en/ini.core.php) PHP 설명서에서 참조할 수 있습니다.

- 활성화 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments): Adobe Commerce 및 Magento Open Source 2.1 이상에 필요합니다.

   을 활성화하는 것이 좋습니다 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) 성능상의 이유로. 많은 PHP 배포에서 OPcache가 활성화되어 있습니다.

   Adobe Commerce 및 Magento Open Source 2.1 이상에서는 코드 생성을 위해 PHP 코드 주석을 사용합니다.

>[!NOTE]
>
>설치 및 업그레이드 중에 문제가 발생하지 않도록 PHP 명령줄 구성과 PHP 웹 서버 플러그인 구성 모두에 동일한 PHP 설정을 적용하는 것이 좋습니다. 자세한 내용은 다음 섹션을 참조하십시오.

## PHP 구성 파일 찾기

이 섹션에서는 필요한 설정을 업데이트하는 데 필요한 구성 파일을 찾는 방법을 설명합니다.

### 찾기 `php.ini` 구성 파일

웹 서버 구성을 찾으려면 [`phpinfo.php` 파일](optional-software.md#create-phpinfophp) 웹 브라우저에서 `Loaded Configuration File` 아래와 같이 변경하는 것을 의미합니다.

![PHP 정보 페이지](../../assets/installation/config_phpini-webserver.png)

PHP 명령줄 구성을 찾으려면 를 입력합니다.

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>하나만 있으면 `php.ini` 파일을 만들면 해당 파일을 변경할 수 있습니다. 두 개 있으면 `php.ini` 파일에서 *모두* 파일. 이렇게 하지 않으면 예기치 않은 성능이 발생할 수 있습니다.

### OPcache 구성 설정 찾기

PHP OPcache 설정은 일반적으로 `php.ini` 또는 `opcache.ini`. 위치는 운영 체제와 PHP 버전에 따라 달라질 수 있습니다. OPcache 구성 파일에 `opcache` 섹션 또는 설정 `opcache.enable`.

다음 지침을 사용하여 찾으십시오.

- Apache 웹 서버:

   Apache가 있는 Ubuntu의 경우 OPcache 설정은 일반적으로 `php.ini` 파일.

   Apache 또는 nginx가 있는 CentOS의 경우 OPcache 설정은 일반적으로 다음 위치에 있습니다. `/etc/php.d/opcache.ini`

   없는 경우 다음 명령을 사용하여 찾습니다.

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- PHP-FPM이 있는 nginx 웹 서버: `/etc/php/7.2/fpm/php.ini`

두 개 이상이면 `opcache.ini`를 눌러 모두 수정합니다.

## PHP 옵션을 설정하는 방법

PHP 옵션을 설정하려면 다음을 수행합니다.

1. 열기 `php.ini` 텍스트 편집기에서 을 참조하십시오.
1. 사용 가능한 시간대에서 서버의 시간대를 찾습니다. [시간대 설정](https://www.php.net/manual/en/timezones.php)
1. 다음 설정을 찾아 필요한 경우 주석 처리를 취소합니다.

   ```conf
   date.timezone =
   ```

1. 2단계에서 찾은 시간대 설정을 추가합니다.

1. 값 변경 `memory_limit` 이 섹션의 시작 부분에서 권장되는 값 중 하나로 이동합니다.

   예,

   ```conf
   memory_limit=2G
   ```

1. 추가 또는 업데이트 `realpath_cache` 다음 값과 일치하도록 구성:

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

1. 다른 항목을 엽니다. `php.ini` (다른 경우) 및에서 동일한 변경 작업을 수행합니다.

## OPcache 옵션 설정

설정하려면 `opcache.ini` 옵션:

1. 텍스트 편집기에서 OPcache 구성 파일을 엽니다.

   - `opcache.ini` (CentOS)
   - `php.ini` (우분투)
   - `/etc/php/7.2/fpm/php.ini` (nginx 웹 서버(CentOS 또는 Ubuntu))

1. 찾기 `opcache.save_comments` 필요한 경우 주석 처리를 해제합니다.
1. 값이 `1`.
1. 변경 사항을 저장하고 텍스트 편집기를 종료합니다.
1. 웹 서버를 다시 시작합니다.

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu 및 CentOS: `service nginx restart`

## 문제 해결

PHP 문제 해결에 대한 도움말은 다음 Adobe Commerce 지원 문서를 참조하십시오.

- [브라우저에서 Adobe Commerce에 액세스할 때 PHP 버전 오류 또는 404 오류](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP 설정 오류](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP Mcrypt 확장이 제대로 설치되지 않았습니다.](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP 버전 준비 검사 문제](https://support.magento.com/hc/en-us/articles/360033546411)
- [일반적인 PHP 오류 및 솔루션](https://support.magento.com/hc/en-us/articles/360030568432)
