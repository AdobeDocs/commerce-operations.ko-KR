---
title: 데이터베이스 테이블 수정 우수 사례
description: Adobe Commerce 및 타사 데이터베이스 테이블을 수정하는 방법과 시기를 알아봅니다.
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# 데이터베이스 테이블 수정 우수 사례

이 문서에서는 [!DNL Adobe Commerce] 또는 타사 모듈입니다. 표를 효과적으로 수정하는 시기 및 방법을 이해하면 상거래 플랫폼의 장기적인 생존력과 안정성을 보장하는 데 도움이 됩니다.

마이그레이션 [!DNL Magento 1] 및 기타 전자 상거래 플랫폼 또는 [!DNL Adobe Commerce] 마켓플레이스에서 추가 데이터를 추가 및 저장해야 할 수 있습니다. 첫 번째 본능은 데이터베이스 테이블에 열을 추가하거나 기존 열을 조정하는 것입니다. 하지만 코어만 수정하면 됩니다 [!DNL Adobe Commerce] 제한된 상황에서 테이블(또는 타사 공급업체 테이블)

## Adobe이 수정을 피하는 것을 권장하는 이유

핵심 테이블을 수정하지 않는 주된 이유는 Adobe Commerce에 원시 SQL 쿼리를 포함하는 기본 로직이 포함되어 있기 때문입니다. 표 구조를 변경하면 문제를 해결하기 어려운 예기치 않은 부작용이 발생할 수 있습니다. 또한 DDL(데이터 정의 언어) 작업에 영향을 주어 성능에 예기치 않고 예측할 수 없는 영향을 줄 수 있습니다.

데이터베이스 테이블 구조를 변경하지 않는 또 다른 이유는 핵심 개발 팀이나 타사 개발자가 데이터베이스 테이블의 구조를 변경하는 경우 변경 사항으로 인해 문제가 발생할 수 있기 때문입니다. 예를 들어 다음과 같은 열이 있는 몇 개의 핵심 데이터베이스 테이블이 있습니다 `additional_data`. 이것은 항상 `text` 열 유형. 하지만 성능상의 이유로 핵심 팀이 열을 `longtext`. 이 유형의 열은 JSON에 대한 별칭입니다. 이 열 유형으로 변환하면 해당 열에 성능 향상 및 검색 기능이 추가되며, 이는 `text` 유형. 이 항목에 대한 자세한 내용은 [JSON 데이터 유형](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}.

## 데이터를 저장하거나 제거할 시기 파악

Adobe은 먼저 이 데이터를 저장할지 여부를 결정할 것을 권장합니다. 기존 시스템에서 데이터를 이동하는 경우 제거할 수 있는 모든 데이터는 마이그레이션 중에 시간과 노력을 절약할 수 있습니다. (나중에 액세스해야 하는 경우 데이터를 보관하는 방법이 있습니다.) 애플리케이션과 성능을 잘 관리하려면 추가 데이터 저장 요청에 동의해도 됩니다. 목표는 데이터를 저장하는 것이 다른 방식으로 채워질 수 없는 비즈니스 요구 사항을 충족하기 위한 요구 사항임을 확인하는 것입니다.

### 기존 데이터

프로젝트에 이전 주문이나 고객 레코드와 같은 이전 데이터가 포함되어 있는 경우 대체 조회 방법을 고려해 보십시오. 예를 들어 비즈니스에 가끔씩 참조할 수만 있도록 데이터에 대한 액세스 권한이 필요한 경우 이전 데이터를으로 마이그레이션하는 대신 상거래 플랫폼 외부에서 호스팅된 이전 데이터베이스의 외부 검색을 구현하는 것이 좋습니다 [!DNL Adobe Commerce].

이 경우 데이터베이스를 서버로 마이그레이션해야 하며, 데이터를 읽을 수 있는 웹 인터페이스를 제공하거나 MySQL Workbench 또는 유사한 도구를 사용하는 교육을 제공해야 합니다. 새 데이터베이스에서 이 데이터를 제외하면 개발 팀이 데이터 마이그레이션 문제를 해결하는 대신 새 사이트에 주력할 수 있으므로 마이그레이션이 빠르게 진행됩니다.

