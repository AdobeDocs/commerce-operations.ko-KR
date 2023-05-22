---
title: 데이터베이스 작업 기록
description: Logger 인터페이스를 사용하여 데이터베이스 작업을 기록하도록 Commerce를 구성합니다.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# 데이터베이스 작업 기록

다음 예에서는 다음을 사용하여 데이터베이스 작업을 기록하는 방법을 보여 줍니다. [`Magento\Framework\DB\LoggerInterface`][interface]: 두 가지 구현이 있습니다.

- 아무것도 기록하지 않음(기본값): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- 에 로그 `var/log` 디렉터리: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Commerce CLI를 사용하여 다음을 수행할 수 있습니다. [데이터베이스 로깅 활성화 및 비활성화](../cli/enable-logging.md#database-logging).

의 기본 구성을 변경하려면 `\Magento\Framework\DB\Logger\LoggerProxy`, 편집 `app/etc/di.xml`.

먼저 의 기본값을 변경합니다. `loggerAlias` 및 `logCallStack` 인수:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

그런 다음 의 파일 경로를 제공합니다. `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

마지막으로 다음을 사용하여 코드를 컴파일합니다.

```bash
bin/magento setup:di:compile
```

및 다음을 사용하여 캐시를 정리합니다.

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
