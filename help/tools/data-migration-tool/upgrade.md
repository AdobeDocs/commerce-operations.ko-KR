---
title: 업그레이드 [!DNL Data Migration Tool]
description: 업그레이드 방법 알아보기 [!DNL Data Migration Tool] Magento 1과 Magento 2 간에 데이터를 전송합니다.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 업그레이드 [!DNL Data Migration Tool]

현재 Magento 2 설치 버전 및 [!DNL Data Migration Tool] 정확하게 일치하십시오. 도구를 업그레이드해야 할 수 있습니다.

## 전제 조건

업그레이드 전 [!DNL Data Migration Tool], 다음을 수행해야 합니다.

* Magento 소프트웨어를 업그레이드하여 최신 버전을 다운로드하십시오.

* 백업 `vendor/magento/data-migration-tool` 디렉터리

* 다음을 확인하십시오. [!DNL Data Migration Tool] 버전이 Magento 애플리케이션 버전과 일치합니다.

### Magento 소프트웨어 업그레이드

아직 그렇게 하지 않았다면, [Magento 소프트웨어 업그레이드](../../upgrade/overview.md).

### 백업 `vendor/magento/data-migration-tool` 디렉터리

업그레이드 전 [!DNL Data Migration Tool], 적어도 다음 백업 `vendor/magento/data-migration-tool` 디렉토리. 업그레이드 중에 이를 삭제하고 업데이트된 코드로 대체할 수 있습니다.

다음 명령을 사용하여 전체 Magento 코드베이스 및 데이터베이스를 백업할 수도 있습니다.

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>다음 `vendor/magento/data-migration-tool` 디렉터리에 사용자 지정 코드가 있습니다. 백업하지 않으면 업그레이드 중에 사용자 정의를 잃을 수 있습니다.


### 버전이 일치하는지 확인

의 버전 [!DNL Data Migration Tool] 그리고 Magento 소프트웨어는 정확히 일치해야 합니다. 예를 들어 Magento 2.1.2에는 버전 2.1.2가 필요합니다. [!DNL Data Migration Tool].

다음을 참조하십시오. [설치 [!DNL Data Migration Tool]](install.md) 방법을 알아보는 주제:

* [확인](install.md#check-your-version) Magento 2 버전

* [찾기](install.md#find-released-versions-of-data-migration-tool) 의 릴리스된 버전 [!DNL Data Migration Tool]

* [확인](install.md#check-version-of-installed-data-migration-tool) 다음 [!DNL Data Migration Tool] 버전

## 업그레이드 [!DNL Data Migration Tool]

1. 애플리케이션 서버에 로 로그인하거나 로 전환합니다. [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md).
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   위치 `<version>` 은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.1.2의 경우 다음을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 명령이 완료되는 동안 잠시 기다려 주십시오.
