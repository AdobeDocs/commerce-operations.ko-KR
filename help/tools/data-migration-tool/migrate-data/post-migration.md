---
title: 데이터 후 마이그레이션 단계
description: 를 사용한 후 수행할 단계를 알아봅니다. [!DNL Data Migration Tool] Magento 1에서 Magento 2으로 데이터를 마이그레이션하려면 다음을 수행하십시오.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# 데이터 후 마이그레이션 단계

마이그레이션을 완료하고 새 Magento 2 사이트를 철저히 테스트한 후 다음 작업을 수행하십시오.

* Magento 1을 유지 관리 모드로 전환하고 모두 영구적으로 정지 [관리](https://glossary.magento.com/admin) 활동

* Magento 2 cron 작업 시작

* [모든 Magento 2 캐시 유형 초기화](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [모든 Magento 2 인덱서 다시 색인화](../../../configuration/cli/manage-indexers.md#reindex)

* Magento 2 프로덕션 하드웨어를 가리키도록 DNS 및 로드 밸런서를 변경합니다.
