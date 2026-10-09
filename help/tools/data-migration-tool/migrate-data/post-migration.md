---
title: 데이터 마이그레이션 후 단계
description: '[!DNL Data Migration Tool]을(를) 사용하여 Magento 1에서 Magento 2로 데이터를 마이그레이션한 후 수행해야 할 단계를 알아봅니다.'
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%
---
# 데이터 마이그레이션 후 단계

마이그레이션을 완료하고 새 Magento 2 사이트를 철저히 테스트한 후 다음 작업을 수행하십시오.

* Magento 1을 유지 관리 모드로 전환하고 모든 관리 활동을 영구적으로 중지합니다.

* Magento 2 cron 작업 시작

* [모든 Magento 2 캐시 유형 플러시](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [모든 Magento 2 인덱서 다시 인덱싱](../../../configuration/cli/manage-indexers.md#reindex)

* Magento 2 프로덕션 하드웨어를 가리키도록 DNS 및 로드 밸런서를 변경합니다.
