---
title: 'ACSD-45488: 여러 소스가 있는 구성 가능한 제품이 자동으로 재고로 반환되지 않음'
description: ACSD-45488 패치는 여러 소스를 가진 구성 가능한 제품이 자동으로 재고로 반환되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45488입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488: 자동으로 재고로 반환되지 않는 여러 소스를 사용하여 구성 가능한 제품

ACSD-45488 패치는 여러 소스를 가진 구성 가능한 제품이 자동으로 재고로 반환되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45488입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 소스를 사용하여 구성 가능한 제품은 자동으로 재고로 반환되지 않습니다.

<u>재현 단계</u>:

1. 보조 스톡 소스를 만듭니다.
1. 두 개의 연결된 가상 제품을 사용하여 구성 가능한 제품을 만듭니다.
1. 연관된 제품을 기본 재고 출처에 지정하고 수량을 1로 설정합니다.
1. `cataloginventory_stock_status`에서 `stock_status`을(를) 확인합니다.
1. 연결된 두 제품을 모두 *품절*&#x200B;로 설정하십시오.
1. `cataloginventory_stock_status`에서 `stock_status`을(를) 확인합니다.
1. 연결된 두 제품을 모두 *재고*(으)로 설정합니다.
1. `cataloginventory_stock_status`에서 `stock_status`을(를) 확인합니다.

<u>예상 결과</u>:

관련 제품이 재고로 설정된 경우 구성 가능한 제품의 재고 상태가 *재고*(으)로 업데이트됩니다.

<u>실제 결과</u>:

관련 제품이 재고로 설정된 경우 구성 가능한 제품의 재고 상태가 *재고*(으)로 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
