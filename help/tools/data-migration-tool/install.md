---
title: ' [!DNL Data Migration Tool] 설치'
description: Magento 1과 Magento 2 간에 데이터를 전송하기 위해  [!DNL Data Migration Tool] 을(를) 설치하는 방법을 알아봅니다.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 설치

>[!INFO]
>
>Magento 및 [!DNL Data Migration Tool] 버전이 일치해야 합니다.


Magento 2와 *의*&#x200B;동일한 릴리스 버전[!DNL Data Migration Tool]을(를) 사용하고 있는지 확인하십시오. 예를 들어 Magento 버전 2.2.0의 경우 [!DNL Data Migration Tool] 버전 2.2.0도 사용해야 합니다.

## 버전 확인

다음 방법 중 하나를 사용하여 Magento 버전을 확인합니다.

- [작성기](#composer-metapackage)
- [GitHub 저장소](#github-repository)

### 작성기 메타패키지

작성기 메타 패키지를 사용하여 Magento 소프트웨어를 다운로드한 경우 다음 명령을 입력합니다.

```bash
php <magento_root>/bin/magento --version
```

### GitHub 저장소

Magento 2 GitHub 리포지토리를 복제한 경우 다음 명령을 입력합니다.

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

현재 `develop` 분기에 있는 경우 계속하려면 [릴리스된 분기](https://developer.adobe.com/commerce/contributor/guides/install/change-version)&#x200B;(으)로 변경해야 합니다.

아직 Adobe Commerce 소프트웨어를 설치하지 않았다면 [지금 설치](../../installation/prerequisites/commerce.md)하십시오.
GitHub 리포지토리를 복제하는 경우 [(기여자) GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)에서 설명한 대로 릴리스 태그를 체크아웃해야 합니다.

## [!DNL Data Migration Tool]의 릴리스 버전 찾기

사용 가능한 릴리스 버전을 찾으려면 [ GitHub 저장소의 ](https://github.com/magento/data-migration-tool/releases)릴리스[!DNL Data Migration Tool] 페이지로 이동하십시오.

## [!DNL Data Migration Tool] 설치

다음에서 [!DNL Data Migration Tool]을(를) 설치할 수 있습니다.

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

설치하기 전에 다음을 확인하십시오.

- [사전 조건](prerequisites.md) 섹션에서 언급된 모든 작업을 완료했습니다.
- [Magento 2 소프트웨어 버전을 확인했습니다](install.md#check-your-version)

### `repo.magento.com`에서 설치

[!DNL Data Migration Tool]을(를) 설치하려면 Magento 루트 설치 디렉터리에서 `composer.json`을(를) 업데이트하여 [!DNL Data Migration Tool] 패키지의 위치를 제공해야 합니다.

1. 응용 프로그램 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 응용 프로그램 서버로 전환합니다.
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   여기서 `<version>`은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 메시지가 표시되면 [인증 키](../../installation/prerequisites/authentication-keys.md)를 입력하십시오. 공개 키는 사용자 이름이고 개인 키는 암호입니다.

### GitHub에서 설치

GitHub 리포지토리를 복제한 경우 아래 단계에 따라 [!DNL Data Migration Tool]을(를) 설치하십시오.

1. 응용 프로그램 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 응용 프로그램 서버로 전환합니다.
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   여기서 `<version>`은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 설치된 [!DNL Data Migration Tool]의 버전 확인

1. [!DNL Data Migration Tool] 디렉터리: `<vendor>/magento/data-migration-tool`(으)로 변경합니다.

1. 텍스트 편집기에서 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json)을(를) 엽니다.

1. 해당 파일의 `version` 항목은 [!DNL Data Migration Tool]의 버전입니다.
