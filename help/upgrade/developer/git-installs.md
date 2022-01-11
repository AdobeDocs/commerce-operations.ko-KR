---
title: Git 기반 설치 업그레이드
description: Git 리포지토리에서 복제한 Adobe Commerce 또는 Magento Open Source 설치를 업그레이드합니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Git 기반 설치 업그레이드

이 항목에서는 기여 개발자가 Adobe Commerce 또는 Magento Open Source을 재설치하지 않고 업데이트할 수 있는 방법에 대해 설명합니다. 기여하고 있는 개발자가 아닌 경우 다음을 참조하십시오 [업그레이드 수행](../implementation/perform-upgrade.md).

기여 개발자인 경우 업그레이드하려면 다음을 수행하십시오.

1. 서버에 로그인합니다.

1. 로 전환 [파일 시스템 소유자](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. 응용 프로그램을 복제한 디렉토리로 변경합니다. 예,

   ```bash
   cd /var/www/magento2
   ```

1. 변경한 내용을 `composer.json` 파일을 덮어쓸 수 있습니다.

1. 백업 만들기 `composer.json` 파일.

   ```bash
   cp composer.json composer.json.old
   ```

1. 로컬 저장소를 업데이트하여 최신 코드를 가져옵니다.

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` 실패: [문제 해결](https://support.magento.com/hc/en-us/articles/360034229872).

1. 비교 및 병합 `composer.json.old` 다음 파일을 사용하여 `composer.json` 파일.

1. 종속성을 해결하고 정확한 버전을 `composer.lock` 파일.

   ```bash
   composer update
   ```

1. 데이터베이스를 업데이트합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 정리:

   ```bash
   bin/magento cache:clean
   ```
