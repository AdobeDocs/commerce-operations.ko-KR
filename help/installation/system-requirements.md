---
title: 시스템 요구 사항
description: Adobe Commerce의 소프트웨어 종속성 및 시스템 요구 사항에 대해 알아봅니다. 테스트를 거친 구성을 검색하여 배포 환경과의 호환성을 보장합니다.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 시스템 요구 사항

다음은 Adobe Commerce에서 테스트한 소프트웨어 종속성 및 서비스를 요약한 것입니다.

클라우드에서의 Commerce에 대한 종속성에는 몇 가지 차이점이 있습니다. Adobe Commerce on Cloud에 대한 서비스 버전 및 호환성 지원은 호스팅된 클라우드 환경에 테스트 및 배포되는 서비스에 의해 결정되며, Adobe Commerce 온-프레미스 배포에서 지원하는 버전과 다를 수도 있습니다. 예를 들어, Elasticsearch 7.17은 Commerce 2.4.4에서 온-프레미스 배포가 지원되지만 OpenSearch 1은 2.4.4 Adobe Commerce on Cloud에서 지원됩니다.

>[!NOTE]
>
>시스템 요구 사항 테이블은 명시적으로 베타 또는 초기 액세스 릴리스를 포함하여 적용되는 특정 Adobe Commerce 버전을 식별합니다. 최신 버전의 Adobe Commerce에 대한 자세한 내용은 [릴리스 노트](../release/release-notes/overview.md)를 참조하십시오.

다음 표에서는 Adobe에서 특정 Adobe Commerce 릴리스에서 테스트한 타사 소프트웨어 종속성의 버전을 보여 줍니다.

Adobe은 다음 표에 설명된 시스템 요구 사항의 조합만 지원합니다. 예를 들어 2.4.5는 MariaDB 10.4로 완전히 테스트됩니다. Adobe은 2.4.5로 업그레이드하기 전에 MariaDB 10.4로 업그레이드하는 것을 권장합니다.

원활한 업그레이드 프로세스를 보장하고 배포 실패를 방지하기 위해 Adobe에서는 RabbitMQ 버전을 점진적으로 업그레이드할 것을 권장합니다. 예를 들어 버전 3.8에서 4.1로 업그레이드할 때 먼저 3.8에서 3.9로 업그레이드한 다음 3.9에서 3.10으로 업그레이드해야 합니다. 버전 3.13에 도달한 후에만 버전 4.1로 업그레이드해야 합니다.

>[!BEGINTABS]

>[!TAB 클라우드의  Commerce]

