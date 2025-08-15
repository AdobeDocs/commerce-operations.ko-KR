---
title: system.xml 참조
description: 시스템 XML 파일이 Commerce 애플리케이션 구성을 관리하는 방법에 대해 알아봅니다.
feature: Configuration, System
badge: label="데이비드 램바우어에 의해 기여" type="Informative" url="https://github.com/DavidLambauer" tooltip="데이비드 램바우어"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 0%

---

# system.xml 참조

`system.xml` 파일을 사용하면 Commerce 시스템 구성을 관리할 수 있습니다. 이 항목을 `system.xml` 파일에 대한 일반 참조로 사용하십시오. `system.xml` 파일은 지정된 Commerce 2 확장의 `etc/adminhtml/system.xml` 아래에 있습니다.

다음 코드 스니펫은 파일의 기본 골격을 보여 줍니다.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>IDE에서 즉시 *XSD 유효성 검사를 수행하려면 `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`을(를) 실행할 수 있습니다.

## 탭 // 섹션 // 그룹/ 필드

`system.xml` 파일에서 서로 관련된 네 가지 다른 엔터티 형식을 정의할 수 있습니다. 다음 섹션에서는 탭, 섹션, 그룹 및 필드 간의 관계를 설명합니다. 다음 스크린샷에는 관리 백엔드의 Commerce 2 시스템 구성이 표시됩니다.
빨간색 사각형은 `system.xml` 파일에 정의된 다른 형식을 표시합니다.

![관리에서 구성된 섹션을 표시하는 스크린샷입니다.](../../assets/configuration/magento2-system-configuration.png)

탭은 다른 구성 영역을 의미론적으로 분할하는 데 사용됩니다. 각 탭에는 하위 메뉴로도 참조할 수 있는 섹션이 하나 이상 포함될 수 있습니다. 섹션에는 하나 이상의 그룹이 포함됩니다.
각 그룹에는 하나 이상의 필드가 나열됩니다. 그룹을 사용하여 다음 필드에 대한 일반 설명을 추가할 수도 있습니다. 언급된 바와 같이, 각 그룹은 하나 이상의 필드를 가질 수 있다. 필드는 가장 작은 엔티티입니다.
시스템 구성 컨텍스트에서 다음을 수행합니다.

## 탭

`<tab>` 태그는 시스템 구성의 기존 또는 새 탭에 대한 참조입니다.

### 탭 속성 참조

`<tab>` 태그에 다음 특성이 있을 수 있습니다.

| 속성 | 설명 | 유형 | 필수 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | 섹션을 참조하는 데 사용되는 식별자를 정의합니다. | `typeId` | 필수 |
| `translate` | 번역할 수 있는 필드를 정의합니다. 레이블을 번역할 수 있도록 `label`을(를) 제공하십시오. | `string` | 선택 사항 |
| `sortOrder` | 섹션의 정렬 순서를 정의합니다. 숫자가 높으면 섹션이 페이지 맨 아래로 밀리고, 숫자가 낮으면 섹션이 맨 위로 밀립니다. | `float` | 선택 사항 |
| `class` | 정의된 CSS 클래스를 렌더링된 탭 HTML 요소에 추가합니다. | `string` | 선택 사항 |

### 탭 노드 참조

`<tab>` 태그에 다음 하위 항목이 있을 수 있습니다.

| 노드 | 설명 | 유형 |
|---------|------------------------------------------------------|----------|
| `label` | 앞줄에 표시되는 레이블을 정의합니다. | `string` |

### 예: 탭 만들기

다음 코드 조각은 예제 데이터가 있는 새 탭을 만드는 방법을 보여 줍니다.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

위의 코드 조각은 식별자가 `A_UNIQUE_ID`인 새 탭을 만듭니다. `translate` 특성이 정의되어 있고 레이블을 참조하므로 `label` 노드를 변환할 수 있습니다. 렌더링 프로세스 중에 CSS 클래스 `a-custom-css-class-to-style-this-tab`이(가) 이 탭에 대해 만들어진 HTML 요소에 적용됩니다.
값이 `sortOrder`인 `10` 특성은 렌더링할 때 모든 탭 목록에서 탭의 위치를 정의합니다.

## 섹션

