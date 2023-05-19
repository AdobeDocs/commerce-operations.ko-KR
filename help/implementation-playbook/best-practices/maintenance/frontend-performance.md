---
title: 감사 프론트엔드 성능
description: 웹 성능 도구를 사용하여 Adobe Commerce 상점 운영을 감사함으로써 사이트 성능에 부정적인 영향을 미치는 문제를 식별하고 해결합니다.
role: Admin, User, Developer
feature: Best Practices
feature-set: Commerce
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 프론트엔드 성능에 대한 모범 사례

웹 성능 도구를 사용하여 Adobe Commerce 스토어의 프론트엔드 성능을 확인하십시오.
이러한 도구는 다양한 지표를 사용하여 온라인 스토어의 성능을 향상시킬 수 있는 강력한 통찰력과 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) /:

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 프론트엔드 성능 확인

웹 사이트 스토어의 프론트엔드 성능을 확인하려면:

1. 다음과 같은 웹 성능 도구를 사용하여 프론트엔드 성능 감사:

   - **[Google 등대](https://web.dev/measure/)**—Lighthouse는 성능, 접근성, 프로그레시브 웹 앱, SEO 등에 대한 감사를 제공합니다. 등대를 실행하는 다양한 방법에 대한 자세한 내용은 [등대 개요](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed 인사이트](https://pagespeed.web.dev/)**—PageSpeed Insights는 느린 웹 페이지 성능의 원인에 대한 자세한 보고서와 이를 수정하는 방법에 대한 권장 사항을 신속하게 제공합니다.

1. 감사 보고서를 검토하고 저장소 성능을 개선하기 위해 제공된 권장 사항을 구현합니다.

## 추가 정보

- [관리자 사용자를 위한 색인 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [개발자를 위한 색인화 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
