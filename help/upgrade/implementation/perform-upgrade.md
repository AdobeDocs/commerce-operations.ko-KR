---
title: 업그레이드 수행
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 프로젝트를 업그레이드하십시오.
source-git-commit: 3c3966a904b0568e0255020d8880d348c357ea95
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 업그레이드 수행

다음 방법으로 소프트웨어를 설치한 경우 명령줄에서 Adobe Commerce 또는 Magento Open Source 응용 프로그램을 업그레이드할 수 있습니다.

- 다운로드 [메타카지](https://glossary.magento.com/metapackage) 사용 `composer create-project` 명령.
- 압축된 아카이브 설치

>[!NOTE]
>
>GitHub 리포지토리를 복제한 경우 이 메서드를 사용하여 업그레이드하지 마십시오. 대신 다음을 참조하십시오 [Git 기반 설치 업그레이드](../developer/git-installs.md) 업그레이드 지침

다음 지침은 작성기를 사용하여 업그레이드하는 방법을 보여줍니다. Adobe Commerce 2.4.2 에서는 작성기 2에 대한 지원을 도입했습니다. &lt;2.4.1에서 업그레이드하려는 경우 먼저 작성기 1을 사용하여 작성기 2(예: 2.4.2)와 호환되는 버전으로 업그레이드해야 합니다 _이전_ 2.4.2 업그레이드를 위해 작성기 2로 업그레이드 또한 [지원되는 버전](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) PHP의 세그먼트입니다.

>[!WARNING]
>
>Adobe Commerce 및 Magento Open Source 업그레이드 절차가 변경되었습니다. 새 버전의 를 설치해야 합니다 `magento/composer-root-update-plugin` 패키지(참조) [전제 조건](../prepare/prerequisites.md)). 또한 업그레이드 명령이 `composer require magento/<package_name>` to `composer require-commerce magento/<package_name>`.

## 시작하기 전에

를 완료해야 합니다. [업그레이드 사전 요구 사항](../prepare/prerequisites.md) 업그레이드 프로세스를 시작하기 전에 환경을 준비하십시오.

## 패키지 관리

>[!NOTE]
>
>다른 릴리스 수준을 지정하는 데 도움이 필요하면 이 섹션의 끝에 있는 예를 참조하십시오. 예를 들어 부 릴리스, 품질 패치 및 보안 패치가 있습니다. Adobe Commerce 고객은 GA(General Availability) 날짜 2주 전에 패치에 액세스할 수 있습니다. 사전 릴리스 패키지는 작성기를 통해서만 사용할 수 있습니다. GA되기 전까지는 다운로드 포털 또는 GitHub에서 찾을 수 없습니다. 작성기에서 이러한 패키지를 찾을 수 없는 경우 Adobe Commerce 지원 센터에 문의하십시오.

