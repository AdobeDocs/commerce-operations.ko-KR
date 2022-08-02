---
title: 프로덕션 시스템 설정
description: Commerce 응용 프로그램에 대한 프로덕션 시스템을 설정하는 방법을 알아봅니다.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# 프로덕션 시스템 설정

한 대의 생산 시스템이 있습니다. 다음 모두 true여야 합니다.

- 모든 상거래 코드는 개발 및 빌드 시스템과 동일한 리포지토리의 소스 제어에 있습니다
- 다음을 모두 확인합니다 _포함_ 소스 제어에서 다음을 수행합니다.

   - `app/etc/config.php`
   - `generated` 디렉토리(및 하위 디렉토리)
   - `pub/media` directory
   - `pub/media/wysiwyg` 디렉토리(및 하위 디렉토리)
   - `pub/static` 디렉토리(및 하위 디렉토리)

- Commerce 2.2 이상을에 설치하고 설정해야 합니다. [프로덕션 모드](../bootstrap/application-modes.md#production-mode)
- 여기에 설명된 대로 파일 시스템 소유권 및 권한이 설정되어 있습니다. [개발, 빌드 및 운영 시스템을 위한 사전 요구 사항](../deployment/prerequisites.md).

## 프로덕션 컴퓨터 설정

프로덕션 시스템을 설정하려면 다음을 수행하십시오.

1. Commerce를 설치하거나 소스 제어에서 가져온 후 프로덕션 서버에 로그인하거나 [파일 시스템 소유자](https://glossary.magento.com/magento-file-system-owner).
1. 만들기 `~/.ssh/.composer/auth.json` 아직 안 하셨다면

   디렉토리를 만듭니다.

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   만들기 `auth.json` 해당 디렉토리.

   `auth.json` 다음을 포함해야 합니다. [인증 키](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

   샘플은

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 변경 내용을 `auth.json`.
1. 복사 `<Commerce root dir>/app/etc/env.php` 개발 시스템에서 프로덕션 시스템으로 이동합니다.
1. 열기 `env.php` 텍스트 편집기에서 필요한 값(예: 데이터베이스 연결 정보)을 변경합니다.
1. 를 실행합니다. [`magento config:set`](../cli/set-configuration-values.md) 또는 [`magento config:set-sensitive`](../cli/set-configuration-values.md) 명령을 사용하여 각 시스템별 또는 중요한 구성 값의 값을 설정합니다.

   다음 섹션에서는 예를 보여줍니다.

## 프로덕션 시스템에서 구성 값 설정

이 섹션에서는 를 사용하여 프로덕션 시스템에서 중요한 값을 설정하는 방법을 설명합니다 `magento config:sensitive:set` 명령.

중요 값을 설정하려면 다음을 수행하십시오.

1. 를 사용하여 설정할 값 찾기 [중요 값 참조](../reference/config-reference-sens.md).
1. 설정에 대한 구성 경로를 확인합니다.
1. 운영 시스템에 파일 시스템 소유자로 로그인하거나 로 전환합니다.
1. 상거래 설치 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   예를 들어 YouTube API 키의 값을 로 설정합니다. `1234`, 입력

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   다음과 같이 대화식으로 하나 이상의 값을 설정할 수도 있습니다.

   ```bash
   bin/magento config:sensitive:set -i
   ```

   메시지가 표시되면 각 중요 설정에 대한 값을 입력하거나 Enter 키를 눌러 값을 건너뛰고 다음 설정으로 이동합니다.

1. 값이 설정되었는지 확인하려면 관리자에게 로그인합니다.
1. 관리자에서 설정을 찾습니다.

   예를 들어 YouTube API 키 설정은 **스토어** > 설정 > **구성** > **카탈로그** > **카탈로그** > **제품 비디오**.

   이 설정은 관리자에 표시되며 편집할 수 없습니다. 다음 그림은 예를 보여줍니다.

   ![관리자의 중요 설정](../../assets/configuration/sensitive-set.png)
