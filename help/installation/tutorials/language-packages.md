---
title: 언어 패키지 제거
description: Adobe Commerce 언어 패키지를 제거하려면 다음 단계를 따르십시오.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 언어 패키지 제거

이 섹션에서는 하나 이상의 언어 패키지를 제거하는 방법에 대해 설명합니다(필요한 경우 파일 시스템에서 언어 패키지의 코드 포함). 나중에 데이터를 복원할 수 있도록 백업을 먼저 만들 수 있습니다.

이 명령은 *에 지정된* only`composer.json` 언어 패키지, 즉 Composer 패키지로 제공되는 언어 패키지를 제거합니다. 언어 패키지가 작성기 패키지가 아닌 경우 파일 시스템에서 언어 패키지 코드를 제거하여 수동으로 제거해야 합니다.

[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령을 사용하여 언제든지 백업을 복원할 수 있습니다.

명령 사용:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

언어 패키지 제거 명령은 다음 작업을 수행합니다.

1. 종속성을 확인합니다. 종속성이 있으면 명령이 종료됩니다.

   이 문제를 해결하려면 모든 종속 언어 패키지를 동시에 제거하거나 먼저 종속 언어 패키지를 제거할 수 있습니다.

1. `--backup code`이(가) 지정된 경우 `var` 및 `pub/static` 디렉터리를 제외한 파일 시스템을 `var/backups/<timestamp>_filesystem.tgz`에 백업하십시오.
1. `composer remove`을(를) 사용하여 코드 베이스에서 언어 패키지 파일을 제거합니다.
1. 캐시를 지웁니다.

예를 들어 다른 언어 패키지가 종속된 언어 패키지를 제거하려고 하면 다음 메시지가 표시됩니다.

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

코드베이스를 백업한 후 두 언어 패키지를 모두 제거하는 방법이 있습니다.

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

다음 디스플레이와 유사한 메시지:

```
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
