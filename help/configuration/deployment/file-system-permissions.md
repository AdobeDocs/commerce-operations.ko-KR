---
title: 파일 시스템 액세스 권한
description: 개발 및 프로덕션 시스템에 대한 Commerce 애플리케이션 파일 시스템의 소유자 또는 소유자를 설정하는 방법을 참조하십시오.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# 파일 시스템 액세스 권한

이 섹션에서는 개발 및 프로덕션 시스템에 대한 Commerce 파일 시스템의 소유자 또는 소유자를 설정하는 방법에 대해 설명합니다. 계속하기 전에 [파일 시스템 소유권 및 사용 권한 개요](../../installation/prerequisites/file-system/overview.md)에서 설명한 개념을 검토하십시오.

이 항목에서는 Commerce 개발 및 프로덕션 시스템에 중점을 둡니다. Commerce을 설치하는 경우 [사전 설치 소유권 및 권한 설정](../../installation/prerequisites/file-system/configure-permissions.md)을 참조하십시오.

다음 섹션에서는 하나 또는 두 개의 파일 시스템 소유자에 대한 요구 사항에 대해 설명합니다. 즉,

- **한 명의 사용자** - 일반적으로 서버의 한 명의 사용자만 액세스할 수 있는 공유 호스팅 공급자에 필요합니다. 이 사용자는 FTP를 사용하여 로그인하고 파일을 전송할 수 있으며 이 사용자는 웹 서버도 실행합니다.

- **두 명의 사용자**—자체 Commerce 서버를 실행하는 경우 두 명의 사용자를 권장합니다. 하나는 파일을 전송하고 명령줄 유틸리티를 실행하는 것이고, 다른 하나는 웹 서버 소프트웨어용 사용자입니다. 가능하면 보다 안전하기 때문에 이것이 바람직하다.

  대신 별도의 사용자가 있습니다.

   - 관리자 및 상점 첫 페이지를 실행하는 웹 서버 사용자.

   - 서버에 로그인하는 데 사용할 수 있는 로컬 사용자 계정인 _명령줄 사용자_&#x200B;입니다. 이 사용자는 Commerce cron job 및 명령줄 유틸리티를 실행합니다.

## 공유 호스팅을 위한 프로덕션 파일 시스템 소유권(사용자 1명)

1인 설정을 사용하려면 웹 서버를 실행하는 사용자와 동일한 사용자로 Commerce 서버에 로그인해야 합니다. 이는 공유 호스팅에 일반적으로 사용됩니다.

파일 시스템 소유자가 한 명인 경우 보안성이 떨어지기 때문에 가능한 경우 공유 호스팅이 아닌 개인 서버에 프로덕션에 Commerce을 배포하는 것이 좋습니다.

### 기본 또는 개발자 모드에 대해 하나의 소유자 설정

기본 또는 개발자 모드에서 다음 디렉터리는 사용자가 쓸 수 있어야 합니다.

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 기타 모든 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

이러한 권한은 명령줄 또는 공유 호스팅 공급자가 제공하는 파일 관리자 응용 프로그램을 사용하여 설정할 수 있습니다.

### 프로덕션 모드에 대해 한 명의 소유자 설정

사이트를 프로덕션에 배포할 준비가 되면 보안을 강화하기 위해 다음 디렉토리에 있는 파일에서 쓰기 액세스 권한을 제거해야 합니다.

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 기타 모든 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

구성 요소를 업데이트하거나 새 구성 요소를 설치하거나 Commerce 소프트웨어를 업그레이드하려면 앞의 모든 디렉토리를 읽기/쓰기로 설정해야 합니다.

#### 코드 파일 및 디렉터리를 읽기 전용으로 만들기

웹 서버 사용자 그룹에서 파일 및 디렉터리에 대한 쓰기 권한을 제거하려면 다음과 같이 하십시오.

1. Commerce 서버에 로그인.

1. Commerce 설치 디렉토리로 변경합니다.

1. 프로덕션 모드로 변경합니다.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 다음 디렉터리에 대한 쓰기 권한을 제거합니다.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 명령줄 도구를 실행 가능한 것으로 만듭니다.

   ```bash
   chmod u+x bin/magento
   ```

