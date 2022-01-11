---
title: 전체 사전 요구 사항
description: 이러한 전제 조건 단계를 완료하여 업그레이드를 위한 Adobe Commerce 또는 Magento Open Source 프로젝트를 준비합니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# 전체 업그레이드 사전 요구 사항

Adobe Commerce 또는 Magento Open Source을 실행하는 데 필요한 사항을 이해하는 것이 중요합니다. 먼저 을(를) 검토해야 합니다 [시스템 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 로 업그레이드하려는 버전의 경우

시스템 요구 사항을 검토한 후 시스템을 업그레이드하기 전에 다음 사전 요구 사항을 완료해야 합니다.

- 모든 소프트웨어 업데이트
- Elasticsearch이 설치되어 있는지 확인합니다
- 열린 파일 제한 설정
- 크론 작업이 실행 중인지 확인합니다
- 설정 `DATA_CONVERTER_BATCH_SIZE`
- 파일 시스템 권한 확인
- 설정 `pub/` 디렉토리 루트
- Composer 업데이트 플러그인 설치

## 모든 소프트웨어 업데이트

다음 [시스템 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) Adobe Commerce 및 Magento Open Source 릴리스에서 테스트한 타사 소프트웨어 버전을 정확하게 설명합니다.

사용자 환경의 모든 시스템 요구 사항과 종속성을 업데이트했는지 확인합니다. PHP 참조 [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), 및 [필수 PHP 설정](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## Elasticsearch이 설치되어 있는지 확인합니다.

Adobe Commerce 및 Magento Open Source에서 소프트웨어를 사용하려면 Elasticsearch을 설치해야 합니다. 2.3.x에서 2.4로 업그레이드하기 전에 2.3.x 인스턴스에서 카탈로그 검색 엔진으로 MySQL, Elasticsearch 또는 타사 확장을 사용하는지 확인해야 합니다. 결과는 사용자가 수행해야 하는 작업을 결정합니다 _이전_ 2.4로 업그레이드

명령줄 또는 관리자를 사용하여 카탈로그 검색 엔진을 결정할 수 있습니다.

- 을(를) 입력합니다. `bin/magento config:show catalog/search/engine` 명령. 명령은 값을 반환합니다 `mysql`, `elasticsearch` (Elasticsearch 2이 구성되었음을 나타냅니다), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`또는 사용자 지정 값으로, 타사 검색 엔진을 설치했음을 나타냅니다.

- 관리자에서 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 필드.

다음 섹션에서는 2.4.0으로 업그레이드하기 전에 수행해야 하는 작업에 대해 설명합니다.

### MySQL

2.4부터는 MySQL이 더 이상 지원되는 카탈로그 검색 엔진이 아닙니다. 업그레이드하기 전에 Elasticsearch을 설치하고 구성해야 합니다. 다음 리소스를 사용하여 이 프로세스를 안내하십시오.

- [Elasticsearch 설치 및 구성](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [Elasticsearch 설치](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 사용할 Elasticsearch 구성 [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) 또는 [Apache](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [Elasticsearch을 사용하도록 상거래 구성](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 및 다시 색인화

일부 타사 카탈로그 검색 엔진은 Adobe Commerce 검색 엔진 맨 위에서 실행됩니다. 확장을 업데이트해야 하는지 여부를 확인하려면 공급업체에 문의하십시오.

### Elasticsearch

2.4.0으로 업그레이드하기 전에 Elasticsearch을 설치 및 구성해야 합니다. Adobe은 더 이상 Elasticsearch 2.x, 5.x 및 6.x를 지원하지 않습니다.

을(를) 참조하십시오. [업그레이드 Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 프로덕션에 배포하기 전에 데이터 백업, 잠재적 마이그레이션 문제 감지, 업그레이드 테스트 등에 대한 전체 지침을 살펴보십시오. 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작할 필요가 있거나 필요하지 않을 수 있습니다.

Elasticsearch을 사용하려면 JDK 1.8 이상이 필요합니다. 자세한 내용은 [JDK(Java Software Development Kit) 설치](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 를 클릭하여 설치된 JDK 버전을 확인합니다.

[Elasticsearch을 사용하도록 Magento 구성](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) Elasticsearch 2을 지원되는 버전으로 업데이트한 후 수행해야 하는 작업에 대해 설명합니다.

### 타사 확장

확장이 2.4와 완전히 호환되는지 여부를 확인하려면 검색 엔진 공급업체에 문의하는 것이 좋습니다.

## 열린 파일 제한 설정

열린 파일 제한(ulimit)을 설정하면 긴 쿼리 문자열의 여러 재귀 호출이나 `bin/magento setup:rollback` 명령. 이 명령은 UNIX 셸마다 다릅니다. 에 대한 세부 사항은 개별 향을 참조하십시오 `ulimit` 명령.

Adobe은 열린 파일을 설정할 것을 권장합니다 [ulimit](http://ss64.com/bash/ulimit.html) 값 `65536` 또는 그 이상 사용할 수 있지만, 필요한 경우 더 큰 값을 사용할 수 있습니다. 명령줄에서 ulimit를 설정하거나 사용자 셸에 대한 영구 설정으로 만들 수 있습니다.

명령줄에서 ulimit를 설정하려면 다음을 수행합니다.

1. 로 전환 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 제한 을 65536.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > 열린 파일 제한 구문은 사용하는 UNIX 셸에 따라 다릅니다. 이전 설정은 Bash 셸과 함께 CentOS 및 Ubuntu에서 작동해야 합니다. 그러나 Mac OS의 경우 올바른 설정은 ulimit -S 65532. 자세한 내용은 매뉴얼 페이지 또는 운영 체제 참조를 참조하십시오.

Bash 쉘에서 값을 설정하려면 다음을 수행합니다.

1. 로 전환 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 열기 `/home/<username>/.bashrc` 텍스트 편집기에서 을 참조하십시오.
1. 다음 줄을 추가합니다.

   ```bash
   ulimit -s 65536
   ```

1. 변경 내용을 `.bashrc` 파일을 종료하고 텍스트 편집기를 종료합니다.

>[!IMPORTANT]
>
>에 대한 값을 설정하지 않는 것이 좋습니다 `pcre.recursion_limit` 속성( `php.ini` 실패 알림 없이 롤백이 불완전할 수 있으므로 파일입니다.

## cron 작업이 실행 중인지 확인

UNIX 작업 스케줄러 `cron` 는 일상적인 Adobe Commerce 및 Magento Open Source 작업에 매우 중요합니다. 색인 재지정, 뉴스레터, 이메일, 사이트 맵 등과 같은 일정을 잡습니다. 몇 가지 기능을 사용하려면 파일 시스템 소유자로 실행 중인 하나 이상의 크론 작업이 필요합니다.

cron 작업이 제대로 설정되었는지 확인하려면 파일 시스템 소유자로 다음 명령을 입력하여 crontab을 확인합니다.

>[!NOTE]
>
>crontab은 cron 작업 실행을 담당하는 구성 파일입니다.

```bash
crontab -l
```

다음과 유사한 결과가 표시됩니다.

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

관리자가 실행 중이 아닐 때 발생하는 또 다른 증상은 다음과 같습니다.

![](../../assets/upgrade-guide/cron-not-running.png)

오류를 보려면 **시스템 메시지** 창 상단에서 다음을 수행합니다.

![](../../assets/upgrade-guide/system-messages.png)

자세한 내용은 [크론 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 추가 정보.

## DATA_CONVERTER_BATCH_SIZE 설정

Adobe Commerce 2.4에는 직렬화된 데이터를 JSON으로 변환해야 하는 보안 개선 사항이 포함되어 있습니다. 이 변환은 업그레이드 중에 발생하며 데이터베이스에 있는 데이터의 양에 따라 시간이 오래 걸릴 수 있습니다.

다음 표는 가장 큰 영향을 받습니다.

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

많은 양의 데이터가 있는 경우 환경 변수의 값을 설정하여 성능을 향상시킬 수 있습니다. `DATA_CONVERTER_BATCH_SIZE`. 기본적으로 이 값은 로 설정됩니다 `50,000`.

환경 변수를 설정하려면 다음을 수행하십시오.

1. 로 전환 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 변수를 설정합니다.

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 메모리가 필요합니다. 먼저 테스트하지 않고 큰 값(약 1GB)으로 설정하지 마십시오.

1. 업그레이드가 완료되면 변수를 설정 해제할 수 있습니다.

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 파일 시스템 권한 확인

보안상의 이유로 Adobe Commerce 및 Magento Open Source에서는 파일 시스템에 대한 특정 권한이 필요합니다. 권한은 다음과 다릅니다 _[소유권](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. 소유권은 파일 시스템에서 작업을 수행할 수 있는 사용자를 결정합니다. 권한은 사용자가 수행할 수 있는 작업을 결정합니다.

파일 시스템의 디렉토리는 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) 그룹에 속해 있어야 합니다.

파일 시스템 권한이 제대로 설정되었는지 확인하려면 애플리케이션 서버에 로그인하거나 호스팅 공급자의 파일 관리자 응용 프로그램을 사용하십시오.

예를 들어 응용 프로그램이 설치된 경우 다음 명령을 입력합니다. `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

샘플 출력:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

샘플 출력에 대한 자세한 내용은 다음을 참조하십시오.

- 대부분의 파일이 `-rw-rw----`: `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- 파일 시스템 소유자가 `magento_user`

자세한 정보를 보려면 다음 명령을 입력할 수 있습니다.

```bash
ls -la /var/www/html/magento2/pub
```

Adobe Commerce 및 Magento Open Source은 정적 파일 자산을 의 하위 디렉토리에 배포하므로 `pub`또한 여기에서 권한 및 소유권을 확인하는 것이 좋습니다.

자세한 내용은 [파일 시스템 권한 및 소유권](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## 설정 `pub/` 디렉토리 루트

자세한 내용은 [보안을 향상하기 위해 docroot 수정](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) 자세한 내용

## Composer 업데이트 플러그인 설치

다음 [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) 작성기 플러그인이 루트 프로젝트에 수행해야 하는 변경 사항을 확인합니다 `composer.json` 파일을 업데이트한 후 새 제품 요구 사항을 업데이트합니다.

이 플러그인은 수동으로 식별하고 수정해야 하는 대신 종속성 충돌을 식별하고 해결하는 데 도움이 되도록 수동 업그레이드를 부분적으로 자동화합니다.

플러그인을 설치하려면 다음을 수행하십시오.

1. 패키지를 `composer.json` 파일.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 종속성을 업데이트합니다.

   ```bash
   composer update
   ```
