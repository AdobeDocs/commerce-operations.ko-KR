---
title: 데이터베이스 테이블 수정 우수 사례
description: Adobe Commerce 및 타사 데이터베이스 테이블을 수정하는 방법과 시기를 알아봅니다.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# 데이터베이스 테이블 수정 우수 사례

이 문서에서는 작성한 데이터베이스 테이블을 수정하는 모범 사례를 제공합니다 [!DNL Adobe Commerce] 또는 서드파티 모듈. 표를 효과적으로 수정하는 시기와 방법을 이해하면 상거래 플랫폼의 장기적인 생존력과 안정성을 확보하는 데 도움이 됩니다.

에서 마이그레이션 [!DNL Magento 1] 및 기타 전자 상거래 플랫폼 또는 [!DNL Adobe Commerce] Marketplace에서 데이터를 추가하고 저장해야 할 수 있습니다. 첫 번째 본능은 데이터베이스 테이블에 열을 추가하거나 기존 열을 조정하는 것입니다. 단, 코어만 수정해야 합니다. [!DNL Adobe Commerce] 제한된 상황의 테이블(또는 타사 공급업체 테이블).

## Adobe이 수정을 피하는 것을 권장하는 이유

핵심 테이블 수정을 피하는 주요 이유는 Adobe Commerce에 원시 SQL 쿼리가 포함된 기본 논리가 포함되어 있기 때문입니다. 표 구조를 변경하면 문제를 해결하기 어려운 예기치 않은 부작용이 발생할 수 있습니다. 또한 DDL(Data Definition Language) 작업을 변경하면 성능에 예기치 않은 예기치 않은 영향을 줄 수 있습니다.

