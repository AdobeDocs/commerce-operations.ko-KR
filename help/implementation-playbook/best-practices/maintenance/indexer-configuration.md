---
title: 인덱서에 대한 구성 우수 사례
description: 인덱서 구성에 대한 다음 모범 사례를 통해 사이트 성능을 유지 및 최적화합니다.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 색인 구성에 대한 우수 사례

사이트 성능을 최적화하고 유지 관리하려면 이 문서에 설명된 성능 모범 사례를 사용하여 인덱서 구성을 검토하고 업데이트합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 일정에 따라 업데이트할 인덱서 설정

Adobe Commerce에는 두 가지 유형의 색인 모드가 있습니다. [!UICONTROL Update on Save] (기본 설정) 및 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 모드 는 카탈로그나 다른 데이터가 변경될 때마다 인덱스를 즉시 업데이트합니다. 예를 들어 관리 사용자가 새 제품을 카테고리에 추가하면 업데이트가 저장되면 카테고리 제품 색인이 즉시 다시 색인화됩니다.

- **[!UICONTROL Update on Schedule]** 모드에서는 데이터 업데이트에 대한 정보가 저장되고, 재인덱싱 작업 및 색인 업데이트는 예약된 간격으로 백그라운드에서 실행되는 cron 작업에 의해 관리됩니다.

백엔드에서 작업하거나 가져오기 및 내보내기가 많은 여러 관리자가 있는 대규모 저장소가 있으면 색인 업데이트가 자주 트리거됩니다. 사이트 인덱스 구성이 [!UICONTROL Update on Save] 모드를 자주 재색인화하면 데이터베이스 성능이 저하되어 사이트 성능이 저하되고 재인덱싱 프로세스, 특히 대형 점포에 대해 지연이 오래 발생합니다.

사이트 성능을 최대화하려면 다음 Best Practice를 사용하여 색인을 수행합니다.

- 인덱스 구성을 검토합니다.
- 인덱서를 다음으로 설정 _[!UICONTROL Update on Schedule]_대규모 사이트 및 업데이트 횟수가 많고 트래픽이 많은 사이트의 경우 자세한 내용은 [인덱스 관리](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 팔로우 [성능 모범 사례](../../../performance/configuration.md) 인덱스를 관리합니다.

## 추가 정보

- [관리자 사용자를 위한 색인 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Magento CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [개발자를 위한 색인 지정 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
