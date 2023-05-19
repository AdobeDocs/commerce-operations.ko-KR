---
title: 구성 설정 재정의
description: 환경 변수를 사용하여 구성 설정을 재정의하는 방법을 알아봅니다.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# 구성 설정 재정의

이 항목에서는 구성 경로를 알고 있는 환경 변수 이름을 파생하는 방법에 대해 설명합니다. 환경 변수를 사용하여 Adobe Commerce 구성 설정을 재정의할 수 있습니다. 예를 들어 프로덕션 시스템에서 결제 프로세서의 라이브 URL 값을 재정의할 수 있습니다.

다음 값을 재정의할 수 있습니다. _임의_ Adobe 환경 변수를 사용한 구성 설정입니다. 그러나 공유 구성 파일을 사용하여 일관된 설정을 유지하는 것이 좋습니다. `config.php`및 시스템별 구성 파일, `env.php`에서 설명한 대로 [배포 일반 개요](../deployment/overview.md).

>[!TIP]
>
>다음을 확인하십시오. [환경 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) 의 주제 _클라우드 인프라의 Commerce 안내서_.

## 환경 변수

환경 변수 이름은 범위 다음에 특정 형식의 구성 경로가 옵니다. 다음 섹션에서는 변수 이름을 결정하는 방법에 대해 자세히 설명합니다.

다음 중 하나에 변수를 사용할 수 있습니다.

- [중요 값](config-reference-sens.md) 은(는) 환경 변수 또는 을 사용하여 설정해야 합니다. [`magento config:sensitive:set`](../cli/set-configuration-values.md) 명령입니다.
- 다음을 사용하여 시스템별 값을 설정해야 합니다.

   - 환경 변수
   - 다음 [`magento config:set`](../cli/set-configuration-values.md) 명령
   - 관리자 다음에 오는 [`magento app:config:dump` 명령](../cli/export-configuration.md)

구성 경로는 다음에서 찾을 수 있습니다.

- [중요한 시스템별 구성 경로 참조](config-reference-sens.md)
- [결제 구성 경로 참조](config-reference-payment.md)
- [상거래 B2B 확장 구성 경로 참조](config-reference-b2b.md)
- [기타 구성 경로 참조](config-reference-general.md)

### 변수 이름

시스템 설정 변수 이름의 일반적인 형식은 다음과 같습니다.

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 다음 중 하나일 수 있습니다.

