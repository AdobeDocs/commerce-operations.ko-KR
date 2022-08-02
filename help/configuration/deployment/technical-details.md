---
title: 기술 세부 사항
description: 파이프라인 배포, 구성 유형 및 권장 워크플로우에 대한 기술 세부 사항을 참조하십시오.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# 기술 세부 사항

이 항목에서는 Commerce 2.2 이상의 파이프라인 배포에 대한 기술 구현 세부 사항을 설명합니다. 개선 사항은 다음 영역으로 나눌 수 있습니다.

- [구성 관리](#configuration-management)
- [관리자의 변경 사항](#changes-in-the-admin)
- [크론 설치 및 제거](#install-and-remove-cron)

이 항목에서는 또한 [권장 워크플로우](#recommended-workflow) 파이프라인 배포의 경우 및에서 파이프라인 작동 방식을 이해하는 데 도움이 되는 몇 가지 예를 제공합니다.

시작하기 전에 [개발, 빌드 및 프로덕션 시스템을 위한 사전 요구 사항](../deployment/prerequisites.md).

## 구성 관리

개발 및 프로덕션 시스템의 구성을 동기화 및 유지 관리할 수 있도록 하려면 다음 재정의 체계를 사용하십시오.

![구성 변수 값의 결정 방식](../../assets/configuration/override-flow-diagram.png)

다이어그램에 표시된 것처럼 구성 값은 다음 순서로 사용됩니다.

1. 환경 변수가 있으면 다른 모든 값을 재정의합니다.
1. 공유 구성 파일에서 `env.php` 및 `config.php`. 의 값 `env.php` 값 재정의 `config.php`.
1. 데이터베이스에 저장된 값에서
1. 해당 소스에 값이 없으면 기본값 또는 NULL이 사용됩니다.

### 공유 구성 관리

공유 구성은에 저장됩니다. `app/etc/config.php`: 소스 제어에서 사용해야 합니다.

개발 관리자의 공유 구성(또는 클라우드 인프라의 Adobe Commerce)을 설정합니다 _통합_) 시스템 및 쓰기 `config.php` 사용 [`magento app:config:dump` 명령](../cli/export-configuration.md).

### 시스템별 구성 관리

시스템별 구성은 `app/etc/env.php`다음 작업을 수행합니다. _not_ 소스 제어에 있어야 합니다.

개발(또는 Adobe Commerce on cloud infrastructure integration) 시스템의 관리자에서 시스템별 구성을 설정하고 구성을 (으)로 작성합니다 `env.php` 사용 [`magento app:config:dump` 명령](../cli/export-configuration.md).

이 명령은 중요한 설정도 `env.php`.

### 중요한 구성 관리

중요한 구성은에 저장됩니다. `app/etc/env.php`.

다음 방법 중 하나로 중요한 구성을 관리할 수 있습니다.

- 환경 변수
- 중요한 구성 저장 위치 `env.php` 프로덕션 시스템에서 [`magento config:set:sensitive` 명령](../cli/set-configuration-values.md)

### 관리에서 잠긴 구성 설정

의 모든 구성 설정 `config.php` 또는 `env.php` 는 관리자에 잠겨 있습니다. 즉, 관리자에서 해당 설정을 변경할 수 없습니다.
를 사용하십시오 [`magento config:set` 또는 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 명령에서 설정을 변경합니다. `config.php` 또는 `env.php` 파일.

## 상거래 관리자

관리자는 프로덕션 모드에서 다음 동작을 표시합니다.

- 관리에서 캐시 유형을 활성화하거나 비활성화할 수 없습니다
- 개발자 설정을 사용할 수 없습니다(**스토어** > 설정 > **구성** > 고급 > **개발자**).

   - CSS, JavaScript 및 HTML 축소
   - CSS 및 JavaScript 병합
   - 서버측 또는 클라이언트측 LESS 컴파일
   - 인라인 번역
   - 앞에서 설명한 대로 의 모든 구성 설정은 `config.php` 또는 `env.php` 가 잠겨 있으므로 관리자에서 편집할 수 없습니다.
   - 관리 로케일을 배포된 테마에 사용되는 언어로만 변경할 수 있습니다

      다음 그림은 **계정 설정** > **인터페이스 로케일** 관리자 목록에 두 개의 배포된 로케일만 표시됩니다.

      ![관리 로케일을 배포된 로케일로 변경할 수 있습니다](../../assets/configuration/split-deploy-admin-locale.png)

- 관리자를 사용하여 범위에 대한 로케일 구성을 변경할 수 없습니다.

   프로덕션 모드로 전환하기 전에 이러한 변경 작업을 수행하는 것이 좋습니다.

   환경 변수 또는 `config:set` 경로가 있는 CLI 명령 `general/locale/code`.

## 크론 설치 및 제거

버전 2.2에서는 처음으로 다음을 제공하여 크론 작업을 설정하는 데 도움을 줍니다 [`magento cron:install` 명령](../cli/configure-cron-jobs.md). 이 명령은 crontab을 명령을 실행하는 사용자로 설정합니다.

또한 `magento cron:remove` 명령.

## 권장 파이프라인 배포 워크플로우

다음 다이어그램은 파이프라인 배포를 사용하여 구성을 관리하는 것을 권장하는 방법을 보여줍니다.

![권장 파이프라인 배포 워크플로우](../../assets/configuration/split-deploy-workflow.png)

### 개발 시스템

개발 시스템에서는 관리자에서 구성을 변경하고 공유 구성을 생성합니다. `app/etc/config.php` 시스템별 구성을 통해 `app/etc/env.php`. 상거래 코드 및 공유 구성을 소스 제어에 확인하고 빌드 서버에 푸시합니다.

또한 확장을 설치하고 개발 시스템에서 상거래 코드를 사용자 지정해야 합니다.

개발 시스템에서:

1. 관리자에서 구성을 설정합니다.

1. 를 사용하십시오 `magento app:config:dump` 파일 시스템에 구성을 쓰는 명령

   - `app/etc/config.php` 는 모든 설정을 포함하는 공유 구성입니다 _제외_ 중요 및 시스템별 설정. 이 파일은 소스 제어에 있어야 합니다.
   - `app/etc/env.php` 는 특정 시스템(예: 호스트 이름 및 포트 번호)에 고유한 설정을 포함하는 시스템별 구성입니다. 이 파일은 _not_ 소스 제어에 있어야 합니다.

1. 소스 제어에 수정된 코드 및 공유 구성을 추가합니다.

1. 개발 중에 생성된 php 코드와 정적 자산 파일을 제거하려면 다음 명령을 실행합니다.

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

자산을 지우기 위한 명령을 실행한 후 Commerce는 작업 파일을 생성합니다.

>[!WARNING]
>
>위의 접근법에 주의하세요. 삭제 `.htacces`의 `generated` 또는 `pub` 폴더로 인해 문제가 발생할 수 있습니다.

### 빌드 시스템

빌드 시스템은 코드를 컴파일하고 상거래에 등록된 주제에 대한 정적 보기 파일을 생성합니다. 상거래 데이터베이스에 연결할 필요가 없습니다. 그것은 상거래 코드베이스만 필요합니다.

빌드 시스템에서:

1. 소스 제어에서 공유 구성 파일을 가져옵니다.
1. 를 사용하십시오 `magento setup:di:compile` 코드를 컴파일하는 명령
1. 를 사용하십시오 `magento setup:static-content:deploy -f` 정적 파일 보기 파일을 업데이트하는 명령
1. 업데이트를 소스 제어에 확인합니다.

>[!INFO]
>
>자세한 내용은 [정적 보기 파일에 대한 배포 전략](../cli/static-view-file-strategy.md).

### 프로덕션 시스템

프로덕션 시스템(즉, 라이브 스토어)에서 소스 제어에서 생성된 자산 및 코드 업데이트를 가져오고 명령줄 또는 환경 변수를 사용하여 시스템 특정 및 중요한 구성 설정을 설정합니다.

프로덕션 시스템에서 다음을 수행합니다.

1. 유지 관리 모드를 시작합니다.
1. 소스 제어에서 코드 및 구성 업데이트를 가져옵니다.
1. Adobe Commerce을 사용하는 경우 대기열 작업자를 중지합니다.
1. 를 사용하십시오 `magento app:config:import` 프로덕션 시스템에서 구성 변경 사항을 가져오는 명령
1. 데이터베이스 스키마를 변경한 구성 요소를 설치한 경우 `magento setup:upgrade --keep-generated` 데이터베이스 스키마와 데이터를 업데이트하려면 생성된 정적 파일을 유지합니다.
1. 시스템별 설정을 설정하려면 `magento config:set` 명령 또는 환경 변수.
1. 중요 설정을 설정하려면 `magento config:sensitive:set` 명령 또는 환경 변수.
1. 청결(이하 _플러시_) 캐시
1. 유지 관리 모드를 종료합니다.

## 구성 관리 명령

구성을 관리하는 데 도움이 되는 다음 명령을 제공합니다.

- [`magento app:config:dump`](../cli/export-configuration.md) 관리 구성 설정을 쓰려면 `config.php` 및 `env.php` (중요 설정 제외)
- [`magento config:set`](../cli/set-configuration-values.md) 를 클릭하여 프로덕션 시스템에서 시스템별 설정 값을 설정합니다.

   선택 사항 사용 `--lock` 관리자에서 옵션을 잠그는 옵션(즉, 설정을 편집할 수 없도록 설정). 설정이 이미 잠긴 경우 `--lock` 옵션을 사용하여 설정을 변경할 수 있습니다.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 를 클릭하여 프로덕션 시스템에서 중요한 설정 값을 설정합니다.
- [`magento app:config:import`](../cli/import-configuration.md) 구성 변경 내용을 가져올 위치 `config.php` 및 `env.php` 프로덕션 시스템에 연결할 수도 있습니다.

## 구성 관리 예

이 섹션에서는 변경 방법을 확인할 수 있도록 구성을 관리하는 예를 보여줍니다 `config.php` 및 `env.php`.

### 기본 로케일 변경

이 섹션에서는 `config.php` 관리자(**스토어** > 설정 > **구성** > 일반 > **일반** > **로케일 옵션**).

관리자에서 변경 작업을 수행한 후 `bin/magento app:config:dump` 값을 `config.php`. 값은 `general` 아래에 배열 `locale` 다음 코드 조각에서 `config.php` 표시:

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

이 섹션에서는 다음 구성을 변경하는 방법을 설명합니다.

- 웹 사이트, 저장소 및 저장소 보기 추가(**스토어** > 설정 > **모든 저장소**)
- 기본 이메일 도메인 변경(**스토어** > 설정 > **구성** > 고객 > **고객 구성**)
- PayPal API 사용자 이름 및 API 암호 설정(**스토어** > 설정 > **구성** > Sales > **결제 방법** > **PayPal** > **필수 PayPal 설정**)

관리자에서 변경 작업을 수행한 후 `bin/magento app:config:dump` 개발 시스템에서 참조할 수 있습니다. 이번에는 모든 변경 사항이 기록되지 않습니다 `config.php`; 실제로 다음 코드 조각에서 볼 수 있듯이 웹 사이트, 저장 및 저장소 보기만 해당 파일에 작성됩니다.

### config.php

`config.php` 다음 포함:

- 웹 사이트, 저장 및 저장소 보기에 대한 변경 사항입니다.
- 시스템별 검색 엔진 설정
- 민감하지 않은 PayPal 설정
- 에서 생략된 중요한 설정을 알려주는 주석입니다. `config.php`

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

기본 이메일 도메인 시스템별 구성 설정이에 작성됩니다 `app/etc/env.php`.

PayPal 설정은 `bin/magento app:config:dump` 명령에서 중요한 설정을 쓰지 않습니다. 다음 명령을 사용하여 프로덕션 시스템에서 PayPal 설정을 설정해야 합니다.

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
