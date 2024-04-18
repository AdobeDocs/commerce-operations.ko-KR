---
title: 설치 [!DNL Data Migration Tool]
description: 설치 방법 알아보기 [!DNL Data Migration Tool] Magento 1과 Magento 2 간에 데이터를 전송합니다.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 설치 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento 및 버전 [!DNL Data Migration Tool] 일치해야 합니다.


을(를) 사용하고 있는지 확인합니다. *동일한 릴리스 버전* Magento 2와 [!DNL Data Migration Tool]. 예를 들어 Magento 버전 2.2.0의 경우 [!DNL Data Migration Tool] 버전 2.2.0.

## 버전 확인

다음 방법 중 하나를 사용하여 Magento 버전을 확인하십시오.

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

현재 다음 위치에 있는 경우: `develop` 분기, (으)로 변경해야 합니다. [릴리스된 분기](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 계속하기 전에

아직 Adobe Commerce 소프트웨어를 설치하지 않았다면, [지금 설치](../../installation/prerequisites/commerce.md).
GitHub 리포지토리를 복제하는 경우에서 설명한 대로 릴리스 태그를 체크아웃해야 합니다 [(기여자) GitHub 리포지토리 복제](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## 의 릴리스된 버전 찾기 [!DNL Data Migration Tool]

로 이동 [릴리스](https://github.com/magento/data-migration-tool/releases) 페이지의 [!DNL Data Migration Tool] 사용 가능한 릴리스 버전을 찾기 위한 GitHub 리포지토리입니다.

## 설치 [!DNL Data Migration Tool]

다음을 설치할 수 있습니다. [!DNL Data Migration Tool] 출처:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

설치하기 전에 다음을 확인하십시오.

- 에 언급된 모든 작업을 완료했습니다. [전제 조건](prerequisites.md) 섹션
- [버전을 확인했습니다.](install.md#check-your-version) Magento 2 소프트웨어

### 다음에서 설치 `repo.magento.com`

을(를) 설치하려면 [!DNL Data Migration Tool], 다음을 업데이트해야 합니다. `composer.json` Magento 루트 설치 디렉토리에서 [!DNL Data Migration Tool] 패키지.

1. 응용 프로그램 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   위치 `<version>` 은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 메시지가 표시되면 [인증 키](../../installation/prerequisites/authentication-keys.md). 공개 키는 사용자 이름이고 개인 키는 암호입니다.

### GitHub에서 설치

GitHub 리포지토리를 복제한 경우 아래 단계에 따라 [!DNL Data Migration Tool].

1. 응용 프로그램 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   위치 `<version>` 은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 설치된 버전 확인 [!DNL Data Migration Tool]

1. 다음으로 변경 [!DNL Data Migration Tool] 디렉터리: `<vendor>/magento/data-migration-tool`.

1. 열기 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 텍스트 편집기에서.

1. 다음 `version` 이 파일의 항목은 [!DNL Data Migration Tool].
