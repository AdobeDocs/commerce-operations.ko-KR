---
title: Git 기반 설치 업그레이드
description: git 저장소에서 복제한 Adobe Commerce 또는 Magento Open Source 설치를 업그레이드합니다.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Git 기반 설치 업그레이드

이 항목에서는 기여 개발자가 Adobe Commerce 또는 Magento Open Source을 다시 설치하지 않고 업데이트하는 방법에 대해 설명합니다. 기여 개발자가 아닌 경우 [업그레이드 수행](../implementation/perform-upgrade.md).

기여 개발자인 경우 업그레이드하려면 다음을 수행하십시오.

{{$include /help/_includes/server-login.md}}

1. 에 대한 변경 사항을 모두 저장합니다. `composer.json` 다음 단계에서 덮어쓰기이므로 파일입니다.

1. 의 백업 만들기 `composer.json` 파일.

   ```bash
   cp composer.json composer.json.old
   ```

1. 로컬 저장소를 업데이트하여 최신 코드를 가져옵니다.

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` 실패, 참조 [문제 해결](https://support.magento.com/hc/en-us/articles/360034229872).

1. 차이점 및 병합 `composer.json.old` 파일이 포함된 파일 `composer.json` 파일.

1. 종속성을 해결하고 정확한 버전을 `composer.lock` 파일.

   ```bash
   composer update
   ```

1. 데이터베이스 업데이트:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 정리합니다.

   ```bash
   bin/magento cache:clean
   ```
