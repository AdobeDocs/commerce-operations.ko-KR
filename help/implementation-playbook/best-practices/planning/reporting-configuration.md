---
title: 보고서 구성에 대한 우수 사례
description: 보고 모듈을 사용하지 않는 경우 보고서 모듈을 제거하여 사이트 성능을 최적화합니다.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 보고서 구성에 대한 우수 사례

비즈니스에 보고 또는 동적 고객 세그먼트 기능이 필요하지 않은 경우 [보고서 기능](https://docs.magento.com/user-guide/configuration/general/reports.html) 저장소 성능을 개선합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 보고 비활성화

보고서 또는 동적 고객 세그먼트를 사용하지 않는 경우 보고서 기능을 비활성화합니다.

1. 책임자에서 다음으로 이동합니다. **스토어** > **설정** > **구성** > **일반** > **보고서**.
1. 아래 **일반 옵션**, 설정됨 **보고서 활성화** 끝 *아니요*.
1. 다음을 실행하여 캐시 초기화 `php bin/magento cache:flush` 또는에서 관리자 **시스템** > **도구** > **캐시 관리**.

## 추가 정보

- [Adobe Commerce에서 보고서 생성](https://docs.magento.com/user-guide/reports.html)
- [고객 다이내믹 세그먼트](https://docs.magento.com/user-guide/marketing/customer-segments.html)
