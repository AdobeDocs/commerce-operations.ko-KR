---
title: 데이터 마이그레이션 작동 방식
description: 용어, 워크플로 다이어그램, 단계를 포함하여 Magento 1과 Magento 2 간의 데이터 마이그레이션 프로세스에 대해 알아봅니다.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# 데이터 마이그레이션 작동 방식

이 항목에서는 를 사용하여 데이터를 Magento 1에서 Magento 2로 마이그레이션하는 방법에 대한 높은 수준의 개요를 제공합니다 [!DNL Data Migration Tool].

다음 [!DNL Data Migration Tool] 는 Magento 1에서 Magento 2로 데이터를 전송하는 데 사용되는 CLI(Command-Line Interface) 툴입니다. 이 도구는 Magento 1과 2 데이터베이스 구조(테이블 및 필드) 간의 일관성을 확인하고, 데이터 전송 진행률을 추적하고, 로그를 만들고, 데이터 확인 테스트를 실행합니다.

## 용어

* **모드** - Magento 1.x에서 Magento 2.x로 데이터를 마이그레이션하는 순서가 지정된 작업 세트입니다.
* **단계** - 마이그레이션할 데이터 종류를 정의하는 모드의 작업.
* **단계** - 데이터를 확인, 전송 및 확인하는 단계 작업
* **맵 파일** - 단계를 완료하기 위해 Magento 1.x와 Magento 2.x 데이터 구조 간의 규칙과 연결을 정의하는 XML 파일입니다.

## 모드

다음 [!DNL Data Migration Tool] 마이그레이션 프로세스를 세 단계로 나누거나 *모드* Magento 1.x에서 Magento 2.x로 데이터를 전송하고 조정하기 위해 세 가지 모드가 여기에 나열되며 다음 순서로 실행되어야 합니다.

1. **설정 모드**: 시스템 구성 및 웹 사이트 관련 설정을 마이그레이션합니다.
1. **데이터 모드**: 데이터베이스 자산을 일괄적으로 마이그레이션합니다.
1. **델타 모드**: 새 고객 및 주문과 같은 증분 변경 사항(마지막 실행 이후의 변경 사항)을 마이그레이션합니다.

![마이그레이션 모드](../../assets/data-migration/MigrationModes2.png)

## 단계

다음 [!DNL Data Migration Tool] 다음 목록을 사용합니다. *단계* 특정 유형의 데이터를 마이그레이션하기 위해 각 모드 내에서. 예를 들어 설정 모드에서는 모든 설정 데이터를 마이그레이션하는 데 사용되는 두 가지 단계인 저장 단계와 설정 단계가 있습니다. 이러한 각 단계(및 다른 모드의 단계)에서 마이그레이션되는 특정 데이터에 대한 자세한 내용은 [[!DNL Data Migration Tool] 기술 사양](technical-specification.md).

![마이그레이션 개요](../../assets/data-migration/MigrationOverview2.png)

## 단계

각 단계 내에는 3개가 있습니다 *단계* 는 데이터가 올바르게 마이그레이션되도록 항상 다음 순서로 실행됩니다.

1. **무결성 검사**: 테이블 필드 이름, 유형 및 기타 정보를 비교하여 Magento 1과 2 데이터 구조 간의 호환성을 확인합니다.
1. **데이터 전송**: Magento 1과 2의 데이터 테이블을 테이블별로 전송합니다.
1. **볼륨 검사**: 테이블 간 레코드 수를 비교하여 전송이 성공했는지 확인합니다.

![마이그레이션 단계](../../assets/data-migration/MigrationSteps2.png)

## 맵 파일

마이그레이션 프로세스의 가장 낮은 수준에는 XML이 있습니다 *맵 파일*. 다음 [!DNL Data Migration Tool] 는 단계의 단계에서 맵 파일을 사용하여 Magento 1.x와 2.x 테이블 간에 서로 다른 데이터 구조를 변환합니다.

예를 들어, Magento Open Source 1.8.0.0 데이터베이스에서 Magento Open Source 2.x.x로 데이터를 변환할 때 맵 파일은 테이블의 이름이 변경된 사실을 설명하고 대상 데이터베이스에서 적절하게 이름을 바꿉니다. 데이터 구조나 데이터 형식에 차이가 없으면 [!DNL Data Migration Tool] 는 확장에 의해 생성된 테이블의 데이터를 포함하여 현재 상태 그대로 Magento 2 데이터베이스로 전송합니다.

맵 파일에서 차이가 선언되지 않으면 [!DNL Data Migration Tool] 오류를 표시하고 시작되지 않습니다.

매핑 파일에 대해서는 다음에서 자세히 설명합니다.[!DNL Data Migration Tool] 기술 사양].

## 마이그레이션 흐름 다이어그램

![마이그레이션 흐름](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 기술 사양](technical-specification.md)

세계 #1 상거래 플랫폼(Magento 1.x)에서 미래의 플랫폼(Magento 2)으로 전환하는 것을 고려하게 되어 기쁘게 생각합니다. 우리는 이 프로세스에 대한 세부 사항을 공유하게 되어 매우 기쁩니다. 이 프로세스를 마이그레이션 이라고 합니다.

## 마이그레이션 구성 요소

Magento 2 마이그레이션에는 데이터, 확장 및 사용자 지정 코드, 테마, 맞춤화의 네 가지 구성 요소가 포함됩니다.

### 데이터

다음을 개발했습니다. **MAGENTO 2[!DNL Data Migration Tool]** 모든 제품, 고객 및 주문 데이터, 스토어 구성, 프로모션 등을 Magento 2로 효율적으로 이동하는 데 도움이 됩니다. 이 안내서에서는 데이터를 마이그레이션하는 데 사용하는 도구와 모범 사례에 대한 정보를 제공합니다.

### 확장 및 사용자 지정 코드

Magento 2에서 Magento 1 확장을 사용할 수 있도록 개발 커뮤니티와 열심히 협력해 왔습니다. 이제 다음을 발표하게 되어 기쁩니다. [Commerce Marketplace](https://marketplace.magento.com/)를 사용하여 즐겨 찾는 확장의 최신 버전을 다운로드하거나 구매할 수 있습니다.

Magento 2용 확장 개발에 대한 자세한 내용은 [PHP 개발자 안내서](https://developer.adobe.com/commerce/php/development/).

### 테마 및 사용자 지정

Magento 2는 상인들에게 혁신적인 쇼핑 경험을 만들고 새로운 수준으로 확장할 수 있는 탁월한 능력을 제공하는 새로운 접근 방식과 기술을 사용합니다. 이러한 발전을 활용하려면 개발자는 테마와 사용자 정의를 변경해야 합니다. 설명서는 Magento 2를 만드는 데 온라인으로 사용할 수 있습니다 [테마](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [레이아웃](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), 및 [사용자 정의](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## 마이그레이션 작업

1.x 버전(예: v1.12에서 v1.14로) 간의 업그레이드처럼, Magento 1에서 Magento 2로 마이그레이션하기 위한 작업 수준은 사이트를 빌드한 방법과 사용자 지정 수준에 따라 다릅니다.
그러나 지속적으로 을 개선하고 있습니다. [!DNL Data Migration Tool] (다음을 참조하십시오. [변경 로그](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) 추가 세부 정보). 따라서 마이그레이션 노력이 지속적으로 감소하고 있습니다.
