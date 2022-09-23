---
title: 시스템 요구 사항
description: 이 참조를 사용하여 Adobe Commerce 및 Magento Open Source 릴리스에서 테스트한 필수 소프트웨어 종속성을 식별합니다.
source-git-commit: df8240b71efe992bc1c0655aa30c32778297a3c6
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# 시스템 요구 사항

이 표는 Adobe이 특정 Adobe Commerce 및 Magento Open Source 릴리스에서 테스트한 타사 소프트웨어 종속성 버전을 보여줍니다. Adobe은 다음 표에 설명된 시스템 요구 사항의 조합만 지원합니다.

예를 들어 2.4.3은 MariaDB 10.4에서 완전히 테스트되었습니다. Adobe은 2.4.3으로 업그레이드하기 전에 MariaDB 10.4로 업그레이드할 것을 권장합니다.

{{$include /help/_includes/templated/system-requirements-table.md}}

## 기타

이 섹션에서는 다른 모든 유형의 필수 및 선택적 소프트웨어에 대한 지원 및 호환성을 설명합니다.

>[!NOTE]
>
>다음 요구 사항은 Adobe Commerce 및 Magento Open Source의 최신 2.4.x 패치 릴리스에 적용됩니다.

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버

### 운영 체제(Linux x86-64)

RedHat Enterprise Linux(RHEL), CentOS, Ubuntu, Debian 등과 같은 Linux 배포판. Microsoft Windows 및 macOS은 지원되지 않습니다.

### PHP 확장

>[!NOTE]
>
>다음 [PHP 설치 지침](prerequisites/php-settings.md) 이러한 확장을 설치하는 단계를 포함합니다.

{{$include /help/_includes/templated/php-extensions.md}}

을(를) 참조하십시오. [공식 PHP 설명서](https://php.net/manual/en/extensions.php) 를 참조하십시오.

### PHP OPcache

다음 사항을 확인하는 것이 좋습니다 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 성능상의 이유로 이 활성화되어 있습니다. 많은 PHP 배포에서 OPcache가 활성화되어 있습니다. 설치되어 있는지 확인하려면 [PHP 설명서](prerequisites/php-settings.md).

별도로 설치해야 하는 경우 [PHP OPcache 설명서](https://php.net/manual/en/opcache.setup.php).

### PHP 설정

다음과 같은 특정 PHP 구성 설정을 사용하는 것이 좋습니다 `memory_limit`로 설정되면 Adobe Commerce 및 Magento Open Source 사용 시 일반적인 문제가 발생하지 않습니다.

자세한 내용은 [필수 PHP 설정](prerequisites/php-settings.md).

### PHPUnit

PHPUnit(명령줄 도구) 9.0.0

### RAM

Commerce Marketplace 및 기타 소스에서 가져오는 응용 프로그램 및 확장을 업그레이드하려면 최대 2GB의 RAM이 필요할 수 있습니다. 2GB 미만의 RAM을 사용하는 경우 [스왑 파일](https://support.magento.com/hc/en-us/articles/360032980432); 그렇지 않으면 업그레이드가 실패할 수 있습니다.

### 시스템 종속성

Adobe Commerce 및 Magento Open Source은 일부 작업에 대해 다음 시스템 도구가 필요합니다.

- [bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [slof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [myqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [친절해](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [사용](https://www.gnu.org/software/sed/manual/sed.html)
- [tar](https://linux.die.net/man/1/tar)

### SSL

- 유효한 [보안 인증서](https://glossary.magento.com/security-certificate) 은 HTTPS에 필요합니다.
- 자체 서명된 SSL 인증서는 지원되지 않습니다.
- TLS(전송 계층 보안) 요구 사항 - PayPal 및 `repo.magento.com` 둘 다 TLS 1.2 이상이 필요합니다.

### 지원되는 브라우저

저장소 및 관리자:

- Microsoft Edge(최신 및 이전 주요 버전)
- Firefox(최신 및 이전 주요 버전) 모든 운영 체제)
- Chrome(최신 및 이전 주요 버전) 모든 운영 체제)
- Safari(최신 및 이전 주요 버전; macOS 전용)
- 데스크탑 스토어용 iPad 2, iPad Mini, Retina 디스플레이가 포함된 iPad(iOS 12 이상)
- iPhone 6 이상용 Safari Mobile 모바일 스토어프런트용 iOS 12 이상
- 모바일용 Chrome(최신 및 이전 주요 버전) [Android 4 이상] mobile storefront용)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 또는 이후 버전(개발 환경만) 성능에 부정적인 영향을 줄 수 있음)

>[!NOTE]
>
>에 알려진 문제가 있습니다 `xdebug` Adobe Commerce 또는 Magento Open Source 설치나 설치 후 상점 또는 관리자에 액세스할 수 있습니다. 자세한 내용은 [xdebug의 알려진 문제](https://support.magento.com/hc/en-us/articles/360034242212).
