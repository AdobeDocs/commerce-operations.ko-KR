---
title: 'MDVA-42507: 장바구니 규칙에 대한 스테이징 업데이트를 적용하면 전체 페이지 캐시가 정리됩니다.'
description: MDVA-42507 패치는 장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42507입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
exl-id: 19f61e31-67da-4bd6-bce7-a9250f3946c7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-42507: 장바구니 규칙에 대한 스테이징 업데이트를 적용하면 전체 페이지 캐시가 정리됩니다.

MDVA-42507 패치는 장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-42507입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니 규칙에 대한 스테이징 업데이트를 적용하면 전체 페이지 캐시가 정리됩니다.

<u>재현 단계</u>:

1. 개발자 모드를 활성화합니다.
1. 여러 제품 및 카테고리 페이지를 열고 (헤더를 통해) 캐시에서 로드되었는지 확인합니다.
1. 장바구니 규칙에 대한 스테이징 업데이트를 적용합니다.
1. 캐시에서 범주 및 제품 페이지가 계속 로드되는지 확인합니다.

<u>예상 결과</u>:

장바구니 규칙에 대한 스테이징 업데이트를 적용한 후 전체 페이지 캐시가 정리되지 않습니다.

<u>실제 결과</u>:

장바구니 규칙에 대한 스테이징 업데이트를 적용하면 전체 페이지 캐시가 정리됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
