---
title: Git 기반 설치 업그레이드
description: git 저장소에서 복제한 Adobe Commerce 설치를 업그레이드합니다.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Git 기반 설치 업그레이드

이 항목에서는 기여 개발자가 Adobe Commerce을 다시 설치하지 않고 업데이트하는 방법에 대해 설명합니다. 기여 개발자가 아닌 경우 [업그레이드 수행](../implementation/perform-upgrade.md)을 참조하세요.

기여 개발자인 경우 업그레이드하려면 다음을 수행하십시오.

{{$include /help/_includes/server-login.md}}

1. 다음 단계를 통해 덮어쓰기되므로 `composer.json` 파일에 대한 변경 내용을 모두 저장하십시오.

1. `composer.json` 파일의 백업을 만듭니다.

   ```bash
   cp composer.json composer.json.old
   ```

1. 로컬 저장소를 업데이트하여 최신 코드를 가져옵니다.

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >`git pull origin develop`이(가) 실패하면 [문제 해결](https://support.magento.com/hc/en-us/articles/360034229872)을 참조하세요.

1. `composer.json.old` 파일을 `composer.json` 파일과 비교하고 병합합니다.

1. 종속성을 해결하고 `composer.lock` 파일에 정확한 버전을 쓰십시오.

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

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
