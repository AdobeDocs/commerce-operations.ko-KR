---
title: 'ACSD-51819: 단일 견적 ID로 여러 주문 배치'
description: ACSD-51819 패치를 적용하여 동일한 견적 ID를 통해 여러 주문을 할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
source-git-commit: 5f22591c499f0f5d349994195731c7c87512f5f0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-51819: 단일 견적 ID로 여러 주문 배치

ACSD-51819 패치는 동일한 견적 ID를 통해 여러 주문을 할 수 있는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51819입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2, 2.4.5-p5, 2.4.6, 2.4.6-p4, 2.4.7-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p11, 2.4.5-p3 - 2.4.5-p10, 2.4.6 - 2.4.6-p8, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 견적 ID로 여러 주문을 할 수 있습니다.

<u>재현 단계</u>:

1. 사용자로 로그인
1. 장바구니에 항목을 추가하고 체크아웃을 진행합니다.
1. 결제 방법을 선택하되 **[!UICONTROL Place Order]** 버튼을 클릭하지 마십시오.
1. 다른 브라우저에서 동일한 계정에 로그인합니다.
1. **[!UICONTROL Place Order]** 단추를 클릭하지 않고 동일한 항목으로 체크아웃을 진행합니다.
1. 두 시스템에서 동시에 **[!UICONTROL Place Order]** 단추를 클릭합니다.
1. 두 브라우저에서 수행한 주문의 유효성을 확인합니다.

<u>예상 결과</u>:

한 브라우저에서 수행한 첫 번째 주문만 성공적으로 처리됩니다.

<u>실제 결과</u>:

두 브라우저 모두에서 주문이 완료되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](/help/tools/quality-patches-tool/usage.md)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [!UICONTROL Quality Patches Tool] 안내서에서  [!DNL Quality Patches Tool][&#128279;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인합니다.


QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
