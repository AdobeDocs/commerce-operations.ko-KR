---
title: 단일 컴퓨터 배포
description: 명령줄을 사용하여 프로덕션 서버에서 Commerce에 업데이트를 배포하는 방법에 대해 알아봅니다.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
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
>기여 개발자는 [이 안내서](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)를 사용하여 Commerce 설치를 업데이트해야 합니다.

## 배포 단계

1. 프로덕션 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 전환합니다.

1. 디렉터리를 Commerce 기본 디렉터리로 변경합니다.

   ```shell
   cd <Commerce base directory>
   ```

1. 다음 명령을 사용하여 유지 관리 모드를 활성화합니다.

   ```shell
   bin/magento maintenance:enable
   ```

1. 다음 명령 패턴을 사용하여 Commerce 또는 해당 구성 요소에 업데이트를 적용합니다.

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **패키지**: 업데이트할 패키지의 이름입니다.

   For example:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **버전**: 업데이트할 패키지의 대상 버전입니다.

1. 작성기로 구성 요소 업데이트:

   ```shell
   composer update
   ```

1. 데이터베이스 스키마 및 데이터 업데이트:

   ```shell
   bin/magento setup:upgrade
   ```

1. 코드를 컴파일합니다.

   ```shell
   bin/magento setup:di:compile
   ```

1. 정적 콘텐츠 배포:

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. 캐시를 정리합니다.

   ```shell
   bin/magento cache:clean
   ```

1. 유지 관리 모드 종료:

   ```shell
   bin/magento maintenance:disable
   ```

