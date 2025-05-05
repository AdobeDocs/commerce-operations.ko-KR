---
title: 'ACSD-63090: 관리자에서 제품을 삭제하면 장바구니가 비워집니다'
description: ACSD-63090 패치를 적용하여 장바구니에 추가된 후 제품이 삭제되어 고객의 장바구니 항목이 사라지는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 513993f0c4bd97047ad128a25a4b2a6b3eebd82b
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090: 관리자에서 제품을 삭제하면 장바구니가 비워집니다

ACSD-63090 패치는 장바구니에 추가된 후 제품이 관리자에서 삭제되어 고객의 장바구니 항목이 사라지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-63090입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p8

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 추가된 후 제품이 삭제되면 장바구니 항목이 사라집니다.

<u>재현 단계</u>:

1. 두 개의 하위 제품으로 구성 가능한 제품을 만듭니다.
1. 등록된 고객으로 로그인합니다.
1. 두 하위 제품을 장바구니에 추가합니다.
1. 계정에서 로그아웃합니다.
1. 카탈로그에서 하위 제품 중 하나를 삭제합니다.
1. API를 사용하여 다른 하위 제품의 가격을 업데이트합니다.

<u>예상 결과</u>:

나머지 제품은 장바구니에 표시되며 기존 견적은 `quote` 데이터베이스 테이블에서 업데이트됩니다.

<u>실제 결과</u>:

* 미니 장바구니가 비어 있습니다.
* `quote` 데이터베이스 테이블에 새 견적 레코드가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool]: 도구 가이드의 품질 패치용 셀프서비스 도구](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
