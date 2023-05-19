---
title: 작업 모드 설정
description: Adobe Commerce 작업 모드 설정에 대해 읽어 보십시오.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 작업 모드 설정

{{file-system-owner}}

보안 및 사용 편의성을 개선하기 위해 전환되는 명령을 추가했습니다 [애플리케이션 모드](../bootstrap/application-modes.md) 개발자에서 프로덕션으로 또는 그 반대로 변경되었습니다.

정적 보기 파일이에 채워지므로 프로덕션 모드의 성능이 향상됩니다. `pub/static` 코드 컴파일로 인해 및 디렉터리입니다.

>[!INFO]
>
>버전 2.0.6 이상에서는 기본, 개발 및 프로덕션 모드 간을 전환할 때 Commerce에서 파일 또는 디렉터리 권한을 명시적으로 설정하지 않습니다. 다른 모드와 달리 개발자 및 프로덕션 모드는 `env.php` 파일. 클라우드 인프라의 Adobe Commerce은 프로덕션 및 유지 관리 모드만 지원합니다.
>
>다음을 참조하십시오 [개발 및 프로덕션의 상거래 소유권 및 권한](../deployment/file-system-permissions.md).

개발자 또는 프로덕션 모드로 변경하면 다음 디렉토리의 내용이 지워집니다.

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

예외:

- `.htaccess` 파일이 제거되지 않음
- `pub/static` 정적 콘텐츠의 버전을 지정하는 파일을 포함합니다. 이 파일은 제거되지 않습니다.

>[!INFO]
>
>기본적으로 Commerce에서는 `var` 캐시, 로그 및 컴파일된 코드를 저장할 디렉터리입니다. 이 디렉토리는 사용자 정의할 수 있지만 이 안내서에서는 다음과 같이 가정합니다. `var`.

## 현재 모드 표시

이렇게 하는 가장 쉬운 방법은 이 명령을 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md). 공유 호스팅이 있는 경우 이 사용자는 공급자가 서버에 로그인할 수 있도록 제공하는 사용자입니다. 개인 서버가 있는 경우 일반적으로 Commerce 서버의 로컬 사용자 계정입니다.

명령 사용:

```bash
bin/magento deploy:mode:show
```

다음과 유사한 메시지가 표시됩니다.

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

여기서:

- **`{mode}`** 다음 중 하나일 수 있습니다. `default`, `developer`, 또는 `production`

## 모드 변경

명령 사용:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

여기서:

- **`{mode}`** 필수 요소로서 다음 중 하나일 수 있습니다. `developer` 또는 `production`

- **`--skip-compilation`** 는 건너뛰는 데 사용할 수 있는 선택적 매개 변수입니다. [코드 컴파일](../cli/code-compiler.md) 프로덕션 모드로 변경하는 경우.

다음 예를 참조하십시오.

### 프로덕션 모드로 변경

```bash
bin/magento deploy:mode:set production
```

다음 디스플레이와 유사한 메시지:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### 개발자 모드로 변경

프로덕션에서 개발자 모드로 변경할 때 예기치 않은 오류가 발생하지 않도록 생성된 클래스와 프록시와 같은 개체 관리자 엔티티를 지워야 합니다. 그런 다음 모드를 변경할 수 있습니다. 다음 단계를 수행하십시오.

1. 프로덕션 모드에서 개발자 모드로 변경하는 경우 `generated/code` 및 `generated/metadata` 디렉터리:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 모드를 설정합니다.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   다음 메시지가 표시됩니다.

   ```terminal
   Enabled developer mode.
   ```

### 기본 모드로 변경

```bash
bin/magento deploy:mode:set default
```

다음 메시지가 표시됩니다.

```terminal
Enabled default mode.
```

### 어디서나 CLI 명령 실행

[어디서나 CLI 명령 실행](../cli/config-cli.md#config-install-cli-first).

추가하지 않은 경우 `<Commerce-install-directory>/bin` 내 시스템으로 `PATH`그런 다음 명령을 단독으로 실행할 때 오류가 발생할 수 있습니다.
