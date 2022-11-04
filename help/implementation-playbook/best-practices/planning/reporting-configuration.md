---
title: 보고서 구성에 대한 우수 사례
description: 사용하지 않는 경우 보고 모듈을 제거하여 사이트 성능을 최적화합니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# 보고서 구성에 대한 우수 사례

비즈니스에 보고 또는 동적 고객 세그먼트 기능이 필요하지 않은 경우, [보고서 기능](https://docs.magento.com/user-guide/configuration/general/reports.html) 저장 성능을 개선합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 보고 비활성화

보고서 또는 동적 고객 세그먼트를 사용하지 않는 경우 보고서 기능을 비활성화합니다.

1. 관리에서 **스토어** > **설정** > **구성** > **일반** > **보고서**.
1. 아래 **일반 옵션**, 설정 **보고서 활성화** to *아니요*.
1. 실행으로 캐시 초기화 `php bin/magento cache:flush` 또는 **시스템** > **도구** > **캐시 관리**.

## 추가 정보

- [Adobe Commerce에서 보고서 생성](https://docs.magento.com/user-guide/reports.html)
- [고객 동적 세그먼트](https://docs.magento.com/user-guide/marketing/customer-segments.html)
