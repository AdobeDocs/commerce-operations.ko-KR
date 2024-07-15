---
title: 모듈 구성 파일
description: 구성 유형을 사용하여 모듈을 사용자 지정하는 방법을 알아봅니다.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# 모듈 구성 파일 개요

이전 버전의 Commerce에서 사용된 `config.xml` 구성 파일의 권한은 이제 여러 모듈 디렉터리에 있는 여러 파일로 나누어집니다. Commerce의 여러 구성 파일은 모듈이 특정 구성 유형을 요청하는 경우에만 요청 시 로드됩니다.

이러한 파일(_구성 유형_)을 사용하여 모듈 동작의 특정 측면을 사용자 지정할 수 있습니다.

여러 모듈이 동일한 구성 유형에 영향을 주는 구성 파일(예: 이벤트)을 선언할 수 있으며, 이러한 여러 구성 파일은 병합됩니다.

다음은 이 주제에서 사용되는 일반적인 용어입니다.

- **구성 개체**—구성 형식을 정의하고 유효성을 검사하는 Commerce 라이브러리 또는 클래스입니다. 예를 들어 `config.xml`에 대한 구성 개체는 [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php)입니다.

- **구성 단계**—단계가 _기본_, _전역_ 및 _영역_&#x200B;으로 정의됩니다. 각 단계는 구성 유형이 로드되고 이름이 같은 구성 유형과 병합되는 시기를 결정합니다. 예를 들어 `module.xml`개의 파일이 다른 `module.xml`개의 파일과 병합됩니다.

