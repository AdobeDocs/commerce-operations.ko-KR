---
title: 작성기 팁 및 요령
description: 빠른 문제 해결을 위한 일반적인 Composer 개발 작업 및 지침에 대해 알아봅니다.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 작성기 팁 및 요령

Composer를 사용하여 Adobe Commerce 모듈을 개발할 때 문제가 발생할 수 있습니다. 이러한 모범 사례에서는 개발을 쉽게 하고 문제를 빠르게 해결하는 데 도움이 되는 몇 가지 일반적인 작업을 설명합니다.

>[!NOTE]
>
>이 지침은 주로 다음에 적용됩니다. [글로벌 참조 아키텍처(GRA)](../overview.md) 프로젝트.

## 작성기 속도 높이기

설치 [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) 비동기 패키지 다운로드를 통해 Composer의 속도를 높이십시오.

```bash
composer global require hirak/prestissimo
```

문제가 발생하면 제거합니다. `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## 모호한 버전 관리 문제 해결

Composer가 패키지 버전으로 인해 교착 상태가 되는 경우가 있습니다. 호환되지 않더라도 호환되지 않는 버전에 대한 메시지가 표시될 수 있습니다. 호환성 문제를 디버깅하기 전에 Composer를 다시 설정해 보십시오.

1. 작성기 캐시를 지웁니다.

   ```bash
   composer clearcache
   ```

1. 제거 `composer.lock` 모든 패키지의 파일입니다.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Composer 패키지를 다시 설치합니다.

   ```bash
   composer install
   ```

>[!TIP]
>
>이 단계는 모든 패키지를 사용 가능한 최신 버전으로 업데이트합니다. 되돌리기 `composer.lock` git에서 파일을 다운로드하여 업그레이드를 취소할 수 있습니다.

## 클라이언트 패키지에서 가능한 업데이트 확인

1. 오래된 패키지를 확인합니다.

   ```bash
   composer outdated
   ```

1. 와일드카드 및/또는 을 사용하여 필터링 `--minor-only` 이전 버전과 호환되지 않는 업그레이드를 건너뛰는 옵션:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## 모듈이 설치되었는지 확인

Git 분기에 설치된 모든 패키지에 대한 세부 사항을 확인합니다.

```bash
composer info
```

실행 `composer install` git 분기 전환 후 실행 전 `composer info`. 그렇지 않으면 체크아웃한 이전 분기에 대한 세부 정보가 Composer에 표시됩니다.

>[!TIP]
>
>필터링하거나 검색하려면 다음 명령 중 하나를 사용하십시오.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## (특정 버전의) 패키지가 설치된 이유를 알아봅니다

경우에 따라 Composer는 다른 패키지의 엄격한 종속성으로 인해 사용 가능한 최신 버전의 패키지를 설치합니다.

다른 패키지에 엄격한 종속성이 있는지 확인합니다.

```bash
composer why client/module-example
```

결과에 명시적으로 필요하지 않은 메타패키지 또는 다른 패키지 목록이 표시되면 해당 패키지에서 명령을 실행합니다.

```bash
composer why example/metapackage
```

## 패키지가 설치되지 않은 이유 알아보기

패키지를 다른 패키지와 충돌하거나 다른 패키지가 이를 대체하거나 종속으로 정의하지 않았기 때문에 작성기가 패키지를 설치하지 않는 경우가 있습니다.

패키지가 설치되지 않은 이유를 알아봅니다.

```bash
composer why-not client/module-example
```

## 개인 작성기 저장소 호스팅

개인 Composer 저장소가 필요한 경우 [비공개 패키지 사용자](https://packagist.com/) 또는 [JFrog 아티팩토리](https://jfrog.com/integration/php-composer-repository/). 사용하지 않음 [사티스](https://github.com/composer/satis).

- **비공개 패키지 사용자** 는 안전하며, 세 명의 관리 사용자와 함께 연간 약 $600 USD가 소요되고 호스팅됩니다.

- **JFrog 아티팩토리** 1년에 미화 1,176달러부터 시작합니다. 이것은 Packagist만큼 일반적으로 사용되는 것은 아니지만, PHP보다 더 많은 언어를 지원합니다.

- **사티스** 에는 내장된 보안 및 자동화가 없으며 추가 호스팅이 필요합니다. 당신의 시간도 자유로워야 비로소 무료입니다.

## 패키지 버전 관리

사용 [시맨틱 버전 관리 2.0.0](https://semver.org/spec/v2.0.0.html) Adobe Commerce에 설명된 대로 [버전 관리 스키마](https://developer.adobe.com/commerce/php/development/versioning/). 헛수고를 하지 마라.

Adobe Commerce 모듈 종속성에 대해 다음을 수행합니다. [모듈 버전 종속성](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) 설명서를 참조하십시오.

내에서 버전 정의를 사용하지 마십시오. `composer.json` 파일. 대신 버전에 Git 태그를 사용하십시오. 다음을 참조하십시오 [작성기 버전 및 제한](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Composer가 아닌 아카이브 파일에 모듈을 배치하는 위치

아카이브의 모듈에 대한 Git 저장소를 생성하고 직접 호스팅합니다. 모든 Adobe Commerce 모듈에는 `composer.json` 파일. Git에서 호스팅하고 Private Packagist와 동기화한 후 Composer를 사용하여 설치할 수 있습니다.

새 버전의 패키지를 받으면 코드를 Git에 업로드하고 태그를 지정한 다음 작성기로 새 버전을 설치합니다.