`<section>` 태그는 시스템 구성의 기존 또는 새 섹션에 대한 참조입니다.

### 섹션 속성 참조

`<section>` 태그에 다음 특성이 있을 수 있습니다.

| 속성 | 설명 | 유형 | 필수 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 섹션을 참조하는 데 사용되는 식별자를 정의합니다. | `typeId` | 필수 |
| `translate` | 번역할 수 있는 필드를 정의합니다. 레이블을 번역할 수 있도록 `label`을(를) 제공하십시오. | `string` | 선택 사항 |
| `type` | 렌더링된 HTML 요소의 입력 유형을 정의합니다. 기본값은 `text`입니다. | `string` | 선택 사항 |
| `sortOrder` | 섹션의 정렬 순서를 정의합니다. 숫자가 높으면 섹션이 페이지 맨 아래로 푸시되고 숫자가 낮으면 섹션이 맨 위로 푸시됩니다. | `float` | 선택 사항 |
| `showInDefault` | 섹션이 기본 구성 범위에 표시되는지 여부를 정의합니다. 섹션을 표시하려면 `1`을(를) 지정하고 섹션을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInStore` | 섹션을 저장소 수준에 표시할지 여부를 정의합니다. 섹션을 표시하려면 `1`을(를) 지정하고 섹션을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInWebsite` | 섹션을 웹 사이트 수준에 표시할지 여부를 정의합니다. 섹션을 표시하려면 `1`을(를) 지정하고 섹션을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `canRestore` | 섹션을 기본값으로 복원할 수 있는지 여부를 정의합니다. | `int` | 선택 사항 |
| `advanced` | 100.0.2 이후 더 이상 사용되지 않습니다. | `bool` | 선택 사항 |
| `extends` | 다른 섹션의 식별자를 제공하면 이 노드의 콘텐츠가 참조한 섹션을 확장합니다. | `string` | 선택 사항 |

### 섹션 노드 참조

`<section>` 태그에 다음 하위 항목이 있을 수 있습니다.

| 노드 | 설명 | 유형 |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | 앞줄에 표시되는 레이블을 정의합니다. | `string` |
| `class` | 정의된 CSS 클래스를 렌더링된 섹션 HTML 요소에 추가합니다. | `string` |
| `tab` | 관련 탭을 참조합니다. 탭의 ID가 필요합니다. | `typeTabId` |
| `header_css` | 이 글을 쓸 당시에는 사용도 평가도 하지 않았다. | `string` |
| `resource` | 이 섹션에 대한 권한 설정을 제공하기 위해 ACL 리소스를 참조합니다. | `typeAclResourceId` |
| `group` | 하나 이상의 하위 그룹을 정의합니다. | `typeGroup` |
| `frontend_model` | 렌더링을 변경하고 출력을 수정할 다른 프론트엔드 모델을 지정합니다. | `typeModel` |
| `include` | 호환 가능한 추가 `system_include.xsd`개 파일을 포함하는 데 사용됩니다. 일반적으로 큰 `system.xml`개 파일을 구성하는 데 사용됩니다. | `includeType` |

### 예: 섹션을 만들고 탭에 할당

다음 코드 조각은 새 섹션 만들기의 기본 사용을 보여 줍니다.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

위에서 설명한 섹션은 ID `A_UNIQUE_SECTION_ID`을(를) 정의합니다. 이 ID는 기본 구성 보기 및 저장소 컨텍스트에 표시됩니다. `label` 노드를 변환할 수 있습니다. 섹션은 ID가 `A_UNIQUE_ID`인 탭에 연결됩니다. ACL `VENDOR_MODULE::path_to_the_acl_resource`에 정의된 권한이 있는 사용자만 섹션에 액세스할 수 있습니다.

## 그룹

`<group>` 태그는 필드를 함께 그룹화하는 데 사용됩니다.

### 그룹 속성 참조

`<group>` 태그에 다음 특성이 있을 수 있습니다.

