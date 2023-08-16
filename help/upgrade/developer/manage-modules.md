---
title: 모듈 및 확장 관리(개발자)
description: 명령줄 인터페이스와 Composer 패키지 관리자를 사용하여 Adobe Commerce 및 Magento Open Source 모듈과 확장을 관리합니다.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 2%

---

# 모듈 및 확장 관리

개발자는 Adobe Commerce 또는 Magento Open Source에서 해당 버전을 지정하여 모듈 및 확장을 업그레이드합니다 `composer.json` 파일. 기여 개발자가 아닌 경우 [업그레이드 수행](../implementation/perform-upgrade.md).

다음을 추가할 수 있습니다. `require` 섹션에 대한 섹션 `composer.json` 파일을 참조하거나 `composer require` 다음과 같은 명령:

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

## 사용 `composer require` 명령

명령 사용:

```bash
composer require <vendor>/<name>:<version>
```

For example:

```bash
composer require example/module:1.0.0
```

Composer가 종속성을 업데이트하고 모듈을 설치하는 동안 잠시 기다려 주십시오.

## 추가 `require` composer.json 파일에 대한 섹션

1. 를 엽니다. `composer.json` 텍스트 편집기에서.

1. 추가 `require` 섹션.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 변경 내용을 `composer.json` 파일을 만들고 텍스트 편집기를 종료합니다.

1. 종속성을 해결하고 정확한 버전을 `composer.lock` 파일.

   ```bash
   composer update
   ```
