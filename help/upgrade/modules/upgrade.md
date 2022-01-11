---
title: 업그레이드 모듈 및 확장
description: 명령줄 인터페이스 및 작성기를 사용하여 Adobe Commerce 및 Magento Open Source 모듈 및 확장을 업그레이드합니다.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 모듈 및 확장 업그레이드

모듈 또는 확장을 업데이트하거나 업그레이드하려면 다음을 수행하십시오.

1. 업데이트된 파일을 Marketplace 또는 다른 확장 개발자가 다운로드합니다. 모듈 이름과 버전을 주목하십시오.

1. 컨텐츠를 Adobe Commerce 또는 Magento Open Source 루트 설치 디렉토리로 내보냅니다.

1. 모듈에 대한 작성기 패키지가 있으면 다음 중 하나를 실행합니다.

   모듈 이름별 업데이트:

   ```bash
   composer update vendor/module-name
   ```

   버전별 업데이트:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 다음 명령을 실행하여 캐시를 업그레이드, 배포 및 청소합니다.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
