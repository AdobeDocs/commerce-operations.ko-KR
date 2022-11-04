---
title: 확장 모범 사례
description: 타사 Adobe Commerce 확장으로 인해 발생하는 성능 문제를 방지하는 방법을 알아봅니다.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# 확장 모범 사례

Adobe Commerce 타사 확장(모듈)은 상점 성능에 부정적인 영향을 줄 수 있는 다양한 문제를 일으킬 가능성이 있습니다. 다음과 같은 우수 사례를 통해 이러한 문제를 방지할 수 있습니다.

- 와 같은 신뢰할 수 있는 소스에서 타사 확장을 다운로드하여 구입합니다. [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- 모든 타사 확장을 최신 버전으로 업데이트합니다.
- 타사 확장을 업데이트할 수 없는 경우, 다른 확장을 사용하는 것이 좋습니다.
- 새 Adobe Commerce 버전으로 업그레이드할 때 설치된 타사 확장이 새 버전과 호환되는지 확인하고 필요한 경우 확장을 업그레이드하십시오.

>[!NOTE]
>
> Adobe Commerce Marketplace에서 사용할 수 있는 모든 확장은 새로운 상거래 릴리스와의 호환성을 유지하기 위해 필요합니다. 자세한 내용은 [릴리스 호환성](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md) 다음 중 하나를 수행합니다.

- Adobe Commerce on cloud 인프라
- Adobe Commerce 온-프레미스

## 추가 정보

- [업그레이드 계획 모범 사례](../../../upgrade/prepare/best-practices.md)
- 클라우드 인프라에서 Adobe Commerce에서 타사 확장 사용
   - [기술 및 요구 사항 - 개발 및 테스트](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-devtest)
   - [통합 및 스테이징에서 완전히 테스트하는 이유는 무엇입니까?](https://devdocs.magento.com/cloud/live/live.html#whytest)
