---
title: 구성 유형
description: 구성 유형을 생성하거나 확장합니다.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# 구성 유형

## 구성 유형 확장

기존 구성 유형을 확장하려면 모듈에 구성 파일만 만들면 됩니다.

예를 들어 이벤트 관찰자를 추가하려면 다음을 생성합니다 `app/code/{VendorName}/{ModuleName}/etc/events.xml` 새 관찰자를 선언합니다.

이벤트 구성 유형이 Commerce에 있으므로 로더 및 `events.xsd` 확인 스키마가 이미 존재하고 작동합니다.

내 새 항목 `events.xml` 는 모듈에서 자동으로 수집되고 다른 모듈과 병합됩니다 `events.xml` 다른 모듈용 파일입니다.

## 구성 유형 만들기

구성 유형을 만들려면 최소한 다음을 추가해야 합니다.

- 로더
- XSD 유효성 검사 스키마
- XML 구성 파일

예를 들어, 확장이 해당 서버에서 엔티티가 인덱스화되는 방식을 구성할 수 있도록 하는 새 검색 서버용 어댑터를 도입하려면 다음을 만듭니다.

- 로더
- XSD 스키마 파일
- 이름이 적절하게 지정된 구성 파일입니다. For example, `search.xml`. 이 파일은 스키마에 대해 읽고 유효성이 검사됩니다.
- 귀하의 작업에 필요한 기타 모든 클래스.

>[!INFO]
>
>새 모듈에 `search.xml` 파일이 로드되면 파일과 병합됩니다.

### 사용 예

구성 유형을 생성하려면 다음을 수행합니다.

1. XSD 파일을 만듭니다.
1. XML 파일을 만듭니다.
1. 에서 구성 개체 정의 `di.xml`.

   Magento_Sales 모듈의 다음 예 [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) 구성 객체의 모양을 보여 줍니다.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - 첫 번째 유형 노드는 연결된 Reader의 파일 이름을 설정합니다 `Converter` 및 `SchemaLocator` 클래스입니다.
   - 그런 다음 `pdfConfigDataStorage` 가상 형식 노드는 reader 클래스를 의 인스턴스에 연결합니다. [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - 마지막으로 마지막 유형 노드는 해당 구성 데이터 가상 유형을 [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) 클래스: 클래스의 값을 실제로 읽는 데 사용됨 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) 파일.

1. 를 확장하여 리더 정의 [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 클래스 및 재작성 매개 변수:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**예:**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>자체 버전의 독자를 만들려는 경우 을 구현하여 만들 수 있습니다 `\Magento\Framework\Config\ReaderInterface`. 다음을 참조하십시오 [Magento_Analytics 구성 판독기](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

판독기를 정의한 후 이 판독기를 사용하여 구성 파일을 수집, 병합, 유효성 검사 및 내부 배열 표현으로 변환합니다.

## 구성 유형 유효성 검사

각 구성 파일은 해당 구성 유형과 관련된 스키마에 대해 검증됩니다. 예: 이전 상거래 버전에서 구성된 이벤트 `config.xml`이제 다음에서 구성됩니다. `events.xml`.

구성 파일은 동일한 구성 유형에 영향을 주는 여러 파일이 병합되기 전과 후에 모두 확인할 수 있습니다(선택 사항). 개별 파일과 병합된 파일에 대한 유효성 검사 규칙이 동일하지 않은 경우 구성 파일의 유효성을 검사하기 위해 두 개의 스키마를 제공해야 합니다.

- 개인의 유효성을 검사하는 스키마
- 병합된 파일의 유효성을 검사하는 스키마

새 구성 파일은 XSD 유효성 검사 스키마와 함께 사용해야 합니다. XML 구성 파일과 해당 XSD 유효성 검사 파일의 이름은 동일해야 합니다.

단일 XML 파일에 두 개의 XSD 파일을 사용해야 하는 경우 스키마 이름을 인식할 수 있고 XML 파일과 연결해야 합니다.
다음 항목이 있는 경우 `events.xml` 파일 및 첫 번째 `events.xsd` 파일(병합할 XSD 파일) `events.xml` 파일 이름을 지정할 수 있음 `events_merged.xsd`.
적절한 XSD 파일을 사용하여 XML 파일의 유효성을 검사하려면 XML 파일의 XSD 파일에 URN(Uniform Resource Name)을 추가해야 합니다. For example:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE는 런타임과 개발 중에 구성 파일의 유효성을 검사할 수 있습니다.
