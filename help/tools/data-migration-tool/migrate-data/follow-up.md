---
title: 데이터 마이그레이션 후속 조치
description: Magento 1에서 Magento 2 데이터 마이그레이션이 성공했는지 그리고 모든 기능이 예상대로 작동하는지 확인하는 방법을 알아봅니다.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# 데이터 마이그레이션 후속 조치

Magento 1의 일부 동작 및 논리가 Magento 2에서 다르게 구현되었습니다. 다음 [!DNL Data Migration Tool] 알아서 하세요 몇 가지 마이그레이션 측면이 있으며, 마이그레이션 후 일부 기능이 원활하게 작동하려면 간단한 단계를 수행해야 하는 경우가 있습니다.

## 정보

### 데이터베이스 분할이 지원되지 않음

다음 [!DNL Data Migration Tool] 에서는 분할 데이터베이스를 지원하지 않습니다.

### 계층 가격으로 변환된 그룹 가격

모든 그룹 가격은 마이그레이션 중에 자동으로 계층 가격으로 변환됩니다.

### 판매 엔터티에 대한 새 번호 지정

주문, 송장, 출하, 대변 메모 및 RMA 마이그레이션에 대한 참조 번호. 마이그레이션 후 새 Magento 2 번호 할당 규칙이 적용됩니다. 새 영업 주체의 수가 다릅니다.

## 단계

### 고객 세그먼트 다시 저장 [Adobe Commerce 전용]

마이그레이션 후 고객 세그먼트를 작성하고 실행하려면 관리 패널에서 다시 저장해야 합니다.

### 시간대 구성

이 도구는 시간대 설정을 마이그레이션하지 않으므로 마이그레이션 후 시간대를 수동으로 구성해야 합니다 **스토어** > **구성** > **로케일 옵션** > **표준 시간대**.

기본적으로 Magento은 데이터베이스의 UTC-0 영역에 시간 데이터를 저장하고 현재 시간대 설정에 따라 표시합니다. 시간 데이터가 UTC-0 이외의 영역의 데이터베이스에 이미 저장된 경우 기존 시간을 UTC-0으로 변환해야 합니다 [!DNL Data Migration Tool]s `\Migration\Handler\Timezone` 핸들러.

다음 예에서는 Magento 1이 데이터베이스의 UTC-7 영역에서 시간을 잘못 저장했습니다(예: 잘못된 타사 확장으로 인해). 마이그레이션 시 고객 계정 생성 시간을 UTC-0 영역으로 올바르게 변환하려면 다음 단계를 수행합니다.

1. 를 복사합니다. `map-customer.xml.dist` 구성 파일을 해당 디렉토리의 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)을 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 파일.

1. 업데이트 `<customer_map_file>` 노드 `config.xml` 그리고 제거 `.dist` 확장 프로그램 `map-customer.xml.dist`

1. 다음 규칙을 `map-customer.xml` 파일:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
