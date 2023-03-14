---
title: 베타 릴리스
description: Adobe Commerce 베타 릴리스와 참여 방법에 대해 알아봅니다.
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Adobe Commerce 베타 릴리스

2023년 6월부터 향후 Adobe은 패치 릴리스(&quot;베타 릴리스&quot;)에 대한 공개 베타를 릴리스할 예정입니다. Beta 릴리스는 GA(일반 출시) 이전에 모든 Adobe Commerce 고객 및 파트너가 사용할 수 있으며 보안, 규정 준수, 성능 및 높은 우선 순위 품질 수정 사항이 포함되어 있습니다.

>[!IMPORTANT]
>
>베타 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 지원(Adobe 지원 서비스 등을 통해)할 의무가 없습니다. 고객은 베타 릴리스 및/또는 관련 설명서나 자료의 올바른 기능이나 성능에 어떠한 의존도 하지 말고 주의하는 것이 좋습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

## 릴리스 내용

각 Adobe Commerce 베타 릴리스에는 다음 기능 영역을 포함하되 이에 국한되지 않고 예약된 릴리스 날짜까지 Adobe Commerce 코어 코드에 전달되는 모든 변경 사항이 포함됩니다.

- 최신 보안 수정 사항
- 성능 향상
- GraphQL 개선 사항
- 일반 품질 버그 수정
- 커뮤니티 기여
- 과의 호환성을 지원하는 데 필요한 변경 사항 [Adobe Commerce 서비스](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## 명명 규칙 및 일정

Adobe은 1년에 두 번 베타 패치를 출시할 예정입니다. 첫 번째 베타 패치는 일반적으로 새로운 핵심 애플리케이션 패치 릴리스의 공식 출시 후 3개월 후에 릴리스됩니다.

베타 릴리스 패키지에는 `-betaX` 접미사. 예를 들어 Adobe Commerce 2.4.7 베타 릴리스 패키지는 다음 명명 규칙을 사용합니다.

- `2.4.7-beta1`
- `2.4.7-beta2`

다음을 참조하십시오. [출시 일정](schedule.md) 예정된 공개 베타 릴리스 날짜 목록입니다.

## 참여의 이점

개발 중인 코드가 빨리 표시되므로 곧 출시될 업그레이드에 대한 기술과 판매자의 준비를 더 빨리 완료할 수 있습니다.

상황이 변경될 수 있지만 Beta 릴리스를 사용하면 코드 베이스 변경 사항이 발생하는 위치를 이해하고 GA 릴리스 날짜 이전에 준비를 시작할 수 있습니다.

## 베타 릴리스 액세스

Adobe Commerce 베타 릴리스는 다른 Adobe Commerce 패치 릴리스와 동일한 방식으로 배포됩니다. `https://repo.magento.com`. 소스 코드는에서 사용할 수 있습니다 [GitHub](https://github.com/magento/magento2).

다음을 참조하십시오 [Composer 설치 빠른 시작](../installation/composer.md) 을 참조하십시오.

## 문제 보고

Adobe은 베타 릴리스에 대한 표준 Adobe 지원 서비스를 제공하지 않습니다.

베타 릴리스와 관련된 피드백을 제출하려면 다음을 따르십시오. [일반 문제 보고 흐름](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 날짜 [GitHub](https://github.com/magento/magento2).

내부 팀은 최신 Beta 릴리스와 관련하여 보고된 모든 중요한 문제를 모니터링하고 GA 릴리스 날짜 이전에 해결되도록 우선 순위를 지정합니다.
