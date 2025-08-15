---
title: 데이터 마이그레이션 모범 사례
description: Magento 1에서 Magento 2로 성공적으로 업그레이드하려면 다음 데이터 마이그레이션 모범 사례를 따르십시오.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 데이터 마이그레이션 모범 사례

이 섹션에서는 마이그레이션을 가속화하고 단순화하는 최상의 권장 사항과 소요 시간에 대한 지침을 제공합니다.

* 마이그레이션 테스트를 수행할 때 **Magento 1 인스턴스에서 데이터베이스 복사본을 사용합니다**. Magento 1 스토어 데이터베이스의 프로덕션 인스턴스를 사용하지 마십시오.

* 마이그레이션 전에 Magento 1 데이터베이스에서 **오래된 중복 데이터를 제거합니다**.

이러한 데이터에는 로그, 주문 견적, 최근에 본 제품 또는 비교한 제품, 방문자, 이벤트별 카테고리 및 프로모션 규칙이 포함될 수 있습니다.

* **마이그레이션을 성공적으로 수행하려면 [일반 규칙을 따르십시오](migrate-data/overview.md#migration-overview)**.

* 성능을 향상시키려면 **파일에서 `direct_document_copy`** 옵션을 사용하도록 설정`config.xml`하세요.

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1과 Magento 2 데이터베이스는 모두 동일한 MySQL 서버에 있어야 하며 데이터베이스 계정은 두 데이터베이스에 모두 액세스할 수 있어야 합니다.

## 벤치마킹 예상

Adobe은 다음 시스템에서 데이터 마이그레이션을 테스트했습니다.

* Virtual Box VM, CentOS 6, 2.5GB RAM, CPU 1 코어 2.6GHz
* 177,000개 제품, 355,000개 주문, 214,000개 고객 보유 데이터베이스

## 성능 결과

* 설정 마이그레이션 시간: ~10분
* 데이터 마이그레이션 시간: ~9시간(URL 재작성을 제외한 모든 데이터, 총 데이터의 ~85%)
* 사이트 다운타임 예상: 몇 분 안에 DNS 설정을 다시 인덱싱하고 변경할 수 있습니다. 페이지 캐시를 예열하는 데 필요한 추가 시간입니다.
