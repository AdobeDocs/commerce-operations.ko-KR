---
title: 인덱서에 대한 구성 모범 사례
description: 인덱서 구성에 대한 모범 사례를 따라 사이트 성능을 유지 및 최적화합니다.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 인덱서 구성에 대한 우수 사례

사이트 성능을 최적화 및 유지 관리하려면 이 문서에 설명된 성능 모범 사례를 사용하여 인덱서 구성을 검토하고 업데이트합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 일정에 따라 업데이트할 인덱서 설정

Adobe Commerce에는 두 가지 유형의 인덱서 모드가 있습니다. [!UICONTROL Update on Save] (기본 설정) 및 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 모드는 카탈로그나 다른 데이터가 변경될 때마다 인덱스를 즉시 업데이트합니다. 예를 들어 관리자 사용자가 카테고리에 새 제품을 추가하면 업데이트가 저장될 때 카테고리 제품 인덱스가 즉시 다시 인덱싱됩니다.

- **[!UICONTROL Update on Schedule]** 모드는 데이터 업데이트에 대한 정보를 저장하고, 리인덱싱 작업 및 인덱스 업데이트는 백그라운드에서 예약된 간격으로 실행되는 cron 작업에 의해 관리됩니다. cron 작업이 실행될 때마다 색인 재지정을 수행하는 것은 아닙니다. 인덱서 변경 로그에 새 항목이 있는 경우에만 다시 인덱싱합니다(예: 인덱서에 백로그가 있는 경우).

백엔드에서 작업하거나 많은 가져오기 및 내보내기를 수행하는 여러 관리자가 있는 큰 저장소가 있으면 빈번한 색인 업데이트가 트리거됩니다. 사이트 인덱스 구성이 로 설정된 경우 [!UICONTROL Update on Save] 모드를 자주 리인덱싱하면 데이터베이스 성능이 저하되어 사이트 성능이 저하되고 특히 대규모 스토어의 경우 리인덱싱 프로세스가 오래 지연됩니다.

사이트 성능을 극대화하려면 색인화에 대한 다음 모범 사례를 따르십시오.

- 색인 구성을 검토합니다.
- 인덱서를 다음으로 설정 _[!UICONTROL Update on Schedule]_대규모 사이트 및 자주 업데이트되고 트래픽이 많은 사이트의 경우. 다음을 참조하십시오 [색인 관리](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 팔로우 [성능 모범 사례](../../../performance/configuration.md) 색인 관리용.

>[!IMPORTANT]
>
>다음 [!DNL Customer Grid] 를 사용해야만 다시 인덱싱할 수 있습니다. [!UICONTROL Update on Save] 옵션을 선택합니다. 이 인덱스는 다음을 지원하지 않습니다. `Update by Schedule` 옵션을 선택합니다.

## 추가 정보

- [관리자 사용자를 위한 색인 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Magento CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [개발자를 위한 색인화 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
