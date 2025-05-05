---
title: 감사 프론트엔드 성능
description: 웹 성능 도구를 사용하여 Adobe Commerce 상점 운영을 감사함으로써 사이트 성능에 부정적인 영향을 미치는 문제를 식별하고 해결합니다.
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---

# 프론트엔드 성능에 대한 모범 사례

웹 성능 도구를 사용하여 Adobe Commerce 스토어의 프론트엔드 성능을 확인하십시오.
이러한 도구는 다양한 지표를 사용하여 온라인 스토어의 성능을 향상시킬 수 있는 강력한 통찰력과 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 프론트엔드 성능 확인

웹 사이트 스토어의 프론트엔드 성능을 확인하려면:

1. 다음과 같은 웹 성능 도구를 사용하여 프론트엔드 성능 감사:

   - **[Google Lighthouse](https://web.dev/measure/)**—Lighthouse에는 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다. 다양한 등대 실행 방법에 대한 자세한 내용은 [등대 개요](https://developer.chrome.com/docs/lighthouse/overview)를 참조하십시오.
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights는 느린 웹 페이지 성능의 원인에 대한 자세한 보고서와 이를 수정하는 방법에 대한 권장 사항을 신속하게 제공합니다.

1. 감사 보고서를 검토하고 저장소 성능을 개선하기 위해 제공된 권장 사항을 구현합니다.

## 추가 정보

- [관리자 사용자를 위한 색인 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=ko)
- [개발자를 위한 인덱싱 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)