데이터를 상거래 외부에 유지하는 것과 관련된 옵션이지만 실시간으로 사용할 수 있는 또 다른 옵션은 GraphQL 메쉬와 같은 다른 도구를 활용하는 것입니다. 이 옵션은 서로 다른 데이터 소스를 결합하고 단일 응답으로 반환합니다.

예를 들어 다음 작업을 수행할 수 있습니다. `stitch` 외부 데이터베이스의 이전 주문, 폐기된 이전 Magento 1 사이트가 함께 제공됩니다. 그런 다음 GraphQL 메쉬를 사용하여 고객 주문 내역의 일부로 표시합니다. 이러한 이전 주문은 현재 주문과 결합할 수 있습니다 [!DNL Adobe Commerce] 환경.

GraphQL과 API 메쉬 사용에 대한 자세한 내용은 [API Mesh란 무엇입니까?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;}) 및 [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}.

## 확장 속성을 사용하여 이전 데이터 마이그레이션

이전 데이터에 마이그레이션이 필요하거나 새 데이터를 저장해야 한다고 결정하는 경우 [!DNL Adobe Commerce], Adobe은 [확장 속성](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}. 확장 속성을 사용하여 추가 데이터를 저장하면 다음과 같은 이점이 있습니다.

- 지속되는 데이터 및 데이터베이스 구조를 제어할 수 있으므로 데이터가 올바른 열 유형 및 적절한 인덱스로 저장되도록 합니다.
- 의 대부분의 엔티티 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 확장 속성 사용을 지원합니다.
- 확장 속성은 프로젝트에 적합한 위치에 데이터를 저장할 수 있는 유연성을 제공하는 스토리지 관련 메커니즘입니다.

두 가지 스토리지 위치 예는 데이터베이스 테이블 및 [!DNL Redis]. 위치를 선택할 때 고려해야 할 주요 사항은 위치가 추가 복잡성을 야기하는지 아니면 성능에 영향을 주는지 입니다.

### 다른 대안을 고려하십시오