| 속성 | 설명 | 유형 | 필수 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 그룹을 참조하는 데 사용되는 식별자를 정의합니다. | `typeId` | 필수 |
| `translate` | 번역할 수 있는 필드를 정의합니다. 레이블을 번역할 수 있도록 `label`을(를) 제공하십시오. 여러 필드는 공백으로 구분해야 합니다. | `string` | 선택 사항 |
| `type` | 렌더링된 HTML 요소의 입력 유형을 정의합니다. 기본값은 `text`입니다. | `string` | 선택 사항 |
| `sortOrder` | 섹션의 정렬 순서를 정의합니다. 숫자가 높으면 섹션이 페이지 맨 아래로 푸시되고 숫자가 낮으면 섹션이 맨 위로 푸시됩니다. | `float` | 선택 사항 |
| `showInDefault` | 그룹이 기본 구성 범위에 표시되는지 여부를 정의합니다. 그룹을 표시하려면 `1`을(를) 지정하고 그룹을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInStore` | 그룹이 저장소 수준에 표시되는지 여부를 정의합니다. 그룹을 표시하려면 `1`을(를) 지정하고 그룹을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInWebsite` | 그룹이 웹 사이트 수준에 표시되는지 여부를 정의합니다. 그룹을 표시하려면 `1`을(를) 지정하고 그룹을 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `canRestore` | 그룹을 기본값으로 복원할 수 있는지 여부를 정의합니다. | `int` | 선택 사항 |
| `advanced` | 100.0.2 이후 더 이상 사용되지 않습니다. | `bool` | 선택 사항 |
| `extends` | 다른 그룹의 식별자를 제공하면 이 노드의 콘텐츠가 참조한 섹션을 확장합니다. | `string` | 선택 사항 |

### 그룹 노드 참조

`<group>` 태그에 다음 하위 항목이 있을 수 있습니다.

| 노드 | 설명 | 유형 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | 앞줄에 표시되는 레이블을 정의합니다. | `string` |
| `fieldset_css` | 그룹 필드 집합에 하나 이상의 CSS 클래스를 추가합니다. | `string` |
| `frontend_model` | 렌더링을 변경하고 출력을 수정할 다른 프론트엔드 모델을 지정합니다. | `typeModel` |
| `clone_model` | 필드를 복제할 특정 모델을 지정합니다. | `typeModel` |
| `clone_fields` | 필드의 복제가 활성화되었거나 비활성화되었습니다. | `int` |
| `help_url` | 확장할 수 없습니다. 아래를 참조하십시오. | `typeUrl` |
| `more_url` | 확장할 수 없습니다. 아래를 참조하십시오. | `typeUrl` |
| `demo_link` | 확장할 수 없습니다. 아래를 참조하십시오. | `typeUrl` |
| `comment` | 그룹 레이블 아래에 주석을 추가합니다. `<![CDATA[//]]>`을(를) 사용하여 HTML을 적용할 수 있습니다. | `string` |
| `hide_in_single_store_mode` | 그룹이 단일 저장소 모드로 표시되어야 하는지 여부입니다. `1`은(는) 그룹을 숨기고, `0`은(는) 그룹을 표시합니다. | `int` |
| `field` | 이 그룹에서 사용할 수 있는 필드를 한 개 이상 정의합니다. | `field` |
| `group` | 하나 이상의 하위 그룹을 정의합니다. | `unbounded` |
| `depends` | 를 사용하여 다른 필드에 대한 종속성을 선언할 수 있습니다. 특정 필드의 값이 `1`인 경우에만 특정 필드/그룹을 표시하는 데 사용됩니다. 이 노드에는 `section/group/field` 문자열이 필요합니다. | `depends` |
| `attribute` | 사용자 지정 특성은 프론트엔드 모델에서 사용할 수 있습니다. 일반적으로 는 주어진 프론트엔드 모델을 더 역동적으로 만드는 데 사용됩니다. | `attribute` |
| `include` | 호환 가능한 추가 `system_include.xsd`개 파일을 포함하는 데 사용됩니다. 일반적으로 큰 `system.xml`개 파일을 구성하는 데 사용됩니다. | `includeType` |

>[!WARNING]
>
>`more_url`, `demo_url` 및 `help_url` 노드는 한 번만 사용되는 PayPal 프론트엔드 모델로 정의됩니다. 이러한 노드는 재사용할 수 없습니다.

### 예: 주어진 섹션에 대한 그룹 만들기

다음 코드 조각은 새 그룹을 만드는 기본 사용 방법을 보여 줍니다.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

