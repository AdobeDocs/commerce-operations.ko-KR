---
title: 주문 처리에 대한 구성 우수 사례
description: 체크아웃 및 주문 처리 성능을 개선하기 위한 구성 모범 사례에 대해 배웁니다.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 주문 처리에 대한 구성 우수 사례

상거래 사이트에서 주문 볼륨이 증가하면 다음 저장소 구성 옵션을 활성화하여 체크아웃 성능 및 주문 처리를 최적화할 수 있습니다.

- **[!UICONTROL Asynchronous indexing]**- 많은 수의 주문이 동시에 배치될 때 발생할 수 있는 데이터베이스 잠금 및 느린 처리를 방지하려면 이 옵션을 활성화합니다.
- **[!UICONTROL Asynchronous email notifications]**- 이 옵션을 사용하면 즉시 보내는 대신 지정된 간격으로 체크아웃 및 주문 처리 이메일 알림을 전송하여 체크아웃 성능을 빠르게 향상시킬 수 있습니다.
- **[!UICONTROL Enable Archiving]**—주문을 보관하고 데이터베이스 디스크 공간을 확보하여 주문 처리를 보다 신속하게 하려면 이 옵션을 활성화합니다. 자세한 내용은 [보관 사용](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 비동기 주문 처리 활성화

비동기 주문 처리를 활성화하는 단계는 배포 모드에 따라 다릅니다.

- 프로덕션 모드의 클라우드 인프라 및 온프레미스 사이트에 대한 Adobe Commerce의 경우 다음 Magento CLI 명령을 사용하여 비동기 색인을 활성화합니다.

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- 기본 또는 프로덕션 모드의 Adobe Commerce 온-프레미스 사이트의 경우 관리자에서 그리드 설정 구성을 업데이트하여 비동기 색인 지정을 활성화합니다.

   자세한 내용은 [예약된 그리드 업데이트 및 재인덱싱 사용](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >프로덕션 환경을 업데이트하기 전에 항상 스테이징 환경에서 구성 변경 사항을 테스트합니다.

## 추가 정보

- [구성 우수 사례](../../../performance/configuration.md)
- [일반 및 고급 구성 경로 참조](../../../configuration/reference/config-reference-general.md)
- [높은 처리량 주문 처리](../../../performance/high-throughput-order-processing.md)