개발자로서 외부 도구의 사용을 항상 고려해야 합니다 [!DNL Adobe Commerce] 환경(예: GraphQL mesh 및 Adobe App Builder). 이러한 도구를 사용하면 데이터에 대한 액세스 권한을 유지할 수 있지만 코어 상거래 애플리케이션이나 기본 데이터베이스 테이블에는 영향을 주지 않습니다. 이 접근 방식을 사용하면 API를 통해 데이터를 노출합니다. 그런 다음 App Builder 구성에 데이터 소스를 추가합니다. GraphQL Mesh를 사용하여 이러한 데이터 소스를 결합하고 여기에서 언급한 대로 단일 응답을 생성할 수 있습니다 [이전 데이터](#legacy-data).

GraphQL 메쉬에 대한 자세한 내용은 [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}. 앱 빌더 Adobe에 대한 자세한 내용은 [App Builder 소개](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}.

## 핵심 테이블 또는 타사 테이블 수정

코어를 수정하여 데이터를 저장하기로 결정하는 경우 [!DNL Adobe Commerce] 또는 타사 모듈 데이터베이스 테이블에서 다음 지침을 사용하여 안정성 및 성능에 미치는 영향을 최소화하십시오.

- 새 열만 추가합니다.
- 수정 안 함 _유형_ 기존 열의 값. 예를 들어 `integer` 변환 후 `varchar` 고유한 사용 사례를 충족하기 위해
- EAV 특성 테이블에 열을 추가하지 마십시오. 이 테이블들은 이미 논리와 책임으로 과부하가 되어 있다.
- 테이블을 조정하기 전에 해당 크기를 결정합니다. 큰 테이블을 변경하면 배포에 영향을 주므로 변경 사항이 적용될 때 분 또는 시간이 지연될 수 있습니다.

## 외부 데이터베이스 테이블 수정 우수 사례

Adobe은 코어 데이터베이스 테이블 또는 타사 테이블에 열을 추가할 때 다음 단계를 수행하는 것을 권장합니다.

1. 업데이트할 내용을 나타내는 네임스페이스를 사용하여 모듈을 만듭니다.

   For example: `app/code/YourCompany/Customer`

1. 모듈을 사용할 수 있도록 적절한 파일을 만듭니다( [모듈 만들기](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}.

1. 라는 파일을 만듭니다. `db_schema.xml` 에서 `etc` 폴더를 만들고 적절한 변경 작업을 수행합니다.

   해당하는 경우 을(를) 생성합니다 `db_schema_whitelist.json` 파일. 자세한 내용은 [선언적 스키마](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/)자세한 내용은 {target=&quot;_blank&quot;} 를 참조하십시오.

### 잠재적 영향

외부 데이터베이스에 열을 추가하면 다음과 같은 방법으로 Adobe Commerce 프로젝트에 영향을 줄 수 있습니다.

- 업그레이드는 더 복잡할 수 있습니다.
- 수정되는 테이블이 큰 경우 배포가 영향을 받습니다.
- 새 플랫폼으로 마이그레이션하는 것은 더 복잡할 수 있습니다.

## 핵심 테이블을 수정하지 않는 방법

Adobe Commerce 데이터베이스 테이블을 [확장 속성](#migrate-legacy-data-with-extension-attributes). 다른 대안은 특수 열(`additional_data`)를 몇 개의 핵심 테이블에 추가하여 데이터를 저장하고 JSON 인코딩 형식으로 저장합니다.

### JSON으로 인코딩된 데이터 열에 데이터 저장

일부 핵심 테이블에는 `additional_data` JSON으로 인코딩된 데이터가 있는 열입니다. 이 열은 하나의 필드에 추가 데이터를 매핑하는 기본 방법을 제공합니다. 이 방법을 사용하면 검색 요구 사항 없이 데이터 검색을 위한 정보를 저장하는 간단한 데이터 요소에 대한 테이블을 추가할 수 없습니다. 다음 `additional_data` 열은 일반적으로 품목 레벨에서만 사용할 수 있으며 전체 견적 또는 주문에 대해서는 사용할 수 없습니다.

- 를 사용할 때의 이점 `additional_data` 필드

   - 추가적인 필드가 필요하지 않으므로 열 수가 최소한으로 유지됩니다. 이 기능은 이미 관련된 테이블이 많이 있는 판매 흐름에서 유용합니다. 이미 복잡한 프로세스에 더 많은 복잡성을 추가하지 않는 것이 가장 좋습니다. 이 방법은 많은 사용 사례를 만족하지만 전부는 아닙니다.

- 단점

   - 이 방법은 읽기 전용 데이터를 저장해야만 이상적입니다. 이 문제는 종속성 또는 데이터베이스 관계를 추가하기 위해 개체를 수정하고 빌드하려면 코드에서 직렬화를 취소해야 하기 때문에 발생합니다.

   - 데이터베이스 작업을 사용하여 이러한 필드를 검색하기가 어렵습니다. 이 메서드를 사용하여 검색하는 속도가 느립니다.

   - 에 데이터를 저장할 때 추가 주의가 필요합니다 `additional_data` 열을 사용하지 마십시오. 잘못된 JSON을 만들거나 런타임 중에 읽기 오류가 발생하여 코드를 중단시킬 수 있는 직렬화 또는 직렬화 해제 작업이 트리거되지 않습니다.

   - 이러한 필드는 개발자가 쉽게 찾을 수 있도록 코드에 명확하게 선언해야 합니다.

   - 진단하기 매우 어려울 수 있는 다른 문제입니다. 예를 들어, 사용하지 않는 경우 일부 기본 PHP 함수를 사용합니다 [!DNL Adobe Commerce] 변형된 데이터의 종료 결과는 핵심 애플리케이션에서 제공하는 래퍼 메서드와 예상 형식과 다를 수 있습니다. 저장하거나 검색되는 데이터의 일관성과 예측 가능성을 보장하려면 항상 래퍼 함수를 사용하십시오.

다음은 의 열 및 구조가 있는 표의 예입니다 `additional_data` 열.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

버전 2.4.3, 2.4.4 및 2.4.5에는 열을 갖는 10개의 표가 있습니다 `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
