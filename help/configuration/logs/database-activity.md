---
title: 데이터베이스 작업 기록
description: 로거 인터페이스를 사용하여 데이터베이스 작업을 기록하도록 Commerce을 구성합니다.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '110'
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

```shell
bin/magento setup:di:compile
```

및 다음을 사용하여 캐시를 정리합니다.

```shell
bin/magento cache:clean
```

