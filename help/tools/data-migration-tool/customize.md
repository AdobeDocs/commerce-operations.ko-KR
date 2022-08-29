---
title: 사용자 지정 [!DNL Data Migration Tool]
description: 사용자 지정하는 방법 알아보기 [!DNL Data Migration Tool] Magento 1과 Magento 2 사이의 확장에서 만든 데이터를 전송합니다.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# 구성 [!DNL Data Migration Tool]

경우에 따라 [확장](https://marketplace.magento.com/extensions.html) 또는 사용자 지정 코드가 Magento 1과 Magento 2 간에 다릅니다. 내에서 확장 포인트 사용 [!DNL Data Migration Tool] 이 데이터를 마이그레이션하려면 다음을 수행하십시오. 데이터 형식과 구조가 동일하면 사용자가 개입하지 않고 자동으로 데이터를 마이그레이션할 수 있습니다.

마이그레이션 중에 [맵 단계](technical-specification.md#map-step) 확장에서 만든 테이블을 포함하여 모든 Magento 1 및 Magento 2 테이블을 검색하고 비교합니다. 테이블이 동일하면 도구에서 데이터를 자동으로 마이그레이션합니다. 표가 다르면 도구가 종료되어 사용자에게 알립니다.

>[!NOTE]
>
>다음 문서를 참조하십시오. [기술 사양](technical-specification.md) 확장을 시도하기 전에 [!DNL Data Migration Tool]. 또한, [마이그레이션 안내서](../overview.md) 마이그레이션 도구 사용에 대한 일반 정보입니다.


## 부분 데이터 형식 및 구조 변경

대부분의 경우 [맵 단계](technical-specification.md#map-step) 에서 다음 방법을 사용하여 작은 데이터 형식 및 구조 변경 사항을 충분히 해결합니다. `map.xml` 파일:

- 매핑 규칙으로 테이블 또는 필드 이름 변경
- 기존 핸들러 또는 사용자 지정 핸들러를 사용하여 데이터 형식 변환

다음은 매핑 규칙과 핸들러를 모두 사용하는 예를 보여 줍니다. 이 예에서는 Magento 2에 대해 개선된 &quot;GreatBlog&quot;라는 가상의 Magento 1 확장을 사용합니다.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- 에서 불필요한 데이터를 마이그레이션하지 마십시오 `great_blog_index` 인덱스 테이블.
- 테이블 `great_blog_publication` 의 이름이 로 변경되었습니다. `great_blog_post` Magento 2에서는 데이터가 새 테이블로 마이그레이션됩니다.
   - 다음 `summary` 필드의 이름이 `title`로 설정되면 데이터가 새 필드로 마이그레이션됩니다.
   - 다음 `priority` 필드가 제거되어 Magento 2에 더 이상 존재하지 않습니다.
   - 의 데이터 `body` 필드의 형식이 변경되었으며 사용자 지정 처리기에 의해 처리되어야 합니다. `\Migration\Handler\GreatBlog\NewFormat`.
- Magento 2의 &quot;GreatBlog&quot; 확장을 위해 새로운 등급 기능이 개발되었습니다.
   - 새로운 `great_blog_rating` 테이블이 생성되었습니다.
   - 새로운 `great_blog_post.rating` 필드가 생성되었습니다.

### 다른 단계에서 매핑 확장

매핑과 같은 기타 단계가 지원됩니다 [EAV 단계](technical-specification.md#eav-step) 및 고객 속성 단계를 포함할 수 있습니다. 이러한 단계는 사전 정의된 Magento 테이블 목록을 마이그레이션합니다. 예를 들어 &quot;GreatBlog&quot; 확장 기능에 `eav_attribute` 표와 이름이 Magento 2에서 변경되었습니다. 테이블이 [EAV 단계](technical-specification.md#eav-step), 매핑 규칙은 다음에 대해 작성해야 합니다 `map-eav.xml` 파일. 다음 `map.xml` 및 `map-eav.xml` 파일은 동일한 `map.xsd` 스키마이므로 매핑 규칙이 동일하게 유지됩니다.

## 주요 데이터 형식 및 구조 변경

맵 단계 외에 `config.xml` 주요 형식 및 구조 변경 사항으로 데이터를 마이그레이션하는 파일:

- [Url 재작성 단계](technical-specification.md#url-rewrite-step)
- 주문 그리드 단계
- [EAV 단계](technical-specification.md#eav-step)

와 달리 [맵 단계](technical-specification.md#map-step)를 검색하는 단계는 모든 테이블 대신 미리 정의된 테이블 목록을 검색합니다.

주요 데이터 형식 및 구조 변경 사항에 대해 사용자 지정 단계를 만듭니다.

### 사용자 지정 단계 만들기

동일한 &quot;GreatBlog&quot; 예를 사용하여 확장에 Magento 1에 테이블이 하나 있지만 Magento 2에 표가 두 개 있도록 재디자인되었다고 가정합니다.

Magento 1에는 `greatblog_post` 표:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento 2에서 태그의 새 표 `greatblog_post_tags` 도입:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` 이제 표는 다음과 같습니다.

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

이전 테이블 구조에서 새 테이블 구조로 모든 데이터를 마이그레이션하려면 `config.xml` 파일. For example:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

이 도구는 `config.xml` 파일; 위에서 아래로 이 예제에서는 `GreatBlog Step` 마지막으로 실행됩니다.

단계에는 네 가지 유형의 클래스가 포함될 수 있습니다.

- 무결성 검사
- 데이터 제공
- 볼륨 확인
- 델타 제공

>[!NOTE]
>
>을(를) 참조하십시오. [구성](technical-specification.md#configuration), [단계 내부](technical-specification.md#step-internals), [단계](technical-specification.md#step-stages), 및 [실행 모드](technical-specification.md#running-modes) 추가 정보.


복잡한 SQL 쿼리를 이 클래스 내에서 어셈블하여 데이터를 가져오고 마이그레이션할 수 있습니다. 또한, [맵 단계](technical-specification.md#map-step) 기존 테이블을 모두 검색하고 `<ignore>` 태그입니다 `map.xml` 파일.

무결성 검사를 위해 `config.xml` 파일 을 사용하여 테이블 구조가 예상대로 작동하는지 확인합니다.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

맵 파일 `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

무결성 검사 클래스 `Vendor\Migration\Step\GreatBlog\Integrity` 확장 `Migration\App\Step\AbstractIntegrity` 및 는 `perform` 테이블 구조를 확인하는 방법

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

그런 다음 데이터를 처리하고 Magento 2 데이터베이스에 저장할 클래스를 만들어야 합니다 `Vendor\Migration\Step\GreatBlog\Data`:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

Volume 클래스에서 `Vendor\Migration\Step\GreatBlog\Volume`, 데이터가 완전히 마이그레이션되었는지 확인합니다.

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

델타 마이그레이션 기능을 추가하려면 `deltalog.xml` 파일. in `group`를 지정하는 경우 변경 사항을 확인해야 하는 테이블의 이름을 지정합니다.

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

그런 다음 `Delta` 클래스 `Vendor\Migration\Step\GreatBlog\Delta` 확장 `Migration\App\Step\AbstractDelta`:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

예제에 제공된 사용자 지정 단계 구현 후 시스템은 단일 Magento 1 테이블에서 데이터를 가져와 `Vendor\Migration\Step\GreatBlog\Data` 클래스를 설정하고 두 Magento 2 테이블에 데이터를 저장합니다. 새로운 레코드와 변경된 레코드는 `Vendor\Migration\Step\GreatBlog\Delta` 클래스 이름을 지정합니다.

## 금지된 확장 메서드

다음 이후 [!DNL Data Migration Tool] Magento 2은 지속적으로 진화하고 있으며 기존 단계 및 핸들러는 변경될 수 있습니다. 다음과 같은 단계의 동작을 무시하지 않는 것이 좋습니다 [맵 단계](technical-specification.md#map-step), [URL 다시 작성 단계](technical-specification.md#url-rewrite-step)및 핸들러를 확장하여 클래스를 확장합니다.

일부 단계는 매핑을 지원하지 않으며, 코드를 변경하지 않으면 변경할 수 없습니다. 마이그레이션 종료 시 데이터를 변경하는 추가 단계를 작성하거나 [GitHub 문제](https://github.com/magento/data-migration-tool/issues) 기존 단계에서 새 확장 지점을 요청합니다.
