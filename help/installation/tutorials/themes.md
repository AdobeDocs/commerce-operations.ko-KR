---
title: 테마 제거
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 테마를 제거합니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# 테마 제거

이 명령을 사용하기 전에 테마의 상대 경로를 알아야 합니다. 테마는 의 하위 디렉토리에 있습니다 `<magento_root>/app/design/<area name>`. 영역을 시작하는 테마 경로를 지정해야 합니다. `frontend` (상점 테마) 또는 `adminhtml` (관리자 테마의 경우)

예를 들어 Adobe Commerce 및 Magento Open Source과 함께 제공되는 Luma 테마의 경로는 입니다 `frontend/Magento/luma`.

주제에 대한 자세한 내용은 다음을 참조하십시오 [테마 구조](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## 테마 제거 개요

이 섹션에서는 파일 시스템에서 테마 코드를 포함하여 하나 이상의 테마를 제거하는 방법을 설명합니다. 백업을 먼저 만들어 나중에 데이터를 복원할 수 있습니다.

이 명령은 제거 *전용* 에 지정된 테마 `composer.json`; 즉, 작성기 패키지로 제공되는 테마를 참조하십시오. 테마가 작성기 패키지가 아닌 경우 다음을 통해 수동으로 제거해야 합니다.

* 업데이트 `parent` 노드 정보 `theme.xml` 테마에 대한 참조를 제거하려면
* 파일 시스템에서 테마 코드를 제거하는 중입니다.

   [테마 상속에 대한 자세한 정보](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## 테마 제거

명령 사용:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

위치

* `{theme path}` 은 영역 이름으로 시작하는 테마 상대 경로입니다. 예를 들어 Adobe Commerce 및 Magento Open Source과 함께 제공된 빈 테마의 경로는 다음과 같습니다 `frontend/Magento/blank`.
* `--backup-code` 다음에 나오는 단락에 설명된 대로 코드 베이스를 백업합니다.
* `--clear-static-content` 생성된 [정적 보기 파일](../../configuration/cli/static-view-file-deployment.md)- 정적 보기 파일이 제대로 표시되는 데 필요합니다.

명령은 다음 작업을 수행합니다.

1. 지정된 테마 경로가 있는지 확인합니다. 그렇지 않으면 명령이 종료됩니다.
1. 주제가 작성기 패키지인지 확인합니다. 그렇지 않으면 명령이 종료됩니다.
1. 종속성을 확인하고 충족되지 않은 종속성이 있으면 명령을 종료합니다.

   이 문제를 해결하려면 모든 테마를 동시에 제거하거나 테마에 따라 테마를 먼저 제거할 수 있습니다.

1. 테마를 사용하지 않는지 확인합니다. 사용 중인 경우 명령이 종료됩니다.
1. 주제가 가상 테마의 기반이 아닌지 확인합니다. 가상 테마인 경우 명령이 종료됩니다.
1. 저장소를 유지 관리 모드로 전환합니다.
1. If `--backup-code` 가 지정되면 다음을 제외하고 코드 베이스를 백업합니다. `pub/static`, `pub/media`, 및 `var` 디렉토리.

   백업 파일 이름은 `var/backups/<timestamp>_filesystem.tgz`

   언제든지 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령.

1. 에서 테마 제거 `theme` 데이터베이스 테이블.
1. 다음을 사용하여 코드 베이스에서 테마 제거 `composer remove`.
1. 캐시를 삭제합니다.
1. 생성된 클래스를 정리합니다.
1. If `--clear-static-content` 이(가) 지정되면, [생성된 정적 보기 파일](../../configuration/cli/static-view-file-deployment.md).

예를 들어 다른 테마가 종속되는 테마를 제거하려고 하면 다음 메시지가 표시됩니다.

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

코드 베이스를 백업하는 것과 같이 두 테마를 동시에 제거하는 것이 한 가지 대안입니다.

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

다음과 유사한 메시지가 표시됩니다.

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
>관리 테마를 제거하려면 구성 요소의 종속성 삽입 구성에서도 제거해야 합니다. `<component root directory>/etc/di.xml`.
