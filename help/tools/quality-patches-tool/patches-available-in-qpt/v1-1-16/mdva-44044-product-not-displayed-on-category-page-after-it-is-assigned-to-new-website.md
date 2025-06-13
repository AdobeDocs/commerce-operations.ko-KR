---
title: 'MDVA-44044: 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않음'
description: MDVA-44044 패치는 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44044입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044: 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않음

MDVA-44044 패치는 제품이 새 웹 사이트에 할당된 후 카테고리 페이지에 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44044입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품이 새 웹 사이트에 할당된 후에는 카테고리 페이지에 표시되지 않습니다.

<u>재현 단계</u>:

1. 인덱서 모드를 예약으로 설정합니다.
1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. `index.php`에 보조 저장소 코드 추가:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. 새 카테고리를 만듭니다.
1. 새로 만든 카테고리에 할당된 새 제품을 만듭니다. 기본 웹 사이트에만 지정해야 합니다.
1. 크론을 작동시키세요
1. 상점 앞에서 범주를 엽니다.
1. 제품을 보조 웹 사이트에 할당합니다.
1. 크론을 다시 실행하세요.

<u>예상 결과</u>:

예약된 인덱서 다음에 제품이 카테고리 페이지에 표시됩니다.

<u>실제 결과</u>:

전체 색인 재지정이 될 때까지 해당 제품이 카테고리 페이지에 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
