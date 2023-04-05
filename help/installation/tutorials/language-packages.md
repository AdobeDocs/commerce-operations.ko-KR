---
title: 언어 패키지 제거
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 언어 패키지를 제거합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# 언어 패키지 제거

이 섹션에서는 하나 이상의 언어 패키지를 제거하는 방법을 설명합니다. 선택적으로 파일 시스템에서 언어 패키지의 코드를 포함합니다. 백업을 먼저 만들어 나중에 데이터를 복원할 수 있습니다.

이 명령은 제거 *전용* 에 지정된 언어 패키지 `composer.json`; 즉, 작성기 패키지로 제공되는 언어 패키지입니다. 언어 패키지가 작성기 패키지가 아닌 경우 파일 시스템에서 언어 패키지 코드를 제거하여 수동으로 제거해야 합니다.

언제든지 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령.

명령 사용:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

언어 패키지 제거 명령은 다음 작업을 수행합니다.

1. 종속성을 확인합니다. 그런 경우 명령이 종료됩니다.

   이 문제를 해결하려면 모든 종속 언어 패키지를 동시에 제거하거나 종속 언어 패키지를 먼저 제거할 수 있습니다.

1. If `--backup code` 이(가) 지정되면 파일 시스템을 백업(제외) `var` 및 `pub/static` 디렉토리) `var/backups/<timestamp>_filesystem.tgz`
1. 다음을 사용하여 코드 베이스에서 언어 패키지 파일을 제거합니다 `composer remove`.
1. 캐시를 삭제합니다.

예를 들어 다른 언어 패키지가 사용하는 언어 패키지를 제거하려고 하면 다음 메시지가 표시됩니다.

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

한 가지 방법은 코드 베이스를 백업한 후 두 언어 패키지를 제거하는 것입니다.

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

다음과 유사한 메시지가 표시됩니다.

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