데이터베이스 테이블 구조 변경을 피하는 또 다른 이유는 핵심 개발 팀이나 서드파티 개발자가 데이터베이스 테이블 구조를 변경할 경우 변경 사항으로 인해 문제가 발생할 수 있기 때문입니다. 예를 들어, 라는 열이 있는 몇 개의 코어 데이터베이스 테이블이 있습니다. `additional_data`. 항상 다음과 같은 작업을 수행했습니다. `text` 열 유형. 하지만 성능상의 이유로 핵심 팀은 열을 로 변경할 수 있습니다. `longtext`. 이 유형의 열은 JSON에 대한 별칭입니다. 이 열 유형으로 변환하면 성능 향상과 검색 기능이 해당 열에 추가되며 이 열은 로 존재하지 않습니다. `text` 유형. 다음에서 이 주제에 대해 자세히 읽어볼 수 있습니다. [JSON 데이터 유형](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## 데이터 저장 또는 제거 시점 파악

Adobe은 먼저 이 데이터를 저장해야 하는지 여부를 결정할 것을 권장합니다. 기존 시스템에서 데이터를 이동하는 경우 제거할 수 있는 모든 데이터는 마이그레이션 중에 시간과 노력을 절약합니다. (나중에 액세스해야 하는 경우 데이터를 보관하는 방법이 있습니다.) 애플리케이션 및 성능을 제대로 관리하려면 추가 데이터 저장 요청에 도전해도 됩니다. 목표는 데이터를 저장하는 것이 다른 방법으로 채울 수 없는 비즈니스 요구 사항을 충족하기 위한 요구 사항인지 확인하는 것입니다.

### 이전 데이터

프로젝트에 이전 주문 또는 고객 레코드와 같은 레거시 데이터가 포함되어 있는 경우 대체 조회 방법을 고려해 보십시오. 예를 들어, 비즈니스에서 가끔 참조하기 위해서만 데이터에 액세스해야 하는 경우 이전 데이터를 로 마이그레이션하는 대신 상거래 플랫폼 외부에 호스팅된 이전 데이터베이스의 외부 검색을 구현하는 것이 좋습니다 [!DNL Adobe Commerce].

이 경우 데이터베이스를 서버로 마이그레이션하여 데이터를 읽을 수 있는 웹 인터페이스를 제공하거나 MySQL Workbench 또는 이와 유사한 도구를 사용하여 교육해야 합니다. 새 데이터베이스에서 이 데이터를 제외하면 개발 팀이 데이터 마이그레이션 문제를 해결하는 대신 새 사이트에 집중할 수 있으므로 마이그레이션을 촉진합니다.

데이터를 상거래 외부에 두되 실시간으로 사용할 수 있도록 하는 또 다른 관련 옵션은 GraphQL mesh와 같은 다른 도구를 활용하는 것입니다. 이 옵션은 서로 다른 데이터 소스를 결합하여 단일 응답으로 반환합니다.

예를 들어 다음과 같은 작업을 수행할 수 있습니다 `stitch` 외부 데이터베이스의 이전 주문(폐기된 이전 Magento 1 사이트)을 함께 가져올 수 있습니다. 그런 다음 GraphQL mesh를 사용하여 고객 주문 내역의 일부로 표시합니다. 이러한 이전 주문은 현재 주문과 결합할 수 있습니다 [!DNL Adobe Commerce] 환경.

GraphQL에서 API mesh 사용에 대한 자세한 내용은 을 참조하십시오. [API Mesh란?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## 확장 속성을 사용하여 이전 데이터 마이그레이션

이전 데이터를 마이그레이션해야 하거나 새 데이터를 [!DNL Adobe Commerce], Adobe은 다음을 권장합니다 [확장 속성](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. 확장 속성을 사용하여 추가 데이터를 저장하면 다음과 같은 이점이 있습니다.

- 지속되는 데이터와 데이터베이스 구조를 제어하여 데이터가 올바른 열 유형과 적절한 인덱스로 저장되도록 할 수 있습니다.
- 의 가장 많은 엔티티 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 확장 특성 사용을 지원합니다.
- 확장 속성은 프로젝트의 최적 위치에 데이터를 저장할 수 있는 유연성을 제공하는 스토리지 독립적인 메커니즘입니다.

저장소 위치의 두 가지 예는 데이터베이스 테이블 및 [!DNL Redis]. 위치를 선택할 때 고려해야 할 핵심 사항은 위치가 복잡성을 초래하는지 또는 성능에 영향을 주는지에 대한 것입니다.

### 다른 대안을 고려하십시오.

개발자로서 항상 외부 도구 사용을 고려해야 합니다 [!DNL Adobe Commerce] GraphQL mesh 및 Adobe App Builder 등의 환경 이러한 도구를 사용하면 데이터에 대한 액세스 권한을 유지하는 데 도움이 되지만 핵심 상거래 애플리케이션이나 기본 데이터베이스 테이블에는 영향을 주지 않습니다. 이 접근 방식을 사용하면 API를 통해 데이터를 노출할 수 있습니다. 그런 다음 App Builder 구성에 데이터 소스를 추가합니다. GraphQL Mesh를 사용하면에서 언급한 대로 이러한 데이터 소스를 결합하여 단일 응답을 생성할 수 있습니다 [이전 데이터](#legacy-data).

GraphQL mesh에 대한 자세한 내용은 [GraphQL Mesh 게이트웨이](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## 코어 테이블 또는 서드파티 테이블 수정

코어를 수정하여 데이터를 저장하기로 결정한 경우 [!DNL Adobe Commerce] 또는 타사 모듈 데이터베이스 테이블인 경우 안정성과 성능에 미치는 영향을 최소화하려면 다음 지침을 사용하십시오.

- 새 열만 추가합니다.
- 수정 안 함 _유형_ 기존 열의 값입니다. 예를 들어, `integer` (으)로 `varchar` 고유한 사용 사례를 충족하기 위해
- EAV 속성 테이블에 열을 추가하지 마십시오. 이러한 테이블은 논리와 권한으로 이미 오버로드되어 있습니다.
- 표를 조정하기 전에 표의 크기를 결정합니다. 큰 테이블을 변경하면 배포에 영향을 미치며, 이로 인해 변경 사항이 적용될 때 몇 분 또는 몇 시간이 지연될 수 있습니다.

## 외부 데이터베이스 테이블 수정에 대한 우수 사례

Adobe 코어 데이터베이스 테이블 또는 서드파티 테이블에 열을 추가할 때는 다음 단계를 수행하는 것이 좋습니다.

1. 업데이트 중인 항목을 나타내는 이름으로 네임스페이스에 모듈을 만듭니다.

   예: `app/code/YourCompany/Customer`

1. 모듈을 활성화할 적절한 파일을 만듭니다(참조). [모듈 만들기](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. 라는 파일 만들기 `db_schema.xml` 다음에서 `etc` 폴더를 만들고 적절하게 변경합니다.

   해당하는 경우 다음을 생성합니다. `db_schema_whitelist.json` 파일. 다음을 참조하십시오 [선언적 스키마](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} 추가 정보.

### 잠재적 영향

외부 데이터베이스에 열을 추가하면 다음과 같은 방법으로 Adobe Commerce 프로젝트에 영향을 줄 수 있습니다.

- 업그레이드는 더 복잡할 수 있습니다.
- 수정 중인 테이블이 큰 경우 배포가 영향을 받습니다.
- 새로운 플랫폼으로 마이그레이션하는 작업은 더욱 복잡해질 수 있습니다.

## 핵심 테이블을 수정하지 않는 방법

다음을 사용하여 Adobe Commerce 데이터베이스 테이블을 수정하지 않을 수 있습니다 [확장 속성](#migrate-legacy-data-with-extension-attributes). 또 다른 대안은 특수 열(`additional_data`)를 몇 개의 핵심 테이블에 포함시켜 데이터를 저장하고 JSON 인코딩 형식으로 저장합니다.

### JSON으로 인코딩된 데이터 열에 데이터 저장

일부 코어 테이블에는 `additional_data` json으로 인코딩된 데이터가 있는 열입니다. 이 열은 한 필드에 추가 데이터를 매핑하는 기본 방법을 제공합니다. 이 방법을 사용하면 검색 요구 사항 없이 데이터 검색을 위한 정보를 저장하는 작고 간단한 데이터 요소에 대한 테이블을 추가할 필요가 없습니다. 다음 `additional_data` 열은 일반적으로 전체 견적 또는 주문이 아닌 품목 레벨에서만 사용할 수 있습니다.

- 를 사용할 때의 이점 `additional_data` 필드

   - 추가 필드가 필요하지 않으므로 열 수를 최소화할 수 있습니다. 이는 이미 관련된 테이블이 많은 영업 플로우에서 유용합니다. 이미 복잡한 이 프로세스에 복잡성을 더하지 않는 것이 좋습니다. 이 방법은 많은 사용 사례를 충족하지만 전부는 아닙니다.

- 단점

   - 이 방법은 읽기 전용 데이터를 저장하는 데에만 이상적입니다. 이 문제는 종속성 또는 데이터베이스 관계를 추가하기 위해 개체를 수정하고 빌드하려면 코드를 역직렬화해야 하기 때문에 발생합니다.

   - 데이터베이스 작업을 사용하여 이러한 필드를 검색하는 것은 어렵습니다. 이 메서드로 검색하는 것은 느립니다.

   - 에 데이터를 저장할 때는 특별히 주의해야 합니다. `additional_data` 잘못된 JSON을 생성하거나 런타임 중 읽기 오류가 발생하여 코드를 손상시킬 수 있는 직렬화 또는 역직렬화 작업이 트리거되지 않도록 하는 열입니다.

   - 이러한 필드는 개발자가 쉽게 찾을 수 있도록 코드에 명확하게 선언해야 합니다.

   - 진단하기 매우 어려울 수 있는 기타 문제가 발생할 수 있습니다. 예를 들어 를 사용하지 않는 경우 일부 기본 PHP 함수를 사용합니다. [!DNL Adobe Commerce] 코어 애플리케이션에 의해 제공되는 래퍼 방법들, 변환된 데이터의 최종 결과는 예상 포맷과 상이할 수 있다. 항상 래퍼 함수를 사용하여 저장 또는 검색 중인 데이터의 일관성과 예측 가능성을 확보하십시오.

다음은 의 열과 구조를 갖는 테이블의 예입니다. `additional_data` 열.

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

버전 2.4.3, 2.4.4 및 2.4.5에는 열이 있는 10개의 테이블이 있습니다 `additional_data`.

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
