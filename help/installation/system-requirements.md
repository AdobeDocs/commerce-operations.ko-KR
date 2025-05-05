---
title: 시스템 요구 사항
description: 이 참조를 사용하여 Adobe Commerce 릴리스에서 테스트한 필수 소프트웨어 종속성을 식별합니다.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ca0c47cf9882bccbc55aca786f3e6615503662f3
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 시스템 요구 사항

다음은 Adobe Commerce에서 테스트한 소프트웨어 종속성 및 서비스를 요약한 것입니다.

Commerce on Cloud의 종속성에 몇 가지 차이점이 있습니다. Adobe Commerce on Cloud에 대한 서비스 버전 및 호환성 지원은 호스팅된 클라우드 환경에 테스트되고 배포된 서비스에 의해 결정되며 경우에 따라 Adobe Commerce 온프레미스 배포에서 지원하는 버전과 다릅니다. 예를 들어 Elasticsearch 7.17은 온프레미스 배포의 경우 Commerce 2.4.4에서 지원되지만 OpenSearch 1은 클라우드의 경우 2.4.4 Adobe Commerce에서 지원됩니다.

>[!NOTE]
>
>시스템 요구 사항은 릴리스된 Adobe Commerce 버전에만 적용됩니다. Beta 또는 조기 액세스 버전은 포함되지 않습니다. 최신 버전의 Adobe Commerce에 대한 자세한 내용은 [릴리스 정보](../release/release-notes/overview.md)를 참조하세요.

다음 표는 Adobe이 특정 Adobe Commerce 릴리스에서 테스트한 타사 소프트웨어 종속성을 보여줍니다.

Adobe은 다음 표에 설명된 시스템 요구 사항의 조합만 지원합니다. 예를 들어 2.4.5는 MariaDB 10.4로 완전히 테스트됩니다. Adobe은 2.4.5로 업그레이드하기 전에 MariaDB 10.4로 업그레이드하는 것을 권장합니다.

>[!BEGINTABS]
>[!TAB 클라우드의  Commerce]

[Commerce on Cloud 템플릿](https://github.com/magento/magento-cloud)은(는) 특정 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

서비스 및 버전이 [`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)에 정의되어 있습니다. 다음은 클라우드 인프라의 Commerce 2.4.6에 대한 기본 서비스 구성입니다.

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

_클라우드 인프라의 Commerce_ 안내서에서 [서비스 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP 설정

`memory_limit` 설정과 같은 특정 PHP 구성 설정이 있으므로 Adobe Commerce 사용 시 일반적인 문제를 방지하는 데 도움이 됩니다. [필수 PHP 설정](prerequisites/php-settings.md)을 참조하세요.

클라우드 구성 지침은 _클라우드 인프라의 Commerce_ 안내서에서 [PHP 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html)을 참조하십시오.

### PHP OPcache

성능상의 이유로 [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php)이 활성화되어 있는지 확인하는 것이 좋습니다. OPcache는 많은 PHP 배포에서 사용할 수 있습니다. `opcache` 확장은 기본적으로 클라우드 인프라의 Commerce에 설치됩니다.

온-프레미스에서 PHP OPcache가 설치되어 있는지 확인하려면 [PHP 설정](prerequisites/php-settings.md)을 참조하십시오. 성능 설정에 대한 자세한 지침은 _성능 모범 사례_ 안내서에서 [PHP 설정](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings)에 대한 소프트웨어 권장 사항을 참조하십시오.

OPcache를 별도로 설치해야 하는 경우 [PHP OPcache 설명서](https://www.php.net/manual/en/opcache.setup.php)를 참조하세요.

### PHP 프로세스 제어

{{php-process-control}}

### PHPUnit

PHPUnit v9(명령줄 도구).

### 확장 프로그램

[PHP 설치 지침](prerequisites/php-settings.md)에 이러한 확장을 설치하는 단계가 포함되어 있습니다.

>[!TIP]
>
>클라우드 인프라의 PHP 확장에 대해서는 _클라우드 인프라의 Commerce_ 안내서에서 [PHP 확장 사용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions)을 참조하십시오.

>[!BEGINTABS]
>[!TAB 클라우드의  Commerce]

다음 표에서는 Adobe Commerce을 클라우드 플랫폼에 배포할 때 지원되는 PHP 확장을 보여 줍니다.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/php-extensions.md}}

설치 정보는 [공식 PHP 설명서](https://www.php.net/manual/en/extensions.php)를 참조하십시오.

>[!ENDTABS]

## 기타

이 섹션에서는 기타 모든 필수 및 선택적 소프트웨어 유형에 대한 지원 및 호환성에 대해 설명합니다.

>[!NOTE]
>
>다음 요구 사항은 Adobe Commerce의 최신 2.4.x 패치 릴리스에 적용됩니다. 관련성이 있는 경우 클라우드 인프라에 대한 Commerce 지침이 제공됩니다.

### 브라우저

Storefront 및 관리자:

- Microsoft Edge (최신 및 이전 주요 버전)
- Firefox(최신 및 이전 주요 버전, 모든 운영 체제)
- Chrome(최신 및 이전 주요 버전, 모든 운영 체제)
- Safari(최신 및 이전 주요 버전, macOS 전용)
- iOS용 Safari (storefront용 최신 및 이전 주요 버전)
- Android용 Chrome (storefront용 최신 및 이전 주요 버전)

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버. 클라우드 인프라의 Commerce은 [SendGrid 이메일 서비스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)를 사용합니다.

### 메모리

Commerce Marketplace 및 기타 소스에서 가져온 애플리케이션 및 확장을 업그레이드하려면 최대 2GB의 RAM이 필요할 수 있습니다. RAM이 2GB 미만인 시스템을 사용하는 경우 [스왑 파일](https://support.magento.com/hc/en-us/articles/360032980432)을 만드십시오. 그렇지 않으면 업그레이드가 실패할 수 있습니다.

### 운영 체제 (Linux x86-64)

RedHat Enterprise Linux(RHEL), CentOS, Ubuntu, Debian 등과 같은 Linux 배포판

Microsoft Windows 및 macOS은 **지원되지 않습니다**.

Adobe Commerce의 일부 작업에는 다음 시스템 도구가 필요합니다.

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
- TLS(전송 계층 보안) 요구 사항 - PayPal과 `repo.magento.com` 둘 다 TLS 1.2 이상이 필요합니다.

클라우드 인프라의 Commerce에 대해서는 _클라우드 인프라의 Commerce_ 안내서에서 [Fastly 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)을 참조하십시오.

### Xdebug

Adobe Commerce의 경우 [php_xdebug 2.5.x](https://xdebug.org/download) 이상을 사용합니다(개발 환경에만 해당, 성능에 부정적인 영향을 줄 수 있음).

클라우드의 Adobe Commerce에 대해서는 _클라우드 인프라의 Commerce_ 안내서에서 [Xdebug 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html)을 참조하십시오.

>[!NOTE]
>
>`xdebug`에는 Adobe Commerce 설치 또는 설치 후 상점 또는 관리자에 액세스하는 데 영향을 줄 수 있는 알려진 문제가 있습니다. _Commerce 지원 기술 자료_&#x200B;에서 [설치 `xdebug`에 영향을 주는 알려진 문제](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html)를 참조하십시오.
