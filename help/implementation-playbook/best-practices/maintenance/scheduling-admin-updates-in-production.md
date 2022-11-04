---
title: 프로덕션 사이트에서 관리 업데이트 예약
description: Adobe Commerce에 중요한 업데이트를 예약하여 느린 성능 및 정전을 방지하는 우수 사례를 알아봅니다.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# 프로덕션 사이트에서 관리 업데이트를 예약하기 위한 우수 사례

운영 사이트에서 느린 성능 및 정전을 방지하기 위해 Adobe Commerce 사이트에서 중요한 업데이트 및 작업을 피크 시간 동안 예약합니다.

중요한 작업의 예:

- 제품 속성 업데이트나 제품 하위 카테고리를 다른 카테고리로 이동하는 등의 관리자 구성 변경
- 데이터 가져오기 또는 내보내기 작업

중요한 작업으로 인해 캐시 무효화 및 재인덱싱 작업이 발생하여 사이트 중단이 발생할 수 있는 응답 시간이 크게 늘어납니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 추가 정보

- [캐싱 모범 사례](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [비공개 컨텐츠: 개인 콘텐츠 무효화](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [하드웨어 권장 사항: 캐시](../../../performance/hardware.md#caches)
- [고급 설정: Redis 설정](../../../performance/advanced-setup.md#set-up-redis)

