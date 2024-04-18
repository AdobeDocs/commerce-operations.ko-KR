---
title: 확장 설치
description: Adobe Commerce 확장을 설치하려면 다음 단계를 따르십시오.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# 확장 설치

Adobe Commerce 동작을 확장하거나 사용자 지정하는 코드를 확장이라고 합니다. 에서 확장을 선택적으로 패키징하고 배포할 수 있습니다. [Commerce Marketplace](https://marketplace.magento.com) 또는 다른 확장 배포 시스템입니다.

확장에는 다음이 포함됩니다.

- 모듈(Adobe Commerce 기능 확장)
- 테마(상점 및 관리자의 모양 및 느낌 변경)
- 언어 패키지(상점 및 관리자 현지화)

>[!TIP]
>
>이 항목에서는 명령줄을 사용하여 Commerce Marketplace에서 구입한 확장을 설치하는 방법을 설명합니다. 동일한 절차를 사용하여 설치할 수 있습니다 _임의_ 확장, 확장의 작성기 이름과 버전만 있으면 됩니다. 찾으려면 확장을 엽니다. `composer.json` 파일을 참조하고 다음에 대한 값을 확인합니다. `"name"` 및 `"version"`.

설치하기 전에 다음을 수행할 수 있습니다.

1. 데이터베이스 백업.
1. 유지 관리 모드 활성화:

   ```bash
   bin/magento maintenance:enable
   ```

확장을 설치하려면 다음을 수행해야 합니다.

1. Commerce Marketplace 또는 다른 확장 개발자로부터 확장을 가져옵니다.
1. Commerce Marketplace에서 확장을 설치하는 경우 `repo.magento.com` 저장소가 다음 위치에 있음: `composer.json` 파일:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 확장의 작성기 이름 및 버전을 가져옵니다.
1. 업데이트 `composer.json` 확장의 이름 및 버전을 사용하여 프로젝트에 있는 파일입니다.
1. 확장이 제대로 설치되었는지 확인합니다.
1. 확장을 활성화하고 구성합니다.

## 확장 작성기 이름 및 버전 가져오기

확장의 작성기 이름 및 버전을 이미 알고 있는 경우 이 단계를 건너뛰고 을 계속 진행합니다. [업데이트 `composer.json` 파일](#update-your-composer-file).

Commerce Marketplace에서 확장의 작성기 이름 및 버전을 가져오려면 다음을 수행하십시오.

1. 에 로그인 [Commerce Marketplace](https://marketplace.magento.com) 확장을 구입할 때 사용한 사용자 이름과 암호로.

1. 오른쪽 위 모서리에서 을(를) 클릭합니다. **사용자 이름** > **내 프로필**.

   ![Marketplace 계정에 액세스](../../assets/installation/marketplace-my-profile.png)

1. 클릭 **내 구매**.

   ![마켓플레이스 구매 내역](../../assets/installation//marketplace-my-purchases.png)

1. 설치할 확장을 찾아 를 클릭합니다 **기술 세부 정보**.

   ![기술 세부 사항에 확장의 작성기 이름이 표시됩니다.](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>또는 의 작성기 이름 및 버전을 찾을 수 있습니다. _임의_ 확장 프로그램(Commerce Marketplace에서 구입했는지 다른 곳에서 구입했는지 여부)의 `composer.json` 파일.

## 작성기 파일 업데이트

확장 이름 및 버전을 `composer.json` 파일:

1. 프로젝트 디렉터리로 이동하여 `composer.json` 파일.

   ```bash
   composer require <component-name>:<version>
   ```

   For example,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. 다음을 입력하십시오. [인증 키](../prerequisites/authentication-keys.md). 공개 키는 사용자 이름이고 개인 키는 암호입니다.

1. 작성기가 프로젝트 종속성 업데이트를 완료하고 오류가 없는지 확인할 때까지 기다립니다.

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## 확장 확인

확장이 제대로 설치되었는지 확인하려면 다음 명령을 실행합니다.

```bash
bin/magento module:status J2t_Payplug
```

기본적으로 확장은 비활성화되어 있을 수 있습니다.

```terminal
Module is disabled
```

확장 이름 형식은 다음과 같습니다 `<VendorName>_<ComponentName>`; 작성기 이름과 다른 형식입니다. 이 형식을 사용하여 확장을 활성화합니다. 확장 이름을 잘 모를 경우 다음을 실행합니다.

```bash
bin/magento module:status
```

그리고 &quot;비활성화된 모듈 목록&quot;에서 확장을 찾습니다.

## 확장 활성화

생성된 정적 보기 파일을 먼저 지우지 않으면 일부 확장이 제대로 작동하지 않습니다. 사용 `--clear-static-content` 확장을 활성화할 때 정적 보기 파일을 지우는 옵션입니다.

1. 확장을 활성화하고 정적 보기 파일을 지웁니다.

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   다음 출력이 표시됩니다.

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. 확장 등록:

   ```bash
   bin/magento setup:upgrade
   ```

1. 프로젝트 다시 컴파일: 프로덕션 모드에서 &quot;Magento 컴파일 명령을 다시 실행하십시오&quot;라는 메시지가 표시될 수 있습니다. 응용 프로그램에서 컴파일 명령을 개발자 모드에서 실행하라는 메시지를 표시하지 않습니다.

   ```bash
   bin/magento setup:di:compile
   ```

1. 확장이 활성화되었는지 확인합니다.

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   확장이 더 이상 비활성화되지 않았는지 확인하는 출력이 표시됩니다.

   ```terminal
   Module is enabled
   ```

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

1. 필요에 따라 Admin에서 확장을 구성합니다.

>[!TIP]
>
>브라우저에서 Storefront를 로드할 때 오류가 발생하면 다음 명령을 사용하여 캐시를 지웁니다. `bin/magento cache:flush`.

## 확장 업그레이드

모듈 또는 확장을 업데이트하거나 업그레이드하려면 다음 작업을 수행하십시오.

1. Marketplace 또는 다른 확장 개발자로부터 업데이트된 파일을 다운로드합니다. 모듈 이름과 버전을 기록해 둡니다.

1. 응용 프로그램 루트 디렉터리로 내용을 내보냅니다.

1. 모듈에 대한 Composer 패키지가 있는 경우 다음 중 하나를 실행합니다.

   모듈 이름별 업데이트:

   ```bash
   composer update vendor/module-name
   ```

   버전별 업데이트:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 다음 명령을 실행하여 캐시를 업그레이드, 배포 및 정리합니다.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
