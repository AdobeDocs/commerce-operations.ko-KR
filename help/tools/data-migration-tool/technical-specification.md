---
title: '[!DNL Data Migration Tool] 기술 사양'
description: ' [!DNL Data Migration Tool] 의 구현 세부 정보와 Magento 1과 Magento 2 간에 데이터를 전송할 때 확장하는 방법에 대해 알아봅니다.'
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 기술 사양

이 단원에서는 [!DNL Data Migration Tool] 구현 세부 사항과 해당 기능을 확장하는 방법을 설명합니다.

## 저장소

[!DNL Data Migration Tool] 소스 코드에 액세스하려면 GitHub [repository](https://github.com/magento/data-migration-tool)를 참조하십시오.

## 시스템 요구 사항

[에 대한 &#x200B;](../../installation/system-requirements.md)시스템 요구 사항[!DNL Data Migration Tool]은(는) Magento 2와 동일합니다.

## 내부 구조

### 디렉터리 구조

다음 다이어그램은 [!DNL Data Migration Tool]의 디렉터리 구조를 나타냅니다.

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## 진입점

마이그레이션 프로세스를 실행하는 스크립트는 `magento-root/bin/magento`에 있습니다.

## 구성

구성 `config.xsd` 파일의 스키마가 `etc/` 디렉터리에 있습니다. Magento 1.x의 각 버전에 대해 기본 구성 파일(`config.xml.dist`)이 만들어집니다. 이 디렉터리는 `etc/` 아래의 별도의 디렉터리에 있습니다.

기본 구성 파일은 사용자 지정 구성 파일로 대체할 수 있습니다([명령 구문](migrate-data/overview.md#command-syntax) 참조).

구성 파일의 구조는 다음과 같습니다.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* 단계 - 마이그레이션 중에 처리되는 모든 단계를 설명합니다.

* source - 데이터 소스에 대한 구성. 사용 가능한 소스 유형: 데이터베이스

* 대상 - 데이터 대상에 대한 구성입니다. 사용 가능한 대상 유형: 데이터베이스

* options - 매개 변수 목록입니다. 필수(map_file, settings_map_file, bulk_size) 및 선택적(custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file) 매개변수를 모두 포함합니다.

Magento이 데이터베이스 테이블에 접두사와 함께 설치된 경우 접두사 옵션 변경. Magento 1 및 Magento 2 데이터베이스에 대해 설정할 수 있습니다. 그에 따라 &quot;source_prefix&quot; 및 &quot;dest_prefix&quot; 구성 옵션을 사용합니다.

구성 데이터는 `\Migration\Config` 클래스로 액세스할 수 있습니다.

## 사용 가능한 단계 작업

| 문서 | 필드 |
|---|---|
| `step` | 단계 노드 내의 두 번째 수준 노드. 관련 단계에 대한 설명은 `title` 특성에 지정해야 합니다. |
| `integrity` | 무결성 검사를 담당하는 PHP 클래스를 지정합니다. 테이블 필드 이름, 유형 및 기타 정보를 비교하여 Magento 1과 2 데이터 구조 간의 호환성을 확인합니다. |
| `data` | 데이터 검사를 담당하는 PHP 클래스를 지정합니다. 데이터를 테이블별로 Magento 1에서 Magento 2로 전송합니다. |
| `volume` | 볼륨 검사를 담당하는 PHP 클래스를 지정합니다. 테이블 간 레코드 수를 비교하여 전송이 성공했는지 확인합니다. |
| `delta` | 델타 검사를 담당하는 PHP 클래스를 지정합니다. 전체 데이터 마이그레이션 후 델타를 Magento 1에서 Magento 2로 전송합니다. |

## Source 데이터베이스 정보 속성

| 문서 | 필드 | 필수? |
|---|---|---|
| `name` | Magento 1 서버의 데이터베이스 이름입니다. | 예 |
| `host` | Magento 1 서버의 호스트 IP 주소입니다. | 예 |
| `port` | Magento 1 서버의 포트 번호입니다. | 아니요 |
| `user` | Magento 1 데이터베이스 서버의 사용자 이름. | 예 |
| `password` | Magento 1 데이터베이스 서버의 암호입니다. | 예 |
| `ssl_ca` | SSL 인증 기관 파일 경로. | 아니요 |
| `ssl_cert` | SSL 인증서 파일 경로. | 아니요 |
| `ssl_key` | SSL 키 파일 경로. | 아니요 |

## 대상 데이터베이스 정보 속성

| 문서 | 필드 | 필수? |
|---|---|---|
| `name` | Magento 2 서버의 데이터베이스 이름입니다. | 예 |
| `host` | Magento 2 서버의 호스트 IP 주소입니다. | 예 |
| `port` | Magento 2 서버의 포트 번호입니다. | 아니요 |
| `user` | Magento 2 데이터베이스 서버의 사용자 이름. | 예 |
| `password` | Magento 2 데이터베이스 서버의 암호입니다. | 예 |
| `ssl_ca` | SSL 인증 기관 파일 경로. | 아니요 |
| `ssl_cert` | SSL 인증서 파일 경로. | 아니요 |
| `ssl_key` | SSL 키 파일 경로. | 아니요 |

## TLS 프로토콜을 사용하여 연결

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

## 단계 내부

마이그레이션 프로세스는 단계로 구성됩니다.

단계는 분리된 일부 데이터를 마이그레이션하는 데 필요한 기능을 제공하는 단위입니다. 단계는 하나 이상의 단계(무결성 검사, 데이터, 볼륨 검사 및 델타)로 구성될 수 있습니다.

기본적으로 몇 가지 단계([맵](#map-step), [EAV](#eav), [URL 다시 쓰기](#url-rewrite-step) 등)가 있습니다. 선택적으로 자신의 단계를 추가할 수도 있습니다.

단계 관련 클래스는 src/Migration/Step 디렉토리에 있습니다.

Step 클래스를 실행하려면 config.xml 파일에 클래스를 정의해야 합니다.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

모든 스테이지 클래스는 StageInterface를 구현해야 합니다.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

데이터 단계에서 롤백을 지원하는 경우 `RollbackInterface` 인터페이스를 구현해야 합니다.

Symfony의 ProgressBar 구성 요소에서 실행 중인 단계를 시각화합니다([진행률 표시줄](https://symfony.com/doc/current/components/console/helpers/progressbar.html) 참조). LogLevelProcessor로 한 단계에서 이 구성 요소에 액세스합니다.

주요 사용 방법은 다음과 같습니다.

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 단계 단계

### 무결성 검사

각 단계에서는 데이터 소스 구조(기본적으로 Magento 1)와 데이터 대상 구조(Magento 2)가 호환되는지 확인해야 합니다. 그렇지 않은 경우 - 호환되지 않는 엔티티와 함께 오류가 표시됩니다. 필드에 서로 다른 데이터 형식이 있는 경우(동일한 필드에 Magento 1의 10진수 데이터 형식과 Magento 2의 정수 데이터 형식이 있는 경우) 맵 파일에서 다루는 경우를 제외하고 경고 메시지가 표시됩니다.

### 데이터 전송

무결성 검사를 통과한 경우 데이터 전송이 실행 중입니다. 오류가 발생하면 롤백이 실행되어 Magento 2의 이전 상태로 돌아갑니다. step 클래스에서 `RollbackInterface` 인터페이스를 구현하는 경우 오류가 발생하면 rollback 메서드가 실행됩니다.

### 볼륨 검사

데이터가 마이그레이션된 후 Volume Check에서 모든 데이터가 올바르게 전송되었는지 추가로 확인할 수 있습니다.

### 델타 게재

델타 기능은 기본 마이그레이션 후 추가된 나머지 데이터를 제공합니다.

## 실행 모드

이 도구는 다음 세 가지 모드로 특정 순서로 실행해야 합니다.

1. 설정 - 시스템 설정 마이그레이션
1. 데이터 - 데이터의 기본 마이그레이션
1. delta - 기본 마이그레이션 후 추가된 나머지 데이터의 마이그레이션

각 모드에는 실행할 고유한 단계 목록이 있습니다. config.xml을 참조하십시오.

### 설정 마이그레이션 모드

이 도구의 설정 마이그레이션 모드는 다음 엔티티를 전송하는 데 사용됩니다.

1. 웹 사이트, 스토어, 스토어 조회수.
1. 저장소 구성(주로 M2에 저장->구성 또는 M1에 시스템->구성)

모든 저장소 구성은 데이터베이스의 core_config_data 테이블에 데이터를 유지합니다. settings.xml 파일에 마이그레이션 프로세스 중에 적용되는 이 테이블에 대한 규칙이 포함되어 있습니다. 이 파일은 무시, 이름 변경 또는 해당 값을 변경해야 하는 설정을 설명합니다. settings.xml 파일의 구조는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

`<key>` 노드 아래에는 `core_config_data` 테이블의 &#39;경로&#39; 열과 함께 작동하는 규칙이 있습니다. `<ignore>` 규칙으로 인해 일부 설정을 전송할 수 없습니다. 이 노드에서는 와일드카드를 사용할 수 있습니다. `<ignore>` 노드에 나열되지 않은 다른 모든 설정은 마이그레이션됩니다. Magento 2에서 설정의 경로를 변경한 경우 `//key/rename` 노드에 추가해야 합니다. 여기서 이전 경로는 `//key/rename/path` 노드에 표시되고 새 경로는 `//key/rename/to` 노드에 표시됩니다.

`<value>` 노드 아래에는 `core_config_data` 테이블의 &#39;value&#39; 열과 함께 작동하는 규칙이 있습니다. 이러한 규칙은 핸들러(`Migration\Handler\HandlerInterface`을(를) 구현하는 클래스)별로 설정 값을 변환하고 Magento 2에 맞게 조정하는 것을 목표로 합니다.

### 데이터 마이그레이션 모드

이 모드에서는 대부분의 데이터가 마이그레이션됩니다. 데이터 마이그레이션 전에 각 단계에 대해 무결성 검사 단계가 실행됩니다. 무결성 검사를 통과하면 [!DNL Data Migration Tool]은(는) 접두사가 `m2_cl_*`인 deltalog 테이블 및 해당 트리거를 Magento 1 데이터베이스에 설치하고 단계의 데이터 마이그레이션 단계를 실행합니다. 오류 없이 마이그레이션이 완료되면 볼륨 검사에서 데이터 일관성을 확인합니다. 라이브 스토어를 마이그레이션하는 경우 경고 메시지가 표시될 수 있습니다. 델타 마이그레이션은 이러한 증분 데이터를 처리하므로 걱정하지 마십시오. 가장 중요한 마이그레이션 단계는 맵, URL 다시 작성 및 EAV입니다.

#### 맵 단계

맵 단계는 대부분의 데이터를 Magento 1에서 Magento 2로 전송합니다. 이 단계에서는 `etc/` 디렉터리에 있는 map.xml 파일에서 지침을 읽습니다. 이 파일은 소스(Magento 1)와 대상(Magento 2)의 데이터 구조 간 차이점을 설명합니다. Magento 1에 Magento 2에 존재하지 않는 일부 확장에 속하는 테이블 또는 필드가 포함된 경우 맵 단계에서 이러한 엔티티를 무시하도록 이러한 엔티티를 여기에 배치할 수 있습니다. 그렇지 않으면 오류 메시지가 표시됩니다.

맵 파일의 형식은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

영역:

* *원본* - 원본 데이터베이스의 규칙을 포함합니다.

* *대상* - 대상 데이터베이스의 규칙을 포함합니다.

옵션:

* *무시* - 이 옵션으로 표시된 문서, 필드 또는 데이터 형식이 무시됩니다.

* *이름 바꾸기* - 다른 이름을 가진 문서 간의 이름 관계를 설명합니다. 대상 문서 이름이 소스 문서와 동일하지 않은 경우 이름 바꾸기 옵션을 사용하여 대상 테이블 이름과 유사한 소스 문서 이름을 설정할 수 있습니다

* *이동* - 지정된 필드를 원본 문서에서 대상 문서로 이동하는 규칙을 설정합니다. 참고: 대상 문서 이름은 소스 문서 이름과 같아야 합니다. 소스 및 대상 문서 이름이 다른 경우 이동된 필드가 포함된 문서에 대해 이름 바꾸기 옵션을 사용해야 합니다

* *transform* - 사용자가 처리기에 설명된 동작에 따라 필드를 마이그레이션할 수 있는 옵션입니다.

* *처리기* - 필드의 변환 동작을 설명합니다. 처리기를 호출하려면 `<handler>` 태그에 처리기 클래스 이름을 지정해야 합니다. `<param>` 태그를 매개 변수 이름 및 값 데이터와 함께 사용하여 핸들러로 전달합니다.

**Source** 사용 가능한 작업:

| 문서 | 필드 |
|--- |--- |
| 이름 바꾸기 무시 | 이동 변환 무시 |

**대상** 사용 가능한 작업:

| 문서 | 필드 |
|--- |--- |
| 무시 | 변형 무시 |

#### 와일드카드

유사한 부분(`document_name_1`, `document_name_2`)이 있는 문서를 무시하려면 와일드카드 기능을 사용할 수 있습니다. 반복 부분(`*`) 대신 `document_name_*` 기호를 넣으면 이 마스크는 이 마스크를 충족하는 모든 원본 또는 대상 문서를 포함합니다.

#### URL 재작성 단계

이 단계는 Magento 2와 호환되지 않는 Magento 1에서 개발된 다양한 알고리즘이 많기 때문에 복잡합니다. 다양한 버전의 Magento 1에 대해 다양한 알고리즘이 있을 수 있습니다. 따라서 Step/UrlRewrite 폴더 아래에는 일부 특정 버전의 Magento용으로 개발된 클래스가 있으며 Migration\Step\UrlRewrite\Version191to2000 이 이러한 클래스 중 하나입니다. URL Rewrites 데이터를 Magento 1.9.1에서 Magento 2로 전송할 수 있습니다.

#### EAV 단계

이 단계는 모든 속성(제품, 고객, RMA)을 Magento 1에서 Magento 2로 전송합니다. 또한 특정 데이터 처리 사례에 대해 map.xml 파일과 유사한 규칙을 포함하는 map-eav.xml 파일을 사용합니다.

다음 단계에서 처리되는 일부 테이블:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 델타 마이그레이션 모드

기본 마이그레이션 후 Magento 1 데이터베이스에 추가 데이터를 추가할 수 있습니다(예: storefront의 고객이). 이 데이터를 추적하기 위해 이 도구는 마이그레이션 프로세스 시작 시 테이블에 대한 데이터베이스 트리거를 설정합니다. 자세한 내용은 [타사 확장에서 만든 데이터 마이그레이션](migrate-data/delta.md#migrate-data-created-by-third-party-extensions)을 참조하십시오.

## 데이터 소스

Magento 1 및 Magento 2의 데이터 소스에 도달하고 해당 데이터(선택, 업데이트, 삽입, 삭제)로 작업하려면 리소스 폴더에 여러 클래스가 있습니다. Migration\ResourceModel\Source 및 Migration\ResourceModel\Destination은 기본 클래스입니다. 모든 마이그레이션 단계는 이를 사용하여 데이터를 처리합니다. 이 데이터는 Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure 등의 클래스에 포함되어 있습니다.

다음은 이러한 클래스의 클래스 다이어그램입니다.

![마이그레이션 도구 데이터 구조](../../assets/data-migration/MmigrationToolDataStructure.png)

## 로깅

마이그레이션 프로세스의 출력을 구현하고 가능한 모든 수준을 제어하기 위해 Magento에서 사용되는 PSR 로거가 적용됩니다. 로깅 기능을 제공하기 위해 `\Migration\Logger\Logger` 클래스가 구현되었습니다. 로거를 사용하려면 생성자 종속성 삽입을 통해 로거를 주입해야 합니다.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

그런 다음 이 클래스를 사용하여 일부 이벤트를 기록할 수 있습니다.

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

로그 정보를 작성해야 하는 위치를 사용자 지정할 수 있습니다. 이렇게 하려면 로거의 pushHandler() 메서드를 사용하여 로거에 처리기를 추가하면 됩니다. 각 처리기는 `\Monolog\Handler\HandlerInterface` 인터페이스를 구현해야 합니다. 현재로서는 두 개의 핸들러가 있습니다.

* ConsoleHandler: 콘솔에 메시지를 씁니다.

* FileHandler: &quot;log_file&quot; 구성 옵션에 설정된 로그 파일에 메시지를 씁니다.

또한 추가 핸들러를 구현할 수 있습니다. Magento 프레임워크에는 핸들러 세트가 있습니다. Logger에 처리기를 추가하는 예:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

로거에 대한 추가 데이터(현재 모드, 테이블 이름)를 설정하려면 로거 프로세서를 사용할 수 있습니다. 기존 프로세서(MessageProcessor)가 한 개 있습니다. 메시지 로깅에 대한 &quot;추가&quot; 데이터를 추가하기 위해 만들어지며 로그 메서드가 실행될 때마다 호출됩니다. MessageProcessor에 &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; 및 &#39;table&#39;에 대한 빈 값이 포함된 $extra var가 보호되었습니다. 로그 방법에 대한 두 번째 매개 변수(컨텍스트)로서 추가 데이터를 프로세서에 전달할 수 있습니다. 현재 AbstractStep->runStage(현재 모드, 단계 및 단계를 프로세서로 전달) 메서드 및 logger->debug 메서드(마이그레이션 테이블 이름 전달)를 사용한 데이터 클래스의 프로세서에 대한 추가 데이터 세트입니다. 로거에 프로세서를 추가하는 예:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

세부담 수준을 설정할 가능성이 있습니다. 현재로서는 세 가지 수준이 있습니다.

* `ERROR`(로그에 오류만 쓰기)
* `INFO`(중요한 정보만 로그에 기록됨, 기본값)
* `DEBUG`(모든 내용이 기록됨)

`setLevel()` 메서드를 호출하여 각 처리기에 대한 자세한 로그 수준을 개별적으로 설정할 수 있습니다. 명령줄 매개 변수를 통해 세부 정보 수준을 설정하려면 응용 프로그램을 시작할 때 &#39;세부 정보&#39; 옵션을 변경해야 합니다.

모노로그 포맷터를 사용하여 로그 메시지를 포맷할 수 있습니다. 포맷터 기능을 사용하려면 `setFormatter()` 메서드를 사용하여 로그 처리기를 지정해야 합니다. 현재 처리기에서 실행된 `MessageFormatter` 메서드를 통해 메시지를 처리하는 동안 특정 형식을 설정하는 포맷터 클래스(`format()`)가 하나 있습니다(자세한 표시 수준에 따라 다름).

로거를 조작하고(처리기와 프로세서 추가) 세부 정보 표시 모드에서 처리하는 작업은 `process()` 클래스의 `Migration\Logger\Manager` 메서드에서 수행됩니다. 이 메서드는 응용 프로그램이 시작될 때 호출됩니다.

## 자동 테스트

[!DNL Data Migration Tool]에는 세 가지 유형의 테스트가 있습니다.

* 정적
* 단위
* 통합

테스트 유형과 동일한 도구의 `tests/` 디렉터리에 있습니다(단위 테스트는 `tests/unit` 디렉터리에 있음). 테스트를 시작하려면 phpunit가 설치되어 있어야 합니다. 현재 디렉터리를 테스트 디렉터리와 실행 phpunit로 변경합니다. For example:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
