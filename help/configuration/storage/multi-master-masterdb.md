---
title: 마스터 데이터베이스 자동 구성
description: 데이터베이스 분할 솔루션을 자동으로 구성하는 방법에 대한 지침을 참조하십시오.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# 마스터 데이터베이스 자동 구성

{{ee-only}}

{{deprecate-split-db}}

이 항목에서는 다음 방법으로 데이터베이스 분할 솔루션을 시작하는 방법에 대해 설명합니다.

1. 단일 마스터 데이터베이스(`magento`)를 사용하여 Adobe Commerce 설치
1. 체크 아웃 및 OMS(이름이 `magento_quote` 및 `magento_sales`임)를 위해 두 개의 추가 마스터 데이터베이스를 만드는 중
1. 체크아웃 및 판매 데이터베이스를 사용하도록 Adobe Commerce 구성

>[!INFO]
>
>이 안내서에서는 세 데이터베이스 모두 Commerce 응용 프로그램과 동일한 호스트에 있으며 이름이 `magento`, `magento_quote` 및 `magento_sales`이라고 가정합니다. 그러나 데이터베이스 위치와 이름을 선택할 수 있는 권한은 사용자에게 있습니다. 우리는 우리의 예제가 지침을 따르기 쉽게 만들었으면 합니다.

## Adobe Commerce 소프트웨어 설치

Adobe Commerce 소프트웨어를 설치한 후 언제든지 분할 데이터베이스를 활성화할 수 있습니다. 즉, 이미 체크아웃 및 주문 데이터가 있는 Adobe Commerce 시스템에 분할 데이터베이스를 추가할 수 있습니다. Adobe Commerce README 또는 [설치 안내서](../../installation/overview.md)의 지침을 사용하여 단일 마스터 데이터베이스를 사용하여 Adobe Commerce 소프트웨어를 설치합니다.

## 추가 마스터 데이터베이스 설정

다음과 같이 체크아웃 및 OMS 마스터 데이터베이스를 생성합니다.

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. MySQL 명령 프롬프트에 액세스하려면 다음 명령을 입력합니다.

   ```bash
   mysql -u root -p
   ```

1. 메시지가 표시되면 MySQL `root` 사용자의 암호를 입력하십시오.
1. 같은 사용자 이름과 암호를 사용하여 `magento_quote` 및 `magento_sales`(이)라는 데이터베이스 인스턴스를 만들려면 다음 명령을 표시된 순서대로 입력하십시오.

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 명령 프롬프트를 종료하려면 `exit`을(를) 입력하십시오.

1. 한 번에 하나씩 데이터베이스를 확인합니다.

   데이터베이스 체크 아웃:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Order Management 시스템 데이터베이스:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL 모니터가 표시되면 데이터베이스가 제대로 만들어진 것입니다. 오류가 표시되면 이전 명령을 반복합니다.

## 마스터 데이터베이스를 사용하도록 Commerce 구성

총 3개의 마스터 데이터베이스를 설정한 후 명령줄을 사용하여 해당 데이터베이스를 사용하도록 Commerce을 구성합니다. (이 명령은 데이터베이스 연결을 설정하고 마스터 데이터베이스 간에 테이블을 배포합니다.)

### 첫 단계

로그인하고 CLI 명령을 실행하려면 [명령 실행](../cli/config-cli.md#running-commands)을 참조하십시오.

### 체크아웃 데이터베이스 구성

명령 구문:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

For example,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

성공적인 설치를 확인하는 메시지가 표시됩니다.

```
Migration has been finished successfully!
```

### OMS 데이터베이스 구성

명령 구문:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

For example,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

성공적인 설치를 확인하는 메시지가 표시됩니다.

```
Migration has been finished successfully!
```
