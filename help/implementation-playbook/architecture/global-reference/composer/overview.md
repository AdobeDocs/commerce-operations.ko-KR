---
title: 작성기 개발
description: '''vendor/'' 디렉터리에서 바로 Composer 모듈을 개발하는 방법에 대해 알아봅니다.'
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# 작성기 개발

이 항목에서는 그 자리에서 (의 Git 저장소로) 작성기 모듈을 개발하는 데 권장되는 접근 방식을 설명합니다. `vendor/` 디렉토리) 및 기본 Git 프로젝트에 이러한 모듈을 추가합니다.

>[!NOTE]
>
>이 지침은 주로 다음에 적용됩니다. [글로벌 참조 아키텍처(GRA)](../overview.md) 프로젝트.

## 개발 분기 준비

1. 주 Git 저장소에서 개발 분기를 생성하거나 체크아웃합니다.
1. 유지 관리하는 각 모듈에 대한 개발 버전이 필요합니다.

   이 예에서 기본 Git 저장소의 모든 분기는 Composer 패키지 버전을 나타냅니다. 이 시나리오에서 작성기 버전에 권장되는 이름 지정 규칙은 다음과 같습니다. `dev-` 뒤에 지점 이름이 옵니다. For example:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 다른 Composer 패키지에 특정 버전의 모듈이 필요한 경우(예: `client/module-example 1.0.12`), 별칭을 사용하여 설치합니다.

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   의 경우 `qa` 분기, 바꾸기 `dev-develop` 포함 `dev-qa`.

## 패키지를 Git 저장소로 변환

기본적으로 패키지에는 `.git/` 디렉토리. 작성기는 사전 빌드된 작성기 패키지를 사용하는 대신 Git에서 패키지를 체크아웃할 수 있습니다. 이 접근 방식의 장점은 개발 중에 패키지를 쉽게 수정할 수 있다는 것입니다.

1. 에서 모듈 제거 `vendor/` 디렉토리.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. 를 사용하여 모듈을 다시 설치합니다. [지정된 Git 소스](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Composer 패키지가 이제 Git 저장소인지 확인합니다.

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. 여러 모듈을 Git 저장소로 일괄 변환하려면(예: &quot;클라이언트&quot; 모듈):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## 개발 시작

1. 기능/작업 분기 생성 또는 체크 아웃 다음 예제는 Jira 티켓과 이름이 같은 분기를 보여 줍니다.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. 모듈에서 분기를 변경한 후에는 Adobe Commerce 캐시 및 정적 콘텐츠를 플러시하여 변경 사항을 참조하십시오.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## 개발로 기본 프로젝트 업데이트

를 수정하여 기본 Git 저장소 업데이트 `composer.lock` 파일. 새 모듈인 경우 활성화합니다.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
