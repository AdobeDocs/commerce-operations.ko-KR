---
title: 데이터베이스 작업 기록
description: 로거 인터페이스를 사용하여 데이터베이스 작업을 기록하도록 Commerce을 구성합니다.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# 데이터베이스 작업 기록

다음 예제에서는 두 개의 구현이 있는 `[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)`을(를) 사용하여 데이터베이스 활동을 기록하는 방법을 보여 줍니다.

- 아무것도 기록하지 않음(기본값): [`Magento\Framework\DB\Logger\Quiet`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- `var/log` 디렉터리에 대한 로그: [`Magento\Framework\DB\Logger\File`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)

>[!TIP]
>
>Commerce CLI를 사용하여 [데이터베이스 로깅을 활성화 및 비활성화](../cli/enable-logging.md#database-logging)할 수 있습니다.

`\Magento\Framework\DB\Logger\LoggerProxy`의 기본 구성을 변경하려면 `app/etc/di.xml`을(를) 편집하세요.

먼저 `loggerAlias` 및 `logCallStack` 인수의 기본값을 다음으로 변경합니다.

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

그 후에 `Magento\Framework\DB\Logger\File`의 파일 경로를 제공하십시오.

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

