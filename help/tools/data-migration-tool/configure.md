---
title: ' [!DNL Data Migration Tool] 구성'
description: Magento 1과 Magento 2 간에 데이터를 전송하도록  [!DNL Data Migration Tool] 을(를) 구성하는 두 가지 방법에 대해 알아봅니다.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 구성

[!DNL Data Migration Tool]을(를) 설치한 후 다음 디렉터리에 매핑 및 구성 파일이 있습니다.

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Magento Open Source 1에서 Magento Open Source 2로 마이그레이션하기 위한 구성 및 스크립트

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Magento Open Source 1에서 Adobe Commerce 2로 마이그레이션하기 위한 구성 및 스크립트
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Adobe Commerce 1에서 Adobe Commerce 2로 마이그레이션하기 위한 구성 및 스크립트

위의 디렉토리에는 지원되는 각 버전에 대한 하위 디렉토리가 있습니다.

## 마이그레이션 구성

[!DNL Data Migration Tool]을(를) 구성하는 방법에는 두 가지가 있습니다.

* 별도의 모듈에서 [!DNL Data Migration Tool] 구성(권장)
* `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 디렉터리에서 [!DNL Data Migration Tool] 구성을 변경합니다.

소스 제어를 사용하여 마이그레이션 구성을 관리하고 배포에 사용하려면 별도의 모듈을 만들어야 합니다.
로컬에서만 [!DNL Data Migration Tool]을(를) 실행할 계획이라면 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` 디렉터리에서 직접 파일을 편집할 수 있습니다.

### 별도의 모듈에서 마이그레이션 구성

데이터를 마이그레이션하기 전에 Magento 2 모듈을 만들어야 합니다.

1. Magento 2 모듈을 만듭니다.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. `config.xml.dist` 구성 파일을 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`)의 적절한 디렉터리에서 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 파일로 복사합니다.

   예를 들어 `Magento 1.9.3.6 Community Edition`을(를) `Magento 2 Open Source`(으)로 마이그레이션하는 경우:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. `config.xml` 파일에서 액세스 세부 정보를 M1 및 M2 데이터베이스 및 암호화 키로 설정해야 합니다.

1. M1 저장소에 사용자 지정 변경 사항이 있는 경우 나머지 구성 파일을 Magento 1 저장소 사용자 지정에 매핑해야 합니다. [구성 및 매핑 파일 작업](#migration-config)을 참조하세요.

### `vendor` 폴더에서 마이그레이션 구성

데이터를 마이그레이션하기 전에 제공된 샘플에서 `config.xml` 구성 파일을 만들어야 합니다.

마이그레이션할 [!DNL Data Migration Tool]을(를) 구성하려면:

1. 응용 프로그램 서버에 [파일 시스템 소유자](../../installation/prerequisites/file-system/overview.md)(으)로 로그인하거나 응용 프로그램 서버로 전환합니다.

1. 다음 디렉토리로 변경합니다.

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 제공된 샘플에서 `config.xml`을(를) 만들려면 다음 명령을 입력하십시오.

   ```bash
   cp config.xml.dist config.xml
   ```

1. 텍스트 편집기에서 `config.xml` 열기

1. 최소한 config.xml 파일에는 M1 및 M2 데이터베이스 및 암호화 키에 대한 액세스 세부 정보가 포함되어야 합니다.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   &lt;crypt_key> 태그에 값이 있어야 합니다. Magento 1 인스턴스의 app/etc/local.xml 파일에 있는 `<key>` 태그에서 찾을 수 있습니다.

   선택적 매개 변수:

   * 데이터베이스 사용자 암호: `password=<password>`
   * 데이터베이스 사용자 지정 포트: `port=<port>`
   * 테이블 접두사: `<source_prefix>`, `<dest_prefix>`

   예를 들어 데이터베이스 소유자의 사용자 이름이 `root`이고 암호가 `pass`이고 Magento 1 데이터베이스에서 접두사 `magento1`을(를) 사용하는 경우 `config.xml`에서 다음을 사용하십시오.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

완료되면 변경 내용을 `config.xml`에 저장하고 텍스트 편집기를 종료합니다.

### TLS 프로토콜을 사용하여 연결

TLS 프로토콜(즉, 공개/개인 암호화 키 사용)을 사용하여 데이터베이스에 연결할 수도 있습니다. `database` 요소에 다음 선택적 특성을 추가합니다.

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

For example:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## 구성 및 매핑 파일 작업

[!DNL Data Migration Tool]은(는) *매핑 파일*&#x200B;을(를) 사용하여 다음을 포함하여 Magento 1과 Magento 2 데이터베이스 간에 사용자 지정 데이터베이스 매핑을 수행할 수 있습니다.

* 테이블 이름 변경

* 필드 이름 변경

* 테이블 또는 필드 무시

* 필드의 데이터 전송을 Magento 2 형식으로 조정

지원되는 Magento 버전에 대한 매핑 파일이 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`의 하위 디렉터리에 있습니다.