[Commerce on Cloud 템플릿](https://github.com/magento/magento-cloud)은(는) 특정 Commerce 버전과 호환되는 서비스에 대한 기본 구성을 제공합니다.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

서비스 및 버전은 [`services.yaml` 파일](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)에 정의되어 있습니다. 클라우드 인프라에서 Commerce 2.4.6에 대한 기본 서비스 구성은 다음과 같습니다.

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

[클라우드 인프라의 Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) 안내서에서 *서비스 구성*&#x200B;을 참조하십시오.

>[!TAB Commerce 온-프레미스]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP 설정

`memory_limit` 설정과 같은 특정 PHP 구성 설정이 있으므로 Adobe Commerce 사용 시 일반적인 문제를 방지하는 데 도움이 됩니다. [필수 PHP 설정](prerequisites/php-settings.md)을 참조하세요.

클라우드 구성 지침은 [클라우드 인프라의 상거래](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) 가이드의 *PHP 설정*&#x200B;을 참조하십시오.

### PHP OP캐시

성능상의 이유로 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php)이(가) 활성화되어 있는지 확인하는 것이 좋습니다. OPcache는 많은 PHP 배포에서 활성화됩니다.
- **Adobe Commerce on Cloud 인프라 배포**&#x200B;의 경우 `opcache` 확장이 기본적으로 설치됩니다.
- **Adobe Commerce 온-프레미스 배포의 경우:**
   - [PHP OPcache 확장이 설치되어 있는지 확인](prerequisites/php-settings.md#verify-php-is-installed).
   - 성능 설정에 대한 구체적인 지침은 [성능 모범 사례](../performance/software.md#php-settings) 안내서에서 *PHP 설정*&#x200B;에 대한 소프트웨어 권장 사항을 참조하십시오.


OPcache를 별도로 설치해야 하는 경우 [PHP OPcache 설명서](https://www.php.net/manual/en/opcache.setup.php)를 참조하세요.

### PHP 프로세스 제어

{{php-process-control}}

### PHPUnit

PHPUnit v9(명령줄 도구로)

### PHP 확장

[PHP 설치 지침](prerequisites/php-settings.md)에는 이러한 확장을 설치하는 단계가 포함되어 있습니다.

>[!TIP]
>
>클라우드 인프라의 PHP 확장에 대해서는 [클라우드 인프라의 상거래](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) 가이드에서 _PHP 확장 사용_&#x200B;을 참조하십시오.

>[!BEGINTABS]

>[!TAB 클라우드의 상거래]

다음 표에서는 Adobe Commerce을 클라우드 플랫폼에 배포할 때 지원되는 PHP 확장을 보여 줍니다.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB 온-프레미스 상거래]

{{$include /help/_includes/templated/php-extensions.md}}

설치에 대한 자세한 내용은 [공식 PHP 설명서](https://www.php.net/manual/en/extensions.php)를 참조하십시오.

>[!ENDTABS]

## 기타

이 절에서는 다른 모든 필수 및 옵션 소프트웨어 유형에 대한 지원 및 호환성에 대해 설명합니다.

>[!NOTE]
>
>Adobe Commerce의 최신 2.4.x 패치 릴리스에는 다음 요구 사항이 적용됩니다. 관련 사항이 있을 경우 클라우드 인프라 상의 상거래가 제공됩니다.

### 브라우저

Storefront 및 관리자:

- Microsoft Edge(최신 및 이전 주 버전)
- Firefox(최신 및 이전 주 버전, 모든 운영 체제)
- Chrome(최신 버전 및 이전 주 버전, 모든 운영 체제)
- Safari(최신 및 이전 주요 버전, macOS 전용)
- iOS용 Safari (storefront용 최신 및 이전 주요 버전)
- Android용 Chrome (storefront용 최신 및 이전 주요 버전)

### 메일 서버

MTA(메일 전송 에이전트) 또는 SMTP 서버. 클라우드 인프라의 Commerce은 [SendGrid 이메일 서비스](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)를 사용합니다.

### 메모리

Commerce Marketplace 및 기타 소스에서 얻은 응용 프로그램 및 확장을 업그레이드하려면 최대 2GB의 RAM이 필요합니다. 2GB 미만의 RAM을 사용하는 시스템을 사용하는 경우 [스왑 파일](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)을 만듭니다. 그렇지 않으면 업그레이드가 실패할 수 있습니다.

### 운영 체제 (Linux x86-64)

RedHat Enterprise Linux(RHEL), CentOS, Ubuntu, Debian 등과 같은 Linux 배포판

Microsoft Windows 및 macOS은 **지원되지 않습니다**.

Adobe Commerce를 사용하려면 일부 작업에 다음 시스템 도구가 필요합니다.

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
- TLS(전송 계층 보안) 요구 사항 - PayPal 및 `repo.magento.com` 모두 TLS 1.2 이상이 필요합니다.

Commerce on Cloud 인프라의 경우 [Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) 가이드의 *Factly configuration*&#x200B;을 참조하십시오.

### Xdebug

Adobe Commerce의 경우 [php_xdebug 2.5.x](https://xdebug.org/download) 이상을 사용하십시오(개발 환경에만 해당. 성능에 부정적인 영향을 줄 수 있음).

Adobe Commerce on Cloud의 경우 [Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) 가이드의 *Configure Xdebug*&#x200B;을 참조하십시오.

>[!NOTE]
>
>설치 후 Adobe Commerce 설치 또는 스토어프런트 또는 관리자에 대한 액세스에 영향을 줄 수 있는 `xdebug`에 알려진 문제가 있습니다. [Commerce Support Knowledge Base`xdebug`에서 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) 설치에 영향을 주는 알려진 문제&#x200B;_를 참조하십시오._


<!-- Last updated from includes: 2026-03-13 12:40:18 -->
