---
title: 'ACSD-49392: 부분 환불 후 주문 상태가 마감으로 변경됨'
description: ACSD-49392 패치를 적용하여 번들 제품에 대한 부분 환불 후 주문 상태가 종료됨으로 변경되는 Adobe Commerce 문제를 수정합니다.
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 67e050b4ceccc3f30bf8cd49125525b2e8d8b0dd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392: 부분 환불 후 주문 상태가 마감으로 변경됨

>[!NOTE]
>
>ACSD-49392 패치가 버전 2.4.6-p7에서 2.4.6-p10까지의 [ACSD-57003](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) 패치로 대체되었습니다.

ACSD-49392 패치는 번들 제품에 대한 부분 환불 후 주문 상태가 종료됨으로 변경되는 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.31이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49392입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.3.7-p4 및 2.4.1 - 2.4.6-p6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

묶음 제품에 대한 부분 환불 후 주문 상태가 마감으로 변경됩니다.

<u>재현 단계</u>:

1. Adobe Commerce에 로그인하고 모든 번들 제품을 만들거나 기존 번들 제품을 사용합니다.
1. 수량이 1보다 큰 이 묶음 상품을 주문하세요.
1. 관리자로 이동하여 **[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;에서 2단계에서 만든 주문을 열고 송장을 만드십시오. 주문 상태를 확인합니다. 처리 중입니다.
1. 부분 대변 메모를 생성합니다(번들의 모든 제품에 대해 환불 안 함).
1. 주문 상태를 확인합니다.

<u>예상 결과</u>

묶음 상품에 대한 부분 대변 메모를 작성한 후, 주문 상태는 처리 중입니다.

<u>실제 결과</u>

묶음 제품에 대한 부분 대변 메모를 작성한 후 주문 상태는 완료입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.[


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
