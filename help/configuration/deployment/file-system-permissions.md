---
title: 파일 시스템 액세스 권한
description: 개발 및 프로덕션 시스템에 대해 상거래 응용 프로그램 파일 시스템의 소유자 또는 소유자를 설정하는 방법을 참조하십시오.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# 파일 시스템 액세스 권한

이 섹션에서는 개발 및 프로덕션 시스템을 위해 Commerce 파일 시스템의 소유자 또는 소유자를 설정하는 방법을 설명합니다. 계속하기 전에 [파일 시스템 소유권 및 권한 개요](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

이 항목에서는 상거래 개발 및 프로덕션 시스템에 중점을 둡니다. 상거래를 설치하는 경우 [사전 설치 소유권 및 권한 설정](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

다음 섹션에서는 하나 또는 두 개의 파일 시스템 소유자를 위한 요구 사항을 설명합니다. 이것의 의미는 다음과 같습니다.

- **사용자 1명**- 일반적으로 서버에 있는 한 명의 사용자만 액세스할 수 있도록 하는 공유 호스팅 공급자에 필요합니다. 이 사용자는 로그인하고 FTP를 사용하여 파일을 전송하며 이 사용자는 웹 서버도 실행할 수 있습니다.

- **사용자 두 명**—고유한 상거래 서버를 실행하는 경우 두 명의 사용자를 권장합니다. 파일 전송 및 명령줄 유틸리티 실행, 웹 서버 소프트웨어의 별도의 사용자 가능하면 보안이 강화되므로 이 것이 좋습니다.

   대신 별도의 사용자가 있습니다.

   - 관리 및 저장소를 실행하는 웹 서버 사용자입니다.

   - A _명령줄 사용자_: 서버에 로그인하는 데 사용할 수 있는 로컬 사용자 계정입니다. 이 사용자는 상거래 cron 작업 및 명령줄 유틸리티를 실행합니다.

## 공유 호스팅을 위한 프로덕션 파일 시스템 소유권(사용자 1명)

단일 소유자 설정을 사용하려면 웹 서버를 실행하는 동일한 사용자로 Commerce 서버에 로그인해야 합니다. 이것은 공유 호스팅에 일반적으로 사용됩니다.

하나의 파일 시스템 소유자가 더 안전하지 않으므로 가능한 경우 공유 호스팅이 아닌 개인 서버에 프로덕션에 상거래를 배포하는 것이 좋습니다.

### 기본 또는 개발자 모드로 한 개의 소유자 설정

기본 또는 개발자 모드에서 사용자가 다음 디렉토리에 쓸 수 있어야 합니다.

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 기타 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

공유 호스팅 공급자가 제공하는 명령줄 또는 파일 관리자 응용 프로그램을 사용하여 이러한 권한을 설정할 수 있습니다.

### 프로덕션 모드에 대해 소유자 한 명 설정

사이트를 프로덕션에 배포할 준비가 되면 보안을 위해 다음 디렉토리의 파일에서 쓰기 액세스를 제거해야 합니다.

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 기타 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

구성 요소를 업데이트하거나, 새 구성 요소를 설치하거나, 상거래 소프트웨어를 업그레이드하려면 이전 모든 디렉터리가 읽기-쓰여야 합니다.

#### 코드 파일 및 디렉터리를 읽기 전용으로 만들기

웹 서버 사용자 그룹에서 파일 및 디렉터리에 대한 쓰기 권한을 제거하려면 다음과 같이 하십시오.

1. Commerce 서버에 로그인합니다.

1. 상거래 설치 디렉토리로 변경합니다.

1. 프로덕션 모드로 변경합니다.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 다음 디렉토리에 대한 쓰기 권한을 제거합니다.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 명령줄 도구를 실행 가능하게 만듭니다.

   ```bash
   chmod u+x bin/magento
   ```

#### 코드 파일 및 디렉터리를 쓰기 가능하게 만들기

구성 요소를 업데이트하고 상거래 소프트웨어를 업그레이드할 수 있도록 파일 및 디렉터리를 쓰기 가능하게 만들려면 다음을 수행하십시오.

1. Commerce 서버에 로그인합니다.
1. 상거래 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   chmod -R u+w .
   ```

### 선택적으로 설정 `magento_umask`

자세한 내용은 [선택적으로 umask 설정](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) 에서 _설치 안내서_.

## 비공개 호스팅을 위한 프로덕션 파일 시스템 소유권(사용자 2명)

자체 서버를 사용하는 경우(호스팅 공급자의 개인 서버 설정 포함) 다음 두 명의 사용자가 있습니다.

- 다음 **웹 서버 사용자**: 관리자 및 storfront를 실행합니다.

   Linux 시스템은 일반적으로 이 사용자에 대한 셸을 제공하지 않습니다. 상거래 서버에 로그인하거나 웹 서버 사용자로 전환할 수 없습니다.

- 다음 **명령줄 사용자**- Commerce 서버에 로그인하거나 (으)로 전환합니다.

   Commerce에서는 이 사용자를 사용하여 CLI 명령과 cron을 실행합니다.

   >[!INFO]
   >
   >명령줄 사용자는 _파일 시스템 소유자_.

이러한 사용자는 동일한 파일에 액세스할 수 있어야 하므로 [공유 그룹](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) 두 사람이 함께 있는 곳에 다음 절차는 이미 이 작업을 수행했다고 가정합니다.

다음 섹션 중 하나를 참조하십시오.

- 개발자 또는 기본 모드에서 두 개의 파일 시스템 소유자
- 프로덕션 모드에서 두 명의 파일 시스템 소유자

### 기본 또는 개발자 모드로 두 개의 소유자 설정

다음 디렉토리에 있는 파일은 개발자 및 기본 모드에서 두 사용자가 모두 쓸 수 있어야 합니다.

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

설정 [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) 비트가 디렉토리에 있으므로 권한은 항상 상위 디렉터리에서 상속됩니다.

>[!INFO]
>
>`setgid` 디렉터리에만 적용됩니다. _not_ 파일로 내보낼 때 시간별 세부기간이 작동하지 않는 문제를 해결했습니다.

또한 웹 서버 그룹이 디렉터리를 쓸 수 있어야 합니다. 컨텐츠가 이러한 디렉토리에 있을 수 있으므로 권한을 재귀적으로 추가합니다.

#### 권한 및 설정 `setgid`

설정하려면 `setgid` 및 개발자 모드 권한:

1. Commerce 서버에 파일 시스템 소유자로 로그인하거나 로 전환합니다.
1. 다음 명령을 표시된 순서대로 입력합니다.

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 프로덕션 모드에서 두 명의 파일 시스템 소유자

사이트를 프로덕션에 배포할 준비가 되면 보안을 위해 다음 디렉토리의 파일에서 쓰기 액세스를 제거해야 합니다.

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 기타 정적 리소스
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 코드 파일 및 디렉터리를 읽기 전용으로 만들기

웹 서버 사용자 그룹에서 파일 및 디렉터리에 대한 쓰기 가능한 권한을 제거하려면 다음과 같이 하십시오.

1. Commerce 서버에 로그인합니다.
1. 상거래 설치 디렉토리로 변경합니다.
1. 파일 시스템 소유자로서 다음 명령을 입력하여 프로덕션 모드로 변경합니다.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 다음 명령을 사용자 로 입력합니다. `root` 권한:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 코드 파일 및 디렉터리를 쓰기 가능하게 만들기

구성 요소를 업데이트하고 상거래 소프트웨어를 업그레이드할 수 있도록 파일 및 디렉터리를 쓰기 가능하게 만들려면 다음을 수행하십시오.

1. Commerce 서버에 로그인합니다.
1. 상거래 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
