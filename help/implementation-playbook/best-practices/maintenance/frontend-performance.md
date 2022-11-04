---
title: 프런트 엔드 성능 감사
description: 웹 성능 도구를 사용하여 Adobe Commerce 저장소 작업을 감사하여 사이트 성능에 부정적인 영향을 주는 문제를 식별하고 해결합니다.
role: Admin, User, Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# 프런트 엔드 성능에 대한 우수 사례

웹 성능 도구를 사용하여 Adobe Commerce 저장소의 프런트 엔드 성능을 확인합니다.
이러한 도구는 다양한 지표를 사용하여 온라인 스토어의 성능을 향상시키기 위한 강력한 통찰력과 권장 사항을 제공합니다.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 프런트 엔드 성능 확인

웹 사이트 스토어의 프런트 엔드 성능을 확인하려면:

1. 다음과 같은 웹 성능 도구를 사용하여 프런트 엔드 성능 감사

   - **[Google 등대](https://web.dev/measure/)**—Lighthouse는 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사를 제공합니다. 등대를 실행하는 다른 방법에 대한 자세한 내용은 [등대 개요](https://developer.chrome.com/docs/lighthouse/overview))
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights는 수정 방법에 대한 권장 사항과 함께 웹 페이지 성능이 느린 원인에 대한 자세한 보고서를 빠르게 제공합니다.

1. 감사 보고서를 검토하고 제공된 권장 사항을 구현하여 저장소 성능을 개선하십시오.

## 추가 정보

- [관리자 사용자를 위한 색인 관리](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI를 사용한 인덱스 관리](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [개발자를 위한 색인 지정 개요](https://developer.adobe.com/commerce/php/development/components/indexing/)


