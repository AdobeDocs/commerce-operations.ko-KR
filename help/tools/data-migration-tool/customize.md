---
title: ' [!DNL Data Migration Tool] 사용자 지정'
description: Magento 1과 Magento 2 간에 확장에서 만든 데이터를 전송하기 위해  [!DNL Data Migration Tool] 을(를) 사용자 지정하는 방법을 알아봅니다.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 구성

경우에 따라 [확장](https://commercemarketplace.adobe.com//extensions.html) 또는 사용자 지정 코드에서 만든 데이터 형식 및 구조가 Magento 1과 Magento 2에서 다릅니다. [!DNL Data Migration Tool] 내의 확장 지점을 사용하여 이 데이터를 마이그레이션하십시오. 데이터 형식 및 구조가 동일한 경우 사용자 개입 없이 이 툴이 데이터를 자동으로 마이그레이션할 수 있습니다.

마이그레이션하는 동안 [맵 단계](technical-specification.md#map-step)에서 확장에서 만든 테이블을 포함하여 모든 Magento 1과 Magento 2 테이블을 검색하고 비교합니다. 테이블이 동일하면 도구에서 데이터를 자동으로 마이그레이션합니다. 테이블이 다른 경우 도구가 종료되고 사용자에게 알립니다.

>[!NOTE]
>
>[을(를) 확장하기 전에 ](technical-specification.md)기술 사양[!DNL Data Migration Tool]을 읽으십시오. 또한 마이그레이션 도구 사용에 대한 일반적인 정보는 [마이그레이션 안내서](../overview.md)를 검토하십시오.


## 사소한 데이터 형식 및 구조 변경

대부분의 경우 [맵 단계](technical-specification.md#map-step)는 `map.xml` 파일에서 다음 방법을 사용하여 사소한 데이터 형식 및 구조 변경을 충분히 확인합니다.

- 매핑 규칙을 사용하여 테이블 또는 필드 이름 변경
- 기존 처리기 또는 사용자 지정 처리기로 데이터 형식 변환

다음은 매핑 규칙과 핸들러를 모두 사용하는 예를 보여줍니다. 이 예제에서는 Magento 2용으로 개선된 &quot;GreatBlog&quot;라는 가상의 Magento 1 확장을 사용합니다.

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

- `great_blog_index` 인덱스 테이블에서 불필요한 데이터를 마이그레이션하지 마십시오.
- 테이블 `great_blog_publication`의 이름이 Magento 2에서 `great_blog_post`(으)로 변경되었으므로 데이터가 새 테이블로 마이그레이션됩니다.
   - `summary` 필드의 이름이 `title`(으)로 변경되었으므로 데이터가 새 필드로 마이그레이션됩니다.
   - `priority` 필드가 제거되어 Magento 2에 더 이상 존재하지 않습니다.
   - `body` 필드의 데이터 형식이 변경되었으므로 사용자 지정 처리기에서 처리해야 합니다. `\Migration\Handler\GreatBlog\NewFormat`.
- Magento 2에서 &quot;GreatBlog&quot; 확장을 위해 새로운 등급 기능이 개발되었습니다.
   - 새 `great_blog_rating` 테이블을 만들었습니다.
   - 새 `great_blog_post.rating` 필드가 만들어졌습니다.

### 다른 단계에서 매핑 확장

[EAV 단계](technical-specification.md#eav-step) 및 고객 특성 단계와 같은 다른 단계는 매핑을 지원합니다. 이 단계는 사전 정의된 Magento 테이블 목록을 마이그레이션합니다. 예를 들어 &quot;GreatBlog&quot; 확장에 `eav_attribute` 테이블에 추가 필드가 있고 Magento 2에서 이름이 변경되었다고 가정해 봅시다. 테이블이 [EAV 단계](technical-specification.md#eav-step)에 의해 처리되므로 `map-eav.xml` 파일에 대해 매핑 규칙을 작성해야 합니다. `map.xml` 및 `map-eav.xml` 파일에서 동일한 `map.xsd` 스키마를 사용하므로 매핑 규칙은 동일하게 유지됩니다.

## 주요 데이터 형식 및 구조 변경

`config.xml` 파일에는 맵 단계 외에도 다음과 같은 주요 형식 및 구조 변경 사항으로 데이터를 마이그레이션하는 다른 단계가 있습니다.

- [Url 다시 작성 단계](technical-specification.md#url-rewrite-step)
- OrderGrid 단계
- [EAV 단계](technical-specification.md#eav-step)

[맵 단계](technical-specification.md#map-step)와 달리 이 단계는 모든 테이블 대신 미리 정의된 테이블 목록을 검사합니다.

주요 데이터 형식 및 구조 변경의 경우 사용자 지정 단계를 만듭니다.

### 사용자 지정 단계 만들기

동일한 &quot;GreatBlog&quot; 예를 사용하여, 확장에 Magento 1에 테이블이 하나 있지만 Magento 2에 테이블이 두 개 있도록 다시 디자인되었다고 가정해 봅시다.

Magento 1에 단일 `greatblog_post` 테이블이 있습니다.

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento 2에 태그 `greatblog_post_tags`에 대한 새 테이블이 도입되었습니다.

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

이제 Magento 2 `greatblog_post` 테이블은 다음과 같습니다.

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

이전 테이블 구조에서 새 테이블 구조로 모든 데이터를 마이그레이션하려면 `config.xml` 파일에 사용자 지정 단계를 만들 수 있습니다. For example:

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

이 도구는 `config.xml` 파일에서 위쪽에서 아래쪽으로 위치에 따라 단계를 실행합니다. 이 예제에서는 `GreatBlog Step`이(가) 마지막으로 실행됩니다.

단계에는 네 가지 유형의 클래스가 포함될 수 있습니다.

- 무결성 검사
- 데이터 전달
- 볼륨 검사
- 델타 게재

>[!NOTE]
>
>자세한 내용은 [구성](technical-specification.md#configuration), [단계 내부](technical-specification.md#step-internals), [단계](technical-specification.md#step-stages) 및 [실행 모드](technical-specification.md#running-modes)를 참조하세요.


이러한 클래스 내에서 복잡한 SQL 쿼리를 취합하여 데이터를 가져오고 마이그레이션할 수 있습니다. 또한 [맵 단계](technical-specification.md#map-step)에서 이러한 테이블을 &quot;무시해야&quot; 합니다. 기존의 모든 테이블을 검사하고 데이터가 `<ignore>` 파일의 `map.xml` 태그에 없으면 데이터를 마이그레이션하려고 시도하기 때문입니다.

무결성 검사를 위해 `config.xml` 파일에 추가 맵 파일을 정의하여 테이블 구조가 예상과 같은지 확인합니다.

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

무결성 검사 클래스 `Vendor\Migration\Step\GreatBlog\Integrity`이(가) `Migration\App\Step\AbstractIntegrity`을(를) 확장하고 테이블 구조를 확인하는 `perform` 메서드를 포함합니다.

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

그런 다음 Magento 2 데이터베이스 `Vendor\Migration\Step\GreatBlog\Data`에 데이터를 처리하고 저장하는 클래스를 만들어야 합니다.

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

볼륨 클래스 `Vendor\Migration\Step\GreatBlog\Volume`에서 데이터가 완전히 마이그레이션되었는지 확인합니다.

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

델타 마이그레이션 기능을 추가하려면 `deltalog.xml` 파일에 새 그룹을 추가하십시오. `group`에서 변경 내용을 확인해야 하는 테이블의 이름을 지정합니다.

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

그런 다음 `Delta`을(를) 확장하는 `Vendor\Migration\Step\GreatBlog\Delta` 클래스 `Migration\App\Step\AbstractDelta`을(를) 만듭니다.

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

예에 제공된 사용자 지정 단계 구현 후 시스템은 단일 Magento 1 테이블에서 데이터를 가져옵니다.
`Vendor\Migration\Step\GreatBlog\Data` 클래스를 사용하여 처리하고 두 개의 Magento 2 테이블에 데이터를 저장합니다. 새 레코드와 변경된 레코드는 `Vendor\Migration\Step\GreatBlog\Delta` 클래스를 사용하여 델타 마이그레이션 시 전달됩니다.

## 금지된 확장 메서드

[!DNL Data Migration Tool] 및 Magento 2는 계속 발전하고 있으므로 기존 단계 및 처리기는 변경될 수 있습니다. 클래스를 확장하여 [맵 단계](technical-specification.md#map-step), [URL 다시 작성 단계](technical-specification.md#url-rewrite-step) 및 처리기와 같은 단계의 동작을 재정의하지 않는 것이 좋습니다.

일부 단계는 매핑을 지원하지 않으며 코드를 변경하지 않고 변경할 수 없습니다. 마이그레이션 종료 시 데이터를 변경하는 추가 단계를 작성하거나 [GitHub 문제](https://github.com/magento/data-migration-tool/issues)를 만들고 기존 단계에서 새 확장 지점을 요청할 수 있습니다.
