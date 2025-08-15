---
title: 단일 컴퓨터 배포
description: 명령줄을 사용하여 프로덕션 서버에서 Commerce에 업데이트를 배포하는 방법에 대해 알아봅니다.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# 단일 시스템 배포

이 항목에서는 명령줄을 사용하여 프로덕션 서버에서 Commerce에 업데이트를 배포하는 방법에 대해 설명합니다. 이 프로세스는 일부 테마와 로케일이 설치된 단일 시스템에서 실행되는 스토어를 담당하는 기술 사용자에게 적용됩니다.

## 가정

- [작성기](../../installation/composer.md)를 사용하여 Commerce을 설치했습니다.
- 서버에 직접 업데이트를 적용하고 있습니다.

>[!WARNING]
>
>`git clone`을(를) 사용하여 Commerce을 설치한 경우에는 이 안내서가 적용되지 않습니다.
>&#x200B;>기여 개발자는 [이 안내서][install]를 사용하여 Commerce 설치를 업데이트해야 합니다.

## 배포 단계

1. 프로덕션 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 전환합니다.

1. 디렉터리를 Commerce 기본 디렉터리로 변경합니다.

   ```bash
   cd <Commerce base directory>
   ```

1. 다음 명령을 사용하여 유지 관리 모드를 활성화합니다.

   ```bash
   bin/magento maintenance:enable
   ```

1. 다음 명령 패턴을 사용하여 Commerce 또는 해당 구성 요소에 업데이트를 적용합니다.

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

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드 종료:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
