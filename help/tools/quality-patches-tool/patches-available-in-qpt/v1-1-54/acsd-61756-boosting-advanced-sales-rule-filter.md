---
title: 'ACSD-61756: 데이터베이스 인덱스 누락으로 인한 ''AdvancedSalesRule'' 필터의 성능 저하'
description: ACSD-61756 패치를 적용하여 'magento_salesrule_filter' 쿼리가 인덱스를 사용하지 않고 전체 테이블 검색을 수행하여 대량의 레코드를 처리할 때 성능이 저하되는 Adobe Commerce 문제를 해결합니다. 이 패치는 'AdvancedSalesRule' 필터의 누락된 데이터베이스 인덱스를 추가하여 성능을 개선합니다.
feature: Price Rules, Price Indexer
role: Admin, Developer
source-git-commit: 42a376d1a791a17d88bea68dfef178a7b2849ce2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: 데이터베이스 인덱스가 누락되어 `AdvancedSalesRule` 필터의 성능이 저하되었습니다.

ACSD-61756 패치를 적용하여 누락된 데이터베이스 인덱스를 추가하여 `AdvancedSalesRule` 필터의 성능을 개선합니다. 이렇게 하면 `magento_salesrule_filter` 쿼리가 인덱스를 사용하지 않고 전체 테이블 검색을 수행하여 테이블에 레코드가 많을 때 성능이 저하되는 문제가 해결됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-61756입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p9

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`magento_salesrule_filter` 쿼리가 인덱스를 사용하지 않고 전체 테이블 검사를 수행하므로 테이블에 레코드가 많을 때 `AdvancedSalesRule` 필터의 성능이 저하됩니다.

<u>재현 단계</u>:

1. 여러 활성 영업 규칙이 있는 체크아웃.

<u>예상 결과</u>:

영업 규칙 성능이 개선되었습니다.

<u>실제 결과</u>:

쿼리가 전체 테이블 검색을 수행하고 인덱스를 활용하지 못하면 테이블에 많은 레코드가 있을 때 성능이 저하됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
