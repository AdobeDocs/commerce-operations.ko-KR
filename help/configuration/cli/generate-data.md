---
title: 성능 테스트를 위한 데이터 생성
description: 성능 테스트에 사용할 대량의 데이터를 생성하는 방법을 알아봅니다.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 8%

---

# 성능 테스트 데이터

을(를) 사용하려면 [성능 툴킷](https://github.com/magento/magento2/blob/2.4/setup/performance-toolkit) 또는 성능 테스트를 위한 다른 도구에서 저장소, 카테고리 및 제품과 같은 많은 양의 데이터를 생성해야 합니다.

{{file-system-owner}}

## 프로필

을 사용하여 만드는 데이터의 양을 조정할 수 있습니다 _프로필_ (small, medium, large 및 extra large). 프로필은 `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` 디렉토리.

예를 들어, `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

다음 그림은 를 사용하여 제품이 상점 정면에 표시되는 방식을 보여 줍니다. _작음_ 프로필:

![생성된 데이터가 있는 샘플 상점](../../assets/configuration/generate-data.png)

다음 표는 데이터 생성기 프로필에 대한 세부 사항을 제공합니다. small, medium, large 및 extra large.

| 매개 변수 | 작은 프로필 | 미디어 프로필 | 중간 다중 사이트 프로필 | 큰 프로필 | 매우 큰 프로필 |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16개(옵션 24개) | 640 및 24개 옵션 | 800(24개 옵션) 및 79(200개 옵션) | 8,000개(옵션 24개) | 16,000 및 24 개 옵션 |
| `product_images` | 제품당 이미지 100개 / 이미지 3개 | 제품당 이미지 1000개 / 이미지 3개 | 제품당 이미지 1000개 / 이미지 3개 | 2000개 이미지/제품당 3개 이미지 | 2000개 이미지/제품당 3개 이미지 |
| `categories` | 30 | 300 | 100 | 3,000 | 6,000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2,000 | 2,000 | 5,000 | 10,000 |
| `tax rates` | 130 | 40,000 | 40,000 | 40,000 | 40,000 |
| `orders` | 80 | 50,000 | 50,000 | 100,000 | 150,000 |

### 데이터 생성기 실행

>[!WARNING]
>
>데이터 생성기를 실행하기 전에 서버에서 실행 중인 모든 cron 작업을 비활성화하십시오. cron 작업을 비활성화하면 데이터 생성기가 활성 cron 작업과 충돌하는 작업을 수행하지 못하고 불필요한 오류가 발생하지 않습니다.

이 섹션에서 설명한 대로 명령을 실행합니다. 명령이 실행되면 다음을 수행해야 합니다. [모든 인덱서 다시 인덱싱](../cli/manage-indexers.md).

명령 옵션:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

위치 `<path-to-profile>` 프로필의 절대 파일 시스템 경로 및 이름을 지정합니다.

예를 들어,

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

작은 프로필에 대한 샘플 출력:

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## 성능 고정 장치

### 관리자 사용자

관리자 사용자를 생성합니다. XML 프로필 노드:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### 속성 집합

지정된 구성으로 속성 세트를 생성합니다. XML 프로필 노드:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### 번들 제품

번들 제품을 생성합니다. 생성된 번들 선택 사항은 카탈로그에 개별적으로 표시되지 않습니다. 제품은 카테고리 및 웹 사이트별로 균일하게 배포됩니다. If  `assign_entities_to_all_websites` 프로필이 (으)로 설정됨 `1`. 제품은 모든 웹 사이트에 할당됩니다.

XML 프로필 노드:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### 장바구니 가격 규칙

장바구니 가격 규칙을 생성합니다. XML 프로필 노드:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### 카탈로그 가격 규칙

카탈로그 가격 규칙을 생성합니다. XML 프로필 노드:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### 카테고리

카테고리를 생성합니다. If `assign_entities_to_all_websites` 이(가) (으)로 설정됨 `0`, 모든 카테고리는 루트 카테고리별로 균일하게 배포됩니다. 그렇지 않으면 모든 카테고리가 하나의 루트 카테고리에 할당됩니다.

XML 프로필 노드:

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### 구성

구성 필드에 대한 값을 설정합니다. XML 프로필 노드:

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### 구성 가능한 제품

구성 가능한 제품을 생성합니다. 생성된 구성 가능한 옵션은 카탈로그에 개별적으로 표시되지 않습니다. 제품은 카테고리 및 웹 사이트별로 균일하게 배포됩니다. If `assign_entities_to_all_websites` 이(가) (으)로 설정됨 `1`, 제품이 모든 웹 사이트에 할당됩니다.

지원되는 XML 노드 형식은 다음과 같습니다.

- 기본 및 사전 정의된 속성 세트당 분배:

   ```xml
   <!-- Number of configurable products -->
   <configurable_products>{int}</configurable_products>
   ```

- 기존 속성 세트를 기반으로 제품을 생성합니다.

   ```xml
   <configurable_products>
   
       <config>
               <!-- Existing attribute set name -->
               <attributeSet>{string}</attributeSet>
   
               <!-- Configurable sku pattern with %s -->
               <sku>{string}</sku>
   
               <!-- Number of configurable products -->
               <products>{int}</products>
   
               <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
               <category>[{string}]</category>
   
               <!-- Type of Swatch attribute e.g. color|image -->
               <swatches>{string}</swatches>
       </config>
   
   <!-- ... more entries ... -->
   </configurable_products>
   ```

- 지정된 수의 특성 및 옵션을 사용하여 동적으로 작성된 특성 세트를 기반으로 제품을 생성합니다.

   ```xml
   <configurable_products>
   
       <config>
           <!-- Number of attributes in configurable product -->
           <attributes>{int}</attributes>
   
           <!-- Number of options per attribute -->
           <options>{int}</options>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
           <category>[{string}]</category>
   
           <!-- Type of Swatch attribute e.g. color|image -->
           <swatches>{string}</swatches>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

- 각 속성에 대해 지정된 구성을 사용하여 동적으로 작성된 속성 세트를 기반으로 제품을 생성합니다.

   ```xml
   <configurable_products>
   
       <config>
           <attributes>
               <!-- Configuration for a first attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
   
                   <!-- Type of Swatch attribute -->
                   <swatches>{string}</swatches>
               </attribute>
   
               <!-- Configuration for a second attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
               </attribute>
           </attributes>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
           <category>[{string}]</category>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

### 고객

고객을 생성합니다. 고객은 사용 가능한 모든 웹 사이트에 대해 정상적인 배포를 합니다. 각 고객은 고객 이메일, 고객 그룹 및 고객 주소를 제외하고 동일한 데이터를 갖습니다.

XML 프로필 노드:

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

다음 XML을 사용하여 고객 구성을 변경할 수 있습니다.

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### 제품 이미지

제품 이미지를 생성합니다. 크기 조정은 생성에 포함되지 않습니다.

XML 프로필 노드:

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### 인덱서 상태

인덱서의 상태를 업데이트합니다. XML 프로필 노드:

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### 주문 수

다양한 유형의 주문 품목을 구성 가능한 수만큼 사용하여 주문을 생성합니다. 선택적으로 생성된 주문에 대해 비활성 견적을 생성합니다.

XML 프로필 노드:

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### 단순 제품

간단한 제품을 생성합니다. 제품은 기본 및 사전 정의된 속성 세트별로 배포됩니다. 추가 속성 세트가 프로필에 다음과 같이 지정된 경우: `<product_attribute_sets>{int}</product_attribute_sets>`, 제품은 추가 속성 세트에 따라서도 배포됩니다.

제품은 카테고리 및 웹 사이트별로 균일하게 배포됩니다. If `assign_entities_to_all_websites` 이(가) (으)로 설정됨 `1`, 제품이 모든 웹 사이트에 할당됩니다.

XML 프로필 노드:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### 웹 사이트

웹 사이트를 생성합니다. XML 프로필 노드:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### 그룹 저장

저장소 그룹 생성(관리에서는 로 지칭됨) _스토어_). 스토어 그룹은 웹 사이트 간에 정상적으로 배포됩니다.

XML 프로필 노드:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### 보기 저장

저장소 보기를 생성합니다. 스토어 보기는 일반적으로 스토어 그룹 간에 배포됩니다. XML 프로필 노드:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### 세율

세율을 생성합니다. XML 프로필 노드:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## 추가 구성 정보:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml`- 기본 속성 세트

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml`—고객 구성

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml`—제품 전체 설명 구성

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml`—제품 설명 구성

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml`- 제품 요약 및 전체 설명 구성 이 이전 구현은 이전 버전과의 호환성을 위해 제공됩니다.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml`- 짧고 전체 설명에 대한 적은 수의 검색어

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml`- 짧고 전체 설명에 사용할 검색어의 수가 많습니다.
