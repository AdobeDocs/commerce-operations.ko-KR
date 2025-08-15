---
title: ' [!DNL Data Migration Tool] 업그레이드'
description: ' [!DNL Data Migration Tool] 을(를) 업그레이드하여 Magento 1과 Magento 2 간에 데이터를 전송하는 방법을 알아봅니다.'
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 업그레이드

현재 Magento 2 설치와 [!DNL Data Migration Tool]의 버전이 정확히 일치하는지 확인하려면 도구를 업그레이드해야 할 수 있습니다.

## 사전 요구 사항

[!DNL Data Migration Tool]을(를) 업그레이드하기 전에 다음을 수행해야 합니다.

* Magento 소프트웨어를 업그레이드하여 최신 버전을 다운로드하십시오.

* `vendor/magento/data-migration-tool` 디렉터리 백업

* [!DNL Data Migration Tool] 버전이 Magento 애플리케이션 버전과 일치하는지 확인하십시오

### Magento 소프트웨어 업그레이드

아직 업그레이드하지 않았다면 [Magento 소프트웨어를 업그레이드](../../upgrade/overview.md)하십시오.

### `vendor/magento/data-migration-tool` 디렉터리 백업

[!DNL Data Migration Tool]을(를) 업그레이드하기 전에 적어도 `vendor/magento/data-migration-tool` 디렉터리를 백업하십시오. 업그레이드 중에 이를 삭제하고 업데이트된 코드로 대체할 수 있습니다.

다음 명령을 사용하여 전체 Magento 코드베이스 및 데이터베이스를 백업할 수도 있습니다.

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>`vendor/magento/data-migration-tool` 디렉터리에 사용자 지정 코드가 있습니다. 백업하지 않으면 업그레이드 중에 사용자 정의를 잃을 수 있습니다.


### 버전이 일치하는지 확인

[!DNL Data Migration Tool] 및 Magento 소프트웨어의 버전이 정확히 일치해야 합니다. 예를 들어 Magento 2.1.2에는 [!DNL Data Migration Tool]의 버전 2.1.2가 필요합니다.

방법을 알아보려면 [설치 [!DNL Data Migration Tool]](install.md) 항목을 참조하십시오.

* Magento 2 버전 [확인](install.md#check-your-version)

* [찾기](install.md#find-released-versions-of-data-migration-tool) 릴리스 버전의 [!DNL Data Migration Tool]

* [ 버전을 ](install.md#check-version-of-installed-data-migration-tool)확인[!DNL Data Migration Tool]

## [!DNL Data Migration Tool] 업그레이드

1. 응용 프로그램 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 전환합니다.
1. 애플리케이션 루트 디렉토리로 변경합니다.
1. 다음 명령을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   여기서 `<version>`은(는) Magento 2 코드베이스 버전과 일치해야 합니다.

   예를 들어 버전 2.1.2의 경우 다음을 입력합니다.

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 명령이 완료되는 동안 잠시 기다려 주십시오.
