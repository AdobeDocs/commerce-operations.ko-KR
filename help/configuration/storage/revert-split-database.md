---
title: 분할 데이터베이스 되돌리기
description: 더 이상 사용되지 않는 분할 데이터베이스 구현에서 단일 데이터베이스 구현으로 되돌립니다.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# 분할 데이터베이스에서 되돌리기

{{ee-only}}

[데이터베이스 분할](multi-master.md)을 구현한 Adobe Commerce 고객의 경우 다음 항목에서는 단일 데이터베이스로 되돌리거나 다시 마이그레이션하는 방법에 대해 설명합니다. 현재 분할 데이터베이스를 사용하고 있으며 2.4.2 이상으로 업그레이드할 계획이 있는 Adobe Commerce 판매자는 이러한 단계와 분할 데이터베이스의 계획된 사용 중단에 대한 [공지](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187)를 검토하는 것이 좋습니다.

분할된 데이터베이스에서 단일 데이터베이스로 되돌리려면 `magento_quote` 및 `magento_sales` 데이터베이스를 단일 `magento_main` 데이터베이스로 로드하기 전에 백업해야 합니다.

이 예제에서는 &quot;root&quot; 사용자로 동일한 호스트(`magento2-mysql`)에 설치된 세 개의 데이터베이스에 모두 로그인합니다. 이러한 값을 데이터베이스에 적합한 값으로 바꾸어야 합니다.

1. `magento_quote` 데이터베이스의 백업을 만듭니다.

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. `magento_sales` 데이터베이스의 백업을 만듭니다.

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. `magento_quote` 데이터베이스를 `magento_main` 데이터베이스에 로드합니다.

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. `magento_sales` 데이터베이스를 `magento_main` 데이터베이스에 로드합니다.

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. `magento_sales` 데이터베이스를 삭제합니다.

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. `magento_quote` 데이터베이스를 삭제합니다.

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. `env.php` 파일의 `connections` 및 `resources` 섹션에서 `checkout` 및 `sales`에 대한 배포 구성을 제거하십시오.
1. 외래 키 복원:

   ```bash
   bin/magento setup:upgrade
   ```

## 작업 확인

단일 데이터베이스 구현이 제대로 작동하는지 확인하려면 다음 작업을 수행하고 [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin)과(와) 같은 데이터베이스 도구를 사용하여 `magento_main` 데이터베이스 테이블에 데이터가 추가되었는지 확인하십시오.

1. 외래 키가 복원되었는지 확인합니다. 예를들어 `quote` 데이터베이스 테이블의 `QUOTE_STORE_ID_STORE_STORE_ID` 키를 사용합니다.
1. 고객이 상점에서 주문을 할 수 있는지 확인합니다.
1. 분할 데이터베이스를 단일 데이터베이스로 되돌리기 전에 생성된 주문을 관리자에서 사용할 수 있는지 확인합니다.