위에서 설명한 그룹은 ID `A_UNIQUE_GROUP_ID`을(를) 정의하며, 기본 구성 보기와 저장소 컨텍스트에 표시됩니다. `label`과(와) `comment`은(는) 모두 변환 가능한 것으로 표시됩니다.

## 필드

`<field>`-태그는 `<group>`-태그 내에서 특정 구성 값을 정의하는 데 사용됩니다.

### 필드 속성 참조

`<field>` 태그에 다음 특성이 있을 수 있습니다.

| 속성 | 설명 | 유형 | 필수 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 필드를 참조하는 데 사용되는 식별자를 정의합니다. | `typeId` | 필수 |
| `translate` | 번역할 수 있는 필드를 정의합니다. 레이블을 번역할 수 있도록 `label`을(를) 제공하십시오. 여러 필드는 공백으로 구분해야 합니다. | `string` | 선택 사항 |
| `type` | 렌더링된 HTML 요소의 입력 유형을 정의합니다. 기본값은 `text`입니다. | `string` | 선택 사항 |
| `sortOrder` | 섹션의 정렬 순서를 정의합니다. 숫자가 높으면 섹션이 페이지 맨 아래로 밀리고, 숫자가 낮으면 섹션이 맨 위로 밀립니다. | `float` | 선택 사항 |
| `showInDefault` | 필드가 기본 구성 범위에 표시되는지 여부를 정의합니다. 필드를 표시하려면 `1`을(를) 지정하고 필드를 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInStore` | 필드가 저장소 수준에 표시되는지 여부를 정의합니다. 필드를 표시하려면 `1`을(를) 지정하고 필드를 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `showInWebsite` | 필드가 웹 사이트 수준에 표시되는지 여부를 정의합니다. 필드를 표시하려면 `1`을(를) 지정하고 필드를 숨기려면 `0`을(를) 지정합니다. | `int` | 선택 사항 |
| `canRestore` | 필드를 기본값으로 복원할 수 있는지 여부를 정의합니다. | `int` | 선택 사항 |
| `advanced` | 100.0.2 이후 더 이상 사용되지 않습니다. | `bool` | 선택 사항 |
| `extends` | 다른 필드의 식별자를 제공하면 이 노드의 콘텐츠가 참조한 섹션을 확장합니다. | `string` | 선택 사항 |

### 필드 유형 참조

`<field>`-Tag에는 `type=""` 특성에 대해 다음 값이 있을 수 있습니다.

| 유형 | 설명 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 표준, 단일 행 텍스트 필드 |
| `textarea` | 텍스트 블록 |
| `select` | 일반 드롭다운입니다. 사용자 지정 `source_model`이(가) 필요할 수 있습니다. `Yes/No`개 선택 항목에도 사용됩니다. 예제는 `Magento\Search\Model\Adminhtml\System\Config\Source\Engine`을(를) 참조하십시오. |
| `multiselect` | `select`과(와) 유사하지만 여러 옵션이 유효합니다. |
| `button` | 즉각적인 이벤트를 트리거하는 단추입니다. 버튼 텍스트 및 작업을 정의하려면 사용자 정의 프론트엔드 모델이 필요합니다. 예제는 `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean`을(를) 참조하십시오. |
| `obscure` | 값이 암호화되어 `****`(으)로 표시되는 텍스트 필드입니다. 브라우저에서 &quot;요소 검사&quot;를 사용하여 유형을 변경해도 값이 표시되지 않습니다. |
| `password` | `obscure`과(와) 마찬가지로 숨겨진 값이 암호화되지 않고 브라우저에서 &quot;Inspect Element&quot;를 사용하여 형식을 강제로 변경하면 값이 표시됩니다. |
| `file` | 처리를 위해 파일을 업로드할 수 있습니다. |
| `label` | 편집 가능한 필드 대신 레이블을 표시합니다. 특정 범위(예: 보기 수준만 저장)에서만 필드를 편집할 수 있는 경우 이 유형을 사용합니다. |
| `time` | 세 개의 드롭다운-시간, 분, 초를 사용하여 시간을 설정하도록 제어합니다. |
| `allowspecific` | 특정 국가의 다중 선택 목록. `source_model`과(와) 같은 `Magento\Shipping\Model\Config\Source\Allspecificcountries` 필요 |
| `image` | 이미지를 업로드할 수 있습니다. |
| `note` | 정보 메모를 페이지에 추가할 수 있습니다. 이 형식에는 메모를 렌더링하는 데 `frontend_model`이(가) 필요합니다. |

사용자 지정 필드 유형을 만들 수도 있습니다. 이 작업은 작업이 있는 특수 버튼이 필요할 때 수행됩니다. 이렇게 하려면 두 가지 기본 요소가 필요합니다.

- `adminhtml` 영역에 블록을 만드는 중
- `type=""`을(를) 이 블록의 경로로 설정하는 중

블록 자체에는 최소한 `__construct` 메서드와 `getElementHtml()` 메서드가 필요합니다. [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping)은(는) 사용자 지정 형식의 간단한 예입니다.

예를 들어 OfflineShipping 모듈에서 내보내기 단추가 `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export`에 정의되어 있고 필드 정의는 다음과 같습니다.

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### 필드 노드 참조

`<field>` 태그에 다음 하위 항목이 있을 수 있습니다.

| 노드 | 설명 | 유형 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | 앞줄에 표시되는 레이블을 정의합니다. | `string` |
| `comment` | 필드 레이블 아래에 주석을 추가합니다. `<![CDATA[//]]>`을(를) 사용하여 HTML을 적용할 수 있습니다. | `string` |
| `tooltip` | 이 필드의 의미를 설명하는 데 사용할 수 있는 또 다른 가능한 프론트엔드 요소입니다. 필드 옆에 작은 아이콘으로 표시됩니다. | `string` |
| `hint` | 추가 정보를 표시합니다. 특정 `frontend_model`에서만 사용할 수 있습니다. | `string` |
| `frontend_class` | 정의된 CSS 클래스를 렌더링된 섹션 HTML 요소에 추가합니다. | `string` |
| `frontend_model` | 렌더링을 변경하고 출력을 수정할 다른 프론트엔드 모델을 지정합니다. | `typeModel` |
| `backend_model` | 구성된 값을 수정할 다른 백엔드 모델을 지정합니다. | `typeModel` |
| `source_model` | 특정 값 집합을 제공하는 다른 원본 모델을 지정합니다. | `typeModel` |
| `config_path` | 필드의 일반 구성 경로를 덮어쓰는 데 사용할 수 있습니다. | `typeConfigPath` |
| `validate` | 다른 유효성 검사 규칙(공백으로 구분)을 정의합니다. 사용 가능한 유효성 검사 규칙의 전체 참조 목록이 아래에 나와 있습니다. | `string` |
| `can_be_empty` | 필드가 비어 있을 수 있도록 지정하기 위해 `type`이(가) `multiselect`인 경우 사용됩니다. | `int` |
| `if_module_enabled` | 특정 모듈이 활성화된 경우에만 필드를 표시하는 데 사용됩니다. | `typeModule` |
| `base_url` | 파일 업로드를 위해 `upload_dir`과(와) 함께 사용됩니다. | `typeUrl` |
| `upload_dir` | 업로드할 대상 디렉터리를 지정합니다. 이 노드에는 추가 속성과 노드가 있습니다. 이걸 사용하기 전에 그들을 살펴보세요. | `typeUploadDir` |
| `button_url` | `button_url` 및 `button_label`이(가) 지정된 경우 단추를 표시합니다. 일반적으로 사용자 지정 프론트엔드 모델과 함께 사용됩니다. | `typeUrl` |
| `button_label` | `button_label` 및 `button_url`이(가) 지정된 경우 단추를 표시합니다. 일반적으로 사용자 지정 프론트엔드 모델과 함께 사용됩니다. | `string` |
| `more_url` | 확장할 수 없습니다. 아래를 참조하십시오. | `typeUrl` |
| `demo_url` | 확장할 수 없습니다. 아래를 참조하십시오. | `typeUrl` |
| `hide_in_single_store_mode` | 그룹이 단일 저장소 모드로 표시되어야 하는지 여부입니다. `1`은(는) 그룹을 숨기고, `0`은(는) 그룹을 표시합니다. | `int` |
| `options` | 사용되지 않습니다. 더 이상 사용되지 않을 수 있습니다. | `complexType` |
| `depends` | 를 사용하여 다른 필드에 종속성을 선언할 수 있습니다. 특정 필드의 값이 `1`인 경우에만 특정 필드/그룹을 표시하는 데 사용됩니다. 이 노드에는 `section/group/field` 문자열이 필요합니다. | `complexType` |
| `attribute` | 사용자 지정 특성은 프론트엔드 모델에서 사용할 수 있습니다. 일반적으로 는 주어진 프론트엔드 모델을 더 역동적으로 만드는 데 사용됩니다. | `complexType` |
| `requires` | 확장할 수 없습니다. 아래를 참조하십시오. | `complexType` |

>[!WARNING]
>
>`more_url`, `demo_url`, `requires` 및 `options` 노드는 다른 핵심 결제 모델에서 정의되며 한 번만 사용됩니다. 이러한 노드는 재사용할 수 없습니다.

### 예: 주어진 그룹에 두 개의 필드 만들기

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

위의 예에서는 기본적으로 및 스토어 보기에서 표시/구성 가능한 두 개의 필드를 만듭니다. 두 필드에는 사용자에게 용도를 설명하는 댓글과 도구 설명이 있습니다. `label` 노드를 변환할 수 있습니다.
`ANOTHER_UNIQUE_FIELD_ID`에서 지정한 모듈을 전체적으로 사용하도록 설정하면 식별자가 `if_module_enabled`인 필드가 표시됩니다. 또한 이 필드는 규칙 `required-entry` 및 `no-whitespace`에 대해 해당 값의 유효성을 검사합니다.
식별자가 `A_UNIQUE_FIELD_ID`인 필드는 해당 값 `Yes` 및 `No`을(를) 제공하는 다른 원본 모델을 정의합니다.

### 공통 소스 모델

Commerce 2 Core에서 제공하는 소스 모델은 다음과 같습니다. 일반적으로 소스 모델이 더 많습니다. 다음 목록은 가장 일반적인 소스 모델을 설명합니다. 이러한 원본 모델이 제대로 작동하려면 필드 특성 `type`을(를) `select`(으)로 설정해야 합니다.

| Source 모델 | 설명 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | `Yes`, `No` 및 `Specified` 값을 제공합니다. |
| `Magento\Config\Model\Config\Source\Enabledisable` | `Enable`, `Disable` 값을 제공합니다. 값을 데이터베이스에 `0` 및 `1`(으)로 저장합니다. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` 및 `24 Hours` 값을 제공합니다. 값은 정수로 저장됩니다. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 시간 형식(12시간/24시간)의 값을 제공합니다. |
| `Magento\Cron\Model\Config\Source\Frequency` | `Daily`, `Weekly` 및 `Monthly` 값을 제공합니다. 값이 데이터베이스에 `D`, `W` 및 `M`(으)로 저장됩니다. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 특정 언어의 2자리 코드 값을 ISO 639-1 형식(예: en)으로 제공합니다. |
| `Magento\Config\Model\Config\Source\Locale` | 위의 값과 비슷하지만 로케일 코드(예: en_US)와 관련되어 있습니다. |

### 필드 유효성 검사

필드에는 하나 이상의 유효성 검사기 클래스가 할당되어 사용자의 입력이 확장의 요구 사항을 충족하는지 확인할 수 있습니다. 유효성 검사 규칙은 `<validate>` 태그에 적용할 수 있습니다.
다음 예제에서는 필드의 유효성을 검사하고 몇 가지 다른 유효성 검사 규칙을 추가합니다.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

다음 유효성 검사 규칙을 사용할 수 있습니다.

| 규칙 | 설명 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 문자, 숫자, 공백 또는 밑줄만 허용합니다. |
| `integer` | 소수가 아닌 양수 또는 음수를 허용합니다. |
| `ipv4` | 유효한 IP v4 주소를 허용합니다. |
| `ipv6` | 유효한 IP v6 주소를 허용합니다. |
| `letters-only` | 문자만 허용합니다. 예: `abcABC`. |
| `letters-with-basic-punc` | 문자 또는 구두점만 허용합니다.<br>다음 식을 전달해야 합니다. `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | (영국) 휴대폰 번호를 허용합니다. |
| `no-marginal-whitespace` | 값의 시작 또는 끝에 공백을 사용할 수 없습니다. |
| `no-whitespace` | 공백을 사용할 수 없습니다. |
| `phoneUK` | (영국) 전화 번호를 허용합니다. |
| `phoneUS` | 미국 전화 번호를 허용합니다. |
| `required-entry` | 빈 값(`validate-no-empty`과 동등한 유효성 검사)을 허용하지 않습니다.<br>유효성 검사 실패 메시지: &quot;필수 필드입니다.&quot; |
| `time` | 00:00에서 23:59 사이의 24시간 형식으로 올바른 시간을 허용합니다. 예: `15`, `15:05` 또는 `15:05:48`. |
| `time12h` | 오전 12:00에서 오후 11:59:59 사이의 12시간 형식으로 올바른 시간을 허용합니다. 예: `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | 숫자와 영문자를 모두 사용하여 7자 이상을 허용합니다. |
| `validate-alphanum-with-spaces` | 문자(a-z 또는 A-Z), 숫자(0-9) 또는 공백만 사용할 수 있습니다. |
| `validate-clean-url` | 유효한 URL을 허용합니다. 예: `https://www.example.com` 또는 `www.example.com`. |
| `validate-currency-dollar` | 유효한(달러) 금액을 허용합니다. 예를 들어 $100.00입니다. |
| `validate-data` | 문자(a-z 또는 A-Z), 숫자(0-9) 또는 밑줄(\_)만 사용할 수 있습니다.<br>첫 문자는 문자여야 합니다.<br>(식 `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>유효성 검사 실패 메시지: &quot;이 필드에는 문자(a-z 또는 A-Z), 숫자(0-9) 또는 밑줄(\_)만 사용하십시오. 첫 번째 문자는 문자여야 합니다.&quot; |
| `validate-date-au` | dd/mm/yyyy 날짜 형식을 적용합니다. 예: 2006년 3월 17일의 경우 2006년 3월 17일 |
| `validate-email` | 유효한 이메일 주소를 허용합니다. 예: johndoe@domain.com. |
| `validate-emailSender` | 유효한 이메일 주소를 허용합니다. 예: johndoe@domain.com. |
| `validate-fax` | 유효한 팩스 번호를 허용합니다. 예: 123-456-7890. |
| `validate-no-empty` | 빈 값(`requried-entry`과 동등한 유효성 검사)을 허용하지 않습니다.<br>유효성 검사 실패 메시지: &quot;빈 값&quot; |
| `validate-no-html-tags` | HTML 태그를 사용할 수 없습니다. |
| `validate-password` | 6자 이상을 허용합니다. 선행 및 후행 공백은 무시됩니다. |
| `validate-phoneLax` | 유효한 전화 번호를 허용합니다. 예: (123) 456-7890 또는 123-456-7890. |
| `validate-phoneStrict` | 유효한 전화 번호를 허용합니다. 예: (123) 456-7890 또는 123-456-7890. |
| `validate-select` | 선택한 선택 옵션에 `null` 값, 문자열 값 `none` 또는 문자열 길이 0이 없도록 강제 적용합니다. |
| `validate-ssn` | 유효한 미국 사회 보장 번호를 허용합니다. 예: 123-45-6789. |
| `validate-street` | 문자(a-z 또는 A-Z), 숫자(0-9), 공백 및 &quot;#&quot;만 사용할 수 있습니다. |
| `validate-url` | 유효한 URL을 허용합니다. 프로토콜이 필요합니다(http://, https:// 또는 ftp://). |
| `validate-xml-identifier` | 유효한 XML 식별자를 허용합니다. 예: something_1, block5, id-4. |
| `validate-zip-us` | 유효한 (미국) 우편 번호를 허용합니다. 예: 90602 또는 90602-1234. |
| `vinUS` | (미국) 차량 식별 번호(VIN) 값을 허용합니다. |

### 기본값

`etc/config.xml` 노드에서 기본값을 지정하여 모듈의 `section/group/field_ID` 파일에 필드의 기본값을 설정할 수 있습니다.

#### 예: `ANOTHER_UNIQUE_FIELD_ID`에 대한 기본값 설정(기본 범위)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### 예: `ANOTHER_UNIQUE_FIELD_ID`의 기본값 설정(웹 사이트 범위)

`websites` 태그를 사용하여 특정 웹 사이트에 대한 기본값을 지정하십시오.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
