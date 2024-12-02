---
title: 'ACSD-61785: GraphQL 돌연변이 및 REST API 호출을 통해 reward_warning_notification 속성을 업데이트할 수 없음'
description: ACSD-61785 패치를 적용하여 GraphQL 돌연변이 및 REST API 호출을 통해 'reward_warning_notification' 속성을 업데이트할 수 없는 Adobe Commerce 문제를 수정하십시오.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: GraphQL 돌연변이 및 REST API 호출을 통해 reward_warning_notification 속성을 업데이트할 수 없음

ACSD-61785 패치는 GraphQL 돌연변이 및 REST API 호출을 통해 `reward_warning_notification` 특성을 업데이트할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-61785입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.7-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 돌연변이 및 REST API 호출을 통해 `reward_warning_notification` 특성을 업데이트할 수 없습니다.

<u>재현 단계</u>:

1. *잔액 업데이트 구독* 및 *포인트 만료 알림 구독*&#x200B;에 대한 GraphQL 및 REST API 스키마/설명서를 확인하십시오.

<u>예상 결과</u>:

GraphQL 및 REST API를 통해 *보상 잔액 업데이트* 및 *포인트 만료 알림*&#x200B;을 구독할 수 있습니다.

<u>실제 결과</u>:

GraphQL 및 REST API에는 이 기능이 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
