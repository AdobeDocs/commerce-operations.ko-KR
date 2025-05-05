---
title: 데이터베이스 테이블 수정 우수 사례
description: Adobe Commerce 및 타사 데이터베이스 테이블을 수정하는 방법과 시기를 알아봅니다.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# 데이터베이스 테이블 수정 우수 사례

이 문서에서는 [!DNL Adobe Commerce] 또는 타사 모듈에서 만든 데이터베이스 테이블을 수정하는 모범 사례를 제공합니다. 표를 효과적으로 수정하는 시기와 방법을 이해하면 상거래 플랫폼의 장기적인 생존력과 안정성을 확보하는 데 도움이 됩니다.

[!DNL Magento 1] 및 기타 전자 상거래 플랫폼에서 마이그레이션하거나 [!DNL Adobe Commerce] 마켓플레이스에서 모듈로 작업하려면 추가 데이터를 추가하고 저장해야 할 수 있습니다. 첫 번째 본능은 데이터베이스 테이블에 열을 추가하거나 기존 열을 조정하는 것입니다. 그러나 제한된 상황에서는 코어 [!DNL Adobe Commerce] 테이블(또는 타사 공급업체 테이블)만 수정해야 합니다.

## Adobe이 수정을 피하는 것을 권장하는 이유

핵심 테이블 수정을 피하는 주요 이유는 Adobe Commerce에 원시 SQL 쿼리가 포함된 기본 논리가 포함되어 있기 때문입니다. 표 구조를 변경하면 문제를 해결하기 어려운 예기치 않은 부작용이 발생할 수 있습니다. 또한 DDL(Data Definition Language) 작업을 변경하면 성능에 예기치 않은 예기치 않은 영향을 줄 수 있습니다.