#### 코드 파일 및 디렉터리를 쓰기 가능 상태로 만들기

구성 요소를 업데이트하고 Commerce 소프트웨어를 업그레이드할 수 있도록 파일과 디렉터리를 쓰기 가능으로 설정하려면 다음을 수행하십시오.

1. Commerce 서버에 로그인.
1. Commerce 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   chmod -R u+w .
   ```

### 선택적으로 `magento_umask` 설정

[설치 안내서](../../installation/next-steps/set-umask.md)에서 _필요에 따라 umask 설정_&#x200B;을 참조하십시오.

## 비공개 호스팅을 위한 운영 파일 시스템 소유권(사용자 2명)

자체 서버(호스팅 공급자의 개인 서버 설정 포함)를 사용하는 경우 두 명의 사용자가 있습니다.

- **웹 서버 사용자**(관리자 및 상점)을 실행합니다.

  Linux 시스템은 일반적으로 이 사용자에게 셸을 제공하지 않습니다. Commerce 서버에 웹 서버 사용자로 로그인하거나 웹 서버 사용자로 전환할 수 없습니다.

- Commerce 서버에 로그인하거나 전환하는 **명령줄 사용자**&#x200B;입니다.

  Commerce은 이 사용자를 사용하여 CLI 명령 및 cron을 실행합니다.

  >[!INFO]
  >
  >명령줄 사용자를 _파일 시스템 소유자_&#x200B;라고도 합니다.

이러한 사용자는 동일한 파일에 액세스해야 하므로 두 사용자가 모두 속한 [공유 그룹](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group)을 만드는 것이 좋습니다. 다음 절차에서는 이미 이 작업을 수행했다고 가정합니다.

다음 섹션 중 하나를 참조하십시오.

- 개발자 또는 기본 모드의 두 파일 시스템 소유자
- 운영 모드의 파일 시스템 소유자 2명

### 기본 또는 개발자 모드로 두 명의 소유자 설정

다음 디렉토리에 있는 파일은 개발자 및 기본 모드의 두 사용자가 모두 쓸 수 있어야 합니다.

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

권한이 항상 상위 디렉터리에서 상속되도록 디렉터리에 [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/)비트를 설정하십시오.

>[!INFO]
>
>`setgid`은(는) 디렉터리에만 적용되며, _은(는) 파일에 적용되지 않습니다_.

또한 디렉터리는 웹 서버 그룹에서 쓸 수 있어야 합니다. 이러한 디렉터리에 컨텐츠가 있을 수 있으므로 권한을 재귀적으로 추가하십시오.

#### 권한 및 `setgid` 설정

개발자 모드에 대한 `setgid` 및 사용 권한을 설정하려면 다음을 수행하십시오.

1. 파일 시스템 소유자로 Commerce 서버에 로그인하거나 파일 시스템 소유자로 전환합니다.
1. 표시된 순서대로 다음 명령을 입력합니다.

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 운영 모드의 파일 시스템 소유자 2명

사이트를 프로덕션에 배포할 준비가 되면 보안을 강화하기 위해 다음 디렉토리에 있는 파일에서 쓰기 액세스 권한을 제거해야 합니다.

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 기타 모든 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 코드 파일 및 디렉터리를 읽기 전용으로 만들기

웹 서버 사용자 그룹에서 파일 및 디렉터리에 대한 쓰기 가능 권한을 제거하려면 다음을 수행합니다.

1. Commerce 서버에 로그인.
1. Commerce 설치 디렉토리로 변경합니다.
1. 파일 시스템 소유자로서 다음 명령을 입력하여 프로덕션 모드로 변경합니다.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. `root` 권한이 있는 사용자로 다음 명령을 입력하십시오.

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 코드 파일 및 디렉터리를 쓰기 가능 상태로 만들기

구성 요소를 업데이트하고 Commerce 소프트웨어를 업그레이드할 수 있도록 파일과 디렉터리를 쓰기 가능으로 설정하려면 다음을 수행하십시오.

1. Commerce 서버에 로그인.
1. Commerce 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
