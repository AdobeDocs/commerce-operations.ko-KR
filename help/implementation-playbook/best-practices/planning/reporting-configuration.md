---
title: 보고서 구성에 대한 우수 사례
description: 보고 모듈을 사용하지 않는 경우 보고서 모듈을 제거하여 사이트 성능을 최적화합니다.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# 보고서 구성에 대한 우수 사례

비즈니스에 보고 또는 동적 고객 세그먼트 기능이 필요하지 않은 경우 [보고서 기능](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports)을 비활성화하여 스토어 성능을 개선하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 보고 비활성화

보고서 또는 동적 고객 세그먼트를 사용하지 않는 경우 보고서 기능을 비활성화합니다.

1. 책임자에서 **스토어** > **설정** > **구성** > **일반** > **보고서**&#x200B;로 이동합니다.
1. **일반 옵션**&#x200B;에서 **보고서 사용**&#x200B;을(를) *아니요*(으)로 설정합니다.
1. `php bin/magento cache:flush`을(를) 실행하거나 **시스템** > **도구** > **캐시 관리**&#x200B;의 관리자에서 캐시를 플러시합니다.

## 추가 정보

- [Adobe Commerce에서 보고서 생성](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [고객 동적 세그먼트](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
