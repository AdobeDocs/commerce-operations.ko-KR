---
title: 인덱서에 대한 구성 모범 사례Configuration best practices for indexers
description: 인덱서 구성에 대한 모범 사례에 따라 사이트 성과 유지 관리 및 최적화Maintain and optimize site performance by following best practices for indexer configuration.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 인덱서 구성에 대한 모범 사례Best practices for indexer configuration

사이트 성과 최적화하고 유지 관리하려면 이 문서에 설명된 성능 모범 사례를 사용하여 인덱서 구성을 검토하고 업데이트합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) :

- 클라우드 인프라 기반 Adobe Systems Commerce
- Adobe Systems Commerce 온-프레미스

## 일정에 따라 업데이트하도록 인덱서 설정Set indexers to update on a schedule

Adobe Systems Commerce에는 및 [!DNL Update on Schedule]라는 두 가지 유형의 인덱서 모드 [!UICONTROL Update on Save] 가 있습니다.

- **[!UICONTROL Update on Save]** mode는 카탈로그 또는 기타 데이터가 변경될 때마다 색인을 즉시 업데이트합니다. 예를 들어 관리자 사용자 사용자가 범주에 새 제품을 추가하는 경우 범주 제품 인덱스는 업데이트가 저장되는 즉시 다시 인덱싱됩니다.

- **[!UICONTROL Update on Schedule]** 모드는 데이터 업데이트에 대한 정보를 저장하고, 리인덱싱 작업과 인덱스 업데이트는 백그라운드에서 예약된 간격으로 실행되는 cron 작업에 의해 관리됩니다. cron 작업이 실행될 때마다 항상 색인 재지정을 수행하는 것은 아닙니다. 인덱서 변경 로그에 새 항목이 있는 경우에만 다시 인덱싱합니다(예: 인덱서에 백로그가 있음).

백엔드에서 여러 관리자가 작업하는 대규모 스토어 또는 많은 가져오기 및 내보내기가 있으면 인덱스가 자주 업데이트됩니다. 사이트 인덱스 구성이 모드로 설정된 [!UICONTROL Update on Save] 경우 잦은 재인덱싱으로 인해 데이터베이스 성능이 저하되어 사이트 성과 저하가 발생하고 특히 대규모 매장의 경우 재인덱싱 프로세스가 오래 지연됩니다.

사이트 성과를 최대화하려면 다음 색인화 우수 사례를 팔로우 따르십시오.

- 인덱스 구성을 검토합니다.
- 인덱서를 _[!UICONTROL Update on Schedule]_&#x200B;대규모 사이트 및 업데이트가 빈번하고 트래픽 트래픽이 많은 사이트에 대해 설정합니다. Index Management[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode)를 참조하십시오.
- 인덱스 관리에 대한 성능 우수 사례를[&#128279;](../../../performance/configuration.md) 따르십시오.

>[!IMPORTANT]
>
>옵션을 [!DNL Customer Grid] 사용해서 [!UICONTROL Update on Save] 만 다시 색인화할 수 있습니다. 이 인덱스는 `Update by Schedule` 옵션을 지원하지 않습니다.

## 추가 정보

- [관리 사용자를 위한 Index 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Magento CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [개발자를 위한 인덱싱 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
