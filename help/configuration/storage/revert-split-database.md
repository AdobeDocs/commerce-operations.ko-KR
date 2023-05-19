---
title: 분할 데이터베이스 되돌리기
description: 더 이상 사용되지 않는 분할 데이터베이스 구현에서 단일 데이터베이스 구현으로 되돌립니다.
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 분할 데이터베이스에서 되돌리기

{{ee-only}}

를 구현한 Adobe Commerce 고객용 [데이터베이스 분할](multi-master.md)다음 항목에서는 단일 데이터베이스로 되돌리거나 다시 마이그레이션하는 방법에 대해 설명합니다. 현재 Split Database를 사용 중인 Adobe Commerce 판매자가 2.4.2 이상으로 업그레이드하는 것이 좋습니다. 이러한 단계와 더불어 [공지](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 분할 데이터베이스의 사용을 중단하는 것을 의미합니다.

분할된 데이터베이스에서 단일 데이터베이스로 되돌리려면 `magento_quote` 및 `magento_sales` 데이터베이스를 단일 데이터베이스에 로드하기 전에 `magento_main` 데이터베이스.

이 예제에서는 동일한 호스트에 설치된 세 개의 데이터베이스에 모두 로그인합니다(`magento2-mysql`)를 루트 사용자로 추가합니다. 이러한 값을 데이터베이스에 적합한 값으로 바꾸어야 합니다.

1. 의 백업 만들기 `magento_quote` 데이터베이스:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 의 백업 만들기 `magento_sales` 데이터베이스:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 을(를) 로드합니다 `magento_quote` 데이터베이스를 `magento_main` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 을(를) 로드합니다 `magento_sales` 데이터베이스를 `magento_main` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 드롭하기 `magento_sales` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 드롭하기 `magento_quote` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 다음에 대한 배포 구성 제거 `checkout` 및 `sales` 다음에서 `connections` 및 `resources` 의 섹션 `env.php` 파일.
1. 외래 키 복원:

   ```bash
   bin/magento setup:upgrade
   ```

## 작업 확인

단일 데이터베이스 구현이 제대로 작동하는지 확인하려면 다음 작업을 수행하고 데이터가 `magento_main` 다음과 같은 데이터베이스 도구를 사용하는 데이터베이스 테이블 [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. 외래 키가 복원되었는지 확인합니다. 예를 들어 `QUOTE_STORE_ID_STORE_STORE_ID` 의 키 `quote` 데이터베이스 테이블.
1. 고객이 상점에서 주문을 할 수 있는지 확인합니다.
1. 분할 데이터베이스를 단일 데이터베이스로 되돌리기 전에 생성된 주문을 관리자에서 사용할 수 있는지 확인합니다.
