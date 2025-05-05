---
title: 보고서 구성 우수 사례
description: 보고 모듈 사용하지 않는 경우 제거하여 사이트 성과 최적화합니다.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# 보고서 구성 우수 사례

비즈니스에 보고 또는 동적 고객 세그먼트 기능이 필요하지 않은 경우 보고서 기능을[&#128279;](https://experienceleague.adobe.com/ko/docs/commerce-admin/config/general/reports) 비활성화하여 스토어 실적을 개선하십시오.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) :

- 클라우드 인프라 기반 Adobe Systems Commerce
- Adobe Systems Commerce 온-프레미스

## 보고 비활성화

보고서 또는 동적 고객 세그먼트를 사용하지 않는 경우 보고서 기능을 비활성화하십시오.

1. Admin(관리)에서 Stores(스토어&#x200B;**) >**&#x200B;설정&#x200B;**> Configuration(**&#x200B;컨피그레이션&#x200B;**) > General >** Reports(**일반** 보고서&#x200B;**)로**&#x200B;이동합니다.
1. 일반 옵션(General Options)에서 **보고서 사용(Enable Reports)을 아니요(No &#x200B;***)로*&#x200B;설정합니다&#x200B;**.**
1. System > 도구 > Cache Management(시스템 캐시 관리&#x200B;**) 아래의**&#x200B;관리(Admin)에서 실행 `php bin/magento cache:flush` 하거나 실행하여 캐시를 플러시합니다. **&#x200B;**&#x200B;**&#x200B;**

## 추가 정보

- [Adobe Systems Commerce에서 보고서 생성](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/reporting/reports-menu)
- [고객 동적 세그먼트](https://experienceleague.adobe.com/ko/docs/commerce-admin/customers/segments/customer-segments)
