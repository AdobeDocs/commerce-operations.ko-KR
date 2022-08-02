---
title: 단일 시스템 배포
description: 명령줄을 사용하여 프로덕션 서버에서 Commerce에 업데이트를 배포하는 방법을 알아봅니다.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---

# 단일 시스템 배포

이 항목에서는 명령줄을 사용하여 프로덕션 서버에서 Commerce에 업데이트를 배포하는 방법에 대한 지침을 제공합니다. 이 프로세스는 일부 테마 및 로케일이 설치된 단일 시스템에서 실행되는 스토어를 담당하는 기술 사용자에게 적용됩니다.

## 가정

- 다음을 사용하여 Commerce를 설치했습니다. [작성기].
- 서버에 업데이트를 직접 적용합니다.

>[!WARNING]
>
>이 안내서는 `git clone` 상거래 설치
>기여 개발자는 [이 안내서][install] 전자 상거래 설치를 업데이트하려면

## 배포 단계

1. 프로덕션 서버에 로그인하거나 [파일 시스템 소유자][file-owner].

1. 전자 상거래 기본 디렉터리로 디렉터리를 변경합니다.

   ```bash
   cd <Commerce base directory>
   ```

1. 다음 명령을 사용하여 유지 관리 모드를 활성화합니다.

   ```bash
   bin/magento maintenance:enable
   ```

1. 다음 명령 패턴을 사용하여 상거래 또는 해당 구성 요소에 업데이트를 적용합니다.

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **패키지**: 업데이트할 패키지의 이름입니다.

   For example:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **버전**: 업데이트할 패키지의 대상 버전입니다.

1. 작성기로 구성 요소 업데이트:

   ```bash
   composer update
   ```

1. 데이터베이스 스키마 및 데이터 업데이트:

   ```bash
   bin/magento setup:upgrade
   ```

1. 코드를 컴파일합니다.

   ```bash
   bin/magento setup:di:compile
   ```

1. 정적 콘텐츠 배포:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드 종료:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://devdocs.magento.com/guides/v2.4/install-gde/install/prepare-install.html
[composer]: https://devdocs.magento.com/guides/v2.4/install-gde/composer.html
[file-owner]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html#magento-file-system-owner
