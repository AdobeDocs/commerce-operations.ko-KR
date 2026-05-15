---
title: 시스템 요구 사항
description: Adobe Commerce에 대한 소프트웨어 종속성 및 시스템 요구 사항에 대해 알아봅니다. 배포 환경과의 호환성에 대해서는 테스트된 구성을 참조하십시오.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 77981e3078ddfb87c40419f435086c7e173528b1
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# 시스템 요구 사항

다음 정보에는 Adobe Commerce에서 테스트한 소프트웨어 종속성 및 서비스가 요약되어 있습니다.

Commerce on Cloud의 종속성에 몇 가지 차이점이 있습니다. Adobe Commerce on Cloud에 대한 서비스 버전 및 호환성 지원은 호스팅된 클라우드 환경에 테스트되고 배포된 서비스에 의해 결정되며 경우에 따라 Adobe Commerce 온프레미스 배포에서 지원하는 버전과 다릅니다.

>[!IMPORTANT]
>
>시스템 요구 사항 표에는 베타 또는 조기 액세스로 레이블이 지정된 릴리스를 포함하여 적용되는 Adobe Commerce 버전이 나열됩니다.
>게시된 최신 Commerce 버전에 대한 [릴리스 정보](../release/release-notes/overview.md)를 참조하세요.
>
>서비스 버전이 Commerce 버전에 대해 지원되는 구성과 일치하지 않으면 Adobe에서 테스트할 수 있는 동작과 다를 수 있습니다. Adobe 지원에서 보고된 비헤이비어를 조사, 문제 해결 또는 확인하기 전에 환경을 지원되는 구성에 맞추도록 요청할 수 있습니다. 환경을 맞춤화한 후 Adobe 지원 센터에서 조사를 계속할 수 있습니다.

다음 표는 Adobe이 특정 Adobe Commerce 릴리스에서 테스트한 타사 소프트웨어 종속성을 보여줍니다.

Adobe은 다음 표에 나열된 시스템 요구 사항 조합만 지원합니다. Adobe은 나열된 조합과 일치하지 않는 구성을 확인하거나 지원하지 않습니다. 예를 들어 Adobe Commerce 2.4.9는 MariaDB 12.3으로 테스트됩니다. 2.4.9로 업그레이드하기 전에 MariaDB 12.3으로 업그레이드하십시오.

## 최신 Commerce 릴리스 버전에 대한 시스템 요구 사항

다음 표에서는 지원되는 모든 Commerce 버전의 최신 릴리스에 대한 시스템 요구 사항을 요약합니다. Adobe은 모든 고객에게 이러한 버전으로 업그레이드할 것을 권장합니다.

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