데이터베이스 테이블 구조 변경을 피하는 또 다른 이유는 핵심 개발 팀이나 서드파티 개발자가 데이터베이스 테이블 구조를 변경할 경우 변경 사항으로 인해 문제가 발생할 수 있기 때문입니다. 예를 들어, 이름이 `additional_data`인 열이 있는 몇 가지 핵심 데이터베이스 테이블이 있습니다. 이 형식은 항상 `text` 열 형식입니다. 하지만 성능상의 이유로 핵심 팀이 열을 `longtext`(으)로 변경할 수 있습니다. 이 유형의 열은 JSON에 대한 별칭입니다. 이 열 유형으로 전환하면 해당 열에 성능 향상과 검색 기능이 추가되며 `text` 유형으로 존재하지 않습니다. [JSON 데이터 형식](https://mariadb.com/kb/en/json-data-type/){target="_blank"}에서 이 주제에 대한 자세한 내용을 읽을 수 있습니다.

## 데이터 저장 또는 제거 시점 파악

Adobe은 먼저 이 데이터를 저장해야 하는지 여부를 결정할 것을 권장합니다. 기존 시스템에서 데이터를 이동하는 경우 제거할 수 있는 모든 데이터는 마이그레이션 중에 시간과 노력을 절약합니다. (나중에 액세스해야 하는 경우 데이터를 보관하는 방법이 있습니다.) 애플리케이션 및 성능을 제대로 관리하려면 추가 데이터 저장 요청에 도전해도 됩니다. 목표는 데이터를 저장하는 것이 다른 방법으로 채울 수 없는 비즈니스 요구 사항을 충족하기 위한 요구 사항인지 확인하는 것입니다.

### 이전 데이터

프로젝트에 이전 주문 또는 고객 레코드와 같은 레거시 데이터가 포함되어 있는 경우 대체 조회 방법을 고려해 보십시오. 예를 들어, 비즈니스에서 가끔 참조하기 위해서만 데이터에 액세스해야 하는 경우 이전 데이터를 [!DNL Adobe Commerce] (으)로 마이그레이션하는 대신 상거래 플랫폼 외부에서 호스팅되는 이전 데이터베이스의 외부 검색을 구현하는 것이 좋습니다.

이 경우 데이터베이스를 서버로 마이그레이션하여 데이터를 읽을 수 있는 웹 인터페이스를 제공하거나 MySQL Workbench 또는 이와 유사한 도구를 사용하여 교육해야 합니다. 새 데이터베이스에서 이 데이터를 제외하면 개발 팀이 데이터 마이그레이션 문제를 해결하는 대신 새 사이트에 집중할 수 있으므로 마이그레이션을 촉진합니다.

데이터를 상거래 외부에 두되 실시간으로 사용할 수 있도록 하는 또 다른 관련 옵션은 GraphQL mesh와 같은 다른 도구를 활용하는 것입니다. 이 옵션은 서로 다른 데이터 소스를 결합하여 단일 응답으로 반환합니다.

예를 들어, 외부 데이터베이스의 이전 주문(사용 중지된 이전 Magento 1 사이트)을 함께 `stitch`할 수 있습니다. 그런 다음 GraphQL mesh를 사용하여 고객 주문 내역의 일부로 표시합니다. 이러한 이전 주문은 현재 [!DNL Adobe Commerce] 환경의 주문과 결합할 수 있습니다.

GraphQL에서 API Mesh를 사용하는 방법에 대한 자세한 내용은 [API Mesh란 무엇입니까](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) 및 [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}를 참조하십시오.

## 확장 속성을 사용하여 이전 데이터 마이그레이션

Adobe 이전 데이터를 마이그레이션해야 하거나 새 데이터를 [!DNL Adobe Commerce]에 저장해야 하는 경우 [확장 특성](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}을 사용하는 것이 좋습니다. 확장 속성을 사용하여 추가 데이터를 저장하면 다음과 같은 이점이 있습니다.

- 지속되는 데이터와 데이터베이스 구조를 제어하여 데이터가 올바른 열 유형과 적절한 인덱스로 저장되도록 할 수 있습니다.
- [!DNL Adobe Commerce]에 있는 대부분의 엔터티는 확장 특성 사용을 지원합니다.
- 확장 속성은 프로젝트의 최적 위치에 데이터를 저장할 수 있는 유연성을 제공하는 스토리지 독립적인 메커니즘입니다.

저장소 위치의 두 가지 예는 데이터베이스 테이블과 [!DNL Redis]입니다. 위치를 선택할 때 고려해야 할 핵심 사항은 위치가 복잡성을 초래하는지 또는 성능에 영향을 주는지에 대한 것입니다.

### 다른 대안을 고려하십시오.

개발자로서 [!DNL Adobe Commerce] 환경 외부의 도구(예: GraphQL mesh 및 Adobe App Builder)를 사용하는 것을 항상 고려해야 합니다. 이러한 도구를 사용하면 데이터에 대한 액세스 권한을 유지하는 데 도움이 되지만 핵심 상거래 애플리케이션이나 기본 데이터베이스 테이블에는 영향을 주지 않습니다. 이 접근 방식을 사용하면 API를 통해 데이터를 노출할 수 있습니다. 그런 다음 App Builder 구성에 데이터 소스를 추가합니다. GraphQL Mesh를 사용하면 이러한 데이터 소스를 결합하여 [기존 데이터](#legacy-data)에 언급된 대로 단일 응답을 생성할 수 있습니다.

GraphQL Mesh에 대한 자세한 내용은 [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}를 참조하십시오. Adobe App Builder에 대한 자세한 내용은 [App Builder 소개](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}를 참조하십시오.

## 코어 테이블 또는 서드파티 테이블 수정

코어 [!DNL Adobe Commerce] 또는 타사 모듈 데이터베이스 테이블을 수정하여 데이터를 저장하기로 결정한 경우 다음 지침을 사용하여 안정성 및 성능에 미치는 영향을 최소화하십시오.

- 새 열만 추가합니다.
- 기존 열의 _type_ 값은 수정하지 마십시오. 예를 들어 고유한 사용 사례를 충족하도록 `integer`을(를) `varchar`(으)로 변경하지 마십시오.
- EAV 속성 테이블에 열을 추가하지 마십시오. 이러한 테이블은 논리와 권한으로 이미 오버로드되어 있습니다.
- 표를 조정하기 전에 표의 크기를 결정합니다. 큰 테이블을 변경하면 배포에 영향을 미치며, 이로 인해 변경 사항이 적용될 때 몇 분 또는 몇 시간이 지연될 수 있습니다.

## 외부 데이터베이스 테이블 수정에 대한 우수 사례

Adobe 코어 데이터베이스 테이블 또는 서드파티 테이블에 열을 추가할 때는 다음 단계를 수행하는 것이 좋습니다.

1. 업데이트 중인 항목을 나타내는 이름으로 네임스페이스에 모듈을 만듭니다.

   예: `app/code/YourCompany/Customer`

1. 모듈을 사용할 수 있는 파일을 만드십시오([모듈 만들기](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"} 참조).

1. `etc` 폴더에 `db_schema.xml` 파일을 만들고 적절하게 변경합니다.

   해당하는 경우 `db_schema_whitelist.json` 파일을 생성합니다. 자세한 내용은 [선언 스키마](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"}를 참조하십시오.

### 잠재적 영향

외부 데이터베이스에 열을 추가하면 다음과 같은 방법으로 Adobe Commerce 프로젝트에 영향을 줄 수 있습니다.

- 업그레이드는 더 복잡할 수 있습니다.
- 수정 중인 테이블이 큰 경우 배포가 영향을 받습니다.
- 새로운 플랫폼으로 마이그레이션하는 작업은 더욱 복잡해질 수 있습니다.

## 핵심 테이블을 수정하지 않는 방법

[확장 특성](#migrate-legacy-data-with-extension-attributes)을 사용하여 Adobe Commerce 데이터베이스 테이블을 수정하지 않아도 됩니다. 또 다른 방법은 몇 개의 핵심 테이블에 있는 특수 열(`additional_data`)을 사용하여 데이터를 저장하고 JSON 인코딩 형식으로 저장하는 것입니다.

### JSON으로 인코딩된 데이터 열에 데이터 저장

일부 코어 테이블에는 JSON 인코딩 데이터를 포함하는 `additional_data` 열이 있습니다. 이 열은 한 필드에 추가 데이터를 매핑하는 기본 방법을 제공합니다. 이 방법을 사용하면 검색 요구 사항 없이 데이터 검색을 위한 정보를 저장하는 작고 간단한 데이터 요소에 대한 테이블을 추가할 필요가 없습니다. `additional_data` 열은 일반적으로 전체 견적 또는 주문에 사용할 수 없고 항목 수준에서만 사용할 수 있습니다.

- `additional_data` 필드 사용의 이점

   - 추가 필드가 필요하지 않으므로 열 수를 최소화할 수 있습니다. 이는 이미 관련된 테이블이 많은 영업 플로우에서 유용합니다. 이미 복잡한 이 프로세스에 복잡성을 더하지 않는 것이 좋습니다. 이 방법은 많은 사용 사례를 충족하지만 전부는 아닙니다.

- 단점

   - 이 방법은 읽기 전용 데이터를 저장하는 데에만 이상적입니다. 이 문제는 종속성 또는 데이터베이스 관계를 추가하기 위해 개체를 수정하고 빌드하려면 코드를 역직렬화해야 하기 때문에 발생합니다.

   - 데이터베이스 작업을 사용하여 이러한 필드를 검색하는 것은 어렵습니다. 이 메서드로 검색하는 것은 느립니다.

   - `additional_data` 열에 데이터를 저장할 때 잘못된 JSON을 만들거나 런타임 중 읽기 오류를 발생시켜 코드를 손상시킬 수 있는 직렬화 또는 역직렬화 작업이 트리거되지 않도록 특별히 주의해야 합니다.

   - 이러한 필드는 개발자가 쉽게 찾을 수 있도록 코드에 명확하게 선언해야 합니다.

   - 진단하기 매우 어려울 수 있는 기타 문제가 발생할 수 있습니다. 예를들어, 일부 네이티브 PHP 함수에서는 코어 응용 프로그램에서 제공하는 [!DNL Adobe Commerce] 래퍼 메서드를 사용하지 않으면 변환된 데이터의 최종 결과가 예상한 형식과 다를 수 있습니다. 항상 래퍼 함수를 사용하여 저장 또는 검색 중인 데이터의 일관성과 예측 가능성을 확보하십시오.

다음은 `additional_data` 열에 대한 열 및 구조가 있는 테이블의 예입니다.

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

버전 2.4.3, 2.4.4 및 2.4.5에는 열 `additional_data`이(가) 있는 10개의 테이블이 있습니다.

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
