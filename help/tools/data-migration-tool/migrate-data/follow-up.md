---
title: 데이터 마이그레이션 후속 조치
description: Magento 1에서 Magento 2로 데이터 마이그레이션이 성공적이었는지와 모든 기능이 예상대로 작동하는지 확인하는 방법을 알아봅니다.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 데이터 마이그레이션 후속 조치

Magento 1의 일부 동작 및 논리가 Magento 2에서 다르게 구현되었습니다. [!DNL Data Migration Tool]이(가) 처리합니다. 알아야 할 마이그레이션 측면이 있으며, 경우에 따라 마이그레이션 후 일부 기능이 원활하게 작동하도록 사소한 단계를 수행해야 합니다.

## 정보

### 데이터베이스 분할이 지원되지 않음

[!DNL Data Migration Tool]은(는) 분할 데이터베이스를 지원하지 않습니다.

### 그룹 가격이 계층 가격으로 전환됨

모든 그룹 가격은 마이그레이션 중에 자동으로 계층 가격으로 전환됩니다.

### 영업 엔티티에 대한 새 번호 지정

주문, 송장, 선적, 대변 메모 및 RMA 이전과 관련된 참조 번호. 마이그레이션 후에는 새로운 Magento 2 번호 할당 규칙이 적용됩니다. 새 판매 개체에 대한 숫자가 다릅니다.

## 단계

### 고객 세그먼트 다시 저장 [Adobe Commerce 전용]

마이그레이션 후 고객 세그먼트를 시작하고 실행하려면 관리자 패널에서 다시 저장해야 합니다.

### 표준 시간대 구성

이 도구는 시간대 설정을 마이그레이션하지 않으므로 마이그레이션 후 **스토어** > **구성** > **로케일 옵션** > **시간대**&#x200B;에서 시간대를 수동으로 구성해야 합니다.

기본적으로 Magento은 데이터베이스의 UTC-0 영역에 시간 데이터를 저장하고 현재 시간대 설정에 따라 표시합니다. 시간 데이터가 이미 UTC-0 이외의 영역에 있는 데이터베이스에 저장된 경우 [!DNL Data Migration Tool]의 `\Migration\Handler\Timezone` 처리기를 사용하여 기존 시간을 UTC-0으로 변환해야 합니다.

다음 예에서는 Magento 1이 데이터베이스의 UTC-7 영역에서 시간을 잘못 절약했습니다(예: 잘못된 타사 확장 때문에). 마이그레이션 시 고객 계정 생성 시간을 UTC-0 영역으로 올바르게 변환하려면 다음 단계를 수행합니다.

1. `map-customer.xml.dist` 구성 파일을 [!DNL Data Migration Tool]&#x200B;(`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)의 적절한 디렉터리에서 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 파일로 복사합니다.

1. `<customer_map_file>`에서 `config.xml` 노드를 업데이트하고 `.dist`에서 `map-customer.xml.dist` 확장을 제거하십시오.

1. `map-customer.xml` 파일에 다음 규칙을 추가합니다.

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
