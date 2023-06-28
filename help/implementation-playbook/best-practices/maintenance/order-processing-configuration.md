---
title: 주문 처리를 위한 구성 모범 사례
description: 체크아웃 및 주문 처리 성능을 개선하기 위한 구성 모범 사례에 대해 알아봅니다.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 주문 처리를 위한 구성 모범 사례

상거래 사이트에서 주문 볼륨이 증가함에 따라 다음 저장소 구성 옵션을 활성화하여 체크아웃 성능 및 주문 처리를 최적화할 수 있습니다.

- **[!UICONTROL Asynchronous indexing]**—이 옵션을 사용하면 많은 수의 주문을 동시에 처리할 때 발생할 수 있는 데이터베이스 잠금 및 처리 속도를 방지할 수 있습니다.
- **[!UICONTROL Asynchronous email notifications]**—이 옵션을 사용하면 이메일 알림을 즉시 전송하는 대신 지정된 간격으로 체크아웃 및 주문 처리를 전송하여 체크아웃 성능을 가속화할 수 있습니다.
- **[!UICONTROL Enable Archiving]**—이 옵션을 사용하면 주문, 송장, 선적 및 대변 메모의 성능을 향상시키고 작업 공간에 불필요한 정보가 없도록 하여 현재 비즈니스에 집중할 수 있습니다. 다음을 참조하십시오 [보관 사용](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 비동기 주문 처리 활성화

비동기 순서 처리를 활성화하는 단계는 배포 모드에 따라 다릅니다.

- 프로덕션 모드의 Adobe Commerce 온 클라우드 인프라 및 온프레미스 사이트의 경우 다음 Magento CLI 명령을 사용하여 비동기 인덱싱을 활성화합니다.

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- 기본 또는 프로덕션 모드의 Adobe Commerce 온-프레미스 사이트의 경우 관리에서 그리드 설정 구성을 업데이트하여 비동기 인덱싱을 활성화합니다.

  다음을 참조하십시오 [예약된 그리드 업데이트 및 리인덱싱 활성화](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >프로덕션 환경을 업데이트하기 전에 항상 스테이징 환경에서 구성 변경 사항을 테스트하십시오.

## 추가 정보

- [구성 모범 사례](../../../performance/configuration.md)
- [일반 및 고급 구성 경로 참조](../../../configuration/reference/config-reference-general.md)
- [높은 처리량 주문 처리](../../../performance/high-throughput-order-processing.md)
