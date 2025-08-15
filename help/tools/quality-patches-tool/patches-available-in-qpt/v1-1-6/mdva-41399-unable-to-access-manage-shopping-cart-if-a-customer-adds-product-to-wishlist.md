---
title: 'MDVA-41399: 고객이 위시리스트에 제품을 추가하는 경우 장바구니 관리에 액세스할 수 없음'
description: MDVA-41399 패치는 고객이 위시리스트에 제품을 추가할 경우 관리 사용자가 장바구니 관리 페이지에 액세스할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41399입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399: 고객이 위시리스트에 제품을 추가하는 경우 장바구니 관리에 액세스할 수 없음

MDVA-41399 패치는 고객이 위시리스트에 제품을 추가할 경우 관리 사용자가 장바구니 관리 페이지에 액세스할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41399입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 위시리스트에 제품을 추가하는 경우 관리자 사용자는 장바구니 관리 페이지에 액세스할 수 없습니다.

<u>필수 구성 요소</u>:

1. 두 개 이상의 제품을 만듭니다.
1. 고객을 만듭니다.
1. 개발자 모드를 활성화합니다.

<u>재현 단계</u>:

1. Storefront로 이동하여 전제 조건에서 고객으로 로그인합니다.
1. 위시리스트에 제품 추가.
1. 관리 패널로 이동하여 만든 고객 편집 페이지로 이동하고 **장바구니 관리** 단추를 클릭합니다.

<u>예상 결과</u>:

관리자 사용자는 장바구니를 관리할 수 있습니다.

<u>실제 결과</u>:

관리자가 오류 메시지를 받습니다. *오류가 발생했습니다. 자세한 내용은 오류 로그를 참조하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool]  가이드의 ](/help/tools/quality-patches-tool/usage.md)> 사용량[!DNL Quality Patches Tool]
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [ 안내서에서 ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인[!DNL Quality Patches Tool].

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
