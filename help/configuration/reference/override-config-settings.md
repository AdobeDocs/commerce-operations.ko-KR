---
title: 구성 설정 무시
description: 환경 변수를 사용하여 구성 설정을 재정의하는 방법을 알아봅니다.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# 구성 설정 무시

이 항목에서는 구성 경로를 아는 환경 변수 이름을 도출하는 방법을 설명합니다. 환경 변수를 사용하여 Adobe Commerce 구성 설정을 재정의할 수 있습니다. 예를 들어, 프로덕션 시스템에서 결제 프로세서의 라이브 URL 값을 무시할 수 있습니다.

의 값을 재정의할 수 있습니다 _임의_ 환경 변수를 사용한 구성 설정 그러나 Adobe은 공유 구성 파일을 사용하여 일관된 설정을 유지하는 것이 좋습니다. `config.php`및 시스템별 구성 파일, `env.php`에 설명된 대로 [배포 일반 개요](../deployment/overview.md).

>[!TIP]
>
>다음을 확인하십시오 [환경 구성](https://devdocs.magento.com/cloud/env/variables-intro.html) 의 주제 _Commerce Cloud 안내서_ 클라우드 인프라에서 Adobe Commerce에서 변수 작업에 대한 자세한 내용은 다음을 참조하십시오.

## 환경 변수

환경 변수 이름은 그 범위로 구성되고 그 뒤에는 특정 형식의 구성 경로가 옵니다. 다음 섹션에서는 변수 이름을 더 자세히 결정하는 방법에 대해 설명합니다.

다음 중 하나에 변수를 사용할 수 있습니다.

- [중요 값](config-reference-sens.md) 환경 변수 또는 [`magento config:sensitive:set`](../cli/set-configuration-values.md) 명령.
- 시스템 특정 값은 다음을 사용하여 설정해야 합니다.

   - 환경 변수
   - 다음 [`magento config:set`](../cli/set-configuration-values.md) 명령
   - 관리자 다음에 [`magento app:config:dump` 명령](../cli/export-configuration.md)

구성 경로는 다음 위치에서 찾을 수 있습니다.

- [구분 및 시스템별 구성 경로 참조](config-reference-sens.md)
- [결제 구성 경로 참조](config-reference-payment.md)
- [상거래 B2B 확장 구성 경로 참조](config-reference-b2b.md)
- [기타 구성 경로 참조](config-reference-general.md)

### 변수 이름

시스템 설정 변수 이름의 일반 형식은 다음과 같습니다.

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 다음 중 하나를 수행할 수 있습니다.

- 전역 범위(즉, _모두_ 범위)

   전역 범위 변수는 다음 형식을 갖습니다.

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 특정 범위(즉, 이 설정은 지정된 스토어 보기 또는 웹 사이트에만 영향을 줍니다.)

   예를 들어 보기 범위 변수를 저장하는 형식은 다음과 같습니다.

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   범위에 대한 자세한 내용은 다음을 참조하십시오.

   - [1단계: 웹 사이트 또는 저장소 보기 범위 값을 찾습니다](#step-1-find-the-website-or-store-view-scope-value)
   - [범위에 대한 상거래 사용 안내서 항목](https://docs.magento.com/user-guide/configuration/scope.html)
   - [범위 빠른 참조](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 에는 이중 밑줄 문자가 대체된 구성 경로가 있습니다 `/`. 자세한 내용은 [2단계: 시스템 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 변수 형식

`<SCOPE>` 다음에서 분리됨 `<SYSTEM__VARIABLE__NAME>` 두 개의 밑줄 문자

`<SYSTEM__VARIABLE__NAME>` 구성 설정의 _구성 경로_: `/` 특정 설정을 고유하게 식별하는 구분된 문자열입니다. 각각 바꾸기 `/` 시스템 변수를 만들 수 있는 두 개의 밑줄 문자가 있는 구성 경로에 있는 문자입니다.

구성 경로에 밑줄 문자가 있으면 밑줄 문자가 변수에 그대로 유지됩니다.

구성 경로의 전체 목록은 다음 위치에서 찾을 수 있습니다.

- [구분 및 시스템별 구성 경로 참조](config-reference-sens.md)
- [결제 구성 경로 참조](config-reference-payment.md)
- [Commerce Enterprise B2B 확장 구성 경로 참조](config-reference-b2b.md)
- [기타 구성 경로 참조](config-reference-general.md)

## 1단계: 웹 사이트 또는 저장소 보기 범위 값을 찾습니다

이 섹션에서는 _범위_ (스토어 보기 또는 웹 사이트). 전역 범위 변수를 설정하려면 다음을 참조하십시오 [2단계: 글로벌, 웹 사이트 또는 저장소 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

범위 값은 `store`, `store_group`, 및 `store_website` 표.

- 다음 `store` 저장소 보기 이름 및 코드를 지정합니다
- 다음 `store_website` 는 웹 사이트 이름과 코드를 지정합니다

관리자를 사용하여 코드 값을 찾을 수도 있습니다.

표를 읽는 방법:

- `Path in Admin` 열

   쉼표 앞의 값은 관리자 탐색의 경로입니다. 쉼표 뒤의 값은 오른쪽 창의 옵션입니다.

- `Variable name` 열은 해당 환경 변수의 이름입니다.

   원할 경우 이러한 구성 매개 변수에 대한 시스템 값을 환경 변수로 지정할 수 있습니다.

   - 전체 변수 이름은 항상 ALL CAPS입니다
   - 변수 이름 시작 `CONFIG__` (밑줄 문자 2개 참고)
   - 다음 항목이 있습니다. `<STORE_VIEW_CODE>` 또는 `<WEBSITE_CODE>` 다음 섹션에 설명된 대로 관리자 또는 상거래 데이터베이스에 있는 변수 이름의 일부입니다.
   - 찾을 수 있습니다. `<SYSTEM__VARIABLE__NAME>` 에 설명된 대로 [2단계: 글로벌, 웹 사이트 또는 저장소 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 관리자에서 웹 사이트 또는 저장소 보기 범위 찾기

다음 표에는 관리에서 웹 사이트를 찾거나 보기 값을 저장하는 방법이 요약되어 있습니다.

| 설명 | 관리자의 경로 | 변수 이름 |
|--------------|--------------|----------------------|
| 저장소 보기 만들기, 편집, 삭제 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 웹 사이트 만들기, 편집, 삭제 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

예를 들어 관리에서 웹 사이트를 찾거나 보기 범위 값을 저장하려면 다음을 수행하십시오.

1. 웹 사이트를 볼 수 있는 권한이 있는 사용자로 관리자에게 로그인합니다.
1. 클릭 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. 웹 사이트 또는 저장소 보기의 이름을 클릭합니다.

   오른쪽 창은 다음과 같이 표시됩니다.

   ![웹 사이트 코드 찾기](../../assets/configuration/website-code.png)

1. 범위 이름은 **[!UICONTROL Code]** 필드.
1. 계속 [2단계: 글로벌, 웹 사이트 또는 저장소 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 데이터베이스에서 웹 사이트 또는 저장소 보기 범위 찾기

데이터베이스에서 이러한 값을 가져오려면 다음을 수행하십시오.

1. 다음 방법으로 개발 시스템에 로그인합니다. [파일 시스템 소유자](https://glossary.magento.com/magento-file-system-owner) 아직 안 하셨다면
1. 다음 명령을 입력합니다.

   ```bash
   mysql -u <database-username> -p
   ```

1. 에서 `mysql>` 프롬프트에 다음 명령을 표시된 순서대로 입력합니다.

   ```shell
   use <database-name>;
   ```

1. 다음 SQL 쿼리를 사용하여 관련 값을 찾습니다.

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   샘플은

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. 에서 가져온 값을 사용합니다. `code` 열은 범위 이름으로, 는 아님 `name` 값.

   예를 들어 테스트 웹 사이트에 대한 구성 변수를 설정하려면 다음 형식을 사용하십시오.

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   여기서 `<SYSTEM__VARIABLE__NAME>` 은 다음 섹션에서 가져옵니다.

## 2단계: 글로벌, 웹 사이트 또는 저장소 보기 변수 설정

이 섹션에서는 시스템 변수를 설정하는 방법을 설명합니다.

- 전역 범위의 값(즉, 모든 웹 사이트, 저장소 및 저장소 보기)을 설정하려면 변수 이름을 `CONFIG__DEFAULT__`.

- 특정 저장소 보기 또는 웹 사이트에 대한 값을 설정하려면 다음에 설명된 대로 변수 이름을 시작하십시오 [1단계: 범위 값 찾기](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 변수 이름의 마지막 부분은 각 구성 설정에 대해 고유한 구성 경로입니다.

[몇 가지 예를 참조하십시오](#examples).

다음 표에는 몇 가지 샘플 변수가 나와 있습니다.

| 설명 | 관리자의 경로(생략) **스토어** > **설정** > **구성**) | 변수 이름 |
|--------------|--------------|----------------------|
| Elasticsearch 서버 호스트 이름 | 카탈로그 > **카탈로그**, **Elasticsearch 서버 호스트 이름** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch 서버 포트 | 카탈로그 > **카탈로그**, **Elasticsearch 서버 포트** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 배송 국가 | Sales > **배송 설정** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 사용자 지정 관리 URL | 고급 > **관리** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 사용자 지정 관리자 경로 | 고급 > **관리** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 예

이 섹션에서는 일부 샘플 변수의 값을 찾는 방법을 보여줍니다.

### Elasticsearch 서버 호스트 이름

글로벌 HTML 축소에 대한 변수 이름을 찾으려면

1. 범위를 결정합니다.

   전역 범위이므로 변수 이름은 `CONFIG__DEFAULT__`

1. 변수 이름의 나머지 부분은 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **결과**: 변수 이름은 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 배송 국가

운송 국가 원점의 변수 이름을 찾으려면

1. 범위를 결정합니다.

   에서 범위를 찾습니다. [데이터베이스](#find-a-website-or-store-view-scope-in-the-database) 1단계에서 설명한 대로: 웹 사이트 또는 저장소 보기 범위 값을 찾습니다. ( 관리에서 ( [2단계의 표: 글로벌, 웹 사이트 또는 저장소 보기 변수 설정](#step-2-set-global-website-or-store-view-variables.

   예를 들어 범위는 `CONFIG__WEBSITES__DEFAULT`.

1. 변수 이름의 나머지 부분은 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **결과**: 변수 이름은 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 환경 변수를 사용하는 방법

PHP의 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 배열과 연결 Commerce가 실행될 때 실행되는 모든 PHP 스크립트에서 값을 설정할 수 있습니다.

>[!TIP]
>
>변수 값을에서 설정 `index.php` 또는 `pub/index.php` 은 웹 서버 구성에 따라 다른 응용 프로그램 시작 지점을 사용할 수 있으므로 항상 예상대로 작동하지 않습니다. 배치 `$_ENV` 의 지시문 `app/bootstrap.php` 파일, 다른 애플리케이션 엔트리 포인트에 상관없이 `$_ENV` 지시어는 항상 실행 `app/bootstrap.php` 파일은 상거래 아키텍처의 일부로 로드됩니다.

2를 설정하는 예 `$_ENV` 값은 다음과 같습니다.

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

단계별 예는 다음과 같습니다. [환경 변수를 사용하여 구성 값 설정](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- 에서 설정한 값을 사용하려면 `$_ENV` 배열, 설정해야 합니다. `variables_order = "EGPCS"`(환경, Get, Post, Cookie 및 서버)를 `php.ini` 파일. 자세한 내용은 [PHP 설명서](https://www.php.net/manual/en/ini.core.php).
>
>- 클라우드 기반의 Adobe Commerce의 경우, [Project Web Interface](https://devdocs.magento.com/cloud/project/project-webint-basic.html#project-conf-env-var)를 채울 때는 변수 이름을 `env:`. For example:
>
>![환경 변수 예](https://devdocs.magento.com/common/images/cloud/cloud_env_var_example.png)
