---
title: 타사 확장 관리
description: Adobe Commerce 확장을 설치, 활성화, 업그레이드 및 제거하려면 다음 단계를 따르십시오.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# 타사 확장 관리

Adobe Commerce 동작을 확장하거나 사용자 지정하는 코드를 확장이라고 합니다. 선택적으로 [Commerce Marketplace](https://commercemarketplace.adobe.com/) 또는 다른 확장 배포 시스템에서 확장을 패키징하고 배포할 수 있습니다.

확장에는 다음이 포함됩니다.

- 모듈(Adobe Commerce 기능 확장)
- 테마(상점 및 관리자의 모양 및 느낌 변경)
- 언어 패키지(상점 및 관리자 현지화)

이 항목에서는 명령줄 인터페이스를 사용하여 _온-프레미스_ 프로젝트에 대해 Commerce Marketplace에서 구입한 타사 확장을 관리하는 방법을 설명합니다. 클라우드 인프라 프로젝트의 경우 [확장 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions)를 참조하십시오.

동일한 절차를 사용하여 _any_ 확장을 설치할 수 있습니다. 필요한 것은 확장의 작성기 이름과 버전입니다. 찾으려면 확장의 `composer.json` 파일을 열고 `"name"` 및 `"version"`의 값을 확인합니다.

## 설치

설치하기 전에 다음을 수행할 수 있습니다.

1. 데이터베이스 백업.
1. 유지 관리 모드 활성화:

   ```bash
   bin/magento maintenance:enable
   ```

확장을 설치하려면 다음을 수행해야 합니다.

1. Commerce Marketplace 또는 다른 확장 개발자로부터 확장을 가져옵니다.
1. Commerce Marketplace에서 확장을 설치하는 경우 `composer.json` 파일에 `repo.magento.com` 저장소가 있는지 확인하십시오.

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. 확장의 작성기 이름 및 버전을 가져옵니다.
1. 확장의 이름과 버전으로 프로젝트의 `composer.json` 파일을 업데이트합니다.
1. 확장이 제대로 설치되었는지 확인합니다.
1. 확장을 활성화하고 구성합니다.

### 확장 정보 가져오기

확장의 작성기 이름과 버전을 이미 알고 있는 경우 이 단계를 건너뛰고 [`composer.json` 파일을 업데이트](#update-composer-dependencies)합니다.

Commerce Marketplace에서 확장의 작성기 이름 및 버전을 가져오려면 다음을 수행하십시오.

1. 확장을 구입할 때 사용한 사용자 이름과 암호로 [Commerce Marketplace](https://commercemarketplace.adobe.com/)에 로그인합니다.

1. 오른쪽 상단 모서리에서 **내 이름** > **내 프로필**&#x200B;을 클릭합니다.

   ![마켓플레이스 계정에 액세스](../../assets/installation/marketplace-my-profile.png)

1. **내 구매**&#x200B;를 클릭합니다.

   ![마켓플레이스 구매 기록](../../assets/installation//marketplace-my-purchases.png)

1. 설치할 확장을 찾아 구성 요소 이름과 버전을 메모합니다.

   ![기술적 세부 정보에 확장의 작성기 이름이 표시됨](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>또는 확장 프로그램의 `composer.json` 파일에서 _any_ 확장의 작성기 이름과 버전(Commerce Marketplace에서 구입했는지 다른 곳에서 구입했는지 여부)을 찾을 수 있습니다.

### 작성기 종속성 업데이트

`composer.json` 파일에 확장 이름 및 버전을 추가합니다.

1. 프로젝트 디렉터리로 이동하여 `composer.json` 파일을 업데이트하십시오.

   ```bash
   composer require <component-name>:<version>
   ```

   For example,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. [인증 키](../prerequisites/authentication-keys.md)를 입력하십시오. 공개 키는 사용자 이름이고 개인 키는 암호입니다.

1. 작성기가 프로젝트 종속성 업데이트를 완료하고 오류가 없는지 확인할 때까지 기다립니다.

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### 설치 확인

확장이 제대로 설치되었는지 확인하려면 다음 명령을 실행합니다.

```bash
bin/magento module:status J2t_Payplug
```

기본적으로 확장은 비활성화되어 있을 수 있습니다.

```
Module is disabled
```

확장 이름이 `<VendorName>_<ComponentName>` 형식입니다. 이 형식은 Composer 이름과 다른 형식입니다. 이 형식을 사용하여 확장을 활성화합니다. 확장 이름을 잘 모를 경우 다음을 실행합니다.

```bash
bin/magento module:status
```

그리고 &quot;비활성화된 모듈 목록&quot;에서 확장을 찾습니다.

### 사용

생성된 정적 보기 파일을 먼저 지우지 않으면 일부 확장이 제대로 작동하지 않습니다. 확장을 사용할 때 정적 보기 파일을 지우려면 `--clear-static-content` 옵션을 사용하십시오.

1. 확장을 활성화하고 정적 보기 파일을 지웁니다.

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   다음 출력이 표시됩니다.

   ```
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

   ```
   Module is enabled
   ```

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```

1. 필요에 따라 Admin에서 확장을 구성합니다.

>[!TIP]
>
>브라우저에서 Storefront를 로드할 때 오류가 발생하면 다음 명령을 사용하여 캐시를 지우십시오. `bin/magento cache:flush`.

## 업그레이드

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

## 제거

타사 확장을 제거하는 방법은 확장 공급업체에 문의하십시오. 지침은 다음 정보를 제공해야 합니다.

- 데이터베이스 테이블 변경 사항을 되돌리는 방법
- 데이터베이스 데이터 변경 사항을 되돌리는 방법
- 제거 또는 되돌려야 하는 파일

>[!CAUTION]
>
>프로덕션 환경에 배포하기 전에 비프로덕션 환경 _먼저_&#x200B;에서 제거 단계를 수행하고 철저히 테스트하십시오.

다음은 타사 확장 제거에 대한 일반적인 정보입니다.

1. Adobe Commerce 프로젝트 저장소에서 확장을 제거합니다.

   - 작성기 기반 확장의 경우 Adobe Commerce `composer.json` 파일에서 확장을 제거합니다.

     ```bash
     composer remove <component-name>
     ```

   - 작성기 기반이 아닌 확장의 경우 Adobe Commerce 프로젝트 저장소에서 물리적 파일을 제거합니다.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. `config.php` 파일이 Adobe Commerce 프로젝트 리포지토리에서 소스 제어에서 사용 중인 경우 `config.php` 파일에서 확장을 제거하십시오.

1. 로컬 데이터베이스를 테스트하여 공급업체에서 제공한 지침이 예상대로 작동하는지 확인합니다.

1. 확장이 제대로 비활성화되어 있고 웹 사이트가 스테이징 환경에서 예상대로 작동하는지 확인하십시오.

1. 프로덕션 환경에 변경 사항을 배포합니다.
