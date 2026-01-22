---
title: 패치 릴리스 일정
description: Adobe이 Adobe Commerce에 대한 새로운 패치 및 보안 수정 사항을 언제 발표할지 알아봅니다.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: ee39af1beb8df93b179c2e5dee3942b3f367e51a
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# 패치 릴리스 일정

Adobe은 조기 채택자에게 향상된 기능을 더 빨리 제공하면서 제품 업그레이드를 단순하고 예측 가능하게 만드는 것 사이의 올바른 균형을 찾기 위해 끊임없이 노력하고 있습니다([버전 관리 정책](versioning-policy.md) 참조).

이 일정의 목적은 Adobe이 핵심 Adobe Commerce PHP 애플리케이션의 지원되는 각 릴리스 라인에 대해 [패치](versioning-policy.md#patch-release) 릴리스를 발표할 계획인 날짜를 제공하는 것입니다. 패치 릴리스는 핵심 코드 베이스를 업그레이드하여 플랫폼을 안전하고 안정적이며 성능을 유지할 수 있는 기회입니다.

>[!NOTE]
>
>새로운 기능, 클라우드 인프라 및 확장성 릴리스에 대한 자세한 내용은 [Adobe Commerce 서비스](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all) 릴리스 설명서를 참조하십시오.

이 페이지에 나열된 예약된 품질, 보안 및 Beta 패치 외에도 Adobe은 [품질 패치 도구](versioning-policy.md#individual-patch)를 통해 [개별 패치](../tools/quality-patches-tool/usage.md)에 대한 액세스를 제공합니다. 이 도구를 사용하면 설치된 Adobe Commerce 버전에 사용할 수 있는 모든 개별 패치에 대한 일반 정보를 적용, 되돌리기 및 볼 수 있습니다.

Adobe Commerce은 다음과 같은 전략으로 월별 패치 릴리스 일정을 따릅니다.

- **격리된 보안 수정**—개별 비누적 [보안 수정](versioning-policy.md#isolated-patch)은(는) 매월 릴리스될 수 있으며 모든 [지원](lifecycle-policy.md) 릴리스 라인에 대한 보안 수정 사항을 포함할 수 있습니다(일반 및 확장 지원 포함).

- **보안 패치**—최소 [보안 패치](versioning-policy.md#security-patch-release)은(는) 모든 [지원](lifecycle-policy.md) 릴리스 라인에 대해 매년(5월) 릴리스됩니다. 이러한 패치에는 이전에 릴리스된 모든 격리된 보안 수정 사항이 포함됩니다. Adobe은 필요한 경우 11월에 추가 보안 패치를 출시할 수 있지만 보장되지는 않습니다.

- **패치**—Adobe Commerce 2.4.x LTS 릴리스 라인(3년 지원 기간)용 전체 [패치](versioning-policy.md#patch-release)은(는) 매년(5월) 릴리스됩니다.

- **Beta 패치**—Adobe Commerce 2.4.x LTS 릴리스 라인용 [베타 패치 2개](versioning-policy.md#beta-patch-release)가 1년에 두 번(3월과 11월) 릴리스됩니다.

자세한 내용은 다음 이미지를 참조하십시오.

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerce 릴리스 일정](../assets/release/release-calendar.drawio.png)


## 릴리스 알림 채널

Adobe은 다음 채널을 통해 고객에게 새 패치 릴리스에 대해 알립니다.

- [Adobe 보안 게시판 및 권고 조치](https://helpx.adobe.com/security/security-bulletin.html#magento)
- 이메일
- 제품 내 경고

>[!NOTE]
>
> 모든 부, 패치 및 보안 릴리스의 릴리스 날짜 및 일반 지원 종료 날짜는 [릴리스 버전](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions)을 참조하십시오.
