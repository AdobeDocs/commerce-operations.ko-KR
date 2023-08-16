---
title: 시스템 설치 빌드
description: 빌드 시스템에 Commerce를 배포하는 방법에 대해 알아봅니다.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 시스템 설정 빌드

다음 요구 사항을 충족하는 빌드 시스템을 한 개 가질 수 있습니다.

- 모든 상거래 코드는 개발 및 프로덕션 시스템과 동일한 저장소에서 소스를 제어합니다
- 다음 사항을 모두 확인합니다. _포함됨_ 소스 제어에서:

   - `app/etc/config.php`
   - `generated` 디렉터리(및 하위 디렉터리)
   - `pub/media` 디렉터리
   - `pub/media/wysiwyg` 디렉터리(및 하위 디렉터리)
   - `pub/static` 디렉터리(및 하위 디렉터리)

- 호환되는 PHP 버전이 설치되어 있어야 합니다.
- 작성기가 설치되어 있어야 합니다.
- 에 설명된 대로 파일 시스템 소유권 및 권한이 설정되어 있습니다. [개발, 빌드 및 프로덕션 시스템의 사전 요구 사항](../deployment/technical-details.md).
- 빌드 시스템에는 Commerce를 설치할 필요가 없지만 코드가 있어야 설치할 수 있습니다.

>[!WARNING]
>
>데이터베이스에 이미 포함되어 있는 경우에는 데이터베이스 연결이 필요하지 않습니다. `config.php`; 참조 [구성 내보내기](../cli/export-configuration.md). 그렇지 않으면 데이터베이스 연결이 필요합니다.

>[!INFO]
>
>빌드 컴퓨터는 자체 호스트에 있거나 설치된 Commerce 시스템과 동일한 호스트에 있을 수 있습니다.

## 빌드 컴퓨터 구성

다음 섹션에서는 빌드 컴퓨터를 구성하는 방법에 대해 설명합니다.

### Composer 설치

먼저 Composer가 이미 설치되어 있는지 확인합니다.

명령 프롬프트에서 다음 명령을 입력합니다.

- `composer --help`
- `composer list --help`

명령 도움말이 표시되면 Composer가 이미 설치되어 있는 것입니다.

오류가 표시되면 다음 절차에 따라 Composer를 설치합니다.

Composer를 설치하려면:

1. Commerce 서버에서 를 로 변경하거나 빈 디렉토리를 만듭니다.

1. 다음 명령을 입력합니다.

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

추가 설치 옵션은 [Composer 설치 설명서][composer].

### PHP 설치

PHP 설치 [센트OS] 또는 [우분투].

### 빌드 시스템 설정

빌드 시스템을 설정하려면 다음을 수행하십시오.

1. 파일 시스템 소유자로 빌드 시스템에 로그인하거나 파일 시스템 소유자로 전환합니다.
1. 소스 제어에서 상거래 코드를 검색합니다.

   Git을 사용하는 경우 다음 명령을 사용합니다.

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Commerce 루트 디렉터리로 변경하고 다음을 입력합니다.

   ```bash
   composer install
   ```

1. 종속성이 업데이트될 때까지 기다립니다.
1. 소유권 설정:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   For example,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Git을 사용하는 경우 를 엽니다. `.gitignore` 텍스트 편집기에서.
1. 다음 각 줄을 `#` 주석을 달 수 있는 문자:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 변경 내용 저장 `.gitignore` 텍스트 편집기를 종료합니다.
1. Git을 사용하는 경우 다음 명령을 사용하여 변경 사항을 커밋합니다.

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   다음을 참조하십시오. [`.gitignore` 참조](../reference/config-reference-gitignore.md) 추가 정보.

1. 빌드 시스템은 [기본 모드](../bootstrap/application-modes.md#default-mode) 또는 [개발자 모드](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` 필수 항목입니다. 다음 중 하나일 수 있습니다. `default` 또는 `developer`.

<!-- Link Definitions -->

[센트OS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[우분투]: https://help.ubuntu.com/lts/serverguide/php.html
