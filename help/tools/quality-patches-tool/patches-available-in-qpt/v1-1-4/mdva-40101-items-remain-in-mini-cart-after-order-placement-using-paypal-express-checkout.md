---
title: 'MDVA-40101: 주문 배치 PayPal Express Checkout 후 항목이 미니 장바구니로 남음'
description: MDVA-40101 패치는 PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후 미니 장바구니에서 항목이 제거되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40101입니다. 이 문제는 Adobe Commerce 2.4.0에서 해결되었습니다.
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
exl-id: 8d3fa92e-39ed-4d8f-8dbe-9c08f787c6f1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-40101: 주문 배치 PayPal Express Checkout 후 항목이 미니 장바구니로 남음

MDVA-40101 패치는 PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후 미니 장바구니에서 항목이 제거되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40101입니다. 이 문제는 Adobe Commerce 2.4.0에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.7

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

PayPal Express Checkout을 사용하여 주문을 성공적으로 배치한 후에도 항목은 미니 장바구니에 남아 있습니다.

<u>재현 단계</u>:

브라우저의 시크릿 모드에서 PayPal Express Checkout을 사용하여 주문합니다.

<u>예상 결과</u>:

미니 장바구니는 주문이 성공적으로 완료되면 비어 있어야 합니다.

<u>실제 결과</u>:

* 성공 페이지에 빈 미니 장바구니가 표시됩니다.
* 다른 모든 페이지에는 구매한 항목이 있는 미니 장바구니가 표시됩니다.
* 장바구니 링크를 클릭하면 빈 장바구니 페이지로 리디렉션됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!DNL Quality Patches Tool] 안내서에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 섹션을 참조하십시오.
