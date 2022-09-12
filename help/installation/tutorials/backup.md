---
title: 파일 시스템, 미디어 및 데이터베이스 백업 및 롤백
description: 다음 단계에 따라 Adobe Commerce 또는 Magento Open Source 애플리케이션을 백업 및 복원합니다.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# 파일 시스템, 미디어 및 데이터베이스 백업 및 롤백

이 명령을 사용하여 다음을 백업할 수 있습니다.

* 파일 시스템(제외) `var` 및 `pub/static` directory)
* 다음 `pub/media` directory
* 데이터베이스

백업은 `var/backups` 디렉토리 및 를 사용하여 언제든지 복원할 수 있습니다. [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령.

백업 후 다음을 수행할 수 있습니다 [롤백](#rollback) 나중에.

>[!TIP]
>
>클라우드 인프라 프로젝트에 대한 Adobe Commerce의 경우 다음을 참조하십시오. [스냅샷 및 백업 관리](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 에서 _클라우드 안내서_.

## 백업 활성화

기본적으로 백업 기능은 비활성화됩니다. 활성화하려면 다음 CLI 명령을 입력합니다.

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**사용 중지 알림:**
>백업 기능은 2.1.16, 2.2.7 및 2.3.0에서 더 이상 사용되지 않습니다. 추가 백업 기술 및 이진 백업 도구(예: Percona XtraBackup)를 조사하는 것이 좋습니다.

## 열린 파일 제한 설정

이전 백업으로 롤백하는 작업이 자동으로 실패하여 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령.

너무 많은 재귀 호출로 인해 긴 쿼리 문자열로 인해 사용자의 할당된 메모리 공간이 메모리가 부족한 경우가 있습니다.

## 열린 파일을 설정하는 방법 `ulimit`

열린 파일을 설정하는 것이 좋습니다 [`ulimit`](https://ss64.com/bash/ulimit.html) 파일 시스템 사용자가 `65536` 더 이상

명령줄에서 이 작업을 수행하거나 셸 스크립트를 편집하여 사용자에 대한 영구 설정을 만들 수 있습니다.

계속하기 전에 아직 수행하지 않았다면 로 전환합니다. [파일 시스템 소유자](../prerequisites/file-system/overview.md).

명령:

```bash
ulimit -s 65536
```

필요한 경우 이 값을 더 큰 값으로 변경할 수 있습니다.

>[!NOTE]
>
>열린 파일의 구문 `ulimit` 는 사용하는 UNIX 셸에 따라 다릅니다. 이전 설정은 Bash 셸과 함께 CentOS 및 Ubuntu에서 작동해야 합니다. 그러나 macOS의 경우 올바른 설정은 다음과 같습니다 `ulimit -S 65532`. 자세한 내용은 매뉴얼 페이지 또는 운영 체제 참조를 참조하십시오.

사용자의 Bash 셸에서 선택적으로 값을 설정하려면 다음을 수행합니다.

1. 아직 수행하지 않았다면 로 전환합니다. [파일 시스템 소유자](../prerequisites/file-system/overview.md).
1. 열기 `/home/<username>/.bashrc` 텍스트 편집기에서 을 참조하십시오.
1. 다음 줄을 추가합니다.

   ```bash
   ulimit -s 65536
   ```

1. 변경 내용을 `.bashrc` 텍스트 편집기를 종료합니다.

>[!WARNING]
>
>에 대한 값을 설정하지 않는 것이 좋습니다 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 에서 `php.ini` 실패 알림 없이 롤백이 불완전할 수 있으므로 파일입니다.

## 백업

명령 사용:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

명령은 다음 작업을 수행합니다.

1. 저장소를 유지 관리 모드로 전환합니다.
1. 다음 명령 옵션 중 하나를 실행합니다.

   | 옵션 | 의미 | 백업 파일 이름 및 위치 |
   |--- |--- |--- |
   | `--code` | 파일 시스템을 백업합니다(var 및 pub/static 디렉토리 제외). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | pub/media 디렉토리를 백업합니다. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 데이터베이스를 백업합니다. | `var/backups/<timestamp>/_db.sql` |

1. 저장소를 유지 관리 모드에서 해제합니다.

예를 들어 파일 시스템 및 데이터베이스를 백업하려면

```bash
bin/magento setup:backup --code --db
```

다음과 유사한 메시지가 표시됩니다.

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## 롤백

이 섹션에서는 이전에 수행한 백업으로 롤백하는 방법을 설명합니다. 복원할 백업 파일의 파일 이름을 알고 있어야 합니다.

백업 이름을 찾으려면 다음을 입력합니다.

```bash
bin/magento info:backups:list
```

백업 파일 이름의 첫 번째 문자열은 타임스탬프입니다.

이전 백업으로 롤백하려면 다음을 입력합니다.

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

예를 들어 이름이 인 미디어 백업을 복원하려면 `1440611839_filesystem_media.tgz`, 입력

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

다음과 유사한 메시지가 표시됩니다.

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