1. 업그레이드 프로세스 중에 저장소에 액세스할 수 없도록 유지 관리 모드로 전환합니다.

   ```bash
   bin/magento maintenance:enable
   ```

   자세한 내용은 [유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) 추가 옵션을 보려면 선택적으로, [사용자 지정 유지 관리 모드 페이지](https://devdocs.magento.com/guides/v2.4/comp-mgr/trouble/cman/maint-mode.html).

1. 메시지 큐 소비자와 같은 비동기 프로세스가 실행되는 동안 업그레이드 프로세스를 시작하면 데이터가 손상될 수 있습니다. 데이터 손상을 방지하려면 모든 크론 작업을 비활성화합니다.

   _Adobe Commerce on cloud 인프라:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. 모든 메시지 큐 소비자를 수동으로 시작하여 모든 메시지가 소비되는지 확인합니다.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   크론 작업이 완료될 때까지 기다립니다. 프로세스 뷰어를 사용하거나 `ps aux | grep 'bin/magento queue'` 모든 프로세스가 완료될 때까지 여러 번 명령

1. 의 백업 만들기 `composer.json` 파일.

   ```bash
   cp composer.json composer.json.bak
   ```

1. 필요에 따라 특정 패키지를 추가하거나 제거합니다.

   예를 들어 Magento Open Source에서 Adobe Commerce으로 업그레이드하는 경우 Magento Open Source 패키지를 제거합니다.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   샘플 데이터를 업그레이드할 수도 있습니다.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. 다음을 사용하여 인스턴스를 업그레이드합니다 `composer require-commerce` 명령 구문:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   명령 옵션은 다음과 같습니다.

   - `<product>` — (필수) 업그레이드할 패키지입니다. 온-프레미스 설치의 경우 이 값은 다음 중 하나여야 합니다 `product-community-edition` 또는 `product-enterprise-edition`.

   - `<version>` —(필수) 업그레이드할 Adobe Commerce 또는 Magento Open Source 버전입니다. For example, `2.4.3`.

   - `--no-update` —(필수) 종속성을 자동으로 업데이트합니다.

   - `--interactive-root-conflicts` —(선택 사항) 이전 버전의 모든 최신 값 또는 업그레이드 중인 버전과 일치하지 않는 사용자 지정된 값을 대화식으로 보고 업데이트할 수 있습니다.

   - `--force-root-updates` —(선택 사항) 충돌하는 모든 사용자 지정 값을 예상 Magento 값으로 무시합니다.

   - `--help` —(선택 사항) 플러그인에 대한 사용 세부 사항을 제공합니다.
   둘 중 어느 것도 아니면 `--interactive-root-conflicts` 아니요 `--force-root-updates` 지정한 경우, 이 명령은 충돌에 있는 기존 값을 유지하고 경고 메시지를 표시합니다. 플러그인에 대한 자세한 내용은 [플러그인 사용 README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. 종속성을 업데이트합니다.

   ```bash
   composer update
   ```

### 예 - 사용 가능한 버전 나열

사용 가능한 2.4.x 버전의 전체 목록을 보려면 다음을 수행하십시오.

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 예 - 부 릴리스

부 릴리스에는 새로운 기능, 품질 수정 및 보안 수정 사항이 포함되어 있습니다. Composer를 사용하여 부 릴리스를 지정합니다. 예를 들어 Magento Open Source 2.4.3 메타패키지를 지정하려면 다음을 수행합니다.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### 예 - 품질 패치

품질 패치는 주로 기능성을 포함합니다 _및_ 보안 수정 사항. 그러나 경우에 따라 이전 버전과 호환되는 새로운 기능이 포함될 수 있습니다. Composer를 사용하여 품질 패치를 다운로드합니다. 예를 들어 Magento Open Source 2.4.1 메타패키지를 지정하려면 다음을 수행합니다.

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### 예 - 보안 패치

보안 패치에는 보안 수정 사항만 포함되어 있습니다. 업그레이드 프로세스를 빠르고 쉽게 수행할 수 있도록 설계되었습니다.

보안 패치는 작성기 이름 지정 규칙을 사용합니다 `2.4.x-px`. 작성기를 사용하여 패치를 지정합니다.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## 메타데이터 업데이트

1. 업데이트 `"name"`, `"version"`, 및 `"description"` 의 필드 `composer.json` 필요에 따라 파일을 사용하십시오.

   >[!NOTE]
   >
   >에서 메타데이터 업데이트 `composer.json` 파일은 완전히 피상적이며 작동하지 않습니다.

1. 업데이트를 적용합니다.

   ```bash
   composer update
   ```

1. 지우기 `var/` 및 `generated/` 하위 디렉토리:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Redis 또는 Memcached와 같은 파일 시스템 이외의 캐시 저장소를 사용하는 경우 캐시도 수동으로 지워야 합니다.

1. 데이터베이스 스키마 및 데이터를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. 유지 관리 모드를 비활성화합니다.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(선택 사항)_ Varnish를 다시 시작합니다.

   페이지 캐싱에 Varnish를 사용하는 경우 다음을 다시 시작합니다.

   ```bash
   service varnish restart
   ```

## 작업 확인

웹 브라우저에서 저장소 URL을 열어 업그레이드가 성공했는지 확인합니다. 업그레이드가 실패한 경우 스토어가 제대로 로드되지 않습니다.

애플리케이션이  `We're sorry, an error has occurred while generating this email.` 오류:

1. 재설정 [파일 시스템 소유권 및 권한](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html) 를 `root` 권한.
1. 다음 디렉터리를 지웁니다.
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 웹 브라우저에 있는 스토어를 다시 확인하십시오.
