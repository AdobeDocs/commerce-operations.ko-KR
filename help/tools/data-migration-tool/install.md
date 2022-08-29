---
title: 설치 [!DNL Data Migration Tool]
description: 설치 방법 알아보기 [!DNL Data Migration Tool] Magento 1과 Magento 2 사이의 데이터를 전송하려면 다음을 수행하십시오.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# 설치 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento 및 버전 [!DNL Data Migration Tool] 일치해야 합니다.


사용 중인지 확인합니다. *동일한 릴리스 버전* Magento 2과 [!DNL Data Migration Tool]. 예를 들어 Magento 버전 2.2.0의 경우 [!DNL Data Migration Tool] 버전 2.2.0.

## 버전 확인

Magento 버전을 확인하려면 다음 방법을 사용하십시오.

- [작성기](#composer-metapackage)
- [GitHub 리포지토리](#github-repository)

### 작성기 메타카지

Magento 소프트웨어를 [작성기](https://glossary.magento.com/composer) methoxackage에서 다음 명령을 입력합니다.

```bash
php <magento_root>/bin/magento --version
```

### GitHub 리포지토리

Magento 2 GitHub 리포지토리를 복제한 경우 다음 명령을 입력합니다.

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

현재 `develop` 브랜치는 <a href="https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/dev_downgrade.html">릴리스된 분기</a> 계속하기 전에

Magento 소프트웨어를 아직 설치하지 않았다면 [지금 설치](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).
GitHub 리포지토리를 복제하는 경우, 에 설명된 대로 릴리스 태그를 체크 아웃해야 합니다 [(기여자) Magento 리포지토리 복제](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/dev_install.html).

## 릴리스된 버전 찾기 [!DNL Data Migration Tool]

로 이동합니다. [릴리스](https://github.com/magento/data-migration-tool/releases) 페이지의 [!DNL Data Migration Tool] 사용 가능한 릴리스 버전을 찾는 GitHub 리포지토리.

## 설치 [!DNL Data Migration Tool]

를 설치할 수 있습니다. [!DNL Data Migration Tool] 변환:

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

설치하기 전에 다음을 확인하십시오.

- 에 언급된 모든 작업을 완료했습니다. [전제 조건](prerequisites.md) 섹션
- [버전을 확인했습니다](install.md#check-your-version) Magento 2 소프트웨어

### 설치 위치 `repo.magento.com`

를 설치하려면 [!DNL Data Migration Tool], 업데이트해야 합니다. `composer.json` Magento 루트 설치 디렉터리에서 [!DNL Data Migration Tool] 패키지.

1. Magento 서버에 로그인하거나 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Magento 2 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   위치 `<version>` 는 Magento 2 코드 베이스의 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 메시지가 표시되면 을 입력합니다 [인증 키](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html). 공개 키는 사용자 이름 입니다. 개인 키는 암호입니다.

### GitHub에서 설치

GitHub 리포지토리에서 Magento 2을 복제한 경우 아래 절차에 따라 을 설치하십시오. [!DNL Data Migration Tool].

1. Magento 서버에 로그인하거나 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Magento 2 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   여기서 `<version>` 는 Magento 2 코드 베이스의 버전과 일치해야 합니다.

   예를 들어 버전 2.2.0의 경우 다음을 입력합니다.

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 설치된 버전 확인 [!DNL Data Migration Tool]

1. 다음으로 변경 [!DNL Data Migration Tool] 디렉토리: `<vendor>/magento/data-migration-tool`.

1. 열기 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 텍스트 편집기에서 을 참조하십시오.

1. 다음 `version` 해당 파일의 항목은 [!DNL Data Migration Tool].
