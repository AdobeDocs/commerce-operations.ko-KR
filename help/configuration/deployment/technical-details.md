---
title: 기술 세부 정보
description: 파이프라인 배포에 대한 기술 세부 정보, 구성 유형 및 권장 워크플로우에 대해 알아보십시오.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# 기술 세부 정보

이 항목에서는 Commerce 2.2 이상의 파이프라인 배포에 대한 기술 구현 세부 사항에 대해 설명합니다. 개선 사항은 다음 영역으로 나눌 수 있습니다.

- [구성 관리](#configuration-management)
- [관리자의 변경 사항](#changes-in-the-admin)
- [cron 설치 및 제거](#install-and-remove-cron)

또한 이 항목에서는 파이프라인 배포를 위한 [권장 워크플로우](#recommended-workflow)에 대해 설명하고 작동 방식을 이해하는 데 도움이 되는 몇 가지 예를 제공합니다.

시작하기 전에 개발, 빌드 및 프로덕션 시스템에 대한 [사전 요구 사항](../deployment/prerequisites.md)을 검토하십시오.

## 구성 관리

개발 및 프로덕션 시스템의 구성을 동기화하고 유지 관리하려면 다음 재정의 체계를 사용합니다.

![구성 변수 값을 결정하는 방법](../../assets/configuration/override-flow-diagram.png)

다이어그램에서 볼 수 있듯이 구성 값은 다음 순서로 사용됩니다.

1. 환경 변수가 있으면 다른 모든 값을 재정의합니다.
1. 공유 구성 파일 `env.php` 및 `config.php`에서. `env.php`의 값은 `config.php`의 값을 재정의합니다.
1. 데이터베이스에 저장된 값.
1. 해당 소스에 값이 없으면 기본값 또는 NULL이 사용됩니다.

### 공유 구성 관리

공유 구성이 `app/etc/config.php`에 저장되며 소스 제어에 있어야 합니다.

개발(또는 클라우드 인프라 _통합_) 시스템의 Adobe Commerce에서 공유 구성을 설정하고 [`magento app:config:dump` 명령을 사용하여 `config.php`에 구성을 씁니다](../cli/export-configuration.md).

### 시스템별 구성 관리

시스템별 구성이 `app/etc/env.php`에 저장되었습니다. 이 구성은 소스 제어에 _해서는 안 됩니다_.

개발(또는 클라우드 인프라 통합 시 Adobe Commerce) 시스템의 관리에서 시스템별 구성을 설정하고 [`magento app:config:dump` 명령을 사용하여 `env.php`에 구성을 씁니다](../cli/export-configuration.md).

이 명령은 또한 중요한 설정을 `env.php`에 씁니다.

### 중요한 구성 관리

중요한 구성은 `app/etc/env.php`에도 저장됩니다.

다음 방법 중 하나로 중요한 구성을 관리할 수 있습니다.

- 환경 변수
- [`magento config:set:sensitive` 명령을 사용하여 프로덕션 시스템의 `env.php`에 중요한 구성을 저장합니다](../cli/set-configuration-values.md)

### 관리자에서 구성 설정이 잠김

`config.php` 또는 `env.php`의 모든 구성 설정이 관리자에서 잠겨 있습니다. 즉, 해당 설정은 관리자에서 변경할 수 없습니다.
[`magento config:set` 또는 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 명령을 사용하여 `config.php` 또는 `env.php` 파일의 설정을 변경합니다.

## Commerce 관리자

관리자는 프로덕션 모드에 있는 동안 다음 동작을 표시합니다.

- 관리자에서 캐시 유형을 활성화하거나 비활성화할 수 없습니다
- 다음을 포함한 개발자 설정을 사용할 수 없습니다(**스토어** > 설정 > **구성** > 고급 > **개발자**).

   - CSS, JavaScript 및 HTML 축소
   - CSS와 JavaScript 병합
   - 서버측 또는 클라이언트측 LESS 컴파일
   - 인라인 번역
   - 앞에서 설명한 대로 `config.php` 또는 `env.php`의 모든 구성 설정이 잠겨 있으므로 관리자에서 편집할 수 없습니다.
   - 관리 로케일을 배포된 테마에서 사용하는 언어로만 변경할 수 있습니다.

     다음 그림은 배포된 두 개의 로케일만 표시하는 관리자의 **계정 설정** > **인터페이스 로케일** 목록의 예를 보여줍니다.

     ![관리 로케일을 배포된 로케일로만 변경할 수 있습니다](../../assets/configuration/split-deploy-admin-locale.png)

- 관리자를 사용하여 어떤 범위에든 로케일 구성을 변경할 수 없습니다.

  프로덕션 모드로 전환하기 전에 이러한 변경 작업을 수행하는 것이 좋습니다.

  환경 변수 또는 `general/locale/code` 경로가 있는 `config:set` CLI 명령을 사용하여 로케일을 계속 구성할 수 있습니다.

## cron 설치 및 제거

버전 2.2에서는 처음으로 [`magento cron:install` 명령](../cli/configure-cron-jobs.md)을 제공하여 cron 작업을 설정하는 데 도움이 됩니다. 이 명령은 명령을 실행하는 사용자로 crontab을 설정합니다.

또한 `magento cron:remove` 명령을 사용하여 crontab을 제거할 수도 있습니다.

## 권장 파이프라인 배포 워크플로

다음 다이어그램은 파이프라인 배포를 사용하여 구성을 관리하는 방법을 보여 줍니다.

![권장 파이프라인 배포 워크플로](../../assets/configuration/split-deploy-workflow.png)

### 개발 시스템

개발 시스템에서는 관리에서 구성을 변경하고 공유 구성 `app/etc/config.php` 및 시스템별 구성 `app/etc/env.php`을(를) 생성합니다. Commerce 코드 및 공유 구성을 소스 제어로 확인하고 빌드 서버로 푸시합니다.

또한 확장을 설치하고 개발 시스템에서 Commerce 코드를 사용자 정의해야 합니다.

개발 시스템에서:

1. 관리자에서 구성을 설정합니다.

1. `magento app:config:dump` 명령을 사용하여 파일 시스템에 구성을 씁니다.

   - `app/etc/config.php`은(는) 모든 설정 _제외_ 및 시스템별 설정이 포함된 공유 구성입니다. 이 파일은 소스 제어에 있어야 합니다.
   - `app/etc/env.php`은(는) 특정 시스템에 고유한 설정(예: 호스트 이름 및 포트 번호)을 포함하는 시스템별 구성입니다. 이 파일은 소스 제어에 _해서는 안 됩니다_.

1. 수정된 코드와 공유 구성을 소스 제어에 추가합니다.

1. 개발 중에 생성된 php 코드 및 정적 에셋 파일을 제거하려면 다음 명령을 실행합니다.

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Commerce은 에셋을 지우는 명령을 실행한 후 작업 파일을 생성합니다.

>[!WARNING]
>
>위의 접근 방식에 주의하십시오. `generated` 또는 `pub` 폴더에서 `.htacces`의 파일을 삭제하면 문제가 발생할 수 있습니다.

### 시스템 구축

빌드 시스템은 코드를 컴파일하고 Commerce에 등록된 테마에 대한 정적 보기 파일을 생성합니다. Commerce 데이터베이스에 대한 연결은 필요하지 않으며 Commerce 코드베이스만 필요합니다.

빌드 시스템에서 다음을 수행합니다.

1. 소스 제어에서 공유 구성 파일을 가져옵니다.
1. `magento setup:di:compile` 명령을 사용하여 코드를 컴파일합니다.
1. 정적 파일 보기 파일을 업데이트하려면 `magento setup:static-content:deploy -f` 명령을 사용하십시오.
1. 소스 제어에 대한 업데이트를 확인합니다.

>[!INFO]
>
>정적 보기 파일에 대한 [배포 전략](../cli/static-view-file-strategy.md)을 참조하세요.

### 프로덕션 시스템

프로덕션 시스템(즉, 라이브 스토어)에서는 소스 제어에서 생성된 에셋 및 코드 업데이트를 가져오고 명령줄 또는 환경 변수를 사용하여 시스템별로 중요한 구성 설정을 설정합니다.

프로덕션 시스템에서:

1. 유지 관리 모드를 시작합니다.
1. 소스 제어에서 코드 및 구성 업데이트를 가져옵니다.
1. Adobe Commerce을 사용하는 경우 대기열 작업자를 중지합니다.
1. `magento app:config:import` 명령을 사용하여 프로덕션 시스템에서 구성 변경 내용을 가져옵니다.
1. 데이터베이스 스키마를 변경한 구성 요소를 설치한 경우 `magento setup:upgrade --keep-generated`을(를) 실행하여 데이터베이스 스키마와 데이터를 업데이트하고 생성된 정적 파일을 유지합니다.
1. 시스템별 설정을 설정하려면 `magento config:set` 명령 또는 환경 변수를 사용하십시오.
1. 중요한 설정을 설정하려면 `magento config:sensitive:set` 명령 또는 환경 변수를 사용하십시오.
1. 캐시를 정리(_플러시_&#x200B;라고도 함)합니다.
1. 유지 관리 모드를 종료합니다.

## 구성 관리 명령

구성을 관리하는 데 도움이 되는 다음 명령을 제공합니다.

- `config.php` 및 `env.php`에 관리자 구성 설정을 쓸 수 있는 [`magento app:config:dump`](../cli/export-configuration.md)(중요한 설정 제외)
- [`magento config:set`](../cli/set-configuration-values.md)을(를) 사용하여 프로덕션 시스템에서 시스템별 설정의 값을 설정합니다.

  선택적 `--lock` 옵션을 사용하여 관리자의 옵션을 잠급니다(즉, 설정을 편집할 수 없도록 설정). 설정이 이미 잠겨 있는 경우 `--lock` 옵션을 사용하여 설정을 변경합니다.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md)을(를) 사용하여 프로덕션 시스템에서 중요한 설정의 값을 설정합니다.
- `config.php` 및 `env.php`의 구성 변경 내용을 프로덕션 시스템으로 가져오려면 [`magento app:config:import`](../cli/import-configuration.md)을(를) 사용하십시오.

## 구성 관리 예

이 섹션에서는 `config.php` 및 `env.php`에 대한 변경 내용을 확인할 수 있도록 구성을 관리하는 예를 보여줍니다.

### 기본 로케일 변경

이 섹션은 관리자(**스토어** > 설정 > **구성** > 일반 > **일반** > **로케일 옵션**)을 사용하여 기본 가중치 단위를 변경할 때 `config.php`에 대해 변경된 내용을 보여줍니다.

관리자를 변경한 후 `bin/magento app:config:dump`을(를) 실행하여 `config.php`에 값을 씁니다. `config.php`의 다음 코드 조각에 표시된 대로 값이 `locale` 아래의 `general` 배열에 작성됩니다.

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### 여러 구성 설정 변경

이 섹션에서는 다음 구성 변경에 대해 설명합니다.

- 웹 사이트, 스토어 및 스토어 보기 추가(**스토어** > 설정 > **모든 스토어**)
- 기본 전자 메일 도메인 변경(**스토어** > 설정 > **구성** > 고객 > **고객 구성**)
- PayPal API 사용자 이름 및 API 암호 설정(**스토어** > 설정 > **구성** > 판매 > **결제 방법** > **PayPal** > **필수 PayPal 설정**)

관리자를 변경한 후 개발 시스템에서 `bin/magento app:config:dump`을(를) 실행합니다. 이번에는 모든 변경 내용이 `config.php`에 기록되지 않습니다. 실제로 다음 코드 조각에 표시된 대로 웹 사이트, 스토어 및 스토어 보기만 해당 파일에 기록됩니다.

### config.php

`config.php`에 포함된 항목:

- 웹 사이트, 스토어 및 스토어 보기 변경 사항.
- 비시스템 특정 검색 엔진 설정
- 민감한 PayPal 설정
- `config.php`에서 생략된 중요한 설정을 알려 주는 댓글

`websites` 배열:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` 배열:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` 배열:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` 배열:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

기본 전자 메일 도메인 시스템별 구성 설정이 `app/etc/env.php`에 기록됩니다.

`bin/magento app:config:dump` 명령이 중요한 설정을 쓰지 않으므로 PayPal 설정이 두 파일에 기록되지 않습니다. 다음 명령을 사용하여 프로덕션 시스템에서 PayPal 설정을 설정해야 합니다.

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