[Commerce on Cloud 템플릿](https://github.com/magento/magento-cloud)은(는) 특정 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

기본 구성의 경우 서비스 및 버전은 [`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)에 정의되어 있습니다.
자세한 내용은 *Commerce on Cloud Infrastructure* 안내서의 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0은 2026년 4월 30일에 지원 종료(EOS)되었습니다.**
이 날짜 이후에 Adobe Commerce 2.4.7, 2.4.6, 2.4.5 및 2.4.4는 호환성을 제공하지 않거나
mySQL 8.0 이후 릴리스된 모든 MySQL 버전에 대한 지원 Adobe은
이 Adobe에서 최신 MySQL 주요 버전의 유효성을 검사하거나 지원을 제공합니다.
Commerce 릴리스 라인.
버전 2.4.7, 2.4.6, 2.4.5, 2.4.4를 실행하는 모든 Adobe Commerce 온-프레미스 고객은 강력하게
데이터베이스 서버를 호환 가능한 MariaDB 버전으로 마이그레이션하는 것이 좋습니다.

**Elasticsearch 7.17은 2026년 1월 15일에 지원 종료(EOS)되었습니다.**
이 날짜 이후에 Adobe Commerce 2.4.6, 2.4.5 및 2.4.4는 호환성을 제공하지 않거나
Elasticsearch 7 이후 릴리스된 모든 Elasticsearch 버전에 대한 지원. Adobe은
이 Adobe에서 최신 Elasticsearch 주요 버전의 유효성을 검사하거나 지원을 제공합니다.
Commerce 릴리스 라인.
버전 2.4.6, 2.4.5, 2.4.4를 실행하는 모든 Adobe Commerce 온-프레미스 고객은 강력하게
는 검색 인프라를 호환 가능한 OpenSearch 버전으로 마이그레이션하는 것이 좋습니다.

>[!ENDTABS]

>[!AVAILABILITY]
>
>MariaDB 12.3의 공식 릴리스 이후 MariaDB 12.3과 Adobe Commerce 2.4.9 간의 <sup>1</sup> 호환성이 확인되며, 이는 5~6월에 제공될 예정입니다.

## 이전 Commerce 릴리스에 대한 시스템 요구 사항

다음 표에는 확장 지원에 포함된 Adobe Commerce 릴리스에 대한 시스템 요구 사항이 나와 있습니다. 이 테이블은 참조용으로만 제공됩니다. Adobe에서는 지원되지 않는 버전의 소프트웨어 종속성을 사용하는 것을 권장하지 않습니다. 지원 센터에서는 보고된 동작을 조사, 문제 해결 또는 확인하기 전에 환경을 지원되는 구성에 맞추어야 합니다.

>[!NOTE]
>
>이 문서의 길이를 최소화하기 위해 테이블이 축소됩니다. 확장할 헤더를 선택합니다.

+++이전 릴리스에 대한 요구 사항

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

[Commerce on Cloud 템플릿](https://github.com/magento/magento-cloud)은(는) 특정 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

기본 구성의 경우 서비스 및 버전은 [`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)에 정의되어 있습니다.
자세한 내용은 *Commerce on Cloud Infrastructure* 안내서의 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0은 2026년 4월 30일에 지원 종료(EOS)되었습니다.**
이 날짜 이후에 Adobe Commerce 2.4.7, 2.4.6, 2.4.5 및 2.4.4는 호환성을 제공하지 않거나
mySQL 8.0 이후 릴리스된 모든 MySQL 버전에 대한 지원 Adobe은
이 Adobe에서 최신 MySQL 주요 버전의 유효성을 검사하거나 지원을 제공합니다.
Commerce 릴리스 라인.
버전 2.4.7, 2.4.6, 2.4.5, 2.4.4를 실행하는 모든 Adobe Commerce 온-프레미스 고객은 강력하게
데이터베이스 서버를 호환 가능한 MariaDB 버전으로 마이그레이션하는 것이 좋습니다.

**Elasticsearch 7.17은 2026년 1월 15일에 지원 종료(EOS)되었습니다.**
이 날짜 이후에 Adobe Commerce 2.4.6, 2.4.5 및 2.4.4는 호환성을 제공하지 않거나
Elasticsearch 7 이후 릴리스된 모든 Elasticsearch 버전에 대한 지원. Adobe은
이 Adobe에서 최신 Elasticsearch 주요 버전의 유효성을 검사하거나 지원을 제공합니다.
Commerce 릴리스 라인.
버전 2.4.6, 2.4.5, 2.4.4를 실행하는 모든 Adobe Commerce 온-프레미스 고객은 강력하게
는 검색 인프라를 호환 가능한 OpenSearch 버전으로 마이그레이션하는 것이 좋습니다.

>[!ENDTABS]

+++

## PHP 설정

`memory_limit` 설정과 같은 특정 PHP 구성 설정이 있으므로 Adobe Commerce 사용 시 일반적인 문제를 방지하는 데 도움이 됩니다. [필수 PHP 설정](prerequisites/php-settings.md)을 참조하세요.

클라우드 구성 지침은 *클라우드 인프라의 Commerce* 안내서에서 [PHP 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)을 참조하십시오.

### PHP OPcache

Adobe에서는 성능상의 이유로 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php)이 활성화되어 있는지 확인할 것을 권장합니다. OPcache는 많은 PHP 배포에서 사용할 수 있습니다.