매핑 파일을 사용하려면 다음을 수행합니다.

1. `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/`에서 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/`(으)로 복사하고 `.dist` 확장을 제거합니다.

1. `config.xml`의 `<options>` 노드에서 새로 복사된 파일의 경로를 업데이트합니다. 업데이트된 경로는 다음 중 하나여야 합니다.

   1. 절대 파일 경로(예: `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`)
   1. magento/data-migration-tool 모듈 상대 파일 경로: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento 루트 상대 파일 경로: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

`<Magento 2 dir>/vendor/magento/data-migration-tool/etc` 및 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` 디렉터리에 다음 구성 파일이 있습니다.

대부분의 경우 `map.xml.dist` 파일을 사용하여 작업하지만 다음 표에서는 각 매핑과 다른 파일에 대해 설명합니다.

| 파일 이름 매핑 | 설명 |
| --- | --- |
| `class-map.xml.dist` | Magento 1과 Magento 2 간의 클래스 매핑 사전 |
| `config.xml.dist` | Magento 1 및 Magento 2 데이터베이스 구성, 단계 구성 및 매핑 파일에 대한 링크를 지정하는 기본 구성 파일 |
| *Adobe Commerce 전용*. `customer-attr-document-groups.xml.dist` | 사용자 지정 고객 속성 단계에서 사용되는 테이블 목록입니다. |
| *Adobe Commerce 전용*. `customer-attr-map.xml.dist` | 사용자 지정 고객 속성 단계에서 사용되는 맵 파일입니다. |
| `deltalog.xml.dist` | 데이터베이스 루틴 설정에 필요한 테이블 목록을 포함합니다. |
| `eav-attribute-groups.xml.dist` | Eav 단계에서 사용되는 속성 목록을 포함합니다. |
| `eav-document-groups.xml.dist` | Eav 단계에서 사용되는 테이블 목록을 포함합니다. |
| `log-document-groups.xml.dist` | 로그 단계에서 사용되는 테이블 목록을 포함합니다. |
| `map-eav.xml.dist` | EAV 단계에서 사용되는 맵 파일입니다. |
| `map-log.xml.dist` | 로그 매핑 파일입니다. |
| *Adobe Commerce 전용*. `map-sales.xml.dist` | SalesOrder 단계에 사용되는 맵 파일입니다. |
| `map.xml.dist` | 맵 단계에 필요한 매핑 파일입니다. |
| `settings.xml.dist` | `core_config_data` 테이블을 마이그레이션하는 데 필요한 규칙을 지정하는 마이그레이션 구성 파일을 설정하는 중입니다. |
| `customer-attribute-groups.xml.dist` | 고객 속성 단계에서 사용되는 속성 목록을 포함합니다. |
| `customer-document-groups.xml.dist` | 고객 속성 단계에서 사용되는 테이블 목록을 포함합니다. |
| `map-customer.xml.dist` | 고객 속성 단계에서 사용되는 맵 파일입니다. |
| `order-grids-document-groups.xml.dist` | OrderGrids 단계에서 사용되는 표의 목록을 포함합니다. |
| `map-document-groups.xml.dist` | 데이터 삽입에서 복제가 발생할 때 업데이트되는 필드를 정의합니다. |
| `map-stores.xml.dist` | 스토어 단계에서 사용되는 맵 파일입니다. |
| `map-tier-price.xml.dist` | 계층 가격 단계에서 사용되는 맵 파일입니다. |
| *Adobe Commerce 전용*. `visual_merchandiser_map.xml.dist` | VisualMerchandiser 단계에서 사용되는 맵 파일입니다. |
| *Adobe Commerce 전용*. `visual_merchandiser_attribute_groups.xml.dist` | VisualMerchandiser 단계에서 사용되는 특성 목록을 포함합니다. |
| *Adobe Commerce 전용*. `visual_merchandiser_document_groups.xml.dist` | VisualMerchandiser 단계에서 사용되는 테이블 목록을 포함합니다. |

자세한 내용은 [[!DNL Data Migration Tool] 기술 사양](technical-specification.md)을 참조하십시오.
