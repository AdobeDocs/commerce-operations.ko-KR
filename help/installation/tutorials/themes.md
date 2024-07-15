---
title: 테마 제거
description: Adobe Commerce 테마를 제거하려면 다음 단계를 따르십시오.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 테마 제거

이 명령을 사용하기 전에 테마의 상대 경로를 알고 있어야 합니다. 테마는 `<magento_root>/app/design/<area name>`의 하위 디렉터리에 있습니다. 영역으로 시작하는 테마의 경로를 지정해야 합니다. `frontend`(상점 테마) 또는 `adminhtml`(관리자 테마)입니다.

예를 들어 Adobe Commerce과 함께 제공되는 Luma 테마의 경로는 `frontend/Magento/luma`입니다.

테마에 대한 자세한 내용은 [테마 구조](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/)를 참조하세요.

## 테마 제거 개요

이 섹션에서는 하나 이상의 테마를 제거하는 방법에 대해 설명합니다(필요한 경우 파일 시스템에서 테마 코드 포함). 나중에 데이터를 복원할 수 있도록 백업을 먼저 만들 수 있습니다.

이 명령은 `composer.json`에 지정된 *전용*&#x200B;개 테마, 즉 Composer 패키지로 제공되는 테마를 제거합니다. 테마가 작성기 패키지가 아닌 경우 다음을 수행하여 수동으로 제거해야 합니다.

* 테마에 대한 참조를 제거하기 위해 `theme.xml`에서 `parent` 노드 정보를 업데이트하는 중입니다.
* 파일 시스템에서 테마 코드 제거.

  [테마 상속에 대한 추가 정보](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## 테마 제거

명령 사용:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

위치

* `{theme path}`은(는) 영역 이름으로 시작하는 테마의 상대 경로입니다. 예를 들어 Adobe Commerce에서 제공한 빈 테마의 경로는 `frontend/Magento/blank`입니다.
* `--backup-code`은(는) 다음 단락에서 설명한 대로 코드 베이스를 백업합니다.
* `--clear-static-content`은(는) 생성된 [정적 보기 파일](../../configuration/cli/static-view-file-deployment.md)을(를) 정리합니다. 정적 보기 파일이 제대로 표시되도록 하는 데 필요합니다.

이 명령은 다음 작업을 수행합니다.

1. 지정된 테마 경로가 있는지 확인하고, 없다면 명령이 종료됩니다.
1. 테마가 작성기 패키지인지 확인합니다. 그렇지 않으면 명령이 종료됩니다.
1. 종속성을 확인하고 충족되지 않는 종속성이 있으면 명령을 종료합니다.

   이 문제를 해결하려면 모든 테마를 동시에 제거하거나 먼저 테마에 따라 를 제거할 수 있습니다.

1. 테마가 사용되고 있지 않은지 확인합니다. 사용되고 있으면 명령이 종료됩니다.
1. 테마가 가상 테마의 기준이 아닌지 확인합니다. 테마가 가상 테마의 기준이 되면 명령이 종료됩니다.
1. 저장소를 유지 관리 모드로 전환합니다.
1. `--backup-code`이(가) 지정된 경우 `pub/static`, `pub/media` 및 `var` 디렉터리를 제외하고 코드베이스를 백업합니다.

   백업 파일 이름은 `var/backups/<timestamp>_filesystem.tgz`입니다.

   [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령을 사용하여 언제든지 백업을 복원할 수 있습니다.

1. `theme` 데이터베이스 테이블에서 테마를 제거합니다.
1. `composer remove`을(를) 사용하여 코드 기반에서 테마를 제거합니다.
1. 캐시를 지웁니다.
1. 생성된 클래스 정리
1. `--clear-static-content`이(가) 지정된 경우 [생성된 정적 보기 파일을 정리](../../configuration/cli/static-view-file-deployment.md)합니다.

예를 들어 다른 테마가 종속된 테마를 제거하려고 하면 다음 메시지가 표시됩니다.

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

한 가지 대안은 코드베이스를 백업하는 다음과 같이 두 테마를 동시에 제거하는 것입니다.

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

다음 디스플레이와 유사한 메시지:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>관리 테마를 제거하려면 구성 요소의 종속성 삽입 구성 `<component root directory>/etc/di.xml`에서도 제거해야 합니다.
