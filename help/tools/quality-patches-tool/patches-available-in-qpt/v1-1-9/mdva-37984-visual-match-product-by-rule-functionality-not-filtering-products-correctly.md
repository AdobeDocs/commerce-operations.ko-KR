---
title: 'MDVA-37984: 스테이징 업데이트를 적용할 때 시각적 머천다이저가 올바르게 작동하지 않음'
description: MDVA-37984 패치는 스테이징 업데이트가 적용될 때 시각적 머천다이저의 "제품별 일치" 기능이 제품을 제대로 필터링하지 못하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37984입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: 스테이징 업데이트를 적용할 때 시각적 머천다이저가 올바르게 작동하지 않음

MDVA-37984 패치는 스테이징 업데이트가 적용될 때 시각적 머천다이저의 &quot;제품별 일치&quot; 기능이 제품을 제대로 필터링하지 못하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37984입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

시각적 머천다이저의 &quot;규칙별 제품 일치&quot; 기능은 스테이징 업데이트가 적용될 때 제품을 올바르게 필터링하지 않습니다.

<u>재현 단계</u>:

1. 기존 제품에 대한 일정 업데이트를 만듭니다.
   * `entity_id`과(와) `row_id`에 대해 다른 값을 설정하십시오.
1. 구성 가능한 새 제품을 만든 다음 간단한 제품을 만듭니다(따라서 새 제품 `entity_id`과(와) `row_ids`도 다름).
   * 문제를 더 쉽게 복제할 수 있도록 단순 제품에 대해 구별 가능한 수량 값(예: 5000)을 설정합니다.
1. 범주 > **범주의 제품**(으)로 이동하여 **규칙별로 제품 일치**&#x200B;를 사용하도록 설정합니다.
1. 이제 속성으로 &quot;Quantity&quot;, 연산자로 &quot;Greater&quot;, 값으로 &quot;4500&quot;을 선택합니다.
1. **저장**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

새로 만든 구성 가능한 제품이 나열됩니다.

<u>실제 결과</u>:

새로 만든 구성 가능한 제품이 나열되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
