---
title: 작업 모드 설정
description: Adobe Commerce 작업 모드 설정에 대해 읽어 보십시오.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 작업 모드 설정

{{file-system-owner}}

보안과 사용 편의성을 개선하기 위해 [응용 프로그램 모드](../bootstrap/application-modes.md)를 개발자에서 프로덕션으로 전환하거나 그 반대로 전환하는 명령을 추가했습니다.

정적 보기 파일이 `pub/static` 디렉터리에 채워져 있고 코드 컴파일로 인해 프로덕션 모드의 성능이 향상되었습니다.

>[!INFO]
>
>버전 2.0.6 이상에서는 기본, 개발 및 프로덕션 모드 간을 전환할 때 Commerce에서 파일 또는 디렉터리 권한을 명시적으로 설정하지 않습니다. 다른 모드와 달리 개발자 및 프로덕션 모드는 `env.php` 파일에 설정되어 있습니다. 클라우드 인프라의 Adobe Commerce은 프로덕션 및 유지 관리 모드만 지원합니다.
>
>[개발 및 프로덕션의 Commerce 소유권 및 권한](../deployment/file-system-permissions.md)을 참조하세요.

개발자 또는 프로덕션 모드로 변경하면 다음 디렉토리의 내용이 지워집니다.

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

예외:

- `.htaccess`개의 파일이 제거되지 않았습니다.
- `pub/static`에 정적 콘텐츠의 버전을 지정하는 파일이 포함되어 있습니다. 이 파일은 제거되지 않습니다.

>[!INFO]
>
>기본적으로 Commerce은 `var` 디렉터리를 사용하여 캐시, 로그 및 컴파일된 코드를 저장합니다. 이 디렉터리를 사용자 지정할 수 있지만 이 안내서에서는 이 디렉터리를 `var`(으)로 가정합니다.

## 현재 모드 표시

가장 쉬운 방법은 이 명령을 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 실행하는 것입니다. 공유 호스팅이 있는 경우 이 사용자는 공급자가 서버에 로그인할 수 있도록 제공하는 사용자입니다. 개인 서버가 있는 경우 일반적으로 Commerce 서버의 로컬 사용자 계정입니다.

명령 사용:

```bash
bin/magento deploy:mode:show
```

다음과 유사한 메시지가 표시됩니다.

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

여기서:

- **`{mode}`**&#x200B;은(는) `default`, `developer` 또는 `production`일 수 있습니다.

## 모드 변경

명령 사용:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

여기서:

- **`{mode}`**&#x200B;은(는) 필수입니다. `developer` 또는 `production`일 수 있습니다.

- **`--skip-compilation`**&#x200B;은(는) 프로덕션 모드로 변경할 때 [코드 컴파일](../cli/code-compiler.md)을 건너뛰는 데 사용할 수 있는 선택적 매개 변수입니다.

다음 예를 참조하십시오.

### 프로덕션 모드로 변경

```bash
bin/magento deploy:mode:set production
```

다음 디스플레이와 유사한 메시지:

```
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

1. 프로덕션 모드에서 개발자 모드로 변경하는 경우 `generated/code` 및 `generated/metadata` 디렉터리의 내용을 삭제합니다.

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 모드를 설정합니다.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   다음 메시지가 표시됩니다.

   ```
   Enabled developer mode.
   ```

### 기본 모드로 변경

```bash
bin/magento deploy:mode:set default
```

다음 메시지가 표시됩니다.

```
Enabled default mode.
```

### 어디서나 CLI 명령 실행

[어디서나 CLI 명령 실행](../cli/config-cli.md#config-install-cli-first).

`PATH` 시스템에 `<Commerce-install-directory>/bin`을(를) 추가하지 않은 경우 명령을 직접 실행할 때 오류가 발생할 수 있습니다.
