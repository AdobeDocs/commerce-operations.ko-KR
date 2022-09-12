---
title: 분할 데이터베이스 되돌리기
description: 사용되지 않는 분할 데이터베이스 구현에서 단일 데이터베이스 구현으로 되돌립니다.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# 분할 데이터베이스에서 되돌리기

{{ee-only}}

구현한 Adobe Commerce 고객의 경우 [데이터베이스 분할](multi-master.md)다음 항목에서는 단일 데이터베이스로 되돌리거나 다시 마이그레이션하는 방법을 설명합니다. 현재 Split Database를 사용하고 있는 Adobe Commerce 가맹점을 추천하며 2.4.2로 업그레이드하고 이후 이러한 단계와 Adobe의 단계를 검토할 계획입니다 [공지](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 분할 데이터베이스의 사용 중단 계획을 참조하십시오.

분할 데이터베이스에서 단일 데이터베이스로 되돌리기 위해서는 `magento_quote` 및 `magento_sales` 단일 데이터베이스에 로드하기 전에 데이터베이스 `magento_main` 데이터베이스.

이 예에서는 동일한 호스트에 설치된 세 개의 데이터베이스에 모두 로그인합니다(`magento2-mysql`)을 &quot;루트&quot; 사용자로 사용할 수 있습니다. 이러한 값을 데이터베이스의 적절한 값으로 바꿔야 합니다.

1. 의 백업 만들기 `magento_quote` 데이터베이스:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 의 백업 만들기 `magento_sales` 데이터베이스:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 로드 `magento_quote` 데이터베이스에 `magento_main` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 로드 `magento_sales` 데이터베이스에 `magento_main` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 를 `magento_sales` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 를 `magento_quote` 데이터베이스:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 에 대한 배포 구성 제거 `checkout` 및 `sales` 에서 `connections` 및 `resources` 의 섹션 `env.php` 파일.
1. 외래 키 복원:

   ```bash
   bin/magento setup:upgrade
   ```

## 작업 확인

단일 데이터베이스 구현이 제대로 작동하는지 확인하려면 다음 작업을 수행하고 데이터가 `magento_main` 데이터베이스 도구를 사용하는 데이터베이스 테이블 [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. 외래 키가 복원되었는지 확인합니다. 예: `QUOTE_STORE_ID_STORE_STORE_ID` 키 `quote` 데이터베이스 테이블.
1. 고객이 상점 앞에서 주문을 할 수 있는지 확인합니다.
1. 분할 데이터베이스를 단일 데이터베이스로 되돌리기 전에 생성된 주문을 관리에서 사용할 수 있는지 확인합니다.
