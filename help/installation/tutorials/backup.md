---
title: 파일 시스템, 미디어 및 데이터베이스 백업 및 롤백
description: 다음 단계에 따라 Adobe Commerce 애플리케이션을 백업하고 복원합니다.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# 파일 시스템, 미디어 및 데이터베이스 백업 및 롤백

이 명령을 사용하면 다음을 백업할 수 있습니다.

* 파일 시스템(`var` 및 `pub/static` 디렉터리 제외)
* `pub/media` 디렉터리
* 데이터베이스

백업은 `var/backups` 디렉터리에 저장되며 언제든지 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령을 사용하여 복원할 수 있습니다.

백업 후 나중에 [롤백](#rollback)할 수 있습니다.

>[!TIP]
>
>클라우드 인프라 프로젝트의 Adobe Commerce에 대해서는 _클라우드 가이드_&#x200B;에서 [스냅샷 및 백업 관리](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)를 참조하십시오.

## 백업 활성화

백업 기능은 기본적으로 비활성화되어 있습니다. 활성화하려면 다음 CLI 명령을 입력합니다.

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**사용 중단 알림:**
>백업 기능은 2.1.16, 2.2.7 및 2.3.0부터 더 이상 사용되지 않습니다. 추가 백업 기술 및 바이너리 백업 도구(예: Percona XtraBackup)를 조사하는 것이 좋습니다.

## 열린 파일 제한 설정

이전 백업으로 롤백하면 자동으로 실패하여 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 명령을 사용하여 불완전한 데이터가 파일 시스템 또는 데이터베이스에 기록됩니다.

경우에 따라 긴 쿼리 문자열로 인해 재귀 호출이 너무 많기 때문에 사용자의 할당된 메모리 공간에 메모리가 부족해지기도 합니다.

## 열린 파일 `ulimit`을(를) 설정하는 방법

파일 시스템 사용자에 대한 열린 파일 [`ulimit`](https://ss64.com/bash/ulimit.html)을(를) `65536` 이상의 값으로 설정하는 것이 좋습니다.

이 작업은 명령줄에서 수행하거나 셸 스크립트를 편집하여 사용자에게 영구적으로 설정할 수 있습니다.

계속하기 전에 [파일 시스템 소유자](../prerequisites/file-system/overview.md)(으)로 전환하십시오.

명령:

```bash
ulimit -s 65536
```

필요한 경우 이 값을 더 큰 값으로 변경할 수 있습니다.

>[!NOTE]
>
>열린 파일 `ulimit`의 구문은 사용하는 UNIX 셸에 따라 다릅니다. 앞의 설정은 CentOS와 Ubuntu에서 Bash 셸과 함께 작동해야 합니다. 그러나 macOS의 경우 올바른 설정은 `ulimit -S 65532`입니다. 자세한 내용은 매뉴얼 페이지 또는 운영 체제 참조를 참조하십시오.

선택적으로 사용자의 기본 셸에 값을 설정하려면 다음을 수행합니다.

1. 아직 수행하지 않았다면 [파일 시스템 소유자](../prerequisites/file-system/overview.md)(으)로 전환하십시오.
1. 텍스트 편집기에서 `/home/<username>/.bashrc` 열기
1. 다음 줄을 추가합니다.

   ```bash
   ulimit -s 65536
   ```

1. 변경 내용을 `.bashrc`에 저장하고 텍스트 편집기를 종료합니다.

>[!WARNING]
>
>실패 알림 없이 불완전한 롤백을 초래할 수 있으므로 `php.ini` 파일에서 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php)의 값을 설정하지 않는 것이 좋습니다.

## 백업

명령 사용:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

이 명령은 다음 작업을 수행합니다.

1. 저장소를 유지 관리 모드로 전환합니다.
1. 다음 명령 옵션 중 하나를 실행합니다.

   | 옵션 | 의미 | 백업 파일 이름 및 위치 |
   |--- |--- |--- |
   | `--code` | 파일 시스템을 백업합니다(var 및 pub/static 디렉터리 제외). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | pub/media 디렉터리를 백업합니다. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 데이터베이스 백업. | `var/backups/<timestamp>/_db.sql` |

1. 유지 관리 모드에서 스토어를 제거합니다.

예를 들어 파일 시스템 및 데이터베이스를 백업하려면

```bash
bin/magento setup:backup --code --db
```

다음 디스플레이와 유사한 메시지:

```
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

이 섹션에서는 이전에 수행한 백업으로 롤백하는 방법에 대해 설명합니다. 복원할 백업 파일의 파일 이름을 알고 있어야 합니다.

백업의 이름을 찾으려면 다음을 입력합니다.

```bash
bin/magento info:backups:list
```

백업 파일 이름의 첫 번째 문자열은 타임스탬프입니다.

이전 백업으로 롤백하려면 다음을 입력합니다.

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

예를 들어 이름이 `1440611839_filesystem_media.tgz`인 미디어 백업을 복원하려면 다음을 입력하십시오.

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

다음 디스플레이와 유사한 메시지:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