- 전역 범위(즉, 의 전역 설정) _모두_ 범위)

   전역 범위 변수의 형식은 다음과 같습니다.

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 특정 범위(즉, 이 설정은 지정된 스토어 보기 또는 웹 사이트에만 영향을 줌)

   예를 들어 스토어 뷰 범위 변수는 다음 형식을 갖습니다.

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   범위에 대한 자세한 내용은 다음을 참조하십시오.

   - [1단계: 웹 사이트 또는 스토어 보기 범위 값 찾기](#step-1-find-the-website-or-store-view-scope-value)
   - [범위에 대한 Commerce 사용 안내서 주제](https://docs.magento.com/user-guide/configuration/scope.html)
   - [범위 빠른 참조](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 는 이중 밑줄 문자가 대체된 구성 경로입니다. `/`. 자세한 내용은 [2단계: 시스템 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 변수 형식

`<SCOPE>` 다음에서 분리됨: `<SYSTEM__VARIABLE__NAME>` 밑줄 문자가 두 개 있습니다.

`<SYSTEM__VARIABLE__NAME>` 구성 설정에서 파생됨 _구성 경로_: `/` 특정 설정을 고유하게 식별하는 구분된 문자열입니다. 각각 바꾸기 `/` 구성 경로에 있는 문자(밑줄 문자 2개 포함)를 사용하여 시스템 변수를 만듭니다.

구성 경로에 밑줄 문자가 포함되어 있으면 밑줄 문자가 변수에 남아 있습니다.

전체 구성 경로 목록은 다음 위치에서 찾을 수 있습니다.

- [중요한 시스템별 구성 경로 참조](config-reference-sens.md)
- [결제 구성 경로 참조](config-reference-payment.md)
- [Commerce Enterprise B2B 확장 구성 경로 참조](config-reference-b2b.md)
- [기타 구성 경로 참조](config-reference-general.md)

## 1단계: 웹 사이트 또는 스토어 보기 범위 값 찾기

이 섹션에서는 다음의 시스템 구성 값을 찾고 설정하는 방법에 대해 설명합니다. _범위_ (스토어 보기 또는 웹 사이트). 전역 범위 변수를 설정하려면 다음을 참조하십시오. [2단계: 글로벌, 웹 사이트 또는 스토어 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

범위 값은 `store`, `store_group`, 및 `store_website` 테이블.

- 다음 `store` 표는 저장소 보기 이름과 코드를 지정합니다.
- 다음 `store_website` 표는 웹 사이트 이름과 코드를 지정합니다.

관리자를 사용하여 코드 값을 찾을 수도 있습니다.

표 읽기 방법:

- `Path in Admin` 열

   쉼표 앞의 값은 관리자 탐색의 경로입니다. 쉼표 뒤의 값은 오른쪽 창의 옵션입니다.

- `Variable name` 열은 해당 환경 변수의 이름입니다.

   원할 경우 이러한 구성 매개변수에 대한 시스템 값을 환경 변수로 지정할 수 있습니다.

   - 전체 변수 이름은 항상 모두 대문자입니다.
   - 변수 이름 시작 `CONFIG__` (밑줄 문자 2개를 참고하십시오)
   - 다음을 찾을 수 있습니다. `<STORE_VIEW_CODE>` 또는 `<WEBSITE_CODE>` 다음 섹션에 표시된 대로 Admin 또는 Commerce 데이터베이스의 변수 이름 부분입니다.
   - 다음을 찾을 수 있습니다. `<SYSTEM__VARIABLE__NAME>` 에서 논의된대로 [2단계: 글로벌, 웹 사이트 또는 스토어 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 관리자에서 웹 사이트 또는 스토어 보기 범위 찾기

다음 표에는 관리자에서 웹 사이트를 찾거나 보기 값을 저장하는 방법이 요약되어 있습니다.

| 설명 | 관리자의 경로 | 변수 이름 |
|--------------|--------------|----------------------|
| 스토어 조회수 생성, 편집, 삭제 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 웹 사이트 만들기, 편집, 삭제 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

예를 들어, 관리자에서 웹 사이트를 찾거나 보기 범위 값을 저장하려면 다음을 수행합니다.

1. 웹 사이트를 볼 수 있는 권한이 있는 사용자로 관리자에 로그인합니다.
1. 클릭 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. 웹 사이트 또는 스토어 보기의 이름을 클릭합니다.

   오른쪽 창은 다음과 유사하게 표시됩니다.

   ![웹 사이트 코드 찾기](../../assets/configuration/website-code.png)

1. 범위 이름이에 표시됩니다. **[!UICONTROL Code]** 필드.
1. 계속 [2단계: 글로벌, 웹 사이트 또는 스토어 보기 변수 설정](#step-2-set-global-website-or-store-view-variables).

### 데이터베이스에서 웹 사이트 또는 스토어 보기 범위 찾기

데이터베이스에서 이러한 값을 가져오려면 다음을 수행합니다.

1. 아직 로그인하지 않은 경우 개발 시스템에 파일 시스템 소유자로 로그인합니다.
1. 다음 명령을 입력합니다.

   ```bash
   mysql -u <database-username> -p
   ```

1. 위치: `mysql>` 프롬프트에서 다음 명령을 표시된 순서대로 입력합니다.

   ```shell
   use <database-name>;
   ```

1. 다음 SQL 쿼리를 사용하여 관련 값을 찾습니다.

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   샘플은 다음과 같습니다.

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

1. 의 값 사용 `code` 열이 범위 이름으로 사용되고 `name` 값.

   예를 들어 테스트 웹 사이트에 대한 구성 변수를 설정하려면 다음 형식을 사용하십시오.

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   위치 `<SYSTEM__VARIABLE__NAME>` 다음 섹션에서 가져옵니다.

## 2단계: 글로벌, 웹 사이트 또는 스토어 보기 변수 설정

이 섹션에서는 시스템 변수를 설정하는 방법에 대해 설명합니다.

- 전역 범위(즉, 모든 웹 사이트, 스토어 및 스토어 보기)에 대한 값을 설정하려면 변수 이름을 `CONFIG__DEFAULT__`.

- 특정 스토어 보기 또는 웹 사이트에 대한 값을 설정하려면 다음에 설명된 대로 변수 이름을 시작합니다. [1단계: 범위 값 찾기](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 변수 이름의 마지막 부분은 각 구성 설정에 대해 고유한 구성 경로입니다.

[몇 가지 예 보기](#examples).

다음 표는 몇 가지 샘플 변수를 보여 줍니다.

| 설명 | 관리자의 경로(생략) **스토어** > **설정** > **구성**) | 변수 이름 |
|--------------|--------------|----------------------|
| Elasticsearch 서버 호스트 이름 | 카탈로그 > **카탈로그**, **Elasticsearch 서버 호스트 이름** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch 서버 포트 | 카탈로그 > **카탈로그**, **Elasticsearch 서버 포트** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 배송 국가 원산지 | 판매 > **배송 설정** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 사용자 지정 관리자 URL | 고급 > **관리자** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 사용자 지정 관리자 경로 | 고급 > **관리자** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 예

이 섹션에서는 일부 샘플 변수의 값을 찾는 방법을 보여줍니다.

### Elasticsearch 서버 호스트 이름

전역 HTML 축소를 위한 변수 이름을 찾으려면 다음을 수행합니다.

1. 범위를 결정합니다.

   변수 이름이 다음으로 시작하도록 전역 범위입니다. `CONFIG__DEFAULT__`

1. 나머지 변수 이름은 입니다. `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **결과**: 변수 이름은 입니다. `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 배송 국가 원산지

운송 국가 출처의 변수 이름을 찾으려면

1. 범위를 결정합니다.

   에서 범위 찾기 [데이터베이스](#find-a-website-or-store-view-scope-in-the-database) 1단계에서 설명한 대로: 웹 사이트 또는 스토어 보기 범위 값을 찾습니다. (또한 관리자는에 표시된 대로 값을 찾을 수 있습니다. [2단계의 표: 전역, 웹 사이트 또는 스토어 뷰 변수 설정](#step-2-set-global-website-or-store-view-variables)

   예를 들어 범위는 다음과 같을 수 있습니다. `CONFIG__WEBSITES__DEFAULT`.

1. 나머지 변수 이름은 입니다. `SHIPPING__ORIGIN__COUNTRY_ID`.

   **결과**: 변수 이름은 입니다. `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 환경 변수를 사용하는 방법

PHP를 사용하여 구성 값을 변수로 설정 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 배열을 연결합니다. Commerce가 실행될 때 실행되는 모든 PHP 스크립트에서 값을 설정할 수 있습니다.

>[!TIP]
>
>에서 변수 값 설정 `index.php` 또는 `pub/index.php` 는 웹 서버 구성에 따라 다른 응용 프로그램 진입점을 사용할 수 있으므로 항상 예상대로 작동하지 않습니다. 배치 `$_ENV` 지시문 `app/bootstrap.php` 파일, 다른 응용 프로그램 진입점에 관계없이 `$_ENV` 지시문은 항상 다음 이후에 실행됩니다. `app/bootstrap.php` 파일은 상거래 아키텍처의 일부로 로드됩니다.

2를 설정하는 예 `$_ENV` 값은 다음과 같습니다.

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

단계별 예를에 나와 있습니다. [환경 변수를 사용하여 구성 값 설정](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- 에 설정한 값을 사용하려면 `$_ENV` array, 다음을 설정해야 합니다. `variables_order = "EGPCS"`(환경, Get, Post, 쿠키 및 서버) `php.ini` 파일. 자세한 내용은 [PHP 설명서](https://www.php.net/manual/en/ini.core.php).
>
>- 클라우드 인프라의 Adobe Commerce에 대해 다음을 사용하여 구성 설정을 재정의하려고 하는 경우 [프로젝트 웹 인터페이스](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), 변수 이름 앞에 을 추가해야 합니다. `env:`. 예:
>
>![환경 변수 예](../../assets/configuration/cloud-console-envvariable.png)
