---
title: 전제 조건 완료
description: 다음 전제 조건 단계를 완료하여 Adobe Commerce 프로젝트를 업그레이드하도록 준비합니다.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# 업그레이드 사전 요구 사항 완료

Adobe Commerce을 실행하는 데 필요한 사항을 이해하는 것이 중요합니다. 먼저 다음을 검토해야 합니다. [시스템 요구 사항](../../installation/system-requirements.md) (으)로 업그레이드할 버전입니다.

시스템 요구 사항을 검토한 후 시스템을 업그레이드하기 전에 다음 사전 요구 사항을 완료해야 합니다.

* 모든 소프트웨어 업데이트
* 지원되는 검색 엔진이 설치되었는지 확인
* 데이터베이스 테이블 형식 변환
* 열린 파일 제한 설정
* cron 작업이 실행 중인지 확인
* 설정 `DATA_CONVERTER_BATCH_SIZE`
* 파일 시스템 권한 확인
* 설정 `pub/` 디렉터리 루트
* Composer 업데이트 플러그인 설치

## 모든 소프트웨어 업데이트

다음 [시스템 요구 사항](../../installation/system-requirements.md) Adobe Commerce 릴리스에서 테스트한 타사 소프트웨어의 버전을 정확하게 설명합니다.

사용자 환경에서 모든 시스템 요구 사항 및 종속성을 업데이트했는지 확인합니다. PHP 보기 [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php), 및 [필수 PHP 설정](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure Pro 프로젝트의 경우 다음을 생성해야 합니다. [지원](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 스테이징 및 프로덕션 환경에서 서비스를 설치하거나 업데이트하는 티켓입니다. 필요한 서비스 변경 사항을 표시하고 업데이트된 사항을 포함시킵니다. `.magento.app.yaml` 및 `services.yaml` 티켓의 파일 및 PHP 버전. 클라우드 인프라 팀이 프로젝트를 업데이트하는 데 최대 48시간이 걸릴 수 있습니다. 다음을 참조하십시오 [지원되는 소프트웨어 및 서비스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## 지원되는 검색 엔진이 설치되었는지 확인

Adobe Commerce에서 소프트웨어를 사용하려면 Elasticsearch 또는 OpenSearch를 설치해야 합니다.

**2.3.x에서 2.4로 업그레이드하는 경우**, 2.3.x 인스턴스에서 MySQL, Elasticsearch 또는 타사 확장을 카탈로그 검색 엔진으로 사용 중인지 여부를 확인해야 합니다. 그 결과에 따라 수행할 작업이 결정됩니다 _다음 이전_ 2.4로 업그레이드

**2.3.x 또는 2.4.x 릴리스 라인에서 패치 릴리스를 업그레이드하는 경우**, Elasticsearch 7.x가 이미 설치된 경우 다음을 수행할 수 있습니다 [OpenSearch로 마이그레이션](opensearch-migration.md).

명령줄 또는 관리자를 사용하여 카탈로그 검색 엔진을 결정할 수 있습니다.

* 다음을 입력합니다. `bin/magento config:show catalog/search/engine` 명령입니다. 이 명령은 값 을 반환합니다. `mysql`, `elasticsearch` (Elasticsearch 2가 구성되었음을 나타냄), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`또는 서드파티 검색 엔진을 설치했음을 나타내는 사용자 지정 값입니다. 2.4.6 이전 버전의 경우 `elasticsearch7` Elasticsearch 7 또는 OpenSearch 엔진에 대한 값입니다. 버전 2.4.6 이상의 경우 `opensearch` OpenSearch 엔진의 값입니다.

* 책임자로부터 다음 값을 확인합니다. **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** 필드.

다음 섹션에서는 2.4.0으로 업그레이드하기 전에 수행해야 하는 작업을 설명합니다.

### MySQL

2.4부터 MySQL은 더 이상 지원되는 카탈로그 검색 엔진이 아닙니다. 업그레이드하기 전에 Elasticsearch 또는 OpenSearch를 설치하고 구성해야 합니다. 다음 리소스를 사용하여 이 프로세스를 안내합니다.

* [설치 및 구성 Elasticsearch](../../configuration/search/overview-search.md)
* [설치 Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 구성 [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) 또는 [Apache](../../installation/prerequisites/search-engine/configure-apache.md) 검색 엔진으로 작업하려면
* [Elasticsearch을 사용하도록 Commerce 구성](../../configuration/search/configure-search-engine.md) 및 색인 재지정

일부 타사 카탈로그 검색 엔진은 Adobe Commerce 검색 엔진 위에서 실행됩니다. 확장을 업데이트해야 하는지 여부를 확인하려면 공급업체에 문의하십시오.

#### 마리아DB

{{$include /help/_includes/maria-db-config.md}}

### 검색 엔진

2.4.0으로 업그레이드하기 전에 Elasticsearch 7.6 이상 또는 OpenSearch 1.2를 설치 및 구성해야 합니다. Adobe은 더 이상 Elasticsearch 2.x, 5.x 및 6.x를 지원하지 않습니다. [검색 엔진 구성](../../configuration/search/configure-search-engine.md) 다음에서 _구성 안내서_ Elasticsearch을 지원되는 버전으로 업그레이드한 후 수행해야 하는 작업에 대해 설명합니다.

을(를) 참조하십시오 [업그레이드 Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 프로덕션에 배포하기 전에 데이터 백업, 잠재적인 마이그레이션 문제 감지 및 업그레이드 테스트에 대한 전체 지침 현재 버전의 Elasticsearch에 따라 전체 클러스터를 다시 시작해야 할 수도 있고 필요하지 않을 수도 있습니다.

Elasticsearch을 사용하려면 JDK(Java Development Kit) 1.8 이상이 필요합니다. 다음을 참조하십시오 [JDK(Java Software Development Kit) 설치](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 설치된 JDK 버전을 확인하려면 다음을 수행하십시오.

#### OpenSearch

OpenSearch는 Elasticsearch의 라이선스 변경에 따른 Elasticsearch 7.10.2의 오픈 소스 포크입니다. 다음 Adobe Commerce 릴리스에서는 OpenSearch에 대한 지원이 도입되었습니다.

* 2.4.6 (OpenSearch에는 별도의 모듈과 설정이 있음)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

다음을 수행할 수 있습니다. [Elasticsearch에서 OpenSearch로 마이그레이션](opensearch-migration.md) 위에 나열된 (또는 이상) Adobe Commerce 버전으로 업그레이드하는 경우에만 해당됩니다.

OpenSearch를 사용하려면 JDK 1.8 이상이 필요합니다. 다음을 참조하십시오 [JDK(Java Software Development Kit) 설치](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 설치된 JDK 버전을 확인하려면 다음을 수행하십시오.

[검색 엔진 구성](../../configuration/search/configure-search-engine.md) 검색 엔진을 변경한 후 수행해야 하는 작업에 대해 설명합니다.

#### 업그레이드 Elasticsearch

Elasticsearch 8.x에 대한 지원은 Adobe Commerce 2.4.6에서 도입되었습니다. 다음 지침은 7.x에서 8.x로 Elasticsearch을 업그레이드하는 예를 보여줍니다.

1. Elasticsearch 7.x 서버를 8.x로 업그레이드하고 가 실행 중인지 확인합니다. 다음을 참조하십시오. [Elasticsearch 설명서](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. 활성화 `id_field_data` 에 다음 구성을 추가하여 필드 `elasticsearch.yml` 파일을 만들고 Elasticsearch 8.x 서비스를 다시 시작합니다.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Elasticsearch 8.x를 지원하기 위해 Adobe Commerce 2.4.6에서는 `indices.id_field_data` 기본적으로 속성을 사용하고 `_id` 의 필드 `docvalue_fields` 속성.

1. Adobe Commerce 프로젝트의 루트 디렉터리에서 작성기 종속성을 업데이트하여 `Magento_Elasticsearch7` 모듈 및 설치 `Magento_Elasticsearch8` 모듈.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. 프로젝트 구성 요소를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. [구성 Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 다음에서 [!DNL Admin].

1. 카탈로그 색인을 다시 색인화합니다.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 활성화된 캐시 유형에서 모든 항목을 삭제합니다.

   ```bash
   bin/magento cache:clean
   ```

#### 다운그레이드 Elasticsearch

실수로 서버의 Elasticsearch 버전을 업그레이드하거나 다른 이유로 다운그레이드해야 한다고 판단되는 경우 Adobe Commerce 프로젝트 종속성도 업데이트해야 합니다. 예를 들어 Elasticsearch 8.x에서 7.x로 다운그레이드하려면 다음을 수행합니다

1. Elasticsearch 8.x 서버를 7.x로 다운그레이드하고 가 실행 중인지 확인합니다. 다음을 참조하십시오. [Elasticsearch 설명서](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Adobe Commerce 프로젝트의 루트 디렉터리에서 작성기 종속성을 업데이트하여 `Magento_Elasticsearch8` 모듈 및 해당 작성기 종속성 및 설치 `Magento_Elasticsearch7` 모듈.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. 프로젝트 구성 요소를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. [구성 Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 다음에서 [!DNL Admin].

1. 카탈로그 색인을 다시 색인화합니다.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 활성화된 캐시 유형에서 모든 항목을 삭제합니다.

   ```bash
   bin/magento cache:clean
   ```

### 타사 확장

확장이 Adobe Commerce 릴리스와 완전히 호환되는지 확인하려면 검색 엔진 공급업체에 문의하는 것이 좋습니다.

## 데이터베이스 테이블 형식 변환

모든 데이터베이스 테이블의 형식을 `COMPACT` 끝 `DYNAMIC`. 또한 저장소 엔진 유형을에서 변환해야 합니다 `MyISAM` 끝 `InnoDB`. 다음을 참조하십시오 [우수 사례](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## 열린 파일 제한 설정

열린 파일 제한(ulimit)을 설정하면 긴 쿼리 문자열의 여러 재귀 호출로 인한 오류나 `bin/magento setup:rollback` 명령입니다. 이 명령은 UNIX 셸마다 다릅니다. 다음에 대한 자세한 내용은 개별 맛을 참조하십시오. `ulimit` 명령입니다.

Adobe은 열린 파일을 설정할 것을 권장합니다 [제한](https://ss64.com/bash/ulimit.html) 다음 값으로 `65536` 또는 그 이상이지만 필요한 경우 더 큰 값을 사용할 수 있습니다. 명령줄에 대한 ulimit을 설정하거나 사용자의 셸에 대한 영구 설정으로 지정할 수 있습니다.

명령줄에서 제한(ulimit)을 설정하려면 다음을 수행합니다.

1. 다음으로 전환 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. ulimit을 (으)로 설정 `65536`.

   ```bash
   ulimit -n 65536
   ```

Bash 셸에서 값을 설정하려면 다음을 수행합니다.

1. 다음으로 전환 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 열기 `/home/<username>/.bashrc` 텍스트 편집기에서.
1. 다음 줄을 추가합니다.

   ```bash
   ulimit -n 65536
   ```

1. 변경 내용을 `.bashrc` 파일을 만들고 텍스트 편집기를 종료합니다.

>[!IMPORTANT]
>
>에 대한 값을 설정하지 않는 것이 좋습니다. `pcre.recursion_limit` 의 속성 `php.ini` 실패 알림 없이 불완전한 롤백을 초래할 수 있기 때문입니다.

## cron 작업이 실행 중인지 확인

UNIX 작업 스케줄러 `cron` 는 일상적인 Adobe Commerce 작업에 매우 중요합니다. 리인덱싱, 뉴스레터, 이메일, 사이트 맵 등의 일정을 수립합니다. 몇 가지 기능을 사용하려면 파일 시스템 소유자로서 cron 작업을 하나 이상 실행해야 합니다.

cron 작업이 제대로 설정되었는지 확인하려면 다음 명령을 파일 시스템 소유자로 입력하여 crontab을 확인합니다.

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

cron 이 실행되지 않는 또 다른 증상은 관리자의 다음 오류입니다.

![](../../assets/upgrade-guide/cron-not-running.png)

오류를 확인하려면 **시스템 메시지** 을 클릭합니다.

![](../../assets/upgrade-guide/system-messages.png)

다음을 참조하십시오 [cron 구성 및 실행](../../configuration/cli/configure-cron-jobs.md) 추가 정보.

## Data_CONVERTER_BATCH_SIZE 설정

Adobe Commerce 2.4에는 일부 데이터를 직렬화에서 JSON으로 변환해야 하는 보안 개선 사항이 포함되어 있습니다. 이 변환은 업그레이드 중에 발생하며 데이터베이스에 있는 데이터의 양에 따라 시간이 오래 걸릴 수 있습니다.

가장 큰 영향을 받는 테이블은 다음과 같습니다.

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

대량의 데이터가 있는 경우 환경 변수의 값을 설정하여 성능을 향상시킬 수 있습니다. `DATA_CONVERTER_BATCH_SIZE`. 기본적으로 값은 로 설정됩니다. `50,000`.

환경 변수를 설정하려면 다음을 수행합니다.

1. 다음으로 전환 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 변수를 설정합니다.

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` 메모리가 필요합니다. 먼저 테스트하지 않고 큰 값(약 1GB)으로 설정하지 마십시오.

1. 업그레이드가 완료되면 변수를 설정 해제할 수 있습니다.

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 파일 시스템 권한 확인

보안상의 이유로 Adobe Commerce에는 파일 시스템에 대한 특정 권한이 필요합니다. 권한 은 과(와) 다릅니다. _[소유권](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. 소유권은 파일 시스템에서 작업을 수행할 수 있는 사용자를 결정하고, 권한은 사용자가 수행할 수 있는 작업을 결정합니다.

파일 시스템의 디렉토리는 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md) 그룹입니다.

파일 시스템 권한이 제대로 설정되어 있는지 확인하려면 응용 프로그램 서버에 로그인하거나 호스팅 공급자의 파일 관리자 응용 프로그램을 사용하십시오.

예를들어, 응용 프로그램이 설치된 경우 다음 명령을 입력합니다 `/var/www/html/magento2`:

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

샘플 출력에 대한 설명은 다음을 참조하십시오.

* 대부분의 파일은 `-rw-rw----`, `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* 파일 시스템 소유자는 입니다. `magento_user`

자세한 정보를 보려면 다음 명령을 입력할 수 있습니다.

```bash
ls -la /var/www/html/magento2/pub
```

Adobe Commerce은 정적 파일 자산을 의 하위 디렉터리에 배포하기 때문에 `pub`, 권한 및 소유권도 확인하는 것이 좋습니다.

자세한 내용은 [파일 시스템 권한 및 소유권](../../installation/prerequisites/file-system/overview.md).

## 설정 `pub/` 디렉터리 루트

다음을 참조하십시오 [보안을 향상하도록 docroot 수정](../../installation/tutorials/docroot.md) 을 참조하십시오.

## Composer 업데이트 플러그인 설치

다음 [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) 작성기 플러그인이 루트 프로젝트에 적용해야 하는 변경 사항을 해결합니다. `composer.json` 새 제품 요구 사항으로 업데이트하기 전에 파일을 작성합니다.

플러그인은 종속성 충돌을 수동으로 식별하고 수정해야 하는 대신 식별하고 해결하는 데 도움을 주어 수동 업그레이드를 부분적으로 자동화합니다.

플러그인을 설치하려면:

1. 에 패키지 추가 `composer.json` 파일.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 종속성 업데이트:

   ```bash
   composer update
   ```
