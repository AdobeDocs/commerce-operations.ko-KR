---
title: 파일 소유권 및 권한 구성
description: 다음 단계에 따라 Adobe Commerce 및 Magento Open Source의 온-프레미스 설치에 대한 파일 시스템 권한을 구성하십시오.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# 파일 소유권 및 권한 구성

이 항목에서는 Adobe Commerce 또는 Magento Open Source을 설치하기 전에 웹 서버 그룹에 대한 읽기-쓰기 권한을 설정하는 방법을 설명합니다. 명령줄이 파일 시스템에 파일을 쓸 수 있도록 이 작업이 필요합니다.

사용하는 절차는 사용 여부에 따라 다릅니다 [공유 호스팅](#set-permissions-for-one-user-on-shared-hosting) 한 명의 사용자가 있고 [개인 서버](#set-ownership-and-permissions-for-two-users) 두 명의 사용자가 있어야 합니다.

## 공유 호스팅에 대한 한 사용자의 권한 설정

이 섹션에서는 웹 서버도 실행하는 동일한 사용자로 응용 프로그램 서버에 로그인할 경우 설치 전 권한을 설정하는 방법을 설명합니다. 이러한 유형의 설정은 공유 호스팅 환경에서 일반적입니다.

응용 프로그램을 설치하기 전에 권한을 설정하려면 다음을 수행하십시오.

1. 애플리케이션 서버에 로그인합니다.
1. 공유 호스팅 공급자가 제공하는 파일 관리자 응용 프로그램을 사용하여 다음 디렉터리에 쓰기 권한이 설정되어 있는지 확인합니다.

   * `vendor` (작성기 또는 압축된 아카이브 설치)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * 기타 정적 리소스

1. 명령줄 액세스가 가능한 경우 다음 명령을 표시된 순서대로 입력합니다.

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   선택적으로 한 줄에 모든 명령을 입력하려면 응용 프로그램이 설치되어 있다고 가정할 때 다음을 입력합니다 `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. 아직 수행하지 않았다면 다음 방법 중 하나로 애플리케이션을 가져옵니다.

   * [작성기 메타카지](../../composer.md)
   * [리포지토리 복제(기여 개발자만)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. 파일 시스템 소유권 및 권한을 설정한 후에는 [애플리케이션 설치](../../advanced.md)

>[!NOTE]
>
>응용 프로그램을 설치한 후 권한을 추가로 제한하려면 [umask 구성](../../next-steps/set-umask.md).

## 두 사용자에 대한 소유권 및 권한 설정

이 섹션에서는 자체 서버 또는 개인 호스팅 설정에 대한 소유권 및 권한을 설정하는 방법을 설명합니다. 이러한 유형의 설정에서는 일반적으로 *사용할 수 없음* 웹 서버 사용자로 로그인하거나 로 전환합니다. 일반적으로 한 사용자로 로그인하고 웹 서버를 다른 사용자로 실행합니다.

두 사용자 시스템의 소유권 및 권한을 설정하려면 다음을 수행합니다.

표시된 순서대로 다음 작업을 완료하십시오.

* [공유 그룹 정보](#about-the-shared-group)
* [파일 시스템 소유자를 만들고 사용자에게 강력한 암호를 제공합니다](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [웹 서버 사용자 그룹 찾기](#find-the-web-server-user-group)
* [파일 시스템 소유자를 웹 서버 그룹에 넣습니다.](#put-the-file-system-owner-in-the-web-server-group)
* [소프트웨어 가져오기](#get-the-software)
* [공유 그룹에 대한 소유권 및 권한을 설정합니다](#set-ownership-and-permissions-for-the-shared-group)

### 공유 그룹 정보

웹 서버가 파일 시스템에서 파일 및 디렉터리를 작성할 수 있도록 하지만 유지 관리도 할 수 있도록 하려면 *소유권* 파일 시스템 소유자가 두 사용자를 모두 동일한 그룹에 있어야 합니다. 이 작업은 두 사용자가 파일(관리자나 다른 웹 기반 유틸리티를 사용하여 만든 파일 포함)에 대한 액세스를 공유할 수 있도록 필요합니다.

이 섹션에서는 파일 시스템 소유자를 만들고 해당 사용자를 웹 서버 그룹에 배치하는 방법에 대해 설명합니다. 원할 경우 기존 사용자 계정을 사용할 수 있습니다. 보안상의 이유로 사용자에게 강력한 암호가 있는 것이 좋습니다.

>[!NOTE]
>
>로 이동 [웹 서버 사용자 그룹 찾기](#find-the-web-server-user-group) 기존 사용자 계정을 사용할 계획이라면

### 파일 시스템 소유자를 만들고 사용자에게 강력한 암호를 제공합니다

이 섹션에서는 파일 시스템 소유자를 만드는 방법을 설명합니다. (파일 시스템 소유자는 *명령줄 사용자*)

CentOS 또는 Ubuntu에서 사용자를 만들려면 다음 명령을 사용자 로 입력합니다. `root` 권한:

```bash
adduser <username>
```

사용자에게 암호를 부여하려면 다음 명령을 사용자로서 입력합니다 `root` 권한:

```bash
passwd <username>
```

화면의 지침에 따라 사용자의 암호를 만듭니다.

>[!WARNING]
>
>없는 경우 `root` 응용 프로그램 서버에 대한 권한, 다른 로컬 사용자 계정을 사용할 수 있습니다. 사용자에게 강력한 암호가 있는지 확인하고 계속 [파일 시스템 소유자를 웹 서버 그룹에 넣습니다.](#step-3-put-the-file-system-owner-in-the-web-servers-group).

예를 들어 `magento_user` 사용자에게 암호를 지정하고 다음을 입력합니다.

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>이 사용자를 만들 때 보안 기능이 추가되었으므로 [강력한 암호](https://en.wikipedia.org/wiki/Password_strength).

### 웹 서버 사용자 그룹 찾기

웹 서버 사용자 그룹을 찾으려면

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   또는

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

일반적으로 사용자와 그룹 이름은 모두 `apache`.

* 우분투: `ps aux | grep apache` Apache 사용자를 찾으려면 다음을 수행하십시오. `groups <apache user>` 그룹을 찾으려면

일반적으로 사용자 이름과 그룹 이름은 모두 `www-data`.

### 파일 시스템 소유자를 웹 서버 그룹에 넣습니다.

파일 시스템 소유자를 웹 서버의 기본 그룹에 배치하려면(일반적인 CentOS 및 Ubuntu의 Apache 그룹 이름을 가정) 다음 명령을 다음 사용자로 입력합니다 `root` 권한:

* CentOS: `usermod -a -G apache <username>`
* 우분투: `usermod -a -G www-data <username>`

>[!NOTE]
>
>다음 `-a -G` 옵션은 추가되므로 중요합니다 `apache` 또는 `www-data` 로서의 *보조* 그룹 을 사용자 계정으로 그룹화하여 사용자의 *기본* 그룹에 속해 있어야 합니다. 사용자 계정에 보조 그룹을 추가하는 것은 [파일 소유권 및 권한 제한](#set-ownership-and-permissions-for-two-users) 공유 그룹의 구성원이 특정 파일에 액세스할 수만 있도록 합니다.

예를 들어 사용자를 추가하려면 `magento_user` 변환 후 `apache` CentOS의 기본 그룹:

```bash
sudo usermod -a -G apache magento_user
```

사용자가 웹 서버 그룹의 구성원인지 확인하려면 다음 명령을 입력합니다.

```bash
groups magento_user
```

다음 샘플 결과는 사용자의 기본(`magento`) 및 보조 ( )`apache`) 그룹에 속해 있어야 합니다.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>일반적으로 사용자 이름과 기본 그룹 이름은 동일합니다.

작업을 완료하려면 웹 서버를 다시 시작하십시오.

* 우분투: `service apache2 restart`
* CentOS: `service httpd restart`

### 소프트웨어 가져오기

아직 수행하지 않았다면 다음 방법 중 하나로 소프트웨어를 가져옵니다.

* [작성기 메타카지](../../composer.md)
* [리포지토리 복제(기여 개발자만)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 공유 그룹에 대한 소유권 및 권한을 설정합니다

응용 프로그램을 설치하기 전에 소유권 및 권한을 설정하려면 다음을 수행하십시오.

1. 애플리케이션 서버에 파일 시스템 소유자로 로그인하거나 로 전환합니다.
1. 다음 명령을 표시된 순서대로 입력합니다.

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

선택적으로 한 줄에 모든 명령을 입력하려면 응용 프로그램이 설치되어 있다고 가정할 때 다음을 입력합니다 `/var/www/html/magento2` 웹 서버 그룹 이름은 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

파일 시스템 권한이 잘못 설정되고 파일 시스템 소유자가 변경할 수 없는 경우 명령을 `root` 권한:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## 파일 시스템 소유자로 전환합니다.

이 항목의 다른 작업을 수행한 후에는 다음 명령 중 하나를 입력하여 해당 사용자로 전환합니다.

* 우분투: `su <username>`
* CentOS: `su - <username>`

For example,

```bash
su magento_user
```
