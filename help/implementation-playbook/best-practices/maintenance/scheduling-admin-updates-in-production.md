---
title: 프로덕션 사이트에 대한 관리자 업데이트 예약
description: 느린 성능 및 중단을 방지하기 위해 Adobe Commerce에 대한 중요한 업데이트를 예약하는 모범 사례에 대해 알아봅니다.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%
---
# 프로덕션 사이트에서 관리 업데이트 예약을 위한 우수 사례

사용량이 적은 시간 동안 Adobe Commerce 사이트에서 중요한 업데이트 및 작업을 예약하여 프로덕션 사이트의 느린 성능 및 중단을 방지합니다.

중요한 작업의 예:

- 제품 속성 업데이트 또는 제품 하위 범주를 다른 범주로 이동과 같은 관리 구성 변경
- 데이터 가져오기 또는 내보내기 작업

중요한 작업을 수행하면 캐시 무효화 및 리인덱싱 작업이 수행되므로 응답 시간이 크게 증가하여 사이트 중단이 발생할 수 있습니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 추가 정보

- [캐싱 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [비공개 콘텐츠: 비공개 콘텐츠 무효화](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [하드웨어 권장 사항: 캐시](../../../performance/hardware.md#caches)
- [고급 설정: Redis 설정](../../../performance/advanced-setup.md#set-up-redis)