- **클라우드 인프라의 Adobe Commerce 배포**&#x200B;의 경우 `opcache` 확장이 기본적으로 설치됩니다.
- **Adobe Commerce 온-프레미스 배포의 경우:**
   - [PHP OPcache 확장이 설치되어 있는지 확인](prerequisites/php-settings.md#verify-php-is-installed).
   - 성능 설정에 대한 구체적인 지침은 *성능 모범 사례* 안내서에서 [PHP 설정](../performance/software.md#php-settings)에 대한 소프트웨어 권장 사항을 참조하십시오.


OPcache를 별도로 설치해야 하는 경우 [PHP OPcache 설명서](https://www.php.net/manual/en/opcache.setup.php)를 참조하세요.

### PHP 프로세스 제어

{{php-process-control}}

### PHPUnit

지원되는 PHPUnit 메이저 버전은 Adobe Commerce 릴리스에 따라 다릅니다. Adobe은 PHPUnit 12로 2.4.9, PHPUnit 10으로 2.4.8-p5, PHPUnit 9로 2.4.7-p10~2.4.4-p18을 테스트합니다. 릴리스에 대해 Adobe에서 테스트한 구성과 일치하는 주요 버전에 명령줄 도구로 PHPUnit를 설치합니다.

### 확장 프로그램

[PHP 설치 지침](prerequisites/php-settings.md)에 이러한 확장을 설치하는 단계가 포함되어 있습니다.

>[!TIP]
>
>클라우드 인프라의 PHP 확장에 대해서는 _클라우드 인프라의 Commerce_ 안내서에서 [PHP 확장 사용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)을 참조하십시오.

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

다음 표에서는 Adobe Commerce을 클라우드 플랫폼에 배포할 때 지원되는 PHP 확장을 보여 줍니다.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/php-extensions.md}}

설치 정보는 [공식 PHP 설명서](https://www.php.net/manual/en/extensions.php)를 참조하십시오.

>[!ENDTABS]

## 기타 소프트웨어 요구 사항

이 섹션에서는 기타 모든 필수 및 선택적 소프트웨어 유형에 대한 지원 및 호환성에 대해 설명합니다.

>[!NOTE]
>
>다음 요구 사항은 Adobe Commerce의 최신 2.4.x 패치 릴리스에 적용됩니다. 관련성이 있는 경우 클라우드 인프라에 대한 Commerce 지침이 제공됩니다.

### 브라우저

Storefront 및 관리자:

- Microsoft Edge (최신 및 이전 주요 버전)
- Firefox(모든 운영 체제에서 최신 및 이전 주요 버전)
- Chrome(모든 운영 체제에서 최신 및 이전 주요 버전)
- Safari(macOS에서만 최신 및 이전 주요 버전)
- iOS용 Safari(상점 첫 화면의 최신 및 이전 주요 버전)
- Android용 Chrome (storefront의 최신 및 이전 주요 버전)

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버. 클라우드 인프라의 Commerce은 [SendGrid 이메일 서비스](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)를 사용합니다.

### 메모리

Commerce Marketplace 및 기타 소스에서 가져온 애플리케이션 및 확장을 업그레이드하려면 최대 2GB의 RAM이 필요할 수 있습니다. RAM이 2GB 미만인 시스템을 사용하는 경우 [스왑 파일](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)을 만듭니다. 그렇지 않으면 업그레이드가 실패할 수 있습니다.

### 운영 체제 (Linux x86-64)

Red Hat Enterprise Linux(RHEL), CentOS, Ubuntu, Debian 등과 같은 Linux 배포판

Microsoft Windows 및 macOS은 **지원되지 않습니다**.

Adobe Commerce의 일부 작업에는 다음 시스템 도구가 필요합니다.

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- HTTPS에는 유효한 보안 인증서가 필요합니다.
- 자체 서명된 SSL 인증서는 지원되지 않습니다.
- TLS(전송 계층 보안) 요구 사항 - PayPal과 `repo.magento.com` 둘 다 TLS 1.2 이상이 필요합니다.

클라우드 인프라의 Commerce에 대해서는 *클라우드 인프라의 Commerce* 안내서에서 [Fastly 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)을 참조하십시오.

### Xdebug

Adobe Commerce의 경우 [php_xdebug 2.5.x](https://xdebug.org/download) 이상을 사용합니다(개발 환경에만 해당, 성능에 부정적인 영향을 줄 수 있음).

클라우드의 Adobe Commerce에 대해서는 *클라우드 인프라의 Commerce* 안내서에서 [Xdebug 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)을 참조하십시오.

>[!NOTE]
>
>`xdebug`에는 Adobe Commerce 설치 또는 설치 후 상점 또는 관리자에 액세스하는 데 영향을 줄 수 있는 알려진 문제가 있습니다. _Commerce 지원 기술 자료_&#x200B;에서 [설치 `xdebug`에 영향을 주는 알려진 문제](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)를 참조하십시오.

<!-- Last updated from includes: 2026-05-11 20:38:54 -->
