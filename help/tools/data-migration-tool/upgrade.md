---
title: 업그레이드 [!DNL Data Migration Tool]
description: 업그레이드 방법 알아보기 [!DNL Data Migration Tool] Magento 1과 Magento 2 사이의 데이터를 전송하려면 다음을 수행하십시오.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 업그레이드 [!DNL Data Migration Tool]

현재 Magento 2 설치 버전과 [!DNL Data Migration Tool] 정확하게 일치하면 도구를 업그레이드해야 할 수도 있습니다.

## 전제 조건

업그레이드하기 전에 [!DNL Data Migration Tool]:

* Magento 소프트웨어를 업그레이드하여 최신 버전을 다운로드하십시오

* 백업 `vendor/magento/data-migration-tool` directory

* 다음을 확인합니다. [!DNL Data Migration Tool] 버전은 Magento 애플리케이션 버전과 일치합니다

### Magento 소프트웨어 업그레이드

아직 안하셨다면, [Magento 소프트웨어 업그레이드](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html).

### 백업 `vendor/magento/data-migration-tool` directory

업그레이드하기 전에 [!DNL Data Migration Tool]적어도 백업 `vendor/magento/data-migration-tool` 디렉토리. 업그레이드 중에 삭제하고 업데이트된 코드로 대체할 수 있습니다.

다음 명령을 사용하여 전체 Magento 코드 베이스와 데이터베이스를 백업할 수도 있습니다.

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>다음 `vendor/magento/data-migration-tool` 디렉토리에 사용자 지정 코드가 포함되어 있습니다. 백업하지 않으면 업그레이드 중에 사용자 지정 사항을 잃을 수 있습니다.


### 버전이 일치하는지 확인

버전 [!DNL Data Migration Tool] 그리고 Magento 소프트웨어가 정확히 일치해야 합니다. 예를 들어 Magento 2.1.2에는 버전 2.1.2가 필요합니다 [!DNL Data Migration Tool].

자세한 내용은 [설치 [!DNL Data Migration Tool]](install.md) 방법:

* [확인](install.md#check-your-version) Magento 2 버전

* [찾기](install.md#find-released-versions-of-data-migration-tool) 릴리스된 버전 [!DNL Data Migration Tool]

* [확인](install.md#check-version-of-installed-data-migration-tool) a [!DNL Data Migration Tool] 버전

## 업그레이드 [!DNL Data Migration Tool]

1. Magento 서버에 로그인하거나 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Magento 2 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   여기서 `<version>` 는 Magento 2 코드 베이스의 버전과 일치해야 합니다.

   예를 들어 버전 2.1.2의 경우 다음을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 명령이 완료될 때까지 기다립니다.
