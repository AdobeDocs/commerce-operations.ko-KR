---
title: 'MDVA-42237: 구성 가능한 제품 특별 가격이 업데이트되지 않음'
description: MDVA-42237 패치는 하위 제품 가격이 변경된 후 구성 가능한 제품의 특별 가격이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42237입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
exl-id: 1bae9a14-d6c1-4ee3-85aa-5d80ef479385
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42237: 구성 가능한 제품 특별 가격이 업데이트되지 않음

MDVA-42237 패치는 하위 제품 가격이 변경된 후 구성 가능한 제품의 특별 가격이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42237입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품의 특별 가격은 하위 제품 가격이 변경된 후에는 업데이트되지 않습니다.

<u>재현 단계</u>:

1. **관리자** > **시스템** > **인덱스 관리**(으)로 이동하고 모든 인덱스에 대해 **인덱스 모드**&#x200B;을(를) **일정별 업데이트**(으)로 설정합니다.
1. 간단한 제품 하나로 구성 가능한 제품을 만들고 하위 제품에 대한 특별 가격을 설정합니다.
1. 특별가격이 상점 앞에 반영되었는지 확인하십시오.
1. GraphQL을 사용하여 특별 가격을 제거하고 상점 첫 화면에서 제품 가격을 다시 확인하십시오.

<u>예상 결과</u>:

더 이상 특별 가격이 상점 앞에 표시되지 않습니다.

<u>실제 결과</u>:

가게 앞에는 가격이 업데이트되어 있지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
