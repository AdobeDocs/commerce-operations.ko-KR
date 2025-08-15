---
title: 확장 우수 사례
description: 타사 Adobe Commerce 확장으로 인한 성능 문제를 방지하는 방법을 알아봅니다.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 1fdbded7738365593ef7da64f4dbe6713984bff3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 확장 우수 사례

Adobe Commerce 타사 확장(모듈)은 상점 성능에 부정적인 영향을 줄 수 있는 다양한 문제를 일으킬 수 있는 잠재력이 있습니다. 다음 모범 사례를 따라 이러한 문제를 방지할 수 있습니다.

- 가능한 모든 곳에서 [프로세스 외부 확장성](https://developer.adobe.com/commerce/extensibility/)을 사용하여 Commerce 통합 및 사용자 지정을 개발하여 유지 관리 및 업그레이드를 용이하게 합니다.
- [Commerce Marketplace](https://marketplace.magento.com/extensions.html)과(와) 같은 신뢰할 수 있는 소스에서 타사 확장을 다운로드하고 구입합니다.
- 모든 타사 확장을 최신 버전으로 업데이트합니다.
- 타사 확장을 계속 업데이트할 수 없는 경우에는 다른 확장을 사용하는 것이 좋습니다.
- 새 버전의 Adobe Commerce으로 업그레이드하려는 경우 설치된 타사 확장이 새 버전과 호환되는지 확인하고 필요한 경우 확장을 업그레이드하십시오.

>[!NOTE]
>
> Adobe Commerce Marketplace에서 사용할 수 있는 모든 확장은 새 Commerce 릴리스와의 호환성을 유지해야 합니다. [릴리스 호환성](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/)을 참조하세요.

## 영향을 받는 제품 및 버전

[지원되는 모든 버전](../../../release/versions.md):

- 클라우드 인프라의 Adobe Commerce
- Adobe Commerce 온-프레미스

## 추가 정보

- [업그레이드 계획 모범 사례](../../../upgrade/prepare/best-practices.md)
- 클라우드 인프라에서 Adobe Commerce과 함께 서드파티 확장 사용
   - [기술 및 요구 사항 - 개발 및 테스트](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [통합 및 스테이징에서 완전히 테스트하는 이유는 무엇입니까?](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
