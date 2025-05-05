---
title: 'ACSD-45169: 시각적 머천다이저가 구성 가능한 제품에 대해 잘못된 재고 및 가격을 표시합니다.'
description: ACSD-45169 패치는 스테이징 업데이트가 적용된 후 시각적 머천다이저에 구성 가능한 제품에 대한 올바른 재고 및 가격이 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45169입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
exl-id: 3f1218ee-2fd0-4f3e-80d7-7e6f9342e0fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169: 시각적 머천다이저가 구성 가능한 제품에 대해 잘못된 재고 및 가격을 표시합니다.

ACSD-45169 패치는 스테이징 업데이트가 적용된 후 시각적 머천다이저에 구성 가능한 제품에 대한 올바른 재고 및 가격이 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45169입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스테이징 업데이트가 적용된 후 Visual Merchandiser에 구성 가능한 제품에 대한 올바른 재고 및 가격이 표시되지 않습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만듭니다.
1. 간단한 제품에 대해 예약된 업데이트를 만듭니다(다른 행 및 엔티티 ID만 있으면 됨).
1. 구성 가능한 제품을 만듭니다.
1. 구성 가능한 제품을 범주에 지정합니다.
1. 범주를 열고 시각적 머천다이저 섹션 아래에서 구성 가능한 제품을 관찰합니다.

<u>예상 결과</u>:

Visual Merchandiser에 올바른 주식과 가격이 표시됩니다.

<u>실제 결과</u>:

Visual Merchandiser에 잘못된 주식과 가격이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
