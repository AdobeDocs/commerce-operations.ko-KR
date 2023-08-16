---
title: 모듈 제거
description: Adobe Commerce 또는 Magento Open Source 모듈을 제거하려면 다음 단계를 따르십시오.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# 모듈 제거

이 섹션에서는 하나 이상의 모듈을 제거하는 방법에 대해 설명합니다. 제거하는 동안 선택적으로 모듈의 코드, 데이터베이스 스키마 및 데이터베이스 데이터를 제거할 수 있습니다. 나중에 데이터를 복구할 수 있도록 백업을 먼저 만들 수 있습니다.

모듈을 사용하지 않을 것이 확실한 경우에만 해당 모듈을 제거해야 합니다. 에 설명된 대로 모듈을 제거하는 대신 비활성화할 수 있습니다 [모듈 활성화 또는 비활성화](manage-modules.md).

>[!NOTE]
>
>이 명령은 선언된 종속성만 `composer.json` 파일. 다음 모듈을 제거하는 경우: _아님_ 다음에 정의됨: `composer.json` 파일, 이 명령은 종속성을 확인하지 않고 모듈을 제거합니다. 이 명령은 다음을 수행합니다 _아님_&#x200B;그러나 파일 시스템에서 모듈의 코드를 제거합니다. 모듈의 코드를 제거하려면 파일 시스템 도구를 사용해야 합니다(예: `rm -rf <path to module>`). 또는 다음을 수행할 수 있습니다. [disable](manage-modules.md) 비작성기 모듈.

명령 사용:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

위치 `{ModuleName}` 의 모듈 이름을 지정합니다. `<VendorName>_<ModuleName>` 포맷. 예를 들어 고객 모듈 이름은 입니다. `Magento_Customer`. 모듈 이름 목록을 가져오려면 다음을 입력합니다 `magento module:status`

모듈 제거 명령은 다음 작업을 수행합니다.

1. 지정된 모듈이 코드 베이스에 있고 Composer에서 설치한 패키지인지 확인합니다.

   이 명령은 작동합니다 _전용_ (Composer 패키지로 정의된 모듈 포함)

1. 다른 모듈과의 종속성을 확인하고 충족되지 않는 종속성이 있으면 명령을 종료합니다.

   이 문제를 해결하려면 모든 모듈을 동시에 제거하거나 종속 모듈을 먼저 제거할 수 있습니다.

1. 계속하려면 확인을 요청하십시오.
1. 저장소를 유지 관리 모드로 전환합니다.
1. 다음 명령 옵션을 처리합니다.

   | 옵션 | 의미 | 백업 파일 이름 및 위치 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | 파일 시스템 백업(제외) `var` 및 `pub/static` 디렉토리). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | pub/media 디렉터리를 백업합니다. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | 데이터베이스 백업. | `var/backups/<timestamp>_db.gz` |

1. If `--remove-data` 을(를) 지정했으면 모듈에 정의된 데이터베이스 스키마와 데이터를 `Uninstall` 클래스입니다.

   제거할 각 모듈에 대해 는 `uninstall` 메서드 in its `Uninstall` 클래스. 이 클래스는 다음에서 상속되어야 합니다. [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 에서 지정된 모듈을 제거합니다. `setup_module` 데이터베이스 테이블.
1. 의 모듈 목록에서 지정된 모듈을 제거합니다. [배포 구성](../../configuration/reference/deployment-files.md).
1. 다음을 사용하여 코드베이스에서 코드 제거 `composer remove`.

   >[!NOTE]
   >
   >모듈 제거 _항상_ 실행 `composer remove`. 다음 `--remove-data` 옵션은 모듈에서 정의한 데이터베이스 데이터와 스키마를 제거합니다. `Uninstall` 클래스.

1. 캐시를 지웁니다.
1. 생성된 클래스를 업데이트합니다.
1. If `--clear-static-content` 이(가) 지정되어 있습니다. 정리 [생성된 정적 보기 파일](../../configuration/cli/static-view-file-deployment.md).
1. 유지 관리 모드에서 스토어를 제거합니다.

예를 들어 다른 모듈이 종속된 모듈을 제거하려고 하면 다음 메시지가 표시됩니다.

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

한 가지 방법은 모듈 파일 시스템을 백업한 후 두 모듈을 모두 제거하는 것입니다. `pub/media` 파일 및 데이터베이스 테이블 _아님_ 모듈의 데이터베이스 스키마 또는 데이터 제거:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

다음 디스플레이와 유사한 메시지:

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>다른 모듈에 종속된 모듈을 제거하려고 하면 오류가 표시됩니다. 이 경우 모듈 하나를 제거할 수 없으며 두 모듈을 모두 제거해야 합니다.

## 파일 시스템, 데이터베이스 또는 미디어 파일 롤백

코드베이스를 백업한 상태로 복원하려면 다음 명령을 사용합니다.

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

위치 `<filename>` 는 의 백업 파일 이름입니다. `<app_root>/var/backups` 디렉토리. 백업 파일 목록을 표시하려면 다음을 입력합니다 `magento info:backups:list`

>[!WARNING]
>
>이 명령은 지정된 파일 또는 데이터베이스를 복원하기 전에 삭제합니다. 예를 들어 `--media-file` 옵션은 아래에 있는 미디어 자산을 삭제합니다. `pub/media` 지정된 롤백 파일에서 복구하기 전의 디렉토리입니다. 이 명령을 사용하기 전에 유지할 파일 시스템이나 데이터베이스를 변경하지 않았는지 확인하십시오.

>[!NOTE]
>
>사용 가능한 백업 파일 목록을 표시하려면 다음을 입력합니다 `magento info:backups:list`

이 명령은 다음 작업을 수행합니다.

1. 저장소를 유지 관리 모드로 전환합니다.
1. 백업 파일 이름을 확인합니다.
1. 코드 롤백 파일을 지정하는 경우:

   a. 롤백 대상 위치가 쓰기 가능한지 확인합니다(참고: `pub/static` 및 `var` 폴더는 무시됩니다).

   b. 응용 프로그램 설치 디렉터리 아래의 모든 파일과 디렉터리를 삭제합니다.

   c. 아카이브 파일을 대상 위치로 추출합니다.

1. 데이터베이스 롤백 파일을 지정하는 경우:

   a. 전체 데이터베이스를 삭제합니다.

   b. 데이터베이스 백업을 사용하여 데이터베이스를 복원합니다.

1. 미디어 롤백 파일을 지정하는 경우:

   a. 롤백 대상 위치가 쓰기 가능한지 확인합니다.

   b. 아래의 모든 파일 및 디렉터리를 삭제합니다. `pub/media`

   c. 아카이브 파일을 대상 위치로 추출합니다.

1. 유지 관리 모드에서 스토어를 제거합니다.

예를 들어 코드(파일 시스템) 백업을 복원하려면 다음 명령을 표시된 순서대로 입력합니다.

* 백업 목록 표시:

  ```bash
  magento info:backups:list
  ```

* 이름이 인 파일 백업 복원 `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  다음 디스플레이와 유사한 메시지:

  ```terminal
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>을(를) 실행하려면 `magento` 디렉토리를 변경하지 않고 다시 명령하므로 `cd pwd`.