- **구성 범위** - 구성 단계와 보완되는 범위에서는 구성 유형 모델을 정의합니다. 예를 들어 `adminhtml`은(는) 스테이지에서 다른 모듈의 `adminhtml` 구성과 함께 로드되는 영역 범위입니다. 자세한 내용은 [모듈 및 영역](https://developer.adobe.com/commerce/php/architecture/modules/areas/)을 참조하세요.

## 구성 로드 및 병합

이 섹션에서는 구성 파일을 로드하고 병합하는 방법에 대해 설명합니다.

### Commerce에서 구성 파일을 로드하는 방법

Commerce은 구성 파일을 다음 순서로 로드합니다(모든 경로는 Commerce 설치 디렉터리를 기준으로 함).

- 기본 구성([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). 이 파일은 Commerce을 부트스트랩하는 데 사용됩니다.
- 모듈(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)의 전역 구성. 모든 모듈에서 특정 구성 파일을 수집하여 함께 병합합니다.
- 모듈(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)의 영역별 구성입니다. 모든 모듈에서 구성 파일을 수집하여 전역 구성에 병합합니다. 일부 영역별 구성은 전역 구성을 재정의하거나 확장할 수 있습니다.

위치

- `<your component base dir>`은(는) 구성 요소가 있는 기본 디렉터리입니다. 일반적인 값은 Commerce 설치 디렉터리를 기준으로 하는 `app/code` 또는 `vendor`입니다.
- `<vendorname>`은(는) 구성 요소의 공급업체 이름입니다. 예를 들어, Commerce의 공급업체 이름은 `magento`입니다.
- `<component-type>`은(는) 다음 중 하나입니다.

   - `module-`: 확장 또는 모듈입니다.
   - `theme-`: 테마.
   - `language-`: 언어 패키지.

>[!INFO]
>
>현재 테마는 `<magento_root>/app/design/frontend` 또는 `<magento_root>/app/design/adminhtml` 아래에 있습니다.

- `<component-name>`: [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json)에 정의된 구성 요소의 이름입니다.

### 구성 파일 병합

구성 파일의 노드는 식별자로 선언된 `$idAttributes` 배열에 정의된 특수 특성이 있는 정규화된 XPath를 기반으로 병합됩니다. 이 식별자는 동일한 상위 노드 아래에 중첩된 모든 노드에 대해 고유해야 합니다.

Commerce 애플리케이션 병합 알고리즘:

- 노드 식별자가 같은 경우(또는 정의된 식별자가 없는 경우) 노드의 모든 기본 콘텐츠(속성, 하위 노드 및 스칼라 콘텐츠)가 무시됩니다.
- 노드 식별자가 같지 않으면 노드는 상위 노드의 새 하위 노드입니다.
- 원본 문서에 동일한 식별자를 가진 노드가 여러 개 있는 경우 식별자를 구별할 수 없으므로 오류가 트리거됩니다.

구성 파일이 병합되면 원본 파일의 모든 노드가 결과 문서에 포함됩니다.

>[!INFO]
>
>[\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 클래스를 사용하여 [구성 파일 로더](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 및 [구성 병합](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 프로세스의 논리를 디버깅하고 이해할 수 있습니다.

## 구성 유형, 객체 및 인터페이스

다음 단원에서는 구성 유형, 해당 구성 객체 및 객체를 사용하는 데 사용할 수 있는 인터페이스에 대한 정보를 제공합니다.

### 구성 유형 및 개체

다음 표는 각 구성 유형과 이 구성 유형이 관련된 Commerce 구성 객체를 보여 줍니다.

| 구성 파일 | 설명 | 단계 | 구성 개체 |
| --- | --- | --- | --- |
| `address_formats.xml` | 주소 형식 선언 | 기본, 글로벌 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [액세스 제어 목록](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | 글로벌 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [고급 보고](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 기본, 글로벌 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 캐시 유형 선언 | 기본, 글로벌 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 카탈로그 속성 구성 | 글로벌 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 및 `env.php` | [배포 구성](../reference/deployment-files.md) | 이러한 파일은 내부 구성 프로세서에서 읽기/쓰기 가능합니다. | 개체가 없어 사용자 지정할 수 없습니다. |
| `config.xml` | 시스템 구성 | 기본, 글로벌 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [메시지 큐 시스템의 측면을 정의합니다](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | 글로벌 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [크론 그룹 구성](../cron/custom-cron-reference.md#configure-cron-groups) | 글로벌 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [크론 그룹 옵션을 지정합니다](../cron/custom-cron-reference.md) | 글로벌 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [선언 스키마](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | 글로벌 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [종속성 삽입](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) 구성 | 기본, 글로벌, 영역 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | EAV 속성 구성 제공 | 글로벌 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 이메일 템플릿 구성 | 글로벌 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [검색 엔진 로케일 중지 단어 구성](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 글로벌 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 이벤트/관찰자 구성 | 전역, 영역 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 엔티티 구성 내보내기 | 글로벌 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [확장 특성](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | 글로벌 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 필드 세트 정의 | 글로벌 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [인덱서 선언](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | 글로벌 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 가져오기 엔티티 선언 | 글로벌 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 관리자의 메뉴 항목을 정의합니다. | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 모듈 구성 데이터 및 소프트 종속성 정의 | 기본, 글로벌 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView 구성](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | 기본, 글로벌 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 결제 모듈 구성 | 기본, 글로벌 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_영구](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) 구성 파일 | 글로벌 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF 설정 | 글로벌 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 제품 옵션 구성 제공 | 글로벌 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 제품 유형 정의 | 글로벌 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [기존 큐와 해당 소비자 간의 관계를 정의합니다](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | 글로벌 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [주제가 게시되는 교환을 정의합니다.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | 글로벌 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [메시지 라우팅 규칙을 정의하고 큐 및 교환을 선언합니다](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | 글로벌 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [고급 보고서](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 글로벌 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 모듈 리소스 정의 | 글로벌 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [경로](https://developer.adobe.com/commerce/php/development/components/routing/) 구성 | 영역 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 판매 총계 구성 정의 | 글로벌 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 검색 엔진 구성 제공 | 글로벌 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 카탈로그 검색 구성 정의 | 글로벌 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 비공개 콘텐츠 블록에 대한 캐시 무효화를 트리거하는 작업을 정의합니다. | 프론트엔드 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 시스템 구성 옵션 정의 페이지 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 모듈 유효성 검사 구성 파일 | 글로벌 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Vendor_Module 보기 구성 값을 정의합니다. | 글로벌 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [웹 API를 구성합니다](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | 글로벌 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [REST 사용자 지정 경로 정의](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | 글로벌 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 위젯 정의 | 글로벌 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 각 국가의 우편번호 형식을 정의합니다. | 글로벌 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 구성 인터페이스

[Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config)의 인터페이스를 사용하여 구성 파일과 상호 작용할 수 있습니다.

[구성 형식을 만드는](../reference/config-create-types.md#create-configuration-types)경우 이러한 인터페이스를 사용할 수 있습니다.

`Magento\Framework\Config`은(는) 다음 인터페이스를 제공합니다.

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)(XML을 구성의 메모리 내 배열 표시로 변환).
- 지정된 범위에서 구성 데이터를 검색하는 [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php).
- [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)에서 읽을 파일의 위치를 식별하는 [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php).
- 저장소에서 구성 데이터를 읽고 읽을 저장소를 선택하는 [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).

즉, 파일 시스템, 데이터베이스, 기타 저장소는 병합 규칙에 따라 구성 파일을 병합하고 유효성 검사 스키마와 함께 구성 파일의 유효성을 검사합니다.

- XSD 스키마를 찾는 [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php).
- 범위 목록을 반환하는 [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php).
- 유효성 검사 상태를 검색하는 [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php).
