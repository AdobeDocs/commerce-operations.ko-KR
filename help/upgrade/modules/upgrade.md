---
title: 모듈 및 확장 업그레이드
description: 명령줄 인터페이스와 작성기를 사용하여 Adobe Commerce 모듈 및 확장을 업그레이드합니다.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 모듈 및 확장 업그레이드

모듈 또는 확장을 업데이트하거나 업그레이드하려면 다음 작업을 수행하십시오.

1. Marketplace 또는 다른 확장 개발자로부터 업데이트된 파일을 다운로드합니다. 모듈 이름과 버전을 기록해 둡니다.

1. 콘텐츠를 Adobe Commerce 루트 설치 디렉토리로 내보냅니다.

1. 모듈에 대한 Composer 패키지가 있는 경우 다음 중 하나를 실행합니다.

   모듈 이름별 업데이트:

   ```bash
   composer update vendor/module-name
   ```

   버전별 업데이트:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 다음 명령을 실행하여 캐시를 업그레이드, 배포 및 정리합니다.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## 공급업체 번들 확장 프로그램(VBE)

Adobe이 모두 제거됨 [VBE](https://devdocs.magento.com/extensions/vendor/) 2.4.4의 공급업체는 Adobe Commerce Marketplace에서 이러한 확장을 계속 지원합니다.

Adobe Commerce 2.4.4 이상에서 이러한 확장을 계속 사용하려면 의 해당 패키지 종속성을 업데이트해야 합니다 `composer.json` 파일 _다음 이전_ 2.4.4로 업그레이드 사용할 패키지 이름 및 버전에 대해서는 공급업체에 문의하십시오.

자세한 내용은 다음 Adobe Commerce 마켓플레이스 목록을 참조하십시오.

- [Amazon 페이](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [클라르나](https://marketplace.magento.com/klarna-m2-klarna.html)
- [정점](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [요트포](https://marketplace.magento.com/yotpo-module-yotpo.html)
