---
title: 'ACSD-66404: [!DNL Galera Cluster] 트랜잭션 크기 제한으로 인해 Cron 작업에서 변경 로그 테이블을 지우지 못했습니다.'
description: ACSD-66404 패치를 적용하여 cron 작업에서 변경 로그 테이블을 지우지 않고 이러한 테이블에 많은 양의 데이터가 있는 경우 [!DNL Galera Cluster] 문제가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: d7ad3b11-aee6-4a26-8892-369fbfe6932e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '382'
ht-degree: 0%
---
# ACSD-66404: [!DNL Galera Cluster] 트랜잭션 크기 제한으로 인해 Cron 작업에서 변경 로그 테이블을 지우지 못했습니다.

ACSD-66404 패치는 cron 작업이 변경 로그 테이블을 지우지 못해 많은 양의 데이터를 처리할 때 [!DNL Galera Cluster] 문제를 발생시키는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-66404입니다. 이 문제는 Adobe Commerce 2.4.9에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p6, 2.4.7-p6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Cron 작업에서 변경 로그 테이블을 지우지 않고 해당 테이블에 많은 양의 데이터가 있는 경우 [!DNL Galera Cluster] 문제가 발생합니다.

<u>재현 단계</u>:

1. 성능 프로필을 사용하여 많은 제품을 생성합니다.
1. `inventory_cl` DB 테이블에 많은 항목이 있도록 시스템의 모든 제품에 대해 대량 업데이트를 수행합니다.
1. `indexer_clean_all_changelogs` cron 작업을 실행합니다.

<u>예상 결과</u>:

`indexer_clean_all_changelogs` cron 작업에서 [!DNL Galera Cluster] 문제를 일으키지 않고 여러 삭제 쿼리의 큰 변경 로그(10GB 이상)에 대한 변경 로그 정리를 수행할 수 있습니다.

<u>실제 결과</u>:

`indexer_clean_all_changelogs` cron 작업은 단일 삭제 쿼리에서 큰 변경 로그(10GB 이상)에 대한 변경 로그 정리를 수행하여 [!DNL Galera Cluster] 문제를 일으킵니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
