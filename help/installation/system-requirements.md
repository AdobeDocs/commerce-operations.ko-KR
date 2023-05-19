---
title: 시스템 요구 사항
description: 이 참조를 사용하여 Adobe Commerce 및 Magento Open Source 릴리스에서 테스트한 필수 소프트웨어 종속성을 식별합니다.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# 시스템 요구 사항

이 표에서는 Adobe이 특정 Adobe Commerce 및 Magento Open Source 릴리스에서 테스트한 타사 소프트웨어 종속성 버전을 보여 줍니다. Adobe은 다음 표에 설명된 시스템 요구 사항의 조합만 지원합니다.

예를 들어 2.4.5는 MariaDB 10.4로 완전히 테스트됩니다. Adobe은 2.4.5로 업그레이드하기 전에 MariaDB 10.4로 업그레이드하는 것을 권장합니다.

{{$include /help/_includes/templated/system-requirements-table.md}}

## 기타

이 섹션에서는 기타 모든 필수 및 선택적 소프트웨어 유형에 대한 지원 및 호환성에 대해 설명합니다.

>[!NOTE]
>
>다음 요구 사항은 Adobe Commerce 및 Magento Open Source의 최신 2.4.x 패치 릴리스에 적용됩니다.

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버

### 운영 체제 (Linux x86-64)

RedHat Enterprise Linux(RHEL), CentOS, Ubuntu, Debian 등과 같은 Linux 배포판 Microsoft Windows 및 macOS은 지원되지 않습니다.

### 확장 프로그램

>[!NOTE]
>
>다음 [PHP 설치 지침](prerequisites/php-settings.md) 이러한 확장을 설치하는 단계를 포함합니다.

{{$include /help/_includes/templated/php-extensions.md}}

을(를) 참조하십시오 [공식 PHP 설명서](https://php.net/manual/en/extensions.php) 자세한 내용은 여기를 참조하십시오.

### PHP OPcache

다음을 확인하는 것이 좋습니다. [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 은(는) 성능상의 이유로 활성화됩니다. OPcache는 많은 PHP 배포에서 사용할 수 있습니다. 설치되어 있는지 확인하려면 다음을 참조하십시오. [PHP 설명서](prerequisites/php-settings.md).

별도로 설치해야 하는 경우 다음을 참조하십시오. [PHP OPcache 설명서](https://php.net/manual/en/opcache.setup.php).

### PHP 설정

다음과 같은 특정 PHP 구성 설정을 권장합니다. `memory_limit`: Adobe Commerce 및 Magento Open Source을 사용할 때 발생할 수 있는 일반적인 문제를 방지할 수 있습니다.

자세한 내용은 [필수 PHP 설정](prerequisites/php-settings.md).

### PHPUnit

PHPUnit(명령줄 도구) 9.0.0

### RAM

Commerce Marketplace 및 기타 소스에서 얻은 응용 프로그램 및 확장을 업그레이드하려면 최대 2GB의 RAM이 필요할 수 있습니다. RAM이 2GB 미만인 시스템을 사용하는 경우 [파일 교체](https://support.magento.com/hc/en-us/articles/360032980432); 그렇지 않으면 업그레이드가 실패할 수 있습니다.

### 시스템 종속성

Adobe Commerce 및 Magento Open Source의 일부 작업을 위해서는 다음 시스템 도구가 필요합니다.

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS에는 유효한 보안 인증서가 필요합니다.
- 자체 서명된 SSL 인증서는 지원되지 않습니다.
- TLS(전송 계층 보안) 요구 사항 - PayPal 및 `repo.magento.com` 둘 다 TLS 1.2 이상이 필요합니다.

### 지원되는 브라우저

Storefront 및 관리자:

- Microsoft Edge(최신 및 이전 주요 버전)
- Firefox(최신 및 이전 주요 버전, 모든 운영 체제)
- Chrome(최신 및 이전 주요 버전, 모든 운영 체제)
- Safari(최신 및 이전 주요 버전, macOS 전용)
- iPad 2, iPad Mini, iPad 및 Retina 디스플레이(iOS 12 이상)용 Safari Mobile(데스크탑 상점)
- iPhone 6 이상용 Safari Mobile; 모바일 상점 앞용 iOS 12 이상
- 모바일용 Chrome(최신 및 이전 주요 버전) [Android 4 이상] 모바일 상점 용)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 또는 이후 버전(개발 환경에만 해당되며 성능에 부정적인 영향을 미칠 수 있음)

>[!NOTE]
>
>에 대해 알려진 문제 있음 `xdebug` 이는 Adobe Commerce 또는 Magento Open Source 설치 또는 설치 후 상점 또는 관리자에 대한 액세스에 영향을 줄 수 있습니다. 자세한 내용은 [xdebug의 알려진 문제](https://support.magento.com/hc/en-us/articles/360034242212).
