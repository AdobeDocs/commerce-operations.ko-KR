---
title: 시스템 요구 사항
description: Adobe Commerce에 대한 소프트웨어 종속성 및 시스템 요구 사항에 대해 알아봅니다. 배포 환경과의 호환성에 대해서는 테스트된 구성을 참조하십시오.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-10-13
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 37a993a1f9b187dcfa74ecde581cf705eb66570d
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# 시스템 요구 사항

다음 정보에는 Adobe Commerce에서 테스트한 소프트웨어 종속성 및 서비스가 요약되어 있습니다.

Adobe Commerce on Cloud 인프라의 소프트웨어 종속성은 온프레미스 배포의 소프트웨어 종속성과 다릅니다. Adobe은 호스팅된 클라우드 환경에서 테스트되고 배포된 서비스를 기반으로 지원되는 서비스 버전 및 호환성을 결정합니다. 이러한 버전은 경우에 따라 온-프레미스 배포에 대해 지원되는 버전과 다릅니다.

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

[클라우드의 Commerce 템플릿](https://github.com/magento/magento-cloud)은(는) 각 릴리스 라인에 대해 최신 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

[`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)은(는) 기본 서비스 및 버전을 정의합니다.
*클라우드 인프라의 Commerce* 안내서에서 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0은 2026년 4월 30일에 지원 종료(EOS)되었습니다.**
이 날짜 이후, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 및 2.4.4에서는 MySQL 8.0 이후 릴리스된 MySQL 버전에 대한 호환성이나 지원을 제공하지 않습니다.
Adobe은 이러한 Commerce 릴리스에 대한 최신 MySQL 주요 버전의 유효성을 검사하거나 지원하지 않습니다.
Adobe Commerce 온-프레미스 버전 2.4.7, 2.4.6, 2.4.5 또는 2.4.4를 실행하는 경우, Adobe에서는 데이터베이스 서버를 호환되는 MariaDB 버전으로 마이그레이션하는 것이 좋습니다.

Adobe Commerce on Cloud 고객은 지원되는 버전에 대한 플랫폼 종속성을 유지해야 합니다. 라이프사이클 정책의 [플랫폼 종속성](../release/lifecycle-policy.md#platform-dependencies)을(를) 참조하십시오.

**Elasticsearch 7.17은 2026년 1월 15일에 지원 종료(EOS)되었습니다.**
이 날짜 이후, Adobe Commerce 2.4.6, 2.4.5 및 2.4.4는 Elasticsearch 7 이후 릴리스된 Elasticsearch 버전에 대한 호환성 또는 지원을 제공하지 않습니다.
Adobe은 이러한 Commerce 릴리스에 대한 최신 Elasticsearch 주요 버전의 유효성을 검사하거나 지원하지 않습니다.
Adobe Commerce 온-프레미스 버전 2.4.6, 2.4.5 또는 2.4.4를 실행하는 경우 Adobe에서는 검색 인프라를 호환되는 OpenSearch 버전으로 마이그레이션할 것을 강력히 권장합니다.

>[!ENDTABS]

## 2.4.10-alpha Commerce 릴리스 버전에 대한 시스템 요구 사항

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## 이전 Commerce 릴리스에 대한 시스템 요구 사항

다음 표에는 확장 지원의 시스템 요구 사항을 포함하여 Adobe Commerce 릴리스에 대한 시스템 요구 사항이 나와 있습니다. 이 표는 참조용으로만 사용하십시오. Adobe에서는 지원되지 않는 버전의 소프트웨어 종속성을 사용하지 않는 것이 좋습니다. Adobe 지원에서 보고된 동작을 조사, 문제 해결 또는 확인하기 전에 환경을 지원되는 구성에 맞추어야 합니다.

>[!NOTE]
>
>Adobe Commerce 2.4.6은 [2027년 8월 30일부터 &#x200B;](../release/lifecycle-policy.md#extended-support)까지 **2028년 5월 31일까지 [보안 전용 전환 기간](../release/lifecycle-policy.md#security-only-transitional-period)부터**&#x200B;까지 **추가 지원을 받습니다.**&#x200B;이 조항은 Adobe Commerce 고객만 사용할 수 있습니다. MySQL과 같은 타사 종속성에 대한 지원은 확장하지 않습니다.
>
>클라우드에서 Adobe Commerce을 실행하는 경우 **2028년 6월 1일** [보안 요구 사항 및 기한](../release/security-enforcement-policy.md) 전에 지원되는 릴리스로 업그레이드하거나 [!DNL Adobe Commerce as a Cloud Service]&#x200B;(으)로 마이그레이션해야 합니다. 전체 라이프사이클 날짜는 [지원 종료 날짜](../release/lifecycle-policy.md#end-of-support-dates) 표를 참조하십시오.
>
>이 문서의 길이를 최소화하기 위해 테이블이 축소됩니다. 확장할 헤더를 선택합니다.

+++이전 릴리스에 대한 요구 사항

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

[Commerce on Cloud 템플릿](https://github.com/magento/magento-cloud)은(는) 특정 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

[`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)은(는) 기본 서비스 및 버전을 정의합니다.
*클라우드 인프라의 Commerce* 안내서에서 [서비스 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0은 2026년 4월 30일에 지원 종료(EOS)되었습니다.**
이 날짜 이후, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 및 2.4.4에서는 MySQL 8.0 이후 릴리스된 MySQL 버전에 대한 호환성이나 지원을 제공하지 않습니다.
Adobe은 이러한 Commerce 릴리스에 대한 최신 MySQL 주요 버전의 유효성을 검사하거나 지원하지 않습니다.
Adobe Commerce 온-프레미스 버전 2.4.7, 2.4.6, 2.4.5 또는 2.4.4를 실행하는 경우, Adobe에서는 데이터베이스 서버를 호환되는 MariaDB 버전으로 마이그레이션하는 것이 좋습니다.

Adobe Commerce on Cloud 고객은 지원되는 버전에 대한 플랫폼 종속성을 유지해야 합니다. 라이프사이클 정책의 [플랫폼 종속성](../release/lifecycle-policy.md#platform-dependencies)을(를) 참조하십시오.

**Elasticsearch 7.17은 2026년 1월 15일에 지원 종료(EOS)되었습니다.**
이 날짜 이후, Adobe Commerce 2.4.6, 2.4.5 및 2.4.4는 Elasticsearch 7 이후 릴리스된 Elasticsearch 버전에 대한 호환성 또는 지원을 제공하지 않습니다.
Adobe은 이러한 Commerce 릴리스에 대한 최신 Elasticsearch 주요 버전의 유효성을 검사하거나 지원하지 않습니다.
Adobe Commerce 온-프레미스 버전 2.4.6, 2.4.5 또는 2.4.4를 실행하는 경우 Adobe에서는 검색 인프라를 호환되는 OpenSearch 버전으로 마이그레이션할 것을 강력히 권장합니다.

>[!ENDTABS]

+++

## PHP 설정

Adobe Commerce 사용 시 일반적인 문제를 방지하기 위해 `memory_limit`과(와) 같은 PHP 설정을 구성합니다. [필수 PHP 설정](prerequisites/php-settings.md)을 참조하세요.

클라우드 구성 지침은 *클라우드 인프라의 Commerce* 안내서에서 [PHP 설정](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)을 참조하십시오.

### PHP OPcache

Adobe에서는 성능을 개선하기 위해 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php)이(가) 활성화되어 있는지 확인하는 것이 좋습니다. 많은 PHP 배포는 OPcache를 활성화합니다.

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

Adobe Commerce은 해당되는 경우를 제외하고 storefront 및 Admin에 대해 다음 브라우저의 최신 및 이전 주요 버전을 지원합니다.

- Microsoft Edge
- Firefox(모든 운영 체제)
- Chrome(모든 운영 체제)
- Safari(macOS만 해당)
- iOS용 Safari(상점 전용)
- Android용 Chrome(상점 첫 화면 전용)

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버. 클라우드 인프라의 Commerce은 [SendGrid 이메일 서비스](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)를 사용합니다.

### 메모리

Commerce Marketplace 및 기타 소스에서 애플리케이션과 확장을 업그레이드하려면 최대 2GB의 RAM이 필요할 수 있습니다. 시스템의 RAM이 2GB 미만이면 [스왑 파일을 만듭니다](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). 스왑 파일이 없으면 업그레이드가 실패할 수 있습니다.

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

Adobe Commerce 개발 환경의 경우에만 [php_xdebug 2.5.x](https://xdebug.org/download) 이상을 사용하십시오. Xdebug는 성능에 부정적인 영향을 줄 수 있습니다.

클라우드의 Adobe Commerce에 대해서는 *클라우드 인프라의 Commerce* 안내서에서 [Xdebug 구성](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)을 참조하십시오.

>[!NOTE]
>
>Xdebug의 알려진 문제는 Adobe Commerce 설치 또는 설치 후 상점 또는 관리자에 대한 액세스에 영향을 줄 수 있습니다. _Commerce 지원 기술 자료_&#x200B;에서 [설치 `xdebug`에 영향을 주는 알려진 문제](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)를 참조하십시오.

<!-- Last updated from includes: 2026-10-13 09:11:06 -->
