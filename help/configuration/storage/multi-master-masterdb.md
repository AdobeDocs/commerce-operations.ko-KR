---
title: 마스터 데이터베이스 자동 구성
description: 분할 데이터베이스 솔루션 자동 구성에 대한 지침을 참조하십시오.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 1%

---


# 마스터 데이터베이스 자동 구성

{{ee-only}}

{{deprecate-split-db}}

이 항목에서는 다음 방법으로 데이터베이스 분할 솔루션을 시작하는 방법을 설명합니다.

1. 단일 마스터 데이터베이스(이름이 지정됨)로 Adobe Commerce 설치 `magento`)
1. 다음에 대한 두 개의 추가 마스터 데이터베이스 만들기 [체크아웃](https://glossary.magento.com/checkout) 및 OMS(이름이 지정됨) `magento_quote` 및 `magento_sales`)
1. 체크아웃 및 판매 데이터베이스를 사용하도록 Adobe Commerce 구성

>[!INFO]
>
>이 안내서에서는 세 데이터베이스 모두 상거래 애플리케이션과 동일한 호스트에 있고 이름이 지정되었다고 가정합니다 `magento`, `magento_quote`, 및 `magento_sales`. 그러나 데이터베이스를 찾을 위치와 이름을 지정할 수 있는 선택은 사용자가 결정합니다. 우리는 우리의 예들이 지침을 더 쉽게 따르도록 하기를 바랍니다.

## Adobe Commerce 소프트웨어 설치

Adobe Commerce 소프트웨어를 설치한 후 언제든지 분할 데이터베이스를 활성화할 수 있습니다. 즉, 체크아웃 및 주문 데이터가 이미 있는 Adobe Commerce 시스템에 분할 데이터베이스를 추가할 수 있습니다. Adobe Commerce README 또는 [설치 안내서](../../installation/overview.md) 단일 마스터 데이터베이스를 사용하여 Adobe Commerce 소프트웨어를 설치하려면 다음을 수행하십시오.

## 추가 마스터 데이터베이스 설정

다음과 같이 체크 아웃 및 OMS 마스터 데이터베이스를 생성합니다.

1. 데이터베이스 서버에 사용자로 로그인합니다.
1. 다음 명령을 입력하여 MySQL 명령 프롬프트로 이동합니다.

   ```bash
   mysql -u root -p
   ```

1. MySQL 입력 `root` 메시지가 표시되면 사용자의 암호입니다.
1. 다음 명령을 표시된 순서대로 입력하여 이름이 인 데이터베이스 인스턴스를 생성합니다 `magento_quote` 및 `magento_sales` 동일한 사용자 이름 및 암호 사용:

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

1. Enter 키 `exit` 명령 프롬프트를 종료하려면 다음을 수행하십시오.

1. 데이터베이스를 한 번에 하나씩 확인합니다.

   체크아웃 데이터베이스:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   주문 관리 시스템 데이터베이스:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL 모니터가 표시되면 데이터베이스를 제대로 만들었습니다. 오류가 표시되면 이전 명령을 반복합니다.

## 마스터 데이터베이스를 사용하도록 상거래 구성

총 세 개의 마스터 데이터베이스를 설정한 후 명령줄을 사용하여 상거래 데이터베이스를 사용하도록 구성합니다. 이 명령은 데이터베이스 연결을 설정하고 마스터 데이터베이스 간에 테이블을 분배합니다.

### 첫 단계

자세한 내용은 [실행 중인 명령](../cli/config-cli.md#running-commands) 로그인한 다음 CLI 명령을 실행합니다.

### 체크아웃 데이터베이스 구성

명령 구문:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

For example,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

다음 메시지가 표시되어 성공적인 설정을 확인합니다.

```terminal
Migration has been finished successfully!
```

### OMS 데이터베이스 구성

명령 구문:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

예,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

다음 메시지가 표시되어 성공적인 설정을 확인합니다.

```terminal
Migration has been finished successfully!
```
