---
title: 모듈 및 확장 관리(개발자)
description: 명령줄 인터페이스와 Composer 패키지 관리자를 사용하여 Adobe Commerce 모듈 및 확장을 관리합니다.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# 모듈 및 확장 관리

기여 개발자는 Adobe Commerce `composer.json` 파일에서 해당 버전을 지정하여 모듈 및 확장을 업그레이드합니다. 기여 개발자가 아닌 경우 [업그레이드 수행](../implementation/perform-upgrade.md)을 참조하세요.

`require` 파일에 `composer.json` 섹션을 추가하거나 다음과 같이 `composer require` 명령을 사용할 수 있습니다.

{{$include /help/_includes/server-login.md}}

다음과 같은 옵션이 있습니다.

## 사용 가능한 모듈 버전 가져오기

명령 사용:

```bash
composer show --all <vendor>/<name>
```

For example:

```bash
composer show --all example/module
```

## `composer require` 명령 사용

명령 사용:

```bash
composer require <vendor>/<name>:<version>
```

For example:

```bash
composer require example/module:1.0.0
```

Composer가 종속성을 업데이트하고 모듈을 설치하는 동안 잠시 기다려 주십시오.

## composer.json 파일에 `require` 섹션 추가

1. 텍스트 편집기에서 `composer.json`을(를) 엽니다.

1. `require` 섹션을 추가합니다.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. `composer.json` 파일에 변경 내용을 저장하고 텍스트 편집기를 종료합니다.

1. 종속성을 해결하고 `composer.lock` 파일에 정확한 버전을 쓰십시오.

   ```bash
   composer update
   ```
